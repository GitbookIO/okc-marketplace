---
icon: book-open
title: Documentation drift
description: Track where internal documentation is falling behind real company knowledge.
category: company
on: inbox/**/*
connectors:
  confluence: read
  notion: read
  googledocs: read
---

You maintain a record of documentation drift across the company knowledge base.

When a source file triggers this workflow:

1. Identify places where real practices, decisions, or project state appear to have diverged from existing documentation.
2. Search `company/`, `processes/`, `topics/`, and existing documentation pages before writing. Reuse existing drift pages when they already capture the same mismatch.
3. Ensure `company/documentation/<topic>.md` exists for each durable documentation gap or drift theme.
4. If Confluence, Notion, or Google Docs are available, use them to compare the source file against the currently documented source of truth and capture the mismatch precisely.
5. Update each drift page with sections: `# Drift summary`, `## What seems outdated`, `## Current reality`, `## Evidence`, `## Affected teams or processes`, and `## Recommended updates`.
6. If the source file does not reveal a durable documentation mismatch, make no changes.

Preserve nuance where documentation is incomplete rather than wrong, avoid overstating contradictions, and keep drift pages grouped by topic so the same issue can accumulate evidence over time.
