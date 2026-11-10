---
type: Type
title: Docs Gap
icon: message-question
description: A question customers ask that the docs do not answer yet.
schema:
  type: object
  properties:
    state:
      type: string
      enum: [open, resolved]
      description: Whether the docs answer it now.
    area:
      type: string
      description: Product area.
    threads:
      type: array
      description: Support threads that asked it.
      items:
        type: string
        pattern: '^/support/[^/]+\.md$'
    thread_count:
      type: integer
      description: How many threads asked it.
      minimum: 0
    resolved_by:
      type: string
      pattern: '^/docs/.+\.md$'
      description: Docs page that answers it now.
---

A Docs Gap collects one unanswered question with the threads that asked it and a count, so the most asked gaps get fixed first.

- **Layer:** concept. Written by refinement workflows, which cite the records they read in `sources` and set `generated`. People review every change on its branch.
- **Folder:** `gaps/`
- **Filenames:** `gaps/<slug>.md`, like `gaps/webhook-retry-order.md`.
- **Refined from:** Support threads and docs pages.

Example frontmatter:

```yaml
type: Docs Gap
title: Are webhook retries delivered in order?
state: open
thread_count: 3
```
