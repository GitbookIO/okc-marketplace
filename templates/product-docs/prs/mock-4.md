---
type: Pull Request
title: Cache carrier rates for an hour
resource: "mock://prs/4"
number: 157
repository: acme/rates-engine
state: merged
author: lena-ito
merged_at: "2026-10-29T09:30:00Z"
systems: [/systems/rates-engine.md]
---

Rates are cached per shipment for an hour, and a rate quote's rates can be bought for one hour after the quote's `created_at`. After that, buy a label returns `rate_expired`. Before this, how long a quote lasted depended on each carrier's own cache, from a few minutes to a day.

This doesn't change the API spec. We should add an expiry time to the quote later, so customers don't have to work it out.

## Changed files

- `src/cache/rates.ts`
- `src/quotes/expiry.ts`
