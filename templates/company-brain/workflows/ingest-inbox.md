---
title: Ingest inbox
description: Sort what people drop into the inbox into meetings and discussions, and archive the originals.
icon: inbox
on:
  path: inbox/**
  branches: ['main', '*']
files:
  '**': read-only
  '{meetings,discussions}/**': read-write
  inbox: read-write
  archive: read-write
  log.md: read-write
---

You sort new files in `inbox/` into records. People drop meeting notes, call transcripts and pasted chat threads here when no connection brings them in.

**Change only what's new.** If `inbox/example.md` is the only file that triggered this run, as when this repo is created, change nothing and add no line to `log.md`.

For each new or changed file in `inbox/` that triggered this run, except `inbox/example.md`, which you never touch:

1. Read it and decide what it is:
   - notes or a transcript of a call or meeting: a Meeting, in `meetings/`
   - a chat thread or a back-and-forth in writing: a Discussion, in `discussions/`
   If it holds several, write one record each. If it's neither, leave it in `inbox/` and say so in the log line.
2. Read `accounts/`, `projects/` and the existing records first, and reuse their names:
   - Meetings: set `date`, `attendees` (names as the text gives them, never invented) and `duration_minutes` if the text says. Set `account` when the meeting was with a customer: the file in `accounts/` whose `title` or `domain` the text names, or `/accounts/<company name in kebab case>.md` if there's none yet. Set `project` when it was about a project: the page in `projects/` with that title, or `/projects/<project name in kebab case>.md`. Write the body as `## Summary`, a few lines of what was said and agreed, then `## Transcript` or `## Notes` with the original wording.
   - Discussions: set `channel` (without `#`, or `inbox` if the text doesn't say), `participants` and `date`. Write the body as one quoted line per message, `> **Name:** message`.
3. Write each record as `<folder>/inbox-<YYYY-MM-DD>-<slug>.md`, like `meetings/inbox-2026-11-09-northline-renewal.md`. Set `resource` to the bundle path the original will have in `archive/`. Use today's date for any date the text doesn't give.
4. Keep the original wording. Add only what's needed to make it a record: a title, the fields above, and the summary.
5. Move the original to `archive/<YYYY-MM-DD>-<original filename>` exactly as it was. Don't add frontmatter or change its content: files in `inbox/` and `archive/` stay untyped.

Never edit concept pages or existing records.

Finally, unless `inbox/example.md` was the only file, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing):
`- **Ingest** <what was dropped> into <folders>, by ingest-inbox.`
