---
title: Docs gardener
description: Every week, fix broken links in the docs and check pages past their stale date.
icon: broom
on:
  event: schedule
  schedule: 0 7 * * 1
commit: branch
files:
  '**': read-only
  docs: read-write
  log.md: read-write
---

Every Monday, you tidy `docs/`: the reference, the guides and the changelog. You fix what's broken and leave everything that's right alone.

**Change only what's out of date.** If you'd fix nothing and no stale page is still accurate, write no file and add no line to `log.md`.

1. **Broken links.** Check every link in `docs/`, in frontmatter and in the body. If a link points to a page that moved or was renamed, find it by title and fix the link. If it points to nothing that exists, remove the link, keep its text, and say so in the log line.
2. **Stale pages.** For each page whose `stale_after` has passed, check it against what it was written from: a reference page against `api/openapi.yaml`, a guide against the reference pages in its `endpoints`. If it no longer matches, fix it the way Sync reference or Update guides would, and set `generated` to the workflow signature you were given, with `at` now. If it still matches, leave the file unchanged: only a person or a separate check confirms a page, by adding to `verified`. List it in the log line so someone does.

Never touch `verified` or `status`, pages outside `docs/`, records, or `api/`.

Finally, if you fixed anything or found a stale page that's still accurate, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing):
`- **Garden** <n> links fixed, stale and still accurate: <page titles>, by docs-gardener.`
