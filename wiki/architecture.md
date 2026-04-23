# Architecture

## Packaging
The entire application is a single self-contained `.html` file with inline CSS and JavaScript. This is a deliberate choice for maximum portability — it opens via `file://` without any build step, server, or external dependencies.

## Rendering
- **Virtual viewport** into an infinite grid. No native scrollbars.
- **Grid lines** rendered via CSS `background-image` with `linear-gradient` patterns. The pattern is sized to match the current cell dimensions, so it scales with the font size slider.
- **Characters** rendered as absolutely positioned `<span>` elements, but only for cells inside the current viewport (virtualized rendering).
- **Camera** stored as cell offsets (`camRow`, `camCol`). Panning adjusts these offsets; rendering translates the visible subset into screen coordinates.

## Rendering Details
- **Grid sizing** is dynamic. A hidden `<span id="measure">M</span>` measures actual font metrics, and CSS custom properties (`--cell-w`, `--cell-h`, `--font-size`) drive the grid pattern and cell positioning.
- **`user-select: none`** and `-webkit-user-select: none` on the viewport prevent browser text selection during drag interactions.

## Data Model
- Sparse `Map` keyed by `"row,col"` strings storing single characters.
- Empty/absent cells are truly empty.
- **Explicit spaces are stored** so internal whitespace is preserved in exports.
- **Spaces do NOT count** as "filled" when computing export bounding boxes.

## State Management
All state lives in simple module-level variables:
- `cells` — the Map of grid content
- `cursorRow`, `cursorCol` — cursor position
- `camRow`, `camCol` — camera/viewport offset
- `fontSize`, `cellW`, `cellH` — typography metrics
- `historyStack`, `historyIdx` — undo/redo snapshots
- `clipBuffer` — internal copy buffer for structured grid copy/paste (see [[clipboard]])

There is no framework; state changes call `render()` directly.

## Input Handling
All keyboard input is handled on `document` with a single `keydown` listener. Mouse interactions (click-to-place, drag-to-pan) are handled on the viewport element. Clipboard paste is intercepted globally when the modal is closed.

## Export Logic
The export algorithm computes a bounding box from non-whitespace characters:
- `minRow`, `maxRow`, `minCol` are global across all non-whitespace cells.
- **Right edge is per-row**: each row is trimmed to its last non-whitespace character.
- All rows between `minRow` and `maxRow` are exported. Empty rows become blank lines.
- Stored characters (including intentional spaces) inside the per-row window are preserved.

See [[export]] for the full algorithm and rationale.
