# Evidence for #4574

## Manual runtime probe (Tauri MCP)

With a 2-file Commit selection set, `deployment.actionTargets(undefined)` (shortcut path, no menu arg):

| Focus | `actionTargets` |
|-------|------------------|
| Project tool window | does **not** use Commit multi-select |
| Commit tool window | returns **both** selected paths |

See `contrast.json`. Screenshot: `after-commit-window.png`.

## Automated
```
pnpm vitest run src/features/deployment/
```
