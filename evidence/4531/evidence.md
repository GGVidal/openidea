# Evidence for #4531

## Settings › Compiler
`after-settings.png` — new **Open / Focus Build tool window** selects (defaults Always / Never).

## Build with Open = Never
`after-build-never.png` — Build Project finished; Build tool window stayed closed; focus remained on the editor/project.

## Tests
```
pnpm vitest run src/features/build/build.test.tsx src/platform/workflowSettings.test.ts src/platform/locales/textCatalog.test.ts
pnpm gen:bindings
```
