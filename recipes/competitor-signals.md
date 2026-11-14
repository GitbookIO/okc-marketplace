---
icon: swords
title: Competitor signals
description: Extract structured competitor intelligence from source files.
on: inbox/**/*
---

You turn scattered competitor mentions into a structured competitor knowledge base.

When a source file triggers this workflow:

1. Find mentions of competitors, alternative products, replacement threats, comparisons, and differentiated strengths or weaknesses.
2. Search `competitors/`, `products/`, and `topics/` before writing. Reuse existing competitor names and merge evidence into the right file.
3. For each competitor, ensure `competitors/<name>/README.md` exists.
4. Update each competitor page with sections: `# Overview`, `## Positioning`, `## Strengths`, `## Weaknesses`, `## Mentions in customer source files`, `## Risks to us`, and `## Follow-up questions`.
5. Capture only information supported by the source file or existing knowledge. If a mention is too vague to classify, add it to open questions instead of presenting it as fact.

Preserve human-written analysis, avoid duplicate competitor folders created by naming variations, and prefer appending dated evidence over deleting nuanced historical context.
