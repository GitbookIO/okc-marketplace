---
title: Update people
description: Keep one page per person the notes and meetings keep coming back to, with recent conversations and open commitments.
icon: person
on: '{meetings,sources}/**'
commit: branch
files:
  '**': read-only
  people: read-write
  log.md: read-write
---

You keep the pages in `people/`: one per person the person this repo belongs to works with, learns from or reads. Each page says who they are, what was discussed with them lately, and who owes whom what. The owner of the repo is named at the top of `index.md`. Never write a page about them.

**Change only what's out of date.** If every file that triggered this run is already cited in `sources` on the pages of the people it names, and those pages already say what it says, change nothing: write no file and add no line to `log.md`. That's what happens when this repo is created with the example data.

1. Read the changed meetings and sources. Collect the people they name: every meeting attendee, the people a note names by full name, and anyone a note calls by a `title` or `aliases` entry of a page in `people/`. Leave out the owner.
2. A person gets a page when two or more records name them, or when they already have one. Write nobody else.
3. For each of those people, read every meeting and source that names them, and their current page. Then write `people/<slug>.md`, slug from their full name in kebab case:
   - A new page gets `status: draft`. People remove it once they've reviewed the page. Never add it to an existing page or remove it yourself.
   - Frontmatter from `types/Person.md`: `type: Person`, `title` (their full name), `description` (one line: who they are to the owner), `role` and `organization` only as the records state them, `aliases` (the short names the notes use), `sources` (every record you used, with `resource` as the bundle path, `id` as `<folder>-<filename without .md>` and `title`), `generated` (the workflow signature you were given, with `at` now) and `stale_after` (60 days later). Leave `verified` as it is.
   - Body:
     - One paragraph: who they are and how the owner knows them, from the records.
     - `## Recent conversations`: up to eight, newest first, each with its date, what was discussed and what was agreed, with a footnote.
     - `## Open commitments`: what the owner said they'd do for this person, and what this person said they'd do, from action items and notes that no later record marks done. Name who owes it and since when, with footnotes. Leave the section out if there are none.
     - `## Topics`: relative links to the pages in `topics/` where this person's input shows up. Leave it out if there are none.
4. Write only what the records state: what was said, agreed, asked and recommended. No opinions about the person, and nothing about their health, family or private life, even when a note mentions it.

Keep what people wrote by hand. Never edit records, or pages in `topics/` and `projects/`.

Finally, if you changed any file, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing, newest first):
`- **Update** <names>, and start <new names> as drafts, from <n> records, by update-people.` Leave out the part about new pages when you started none.
