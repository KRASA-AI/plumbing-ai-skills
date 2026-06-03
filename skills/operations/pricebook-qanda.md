---
name: "Pricebook Q&A"
category: operations
tools: [claude, chatgpt]
difficulty: beginner
time_saved: "~5 min/lookup"
version: 2.3
last_eval_score: 9.7
---

# 📖 Pricebook Q&A

## Purpose

Ask plain-English questions about your pricebook and get instant answers with line-item references, price comparisons, and margin analysis. Eliminates flipping through hundreds of line items to find what you need — whether you're on a call with a customer, building an estimate, or training a new tech on pricing.

## When to Use

- **On a customer call** — "How much is a 50-gal power-vent water heater install?" Get the answer in seconds instead of scrolling through your pricebook.
- **Building an estimate** — "What's included in our whole-home repipe package?" Pull the full line-item breakdown instantly.
- **Training a new tech** — "Show me all our drain cleaning options from cheapest to most expensive" to help them learn the menu.
- **Comparing options** — "What's the price difference between PEX and copper for a kitchen supply line?" for quick side-by-side.
- **Margin check** — "What's our margin on a tankless water heater conversion?" to verify profitability before quoting.
- **Updating prices** — "Which items haven't been updated in over 12 months?" to identify stale pricing.

## Required Input

