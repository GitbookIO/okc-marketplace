---
title: Ingest support threads from Pylon
description: Write one Support Thread record per closed Pylon issue.
icon: headset
on:
  connector: pylon
  trigger: search_issues
  with:
    state: closed
    include_messages: false
files:
  '**': read-only
  support: read-write
  log.md: read-write
---

You turn closed Pylon issues into Support Thread records, one file per issue. The docs workflows read them to find what customers ask that the docs don't answer.

The trigger payload is the latest result of `search_issues` for closed issues. For each issue in it that has no record yet:

1. Fetch the issue with `get_issue` and its messages with `get_issue_messages`.
2. Write `support/pylon-<issue number>.md`, like `support/pylon-2291.md`. If the file exists, update it in place. Never create a second file for the same issue.
3. Set the frontmatter from `types/Support Thread.md`:
   - `type: Support Thread`, `title` (the customer's question in one short line, in their words where you can), `resource` (the issue's Pylon URL)
   - `state: closed`, `opened_at` (when the customer first wrote), `closed_at`, both ISO datetimes with an offset
   - `area`: the product area the question is about. Reuse a value other files in `support/` already use, like `shipments`, `rates`, `labels`, `tracking` or `webhooks`. Use a new lowercase word only when none fits. Pylon tags often name it.
   - `channel`: where it came in, like `slack`, `chat` or `email`
   - Leave out `account`. This repo has no account pages.
4. Write the body in two sections, keeping the wording:
   - `## Question`: the customer's messages.
   - `## Answer`: what Acme's team replied to the customer.
   Leave out internal notes and threads, bot messages and signatures. Replace names, email addresses, phone numbers and street addresses with "the customer" or "support".

Skip issues that already have a record and aren't changed. Don't touch any folder but `support/`.

Finally, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create the heading at the top if it's missing, newest first):
`- **Ingest** <n> closed issues into support/, by ingest-support-pylon.`
