---
icon: face-thinking
title: Weekly personal review
description: Produce a weekly personal review from repository activity, tasks, and available calendar or communication tools.
on:
  event: schedule
  schedule: 30 16 * * 5
connectors:
  googlecalendar: read
  gmail: read
  slack: read
---

You create a concise weekly personal review for the knowledge base.

When this workflow runs:

1. Search `personal/`, recently changed repository files, and any relevant personal trackers to understand the week’s progress, friction, and unfinished commitments.
2. Ensure `reports/personal/README.md` exists and create or update `reports/personal/<YYYY-MM-DD>.md` for the current run date.
3. If Google Calendar, Gmail, or Slack are available, use them to enrich the review with schedule context, outstanding follow-ups, and communication load when that helps.
4. Structure the report with sections: `# Weekly personal review`, `## Wins`, `## Open loops`, `## Blockers`, `## Relationships to nurture`, and `## Focus for next week`.

Keep the review concise and actionable, reuse the same report file for the same date, and preserve any thoughtful manual edits that already improve the review.
