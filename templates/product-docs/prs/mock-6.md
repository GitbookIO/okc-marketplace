---
type: Pull Request
title: Add signature_required to create shipment
resource: "mock://prs/6"
number: 552
repository: acme/shipments-api
state: merged
author: ravi-menon
merged_at: "2026-11-03T14:00:00Z"
systems: [/systems/shipments-api.md]
---

Create shipment takes `signature_required`, false by default, and every shipment returns it. When it's true, the carrier gets a signature on delivery. Services that charge for signatures quote the higher price in rates.

## Changed files

- `src/routes/shipments/create.ts`
- `src/models/shipment.ts`
- `src/carriers/options.ts`
