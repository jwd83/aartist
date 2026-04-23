# Export

The export system trims ASCII art to a tight bounding box while preserving intentional internal whitespace.

## Algorithm

1. Scan all cells for non-whitespace characters.
2. Compute global bounds:
   - `minRow`, `maxRow` — top and bottom edges
   - `minCol` — leftmost non-whitespace column
3. For each row, compute a **per-row right edge**: the last non-whitespace column in that row.
4. Emit every row from `minRow` to `maxRow`.
   - If a row has no non-whitespace cells, emit a blank line.
   - Otherwise emit from `minCol` to the per-row right edge, using stored characters (including spaces).

## Preserving Intent

Explicitly stored spaces inside the bounding box are kept. Only the **edges** are trimmed. This means ASCII art with internal gaps renders correctly on export.

## Related

- [[architecture]] — Data model and rendering
- [[features]] — Export .txt and Export to Clipboard buttons
- [[roadmap]] — Future format support (.ans, .html)
