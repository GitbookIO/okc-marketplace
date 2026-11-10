---
title: Ingest deals from HubSpot
description: Write or update one Deal record per HubSpot deal.
icon: handshake
on:
  connector: hubspot
  trigger: search_crm_objects
  with:
    objectType: deals
    sorts:
      - propertyName: hs_lastmodifieddate
        direction: DESCENDING
    limit: 50
files:
  '**': read-only
  deals: read-write
  log.md: read-write
---

You keep Deal records in step with HubSpot, one file per deal. Update customers reads them for each customer's renewals and expansions.

The trigger payload is the latest result of `search_crm_objects` for deals, most recently modified first. For each deal in it that changed since its record was written:

1. Fetch the deal and its associated company with `get_crm_objects` if the payload lacks its name, stage, close date, amount, type or company.
2. Write `deals/hubspot-<deal id>.md`, like `deals/hubspot-901233.md`. If the file exists, update it in place.
3. Set the frontmatter from `types/Deal.md`:
   - `type: Deal`, `title` (the deal name), `resource` (the deal's HubSpot URL)
   - `account`: the associated company. Use the file in `accounts/` whose `resource` is that company's HubSpot URL. If there's none yet, link `/accounts/<company name in kebab case>.md`, without words like Inc or Ltd, the name Ingest accounts will give it.
   - `stage`: the deal stage's label, lowercased, like `presentation scheduled`, `contract sent`, `closed won` or `closed lost`
   - `close_date`, `amount`, `currency`
   - `kind`: `new` for new business. For existing business, `renewal` if the deal renews the current contract, otherwise `expansion`. The deal name or pipeline usually says which.
4. Write the body as the deal's description and next step, if HubSpot has them. Add a stage change under `## History`, one dated line each, newest last, keeping earlier lines.

Never edit records in other folders. Companies have their own workflow.

Finally, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create the heading at the top if it's missing, newest first):
`- **Ingest** <n> HubSpot deals into deals/, by ingest-deals-hubspot.`
