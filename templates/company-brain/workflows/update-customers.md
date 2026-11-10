---
title: Update customers
description: Keep one Customer page per account current from its deals, meetings, support threads and issues.
icon: building-user
on: '{accounts,deals,meetings,support,issues}/**'
commit: branch
files:
  '**': read-only
  customers: read-write
  log.md: read-write
---

You keep Customer pages in `customers/` current. Each joins what sales, support and engineering know about one customer, so anyone can read where the relationship stands without asking around.

**Change only what's out of date.** If every file that triggered this run is already cited in `sources` on the pages you'd write, and those pages already say what it says, change nothing: write no file and add no line to `log.md`. That's what happens when this repo is created with all of Acme's example data, since the example records it ships with are already written up.

1. Collect the accounts the changed records are about: the account file itself for a change in `accounts/`, and the `account` link of a changed deal, meeting, support thread or issue.
2. For each of those accounts, read everything about it: its file in `accounts/` if there is one, and every deal, meeting, support thread and issue whose `account` links it. Read the pages in `projects/` whose `customers` list it.
3. Write `customers/<account slug>.md`, using the slug of the account link, like `customers/northline.md` for `/accounts/northline.md`.
   - If the page doesn't exist, create it with `status: draft`, for an account that is a customer (`lifecycle_stage: customer` or a `closed won` deal) or that any meeting, support thread or issue links. Skip an account with nothing but its CRM file.
   - People remove `status: draft` once they've reviewed the page. Never add it to an existing page or remove it yourself.
4. Frontmatter from `types/Customer.md`:
   - `type: Customer`, `title` (the account's `title`, or the company name the records use), `description` (one line: who they are and where things stand)
   - `account`: the account link, but only if the file exists in `accounts/`. Leave it out until the CRM syncs it.
   - `owner`: the account's `owner`
   - `health`: `healthy`, `watch` or `at risk`, judged from the records. `at risk` when an open renewal is in doubt, or the customer complained about the same problem in 3 or more threads or meetings in 30 days. `watch` when there's an unresolved complaint or an open request they've tied to a deal. Otherwise `healthy`. Leave it out for a prospect with no closed deal.
   - `renewal_date`: the `close_date` of the open renewal deal, or a year after the latest won deal
   - `sources`: every record you used, with `resource` as the bundle path and `id` as `<folder>-<filename without .md>`. `generated`: the workflow signature you were given, with `at` now. `stale_after`: 30 days later.
5. Body:
   - One paragraph: who they are, what they use Acme for, and where the relationship stands now.
   - `## Health`: the health and the two or three reasons for it, with footnotes.
   - `## Deals`: a table of deals, newest first, with kind, stage, amount and close date, each with a footnote.
   - `## What they've asked for`: requests from meetings, support threads and issues, one line each, with the project page linked when one covers it, and footnotes.
   - `## Open issues`: issues that link the account and aren't `done` or `canceled`, with priority and footnotes.
   - `## Support`: how many threads in the last 90 days and what about, then the latest three, with footnotes. If there are 4 or more, add a Vega-Lite bar chart in a `vega-lite` code block of threads per week, colored by `area`.
   - `## Recent conversations`: meetings, newest first, one line each with what was agreed, and footnotes.
   Leave a section out if it would be empty.

Describe the relationship, not the people. Name customer staff only as a cited record names them, and don't add a contacts section. Keep what people wrote by hand. Never edit records.

Finally, if you changed any file, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing):
`- **Update** <customer titles> from <n> records, by update-customers.`
