# Drift Local Database Quick‑Start for **Quiver**

> Goal: store study notes offline first, then sync to Supabase when online.

## 1. Why Drift?

* Type‑safe SQL with autocompletion and compile‑time checks.
* Works on Flutter, Android, iOS, desktop, web.
* Generates boilerplate for you via `build_runner`.
* Plays well with background isolates ⇒ keeps UI smooth.

## 2. Add Dependencies (`pubspec.yaml`)

```yaml
dependencies:
  drift: ^2.26.1
  drift_flutter: ^0.2.4  # SQLite wrapper for Flutter
  path_provider: ^2.1.5  # Finds app‑specific folders

dev_dependencies:
  drift_dev: ^2.26.1
  build_runner: ^2.4.15
```

Run:

`dart pub add drift drift_flutter path_provider dev:drift_dev dev:build_runner`

## 3. Define Your Database

`lib/database.dart`

```dart
import 'dart:io';
import 'package:drift/drift.dart';
import 'package:drift_flutter/drift_flutter.dart';
import 'package:path_provider/path_provider.dart';
import 'package:path/path.dart' as p;

part 'database.g.dart';

class Notes extends Table {
  IntColumn get id => integer().autoIncrement()();
  TextColumn get title => text().withLength(min: 1, max: 120)();
  TextColumn get body => text()();
  DateTimeColumn get createdAt => dateTime().withDefault(currentDateAndTime)();
  DateTimeColumn get updatedAt => dateTime().nullable()();
  BoolColumn get isSynced => boolean().withDefault(const Constant(false))();
}

@DriftDatabase(tables: [Notes])
class AppDatabase extends _$AppDatabase {
  AppDatabase() : super(_openConnection());

  @override
  int get schemaVersion => 1;
}

LazyDatabase _openConnection() {
  return LazyDatabase(() async {
    final dir = await getApplicationSupportDirectory();
    final file = File(p.join(dir.path, 'quiver.sqlite'));
    return NativeDatabase.createInBackground(file);
  });
}
```

### Generate Code

```
dart run build_runner build   # one‑off
dart run build_runner watch   # auto‑rebuild on file save
```

## 4. Basic CRUD

```dart
final db = AppDatabase();

// insert
await db.into(db.notes).insert(
  NotesCompanion.insert(title: 'First note', body: 'Hello world'),
);

// read
final allNotes = await db.select(db.notes).get();
```

### Live Updates

```dart
Stream<List<Note>> watchAll() => db.select(db.notes).watch();
```

Streams repaint UI automatically when data changes.

## 5. Offline‑First Sync Pattern (high level)

1. **Write locally first** – mark `isSynced = false`.
2. **Connectivity checker** (e.g. `connectivity_plus`) triggers sync when online.
3. **Upload new/changed rows** to Supabase via RPC or REST.
4. **Mark rows as synced** (`isSynced = true`, `updatedAt` server timestamp).
5. **Resolve conflicts** (e.g. last‑write‑wins or version column).
6. Listen to Supabase realtime channel to pull remote changes.

You can wrap this logic in a `SyncService` singleton that:

* Watches the `notes` stream for unsynced rows.
* Queues them for upload when `hasInternet == true`.
* Applies remote patches into the local DB inside a transaction.

## 6. Migrations

On schema changes:

1. Increment `schemaVersion`.
2. Implement `migrate()` in `AppDatabase`.
3. Use Drift’s built‑in helpers (`createTable`, `addColumn`, etc.).

## 7. Recommended Next Reads

* Drift docs: **Getting Started** & **Writing Queries**.
* Supabase docs: **Flutter Client** → “Upsert” & \*\*realtime”.
* Article: *“Offline‑first sync in Flutter with Drift + Supabase”* (search).

### TL;DR

1. Add deps → run `build_runner`.
2. Define tables → generate code.
3. Use Drift APIs for local reads/writes.
4. Build a small sync layer to push/pull data to Supabase when online.
