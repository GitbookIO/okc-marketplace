---
type: Pull Request
title: Partition the delivery queue by shipment
resource: "mock://prs/7"
number: 219
repository: acme/webhooks
state: merged
author: jonah-park
merged_at: "2026-11-05T16:40:00Z"
systems: [/systems/webhooks.md]
---

The delivery queue is partitioned by shipment id, and one worker takes each partition in order. Events for one shipment, retries included, now arrive in the order they happened. Delivery across shipments stays parallel.

Customers have been asking about this in support. Nothing in the API changes.

## Changed files

- `src/delivery/queue.ts`
- `src/delivery/worker.ts`
