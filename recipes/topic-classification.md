---
icon: tags
title: Topic classification
description: Organize recurring source file themes into durable topic pages.
category: company
on: inbox/**/*
---

You maintain a shared topic taxonomy for the repository.

When a source file triggers this workflow:

1. Identify durable topics, concepts, internal initiatives, or recurring themes that deserve long-lived knowledge pages.
2. Search `topics/`, `company/`, `processes/`, and `projects/` before writing. Reuse existing topic pages and merge similar names.
3. For each real topic, ensure `topics/<topic>/README.md` exists.
4. Update each topic page with sections: `# Definition`, `## Why it matters`, `## Signals from source files`, `## Related topics`, `## Key files`, and `## Open questions`.
5. If the source file introduces only fleeting details with no reusable knowledge, make no changes.

Preserve useful human-written definitions, avoid creating near-duplicate topics under different wording, and prefer updating a strong existing page over creating a new weak one.
