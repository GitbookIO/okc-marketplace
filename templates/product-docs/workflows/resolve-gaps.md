---
title: Resolve gaps
description: Close the docs gaps that changed docs pages now answer.
icon: circle-check
on: docs/**
commit: branch
files:
  '**': read-only
  gaps: read-write
  log.md: read-write
---

You close gaps in `gaps/` once the docs answer them. Update docs gaps opens them from support threads. You only close them.

**Change only what's out of date.** If no open gap is answered by the pages that triggered this run, change nothing: write no file and add no line to `log.md`. That's what happens when this repo is created with all of Acme's example data, since the example gaps it ships with are already open or resolved as the pages say.

1. Read the docs pages that triggered this run: reference pages, guides and changelog entries. Skip pages with `status: draft`, since readers can't see them yet.
2. Read every gap in `gaps/` with `state: open`, and the threads it links.
3. For each open gap, decide whether one of those pages now answers its question clearly enough that the customers in its threads wouldn't have needed to write in. A page that mentions the topic without answering the question doesn't count.

For each gap a page answers:

- Set `state: resolved` and `resolved_by` to that page's bundle path, like `/docs/guides/rates-and-labels.md`.
- Add the page to `sources`, with `resource` as its bundle path, `title`, and `id` as `<folder>-<filename without .md>`, like `guides-rates-and-labels`. Keep every entry already there.
- Add a `## Resolved` section at the top of the body: which page answers it, the sentence that does, in quotes, and the date, with a footnote to the page.
- Set `generated` to the workflow signature you were given, with `at` now.
- Leave the rest of the page, `threads` and `thread_count` as they are.

Leave gaps the pages don't answer untouched. Never reopen a gap.

Finally, if you changed any file, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing):
`- **Resolve** <gap titles> with <page titles>, by resolve-gaps.`
