## [2026-04-22] init | Project created and initial build

Created the ASCII Art Designer project. Built a single-file HTML editor with the following decisions:
- Self-contained `.html` file for maximum portability
- Virtual infinite grid with DOM-based rendering
- Dark theme with system monospace font
- Overwrite typing mode with block cursor
- Sparse Map data model keyed by `row,col`
- Per-row right-edge trimming on export
- Smart Enter key (returns to first populated cell of row)

Built `ascii-designer.html` and `design.md`.

## [2026-04-22] feature | Export to clipboard + delete behavior fix

Two small adjustments:
1. Added **Copy** button that copies trimmed ASCII art to system clipboard via `navigator.clipboard`.
2. Changed Backspace and Delete to both erase the **current cursor cell** without moving the cursor (previously Backspace moved left and deleted the cell behind).

## [2026-04-22] feature | Grid selection + drag fix

Major interaction overhaul:
1. **Grid selection** — Left-click and drag to select a rectangular region of cells. Visual highlight with blue overlay. Selection dimensions shown in status bar.
2. **Fixed left-click drag jank** — Added `user-select: none` to viewport to prevent browser text selection during drag.
3. **New input model**:
   - Left-click = place cursor
   - Left-click drag = select region
   - Right-click drag = pan camera
   - Shift+wheel = horizontal pan
4. **Selection operations** — Escape clears selection. Backspace/Delete clears all cells inside the active selection.
