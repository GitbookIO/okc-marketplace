---
title: Ingest issues from Linear
description: Write or update one Issue record per Linear issue.
icon: list-check
on:
  connector: linear
  trigger: list_issues
  with:
    orderBy: updatedAt
    limit: 50
files:
  '**': read-only
  issues: read-write
  log.md: read-write
---

You keep Issue records in step with Linear, one file per issue. Update projects reads them for each project's progress, and Update customers for what each customer is waiting on.

The trigger payload is the latest result of `list_issues`, most recently updated first. For each issue in it that changed since its record was written:

1. Fetch the issue with the Linear tools if the payload lacks its description, state, priority, assignee, labels, team, project or customer requests.
2. Write `issues/linear-<identifier>.md`, like `issues/linear-ENG-214.md`. If the file exists, update it in place.
3. Set the frontmatter from `types/Issue.md`:
   - `type: Issue`, `title`, `resource` (its Linear URL), `identifier`
   - `state`: the Linear workflow state, lowercased, like `backlog`, `todo`, `in progress`, `done` or `canceled`
   - `priority`: Linear's Urgent, High, Medium, Low and No priority become `urgent`, `high`, `medium`, `low` and `none`
   - `assignee`, `labels`, `created_at`, `updated_at`, and `closed_at` when it's done or canceled
   - `team`: always `/teams/<Linear team name in kebab case>.md`, or the page in `teams/` with that title. It may not exist yet: Update teams creates it.
   - `project`: the issue's Linear project, as the page in `projects/` with that title, or `/projects/<project name in kebab case>.md`. Update projects creates missing pages as drafts. Leave it out if the issue has no project.
   - `account`: the customer that asked for it or is affected, from the issue's customer requests or a `customer:<name>` label. Match it to a file in `accounts/` by domain or name, or link `/accounts/<company name in kebab case>.md` if there's none yet. Leave it out if no customer is named.
   - `system`: the issue's `system:<name>` label if it has one, like `/systems/label-service.md` for `system:label-service`, otherwise the Linear team name in kebab case. This repo has no System pages, so the link stays as it is, for repos that add them.
4. Write the body as the issue description. Add new comments that carry decisions or findings under `## Notes`, newest last.

Never edit records in other folders.

Finally, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create the heading at the top if it's missing, newest first):
`- **Ingest** <n> Linear issues into issues/, by ingest-issues-linear.`
