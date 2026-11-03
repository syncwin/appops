# Projects, sync and Git (Nowa 3.16.4)

## Project types
- **Local project**: a Flutter folder on disk, available on every plan through Nowa Desktop. Create: Desktop → Local Projects → New Local Project. The default folder is set in settings; choose one under the user's dev folder.
- **Desktop settings** (Settings → Editor settings): *Local setup* holds Flutter SDK Path, Default Projects Path and VS Code path (point them at the existing installs; skip "Set up automatically", which downloads its own Flutter). *Git* holds GitHub Integration, Legacy Remote Credentials and External Local Credentials; the user connects GitHub there.
- **Cloud project**: stored by Nowa; Settings → Project Sync copies cloud ↔ local in one click (not Git).
- **Workspaces / monorepos** (3.12+): import a local repo and pick the package; the package shows under its own name in Recents (3.16.4).

## What Nowa adds
`.nowa/`: `comments.json`, `settings.json` (board theme), `run.local` (git-ignored run args), a temp cache. Commit `.nowa/comments.json` and `settings.json`; ignore `run.local` and the cache. Nowa AI never edits `.nowa/`, `Info.plist` or `AndroidManifest.xml` directly (3.15); platform permissions go through Nowa settings.

## Two-way sync with an IDE
Open the same folder in VS Code or Claude Code; "changes sync instantly both ways". Since 3.15 Nowa hot-reloads outside edits once writes settle. A `pubspec.yaml` change asks for a new run.

## Round-trip rules (code edited outside Nowa)
1. Save & Commit in Nowa before anyone edits files (Git actions auto-save first since 3.16.4).
2. Keep widget trees declarative. A widget built by `_buildX()` helper methods shows as a sealed box Nowa can't edit; split into widget classes.
3. Annotations (`@JsonSerializable`, `@JsonKey`, `@HiveType`, `@pragma`) survive since 3.15; stay on 3.16.4 or later.
4. Recently fixed save-path bugs: `const`, `async*`/`sync*`, record destructuring in `for` loops (3.16.4); `!`/`?.`, closure types, extension modifiers (3.15). Expect edge cases with new Dart syntax: run the developer plugin's gate (`flutter analyze`) after every Nowa save.
5. Keep generated code (freezed, drift, riverpod_generator) in packages Nowa doesn't open.
6. Don't let Nowa and a person edit platform files at the same time.

## Git panel
Commit, pull, merge, checkout, revert; Save & Commit (3.16.4); SSH (3.12); several GitHub accounts (3.16.2); switching branches without committing first (3.12.5); pull refuses to overwrite uncommitted changes (3.15). The branch shows `*` when dirty and ↑↓ counts. GitHub integration (cloud) is on higher plans; local Git works on every plan.

Workflow: pull → new branch per task (`ui/<task>`) → edit in Nowa and/or code → Save & Commit → push and open a PR (push needs the user's yes) → the developer plugin's CI gate.
