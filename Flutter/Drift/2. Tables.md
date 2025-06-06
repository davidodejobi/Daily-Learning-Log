# Drift Tables – Crash Course for **Quiver**

This note distills everything you need to model Quiver’s data layer with Drift. Keep it as a quick‑reference while coding.

## 1  Table Anatomy

• Every table is a Dart class that `extends Table`.
• Columns are `late final` fields. The *first* builder call (`integer()`, `text()`, …) decides the SQL type.
• At build time Drift generates a **Row class** (e.g. `StudySetsData`) and a **Companion** for inserts/updates.

```dart
class StudySets extends Table {
  // Primary key – auto‑increments by default
  IntColumn get id => integer().autoIncrement()();

  // Display name
  TextColumn get title => text().withLength(min: 1, max: 80)();

  // Cached counters for fast UI chips ➟ updated via triggers (see §6)
  IntColumn get summaryCount   => integer().withDefault(const Constant(0))();
  IntColumn get flashcardCount => integer().withDefault(const Constant(0))();
  IntColumn get quizCount      => integer().withDefault(const Constant(0))();

  // Audit columns from a Mixin (see §3)
  // createdAt, updatedAt
}
```

## 2  Core Column Builders

| Dart type | Builder      | Notes                                                            |
| --------- | ------------ | ---------------------------------------------------------------- |
| int       | `integer()`  | 64‑bit INTEGER in SQLite                                         |
| BigInt    | `int64()`    | Use if targeting Web and numbers may exceed JS 53‑bit safe range |
| String    | `text()`     | Add `withLength()` for min/max                                   |
| bool      | `boolean()`  | Stored as 0 / 1                                                  |
| double    | `real()`     | IEEE‑754                                                         |
| Uint8List | `blob()`     | Raw bytes (attachments, thumbnails)                              |
| DateTime  | `dateTime()` | Stored as INTEGER (unix seconds) **or** TEXT (ISO‑8601) – see §4 |

## 3  Reuse Columns with Mixins

```dart
mixin AuditColumns on Table {
  DateTimeColumn get createdAt => dateTime()
      .clientDefault(() => DateTime.now())();
  DateTimeColumn get updatedAt => dateTime()
      .nullable()(); // manually set on update
}

class Topics extends Table with AuditColumns {
  IntColumn get id => integer().autoIncrement()();
  IntColumn get studySetId => integer().references(StudySets, #id)();
  TextColumn get title => text()();
  IntColumn get position => integer()(); // sort order
}
```

## 4  DateTime Storage Choice

SQLite lacks a native datetime type. Drift defaults to INTEGER unix seconds. For ISO‑8601 strings (good for TZ‑aware sync):

1. Add `build.yaml` at project root:

```yaml
targets:
  $default:
    builders:
      drift_dev:
        options:
          store_date_time_values_as_text: true
```

2. Regenerate code: `dart run build_runner build`

## 5  Primary Keys & Uniqueness

• `autoIncrement()` ➟ integer PK, autoincrement.
• For composite or non‑integer PKs override `primaryKey`:

```dart
@override
Set<Column> get primaryKey => {userId, studySetId};
```

• Uniqueness without PK: `text().unique()` or `uniqueKeys` getter.

## 6  Trigger‑Backed Counters (StudySet chips)

```sql
CREATE TRIGGER trg_summary_insert AFTER INSERT ON summaries
BEGIN
  UPDATE study_sets
  SET summary_count = summary_count + 1,
      updated_at = datetime('now')
  WHERE id = NEW.study_set_id;
END;
```

Create analogous triggers for DELETE and for flashcards/quizzes. Declare them in a Drift `.sql` file or via `customConstraints`.

## 7  Outbox + Sync Metadata (Offline‑First)

| Table               | Purpose                                                                                                                      |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `pending_mutations` | Queue of local inserts/updates/deletes waiting for Supabase. Columns: id PK, table, rowId, action, payload (JSON), createdAt |
| `sync_state`        | Stores cursor (`lastPulledAt`), per‑table version stamps for delta sync                                                      |

At app launch:

1. Read connectivity ⇒ if online, process `pending_mutations` then pull delta.
2. All CRUD ops wrap a local DB Tx + insert into `pending_mutations`.

## 8  Handy Drift Patterns

• **Generated columns** for derived values:

```dart
RealColumn get percentComplete => real().generatedAs(
  completedCards * const Expression<double>('1.0') / totalCards
)();
```

• **Indexes** for fast lookups in big tables:

```dart
@TableIndex(name: 'idx_topic_studyset', columns: {#studySetId})
```

• **Foreign Keys**: remember to enable them once per connection:

```dart
@override
MigrationStrategy get migration => MigrationStrategy(
  onCreate: (m) async {
    await m.createAll();
    await customStatement('PRAGMA foreign_keys = ON;');
  },
);
```

## 9  Typical Table Set for Quiver

```dart
class Summaries extends Table with AuditColumns {
  IntColumn get id => integer().autoIncrement()();
  IntColumn get topicId => integer().references(Topics, #id)();
  TextColumn get content => text()();
}

class Flashcards extends Table with AuditColumns {
  IntColumn get id => integer().autoIncrement()();
  IntColumn get topicId => integer().references(Topics, #id)();
  TextColumn get front => text()();
  TextColumn get back  => text()();
}

class Quizzes extends Table with AuditColumns {
  IntColumn get id => integer().autoIncrement()();
  IntColumn get topicId => integer().references(Topics, #id)();
  TextColumn get question => text()();
  TextColumn get answer   => text()();
}

class StudyProgress extends Table {
  IntColumn get id => integer().autoIncrement()();
  IntColumn get userId => integer()(); // if multi‑user later
  IntColumn get topicId => integer().references(Topics, #id)();
  RealColumn get completion = real().withDefault(const Constant(0))();
}
```

## 10  Workflow Recap

1. Define/modify tables.
2. `dart run build_runner watch` to regen code.
3. Write Drift DAOs or use generated `database.<table>` helpers.
4. Trigger counters keep UI chips instant.
5. Outbox pattern guarantees no data loss offline.
6. Migrate carefully when schema changes (`schemaVersion`++ + `MigrationStrategy`).

Happy hacking! Stay offline, sync when you can, and keep Quiver fast 🚀
