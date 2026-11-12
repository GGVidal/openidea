# #2991 manual verify

## Setup
- `pnpm tauri dev` (MCP bridge :9223)
- Fixture: `.scratch/2991-ligatures/fixture/ligatures.ts` (`!==`)
- Find in Files → query `!==`

## What we checked
1. Live Find dialog with committed fix: `:root` / result `.tok-operator` / preview `.cm-scroller` all compute `font-variant-ligatures: none`.
2. With injected Fira Code (ligature-capable font), pixel-diff of Find dialog:
   - bug (results ligatures forced on) vs fix-variant (`font-variant-ligatures: none`): **164 px differ** in the results `!==` glyph box `(63,126)-(84,137)`.
   - fix-variant vs fix-features (`+ font-feature-settings`): **identical** → variant-only fix is enough.
3. Ligature board (`ligature-board-crop.png`) shows Fira Code ON vs OFF for `!==`.

## Evidence
- `after-dialog.png` — Find UI with ship fix (JetBrains Mono)
- `bug-dialog.png` / `fix-variant-dialog.png` — Fira Code A/B
- `bug-glyph-zoom.png` / `fix-variant-glyph-zoom.png` — cropped `!==` delta
- `ligature-board-crop.png` — font feature probe
