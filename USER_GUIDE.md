# User Guide — Lodging Evaluator

*A smarter way to research travel lodging. Takes 2 minutes to set up. Saves hours of searching.*

---

## What this tool does

Most lodging searches end the same way: too many options, inconsistent reviews, no clear signal on what's actually worth paying for. This tool flips that.

You tell it what matters to you — your destination, dates, who's traveling, must-haves, loyalty programs — and it generates a structured research request that you paste into Claude (free account). Claude comes back with a scored shortlist of the best-fit properties, complete with real cost breakdowns including loyalty and credit card benefit deductions.

No more open tabs. No more star-rating paralysis.

---

## Getting started in 3 steps

### Step 1 — Fill out the intake form

Open the tool and complete the form at the top:

| Field | What to do |
|---|---|
| **Destination** | Start typing — a dropdown of curated destinations appears |
| **Travel Dates** | Click the date field to open a calendar; click your start date, then end date |
| **Travelers** | Use + / − to set adults and children |
| **Non-Negotiables** | Tap any must-have amenities (pool, beach, spa, etc.); add custom ones with the text field |
| **Reward Programs** | Tap any loyalty programs or cards you hold — this affects the cost model |
| **Lodging Type** | Optional — tap to narrow to resorts, boutiques, villas, or leave blank for all |
| **Budget Tier** | Select your range from Budget to Ultra-Luxury |

Then click **Generate Research →**

---

### Step 2 — Get your research prompt

Two buttons appear after you submit:

**⚡ Cowork Brief** — If you're using Cowork with Claude, click this. Copy the brief and paste it directly into your Cowork session.

**🤖 Claude.ai Prompt** — If you're using the free Claude.ai website, click this. You'll see a full research prompt with the scoring methodology built in.

Click **Copy Prompt**, then either:
- Go to [claude.ai](https://claude.ai), start a new conversation, and paste
- Or click **Open Claude.ai** to go there directly (the prompt is copied to your clipboard automatically)

---

### Step 3 — Read your results

Claude will return a ranked list of 5–7 properties. For each one you'll see:

- **Composite score** (0–100) — weighted across the five dimensions below
- **Recommended room** — the best fit for your traveler profile, with sqft and bed config
- **Cost breakdown** — nightly rate → taxes → resort fees → gross total → loyalty deductions → effective total
- **Review highlights** — 3 positives, 2–3 concerns, family/group signal
- **Key amenities**

---

## Understanding the scores

Properties are evaluated across five dimensions, each scored 0–10:

| Dimension | What it measures |
|---|---|
| **Location / Access** | Proximity to what matters — beach, attractions, ease of getting around |
| **Design / Experience** | Architecture, room quality, aesthetic, unique features, wow factor |
| **Service** | Staff quality, responsiveness, personalization. *Excluded for rentals/villas (weight redistributed)* |
| **Family Suitability** | Fit for your specific traveler profile — age-appropriate amenities, safety, programming |
| **Review Confidence** | Consumer signal quality — volume, recency, thematic positives, recurring concerns |

**Default weights:** Location 20% · Design 20% · Service 30% · Family 15% · Reviews 15%

The composite score is the weighted average across all five, normalized to 100. You can adjust weights live using the sliders in the dashboard.

---

## Understanding the cost breakdown

Every property shows a full cost rollup:

```
Nightly rate × nights          = Base total
+ Local taxes (~15%)           = Tax amount
+ Resort fee × nights          = Resort fees
────────────────────────────────────────────
                                 Gross total
− Breakfast credit (FHR/Edit)  = Benefit deduction
− Property F&B credit          = Benefit deduction
────────────────────────────────────────────
                                 Effective total
÷ nights                       = Effective nightly rate
```

**Why effective cost matters:** Two properties at the same rack rate can end up hundreds of dollars apart in real cost once loyalty benefits are applied. A Four Seasons at $1,100/night with Amex FHR (breakfast + $100 credit) can be cheaper effective than a $900/night property with no benefits.

---

## Loyalty & card benefits modeled

| Program | Benefits applied |
|---|---|
| **Amex Fine Hotels + Resorts (FHR)** | Daily breakfast for 2 + $100 F&B/property credit |
| **Chase Sapphire Reserve (The Edit)** | Daily breakfast for 2 + $100 property credit |
| **World of Hyatt** | Points earning; free night redemptions; suite upgrades (Globalist) |
| **Marriott Bonvoy** | Points earning; suite upgrades (Platinum+) |
| **Hilton Honors** | Points earning; room upgrades (Diamond) |

Select the programs you hold in the intake form. Only programs you select are applied to the cost calculation.

---

## Tips for better results

**Be specific on non-negotiables.** The tool passes these directly to Claude, which will flag when properties don't meet them. A pool at a Waikiki hotel and a private plunge pool at a villa are very different — add context if it matters.

**Destination matters for tax rates.** Hawaii has a ~15% combined tax rate on lodging. Hawaii and New York will look very different on gross cost vs. effective cost. Claude applies local tax rates in the research.

**Adjust weights for your trip type.** A romantic getaway? Turn Family down to 0, Service up. A remote work trip? Location matters less, Design more. The sliders on the dashboard let you re-rank instantly.

**The effective nightly rate is your apples-to-apples number.** Don't compare gross rates across properties — compare effective nightly. That's the real spend per night after all deductions.

**Room selection changes everything.** The tool defaults to the best-fit room for your traveler profile, but you can switch rooms manually on each property card. The cost breakdown updates in real time.

---

## Questions?

This tool was built for personal travel planning. Results are research starting points — always verify current rates directly with properties before booking. Rate data in the pre-loaded Hawaii dashboard reflects approximate 2025 published rates; actual Sep/Oct 2026 rates should be confirmed at time of booking.
