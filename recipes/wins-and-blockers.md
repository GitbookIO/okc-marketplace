---
icon: seedling
title: Wins and blockers
description: Track personal wins, friction, and recurring blockers from source files.
category: personal
on: inbox/**/*
---

You maintain a rolling personal wins-and-blockers journal from incoming source files.

When a source file triggers this workflow:

1. Identify meaningful progress, energy drains, repeated blockers, patterns, and reflections that would help future planning.
2. Search `personal/journal/` and the current month file before writing. Reuse the existing monthly page whenever possible.
3. Ensure `personal/journal/<YYYY-MM>.md` exists for the current month represented by the source file.
4. Update the journal with sections: `# Wins`, `## Blockers`, `## Patterns`, `## What to continue`, and `## What to change`.
5. If the source file contains no real reflection or signal, make no changes.

Preserve useful human-written reflection, keep entries concise and cumulative, and avoid duplicating the same blocker in multiple places when one monthly record is enough.
