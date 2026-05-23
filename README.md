# Lodging Evaluator — Travel Intelligence Tool

> Cut through the noise. Score what matters. Know the real cost before you book.

A personal travel lodging research tool that combines a structured intake form with AI-powered research output. Instead of drowning in aggregator results and star ratings, you define your criteria — then get a scored, cost-modeled shortlist of properties ranked against what actually matters to you. Supports luxury hotels, boutique properties, and curated vacation rentals (Plum Guide, onefinestay) in the same unified comparison.

---

## How it works

**1. Fill out the intake form**
Enter your destination, travel dates, travelers, non-negotiables, reward programs, lodging preferences, and whether to include hotels, curated rentals, or both.

**2. Generate a research prompt**
The tool produces a structured research request — either a compact Cowork brief or a full Claude.ai prompt with the evaluation methodology embedded. Both now include a JSON output schema Claude will fill in.

**3. Paste into Claude, get your shortlist + JSON**
Claude researches and scores properties against your exact criteria, returns a full narrative shortlist, then appends an importable JSON block at the end.

**4. Import to dashboard**
Copy the JSON block from Claude's response → click **⬆⬇ Trips** in the dashboard → paste into Import → your new trip loads as a fully scored dashboard alongside any previous trips.

---

## Two usage paths

| | Cowork Mode | Claude.ai Mode |
|---|---|---|
| **Who** | Tool owner (you) | Friends & family |
| **How** | Paste brief into Cowork session | Paste prompt into claude.ai (free account works) |
| **Output** | Full scored dashboard via import | Scored shortlist with cost breakdown in chat |
| **Cost** | Uses your Cowork session | Uses their own Claude account |

---

## Features

### Intake Form
- 🔍 **Destination search** — Predictive input across 150+ curated worldwide destinations
- 📅 **Visual calendar picker** — Two-month range selector with night count; stays open while you navigate
- 👥 **Traveler counters** — Adults and children with independent controls
- 🚫 **Non-negotiables** — Tap-to-select amenity chips (pool, beach, spa, gym, kids' club, etc.) + custom add
- 💳 **Reward programs** — Amex FHR, Chase The Edit, World of Hyatt, Marriott Bonvoy, Hilton Honors, IHG, Virtuoso
- 🏨 **Lodging type** — Resort, Boutique, Villa, Rental, All-Inclusive (or leave open)
- 💰 **Budget tier** — Budget through Ultra-Luxury
- 🔎 **Research scope** — Toggle Hotels, Curated Rentals (Plum Guide, onefinestay), or Both

### Evaluation Dashboard
- **Multi-trip storage** — All trips saved locally in your browser; switch between them via the trip selector
- **Import / Export** — Import any Claude-generated JSON to add a new trip; export any trip as a JSON file to share
- **5-dimension scoring** — Location, Design, Service/Host Quality, Family Suitability, Review Confidence
- **Live weight sliders** — Auto-balance to 100%; composite scores update instantly across all cards
- **Smart Type Adapter** — Hotels and rentals scored on a normalized 100-point scale; service weight excluded for rentals and redistributed proportionally
- **Rental cost model** — Cleaning fees and platform service fees amortized across nights into a true effective nightly rate
- **Room type selector** — Per-property room categories with real names, sq footage, and bed config; family-recommended default with manual override
- **Full hotel cost model** — Rack rate → taxes → resort fees → gross → loyalty benefit deductions → effective total → effective nightly
- **Top 3 recommendations** — Score-ranked highlight cards with property photos where available
- **Review intelligence** — Positive themes, concern themes, family signal per property
- **Sort & filter** — By composite score, effective cost, or gross cost; filter All / Hotels / Rentals; grid, list, or table view
- **Type badges** — Hotel properties shown in blue; rental properties (Plum Guide, onefinestay, etc.) in green

### Research Output
- **⚡ Cowork Brief** — Compact structured parameters for paste into a Cowork/Claude session
- **🤖 Claude.ai Prompt** — Full prompt with embedded evaluation methodology; works with any Claude account
- Both outputs include the importable JSON schema so Claude returns dashboard-ready data

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

1. Open the tool and fill out the intake form with your destination, dates, and criteria
2. Set **Research** toggles: Hotels, Curated Rentals, or Both
3. Click **Generate Research →**
4. Choose **⚡ Cowork Brief** or **🤖 Claude.ai Prompt** and copy it
5. Paste into Claude — you'll get a scored narrative response followed by a JSON block
6. Copy the JSON block (everything between the ` ```json ` and ` ``` ` markers)
7. Back in the tool, click **⬆⬇ Trips** → paste into the Import panel → click **Import Trip**
8. Your new trip loads instantly as a full scored dashboard; use the trip selector to switch between trips

---

## Sharing a trip comparison

Trip data lives in your browser's localStorage — it doesn't travel with the URL. To share a specific trip:

1. Open the trip you want to share in the dashboard
2. Click **⬆⬇ Trips** → use **Download JSON** or **Copy to Clipboard**
3. Send the JSON file (or paste) to the other person
4. They open the tool, click **⬆⬇ Trips** → Import, paste the JSON, and get your full comparison

To share the tool itself, share the GitHub Pages URL. Friends use **🤖 Claude.ai Mode** and a free Claude account — the full scoring methodology is embedded in the prompt.

See `USER_GUIDE.md` for a non-technical walkthrough.

---

## Skill file

`skills/lodging-evaluator/SKILL.md` is the portable evaluation framework that powers all research. It defines the 5-dimension scoring model, Smart Type Adapter, budget tier classification, loyalty benefit formulas, room recommendation logic, review intelligence methodology, and cost rollup formula.

This file does **not** need to be re-uploaded to GitHub on every update — it only changes if you modify the evaluation framework itself.
