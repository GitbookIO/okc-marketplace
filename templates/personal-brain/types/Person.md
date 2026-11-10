---
type: Type
title: Person
icon: person
description: Someone a person meets or reads, in a personal repo only.
schema:
  type: object
  properties:
    role:
      type: string
      description: What they do.
    organization:
      type: string
      description: Where they work.
    aliases:
      type: array
      description: Other names they go by.
      items:
        type: string
---

A Person page keeps what one person knows about someone they meet or read. It only appears in personal repos, never in company ones.

- **Layer:** concept. Written by refinement workflows, which cite the records they read in `sources` and set `generated`. People review every change on its branch.
- **Folder:** `people/`
- **Filenames:** `people/<slug>.md`, like `people/rosa-lind.md`.
- **Refined from:** Sources and meetings.

Example frontmatter:

```yaml
type: Person
title: Rosa Lind
role: Researcher
```
