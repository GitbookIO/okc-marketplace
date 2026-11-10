---
type: Project
title: Usage-based billing
description: Charge per label bought instead of a flat volume tier.
state: active
team: "/teams/payments.md"
lead: Maya Chen
target_date: 2026-12-01
customers: ["/customers/bramble.md", "/customers/pinecrest.md"]
sources:
  - id: issues-mock-10
    resource: "/issues/mock-10.md"
    title: Meter labels bought per account
  - id: issues-mock-11
    resource: "/issues/mock-11.md"
    title: Invoice line items per label
  - id: issues-mock-12
    resource: "/issues/mock-12.md"
    title: Invoice lines per warehouse
  - id: issues-mock-13
    resource: "/issues/mock-13.md"
    title: Usage page in the dashboard
  - id: meetings-mock-9
    resource: "/meetings/mock-9.md"
    title: "Bramble & Co usage billing beta call"
  - id: meetings-mock-3
    resource: "/meetings/mock-3.md"
    title: Usage billing pricing review
generated:
  by: "workflow:update-projects:anthropic/claude-opus-5-5"
  at: "2026-11-05T16:00:00Z"
stale_after: "2026-12-05T16:00:00Z"
verified:
  - by: "human:maya@acme.example"
    at: "2026-11-06T09:00:00Z"
---

Usage-based billing charges per label bought instead of a flat volume tier, and rate quotes stay free. Metering is in progress, and a beta starts on 1 December. Maya Chen leads it.[^meetings-mock-3][^meetings-mock-9][^issues-mock-10]

## Progress

0 of 4 issues done.

```mermaid
pie title Issues by state
  "In progress" : 1
  "To do" : 1
  "Backlog" : 2
```

## Who it's for

- [Bramble & Co](../customers/bramble.md): its volume is up about 30% since its Rotterdam warehouse opened. It joins the beta if it starts on 1 December, and asked for invoice lines per warehouse.[^meetings-mock-9][^issues-mock-12]
- [Pinecrest Books](../customers/pinecrest.md): its volume swings with the school year, and it asked for invoices that show what each label cost.[^issues-mock-11]

## Open work

- ENG-254, Meter labels bought per account. High, in progress, Dev Okafor.[^issues-mock-10]
- ENG-255, Invoice line items per label. Medium, to do, unassigned.[^issues-mock-11]
- ENG-257, Usage page in the dashboard. Medium, backlog, unassigned.[^issues-mock-13]
- ENG-256, Invoice lines per warehouse. Low, backlog, unassigned.[^issues-mock-12]

## Recent meetings

- 5 November, Bramble beta call: Bramble joins from 1 December and asked for invoice lines per warehouse, which won't be in the first version.[^meetings-mock-9]
- 14 October, pricing review: per label bought, quotes stay free. A free tier is discussed separately.[^meetings-mock-3]

## Risks

- Nobody is assigned to invoices or the usage page yet, and the beta starts on 1 December.[^issues-mock-11][^issues-mock-13]
