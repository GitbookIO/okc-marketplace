---
title: Ingest inbox
description: Turn each note, link or conversation summary dropped into the inbox into a source or a meeting, and archive the original.
icon: inbox
on:
  path: inbox/**
  branches: ['main', '*']
files:
  '**': read-only
  '{sources,meetings}/**': read-write
  inbox: read-write
  archive: read-write
  log.md: read-write
---

You turn new files in `inbox/` into records. The person this repo belongs to drops their own notes, links and meeting notes here, and agents connected over MCP save summaries of conversations here. The person is named at the top of `index.md`.

**Change only what's new.** If `inbox/example.md` is the only file that triggered this run, as when this repo is created, change nothing and add no line to `log.md`.

For each new or changed file in `inbox/` that triggered this run, except `inbox/example.md`, which you never touch:

1. Read it and decide what it is:
   - notes or a transcript of a meeting or call with other people, with who was there: a Meeting, in `meetings/`
   - anything else: a note, a link with or without a comment, a pasted article, a summary of a conversation with an agent: a Source, in `sources/`
   One file is one record. If it clearly holds several unrelated items, like a list of three links with a note each, write one Source per item.
2. Read `projects/` and `people/` first, and reuse the names you find there.
   - Sources: write `sources/<YYYY-MM-DD>-<slug>.md`, like `sources/2026-11-09-ledger-backfill-plan.md`, using the date the item was captured. Set `kind`: `note` for the person's own notes and for conversation summaries, `link` for a link with at most a short comment, `article` for a pasted article someone else wrote. Set `captured_at` from the text, or now if it doesn't say. Set `author` to whoever wrote the text: the person this repo belongs to for their own notes, the agent's name as it signs for a conversation summary, like `Claude`, or the article's author. Write the body as `## Summary`, two to five lines in plain words in the writer's own voice, then `## Note`. For the owner's notes and conversation summaries that's the first person, as they'd write it: "Handed the backfill to Dev. Pairing for the first week.", never "<name> handed". Then `## Note` with the original text as it was. For a link, put the URL on its own line at the top of `## Note`.
   - Meetings: write `meetings/inbox-<YYYY-MM-DD>-<slug>.md`. Set `date`, `attendees` (names as the text gives them, never invented) and `duration_minutes` if the text says. Set `project` when the meeting was about a project: the page in `projects/` with that title, or `/projects/<project name in kebab case>.md`. Write the body as `## Summary`, a few lines of what was said and agreed, with action items, then `## Notes` or `## Transcript` with the original wording.
3. Set `title` to what the item is about, in a few words, and `resource` to the bundle path the original will have in `archive/`, like `/archive/2026-11-09-ledger-backfill-plan.md`.
4. Keep the original wording. Add only what's needed to make it a record: the title, the fields above and the summary. Don't decide topics here. Update topics does that.
5. Move the original to `archive/<YYYY-MM-DD>-<original filename>` exactly as it was. Don't add frontmatter or change its content: files in `inbox/` and `archive/` stay untyped.

Never edit topic, person or project pages, or existing records.

Finally, unless `inbox/example.md` was the only file, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing, newest first):
`- **Ingest** <what was dropped> into <folders>, by ingest-inbox.`
