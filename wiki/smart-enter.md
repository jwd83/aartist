# Smart Enter

The Enter key implements a newline behavior optimized for ASCII art drawing.

## Behavior

1. Determine the **first populated cell** of the current row (scanning left to right, ignoring whitespace-only cells).
2. If found, move the cursor to that column.
3. Move the cursor down one row.
4. If the current row is empty, fall back to the cursor's current column.

## Rationale

When drawing shapes line by line, artists often start each line at the same horizontal offset. Smart Enter avoids the need to manually reposition the cursor to the left edge of the drawn content on every new line.

## Related

- [[features]] — Editing controls
- [[architecture]] — Input handling
