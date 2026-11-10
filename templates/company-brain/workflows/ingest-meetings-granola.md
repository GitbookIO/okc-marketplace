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

You turn Granola meetings into Meeting records, one file per meeting. The customer, project and decision workflows read them, so what you link here decides which pages a meeting updates.

The trigger payload is the latest result of `search_meetings` with no keywords, newest first, from the fixed `from_date`. For each meeting in it that has no record yet:

1. Fetch its notes and summary with `get_meetings`, and its transcript with `get_meeting_transcript` if the workspace allows it.
2. Write `meetings/granola-<meeting id>.md`, like `meetings/granola-7c21.md`. If the file exists, update it in place. Never create a second file for the same meeting.
3. Set the frontmatter from `types/Meeting.md`:
   - `type: Meeting`, `title` (the meeting title from Granola), `resource` (the meeting's Granola note URL)
   - `date`, and `duration_minutes` if Granola gives it
   - `attendees`: the names of the people who attended, as Granola gives them
   - `account`: the customer the meeting was with, if any. Match an attendee's email domain to the `domain` of a file in `accounts/`, or the company name to its `title`, and link that file, like `/accounts/northline.md`. If none matches, link `/accounts/<company name in kebab case>.md`, without words like Inc or Ltd. The CRM ingest writes that file when it syncs the company. Leave `account` out when every attendee works at Acme.
   - `project`: the project the meeting was about, if the title or notes name one. Use the page in `projects/` with that title, or `/projects/<project name in kebab case>.md` if there's none yet. Update projects creates it as a draft. Leave it out for general check-ins.
4. Write the body as `## Summary` (Granola's summary and action items), then `## Transcript` (one line per speaker turn, `**Name:** what they said`), or `## Notes` when there's no transcript.

Don't touch any folder but `meetings/`.

Finally, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create the heading at the top if it's missing, newest first):
`- **Ingest** <n> Granola meetings into meetings/, by ingest-meetings-granola.`
