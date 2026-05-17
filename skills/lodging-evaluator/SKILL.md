# Lodging Evaluator — SKILL.md v2

## Purpose
Reusable skill for evaluating lodging options for any trip. Produces a self-contained, interactive HTML dashboard with live scoring, room type selector, amenities checklist, loyalty/card benefit calculation, and rolled-up cost view. Supports hotels, resorts, boutique hotels, villas, and rentals in a single unified view.

---

## Step 1 — Collect Trip Parameters

Ask the user for:
- Destination (city, region, country)
- Travel dates and duration (nights)
- Traveler profile (adults, children, ages)
- Non-negotiables (pool, beach access, full kitchen, pet-friendly, etc.)
- Accommodation preference (resort, boutique, rental, or all types)
- Budget orientation (Solid $250-400 / Premium $400-700 / Luxury $700-1100 / Ultra $1100+)
- Active loyalty/card programs (see Step 6)
- Special considerations (accessibility, proximity to attractions, quiet vs. energetic)

---

## Step 2 — Accommodation Tier Reference

| Tier | Description |
|------|-------------|
| Upscale Independent | Design-forward boutique, strong reviews, independent ownership |
| Lifestyle Brand | W, Andaz, Kimpton — brand-backed boutique energy |
| Classic Luxury Resort | JW Marriott, Hilton, Westin, Ritz-Carlton |
| Ultra-Premium | Four Seasons, Aman, Rosewood, Six Senses, independent ultra-luxury |

---

## Step 3 — Budget Tier Reference

| Tier | Nightly Rate | Value Elasticity |
|------|-------------|-----------------|
| Solid | $250–400 | Standard expectations |
| Premium | $400–700 | Elevated amenities expected |
| Luxury | $700–1100 | Full-service, exceptional design |
| Ultra | $1100+ | No compromises |

Value Elasticity: A property scoring above its price tier should be flagged as a **Value Find**.

---

## Step 4 — Lodging Type Classification

Use `type` field in property data:
- `resort` — full-service resort with hotel-style service
- `boutique` — smaller independent or lifestyle-brand hotel
- `villa` — private villa rental, typically high-end
- `rental` — AirBnB, VRBO, or similar self-catered rental

**Trip Mode filter behavior:**
- "Hotels & Resorts" shows type: resort or boutique
- "Rentals" shows type: villa or rental

---

## Step 5 — Scoring Model

Five dimensions, each scored 0–10:

| Dimension | What to assess |
|-----------|---------------|
| Location & Access | Proximity to trip goals, transport, walkability |
| Design & Experience | Aesthetic quality, ambiance, architectural distinction |
| Service | Staff quality, responsiveness, personalization (exclude for rentals/villas) |
| Family / Toddler Fit | Child infrastructure, pools, programming, safety, stroller access |
| Review Confidence | Composite of consumer rating × review volume (see Step 6) |

**Default weights by type:**

| Type | Location | Design | Service | Family | Review |
|------|----------|--------|---------|--------|--------|
| Resort/Hotel | 20% | 20% | 30% | 15% | 15% |
| Boutique | 25% | 35% | 25% | 15% | — |
| Villa/Rental | 35% | 35% | 0% | 20% | 10% |

For rentals/villas: Service weight is excluded and redistributed proportionally across remaining dimensions.

Weights are user-adjustable via live sliders in the dashboard. Composite score recalculates in real time.

---

## Step 6 — Review Intelligence Layer

For each property, capture:
- **Rating** (0–10 scale, normalize if needed)
- **Review volume** (number of reviews on TripAdvisor/Google)
- **Review Confidence score** = normalize(rating × log(volume))
- **Positive theme clusters** — top 3 recurring praise themes
- **Concern theme clusters** — top 2–3 recurring criticism themes
- **Family/toddler signal** — specific mentions of children, cribs, pools, strollers
- **Recency weighting** — note if reviews skew old vs. recent

---

## Step 7 — Loyalty & Card Benefit Layer

Track five programs. Hard-dollar benefits only count for properties that officially participate.

| Program | Hard Benefits | Soft Benefits |
|---------|--------------|---------------|
| Amex Fine Hotels + Resorts (FHR) | Daily breakfast (~$90–95/room/day) + $100 property credit | Room upgrade, early check-in, late checkout |
| Chase Sapphire The Edit | Daily breakfast (~$90/room/day) + $100 experience credit | Room upgrade, early check-in |
| Hyatt World of Hyatt | Points only (unless award night) | Status upgrades |
| Marriott Bonvoy | Points only (unless award night) | Status upgrades |
| Hilton Honors | Points only (unless award night) | Diamond recognition |

**Double-Stack**: Flag properties where two programs apply simultaneously (e.g., Amex FHR + Bonvoy, Amex FHR + Hilton). These deliver the strongest combined value.

**Benefit value formula:**
- Breakfast benefit = `bkfstPerDay × nights` (per room, not per person)
- Credit benefit = one-time stay credit
- Total benefit = breakfast + credit

---

## Step 8 — Room Type Data

For each property, collect 3–4 room configurations:

