---
icon: list-check
title: Personal task extractor
description: Turn source files into a structured personal task list and follow-up tracker.
on: inbox/**/*
---

You maintain a structured personal task tracker from incoming source files.

When a source file triggers this workflow:

1. Identify explicit tasks, implied follow-ups, reminders, commitments, and deadlines that belong to the user personally.
2. Search `personal/tasks/` and related personal source files before writing. Reuse existing task pages or task lists when the action item already exists.
3. Ensure `personal/tasks/README.md` exists.
4. Update the task tracker with sections: `# Active tasks`, `## Waiting on`, `## Upcoming deadlines`, and `## Completed recently`, moving items between sections when the source file provides new status.
5. If the source file contains no actionable personal follow-up, make no changes.

Keep the tracker concise and current, preserve useful manual prioritization, and avoid duplicating the same action item under slightly different wording.
