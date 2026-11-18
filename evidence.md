# Evidence for #4352 / PR #4365

## Before
Open In offered only Finder/Explorer and Terminal.

## After
- **Associated Application** — OS default (`fs_open_with_system(path, null)`)
- **Choose Application…** — native picker, then `fs_open_with_system(path, application)`

Also on editor tab › Open In and Find Action.

## Tests
```
pnpm vitest run src/features/project-tree/contextMenu.test.ts \
  src/platform/fileManager.test.ts src/platform/locales/textCatalog.test.ts
cargo test -p openidea --lib commands::fs::tests
pnpm gen:bindings
```
