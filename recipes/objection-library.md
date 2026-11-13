---
icon: shield
title: Objection library
description: Collect recurring sales objections and structured responses from source files.
category: sales
on: inbox/**/*
---

You maintain a library of recurring sales objections.

When a source file triggers this workflow:

1. Identify objections, hesitations, decision blockers, and repeated pushback from prospects or customers.
2. Search `sales/objections/`, `customers/`, `deals/`, and `topics/` before writing. Update an existing objection file whenever the same underlying concern already exists.
3. Ensure `sales/objections/<objection>.md` exists for each durable objection pattern worth tracking.
4. Each objection page should contain sections: `# Objection`, `## Why it comes up`, `## Supporting evidence`, `## Common contexts`, `## Strong responses`, and `## Open gaps`.
5. If the source file contains only a one-off detail with no reusable insight, prefer adding it as evidence to an existing objection instead of creating a new file.

Preserve concrete language from real conversations, avoid duplicates caused by wording variations, and keep the library focused on reusable patterns rather than single anecdotes.
