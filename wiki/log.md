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

## [2026-04-22] feature | Internal copy/paste + rename

1. **Internal copy/paste** — Select a region, **Ctrl+C** copies it to an internal buffer (and system clipboard). **Ctrl+V** pastes the buffer at the cursor. Behaves like a spreadsheet. Falls back to system clipboard paste when no internal buffer exists.
2. **Renamed toolbar button** — "Copy" is now "Export to Clipboard" for clarity.

## [2026-04-23] lint | Wiki health check and cleanup

Ran a full lint pass on the wiki. Issues found and fixed:
- Moved shipped features (grid selection, internal copy/paste) out of roadmap Future Ideas
- Corrected stale line-count claim and filename reference in overview
- Added missing cross-references across all pages
- Created new pages: [[export]], [[smart-enter]], [[clipboard]]
- Added missing architectural details (measureEl, CSS vars, user-select, clipBuffer)
- Added [[AGENTS.md|schema document]] defining wiki conventions and workflows
