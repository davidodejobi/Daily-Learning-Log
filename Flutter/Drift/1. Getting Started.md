# Drift Local Database Quick‑Start for **Quiver**

Goal: store study notes offline first, then sync to Supabase when online.

## 1. Why Drift?

* Type‑safe SQL with autocompletion and compile‑time checks.
* Works on Flutter, Android, iOS, desktop, and web.
* Generates boilerplate for you via `build_runner`.
* Uses background isolates so heavy queries never block your UI.

## 2. Add Dependencies (`pubspec.yaml`)

```yaml
dependencies:
  drift: ^2.26.1
  drift_flutter: ^0.2.4        # SQLite wrapper for Flutter
  path_provider: ^2.1.5        # Finds app‑specific folders

dev_dependencies:
  drift_dev: ^2.26.1
  build_runner: ^2.4.15
```

Add them quickly:

```bash
dart pub add drift drift_flutter path_provider \
  dev:drift_dev dev:build_runner
```

## 3. Define Your Database

`lib/database.dart`

```dart
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
```

### 3 a. Deep‑dive: the manual `_openConnection()`

Below is the full version you saw in the docs. It shows **exactly** how Drift opens SQLite on every platform and why extra Android tweaks are required.

```dart
import 'dart:io';                               // Platform checks & file I/O
import 'package:drift/native.dart';             // NativeDatabase & LazyDatabase
import 'package:path_provider/path_provider.dart'; // Safe OS folders
import 'package:path/path.dart' as p;           // Join paths in a cross‑platform way
import 'package:sqlite3/sqlite3.dart';          // Low‑level SQLite bindings
import 'package:sqlite3_flutter_libs/sqlite3_flutter_libs.dart'; // extra Flutter glue

LazyDatabase _openConnection() {
  // LazyDatabase runs the expensive file lookup only the first time
  // you actually use the database. Great for faster cold‑starts.
  return LazyDatabase(() async {
    // 1️⃣ Choose a **persistent** location for the .sqlite file
    final dbFolder = await getApplicationDocumentsDirectory(); // e.g. /data/user/0/<package>/documents
    final file = File(p.join(dbFolder.path, 'db.sqlite'));

    // 2️⃣ Patch quirks on older Android versions
    if (Platform.isAndroid) {
      // Some very old devices (pre‑N) crash when dlopen‑ing the bundled libsqlite3.so.
      // This helper swaps in a safer loader path so Drift can still start.
      await applyWorkaroundToOpenSqlite3OnOldAndroidVersions();
    }

    // 3️⃣ Tell SQLite where it may place its **temporary** files
    // Android sandboxes /tmp away, so we redirect to your app cache dir.
    final cacheBase = (await getTemporaryDirectory()).path;   // /data/user/0/<package>/cache
    sqlite3.tempDirectory = cacheBase;

    // 4️⃣ Finally create a NativeDatabase **in the background isolate**
    // so heavy open() work never freezes the UI.
    return NativeDatabase.createInBackground(file);
  });
}
```

#### What each line achieves

| Code                                                 | Meaning                                                                                              |
| ---------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| `dart:io` imports                                    | Needed for `File`, `Platform` checks, and path ops                                                   |
| `drift/native.dart`                                  | Gives you `NativeDatabase` + `LazyDatabase` helpers                                                  |
| `path_provider`                                      | Abstracts “documents” and “cache” folders on Android/iOS/macOS/Linux/Windows                         |
| `path` (`as p`)                                      | `p.join()` builds correct paths on every OS                                                          |
| `sqlite3` / `sqlite3_flutter_libs`                   | Raw SQLite3 bindings bundled for every CPU arch                                                      |
| `LazyDatabase`                                       | Defers expensive async setup until the **first** query                                               |
| `getApplicationDocumentsDirectory()`                 | Returns a sandboxed folder that persists even after app restarts                                     |
| `applyWorkaroundToOpenSqlite3OnOldAndroidVersions()` | Fixes library‑loading bugs on very old Androids                                                      |
| `sqlite3.tempDirectory = ...`                        | Because `/tmp` is blocked on Android, SQLite would error out—this line points it to a safe cache dir |
| `NativeDatabase.createInBackground(file)`            | Opens the DB on a separate isolate so the main thread stays smooth                                   |

**Bottom line:** this helper guarantees that your SQLite file ends up in a safe, persisted location and that Android edge cases won’t crash startup.

### 3 b. Generate code

```bash
dart run build_runner build   # one‑off
dart run build_runner watch   # rebuild on save
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

### Live updates

```dart
Stream<List<Note>> watchAll() => db.select(db.notes).watch();
```

## 5. Offline‑first sync pattern (high level)

1. Write locally first → set `isSynced = false`.
2. Connectivity watcher (e.g. `connectivity_plus`) triggers sync when online.
3. Upload unsynced rows to Supabase (`upsert`).
4. On success, mark them `isSynced = true` and update timestamps.
5. Pull remote changes via Supabase Realtime and merge.
6. Resolve conflicts (`updatedAt` or a `version` column).

Wrap this in a `SyncService` that:

* Streams unsynced rows.
* Queues uploads when `hasInternet == true`.
* Applies remote patches inside a Drift transaction.

## 6. Migrations

1. Increment `schemaVersion` when you change tables.
2. Override `migrate()` in `AppDatabase`.
3. Use helpers (`createTable`, `addColumn`) to describe transitions.

## 7. Recommended next reads

* Drift docs: **Getting Started**, **Writing Queries**, **Migrations**.
* Supabase docs: Flutter client → *Realtime* and *Upsert*.
* Blog: *Offline‑first sync in Flutter with Drift + Supabase* (search).

### TL;DR

1. Add deps → run `build_runner`.
2. Define tables → generate code.
3. Use Drift APIs for local reads/writes.
4. Build a tiny sync layer to push/pull data to Supabase when online.

Happy coding! 🚀
