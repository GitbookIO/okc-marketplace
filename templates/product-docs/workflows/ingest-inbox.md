---
title: Ingest inbox
description: Sort what people drop into the inbox into records, and archive the originals.
icon: inbox
on:
  path: inbox/**
  branches: ['main', '*']
files:
  '**': read-only
  '{support,prs}/**': read-write
  inbox: read-write
  archive: read-write
  log.md: read-write
---

You sort new files in `inbox/` into records. People drop pasted support conversations and pull request descriptions here when no connection brings them in.

**Change only what's new.** If `inbox/example.md` is the only file that triggered this run, as when this repo is created, change nothing and add no line to `log.md`.

For each new or changed file in `inbox/` that triggered this run, except `inbox/example.md`, which you never touch:

1. Read it and decide what it is:
   - a conversation where a customer asks Acme something: a Support Thread, in `support/`
   - a pull request description or a merged change to Acme's code: a Pull Request, in `prs/`
   If it holds several, write one record each. If it's neither, leave it in `inbox/` and say so in the log line.
2. Read the existing records of that kind first, and reuse their values:
   - Support threads: set `area` to a value `support/` already uses, like `rates` or `webhooks`, when one fits. Set `state` to `closed` if the customer got an answer, otherwise `open`. Leave out `account`. Write the body as `## Question` and `## Answer`, and replace names, email addresses and phone numbers with "the customer" or "support".
   - Pull requests: set `repository` as `owner/name` and `number` if the text gives them, `state: merged` if it was merged, `author` as a handle, and always `systems: [/systems/<repository name in kebab case>.md]`, like `/systems/rates-engine.md` for `acme/rates-engine`. Leave out `issues`. Keep the description as the author wrote it, then a `## Changed files` list if the text has one.
3. Write each record as `<folder>/inbox-<YYYY-MM-DD>-<slug>.md`, like `prs/inbox-2026-11-09-rate-quote-expiry.md`, with the frontmatter its type in `types/` describes. Set `resource` to the bundle path the original will have in `archive/`. Use today's date for any time the text doesn't give, with an offset.
4. Keep the original wording in the body. Add only what's needed to make it a record: a title, and the fields above.
5. Move the original to `archive/<YYYY-MM-DD>-<original filename>` exactly as it was. Don't add frontmatter or change its content: files in `inbox/` and `archive/` stay untyped.

Never edit pages in `docs/`, `gaps/` or `digests/`, existing records, or `api/`.

Finally, unless `inbox/example.md` was the only file, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing):
`- **Ingest** <what was dropped> into <folders>, by ingest-inbox.`
