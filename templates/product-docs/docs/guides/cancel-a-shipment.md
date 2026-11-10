---
type: Guide
title: Cancel a shipment
description: Cancel a shipment before pickup, and what happens to a label you already bought.
status: draft
audience: Developers who let customers cancel orders
endpoints: [/docs/reference/cancel-shipment.md, /docs/reference/get-shipment.md]
sources:
  - id: reference-cancel-shipment
    resource: /docs/reference/cancel-shipment.md
    title: Cancel a shipment
  - id: reference-get-shipment
    resource: /docs/reference/get-shipment.md
    title: Get a shipment
  - id: gaps-refund-after-cancel
    resource: /gaps/refund-after-cancel.md
    title: Do I get the label fee back when I cancel a shipment?
generated:
  by: "workflow:update-guides:anthropic/claude-opus-5-5"
  at: "2026-11-06T14:30:00Z"
stale_after: "2026-12-06T14:30:00Z"
---

Customers change their minds. This guide cancels a shipment before the carrier picks it up, and says what happens to a label you already bought. It's for developers who let their customers cancel orders. It's a draft, written because three customers asked what happens to the label fee.[^gaps-refund-after-cancel]

1. **Check the status.** Get the shipment first. You can cancel it until the carrier has the parcel.[^reference-get-shipment][^reference-cancel-shipment]

   ```bash
   curl https://api.acme.example/v1/shipments/shp_8Kd2 \
     -H "Authorization: Bearer $ACME_API_KEY"
   ```

2. **Cancel it.** The response is the shipment with `status: cancelled`. If the carrier already picked it up, or it's already cancelled, you get a 409 with `cannot_cancel`.[^reference-cancel-shipment]

   ```bash
   curl -X POST https://api.acme.example/v1/shipments/shp_8Kd2/cancel \
     -H "Authorization: Bearer $ACME_API_KEY"
   ```

3. **The label.** If you bought a label, Acme asks the carrier to void it.[^reference-cancel-shipment]

To confirm: whether the label fee always comes back, and how long it takes. The reference doesn't say. Support has told customers it takes up to 14 days.[^gaps-refund-after-cancel]

To confirm: whether a label the carrier already scanned can be voided, and what customers should do about its fee.[^gaps-refund-after-cancel]

## Related

- [Cancel a shipment](../reference/cancel-shipment.md)
- [Get a shipment](../reference/get-shipment.md)
