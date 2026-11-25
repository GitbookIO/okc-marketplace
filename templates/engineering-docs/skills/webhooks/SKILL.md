---
name: webhooks
description: How to change Webhooks safely. Use when working on webhook delivery, retries, ordering, queue partitions or payload signatures.
type: Skill
system: /systems/webhooks.md
sources:
  - id: systems-webhooks
    resource: /systems/webhooks.md
    title: "Webhooks"
  - id: specs-mock-2
    resource: /specs/mock-2.md
    title: "Webhook delivery guarantees"
  - id: prs-mock-4
    resource: /prs/mock-4.md
    title: "Deliver retries from a parallel worker pool"
  - id: prs-mock-5
    resource: /prs/mock-5.md
    title: "Partition the delivery queue by shipment"
  - id: prs-mock-6
    resource: /prs/mock-6.md
    title: "Cap delivery retries at 5 attempts"
  - id: incidents-mock-2
    resource: /incidents/mock-2.md
    title: "Webhook deliveries fell 40 minutes behind"
  - id: runbooks-webhook-delivery-backlog
    resource: /runbooks/webhook-delivery-backlog.md
    title: "Webhook delivery backlog"
  - id: decisions-2026-10-17-cap-webhook-retries-at-5
    resource: /decisions/2026-10-17-cap-webhook-retries-at-5.md
    title: "Cap webhook retries at 5 attempts"
generated:
  by: workflow:system-skills:anthropic/claude-opus-5-5
  at: 2026-11-09T07:00:00Z
---

## What it is

[Webhooks](../../systems/webhooks.md) delivers shipment events to the endpoints customers register, signs every payload, and retries failed deliveries. Customers build their own shipment timelines from these events.

## Rules from specs

- Open drift: [Webhook delivery guarantees](../../specs/mock-2.md) requires up to 8 retries over 24 hours, but [retries stop after 5 over about 2 hours](../../prs/mock-6.md), as Platform [decided on 17 October](../../decisions/2026-10-17-cap-webhook-retries-at-5.md). Ask Platform which one holds before touching retry config.
- Every event is [delivered at least once](../../specs/mock-2.md).
- Events for one shipment [arrive in the order they happened](../../specs/mock-2.md). Keep the queue [partitioned by shipment ID](../../prs/mock-5.md).
- [Sign the exact bytes sent](../../specs/mock-2.md), with HMAC SHA-256 in the `Acme-Signature` header.

## How changes are made here

- Delivery code lives in `src/delivery/`. [Ordering is tested](../../prs/mock-5.md) in `test/delivery/order.test.ts`.
- [Retry limits live](../../prs/mock-6.md) in `config/retry.yaml`, not in code.
- Pull requests say which incident or decision they follow, as in [Deliver retries from a parallel worker pool](../../prs/mock-4.md) and [Cap delivery retries at 5 attempts](../../prs/mock-6.md).

## Before you merge

- Run the ordering test. A [worker pool](../../prs/mock-4.md) without [partitions](../../prs/mock-5.md) delivered events out of order for three weeks.
- Think about a burst of three times the usual tracking volume. One consumer [fell 40 minutes behind on 14 October](../../incidents/mock-2.md).
- If deliveries fall behind after a deploy, [add consumers until the queue stops growing](../../runbooks/webhook-delivery-backlog.md).
