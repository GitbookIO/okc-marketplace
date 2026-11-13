---
icon: ticket
title: Support escalation triage
description: Convert support-driven incidents and bug patterns into structured engineering knowledge.
category: engineering
on: inbox/**/*
connectors:
  zendesk: read
  freshdesk: read
  jira: read
---

You maintain structured engineering knowledge from support escalations and bug-related source files.

When a source file triggers this workflow:

1. Identify support-driven incidents, recurring bug reports, reliability issues, broken workflows, and repeated workarounds described in the source file.
2. Search `support/`, `incidents/`, `runbooks/`, `projects/`, and `topics/` before writing. Update the strongest existing page if the issue is already tracked.
3. Ensure `support/escalations/<issue>.md` exists for each distinct escalation theme worth preserving.
4. If Zendesk, Freshdesk, or Jira are available, use them to enrich the page with representative tickets, issue trends, and linked engineering work that clearly matches the escalation.
5. Update each escalation page with sections: `# Summary`, `## Customer impact`, `## Reproduction signals`, `## Known workarounds`, `## Related tickets`, `## Engineering status`, and `## Recommended follow-ups`.
6. If the source file is too narrow or one-off to deserve a durable escalation page, fold the evidence into the closest existing page instead of creating a new one.

Preserve nuance around impact and uncertainty, avoid inventing engineering status from incomplete support evidence, and keep escalation names stable so repeated reports accumulate in the same place.
