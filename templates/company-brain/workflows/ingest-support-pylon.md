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

You turn closed Pylon issues into Support Thread records, one file per issue. Update customers reads them to see what each customer struggles with.

The trigger payload is the latest result of `search_issues` for closed issues. For each issue in it that has no record yet:

1. Fetch the issue with `get_issue`, its account, and its messages with `get_issue_messages`.
2. Write `support/pylon-<issue number>.md`, like `support/pylon-2291.md`. If the file exists, update it in place. Never create a second file for the same issue.
3. Set the frontmatter from `types/Support Thread.md`:
   - `type: Support Thread`, `title` (the customer's question in one short line, in their words where you can), `resource` (the issue's Pylon URL)
   - `state: closed`, `opened_at` (when the customer first wrote), `closed_at`, both ISO datetimes with an offset
   - `account`: the customer's company. Match the Pylon account's domain to the `domain` of a file in `accounts/`, or its name to its `title`, and link that file, like `/accounts/northline.md`. If none matches, link `/accounts/<company name in kebab case>.md`, without words like Inc or Ltd. The CRM ingest writes that file when it syncs the company. Leave it out only if Pylon names no account.
   - `area`: the product area the question is about. Reuse a value other files in `support/` already use, like `shipments`, `rates`, `labels`, `billing` or `webhooks`. Use a new lowercase word only when none fits. Pylon tags often name it.
   - `channel`: where it came in, like `slack`, `chat` or `email`
4. Write the body in two sections, keeping the wording:
   - `## Question`: the customer's messages.
   - `## Answer`: what Acme's team replied to the customer.
   Leave out internal notes and threads, bot messages and signatures. Replace the customer's personal email addresses, phone numbers and street addresses with "the customer".

Skip issues that already have a record and aren't changed. Don't touch any folder but `support/`.

Finally, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create the heading at the top if it's missing, newest first):
`- **Ingest** <n> closed issues into support/, by ingest-support-pylon.`
