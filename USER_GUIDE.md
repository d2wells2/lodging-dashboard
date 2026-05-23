# User Guide — Lodging Evaluator

*A smarter way to research travel lodging. Takes 2 minutes to set up. Saves hours of searching.*

---

## What this tool does

Most lodging searches end the same way: too many options, inconsistent reviews, no clear signal on what's actually worth paying for. This tool flips that.

You tell it what matters to you — destination, dates, who's traveling, must-haves, loyalty programs — and it generates a structured research request you paste into Claude. Claude comes back with a scored shortlist of the best-fit properties, complete with real cost breakdowns including loyalty benefit deductions. Then you import those results directly into the dashboard for a live side-by-side comparison.

Works for luxury hotels, boutique properties, and curated vacation rentals (Plum Guide, onefinestay) — all in the same comparison.

No more open tabs. No more star-rating paralysis.

---

## Getting started in 4 steps

### Step 1 — Fill out the intake form

Open the tool and complete the form at the top:

| Field | What to do |
|---|---|
| **Destination** | Start typing — a dropdown of curated destinations appears |
| **Travel Dates** | Click the date field to open a calendar; click your start date, then end date; click **Done ✓** when finished |
| **Travelers** | Use + / − to set adults and children |
| **Non-Negotiables** | Tap any must-have amenities (pool, beach, spa, etc.); add custom ones with the text field |
| **Reward Programs** | Tap any loyalty programs or cards you hold — this affects the cost model |
| **Lodging Type** | Optional — tap to narrow to resorts, boutiques, villas, or leave blank for all |
| **Budget Tier** | Select your range from Budget to Ultra-Luxury |
| **Research** | Choose Hotels, Curated Rentals (Plum Guide, onefinestay), or Both |

Then click **Generate Research →**

---

### Step 2 — Get your research prompt

Two buttons appear after you submit:

**⚡ Cowork Brief** — If you're using Cowork with Claude, click this. Copy the brief and paste it into your Cowork session.

