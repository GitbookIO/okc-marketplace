---
type: Pull Request
title: Time out carrier label calls after 8 seconds
resource: "mock://prs/3"
number: 96
repository: acme/label-service
state: merged
author: ravi-menon
merged_at: "2026-10-26T10:20:00Z"
systems: [/systems/label-service.md]
---

Label calls to carriers now time out after 8 seconds and return a 504 with `carrier_timeout`, instead of hanging for up to 30 seconds and returning a 502.

Buy a label now accepts `Idempotency-Key`, like create shipment. A retry with the same key returns the label from the first request if that one went through, so nobody is charged twice. Support has been telling customers to do this since the 20th.

## Changed files

- `src/carriers/client.ts`
- `src/routes/labels/buy.ts`
- `src/idempotency.ts`
