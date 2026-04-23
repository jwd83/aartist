# ASCII Art Designer (aartist)

A single-file, portable HTML ASCII art editor. Open directly in any browser. No build step, no dependencies, no server required.

## Goal
Make it trivial to create, edit, and export ASCII art. The editor should feel like a text editor mapped onto an infinite 2D grid — click to place a cursor, type to draw, pan around freely.

## Status
**Functional MVP.** Core editing, import/export, save/load, undo/redo, and clipboard copy all work. The app is a single self-contained HTML file that opens anywhere.

## Key Files
- `index.html` — The entire application (CSS + JS inline)
- `design.md` — Original design document capturing session decisions
- `wiki/` — This knowledge base

## Related
- [[features]] — Full capability list
- [[architecture]] — Technical design and data model
- [[roadmap]] — Known issues and future direction

## Philosophy
- **Portability over features.** One file, zero dependencies, works offline.
- **Grid-native.** ASCII art is inherently grid-based; the UI should reflect that.
- **Preserve intent.** Internal whitespace is kept on export, but edges are trimmed to keep exports clean.
