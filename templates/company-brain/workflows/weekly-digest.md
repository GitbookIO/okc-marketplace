---
title: Weekly digest
description: Summarize last week's customer conversations, deals, decisions and pages that need a person.
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

Every Monday, you write one digest of the week that just ended, Monday to Sunday, for everyone at Acme who talks to customers or builds for them.

**Change only what's out of date.** If this week's digest already exists and nothing in it would change, change nothing: write no file and add no line to `log.md`.

1. Read `log.md` for that week. Then read the records dated in it: meetings by `date`, support threads by `opened_at`, issues by `created_at` and `closed_at`, discussions by `date`. Read every open deal, and the decisions dated in the week. Read the Customer pages, the Project pages and the `## Needs review` sections of the Team pages. For the chart, also read support threads from the five weeks before.
2. Write `digests/<YYYY-MM-DD>.md`, named after the Sunday the week ends on.
3. Frontmatter from `types/Digest.md`: `type: Digest`, `title` ("Week of <D Month YYYY>", the Monday), `description` (the week in one line), `period_start`, `period_end`, `sources` (every record and page cited, with `resource` as the bundle path and `id` as `<folder>-<filename without .md>`) and `generated` (the workflow signature you were given, `at` now).
4. Body:
   - One paragraph: the most important thing that happened with customers that week, with counts of meetings, support threads, decisions and issues opened and closed.
   - A Vega-Lite bar chart in a `vega-lite` code block of support threads per week over the last 6 weeks, stacked by customer.
   - `## Customers`: customers that are `at risk` or `watch`, and why, with footnotes.
   - `## Deals`: open deals closing in the next 60 days, by close date, with stage, amount and a footnote.
   - `## Decisions`: decisions dated that week, proposed ones last, with footnotes.
   - `## Projects`: what moved in each active project, with footnotes.
   - `## Needs review`: the stale pages from the Team pages, by team.

Count only what the records and pages show. Leave a section out if it would be empty.

Finally, if you changed any file, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing):
`- **Write** the digest for the week of <date>, by weekly-digest.`
