---
icon: computer-mouse
title: Session friction review
description: Turn behavioral source files and design-tool context into structured journey friction knowledge.
on: inbox/**/*
connectors:
  posthog: read
  figma: read
---

You maintain structured design journey knowledge from usability and behavior source files.

When a source file triggers this workflow:

1. Identify user journeys, drop-off points, repeated confusion, missing affordances, and component-level friction described in the source file.
2. Search `design/`, `research/`, `personas/`, and `topics/` before writing. Reuse existing journey or friction pages when the theme already exists.
3. Ensure `design/journeys/<journey>.md` exists for each meaningful journey or flow.
4. If PostHog or Figma are available, use them to enrich the page with product-behavior evidence, replay-derived patterns, or design-system context that clearly matches the journey.
5. Update each journey page with sections: `# Journey summary`, `## Friction points`, `## Evidence`, `## Impacted personas`, `## Related components`, and `## Candidate improvements`.
6. If the source file does not contain durable journey knowledge, make no changes.

Preserve concrete behavioral evidence, avoid flattening distinct frictions into one vague summary, and prefer updating a strong existing journey page over creating overlapping files.
