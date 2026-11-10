---
title: Ingest meetings from Fireflies
description: Write one Meeting record per Fireflies transcript.
icon: microphone
on:
  connector: fireflies
  trigger: fireflies_get_transcripts
  with:
    limit: 50
files:
  '**': read-only
  meetings: read-write
  log.md: read-write
---

You turn Fireflies transcripts into Meeting records, one file per meeting. Update topics, Update people and Update projects read them, so what you write here decides which pages a meeting updates.

The trigger payload is the latest result of `fireflies_get_transcripts`. For each transcript in it that has no record yet:

1. Fetch its summary with `fireflies_get_summary` and its sentences with `fireflies_get_transcript`.
2. Write `meetings/fireflies-<transcript id>.md`, like `meetings/fireflies-01JC8X4.md`. If the file exists, update it in place. Never create a second file for the same meeting.
3. Set the frontmatter from `types/Meeting.md`:
   - `type: Meeting`, `title` (the meeting title from Fireflies), `resource` (the transcript's Fireflies URL)
   - `date`, and `duration_minutes`
   - `attendees`: the names of the people who spoke or were invited, as Fireflies gives them
   - `project`: the project the meeting was about, if the title or summary names one. Use the page in `projects/` with that title, or `/projects/<project name in kebab case>.md` if there's none yet. Update projects creates it as a draft. Leave it out for one-on-ones and general check-ins that cover several things.
4. Write the body as `## Summary` (Fireflies' summary and action items, with who owns each), then `## Transcript` (the sentences, one line per speaker turn, `**Name:** what they said`).

Don't touch any folder but `meetings/`.

Finally, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create the heading at the top if it's missing, newest first):
`- **Ingest** <n> Fireflies transcripts into meetings/, by ingest-meetings-fireflies.`
