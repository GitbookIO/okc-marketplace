---
type: Type
title: Changelog Entry
icon: clock-rotate-left
description: One change to the public API, as readers of the docs see it.
schema:
  type: object
  properties:
    date:
      type: string
      format: date
      description: When the change reached the API spec on the default branch.
    api_version:
      type: string
      description: The spec's info.version after the change.
    change:
      type: string
      enum: [added, changed, deprecated, removed, fixed]
      description: Kind of change.
    breaking:
      type: boolean
      description: Whether existing integrations must change.
    endpoints:
      type: array
      description: Reference pages for the operations it changes.
      items:
        type: string
        pattern: '^/docs/reference/[^/]+\.md$'
  required: [date, change]
---

A Changelog Entry says what changed in the API, when, and what integrations need to do about it. Each entry is its own page, so two spec changes on separate branches never conflict. Files are named by date, so the folder reads as the changelog.

- **Layer:** concept. Written by refinement workflows, which cite the records they read in `sources` and set `generated`. People review every change on its branch.
- **Folder:** `docs/changelog/`
- **Filenames:** `docs/changelog/<date>-<slug>.md`, like `docs/changelog/2026-11-03-signature-required.md`.
- **Refined from:** `api/openapi.yaml` and the pull requests behind each change.

Example frontmatter:

```yaml
type: Changelog Entry
title: Ask for a signature on delivery
date: 2026-11-03
api_version: 1.14.0
change: added
breaking: false
endpoints: [/docs/reference/create-shipment.md]
```
