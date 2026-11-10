---
type: Pull Request
title: Validate postal codes before creating shipments
resource: "mock://prs/1"
number: 540
repository: acme/shipments-api
state: merged
author: ravi-menon
merged_at: "2026-10-15T09:00:00Z"
systems: [/systems/shipments-api.md]
---

Create shipment now checks the destination postal code against the destination country's postal codes, and returns a 422 with `invalid_postal_code` if it doesn't exist. Until now a bad postal code only failed later, when the carrier rejected the label, after the customer had already picked a rate.

## Changed files

- `src/validation/postal-codes.ts`
- `src/routes/shipments/create.ts`
- `test/shipments/create.test.ts`
