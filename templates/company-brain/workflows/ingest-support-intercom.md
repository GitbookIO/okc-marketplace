---
title: Ingest support threads from Intercom
description: Write one Support Thread record per closed Intercom conversation.
icon: headset
on:
  connector: intercom
  trigger: search_conversations
  with:
    state: closed
    per_page: 50
files:
  '**': read-only
  support: read-write
  log.md: read-write
---

You turn closed Intercom conversations into Support Thread records, one file per conversation. Update customers reads them to see what each customer struggles with.

The trigger payload is the latest result of `search_conversations` for closed conversations. For each conversation in it that has no record yet:

1. Fetch the whole conversation with `get_conversation`: every part, its tags, its contact's company and its timestamps.
2. Write `support/intercom-<conversation id>.md`, like `support/intercom-88412.md`. If the file exists, update it in place. Never create a second file for the same conversation.
3. Set the frontmatter from `types/Support Thread.md`:
   - `type: Support Thread`, `title` (the customer's question in one short line, in their words where you can), `resource` (the conversation's Intercom URL)
   - `state: closed`, `opened_at` (when the customer first wrote), `closed_at`, both ISO datetimes with an offset
   - `account`: the customer's company. Match the contact's email domain to the `domain` of a file in `accounts/`, or the company name to its `title`, and link that file, like `/accounts/northline.md`. If none matches, link `/accounts/<company name in kebab case>.md`, without words like Inc or Ltd. The CRM ingest writes that file when it syncs the company. Leave it out only if Intercom names no company.
   - `area`: the product area the question is about. Reuse a value other files in `support/` already use, like `shipments`, `rates`, `labels`, `billing` or `webhooks`. Use a new lowercase word only when none fits.
   - `channel`: where it came in, like `chat` or `email`
4. Write the body in two sections, keeping the wording:
   - `## Question`: the customer's messages.
   - `## Answer`: what Acme's team replied.
   Leave out internal notes, bot greetings and signatures. Replace the customer's personal email addresses, phone numbers and street addresses with "the customer".

Skip conversations that already have a record and aren't changed. Don't touch any folder but `support/`.

Finally, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create the heading at the top if it's missing, newest first):
`- **Ingest** <n> closed conversations into support/, by ingest-support-intercom.`
