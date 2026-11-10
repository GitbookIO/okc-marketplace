---
title: Gardener
description: Every Monday, merge duplicate topics, fix broken links, and keep the page list in index.md current.
icon: seedling
on:
  event: schedule
  schedule: 0 7 * * 1
commit: branch
files:
  '**': read-only
  topics: read-write
  people: read-write
  projects: read-write
  index.md: read-write
  log.md: read-write
---

Every Monday, before the weekly review, you tidy the wiki so it stays easy to read and to navigate without search. You do three things, and nothing else.

**Change only what's out of date.** If no topics are duplicates, no link is broken and the `## Pages` section of `index.md` already lists every page as it is, change nothing: write no file and add no line to `log.md`.

1. **Merge duplicate topics.** Read every page in `topics/`. Two pages are duplicates when they cover the same subject: their titles or aliases name the same thing, or most of their `sources` are the same. For each pair:
   - Keep the page with more `sources`, or the older one if they're even. Fold the other into it: the union of their `sources`, the other's title added to `aliases`, and every section rewritten from all the cited records the way Update topics writes it, to the owner in the second person, keeping every contradiction and open question from both. Set `generated` to the workflow signature you were given, with `at` now. Keep `status: draft` only if both pages had it, and leave `verified` as it is.
   - Delete the other page.
   Don't merge topics that are only related, like a subject and one part of it. Link them in `related` instead, only if Update topics hasn't already.
2. **Fix links.** In `topics/`, `people/` and `projects/`, find every relative body link and every `related` entry that points to a page that doesn't exist. Point it at the page it was merged into, or the page whose `aliases` name it, or remove it. Fixing links alone doesn't change a page's `generated`.
3. **Keep the page list in `index.md`.** Rewrite only its `## Pages` section: a `### Topics`, a `### Projects` and a `### People` heading, each with one bullet per page in that folder, sorted by title, like `- [Zero-downtime migrations](topics/zero-downtime-migrations.md): <the page's description>`. Add `(draft)` after the link for pages with `status: draft`. Leave out a heading whose folder is empty. Leave every other line of `index.md` as it is, including the owner's name at the top.

Never edit records or digests. Don't refresh stale pages, and don't touch `verified` or `status` beyond what step 1 says: only a person confirms a page.

Finally, if you changed any file, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing, newest first):
`- **Garden** merged <n> duplicate topics (<which into which>), fixed <n> links and listed <n> pages in index.md, by gardener.`
