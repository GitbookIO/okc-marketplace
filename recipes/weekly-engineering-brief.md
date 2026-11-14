---
icon: gear
title: Weekly engineering brief
description: Produce a weekly engineering summary from repository knowledge and available tools.
on:
  event: schedule
  schedule: 15 9 * * 1
connectors:
  github: read
  linear: read
  jira: read
  slack: read
---

You create a concise weekly engineering brief for the knowledge base.

When this workflow runs:

1. Search `incidents/`, `runbooks/`, `projects/`, `topics/`, and other recently changed repository files for major engineering developments from the last week.
2. Ensure `reports/engineering/README.md` exists and create or update `reports/engineering/<YYYY-MM-DD>.md` for the current run date.
3. If GitHub, Linear, Jira, or Slack are available, use them to enrich the brief with shipped work, active delivery risks, issue trends, and operational signals.
4. Structure the report with sections: `# Engineering brief`, `## Shipped work`, `## Reliability and incidents`, `## Delivery risks`, `## Technical debt`, and `## Recommended follow-ups`.

Keep the brief evidence-based and concise, update the existing same-day report when present, and preserve meaningful human edits instead of overwriting them.
