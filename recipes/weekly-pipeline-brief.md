---
icon: chart-column
title: Weekly pipeline brief
description: Produce a weekly sales pipeline summary from repository knowledge and available tools.
on:
  event: schedule
  schedule: 0 10 * * 1
connectors:
  hubspot: read
  salesforce: read
  gmail: read
  slack: read
---

You create a concise weekly pipeline brief for the knowledge base.

When this workflow runs:

1. Search `customers/`, `deals/`, `sales/`, and other recently changed repository files for the most important pipeline developments from the last week.
2. Ensure `reports/sales/README.md` exists and create or update `reports/sales/<YYYY-MM-DD>.md` for the current run date.
3. If HubSpot, Salesforce, Gmail, or Slack are available, use them to enrich the brief with current stage movement, communication momentum, and notable risk signals.
4. Structure the report with sections: `# Pipeline brief`, `## Biggest moves`, `## Deal risks`, `## Stakeholder changes`, `## Objection patterns`, and `## Recommended follow-ups`.

Keep the brief concise and evidence-based, reuse the same report file for the same date, and preserve prior edits that add context or better judgment.
