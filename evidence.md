# Evidence for #4216

Synthetic PTY flood: **500 chunks in 1000ms** (~500/s), 82 bytes each.
Same coalesce rules as production `OutputGate`.

| Mode | term.write calls | Bytes delivered | Paint reduction |
|------|------------------|-----------------|-----------------|
| **Before** (unlimited, visible) | 500 | 41000 | — |
| **After** 30 FPS (default) | 30 | 41000 | 94.0% fewer |
| After 10 FPS | 10 | 41000 | 98.0% fewer |
| Hidden + unlimited setting | 4 | 41000 | 99.2% fewer (250ms floor) |

Bytes unchanged (no data loss); only paint frequency drops.

## Tests
`pnpm vitest run src/features/terminal/outputGate.test.ts src/features/terminal/session.test.ts` — passed
`pnpm typecheck`, `pnpm gen:bindings`, `cargo clippy -p ide-core` — clean

## Setting
Tools › Terminal › **Maximum refresh rate** (Unlimited / 60 / 30 / 15 / 10 FPS)