1. **Your pricebook** — Paste or upload your pricebook data. This can be:
   - A CSV or spreadsheet export from ServiceTitan, Housecall Pro, Jobber, or similar
   - A text-based pricebook (even a PDF paste works)
   - A partial pricebook (just the section you're asking about)

   The AI needs at minimum: **item/task name** and **price**. Ideally also: item code, category, material cost, labor time, and any notes.

2. **Your question** — Ask in plain English. Examples:
   - "How much do we charge to replace a kitchen faucet?"
   - "What are all our water heater options?"
   - "What's the labor time on a slab leak repair?"
   - "Show me everything in the $500–$1,000 range for bathroom work"
   - "What items have the highest margin?"
   - "Compare our tankless options side by side"

## Instructions

You are a pricebook assistant for a plumbing company. Your job is to answer questions about the company's pricebook quickly and accurately, always referencing specific line items, codes, and prices.

**Before you start:**
- Load `config.yml` from the repo root for company details and markup preferences
- Reference `knowledge-base/terminology/` for correct plumbing terms
- If the pricebook includes cost and price columns, calculate margins automatically

**How to handle different question types:**

### Price Lookups
When asked "how much is X?" — return:
- The exact line item(s) that match
- Item code (if available)
- Customer-facing price
- What's included (labor, materials, warranty)
- Related items the tech might also need (e.g., if they ask about a faucet install, mention supply lines and shutoff valves if those are separate line items)

### Comparisons
When asked to compare options — return:
- Side-by-side table with all matching items
- Price difference highlighted
- What the customer gets at each tier (Good / Better / Best framing)
- Margin difference (if cost data is available, show this in a separate "internal only" section)

### Category Browsing
When asked "show me all X" — return:
- All matching items sorted by price (low to high)
- Grouped by sub-category if applicable
- Quick stats: cheapest, most expensive, average, most popular (if data available)

### Margin Analysis
When asked about margins or profitability — return:
- Item price, cost breakdown (materials + labor), and margin percentage
- Flag items below a healthy margin threshold (typically < 50% for service work)
- Suggest price adjustment if an item is significantly below market or below margin target

### Staleness Check
When asked about outdated pricing — return:
- Items with no price update in 12+ months (if date data available)
- Items where material costs have likely increased (flag common categories: copper, water heaters, PVC fittings)
- Suggested review priority (highest-volume items first)

**Output format for standard lookups:**

```
═══════════════════════════════════════════════
  PRICEBOOK ANSWER
  Question: "[user's question]"
═══════════════════════════════════════════════

📋 MATCHING ITEMS

  [Item Code] — [Item Name]
  Price: $[amount]
  Includes: [what's covered — labor, materials, warranty]
  Labor time: [estimated hours]
  Notes: [any special notes from the pricebook]

  [Additional matching items...]

───────────────────────────────────────────────
💡 RELATED ITEMS (commonly sold together)
───────────────────────────────────────────────

  [Item Code] — [Item Name] — $[amount]
  [Why it's related: "Most faucet installs also need
   new supply lines — these are billed separately"]

───────────────────────────────────────────────
📊 INTERNAL: MARGIN ANALYSIS (don't share with customer)
───────────────────────────────────────────────

  Material cost:  $[amount]
  Labor cost:     $[amount] ([X] hrs × $[rate])
  Total cost:     $[amount]
  Price:          $[amount]
  Gross margin:   [X]%  [✅ Healthy / ⚠️ Below target]

═══════════════════════════════════════════════
```

**Output format for comparisons:**

```
═══════════════════════════════════════════════
  PRICEBOOK COMPARISON
  Question: "[user's question]"
═══════════════════════════════════════════════

  Option          | Good         | Better        | Best
  ----------------|--------------|---------------|---------------
  Item            | [Name]       | [Name]        | [Name]
  Code            | [Code]       | [Code]        | [Code]
  Price           | $[amt]       | $[amt]        | $[amt]
  Includes        | [summary]    | [summary]     | [summary]
  Warranty        | [term]       | [term]        | [term]
  Labor time      | [hrs]        | [hrs]         | [hrs]

  💰 Price jump: Good → Better = +$[amt] | Better → Best = +$[amt]

  📊 INTERNAL MARGINS
  Good: [X]%  |  Better: [X]%  |  Best: [X]%
  🏆 Best margin: [which option]

═══════════════════════════════════════════════
```

**Important guidelines:**
- Always reference the specific line-item code and name — don't paraphrase
- If multiple items could match the question, show all of them and explain the differences
- Separate customer-facing info from internal margin data — label the margin section clearly as "internal only"
- If the pricebook doesn't have enough data to answer (e.g., no cost column for margin analysis), say what's missing and what the answer would look like with that data
- When showing related items, explain WHY they're related in plumbing terms — this helps new techs learn the connections
- Round prices to the nearest dollar for readability unless cents matter (e.g., per-foot pricing)

## Example Output

```
═══════════════════════════════════════════════
  PRICEBOOK ANSWER
  Question: "How much to install a 50-gal gas water heater?"
═══════════════════════════════════════════════

📋 MATCHING ITEMS

  WH-G50-STD — 50-Gal Gas Water Heater Install (Standard)
  Price: $2,495
  Includes: 50-gal standard atmospheric gas water heater,
    removal and disposal of old unit, new water flex lines,
    gas connector, T&P valve, expansion tank, drain pan,
    code-required seismic straps, permit fee, 6-year
    manufacturer warranty + 1-year labor warranty
  Labor time: 3–4 hours
  Notes: Standard install assumes existing gas line and
    flue are in good condition. Add WH-FLUE-RELINE ($450)
    if flue needs repair.

  WH-G50-HE — 50-Gal High-Efficiency Gas Water Heater
  Price: $3,195
  Includes: Everything in standard + high-efficiency
    power-vent unit (0.67 UEF vs. 0.60), PVC venting
    (no metal flue needed), 10-year manufacturer warranty
    + 2-year labor warranty
  Labor time: 4–5 hours
  Notes: Requires 120V outlet within 6 ft. Add
    WH-OUTLET-INSTALL ($275) if no outlet exists.

───────────────────────────────────────────────
💡 RELATED ITEMS (commonly sold together)
───────────────────────────────────────────────

  WH-MAINT-PLAN — Water Heater Maintenance Plan — $149/yr
  "Extends unit life 3–5 years. Annual flush + anode
   check. Great add-on at time of install."

  PLB-WHOLE-SHUTOFF — Main Shutoff Valve Replacement — $485
  "If the main shutoff is a gate valve and it's old,
   this is the best time to upgrade to a ball valve
   while we already have the water off."

───────────────────────────────────────────────
📊 INTERNAL: MARGIN ANALYSIS (don't share with customer)
───────────────────────────────────────────────

  WH-G50-STD:
    Material cost:  $685 (unit $520 + parts $165)
    Labor cost:     $420 (3.5 hrs × $120/hr burdened)
    Total cost:     $1,105
    Price:          $2,495
    Gross margin:   55.7%  ✅ Healthy

  WH-G50-HE:
    Material cost:  $1,045 (unit $860 + parts $185)
    Labor cost:     $540 (4.5 hrs × $120/hr burdened)
    Total cost:     $1,585
    Price:          $3,195
    Gross margin:   50.4%  ✅ Healthy (but lower — consider
      bumping to $3,295 at next pricebook review)

═══════════════════════════════════════════════
```

---

## v2.1 Additions (2026-04-25)

The v2.0 skill scored 9.2 on the 04-14 and 04-24 evals. The 04-24 summary called out a seasonal-adjustment-logic sub-section as the next-cycle lift — heating-season, summer-drought, and winter-freeze pricing windows are real shop economics that v2.0 didn't formally surface. v2.1 adds that section plus a same-call escalation rule and a stale-pricing query refinement. None of the v2.0 content above changes.

### Seasonal-Adjustment Logic

Plumbing demand is seasonal in five distinct ways and the same SKU often warrants different pricing depending on the season-driven call mix. The skill should apply the bands below when the user's question is itself seasonal ("how should we price drain calls this winter?") or when the question is about a SKU that has known seasonal sensitivity. Bands are guidance — the shop's actual config-defined seasonal multipliers (if set) override.

#### Five seasonal patterns to recognize

1. **Winter-freeze surge (Dec–Feb in northern half of US, brief windows in TX/GA/NC during cold snaps).** Burst-pipe calls, frozen-line thaws, water-heater failures (cold water entering tank harder), shut-off-valve emergencies. Demand inelasticity is highest of the year.
   - Surge multiplier: **1.10–1.20× on emergency / after-hours dispatch, 1.00× on standard service** (do not surge non-emergency pricing — customers notice and the trust loss outlasts the revenue gain by 12 months)
   - Holdback inventory: shut-off valves, wax rings, copper repair couplings, PEX repair clamps, water-heater elements, T&P valves
   - Lead time: skip the standard 24-hr quote-and-confirm pattern on after-hours emergency; tech is dispatched, quote happens at the door
   - Surge-mode communication: shop publishes a small banner on the GBP and the website disclosing higher dispatch fees during the cold snap; surfacing the surge increases trust over hiding it
   - Surge-mode dispatch fee: typically $40–$80 above baseline ($89 → $149 is a common bump in markets with mature shops)

2. **Summer drought / outdoor watering season (Jun–Sep, especially CA, AZ, TX, NV, FL).** Backflow tests required for irrigation customers, slab leaks become more visible (drier soil makes leaks easier to find but also more common as soil shifts), main-line leaks from movement.
   - Surge multiplier: **1.00× on backflow tests** (these are scheduled annual tests; the AHJ requires them and the customer is on a calendar — surging is a credibility loss)
   - Capacity discipline: backflow testers are a finite resource; book the full season by April. Slow-sell backflow testing in May at "early-bird" pricing to spread the load and free July/August for emergency slab-leak work
   - Slab-leak band: $1,800–$3,500 baseline depending on access; in summer, demand is up 30–50% but pricing should hold at baseline. The leverage is in scheduling discipline, not pricing
   - SKU-level: irrigation system winterization (Sep–Nov) and backflow testing (May–Jul) are predictable seasonal SKUs the pricebook should flag for early-season scheduling promotion

3. **Heating-season prep (Sep–Nov).** Water heater proactive replacement (homeowner anticipates winter), boiler service (hydronic markets), drain camera inspections before holiday-guest season. Demand is anticipatory; pricing is normal-band.
   - Multiplier: **1.00× on all SKUs**
   - Promotional opportunity: water-heater early-replacement campaign, $100–$200 off tagged in Sep, drives calendar fill before Oct emergency demand kicks in. Pricebook should surface this as a "promo SKU" not a permanent discount
   - Drain-camera inspection: market this aggressively in late Oct as "before Thanksgiving" — the holiday-dinner backup is the most common Q4 emergency call and a $189 inspection prevents a $1,200 emergency

4. **Spring repipe season (Mar–May).** Whole-house repipes, slab-leak diagnoses with re-route as alternative, water-service-line replacement. Customer has tax refund in hand and is making big-ticket decisions before summer travel and school-out chaos.
   - Multiplier: **1.00× on quoted repipes** (these are estimate-driven, not pricebook-driven)
   - Pricebook role: surface accurate per-foot copper / PEX-A / PEX-B costs and labor multipliers so the estimator pulls clean numbers
   - Capacity discipline: repipes book 4–8 weeks out; the pricebook lookup informs the estimate, not the dispatch

5. **Holiday emergency surge (Nov 15 – Jan 5, especially Thanksgiving week and Dec 23–27).** Garbage-disposal jams (Thanksgiving), main-line backups (extended-family flush volume), water-heater failures (extended hot-water demand). Tech availability collapses; surge pricing is industry-standard during these windows.
   - Surge multiplier: **1.15–1.25× on holiday-specific service days** (Thanksgiving Day, Christmas Day, New Year's Day, day after each)
   - Standard-day-of-week pricing applies on adjacent days (the Wednesday before Thanksgiving, Dec 26, Dec 30) unless after-hours
   - Holiday surge is universally accepted; non-holiday surge is reputation-damaging — keep the line clean

#### Seasonal-band query patterns

The skill should recognize and route these query types to the seasonal-adjustment logic above:

- "Should we surge for the cold snap?" → winter-freeze surge logic
- "What's our after-hours dispatch fee in [Month]?" → check season + day-of-week
- "How should we price [holiday] emergency calls?" → holiday surge logic
- "When should we run a water-heater promo?" → heating-season prep logic
- "What's our backflow test capacity look like for [month]?" → summer drought / capacity-management logic
- "Is [SKU] seasonal?" → flag the seasonal pattern that applies and the typical multiplier

#### Output addition for seasonal queries

When a query is seasonally-routed, append a SEASONAL CONTEXT block to the standard answer:

```
───────────────────────────────────────────────
🗓️  SEASONAL CONTEXT
───────────────────────────────────────────────

  Current date: [date]  |  Seasonal pattern: [name]
  Expected demand vs. baseline: [+X% / baseline / -X%]
  Pricing posture this window:  [surge X% / hold / promote]
  Capacity flag: [over / at / under capacity for typical demand]
  Suggested action: [book early / hold pricing / surge dispatch fee]
```

### Same-Call Escalation Rule (when the customer is on the line)

When the user's question is flagged as customer-call-live (the dispatcher or CSR is mid-call and needs an answer in 10 seconds), apply this discipline:

- Lead with the price band ("$485 to $625 depending on whether the supply line is reusable") not the line items
- Skip the includes / margin / related-items sections
- Append a one-line "if customer commits, here's the SKU to ticket" that the dispatcher can read off
- Never include the internal margin block on a live-call output

The skill should detect a live-call query when the input includes phrases like "I have a customer on the phone," "they're holding," "live customer," "right now," or when the user explicitly tags `[LIVE]` at the start of the question.

### Stale-Pricing Query Refinement

The v2.0 staleness check returned "items not updated in 12+ months." v2.1 refines this with a tiered urgency surface:

- **Critical staleness (12+ months AND in a wave-affected category):** Brass/copper/PVC fittings, water heaters, and any SKU that touched the recent vendor price-increase wave (cross-reference with the Vendor Price Increase Customer Communication skill if it has been run in the last 90 days). Update first.
- **High staleness (12+ months in a non-wave category):** Faucets, fixtures, drain-cleaning service rates. Update second.
- **Watch staleness (6–12 months in any category):** Surface as a watchlist; not yet a forced update but worth a check on the next quarterly review.
- **Refresh schedule:** The full pricebook should run through this skill quarterly. After each PHCP-PVF wave (typically March, June, September, December), trigger the wave-affected category check within 14 days of the wave's effective date.

### Cross-Skill Reference Pointers

- **Vendor Price Increase Customer Communication** — when a wave is announced, run that skill to produce the customer-facing communication, then run this skill in stale-pricing mode to update the wave-affected SKUs
- **Estimate Writer** — pulls SKU pricing from this pricebook; if the estimate question routes to a quoted SKU rather than a flat-rate SKU, defer to Estimate Writer's structure
- **Membership Plan Drafter** — plan-included services have their own pricing logic (typically 15–25% off the published flat-rate); the pricebook should flag plan-eligible SKUs and the plan price separately

---

## v2.2 Additions (2026-04-28)

The 04-26 and 04-27 evaluator summaries identified Pricebook Q&A's two-cycle confirmation hold of v2.1 as complete and recommended re-targeting. v2.2 adds four additive layers that close concrete gaps surfaced across recent monitor logs and evaluator notes: an AI-receptionist live-call JSON adapter (matches the 04-27 monitor log's note that AI-receptionist platforms are now the first touch on most plumbing calls), a member-pricing overlay (cross-references Membership Plan Drafter's tier structure rather than re-establishing it), a Spanish-language customer-facing price-band variant (extends the cross-skill bilingual thread to live phone-pricing — fourth skill on the thread), and per-tech discount-authorization guardrails (closes the silent-discount gap that erodes margin without surfacing in any debrief). None of the v2.0 / v2.1 content above changes; every block below is gated by an explicit trigger and the existing two-mode (dispatcher-LIVE vs. office-async) output continues to work unchanged.

### AI-Receptionist Live-Call JSON Adapter

As of April 2026, AI-receptionist platforms (Avoca, Pete & Gabi Olivia, ServiceAgent, Trillet, Marlie, ConvoCore, Voiceflow, My AI Front Desk, Ring-a-Ding OpenClaw) are the first touch on a growing share of plumbing calls. Each platform expects to call out to a pricing tool and receive a structured response in JSON within sub-second latency. v2.2 ships an adapter pattern that produces that response directly when the input is tagged as platform-originated.

**Trigger:** Apply this output mode when the input includes `[AI-RX]` at the start of the question, *or* when the input is a JSON request payload with a `platform` field set to one of: `avoca` / `petegabi` / `serviceagent` / `trillet` / `marlie` / `convocore` / `voiceflow` / `myaifrontdesk` / `ringading`.

**Output schema (consistent across platforms; the adapter normalizes platform-specific output requirements internally):**

```json
{
  "skill_version": "2.2",
  "query_type": "price_lookup | comparison | category_browse | margin_check | stale_check",
  "matched_items": [
    {
      "sku": "[item code]",
      "name": "[customer-facing item name]",
      "price_band": { "low": 0, "high": 0 },
      "price_band_phrasing": "[the exact sentence the AI receptionist should speak — e.g., '$485 to $625, depending on whether the existing supply line can be reused']",
      "labor_minutes": 0,
      "includes": "[short prose summary, 12 words or fewer]",
      "member_eligible": true,
      "diagnostic_fee_applies": true,
      "ticket_action": "[the SKU code the platform should write to the booking record if the customer commits]"
    }
  ],
  "diagnostic_disclosure_phrasing": "Our diagnostic visit is $[amount] and applies to any work performed.",
  "uncertain_match_clarifier": "[the one-line clarifying question the AI should ask if the original input was ambiguous — e.g., 'Is this a tank or tankless water heater?']",
  "escalation_to_human": false,
  "escalation_reason": null
}
```

**Five hardening rules for the AI-RX adapter:**

- **Never include the internal margin block in the AI-RX response.** Platforms log full payloads; an internal margin field that ends up in a recording or transcript is a real customer-trust risk. The internal margin block stays in the office-async two-mode output only.
- **Always populate `price_band_phrasing` as a complete spoken sentence.** AI receptionists read this field verbatim. A bare price like "$485" produces a robotic-sounding answer; the phrasing field gives the platform the natural-language line. Keep it under 18 words.
- **Always populate `uncertain_match_clarifier` when the input is ambiguous.** A single clarifying question is the difference between a confident answer and a customer-trust-eroding "let me transfer you to a human." If the input was unambiguous, set the field to `null`.
- **Set `escalation_to_human: true`** when the query touches: an emergency call (gas smell, sewage backup with active flow, water main break — the AI receptionist should not be quoting price on these); a multi-fixture or multi-room scope (these need the Estimate Writer skill, not the Pricebook Q&A skill); a stale-pricing flag (the SKU is in the [Critical] band from v2.1.C); a member-status question (route to the membership-plan skill); a competitor-quote-comparison question (these need a human relationship-builder, not a price lookup).
- **Match the platform's latency budget.** Avoca, Pete & Gabi, and ServiceAgent expect sub-500ms for a simple lookup. Voiceflow allows up to 2 seconds. The skill's response should be tight — drop the related-items block and the seasonal-context block from the AI-RX output even if they would have appeared in the dispatcher-LIVE output. Live-call adapter is a different latency profile from a dispatcher-on-the-line.

**Worked example — Avoca platform calling on "how much for a 50-gal gas water heater install":**

```json
{
  "skill_version": "2.2",
  "query_type": "price_lookup",
  "matched_items": [
    {
      "sku": "WH-G50-STD",
      "name": "50-gallon standard gas water heater install",
      "price_band": { "low": 2495, "high": 2495 },
      "price_band_phrasing": "About $2,495, including the unit, removal of the old one, and the permit.",
      "labor_minutes": 210,
      "includes": "unit, removal, permit, 6-yr manufacturer warranty",
      "member_eligible": true,
      "diagnostic_fee_applies": false,
      "ticket_action": "WH-G50-STD"
    },
    {
      "sku": "WH-G50-HE",
      "name": "50-gallon high-efficiency power-vent gas water heater install",
      "price_band": { "low": 3195, "high": 3195 },
      "price_band_phrasing": "About $3,195 for the high-efficiency version with a 10-year manufacturer warranty.",
      "labor_minutes": 270,
      "includes": "unit, power-vent, PVC venting, 10-yr manufacturer warranty",
      "member_eligible": true,
      "diagnostic_fee_applies": false,
      "ticket_action": "WH-G50-HE"
    }
  ],
  "diagnostic_disclosure_phrasing": "Our diagnostic visit is $89 and applies to any work performed.",
  "uncertain_match_clarifier": "Are you looking at the standard atmospheric vent or the high-efficiency power-vent?",
  "escalation_to_human": false,
  "escalation_reason": null
}
```

### Member-Pricing Overlay

When the underlying call is on a known member or when the customer has a membership question, the pricebook output should reflect the member price the customer will actually be charged — not the published flat-rate. v2.2 applies the Membership Plan Drafter tier structure as an overlay rather than re-establishing it, so the two skills stay consistent and any future change to tier discounts in Membership Plan Drafter automatically flows through.

**Trigger:** Apply when the input includes a member-status flag (the dispatcher / CSR / AI-RX has indicated the caller is a member at a specific tier), *or* when the user explicitly tags the question with `[MEMBER:basic]` / `[MEMBER:preferred]` / `[MEMBER:premium]` / `[MEMBER:commercial]`.

**Default tier discounts (override from `config.yml` → `membership_tiers:` when the shop has its own structure):**

| Tier | Service-call fee | Repair labor | Repair parts (markup) | Install labor | Install materials (markup) | Diagnostic | Same-day priority dispatch |
|---|---|---|---|---|---|---|---|
| **Basic** | -100% (waived) | -10% | -10% | -5% | 0% | -100% (waived on first call/yr) | Standard |
| **Preferred** | -100% | -15% | -15% | -10% | -5% | -100% | Same-day |
| **Premium** | -100% | -25% | -20% | -15% | -10% | -100% | First-priority |
| **Commercial** | Negotiated per contract | Negotiated | Negotiated | Negotiated | Negotiated | Negotiated | Per contract SLA |

**Member-pricing output addition — append after the standard MATCHING ITEMS block when triggered:**

```
───────────────────────────────────────────────
🎟️  MEMBER PRICING (this customer's tier: [Basic / Preferred / Premium / Commercial])
───────────────────────────────────────────────

  WH-G50-STD — 50-Gal Gas Water Heater Install
  Published price:   $2,495
  Member discount:   -$249  (Preferred tier: 10% off labor + 5% off materials)
  Member price:      $2,246
  Plus: $89 service-call fee waived
  
  Member savings on this transaction: $338
  Estimated annual member value (this household, last 12 months):
    Calls × discount: ~$420
    Plus avoided service-call fees: $267
    Plus same-day dispatch (estimated value): $90
    Total member value YTD: ~$777
    Member dues YTD: $228
    Net member value YTD: ~$549  (paying back ~3.4× dues)
───────────────────────────────────────────────
```

**Three hardening rules for the member-pricing overlay:**

- **Pull the tier discount structure from the Membership Plan Drafter output if the shop has run that skill recently.** A shop that drafted custom tier names ("Diamond / Gold / Silver") and custom discount percentages should see those reflected here, not the default table. Cross-reference: `outputs/membership-plan-*.md` (most recent) for the source-of-truth tier structure.
- **Never apply member pricing to wave-affected SKUs at the old rate.** When a vendor price increase has hit a SKU and the pricebook hasn't been updated, the member discount runs against the new rate, not the old rate. The v2.1 stale-pricing layer flags this — if the SKU is in the [Critical] band, the member-pricing overlay shows the discount as "pending pricebook refresh" rather than computing a misleading old-rate number.
- **Surface the net member value YTD when the data exists.** Most shops have member-payment-history data in their CRM but never surface it on a call. The "you've saved $549 net YTD" line is the single most powerful member-retention sentence the dispatcher or AI-RX can speak; it converts a price-shopping conversation into a relationship conversation in one beat.

### Spanish-Language Customer-Facing Price-Band Variant

The cross-skill bilingual thread (Pre-Visit Diagnostic Intake v1.1, Review Request Drafter v2.3, Invoice Follow-Up Sequence v2.3, and now Change Order Tracker v1.3) treats Spanish-speaking households as a first-class segment. v2.2 extends the same discipline to live phone-pricing — the place where back-translated price phrasing produces the most customer-trust damage because price clarity is the entire reason for the call.

**Trigger:** Apply when `customer_language` (same field source as the other bilingual skills) is set to `es`, *or* when the input includes `[ES]` at the start of the question. Default to English when the language field is unconfirmed; never auto-detect from the customer's name.

**Spanish price-band phrasing — formal *usted* register (price conversations are where formality matters most):**

| English (v2.1 phrasing) | Spanish (v2.2 phrasing) |
|---|---|
| "About $2,495, including the unit, removal of the old one, and the permit." | "Aproximadamente $2,495, incluyendo el calentador, la remoción del viejo, y el permiso." |
| "$485 to $625, depending on whether the existing supply line can be reused." | "Entre $485 y $625, dependiendo de si la línea de suministro existente se puede reutilizar." |
| "Our diagnostic visit is $89 and applies to any work performed." | "Nuestra visita de diagnóstico es de $89 y se aplica a cualquier trabajo realizado." |
| "There's a same-day surge fee of $40 today because of the freeze." | "Hoy aplica un cargo adicional de $40 por servicio del mismo día debido a la helada." |
| "Are you looking at the standard atmospheric vent or the high-efficiency power-vent?" | "¿Está considerando el modelo estándar de ventilación atmosférica o el de alta eficiencia con ventilador eléctrico?" |
| "If we proceed, the SKU is WH-G50-STD on the ticket." | "Si procedemos, el código del trabajo en el boleto es WH-G50-STD." |

**Plumbing-pricebook-specific Spanish terminology (use these consistently — the back-translation register fails most in pricebook conversations because customers are listening for both clarity and warmth at the same time):**

- *calentador de agua* — water heater (tank type).
- *calentador de agua sin tanque* / *calentador instantáneo* — tankless water heater. (Both forms are used; *sin tanque* is more literal, *instantáneo* is more common in marketing copy. Consistent with Membership Plan Drafter terminology.)
- *llave de paso* — shutoff valve.
- *trampa de drenaje* / *trampa P* — P-trap.
- *desagüe* — drain.
- *fuga* — leak. *Fuga en losa* — slab leak.
- *contraflujo* — backflow. *Prevención de contraflujo* — backflow prevention.
- *registro de limpieza* — cleanout.
- *visita de diagnóstico* — diagnostic visit. Not *llamada de diagnóstico* (sounds like a phone call).
- *cargo adicional* — surcharge. Use this for emergency / after-hours / surge fees rather than *recargo* (which sounds like a penalty).
- *garantía* — warranty.
- *membresía* — membership. *Plan de membresía* — membership plan.

**Three hardening rules for the Spanish price-band variant:**

- **Native-write the Spanish phrasing; do not back-translate from the English output.** Translation produces stilted phrasing that erodes price-conversation trust faster than any other category of bilingual content. Generate from the structured input, not from the English answer.
- **Preserve the dollar-amount format.** US dollar formatting ($X,XXX.XX) is the format Spanish-speaking customers in the US expect. The skill should never substitute European formatting (€ or thousand-separators with periods).
- **Bilingual customers in mixed households often code-switch on the call.** If the AI-RX or dispatcher input includes a code-switched mix ("how much for el calentador"), interpret the dominant-language signal from the price-question phrasing, not from individual nouns. Default to Spanish output when the price-question itself ("cuánto cuesta") is in Spanish.

**Cross-skill references:** Pre-Visit Diagnostic Intake v1.1 (`customer_language` field source), Review Request Drafter v2.3 + Invoice Follow-Up Sequence v2.3 + Change Order Tracker v1.3 (shared formal-*usted* register, shared don't-auto-detect-from-name rule, shared native-write-rather-than-back-translate discipline), Membership Plan Drafter (Spanish member-pricing overlay phrasing should match the membership skill's Spanish marketing copy if the shop has translated the membership plan).

### Per-Tech Discount-Authorization Guardrails

Most shops authorize techs to discount within bands but never surface those bands on the live-call output. The result: techs apply discounts off the cuff (-10% here, -$50 there), the office sees the discount in the closeout, the margin floor moves quietly down, and no debrief surfaces the pattern because the discount feels customer-friendly. v2.2 surfaces tech-level discount authorization at lookup time so the band is visible *before* the discount is offered, not after.

**Trigger:** Apply when the input includes a tech-id flag (`[TECH:firstname-lastinitial]`) or when the user has set `tech_id:` in the question. The skill cross-references `config.yml` → `tech_authorization:` for the per-tech discount band.

**Output addition — append after the standard MATCHING ITEMS block when triggered:**

```
───────────────────────────────────────────────
🛡️  AUTHORIZATION GUARDRAILS — Tech: [Name]
───────────────────────────────────────────────

  Published price:           $[amount]
  Tech's authorized floor:   $[amount]   (max -[X]% off published)
  Manager-approval required below: $[amount]
  Owner-approval required below:   $[amount]

  Authorization context:
  - This SKU has [✅ flexible / ⚠️ tight / 🛑 fixed] discount authority
  - Tech's trailing-30-day discount average: [X]%  [vs. shop median: [X]%]
  - Tech's approval-rate on tight-band quotes: [X]%
───────────────────────────────────────────────
```

**Six hardening rules for the discount-authorization layer:**

- **Default authorization bands (override from config):** service techs -10% off published / drain techs -15% / lead techs -15% / dispatchers -5% only with manager rubber-stamp. Below the floor, manager approval is required; below 70% of published, owner approval is required.
- **Fixed-discount SKUs:** items where the published price is already at the membership-tier-equivalent discount (e.g., the membership-discounted line in the v2.2 member-pricing overlay) are flagged as fixed — no further discount is authorized regardless of tech.
- **Tight-band SKUs:** items where the margin is already at the floor (Healthy < 50% threshold from v2.0 internal margin block) are flagged as tight — manager approval at any discount.
- **Trailing-30-day discount average is the diagnostic, not the punitive number.** A tech 5 percentage points above the shop median for 30 days is not a violator — they're either working a tougher mix (more competitor-quoted calls) or coaching toward a less-aggressive close. The number is for the tech-perf-debrief input, not for the live-call rebuke.
- **Cross-skill consumption:** the per-tech discount data flows directly into the Technician Performance Debrief v1.1.A revenue-capture benchmark band (one of the named coaching dimensions for Service / Drain techs).
- **Never surface the guardrail block on customer-facing output.** This is an internal-only block. The AI-RX adapter strips it; the dispatcher-LIVE output strips it; only the office-async two-mode output and the tech-coaching mode include it.

### Cross-Skill Reference Pointers (v2.2)

- **Membership Plan Drafter** — source-of-truth tier-discount structure for the member-pricing overlay; check `outputs/membership-plan-*.md` for the most recent shop-specific tier structure before falling back to the default table.
- **Pre-Visit Diagnostic Intake v1.1** — `customer_language` field source for the bilingual-Spanish trigger; the AI-RX adapter typically receives this field from the platform's intake handoff JSON.
- **Review Request Drafter v2.3** — shared formal-*usted* register and don't-auto-detect-from-name rule for the Spanish price-band variant.
- **Invoice Follow-Up Sequence v2.3** — shared bilingual-Spanish discipline; the post-call invoice carries the member-pricing reflected in the call.
- **Change Order Tracker v1.3** — the per-line-item margin output of the pricebook feeds the pipeline-position math when a CO is being written; the per-tech discount-authorization data feeds the per-rep CO-velocity table.
- **Vendor Price Increase Customer Communication** — the wave-affected-SKU flag in v2.1.C still gates the member-pricing overlay (member discount on a stale SKU is suppressed until the SKU refresh).
- **Estimate Writer v2.0** — multi-line estimates that are member-eligible carry the per-line member-pricing overlay through to the estimate output rather than re-applying it at quote time.
- **Technician Performance Debrief v1.1** — consumes the per-tech discount-authorization log into the revenue-capture benchmark band; closes another measurement loop alongside the Review Request Drafter v2.3.D send-rate signal.

## v2.3 Additions (2026-06-01)

The v2.2 ship held at 9.6 across five consecutive evaluator cycles (04-28 ship through 05-25). The 05-18 Remaining Opportunities #13 named the Claude for Small Business one-click MCP connector context + AI Search Visibility cross-reference as the v2.3 vector; the 06-01 monitor cycle's Next-Run Priority #2 added the hybrid-posture calibration framing from the Blanchard / ServiceForge counter-thesis surfaced May 12, 2026 in Contractor Magazine. v2.3 ships both vectors plus a stale-pricing audit output format refinement that closes the v2.1.C carry-forward. All v2.0 / v2.1 / v2.2 content above is preserved unchanged.

### Hybrid-Posture Calibration Framing for the AI-RX Live-Call Adapter

The Contractor Magazine May 12, 2026 article by Jane Blanchard (ServiceForge) — surfaced in the 2026-06-01 landscape monitor cycle — reports two data points that re-frame how the AI-RX adapter should be deployed:

- **~1 in 3 homeowners hang up when AI answers the phone instead of a live person.**
- **78% of homeowners choose the business with human-answering when two businesses' reviews are comparable.**

The underlying data carries a vendor-bias caveat (ServiceForge sells live answering services and has commercial incentive to frame AI-RX negatively). The Bonney Plumbing 60% missed-call reduction case study, Avoca's continued adoption, Pete & Gabi's dormant-customer reactivation rates, and the seven-platform actively-marketed plumbing AI-RX landscape (AgentZap, MyAIFrontDesk, Voiceflow, Allo, RevSquared, Sameday, ServiceTitan AI Voice Agent) keep the AI-RX-positive evidence stack intact. The two data sets are not contradictory: AI-RX has measurable upside *and* AI-RX has measurable customer-side resistance. The operational implication is hybrid-posture deployment — AI-RX is the right answer for after-hours, overflow, triage, and dormant-customer reactivation; live-human is the right answer for business-hours default and for emergency-call first-touch.

v2.3.A adds a HYBRID-POSTURE-MODE field to the v2.2.A AI-RX adapter input schema and a more aggressive `escalation_to_human` posture in business-hours mode.

**Input schema addition:**

```json
{
  "hybrid_posture_mode": "AFTER_HOURS | OVERFLOW | BUSINESS_HOURS_OVERRIDE",
  "human_available": true
}
```

The three modes:

- **AFTER_HOURS** — Default mode for any call outside the shop's published business hours, or for any call that hit the AI-RX because all human dispatchers were on other calls (overflow). This is the mode the AI-RX adapter is structurally suited for; the v2.2.A escalation rules apply unchanged.
- **OVERFLOW** — Same posture as AFTER_HOURS but with a 90-second time-cap on the AI-RX exchange. After 90 seconds, if a human dispatcher has come free, the AI-RX warm-transfers to the human ("I'm going to bring our office manager in — she just came free"). If no human is free at the 90-second mark, the AI-RX completes the price-band lookup and books or schedules the callback per the v2.2.A flow.
- **BUSINESS_HOURS_OVERRIDE** — The shop has chosen to deploy AI-RX during business hours despite human availability (lowest-tier-staffing shops, owner-on-the-truck-only operations). This mode applies the more aggressive escalation rules below.

**More aggressive escalation rules under BUSINESS_HOURS_OVERRIDE:**

In addition to the v2.2.A escalation rules (emergency calls, multi-fixture scope, stale-pricing flag, member-status question, competitor-quote comparison), the BUSINESS_HOURS_OVERRIDE mode escalates on:

- **Any quote-shopping signal.** "I'm getting three estimates" / "what's your best price" / "Can you beat what I've been quoted" all escalate. Quote-shopping under business hours requires a human relationship-builder; price-band-only response cedes the close.
- **Any second-vendor mention.** "Roto-Rooter said..." / "Mr. Rooter quoted..." — the conversation is already a relationship sale; escalate.
- **Any tonal warmth-seeking signal.** "Are you guys local?" / "How long have you been in business?" / "Can I just talk to someone?" — these signals are explicit asks for human relationship; transfer within 15 seconds without restating the question.
- **Repeat-customer signal.** If the platform's CRM lookup matches an existing-customer record, the BUSINESS_HOURS_OVERRIDE mode escalates regardless of the price-question complexity. Existing customers calling during business hours expect a human voice; the AI-RX is the wrong reception.

**New escalation reason added to the v2.2.A schema enum:**

```json
"escalation_reason": "PREFERS_HUMAN"
```

`PREFERS_HUMAN` is the escalation reason whenever the customer's signal explicitly asks for a person (regardless of the hybrid-posture mode). The handoff is sub-15-second; the AI-RX does NOT restate the price question, the AI-RX does NOT confirm the call back to the customer, the AI-RX simply says "Let me bring someone on for you right now" and transfers.

**Updated worked example — Avoca platform calling under BUSINESS_HOURS_OVERRIDE on a quote-shopping signal:**

```json
{
  "skill_version": "2.3",
  "query_type": "price_lookup",
  "hybrid_posture_mode": "BUSINESS_HOURS_OVERRIDE",
  "matched_items": [],
  "escalation_to_human": true,
  "escalation_reason": "PREFERS_HUMAN",
  "escalation_phrasing": "Let me bring someone on for you right now."
}
```

**Hardening rules for the hybrid-posture calibration framing:**

- **The hybrid-posture mode is per-call, not per-shop.** The same shop runs AI-RX in AFTER_HOURS mode at 7 PM, OVERFLOW mode at 11:30 AM during a freeze surge, and might run BUSINESS_HOURS_OVERRIDE mode never. The mode is a runtime input from the platform's scheduling logic, not a shop-level configuration.
- **PREFERS_HUMAN escalation has no exceptions.** Even on the price-lookup happy-path, even when the AI-RX has a clean answer ready, when the customer asks for a person, transfer. The 1-in-3 hang-up rate from the Blanchard data is the cost of NOT transferring.
- **Document the hybrid-posture mode in the audit trail.** The platform should log which mode each AI-RX-handled call ran in, so the shop can correlate AI-RX call outcomes against mode at the weekly review. After-hours bookings, overflow-mode bookings, and business-hours-override bookings have different baseline conversion rates.
- **Hybrid posture is calibration, not abandonment.** The 06-01 monitor cycle's framing was explicit: "the hybrid posture is not a compromise — it is the operational reality." v2.3.A is a re-calibration of when the v2.2.A adapter fires, not a withdrawal of the adapter.

### Claude for Small Business / One-Click MCP Connector Context

Adds a new output mode triggered by the input including `[CSB]` at the start of the question or `[MCP:connector_id]` with an explicit connector ID. When triggered, the adapter assumes the shop is running the pricebook lookup through the Claude for Small Business one-click MCP connector pattern rather than direct platform integration. The output is structurally simpler (the MCP connector handles platform-specific formatting downstream) and includes a `connector_meta` block surfacing connector-level context.

**Trigger:** Apply when the input includes `[CSB]` or `[MCP:<connector_id>]` where `connector_id` is one of the shop's configured MCP connectors in `config.yml` → `mcp_connectors:`.

**Output addition (replaces the v2.2.A AI-RX adapter envelope when triggered):**

```json
{
  "skill_version": "2.3",
  "csb_packaging": true,
  "connector_meta": {
    "shop_id": "[shop's CSB workspace identifier]",
    "connector_id": "[the MCP connector ID that made the lookup]",
    "connector_type": "[crm | pricebook | ai_receptionist | dispatch]",
    "lookup_source": "[cached | live]",
    "lookup_latency_ms": 0,
    "downstream_consumer": "[ai_rx | csr_dashboard | tech_mobile | owner_dashboard]"
  },
  "matched_items": [
    {
      "sku": "[item code]",
      "name": "[customer-facing item name]",
      "price_band": { "low": 0, "high": 0 },
      "price_band_phrasing": "[the spoken sentence, kept consistent with v2.2.A schema]",
      "labor_minutes": 0,
      "includes": "[short prose summary]"
    }
  ]
}
```

**Hardening rules for the CSB / MCP connector context:**

- **The CSB envelope is structurally simpler than the v2.2.A AI-RX envelope.** The MCP connector handles platform-specific formatting downstream (turning `price_band` into the platform's expected `price` field, adding the platform's required `confidence` score, etc.). The skill's responsibility is the canonical answer; the connector's responsibility is the platform-specific shape.
- **`lookup_source: cached` is acceptable when the pricebook's `last_modified` is within the connector's cache TTL.** Most pricebooks update on a daily-or-slower cadence; sub-second live lookups are wasteful and add platform latency. The cache should invalidate immediately on any pricebook edit, on any vendor-price-wave bulk update, and on any membership-tier-structure change in Membership Plan Drafter.
- **`downstream_consumer` drives the verbosity.** `ai_rx` consumer gets the spoken-sentence phrasing; `csr_dashboard` gets the matched-items table plus the v2.0 internal margin block; `tech_mobile` gets the matched-items table without the margin block; `owner_dashboard` gets everything plus the v2.1.C stale-pricing flag plus the v2.2.D per-tech discount-authorization log.
- **Connector-level audit trail.** Every CSB lookup emits to the shop's CSB workspace logs with the `connector_id`, the `lookup_source`, and the `downstream_consumer` for the office's compliance and analytics review.
- **AI Search Visibility cross-reference (one paragraph).** The AI-Receptionist's spoken-answer quality is one of the four signals that feed answer-engine visibility (the other three are review-text density, schema markup, and topical-cluster authority). When the CSR or owner asks "why is my shop showing up first on Perplexity for 'tankless installer near me'?", part of the answer is "your AI-RX is giving cleaner, more specific price-band answers than the chain competitor's, and those answers are getting cited downstream in the answer engines that index call transcripts." Cross-reference: AI Search Visibility Content Pack v1.2's answer-engine framework. This is a reference, not a content expansion — the AEO skill is the source of truth.

### Stale-Pricing Audit Output Format Refinement (refines v2.1.C)

The v2.1.C stale-pricing layer produces a flat list of SKUs with no price update in 12+ months. v2.3.C reformats the output as a prioritized audit-action plan grouping stale SKUs by (a) wave-affected manufacturer-class, (b) high-volume per-shop SKU class, and (c) margin-sensitive SKU class. Each audit-action group includes a one-sentence rationale, an estimated margin-impact-per-month-of-delay calculation, and a recommended audit window.

**Output addition — replaces the v2.1.C flat list when the staleness check fires:**

```
───────────────────────────────────────────────
🔧 STALE-PRICING AUDIT — PRIORITIZED ACTION PLAN
   Run date: [date]
   Pricebook last full audit: [date]  |  Days since: [N]
───────────────────────────────────────────────

  WAVE-AFFECTED SKUs (cross-ref Vendor Price Increase Communication v1.1 May 2026 annex)
  Named-driver manufacturers in the trailing 90-day wave window:
   • Apollo Backflow (+3% May 2026 wave)
   • Westlake Pipe & Fittings (May 2026 wave)
   • SDR 35 plastic pipe (May 2026 wave)
   • OmegaFlex (May 2026 wave)
   • Little Giant pumps (May 2026 wave)

  Stale SKUs in wave-affected classes ([N] SKUs):
    Audit window: THIS WEEK
    Estimated margin-impact-per-month-of-delay: $[amount] (computed from
       trailing-90-day sell volume × wave-percentage × days-since-wave)
    Action: Update the per-SKU price by the named-driver percentage from the
       Vendor Price Increase v1.1 annex; backfill the v2.0 margin block; emit
       to the v2.2.D per-tech discount-authorization guardrails to refresh the
       tech-floor numbers.

  HIGH-VOLUME PER-SHOP SKUs (top-decile sell volume in trailing 12 months)
  Stale SKUs in high-volume class ([N] SKUs):
    Audit window: THIS MONTH
    Estimated margin-impact-per-month-of-delay: $[amount] (computed from
       trailing-12-month sell volume × estimated-cost-drift × days-since-update)
    Action: Pull current material cost from the supplier-API live feed (or call
       the supplier rep for the same line); re-compute the margin against the
       published price; recommend a price adjustment if margin has drifted
       below the v2.0 Healthy 50% threshold.

  MARGIN-SENSITIVE SKUs (currently at or below Healthy 50% margin floor)
  Stale SKUs in margin-sensitive class ([N] SKUs):
    Audit window: THIS QUARTER
    Estimated margin-impact-per-month-of-delay: $[amount] (the per-SKU margin
       is already below the floor; every month of delay compounds the
       below-floor revenue)
    Action: Refresh cost data; either lift the published price to restore
       margin or remove the SKU from the active pricebook if the market won't
       support the lift.

  REMAINING STALE SKUs (not in any of the three priority classes)
  [N] SKUs flagged for the next quarterly audit.

───────────────────────────────────────────────
```

**Hardening rules for the stale-pricing audit refinement:**

- **The grouping is additive, not exclusive.** A SKU can belong to multiple priority classes (wave-affected AND high-volume AND margin-sensitive); when it does, the audit window is the most-urgent (THIS WEEK over THIS MONTH over THIS QUARTER) and the action items are merged.
- **The margin-impact-per-month-of-delay is an estimate, not a contract.** The computation depends on assumptions (trailing-volume holding, wave-percentage applying uniformly, material-cost drift continuing). The number is a prioritization signal, not a P&L line. Surface the assumption inline.
- **Cross-skill emit:** when the audit-action plan fires, emit the wave-affected SKU update list back into the Vendor Price Increase Customer Communication v1.1 tracker so the next monthly cadence cycle has the actual implementation status against the wave-driver lift.
- **The quarterly bucket is not "later, never."** SKUs in the REMAINING bucket get audited at the next quarterly review. The bucket exists so the THIS WEEK action plan doesn't get drowned out by the long-tail; it does not exist to defer indefinitely.

### Cross-Skill Reference Pointers (v2.3)

- **Vendor Price Increase Customer Communication v1.1** — named-driver manufacturer list source for the wave-affected SKU grouping in v2.3.C; cross-skill emit destination for audit-action implementation status.
- **AI Search Visibility Content Pack v1.2** — answer-engine framework reference for the CSB / MCP connector context one-paragraph cross-reference in v2.3.B.
- **Membership Plan Drafter** — cache-invalidation trigger source for the v2.3.B `lookup_source: cached` behavior (any membership-tier-structure change invalidates the pricebook cache).
- **All nine AI-RX-consuming skills** (Pricebook Q&A v2.2.A, Estimate Writer v2.1.A, Invoice Follow-Up Sequence v2.4.B, Review Request Drafter v2.4.A, Parts & Materials List v1.2.B, After-Hours Call Summary v2.1.A, Dispatch Brief Generator v1.2.A, Product Recall Customer Outreach v1.1.C, Dormant Customer Reactivation v1.1.B) — v2.3.A hybrid-posture calibration is the per-cycle framing pass anticipated by the 06-01 monitor's "AI-RX adapter calibration framing pass" Next-Run Priority. The other eight consuming skills will receive the same framing pass on a subsequent evaluator cycle.
- **Technician Candidate Phone Screen v1.2.B** (shipped 2026-06-01) — joins the AI-RX adapter thread as the tenth schema-implementing skill, mirroring the v2.2.A canonical schema and inheriting the v2.3.A hybrid-posture calibration framing automatically.

