---
type: Type
title: Source
icon: paperclip
description: Something a person saved to read or remember, one file per item.
schema:
  type: object
  properties:
    kind:
      type: string
      enum: [article, note, link]
      description: Article, own note, or bare link.
    captured_at:
      type: string
      format: date-time
      description: When it was saved.
    author:
      type: string
      description: Who wrote the original, if known.
  required: [kind, captured_at]
---

A source is one saved item: an article, a note, a link. The body holds a short summary and the original text or a pointer to it.

- **Layer:** record. Written by ingest workflows, one file per source event. Refinements read records and never edit them.
- **Folder:** `sources/`
- **Filenames:** `sources/<date>-<slug>.md`, like `sources/2026-11-02-llm-wiki.md`. Mocks are `sources/mock-<n>.md` with `resource: mock://sources/<n>`.
- **Ingested from:** `inbox/`, browser clips, Readwise, agents connected over MCP.

Example frontmatter:

```yaml
type: Source
title: Notes on compiled wikis
resource: mock://sources/6
kind: article
captured_at: 2026-11-02T19:30:00Z
```
