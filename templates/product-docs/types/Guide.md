---
type: Type
title: Guide
icon: graduation-cap
description: A task-based page in the public docs.
schema:
  type: object
  properties:
    endpoints:
      type: array
      description: Endpoints the guide uses.
      items:
        type: string
        pattern: '^/docs/reference/[^/]+\.md$'
    audience:
      type: string
      description: Who the guide is for.
---

A Guide walks a reader through a task with the API, kept in step with the reference and with what customers ask.

- **Layer:** concept. Written by refinement workflows, which cite the records they read in `sources` and set `generated`. People review every change on its branch.
- **Folder:** `docs/guides/`
- **Filenames:** `docs/guides/<slug>.md`, like `docs/guides/track-a-shipment.md`.
- **Refined from:** API changes and docs gaps.

Example frontmatter:

```yaml
type: Guide
title: Track a shipment
endpoints: [/docs/reference/get-shipment.md]
```
