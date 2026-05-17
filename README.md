# Travel Toolkit — Lodging Evaluator

A personal lodging evaluation dashboard built for the well-traveled explorer. Cuts through the noise of lodging search by scoring properties against what actually matters: location, design, service, family fit, and real review intelligence — not just star ratings.

## What's in here

**`index.html`** — Interactive lodging comparison dashboard
- Multi-variable scoring across 5 dimensions
- Review intelligence: positive themes, concern themes, family/toddler signal
- Loyalty & card benefit layer (Amex FHR, Chase The Edit, Hyatt, Marriott Bonvoy, Hilton)
- Rolled-up cost view: rack rate → gross total → effective total after benefits
- Sort by composite score, effective nightly rate, family fit, or gross total
- Filter by location zone, value finds, or Amex FHR properties
- Direct links to book, review, and validate each property

**`skills/lodging-evaluator/SKILL.md`** — Reusable evaluation framework
- Portable skill that can generate a new dashboard for any trip
- Covers accommodation tiers, budget tiers, scoring model, review intelligence extraction, benefit calculation, and cost rollup

## Current dashboard
**Oahu, Hawaii — Late September / Early October 2026**
4 nights · 2 adults + 1 toddler · Pool required

## To refresh for a new trip
Open a conversation with Claude, reference `skills/lodging-evaluator/SKILL.md`, and provide new trip parameters. A new dashboard will be generated and can replace or sit alongside this one.
