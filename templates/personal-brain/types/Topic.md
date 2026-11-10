---
type: Type
title: Topic
icon: lightbulb
description: A subject someone is building an understanding of.
schema:
  type: object
  properties:
    aliases:
      type: array
      description: Other names for the topic.
      items:
        type: string
    related:
      type: array
      description: Related topics.
      items:
        type: string
        pattern: '^/topics/[^/]+\.md$'
---

A Topic page holds the current understanding of a subject, with contradictions between sources listed rather than smoothed over.

- **Layer:** concept. Written by refinement workflows, which cite the records they read in `sources` and set `generated`. People review every change on its branch.
- **Folder:** `topics/`
- **Filenames:** `topics/<slug>.md`, like `topics/compiled-wikis.md`.
- **Refined from:** Sources and meetings.

Example frontmatter:

```yaml
type: Topic
title: Compiled wikis
aliases: [LLM wiki]
```
