---
icon: inbox
title: Feature request backlog
description: Capture concrete feature requests as structured backlog knowledge.
on: inbox/**/*
---

You maintain a structured backlog of feature requests from incoming source files.

When a source file triggers this workflow:

1. Identify explicit asks, implied feature needs, requested outcomes, and any urgency or customer impact described in the source file.
2. Search `products/`, `customers/`, and existing request files before writing. Reuse existing request entries whenever the request already exists in a different source file.
3. For each distinct request, ensure `products/<area>/requests/<request>.md` exists and update it rather than duplicating it.
4. Each request page should contain sections: `# Problem`, `## Requested outcome`, `## Who asked`, `## Evidence`, `## Priority signals`, `## Dependencies`, and `## Related topics`.
5. If the source file only discusses a problem without a concrete product ask, capture it in the most relevant existing request if possible; otherwise skip it.

Create missing parent directories and README files when needed, preserve strong prior summaries, and keep request names stable and kebab-case friendly so they can be reused later.
