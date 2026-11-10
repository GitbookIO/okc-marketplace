---
title: Update projects
description: Keep one page per project, at work or not, with where it stands, what was decided and what's next.
icon: diagram-project
on: '{meetings,sources}/**'
commit: branch
files:
  '**': read-only
  projects: read-write
  log.md: read-write
---

You keep the pages in `projects/`: one per piece of work with a goal and an end that the person this repo belongs to is part of, at work or in their own life. The owner is named at the top of `index.md`, and their notes are written in the first person.

**Change only what's out of date.** If every file that triggered this run is already cited in `sources` on the pages of the projects it's about, and those pages already say what it says, change nothing: write no file and add no line to `log.md`. That's what happens when this repo is created with the example data.

1. Read the changed meetings and sources, and collect the projects they're about:
   - a meeting's `project` link
   - a page in `projects/` whose `title` a source names or is mainly about
   - a goal with an end that no page covers yet, like "ship X by 1 December" or "hold a conversation in Dutch by Christmas", when a meeting links it or a source sets it out
2. For each of those projects, read every meeting that links it, every source that's about it, and its current page.
3. If a project has no page yet, create `projects/<slug>.md`, using the slug from the meeting's link or the project name in kebab case, with `status: draft`. People remove `status: draft` once they've reviewed the page. Never add it to an existing page or remove it yourself.
4. Frontmatter from `types/Project.md`:
   - `type: Project`, `title`, `description` (one line: the goal)
   - `state`: `done` if a record says it's finished, `paused` if the latest record puts it on hold, `active` if a record in the last 30 days moved it forward, otherwise `planned`
   - `lead`: the person the records name as leading it, often the owner
   - `target_date`: the date a record agreed on. Keep an existing one unless a later record changed it.
   - `sources`: every record you used, with `resource` as the bundle path, `id` as `<folder>-<filename without .md>` and `title`. `generated`: the workflow signature you were given, with `at` now. `stale_after`: 30 days later. Leave `verified` as it is.
5. Body:
   - One paragraph: what the project is for and where it stands, written to the owner in the second person: "You're moving credits and refunds into the Ledger", never the owner's name or "I".
   - `## Where it stands`: what's done and what's under way, with footnotes. When the records describe phases or steps in order, add a Mermaid `flowchart LR` in a `mermaid` code block with one node per phase, and mark the current one.
   - `## Next steps`: open action items, each with who owns it and any date, with footnotes.
   - `## Decisions`: what was agreed, newest first, with the date and a footnote.
   - `## Risks`: what could make it late or miss its goal, with footnotes. Write `Nothing known.` if there's none.
   Leave a section out if it would be empty, except Risks.

Keep what people wrote by hand. Never edit records, or pages in `topics/` and `people/`.

Finally, if you changed any file, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing, newest first):
`- **Update** <project titles>, and start <new project titles> as drafts, from <n> records, by update-projects.` Leave out the part about new pages when you started none.
