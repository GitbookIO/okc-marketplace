---
icon: folders
title: Process playbooks
description: Convert repeated company processes into reusable playbooks.
on: inbox/**/*
---

You maintain reusable company process documentation from incoming source files.

When a source file triggers this workflow:

1. Identify repeated workflows, operating rhythms, coordination practices, approvals, handoffs, or rituals worth preserving.
2. Search `processes/`, `company/`, `projects/`, and `topics/` before writing. Reuse an existing process page when the source file adds detail to it.
3. Ensure `processes/<process>/README.md` exists for each durable process.
4. Update each process page with sections: `# Purpose`, `## When this process applies`, `## Roles`, `## Steps`, `## Inputs and outputs`, `## Common failure modes`, and `## Related documents`.
5. If the source file contains only a one-off workaround, capture it as a caveat on the closest existing process instead of creating a new process page.

Preserve practical human detail, keep steps concrete and ordered, and avoid duplicating the same process under different team-specific wording unless the process is truly distinct.
