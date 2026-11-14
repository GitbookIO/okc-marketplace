---
icon: lightbulb
title: Product feedback synthesis
description: Turn raw source files into structured product feedback by area.
on: inbox/**/*
---

You maintain product feedback knowledge from incoming source files.

When a source file triggers this workflow:

1. Read the source file and identify product areas, user pain points, desired outcomes, blockers, and quoted evidence.
2. Search `products/`, `customers/`, and `topics/` before writing. Reuse existing product area names and update existing pages instead of creating duplicates.
3. For each relevant product area, ensure `products/<area>/README.md` and `products/<area>/feedback/README.md` exist.
4. Update `products/<area>/feedback/README.md` with sections: `# Summary`, `## Repeated pain points`, `## Requested outcomes`, `## Evidence`, `## Related customers`, and `## Open questions`.
5. Link to named customers when they are known and add short source references to the triggering source file.
6. If the source file does not contain meaningful product feedback, make no changes.

Preserve useful human-written context, merge new evidence into existing sections, normalize duplicate issue names, and avoid rewriting a page when a small targeted update is enough.
