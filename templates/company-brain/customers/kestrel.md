---
type: Customer
title: Kestrel Outdoor
description: "Outdoor retailer whose labels failed twice in two weeks, with a renewal due in January."
account: "/accounts/kestrel.md"
owner: Ada Mensah
health: at risk
renewal_date: 2027-01-31
sources:
  - id: accounts-kestrel
    resource: "/accounts/kestrel.md"
    title: Kestrel Outdoor
  - id: deals-mock-6
    resource: "/deals/mock-6.md"
    title: Kestrel Outdoor 2027 renewal
  - id: deals-mock-5
    resource: "/deals/mock-5.md"
    title: Kestrel Outdoor first contract
  - id: meetings-mock-5
    resource: "/meetings/mock-5.md"
    title: "Kestrel Outdoor escalation: labels during the sale"
  - id: meetings-mock-1
    resource: "/meetings/mock-1.md"
    title: Kestrel Outdoor quarterly review
  - id: support-mock-12
    resource: "/support/mock-12.md"
    title: Labels failing again this morning
  - id: support-mock-6
    resource: "/support/mock-6.md"
    title: Getting timeout errors on every label
  - id: support-mock-5
    resource: "/support/mock-5.md"
    title: Labels failing during our sale
  - id: support-mock-2
    resource: "/support/mock-2.md"
    title: Label purchases are taking 6 to 8 seconds
  - id: issues-mock-2
    resource: "/issues/mock-2.md"
    title: Route label calls to Swiftway when Parcelline times out
  - id: issues-mock-4
    resource: "/issues/mock-4.md"
    title: Kestrel labels fail during the Parcelline outage
generated:
  by: "workflow:update-customers:anthropic/claude-opus-5-5"
  at: "2026-11-06T16:00:00Z"
stale_after: "2026-12-06T16:00:00Z"
---

Kestrel Outdoor is an outdoor gear retailer whose label volume triples during its two big sales a year.[^accounts-kestrel] Labels failed during its sale on 24 October and again during a Parcelline outage on 4 November. Its renewal is due 31 January, and it wants failover to a second carrier before Black Friday on 27 November.[^deals-mock-6][^meetings-mock-5]

## Health

At risk.

- Labels failed in 3 support threads and an escalation call in the last 30 days: during the sale on 24 October, and during the Parcelline outage on 4 November.[^support-mock-5][^support-mock-6][^meetings-mock-5][^support-mock-12][^issues-mock-4]
- Kestrel said it will look at other shipping APIs if labels fail again in November, and its renewal is due 31 January.[^deals-mock-6]
- Acme credited 20% of October's label fees, and Kestrel accepted. Failover to Swiftway is in testing, with a target of 20 November.[^meetings-mock-5][^issues-mock-2]

## Deals

| Deal | Kind | Stage | Amount | Close date |
| --- | --- | --- | --- | --- |
| Kestrel Outdoor 2027 renewal[^deals-mock-6] | renewal | qualified to buy | 54,000 USD | 31 January 2027 |
| Kestrel Outdoor first contract[^deals-mock-5] | new | closed won | 54,000 USD | 31 January 2026 |

## What they've asked for

- A backup carrier when Parcelline slows down, working before Black Friday. Covered by [Carrier failover](../projects/carrier-failover.md).[^meetings-mock-1][^meetings-mock-5][^issues-mock-2]

## Open issues

- ENG-246, Route label calls to Swiftway when Parcelline times out. Urgent, in progress.[^issues-mock-2]

## Support

4 threads in the last 90 days, all about labels.

- 4 November: Labels failing again this morning.[^support-mock-12]
- 24 October: Getting timeout errors on every label.[^support-mock-6]
- 24 October: Labels failing during our sale.[^support-mock-5]

Older: 5 October, Label purchases are taking 6 to 8 seconds.[^support-mock-2]

```vega-lite
{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "description": "Kestrel Outdoor support threads per week, by area",
  "data": {
    "values": [
      {
        "week": "2026-10-05",
        "area": "labels",
        "threads": 1
      },
      {
        "week": "2026-10-19",
        "area": "labels",
        "threads": 2
      },
      {
        "week": "2026-11-02",
        "area": "labels",
        "threads": 1
      }
    ]
  },
  "mark": "bar",
  "encoding": {
    "x": {
      "field": "week",
      "type": "ordinal",
      "title": "Week of"
    },
    "y": {
      "field": "threads",
      "type": "quantitative",
      "title": "Support threads"
    },
    "color": {
      "field": "area",
      "type": "nominal",
      "title": "Area"
    }
  }
}
```

## Recent conversations

- 27 October, escalation: about 1,200 orders shipped a day late during the sale. Acme credited 20% of October's label fees and promised failover before Black Friday.[^meetings-mock-5]
- 30 September, quarterly review: Kestrel asked for a backup carrier during sales. Renewal talks start in December.[^meetings-mock-1]