**🤖 Claude.ai Prompt** — If you're using the free Claude.ai website, click this. You'll see a full research prompt with the scoring methodology built in. Click **Copy Prompt**, go to [claude.ai](https://claude.ai), start a new conversation, and paste.

---

### Step 3 — Read your results and copy the JSON

Claude returns a ranked list of 5–7 properties. For each one you'll see:

- **Composite score** (0–100) — weighted across the five dimensions below
- **Recommended room** — best fit for your traveler profile, with sqft and bed config
- **Cost breakdown** — nightly rate → taxes → fees → gross → loyalty deductions → effective total
- **Review highlights** — 3 positives, 2–3 concerns, family/group signal
- **Key amenities**

At the end of Claude's response, you'll also see a **JSON block** — a block of structured data that starts with ` ```json `. That's what you'll use in Step 4.

---

### Step 4 — Import to your dashboard

1. Select and copy everything in the JSON block (from ` ```json ` to the closing ` ``` `)
2. Back in the tool, click **⬆⬇ Trips** in the dashboard filter bar
3. Paste the JSON into the **Import a Trip** box
4. Click **Import Trip**

Your new destination loads instantly as a fully scored dashboard — cards, Top 3, cost breakdowns, sorting — right alongside any previous trips. Use the **Trip:** dropdown at the top of the filter bar to switch between saved trips.

---

## Switching between trips

The tool remembers every trip you import, stored privately in your browser. No account needed. To switch trips, use the **Trip:** dropdown in the filter bar — all your saved destinations are listed there.

Your Hawaii 2026 comparison is always available as the default. Imported trips are saved automatically and persist between sessions.

---

## Hotels vs. curated rentals

When you select **Both** in the Research toggle, Claude searches luxury hotels and curated rental platforms (Plum Guide, onefinestay) side by side. These platforms vet their listings for quality, so the data is reliable — unlike raw Airbnb or VRBO searches.

Rental properties show up in the same dashboard as hotels with a few differences:
- A **green badge** identifies the platform (Plum Guide, onefinestay, etc.) vs. blue for hotels
- Bedroom count, kitchen, and laundry are shown on the card
- The "Service" score label changes to "Host & Management Quality"
- The cost model handles **cleaning fees and platform service fees**, spreading them across your nights so the effective nightly rate is a true apples-to-apples number

---

## Understanding the scores

Properties are evaluated across five dimensions, each scored 0–10:

| Dimension | What it measures |
|---|---|
| **Location / Access** | Proximity to what matters — beach, attractions, ease of getting around |
| **Design / Experience** | Architecture, room quality, aesthetic, unique features, wow factor |
| **Service / Host Quality** | Staff or host responsiveness, personalization. *Excluded for rentals; weight redistributed* |
| **Family Suitability** | Fit for your specific traveler profile — age-appropriate amenities, safety, programming |
| **Review Confidence** | Consumer signal quality — volume, recency, thematic positives, recurring concerns |

**Default weights:** Location 20% · Design 20% · Service 30% · Family 15% · Reviews 15%

The composite score is the weighted average across all five, normalized to 100. Adjust weights live using the sliders in the dashboard — they auto-balance so they always sum to 100%.

---

## Understanding the cost breakdown

### Hotels
```
Nightly rate × nights          = Base total
+ Local taxes                  = Tax amount
+ Resort fee × nights          = Resort fees
─────────────────────────────────────────────
                                 Gross total
− Breakfast credit (FHR/Edit)  = Benefit deduction
− Property F&B credit          = Benefit deduction
─────────────────────────────────────────────
                                 Effective total
÷ nights                       = Effective nightly rate
```

### Vacation Rentals
```
Nightly rate × nights          = Base total
+ Cleaning fee (one-time)      = Cleaning fee
+ Platform service fee         = Service fee
+ Local taxes                  = Tax amount
─────────────────────────────────────────────
                                 Gross total
─────────────────────────────────────────────
                                 Effective total
÷ nights                       = Effective nightly rate
```

**Why effective cost matters:** Two properties at the same rack rate can end up hundreds of dollars apart once all fees and benefits are applied. A Four Seasons at $1,100/night with Amex FHR (breakfast + $100 credit) can be cheaper effective than a $900/night property with no benefits. A rental at $600/night with a $350 cleaning fee over 3 nights is actually $717/night effective — not $600.

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

## Sharing a trip comparison

Your saved trips live in your browser — they don't travel with a shared URL. To share a specific trip comparison with someone:

1. In the dashboard, click **⬆⬇ Trips**
2. Click **Download JSON** (or Copy to Clipboard) under **Export Current Trip**
3. Send them the JSON file or paste
4. They open the tool, click **⬆⬇ Trips** → Import, paste the JSON, and click **Import Trip**

They'll see your full comparison — scores, cost breakdowns, room selections — exactly as you built it.

---

## Tips for better results

**Be specific on non-negotiables.** The tool passes these directly to Claude, which will flag when properties don't meet them. "Pool" at a Waikiki hotel and a private plunge pool at a villa are very different — add context if it matters.

**Use Both for trip types where value varies.** A Plum Guide villa can offer 3 bedrooms, a full kitchen, and a private pool at a lower effective cost than a hotel suite — but you only see that if they're in the same comparison.

**Adjust weights for your trip type.** A romantic getaway? Turn Family down, Service up. A family trip? Flip that. The sliders re-rank everything instantly and always sum to 100%.

**The effective nightly rate is your apples-to-apples number.** Don't compare gross rates across property types — compare effective nightly. That's the real spend per night after all fees and deductions are factored in.

**Room selection changes everything.** The tool defaults to the best-fit room for your traveler profile, but you can switch rooms manually on each property card. The cost breakdown updates in real time.

---

## Questions?

This tool was built for personal travel planning. Results are research starting points — always verify current rates directly with properties before booking. Rate data in the pre-loaded Hawaii dashboard reflects approximate published rates; actual rates should be confirmed at time of booking.
