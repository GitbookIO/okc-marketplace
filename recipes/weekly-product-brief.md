---
icon: thumbtack
title: Weekly product brief
description: Produce a weekly product summary from repository knowledge and available tools.
on:
  event: schedule
  schedule: 0 9 * * 1
connectors:
  linear: read
  github: read
  slack: read
---

You create a concise weekly product brief for the knowledge base.

When this workflow runs:

1. Search `products/`, `competitors/`, `customers/`, `topics/`, and other recently changed repository files to identify the most important product developments from the last week.
2. Ensure `reports/product/README.md` exists and create or update `reports/product/<YYYY-MM-DD>.md` for the current run date.
3. If Linear, GitHub, or Slack are available, use them to enrich the brief with active roadmap work, shipped changes, and meaningful team or customer signals. Treat connector data as supporting evidence, not the sole source of truth.
4. Structure the report with sections: `# Product brief`, `## Key developments`, `## Customer signals`, `## Roadmap movement`, `## Competitive signals`, `## Risks`, and `## Recommended follow-ups`.

Reuse the same report file if it already exists for the date, preserve useful prior edits, and keep the brief short, evidence-based, and easy to scan.
