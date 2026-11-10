---
type: Decision
title: Build Saturday delivery on Parcelline first
description: Saturday delivery starts with Parcelline. Swiftway follows later.
state: accepted
decided_on: 2026-10-23
deciders: [Lena Ito, Sam Reyes]
sources:
  - id: meetings-mock-6
    resource: "/meetings/mock-6.md"
    title: "Roadmap review: Saturday delivery"
generated:
  by: "workflow:record-decisions:anthropic/claude-opus-5-5"
  at: "2026-10-23T16:00:00Z"
stale_after: "2027-04-21T16:00:00Z"
---

## Decision

Saturday delivery is built on Parcelline first, with Swiftway later. Lena Ito leads it, with a target of 1 February 2027.[^meetings-mock-6]

## Options considered

```mermaid
flowchart TD
  q["Which carrier does Saturday delivery start with?"]
  q --> o0["Parcelline first"]
  q --> o1["Swiftway first"]
  q --> o2["Both at once"]
  style o0 stroke-width:3px
```

- **Parcelline first**: covers two of Tidewater's three regions on Saturdays.
- **Swiftway first**: covers all three, at about twice the price.
- **Both at once**: two sets of service levels in rates and in the dashboard.

## Reasons

- Parcelline covers two of Tidewater's three regions on Saturdays.[^meetings-mock-6]
- Swiftway's Saturday service costs about twice as much, which is hard to pass on.[^meetings-mock-6]
- Both at once is too much for the first quarter.[^meetings-mock-6]

## Consequences

- [Tidewater Pharmacy](../customers/tidewater.md)'s third region waits for Swiftway.[^meetings-mock-6]
- [Saturday delivery](../projects/saturday-delivery.md) targets 1 February 2027.[^meetings-mock-6]

## Who decided

Lena Ito and Sam Reyes, on 23 October 2026.
