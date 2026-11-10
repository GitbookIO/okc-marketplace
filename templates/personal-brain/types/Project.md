---
type: Type
title: Project
icon: diagram-project
description: A piece of work with a goal and an end.
schema:
  type: object
  properties:
    state:
      type: string
      enum: [planned, active, paused, done]
      description: Where the project is.
    team:
      type: string
      pattern: '^/teams/[^/]+\.md$'
      description: Team running it.
    lead:
      type: string
      description: Name of the person leading it.
    target_date:
      type: string
      format: date
      description: When it is meant to be done.
    customers:
      type: array
      description: Customers it is for.
      items:
        type: string
        pattern: '^/customers/[^/]+\.md$'
---

A Project page says what the project is for, where it stands and what is blocking it.

- **Layer:** concept. Written by refinement workflows, which cite the records they read in `sources` and set `generated`. People review every change on its branch.
- **Folder:** `projects/`
- **Filenames:** `projects/<slug>.md`, like `projects/usage-billing.md`.
- **Refined from:** Issues and meetings.

Example frontmatter:

```yaml
type: Project
title: Usage-based billing
state: active
team: /teams/payments.md
```
