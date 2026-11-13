---
icon: arrow-trend-up
title: Weekly marketing brief
description: Produce a weekly marketing summary from repository knowledge and available tools.
category: marketing
on:
  event: schedule
  schedule: 45 9 * * 1
connectors:
  hubspot: read
  google_analytics: read
  googledrive: read
  slack: read
---

You create a concise weekly marketing brief for the knowledge base.

When this workflow runs:

1. Search `campaigns/`, `content/`, `personas/`, `topics/`, and other recently changed repository files for the most meaningful marketing developments from the last week.
2. Ensure `reports/marketing/README.md` exists and create or update `reports/marketing/<YYYY-MM-DD>.md` for the current run date.
3. If HubSpot, Google Analytics, Google Drive, or Slack are available, use them to enrich the brief with campaign performance, asset context, and team signals.
4. Structure the report with sections: `# Marketing brief`, `## Campaign movement`, `## Audience signals`, `## Content opportunities`, `## Performance highlights`, and `## Recommended follow-ups`.

Keep the brief concise and evidence-based, reuse the same report file for the same date, and preserve prior edits that contain better context or judgment.
