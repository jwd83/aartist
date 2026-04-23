# Clipboard

The editor supports two parallel clipboard systems: an internal grid buffer for structured copy/paste, and the system clipboard for text interchange.

## Internal Copy / Paste

- **Ctrl+C** with an active selection copies the selected region to `clipBuffer`.
- **Ctrl+V** with a non-null `clipBuffer` pastes it at the cursor position.
- The buffer stores a sparse `Map` keyed by relative offsets (`"dr,dc"`) and preserves spaces.

This behaves like a spreadsheet: relative positioning is maintained, and the paste can be repeated.

## System Clipboard

- **Export to Clipboard** toolbar button copies the bounding-box-trimmed art via `navigator.clipboard.writeText()`.
- **Ctrl+V** with no internal buffer falls back to `navigator.clipboard.readText()`, inserting plain text at the cursor via `importText()`.
- Browser `paste` events are also intercepted globally when the modal is closed.

## Related

- [[features]] — Copy, paste, and import controls
- [[architecture]] — Data model and state management
- [[export]] — Bounding-box trim rules
