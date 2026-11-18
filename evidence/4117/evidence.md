# Evidence for #4117

## Before
Full workbench: Project tool window + editor tab for `OrderBook.java` with unsaved `// unsaved #4117 marker`.

`before-detach.png`

## After
- `after-editor.png` — lightweight `editor-main-*` window: editor + tab only (no tool windows), same unsaved text, title `java-app — OrderBook.java`
- `after-main.png` — source tab removed from the project window after successful handoff

## Acceptance
- Open in New Window → aux editor (not a second workbench)
- Unsaved text preserved across the move
- Source tab removed only after the aux window reported ready
- Save in the aux window uses the shared project document (peer sync)

## Tests
```
pnpm vitest run src/editor/core/detachTab.test.ts src/platform/auxWindow.test.ts
cargo test -p openidea --lib windows::tests::auxiliary_windows_map_to_their_parent -- --exact
pnpm gen:bindings
```
