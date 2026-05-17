# Lodging Evaluator — Travel Intelligence Tool

> Cut through the noise. Score what matters. Know the real cost before you book.

A personal travel lodging research tool that combines a structured intake form with AI-powered research output. Instead of drowning in aggregator results and star ratings, you define your criteria — then get a scored, cost-modeled shortlist of properties ranked against what actually matters to you.

---

## How it works

**1. Fill out the intake form**
Enter your destination, travel dates, travelers, non-negotiables, reward programs, and lodging preferences.

**2. Generate a research prompt**
The tool produces a structured research request — either a compact Cowork brief or a full Claude.ai prompt with the evaluation methodology embedded.

**3. Paste into Claude, get your shortlist**
Claude researches and scores properties against your exact criteria, with full cost breakdowns including loyalty benefit deductions.

---

## Two usage paths

| | Cowork Mode | Claude.ai Mode |
|---|---|---|
| **Who** | Tool owner (you) | Friends & family |
| **How** | Paste brief into Cowork session | Paste prompt into claude.ai (free account works) |
| **Output** | Full scored dashboard built here | Scored shortlist with cost breakdown in chat |
| **Cost** | Uses your Cowork session | Uses their own Claude account |

---

## Features

### Intake Form
- 🔍 **Destination search** — Predictive input across 150+ curated worldwide destinations
- 📅 **Visual calendar picker** — Two-month range selector with night count
- 👥 **Traveler counters** — Adults and children with independent controls
- 🚫 **Non-negotiables** — Tap-to-select amenity chips (pool, beach, spa, gym, kids' club, etc.) + custom add
- 💳 **Reward programs** — Amex FHR, Chase The Edit, World of Hyatt, Marriott Bonvoy, Hilton Honors, IHG, Virtuoso
- 🏨 **Lodging type** — Resort, Boutique, Villa, Rental, All-Inclusive (or leave open)
- 💰 **Budget tier** — Budget through Ultra-Luxury

### Evaluation Dashboard (Hawaii 2026 pre-loaded)
- **5-dimension scoring** — Location, Design, Service, Family Suitability, Review Confidence
- **Live weight sliders** — Adjust scoring weights in real time; composite scores update instantly
- **Smart Type Adapter** — Resorts, boutiques, villas, and rentals scored on a normalized 100-point scale with type-specific weight redistribution (service excluded for rentals/villas)
- **Room type selector** — Per-property room categories with real names, sq footage, and bed config; family-recommended default with manual override
- **Full cost model** — Rack rate → taxes → resort fees → gross total → loyalty benefit deductions → effective total → effective nightly
- **Top 3 recommendations** — Score-ranked highlight cards
- **Review intelligence** — Positive themes, concern themes, family signal per property
- **Sort & filter** — By composite score, effective cost, gross cost; filter by lodging type; grid or list view
- **All-inclusive badge** — Flagged on applicable properties

### Research Output
- **⚡ Cowork Brief** — Compact structured parameters for paste into a Cowork/Claude session
- **🤖 Claude.ai Prompt** — Full prompt with embedded evaluation methodology; works with any Claude account

---

## What's in this repo

```
index.html              # Main tool (intake form + dashboard)
README.md               # This file
USER_GUIDE.md           # Non-technical guide for sharing with friends
skills/
  lodging-evaluator/
    SKILL.md            # Full reusable evaluation framework
```

---

## Pre-loaded data

**Oahu, Hawaii — Late September / Early October 2026**
4 nights · 2 adults + 1 toddler · Pool required

Properties evaluated (with researched room categories):
- Four Seasons Resort Oahu at Ko Olina
- JW Marriott Ihilani Ko Olina Resort & Spa
- Halekulani Hotel
- The Royal Hawaiian, A Luxury Collection Resort
- The Kahala Hotel & Resort
- Ka La'i Waikiki Beach, LXR Hotels & Resorts
- The Ritz-Carlton O'ahu, Turtle Bay

---

## Using for a new trip

1. Open the tool and fill out the intake form with your new destination and criteria
2. Click **Generate Research →**
3. Click **⚡ Cowork Brief** or **🤖 Claude.ai Prompt**
4. Paste into Claude — you'll get a scored shortlist back
5. To add results as a new dashboard, open a Cowork session, reference `skills/lodging-evaluator/SKILL.md`, and provide the research output

---

## Sharing with friends

Share the GitHub Pages URL. Friends click **🤖 Claude.ai Mode**, copy the prompt, and paste it into [claude.ai](https://claude.ai) (free account works). The full scoring methodology is embedded in the prompt so results match your standard.

See `USER_GUIDE.md` for a non-technical walkthrough to share alongside the tool.

---

## Skill file

`skills/lodging-evaluator/SKILL.md` is the portable evaluation framework that powers all research. It defines:
- The 5-dimension scoring model and weights
- Smart Type Adapter (cross-type normalization)
- Budget tier classification
- Loyalty benefit calculation formulas (FHR, Chase The Edit, Hyatt, Marriott, Hilton)
- Room type recommendation logic
- Review intelligence extraction methodology
- Cost rollup formula
- Workflow for adding new trips to the dashboard

This file does **not** need to be re-uploaded to GitHub on every update — it only changes if you modify the evaluation framework itself.
