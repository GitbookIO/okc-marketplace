---
type: Guide
title: Handle errors and retry safely
description: Read Acme's error codes, and retry shipments and label purchases without doing anything twice.
audience: Developers taking an integration to production
endpoints: [/docs/reference/create-shipment.md, /docs/reference/buy-label.md]
sources:
  - id: reference-create-shipment
    resource: /docs/reference/create-shipment.md
    title: Create a shipment
  - id: reference-buy-label
    resource: /docs/reference/buy-label.md
    title: Buy a label
  - id: changelog-2026-10-15-invalid-postal-code
    resource: /docs/changelog/2026-10-15-invalid-postal-code.md
    title: Reject unknown postal codes
  - id: changelog-2026-10-26-label-timeout
    resource: /docs/changelog/2026-10-26-label-timeout.md
    title: Label purchases time out after 8 seconds
  - id: gaps-label-timeout-retry
    resource: /gaps/label-timeout-retry.md
    title: Is it safe to retry a label purchase that timed out?
generated:
  by: "workflow:update-guides:anthropic/claude-opus-5-5"
  at: "2026-10-26T14:00:00Z"
stale_after: "2026-11-25T14:00:00Z"
---

Networks fail and carriers are slow. This guide shows how to read Acme's errors and how to retry without creating two shipments or buying two labels. It's for developers taking an integration to production.

1. **Read the code.** Every error has an HTTP status and a body with a stable `code` and a `message` for people. Branch on `code`, never on `message`.[^reference-create-shipment]

   ```json
   { "error": { "code": "invalid_postal_code", "message": "3511 XX is not a postal code in NL." } }
   ```

2. **Send an Idempotency-Key** with every create and every label purchase, like a UUID per order. Sending the same key again within 24 hours returns the first response instead of doing the work twice. The same key with a different body returns `idempotency_conflict`.[^reference-create-shipment][^reference-buy-label]
3. **Fix what you sent.** `invalid_request` means a field is missing or malformed. `invalid_postal_code` means the destination postal code doesn't exist in its country, so ask for the address again.[^changelog-2026-10-15-invalid-postal-code]
4. **Retry what timed out.** `carrier_timeout` means the carrier didn't answer within 8 seconds. Retry with the same `Idempotency-Key`: if the first request went through, you get the same label back and aren't charged twice. Customers asked about exactly this.[^changelog-2026-10-26-label-timeout][^gaps-label-timeout-retry]
5. **Start over when a rate expires.** `rate_expired` means the rate is too old to buy. Get rates again and use a new one.[^reference-buy-label]
6. **Don't retry the rest.** `not_found` and `label_exists` won't change on a retry.[^reference-buy-label]

## Related

- [Create a shipment](../reference/create-shipment.md)
- [Buy a label](../reference/buy-label.md)
