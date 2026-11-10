---
type: Topic
title: "API design"
description: "How Maya designs endpoints like the usage API: one pagination style, integer amounts, a beta flag, and the docs page first."
aliases: ["Usage API"]
sources:
  - id: sources-mock-3
    resource: "/sources/mock-3.md"
    title: "Usage API: first design notes"
generated:
  by: "workflow:update-topics:anthropic/claude-opus-5-5"
  at: "2026-10-01T13:10:00Z"
stale_after: "2026-10-31T13:10:00Z"
---

The first design for a usage endpoint follows the conventions Acme's API already has, and starts from the docs page rather than the code.[^sources-mock-3]

## Current understanding

- Reuse what exists: cursor pagination like list shipments, with pages of up to 200. Don't invent a second style.[^sources-mock-3]
- Amounts are integers in minor units, with a currency. Never floats.[^sources-mock-3]
- New endpoints ship behind a beta flag per account.[^sources-mock-3]
- Write the docs page before the code. A field that can't be explained in one sentence is the wrong field.[^sources-mock-3]

## Contradictions

None so far.

## Open questions

- Does a voided label show up in usage with a negative amount, or disappear?[^sources-mock-3]

## See also

- [Usage-based billing](../projects/usage-based-billing.md)
