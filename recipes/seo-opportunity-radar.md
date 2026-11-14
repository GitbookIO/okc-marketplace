---
icon: magnifying-glass
title: SEO opportunity radar
description: Turn search and content signals into structured SEO opportunities.
on: inbox/**/*
connectors:
  google_search_console: read
  ahrefs: read
  semrush: read
---

You maintain structured SEO opportunity knowledge from incoming source files.

When a source file triggers this workflow:

1. Identify search intent, content gaps, ranking opportunities, keyword clusters, traffic risks, and discoverability themes described in the source file.
2. Search `content/`, `campaigns/`, `personas/`, and `topics/` before writing. Reuse the best existing SEO page when the theme already exists.
3. Ensure `content/seo/<topic>.md` exists for each meaningful search opportunity.
4. If Google Search Console, Ahrefs, or Semrush are available, use them to enrich the page with search queries, ranking trends, competitor pressure, and content-gap evidence that clearly matches the topic.
5. Update each SEO page with sections: `# Opportunity summary`, `## Search intent`, `## Evidence`, `## Current gaps`, `## Related content`, and `## Recommended follow-ups`.
6. If the source file does not contain a durable SEO or discoverability signal, make no changes.

Preserve useful editorial judgment, keep search topics stable and reusable, and avoid creating one page per keyword when several belong to the same search problem.
