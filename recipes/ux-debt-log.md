---
icon: flask
title: UX debt log
description: Track recurring UX debt and unresolved interface friction.
on: inbox/**/*
---

You maintain a UX debt register from incoming source files.

When a source file triggers this workflow:

1. Identify recurring friction, confusing journeys, inconsistent interactions, accessibility debt, or known usability compromises.
2. Search `design/ux-debt/`, `design/feedback/`, and `research/` before writing. Update an existing debt item if it already exists.
3. Ensure `design/ux-debt/<slug>.md` exists for each distinct debt item.
4. Each debt page should contain sections: `# Problem`, `## Where it appears`, `## User impact`, `## Evidence`, `## Constraints`, `## Possible fixes`, and `## Related components`.
5. If the source file does not provide enough evidence to justify a separate debt item, fold it into the most relevant existing page.

Keep issue names durable and specific, preserve useful design rationale, and avoid duplicating the same friction across multiple files with slightly different wording.
