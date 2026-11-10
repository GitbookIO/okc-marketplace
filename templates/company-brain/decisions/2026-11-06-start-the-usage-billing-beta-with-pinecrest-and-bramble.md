---
type: Decision
title: Start the usage billing beta with Pinecrest and Bramble
description: "Pinecrest Books and Bramble & Co try usage-based billing from 1 December, free during the beta."
state: accepted
decided_on: 2026-11-06
deciders: [Maya Chen, Ada Mensah, Sam Reyes]
sources:
  - id: discussions-mock-8
    resource: "/discussions/mock-8.md"
    title: "Who goes first in the usage billing beta?"
generated:
  by: "workflow:record-decisions:anthropic/claude-opus-5-5"
  at: "2026-11-06T16:00:00Z"
stale_after: "2027-05-05T16:00:00Z"
---

## Decision

Pinecrest Books and Bramble & Co try usage-based billing from 1 December, free during the beta.[^discussions-mock-8]

## Options considered

```mermaid
flowchart TD
  q["Who goes first in the usage billing beta?"]
  q --> o0["Pinecrest and Bramble"]
  q --> o1["Larger customers first"]
  style o0 stroke-width:3px
```

- **Pinecrest and Bramble**: both asked for it, and both have volume that swings a lot.
- **Larger customers first**: a billing mistake would cost more.

## Reasons

- Pinecrest asked in September and Bramble the day before. Both have volume that swings a lot.[^discussions-mock-8]
- They're small enough that a billing mistake won't hurt much.[^discussions-mock-8]

## Consequences

- [Usage-based billing](../projects/usage-based-billing.md) needs metering ready by 1 December.
- Ada Mensah tells [Pinecrest Books](../customers/pinecrest.md) and [Bramble & Co](../customers/bramble.md).[^discussions-mock-8]

## Who decided

Maya Chen, Ada Mensah and Sam Reyes, on 6 November 2026.
