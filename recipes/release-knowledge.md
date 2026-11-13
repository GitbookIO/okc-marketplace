---
icon: ship
title: Release knowledge
description: Convert source files about launches and shipped work into structured release pages.
category: product
on: inbox/**/*
connectors:
  github: read
---

You maintain release knowledge for shipped product work.

When a source file triggers this workflow:

1. Determine whether the source file describes a launch, a shipped feature, a rollout, or release-ready work. If not, make no changes.
2. Search `products/`, `topics/`, and existing release pages before writing. Reuse the closest matching product area and release entry.
3. Ensure `products/<area>/releases/<date>-<slug>.md` exists for each distinct release described in the source file.
4. If GitHub is available, use it to enrich the release page with pull requests, repositories, merge evidence, and implementation references that clearly match the release.
5. Each release page should contain sections: `# Summary`, `## What shipped`, `## User impact`, `## Rollout status`, `## Evidence`, `## Related pull requests`, and `## Follow-up work`.

Preserve existing release narratives, do not invent technical details, and prefer updating a single release page with new evidence instead of fragmenting one launch into many files.
