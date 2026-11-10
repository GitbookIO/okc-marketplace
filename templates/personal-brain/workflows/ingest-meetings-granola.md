---
title: Ingest meetings from Granola
description: Write one Meeting record per Granola meeting.
icon: microphone
on:
  connector: granola
  trigger: search_meetings
  with:
    from_date: '2026-11-01'
    limit: 50
files:
  '**': read-only
  meetings: read-write
  log.md: read-write
---

You turn Granola meetings into Meeting records, one file per meeting. Update topics, Update people and Update projects read them, so what you write here decides which pages a meeting updates.

The trigger payload is the latest result of `search_meetings` with no keywords, newest first, from the fixed `from_date`. For each meeting in it that has no record yet:

1. Fetch its notes and summary with `get_meetings`, and its transcript with `get_meeting_transcript` if the workspace allows it.
2. Write `meetings/granola-<meeting id>.md`, like `meetings/granola-7c21.md`. If the file exists, update it in place. Never create a second file for the same meeting.
3. Set the frontmatter from `types/Meeting.md`:
   - `type: Meeting`, `title` (the meeting title from Granola), `resource` (the meeting's Granola note URL)
   - `date`, and `duration_minutes` if Granola gives it
   - `attendees`: the names of the people who attended, as Granola gives them
   - `project`: the project the meeting was about, if the title or notes name one. Use the page in `projects/` with that title, or `/projects/<project name in kebab case>.md` if there's none yet. Update projects creates it as a draft. Leave it out for one-on-ones and general check-ins that cover several things.
4. Write the body as `## Summary` (Granola's summary and action items, with who owns each), then `## Transcript` (one line per speaker turn, `**Name:** what they said`), or `## Notes` when there's no transcript.

Don't touch any folder but `meetings/`.

Finally, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create the heading at the top if it's missing, newest first):
`- **Ingest** <n> Granola meetings into meetings/, by ingest-meetings-granola.`
