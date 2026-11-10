---
title: Ingest accounts from HubSpot
description: Write or update one Account record per HubSpot company.
icon: building
on:
  connector: hubspot
  trigger: search_crm_objects
  with:
    objectType: companies
    sorts:
      - propertyName: hs_lastmodifieddate
        direction: DESCENDING
    limit: 50
files:
  '**': read-only
  accounts: read-write
  log.md: read-write
---

You keep Account records in step with HubSpot, one file per company. Every other record links its customer here, and Update customers builds each Customer page from its account.

The trigger payload is the latest result of `search_crm_objects` for companies, most recently modified first. For each company in it that changed since its record was written:

1. Fetch the company with `get_crm_objects` if the payload lacks its name, domain, owner, lifecycle stage or tier. Look up the owner's name with the HubSpot tools.
2. Name the file after the company: `accounts/<company name in kebab case>.md`, without words like Inc or Ltd, like `accounts/northline.md` for Northline Freight. If a file in `accounts/` already has this company's HubSpot URL as `resource`, update that file in place, whatever its name. Other records may already link the name you choose, so never rename an existing file.
3. Set the frontmatter from `types/Account.md`:
   - `type: Account`, `title` (the company name), `resource` (the company's HubSpot URL)
   - `domain`, `owner` (the owner's name)
   - `lifecycle_stage`: HubSpot's lifecycle stage, lowercased, like `lead`, `opportunity` or `customer`
   - `tier`: the company's `tier` property if the portal has one, like `enterprise`, `growth` or `starter`. Otherwise leave it out.
4. Write the body as one short paragraph from the company's description, industry and size, if HubSpot has them. Nothing else.

Never edit records in other folders. Deals have their own workflow.

Finally, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create the heading at the top if it's missing, newest first):
`- **Ingest** <n> HubSpot companies into accounts/, by ingest-accounts-hubspot.`
