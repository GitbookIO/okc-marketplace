---
type: Decision
title: "Route Kestrel's Black Friday labels through Swiftway"
description: "Proposed: send all of Kestrel's labels through Swiftway from 27 to 30 November."
state: proposed
decided_on: 2026-11-04
deciders: [Hana Novak]
sources:
  - id: discussions-mock-6
    resource: "/discussions/mock-6.md"
    title: "Route all of Kestrel's Black Friday labels through Swiftway?"
generated:
  by: "workflow:record-decisions:anthropic/claude-opus-5-5"
  at: "2026-11-04T16:00:00Z"
stale_after: "2027-05-03T16:00:00Z"
status: draft
---

## Decision

Not decided. Hana Novak proposes sending all of Kestrel Outdoor's labels through Swiftway from 27 to 30 November, failover or not. Lena Ito would rather turn failover on for Kestrel first, and decide after the test on 20 November.[^discussions-mock-6]

## Options considered

```mermaid
flowchart TD
  q["How does Acme protect Kestrel on Black Friday?"]
  q --> o0["Route all labels through Swiftway"]
  q --> o1["Turn failover on for Kestrel first"]
```

- **Route all labels through Swiftway**: Hana's proposal, kept as the fallback plan.
- **Turn failover on for Kestrel first**: Lena's preference, if the test on 20 November goes well.

## Reasons

- Kestrel is nervous about Black Friday after labels failed again on 4 November.[^discussions-mock-6]
- Swiftway costs about 12% more per label, and nobody has said who pays the difference.[^discussions-mock-6]

## Consequences

- If it's agreed, someone decides who pays Swiftway's higher price for those four days.[^discussions-mock-6]
- [Kestrel Outdoor](../customers/kestrel.md) and [Carrier failover](../projects/carrier-failover.md) depend on the test on 20 November.

## Who decided

Proposed by Hana Novak on 4 November 2026. Nothing is agreed yet.
