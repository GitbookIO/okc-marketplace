---
title: Ingest discussions from Slack
description: Write one Discussion record per thread in a chosen Slack channel.
icon: comments
on:
  connector: slack
  trigger: slack_read_channel
  with:
    channel_id: C0000000000
    limit: 50
    response_format: concise
files:
  '**': read-only
  discussions: read-write
  log.md: read-write
---

You turn threads in one Slack channel into Discussion records, one file per thread. Record decisions reads them, since that's where the reasons behind a decision are often written down.

This workflow watches the one channel in `on.with.channel_id`. Set it to a channel where decisions get made, like `#deals` or `#cs-escalations`. To watch another channel, copy this file and change the id.

The trigger payload is the latest result of `slack_read_channel` for that channel, newest first. For each message in it that started a thread with at least two replies, and either has no record yet or has new replies:

1. Fetch the whole thread with `slack_read_thread`.
2. Write `discussions/slack-<channel id>-<thread timestamp without the dot>.md`, like `discussions/slack-C04Q2-1730801234000123.md`. If the file exists, update it in place.
3. Set the frontmatter from `types/Discussion.md`:
   - `type: Discussion`, `title` (the question or topic of the thread, in one short line), `resource` (the thread's Slack permalink)
   - `channel`: the channel name without `#`, like `deals`
   - `participants`: the names of everyone who posted, in the order they first posted
   - `date`: the day the thread started
4. Write the body as the thread, one quoted line per message: `> **Name:** message`, with an empty `>` line between messages. Keep the wording. Leave out bot messages and messages that are only a reaction or an emoji.

Skip messages without a thread, and threads that already have a record with the same replies. Don't touch any folder but `discussions/`.

Finally, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create the heading at the top if it's missing, newest first):
`- **Ingest** <n> Slack threads from #<channel> into discussions/, by ingest-discussions-slack.`
