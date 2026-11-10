---
type: Topic
title: "API design"
description: "Your rules for the usage API: one pagination style, integer amounts, a beta flag, docs first."
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

Your rules of thumb from the first pass at a usage endpoint. Mostly: reuse what Acme's API already does, and write the docs page before the code.[^sources-mock-3]

## Current understanding

- One pagination style: cursor pagination like list shipments, up to 200 a page. Don't invent a second one.[^sources-mock-3]
- Amounts are integers in minor units, with a currency. Never floats.[^sources-mock-3]
- New endpoints go behind a beta flag per account.[^sources-mock-3]
- Docs page first. If you can't explain a field in one sentence, it's the wrong field.[^sources-mock-3]

## Open questions

- Does a voided label show up in usage with a negative amount, or just disappear?[^sources-mock-3]

## See also

- [Usage-based billing](../projects/usage-based-billing.md)
