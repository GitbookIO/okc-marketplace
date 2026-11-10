---
title: Update teams
description: Keep each Team page current from the Project pages it runs.
icon: users
on: projects/**
commit: branch
files:
  '**': read-only
  teams: read-write
  log.md: read-write
---

You keep Team pages in `teams/` current from the Project pages. This runs after an Update projects branch merges, so you read reviewed Project pages, not raw records.

**Change only what's out of date.** If every page that triggered this run is already cited in `sources` on the pages you'd write, and those pages already agree with it, change nothing: write no file and add no line to `log.md`. That's what happens when this repo is created with all of Acme's example data, since the example pages it ships with already agree.

1. Read the Project pages that changed. Collect the teams they name in `team`.
2. For each of those teams, read every Project page whose `team` is that team, and the current `teams/<slug>.md`. If a team has no page yet, create `teams/<slug>.md` for it, using the slug from the link, with `status: draft`, a `title` from the slug and a one-line `description` of what it works on. Leave out `lead` and `channel` until a person adds them. People remove `status: draft` once they've reviewed the page, so never add it to an existing page or remove it yourself.
3. Frontmatter from `types/Team.md`: keep `type`, `title`, `description`, `lead` and `channel`. Leave out `systems`. Set `sources` to those Project pages (with `resource` as the bundle path and `id` as `projects-<slug>`), `generated` to the workflow signature you were given with `at` now, and `stale_after` to 30 days later.
4. Body:
   - One paragraph on what the team is working on now and for whom.
   - `## Projects`: one line per project with its state, target date and a footnote.
   - `## Customers`: the customers its projects are for, linked to their pages, each with the projects that serve them.
   - `## Risks`: the risks from its Project pages, with footnotes. Write `Nothing known.` if there are none.
   - `## Needs review`: Staleness sweep writes this section. Keep it exactly as it is. On a new page, write `Nothing right now.`

Don't write about individual people beyond the lead. Keep what people wrote by hand.

Finally, if you changed any file, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing):
`- **Update** <team titles> from <n> Project pages, by update-teams.`
