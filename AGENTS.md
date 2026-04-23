# aartist Wiki Schema

This document defines the structure, conventions, and workflows for maintaining the ASCII Art Designer wiki.

## Directory Layout

```
/wiki/
  index.md        — Catalog of all pages with links and summaries
  log.md          — Append-only chronological activity log
  overview.md     — Project purpose, goals, current status
  architecture.md — Technical design, data model, rendering
  features.md     — Feature inventory and behavior specs
  roadmap.md      — Known issues, future ideas, open questions
  export.md       — Export algorithm and bounding-box rules
  smart-enter.md  — Smart Enter key behavior spec
  clipboard.md    — Internal and system clipboard operations
```

## Conventions

- All wiki pages are Obsidian-flavored markdown with `[[wiki-link]]` syntax.
- Each page should link to at least 2 other wiki pages where relevant.
- Use `##` for top-level sections, `###` for subsections.
- Code references should match actual variable/function names from `index.html`.
- Keep claims accurate — if a feature ships, move it out of "Future Ideas" immediately.

## Workflows

### Ingest
When new features or changes are made to `index.html` or `design.md`:
1. Append an entry to `log.md` with format `## [YYYY-MM-DD] type | Brief description`
2. Update relevant behavior/spec pages (`features.md`, `architecture.md`, etc.)
3. Update `index.md` if new pages are created
4. Move shipped items from `roadmap.md` "Future Ideas" to "Recently Shipped"

### Query
When answering questions about the project:
1. Read `index.md` first to locate relevant pages
2. Read those pages, then synthesize with citations
3. If the answer reveals a new connection or concept, file it back into the wiki

### Lint
Periodically check for:
- Stale claims (shipped features still listed as future)
- Missing cross-references
- Orphan concepts mentioned but not paged
- Inaccurate statistics (line counts, etc.)
- Log gaps (missing entries for significant changes)
