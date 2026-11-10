---
title: Weekly review
description: Every Monday, write a digest of what was captured last week and the threads still open.
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

Every Monday, you write one digest of the week that just ended, Monday to Sunday, for the person this repo belongs to. They read it to see what they captured, what their pages now say, and what they still owe or still wonder about. The owner is named at the top of `index.md`.

**Change only what's out of date.** If this week's digest already exists and nothing in it would change, change nothing: write no file and add no line to `log.md`.

1. Read `log.md` for that week. Read the sources captured in it, by `captured_at`, and the meetings held in it, by `date`. For the chart, also count sources and meetings from the five weeks before.
2. Read the pages in `topics/`, `people/` and `projects/`. Note the ones whose `generated.at` falls in the week, the ones with `status: draft`, and the ones whose `stale_after` is before now.
3. Write `digests/<YYYY-MM-DD>.md`, named after the Sunday the week ends on.
4. Frontmatter from `types/Digest.md`: `type: Digest`, `title` ("Week of <D Month YYYY>", the Monday), `description` (the week in one line), `period_start`, `period_end`, `sources` (every record and page cited, with `resource` as the bundle path, `id` as `<folder>-<filename without .md>` and `title`) and `generated` (the workflow signature you were given, with `at` now).
5. Body:
   - One paragraph: the most important thing that moved this week, with counts of sources and meetings captured. Write the whole digest to the owner, in the second person, like a short note from someone who read everything: "You captured four things this week." Keep it short.
   - A Vega-Lite bar chart in a `vega-lite` code block of records captured per week over the last 6 weeks, stacked by type, Source or Meeting.
   - `## Captured`: the week's sources and meetings, one line each with its weekday and a footnote. When both appear, put work under `### Work` and the rest of life under `### Everything else`.
   - `## What changed`: the topic, person and project pages updated in the week, one line each on what changed, with footnotes. Name new contradictions.
   - `## Open threads`: open commitments from the People pages, next steps due in the next two weeks from the Project pages, and open questions and contradictions from the Topic pages updated in the week, with footnotes.
   - `## Needs review`: pages with `status: draft`, then pages past their `stale_after` date, as relative links.

Count only what the records and pages show. Leave a section out if it would be empty. Never edit any page but the digest.

Finally, if you changed any file, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing, newest first):
`- **Write** the weekly review for the week of <date>, by weekly-review.`
