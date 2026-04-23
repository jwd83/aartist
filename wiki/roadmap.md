# Roadmap

## Known Issues / Limitations
- **No line insertion or deletion.** There's no way to insert a blank row or delete a row and shift everything below up.
- **Undo snapshots are full-state.** At large grid sizes this could get memory-heavy. Differential snapshots would be more efficient.
- **No mobile support.** The editor assumes keyboard and mouse; touch input is untested.

## Future Ideas
- **Fill tool / rectangle draw.** Click-and-drag to draw lines or boxes with box-drawing characters (`│`, `─`, `┌`, etc.).
- **Selection mode.** Click-and-drag to select a rectangular region; cut, copy, paste within the grid.
- **Layer system.** Multiple layers that can be toggled on/off, merged, or reordered.
- **Color support.** ANSI color codes or HTML color overlay for each cell.
- **Template library.** Pre-built shapes, borders, or ASCII fonts that can be stamped onto the canvas.
- **Better font handling.** Allow user-selected web fonts or variable-width fallback handling.
- **Search / find within canvas.** Jump to a specific character sequence.
- **Collaboration.** CRDT-based multiplayer editing (ambitious, but fun).

## Open Questions
- Should the project stay strictly single-file, or is a small module-bundled version acceptable for advanced features?
- Is there value in a CLI companion tool (e.g., render ASCII art to PNG, or validate grid consistency)?
- Should exports support formats beyond `.txt` (e.g., `.ans` for ANSI art, `.html` for colored output)?
