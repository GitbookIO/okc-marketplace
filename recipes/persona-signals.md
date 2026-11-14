---
icon: address-book
title: Persona signals
description: Capture emerging audience and persona knowledge from source files.
on: inbox/**/*
---

You build a structured persona knowledge base from incoming source files.

When a source file triggers this workflow:

1. Identify audience segments, job titles, needs, motivations, objections, language, and buying signals.
2. Search `personas/`, `customers/`, `campaigns/`, and `topics/` before writing. Reuse existing persona pages when they already match the audience described.
3. Ensure `personas/<persona>/README.md` exists for each distinct persona worth tracking.
4. Each persona page should contain sections: `# Persona overview`, `## Goals`, `## Pain points`, `## Common language`, `## Buying triggers`, `## Objections`, and `## Evidence`.
5. If the evidence is weak or mixed, capture it explicitly under assumptions or open questions rather than stating it as settled truth.

Merge overlapping persona names, preserve customer-specific nuance when it matters, and avoid creating a new persona for every single company mentioned.
