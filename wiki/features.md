# Features

## Editing
- **Overwrite typing** — Type a character to place it at the cursor and advance right.
- **Block cursor** — Blinking cursor that fills the current cell.
- **Arrow key navigation** — Move cursor cell-by-cell; camera follows to keep cursor visible.
- **Smart Enter** — Returns to the first populated cell of the current row, then moves down. Falls back to current column if the row is empty.
- **Backspace / Delete** — Erase the current cursor cell, or all cells in the current selection if one is active.
- **Escape** — Clears the current grid selection.
- **Tab** — Inserts two spaces.

## Viewport
- **Infinite grid** — No hard boundaries; the canvas expands conceptually as you type.
- **Panning** — Right-click drag to pan the camera. Mouse wheel scrolls vertically; Shift+wheel scrolls horizontally.
- **Click to place cursor** — Left-click a cell to move the cursor there.
- **Grid selection** — Left-click and drag to select a rectangular region of cells. Selection shown with blue highlight.
- **Font size slider** — Adjusts grid zoom dynamically (8px–48px).

## Import / Copy-Paste
- **Import Text button** — Opens a modal textarea; text is inserted at the current cursor position, line-by-line.
- **Internal copy/paste** — Select a region, then **Ctrl+C** to copy it to an internal buffer (also writes to system clipboard). **Ctrl+V** pastes the buffer starting at the cursor. Works like a spreadsheet.
- **System clipboard paste** — When no internal copy buffer exists, **Ctrl+V** reads from the system clipboard and inserts plain text at the cursor.

## Export
- **Export .txt** — Downloads a `.txt` file using the bounding-box trim rules (see [[architecture]]).
- **Export to Clipboard** — Copies the trimmed ASCII art directly to the system clipboard.

## Save / Load
- **Save** — Downloads a JSON blob containing the full cell map, camera position, cursor position, and font size.
- **Load** — Reads a previously saved JSON blob via file picker and restores the session.

## Undo / Redo
- **Undo (Ctrl+Z)** and **Redo (Ctrl+Shift+Z or Ctrl+Y)**.
- Maintains a stack of full grid snapshots (max 50).
- Toolbar buttons also available.

## UI
- **Dark theme** with faint grid lines for alignment.
- **Status bar** showing current row, column, and total cell count.
