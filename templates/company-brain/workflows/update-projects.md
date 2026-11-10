---
title: Update projects
description: Keep one Project page per project current from its issues and meetings.
icon: diagram-project
on: '{issues,meetings}/**'
commit: branch
files:
  '**': read-only
  projects: read-write
  log.md: read-write
---

You keep Project pages in `projects/` current: what each project is for, where it stands, who it's for and what's in the way.

**Change only what's out of date.** If every file that triggered this run is already cited in `sources` on the pages you'd write, and those pages already say what it says, change nothing: write no file and add no line to `log.md`. That's what happens when this repo is created with all of Acme's example data, since the example records it ships with are already written up.

1. Collect the projects the changed issues and meetings link in `project`.
2. For each of those projects, read every issue and meeting whose `project` links it, and the current `projects/<slug>.md`. Read the `customers/` pages of the accounts those records link.
3. If a project has no page yet, create `projects/<slug>.md`, using the slug from the link, with `status: draft`. People remove `status: draft` once they've reviewed the page. Never add it to an existing page or remove it yourself.
4. Frontmatter from `types/Project.md`:
   - `type: Project`, `title`, `description` (one line: the goal)
   - `state`: `done` if it has issues and every one is `done` or `canceled`. `paused` if the latest meeting says it's on hold. `active` if any issue is in progress or done, or a meeting in the last 30 days moved it forward. Otherwise `planned`.
   - `team`: the team most of its issues link, or the team a meeting names as running it
   - `lead`: the person a meeting names as leading it, if any
   - `target_date`: the date a meeting agreed on, if any. Keep an existing one unless a later meeting changed it.
   - `customers`: the Customer pages of the accounts its records link, sorted by title. Only pages that exist.
   - `sources`: every record you used, with `resource` as the bundle path and `id` as `<folder>-<filename without .md>`. `generated`: the workflow signature you were given, with `at` now. `stale_after`: 30 days later.
5. Body:
   - One paragraph: what the project is for and where it stands.
   - `## Progress`: issues done out of the total, then a Mermaid `pie` chart in a `mermaid` code block of issues by state.
   - `## Who it's for`: each customer, what they asked for and any deal or date it's tied to, with footnotes.
   - `## Open work`: issues not `done` or `canceled`, highest priority first, with assignee and footnotes.
   - `## Recent meetings`: what was agreed, newest first, with footnotes.
   - `## Risks`: what could make it late or miss what customers need, with footnotes. Write `Nothing known.` if there's none.
   Leave a section out if it would be empty, except Risks.

Keep what people wrote by hand. Never edit records.

Finally, if you changed any file, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing):
`- **Update** <project titles> from <n> records, by update-projects.`
