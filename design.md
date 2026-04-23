# ASCII Art Designer — Design Document

## Overview
A single-file, portable HTML ASCII art editor. Open directly in any browser. No build step, no dependencies, no server required.

---

## Architecture & Packaging
- **Single self-contained `.html` file** with inline CSS and JavaScript.
- Opens via `file://` or any static host.
- Zero external dependencies.

---

## Rendering
- **Virtual viewport** into an infinite grid. No native scrollbars.
- **Grid lines**: rendered via CSS `background-image` pattern (infinite, performant).
- **Characters**: absolutely positioned `<span>` elements only for cells inside the current viewport.
- **Camera**: stored as cell offset (`camRow`, `camCol`).
- **Panning**: drag the background; arrow keys move the cursor and camera follows.

---

## Theme & Typography
- **Theme**: Dark (dark background, light text, faint grid lines).
- **Font**: Fixed system monospace stack (`Courier New`, Consolas, `monospace`).
- **Zoom**: Toolbar slider adjusts font size dynamically.

---

## Input & Cursor
- **Cursor style**: Blinking block cursor filling the cell.
- **Typing mode**: Overwrite. Type to replace the cell and advance right.
- **Navigation**: Arrow keys move cursor cell-by-cell.
- **Enter key**: Smart newline. Returns to the first populated cell of the current row, then moves down one. If the row is empty, falls back to current column.
- **Backspace**: Clears cell to the left, moves cursor left.
- **Delete**: Clears current cell, cursor stays.

---

## Data Model
- **Sparse `Map`** keyed by `"row,col"` storing single characters.
- Empty/absent cells are truly empty.
- **Explicit spaces are stored** so internal whitespace is preserved in exports.
- **Spaces do NOT count** as "filled" when computing export edges.

---

## Import / Paste
- **Paste button**: Opens a modal textarea. Text inserted at current cursor position, line-by-line.
- **Clipboard paste** (`Ctrl+V`): Intercepted when canvas is focused to insert plain text directly.

---

## Export Rules
Bounding box computed from non-whitespace characters:
- `minRow`, `maxRow`, `minCol` are global.
- **Right edge is per-row**: each row trimmed to its last non-whitespace character.
- All rows between `minRow` and `maxRow` exported. Empty rows become blank lines.
- All stored characters (including intentional spaces) inside the per-row window preserved.

---

## Save / Load / Export
- **Save**: Downloads a JSON blob containing cell map, camera position, cursor position, font size.
- **Load**: Reads JSON blob back via file picker.
- **Export**: Downloads a `.txt` file using bounding-box rules above.

---

## Editing Conveniences
- **Undo/Redo**: Stack storing full grid snapshots. `Ctrl+Z` / `Ctrl+Shift+Z`.
- **Status bar**: Displays cursor coordinates.
