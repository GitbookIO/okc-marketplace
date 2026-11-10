---
title: Staleness sweep
description: Every week, list the pages past their review date on the Team page of the team that owns them.
icon: hourglass-half
on:
  event: schedule
  schedule: 0 7 * * 1
commit: branch
files:
  '**': read-only
  teams: read-write
  log.md: read-write
---

Every Monday, before the digest, you find the pages nobody has confirmed in time and tell the team that owns each one. A page goes stale when its `stale_after` date passes without new records to update it or a person to verify it.

**Change only what's out of date.** If no `## Needs review` section would change, write no file and add no line to `log.md`.

1. Read every page in `customers/`, `projects/`, `decisions/` and `teams/`. A page is stale when its `stale_after` is before now. Skip pages without one.
2. Find the team that owns each stale page:
   - A project: its `team`.
   - A customer: the teams of the projects whose `customers` list it. If none, the team whose `lead` is the customer's `owner`.
   - A decision: the team of the project its source meetings link. If none, the team whose `channel` is the channel of its source discussions.
   - A team: the team itself.
   If no team owns it, list it in the log line instead.
3. In each Team page, replace the `## Needs review` section with one line per stale page it owns, oldest first: `- [<title>](<relative path>): past its review date since <D Month>, last written by <workflow or person>.` Write `Nothing right now.` when the team owns none. If the page has no such section, add it at the end.

Change nothing else. Don't edit stale pages, `generated`, `verified`, `status` or any other section of a Team page: only a person or a separate check confirms a page, by adding to `verified`. Don't create Team pages.

Finally, if you changed any file, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing):
`- **Sweep** <n> stale pages for <team titles>, unowned: <page titles or none>, by staleness-sweep.`
