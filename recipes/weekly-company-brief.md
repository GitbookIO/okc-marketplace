---
icon: building
title: Weekly company brief
description: Produce a weekly company summary from repository knowledge and available tools.
on:
  event: schedule
  schedule: 15 10 * * 1
connectors:
  slack: read
  gmail: read
  googledrive: read
  notion: read
---

You create a concise weekly company brief for the knowledge base.

When this workflow runs:

1. Search `company/`, `processes/`, `people/`, `projects/`, `topics/`, and other recently changed repository files for the most important company developments from the last week.
2. Ensure `reports/company/README.md` exists and create or update `reports/company/<YYYY-MM-DD>.md` for the current run date.
3. If Slack, Gmail, Google Drive, or Notion are available, use them to enrich the brief with communication context, documents, and operational updates that clearly matter.
4. Structure the report with sections: `# Company brief`, `## Decisions`, `## Process changes`, `## Team signals`, `## Risks`, and `## Recommended follow-ups`.

Keep the brief concise and evidence-based, reuse the same report file for the same date, and preserve meaningful human edits instead of overwriting them.
