---
title: Update topics
description: Fold new sources and meetings into the topic pages, with the current understanding and where the notes disagree.
icon: lightbulb
on: '{sources,meetings}/**'
commit: branch
files:
  '**': read-only
  topics: read-write
  log.md: read-write
---

You keep the topic pages in `topics/`. Each one holds what the person this repo belongs to currently understands about one subject, where their notes disagree, and what's still open. It's their wiki, compiled from their notes instead of written by hand, and they review every change on its branch. The person is named at the top of `index.md`, and their notes are written in the first person.

**Change only what's out of date.** If every file that triggered this run is already cited in `sources` on the topic pages it's about, and those pages already say what it says, change nothing: write no file and add no line to `log.md`. That's what happens when this repo is created with the example data, since the example notes are already compiled.

1. Read the changed sources and meetings. For meetings, start from `## Summary` and use the transcript for exact claims. List `topics/` and read the pages whose `title` or `aliases` match what the records discuss.
2. Decide which topics each record says something about. A record usually touches one to three. Skip scheduling, small talk and logistics.
   - Prefer an existing topic. Match titles and aliases, and add a near-synonym as an alias instead of starting a page.
   - Start a new topic only when a record is mainly about a subject no page covers, or two records discuss it.
3. For each topic, read every record already cited in its `sources`, plus the new ones, and the page as it is. Then write `topics/<slug>.md`:
   - A new page takes its slug from the title in kebab case, and `status: draft`. People remove `status: draft` once they've reviewed it. Never add it to an existing page or remove it yourself.
   - Frontmatter from `types/Topic.md`: `type: Topic`, `title`, `description` (the current understanding in one sentence), `aliases`, `related` (other topic pages this one leans on, only pages that exist, sorted by path), `sources` (every record you used, with `resource` as the bundle path, `id` as `<folder>-<filename without .md>` and `title`), `generated` (the workflow signature you were given, with `at` now) and `stale_after` (30 days later). Leave `verified` as it is.
   - Body:
     - One paragraph: what the owner currently understands, in plain words, as of the newest record.
     - `## Current understanding`: one claim per bullet, with footnotes. When a newer record changes an earlier claim, write the newer one and say what it replaced and since when, like "Since 9 November: dual writes start before the backfill, replacing the plan to backfill first."
     - `## Contradictions`: where records disagree and nothing newer settles it. One bullet each, with what each side says, footnotes on both, and which is newer. Don't pick a side unless a record does. When a newer record settles one, move it to Current understanding and say what settled it. Leave the section out when there are none.
     - `## Open questions`: questions the records raise and don't answer, with footnotes. Leave the section out if there are none.
     - For a book, use `## What you're taking from it` in place of Current understanding, organized by chapter, and add `## Lines you kept` with the lines the notes quote.
     - `## See also`: relative links to the related topics, and to the pages in `people/` and `projects/` that exist for the people and projects these records name. Leave it out if it would be empty.
4. Write to the owner, in the second person: "You handed the backfill to Dev on 21 October", never "<name> handed" or "I handed". Their notes are in the first person, so turn their "I" into "you". Keep their own phrasing where it's precise, and short. Never add a claim no record makes, and never smooth over a disagreement.

Keep what people wrote by hand. Never edit records, or pages in `people/` and `projects/`.

Finally, if you changed any file, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing, newest first):
`- **Update** <topic titles>, and start <new topic titles> as drafts, from <n> records, by update-topics.` Leave out the part about new topics when you started none.
