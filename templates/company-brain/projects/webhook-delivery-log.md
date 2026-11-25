---
type: Project
title: Webhook delivery log
description: "Show every webhook delivery attempt in the dashboard, and resend failed ones."
state: active
team: "/teams/web.md"
customers: ["/customers/harbor.md", "/customers/northline.md"]
sources:
  - id: issues-mock-7
    resource: "/issues/mock-7.md"
    title: "Delivery log: keep 30 days of attempts"
  - id: issues-mock-5
    resource: "/issues/mock-5.md"
    title: "Delivery log: filter by event type"
  - id: issues-mock-6
    resource: "/issues/mock-6.md"
    title: "Delivery log: export attempts as CSV"
  - id: meetings-mock-7
    resource: "/meetings/mock-7.md"
    title: Harbor Coffee Roasters check-in
generated:
  by: "workflow:update-projects:anthropic/claude-opus-5-5"
  at: "2026-11-05T16:00:00Z"
stale_after: "2026-12-05T16:00:00Z"
---

The webhook delivery log shows customers every attempt to deliver a webhook, and lets them resend a failed one. It launched on 30 October with 7 days of history. The work now is what customers asked for around launch: filters, export and a longer history. ([Harbor Coffee Roasters check-in](../meetings/mock-7.md), [Delivery log: filter by event type](../issues/mock-5.md))

## Progress

0 of 3 issues done.

```mermaid
pie title Issues by state
  "In progress" : 1
  "Backlog" : 2
```

## Who it's for

- [Northline Freight](../customers/northline.md): its auditors need 30 days of history, and its renewal depends on it. ([Delivery log: keep 30 days of attempts](../issues/mock-7.md))
- [Harbor Coffee Roasters](../customers/harbor.md): wants to export attempts as CSV for its support team. ([Delivery log: export attempts as CSV](../issues/mock-6.md), [Harbor Coffee Roasters check-in](../meetings/mock-7.md))

## Open work

- ENG-251, Delivery log: keep 30 days of attempts. High, backlog, unassigned. ([Delivery log: keep 30 days of attempts](../issues/mock-7.md))
- ENG-249, Delivery log: filter by event type. Medium, in progress, Jonah Park. ([Delivery log: filter by event type](../issues/mock-5.md))
- ENG-250, Delivery log: export attempts as CSV. Low, backlog, unassigned. ([Delivery log: export attempts as CSV](../issues/mock-6.md))

## Recent meetings

- 28 October: Harbor's subscription system missed shipped events. The log answers that from launch, and Harbor asked to export it. ([Harbor Coffee Roasters check-in](../meetings/mock-7.md))

## Risks

- Keeping 30 days has no owner or date, and Northline's renewal depends on it. ([Delivery log: keep 30 days of attempts](../issues/mock-7.md))