```javascript
rooms: [
  { name: 'Standard Room Name', rate: 000, familyRec: false },
  { name: 'Recommended Room', rate: 000, familyRec: true },  // default for traveler profile
  { name: 'Suite Option', rate: 000, familyRec: false },
  { name: 'Premium Suite', rate: 000, familyRec: false }
]
```

- `familyRec: true` on the room most appropriate for the traveler profile (family with toddler = suite or connecting room)
- User can override to any room type; cost model updates live
- Room selector shows "★" next to recommended option

---

## Step 9 — Amenities Checklist

Standard amenity keys (boolean per property):

```
pool, spa, gym, beach, restaurant, roomService, childcare, waterSports, bar, fullKitchen, privatePool, parking
```

Expand for rental/villa context: add `washer`, `bbq`, `hotTub`, `workspace`, `petsAllowed` as needed.

**Non-negotiables**: Defined per trip. Any property missing a non-negotiable gets a ⚠️ badge.

---

## Step 10 — All-Inclusive Flag

Set `allInclusive: true/false` on each property. When true, a badge displays on the card. No cost model change — user accounts for F&B value mentally.

---

## Step 11 — Rolled-Up Cost View

Per property, compute with the selected room type:

```
Base rate (rack × nights)
+ Hawaii taxes (or destination-specific tax rate)
+ Resort fee (per night × nights, or $0 if confirmed waived)
= GROSS TOTAL
− Hard benefit deductions (breakfast + credit if applicable)
= EFFECTIVE TOTAL
÷ nights = Effective Nightly Rate
```

Hawaii tax rate: ~14.96% (GET 4.712% + TAT 10.25%)
Update tax rate per destination. Common rates: NYC ~14.75%, Miami ~13%, Paris ~7%, Tokyo ~10%.

---

## Step 12 — Output Format

### Property Data Object Template

```javascript
{
  id: 'unique-id',
  name: 'Property Name',
  subtitle: 'Brand or Descriptor (optional)',
  type: 'resort|boutique|villa|rental',
  tier: 'Ultra-Premium|Classic Luxury|Upscale Independent|Lifestyle Brand',
  zone: 'zone-slug',
  allInclusive: false,
  gradient: 'gradient-{id}',  // CSS gradient class for photo fallback
  photoUrl: null,              // or CDN image URL if available
  galleryUrl: 'https://...',
  bookingUrl: 'https://...',
  bookingLabel: 'Book Direct|Book / Bonvoy|etc.',
  taUrl: 'https://www.tripadvisor.com/...',
  gUrl: 'https://www.google.com/maps/search/...',
  programs: { fhr: bool, bonvoy: bool, hyatt: bool, hilton: bool, chase: bool },
  doubleStack: bool,
  scores: { location: 0-10, design: 0-10, service: 0-10, family: 0-10, review: 0-10 },
  reviews: {
    rating: 0.0,
    count: 000,
    positives: ['Theme 1', 'Theme 2', 'Theme 3'],
    concerns: ['Concern 1', 'Concern 2'],
    familySignal: 'Strong|Moderate|Weak — explanation'
  },
  amenities: { pool: bool, spa: bool, gym: bool, beach: bool, restaurant: bool,
               roomService: bool, childcare: bool, waterSports: bool, bar: bool,
               fullKitchen: bool, privatePool: bool, parking: bool },
  rooms: [
    { name: 'Room Type', rate: 000, familyRec: bool }
  ],
  resortFee: 0,
  taxRate: 0.1496,
  benefit: { program: 'fhr|chase|bonvoy|hilton|hyatt|null', bkfstPerDay: 0, credit: 0, notes: '' },
  top3why: 'Why this appears in Top 3 (null if not top 3)',
  description: 'One-line property summary'
}
```

### Trip Data Object Template

```javascript
{
  id: 'destination-year',
  name: 'City, Country',
  emoji: '🌍',
  dates: 'Month Range Year',
  nights: 0,
  travelers: { adults: 0, children: 0, childAges: [] },
  travelersLabel: '2 adults + 1 toddler',
  nonNegotiables: ['pool'],
  programs: ['fhr','chase','bonvoy','hyatt','hilton'],
  programsLabel: 'Amex FHR · Chase The Edit · Bonvoy · Hyatt · Hilton',
  defaultWeights: { location: 20, design: 20, service: 30, family: 15, review: 15 },
  properties: [ /* property objects */ ]
}
```

---

## Step 13 — Adding a New Trip to the Dashboard

1. Collect parameters (Step 1)
2. Research 6–8 properties using Steps 4–11
3. Build new trip object following the template above
4. Add to the `TRIPS` object in the existing dashboard HTML: `TRIPS['new-trip-id'] = { ... }`
5. The trip switcher dropdown automatically picks it up — no other changes needed
6. Update `index.html` in the GitHub repo (drag-and-drop upload, then commit)

---

## Notes

- Composite score recalculates live as user adjusts sliders — do not hard-code it
- Top 3 section is dynamic (top 3 by current composite score) — `top3why` text is used when a property lands in top 3
- Room selector updates cost model live — room data must be accurate
- Photo sourcing: attempt to fetch property CDN images; fall back to CSS gradient with emoji if unavailable
- GitHub Pages deployment: single `index.html` file, public repo, Pages enabled from main branch root
