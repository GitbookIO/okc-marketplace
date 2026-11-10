---
title: Weekly digest
description: Summarize last week's support questions, API changes, gaps and pages that need a person.
icon: newspaper
on:
  event: schedule
  schedule: 0 8 * * 1
commit: branch
files:
  '**': read-only
  digests: read-write
  log.md: read-write
---

Every Monday, you write one digest of the week that just ended, Monday to Sunday, for the people who write Acme's docs.

**Change only what's out of date.** If this week's digest already exists and nothing in it would change, change nothing: write no file and add no line to `log.md`.

1. Read `log.md` for that week. Then read support threads by `opened_at`, pull requests by `merged_at` and changelog entries by `date` in that week, and the gaps in `gaps/` opened or resolved in it. For the chart, also read support threads from the five weeks before.
2. Write `digests/<YYYY-MM-DD>.md`, named after the Sunday the week ends on.
3. Frontmatter from `types/Digest.md`: `type: Digest`, `title` ("Week of <D Month YYYY>", the Monday), `description` (the week in one line), `period_start`, `period_end`, `sources` (every record and page cited, with `resource` as the bundle path and `id` as `<folder>-<filename without .md>`) and `generated` (the workflow signature you were given, `at` now).
4. Body:
   - One paragraph: the most important thing for the docs that week, with counts of support threads, API changes and gaps opened and resolved.
   - A Vega-Lite bar chart in a `vega-lite` code block of support threads per week over the last 6 weeks, stacked by `area`.
   - `## API changes`: the week's changelog entries, one line each with a footnote.
   - `## Gaps`: gaps opened and resolved that week, then the three open gaps with the most threads, with footnotes.
   - `## Shipped but not in the docs`: pull requests merged that week that change what customers see but that no changelog entry cites, with footnotes.
   - `## Needs a person`: draft guides waiting for review, and pages past `stale_after`.

Count only what the records and pages show. Leave a section out if it would be empty.

Finally, if you changed any file, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing):
`- **Write** the digest for the week of <date>, by weekly-digest.`
