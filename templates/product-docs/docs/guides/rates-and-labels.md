---
type: Guide
title: Get rates and buy a label
description: Compare carrier rates for a shipment, buy a label with one of them, and pick its file format.
audience: Developers who buy labels from their own app
endpoints: [/docs/reference/create-rate-quote.md, /docs/reference/buy-label.md]
sources:
  - id: reference-create-rate-quote
    resource: /docs/reference/create-rate-quote.md
    title: Get rates
  - id: reference-buy-label
    resource: /docs/reference/buy-label.md
    title: Buy a label
  - id: changelog-2026-10-26-label-timeout
    resource: /docs/changelog/2026-10-26-label-timeout.md
    title: Label purchases time out after 8 seconds
  - id: changelog-2026-11-06-label-format
    resource: /docs/changelog/2026-11-06-label-format.md
    title: Choose the label format
generated:
  by: "workflow:update-guides:anthropic/claude-opus-5-5"
  at: "2026-11-06T14:30:00Z"
stale_after: "2026-12-06T14:30:00Z"
---

Once a shipment exists, you choose how to send it. This guide gets the rates for a shipment, buys a label with one of them, and picks the label's file format. It's for developers who buy labels from their own app, like a checkout or a warehouse tool.

1. **Get rates.** Send the shipment's id. The quote lists every service that can take the shipment, cheapest first, with `carrier`, `service`, `amount`, `currency` and `estimated_days`.[^reference-create-rate-quote]

   ```bash
   curl -X POST https://api.acme.example/v1/rates \
     -H "Authorization: Bearer $ACME_API_KEY" \
     -H "Content-Type: application/json" \
     -d '{"shipment_id":"shp_8Kd2"}'
   ```

2. **Pick a rate** and keep its `id`, like `rate_71Pq`. Show customers `amount` with `currency`. `amount` is a decimal string, so don't read it as a floating-point number.[^reference-create-rate-quote]
3. **Buy the label** with that rate's id. Send an `Idempotency-Key`, so a retry can never buy a second label.[^reference-buy-label]

   ```bash
   curl -X POST https://api.acme.example/v1/shipments/shp_8Kd2/label \
     -H "Authorization: Bearer $ACME_API_KEY" \
     -H "Idempotency-Key: 8f14e45f-order-4417" \
     -H "Content-Type: application/json" \
     -d '{"rate_id":"rate_71Pq","label_format":"zpl"}'
   ```

4. **Choose a format.** `label_format` is `pdf_4x6` unless you say otherwise. Use `pdf_a4` for office printers or `zpl` for thermal printers.[^changelog-2026-11-06-label-format]
5. **Download the label** from `label_url`. The response also has the `tracking_number`, and says which `label_format` the file is in.[^reference-buy-label]

If buying returns `rate_expired`, the rate is too old. Get rates again and buy with a new one.[^reference-buy-label] If it returns `carrier_timeout`, the carrier didn't answer within 8 seconds. Retry with the same `Idempotency-Key`.[^changelog-2026-10-26-label-timeout]

## Related

- [Get rates](../reference/create-rate-quote.md)
- [Buy a label](../reference/buy-label.md)
