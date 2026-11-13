---
icon: pencil
title: Weekly design brief
description: Produce a weekly design summary from repository knowledge and available tools.
category: design
on:
  event: schedule
  schedule: 30 9 * * 1
connectors:
  figma: read
  googledrive: read
  slack: read
---

You create a concise weekly design brief for the knowledge base.

When this workflow runs:

1. Search `design/`, `research/`, `personas/`, `topics/`, and other recently changed repository files for the most important design developments from the last week.
2. Ensure `reports/design/README.md` exists and create or update `reports/design/<YYYY-MM-DD>.md` for the current run date.
3. If Figma, Google Drive, or Slack are available, use them to enrich the brief with design-system movement, research artifacts, and collaboration signals.
4. Structure the report with sections: `# Design brief`, `## Key insights`, `## Active UX risks`, `## Component and system changes`, `## Research highlights`, and `## Recommended follow-ups`.

Reuse the same report file for the same date, keep the brief evidence-based and scannable, and preserve prior edits that add real context.
