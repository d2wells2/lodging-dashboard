# Lodging Evaluator Skill

A reusable, criteria-driven lodging evaluation framework for the well-traveled explorer. Surfaces the best-fit properties for any trip — not the most-promoted ones — using a multi-variable scoring model, review intelligence, loyalty/card benefit calculation, and honest rolled-up cost view.

---

## When to Use This Skill

Invoke when the user wants to find lodging for any trip. Works for hotels, resorts, boutique properties, and vacation rentals. Especially useful when:
- The user is overwhelmed by options across platforms
- They have specific quality or experience standards
- They hold loyalty or card benefit programs
- They want honest total cost visibility, not just nightly rates

---

## Step 1 — Collect Trip Parameters

DESTINATION, AREA PREFERENCE, TRAVEL DATES, DURATION, PARTY, NON-NEGOTIABLES, ACCOMMODATION TIER, BUDGET TIER, PROGRAMS

---

## Step 2 — Accommodation Tier Reference

| Tier | Description | Examples |
|------|-------------|---------|
| Upscale Independent | Boutique, design-forward, character-rich | Local luxury independents |
| Lifestyle Brand | Curated, strong aesthetic identity | Andaz, 1 Hotels, Autograph Collection |
| Classic Luxury Resort | Full infrastructure, predictable excellence | Ritz-Carlton, Four Seasons, JW Marriott, Conrad, Waldorf Astoria |
| Ultra-Premium | Rare, intimate, experiential | Aman, Rosewood, Six Senses, Alila |

---

## Step 3 — Budget Tier Reference

| Tier | Nightly Rate | What to Expect |
|------|-------------|----------------|
| Solid | $250–400 | Clean, amenity-complete, no friction |
| Premium | $400–700 | Elevated design, better service, memorable |
| Luxury | $700–1,100 | Resort-full, effortless, worth the splurge |
| Ultra | $1,100+ | Exceptional by design, not just price |

Value elasticity always on: flag properties that score above their price tier as Value Finds.

---

## Step 4 — Search & Surface Properties

Search: Google Hotels, TripAdvisor, Booking.com, Hotels.com, Airbnb/VRBO, direct brand sites, Amex FHR directory, Chase The Edit directory, Hyatt.com, Marriott.com, Hilton.com. Target 8–12 raw candidates, score down to 6–8.

---

## Step 5 — Scoring Model

Dimension weights by property type:

| Dimension | Resort/Hotel | Boutique | Vacation Rental |
|-----------|-------------|----------|-----------------|
| Location & Access | 20% | 25% | 35% |
| Design & Experience | 20% | 35% | 35% |
| Service | 30% | 25% | 0% |
| Family/Toddler Fit | 15% | 15% | 20% |
| Review Confidence | 15% | 15% | 10% |

Score each dimension 1–10. Service = 0% for vacation rentals (redistribute to Location/Design).

---

## Step 6 — Review Intelligence Layer

For each property extract:
- REVIEW CONFIDENCE: aggregate rating + volume + confidence level (High/Med/Low)
- POSITIVE THEMES (top 3): recurring themes from favorable reviews
- CONCERN THEMES (top 2–3): recurring themes from critical reviews
- FAMILY/TODDLER SIGNAL: what reviewers with kids specifically say
- RECENCY NOTE: flag if concern themes are recent (last 12 months)

---

## Step 7 — Loyalty & Card Benefit Layer

Programs to check:

| Program | Key Benefits |
|---------|-------------|
| Amex Fine Hotels + Resorts (FHR) | Daily breakfast x2, $100 property credit, 4pm checkout, noon check-in when available, room upgrade |
| Chase Sapphire The Edit | Daily breakfast x2, $100 experience credit, room upgrade, flexible check-in/out |
| Hyatt World of Hyatt | Points, upgrades by status, Globalist 4pm checkout |
| Marriott Bonvoy | Points, upgrades by status, Titanium/Ambassador 4pm checkout |
| Hilton Honors | Points, upgrades, Diamond breakfast at select properties |

Flag double-stack opportunities (e.g., Ritz-Carlton = Bonvoy + FHR eligible).

Benefit value calc:
- Breakfast (FHR/The Edit): $85–100/day x nights (Hawaii rate)
- Property credit: $100/stay
- Total estimated benefit value = sum of above

---

## Step 8 — Rolled-Up Cost View

Always show full picture:

Base room rate:       $XXX/night x [N] nights  = $X,XXX
Taxes (~14.96% HI):                             = $XXX
Resort fees:          $XX/night x [N] nights   = $XXX
GROSS TOTAL:                                    $X,XXX
- Breakfast credit:  -$XX/day x [N] nights     = -$XXX
- Property credit:                              = -$100
EFFECTIVE TOTAL:                                $X,XXX
EFFECTIVE NIGHTLY:                              $XXX/night

Hawaii tax rate: ~14.96% (GET 4.712% + TAT 10.25%). Always research resort fees per property — check direct website or ResortFeeChecker.com.

---

## Step 9 — Output Format

Render as interactive HTML artifact with explore/validate/purchase flows. For each property card include: name, tier, location, scores, review intelligence, benefit layer, cost view, value flag, and direct links (book direct, OTA, Google Reviews, TripAdvisor, program portal). Follow with summary ranking table sortable by composite score and effective nightly rate.

---

## Calibration Notes

- Never use aggregate star rating as primary filter
- Value elasticity always on
- Family/Toddler Fit never optional — flag low scores regardless of other scores
- Resort fees frequently hidden on OTAs — always research
- Verify program participation at booking time — directories change
- Weight last 12 months of reviews more heavily than older patterns
