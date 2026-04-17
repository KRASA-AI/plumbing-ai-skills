---
name: "Water Heater Standards Briefing"
category: sales
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~30 min per customer briefing; replaces a back-and-forth comparison most shops do verbally and inconsistently"
version: 1.0
last_eval_score: null
---

# Water Heater Standards Briefing

## Purpose

Produce a customer-facing briefing that converts the two looming federal water heater efficiency deadlines — the **October 6, 2026 commercial condensing-only standard** and the **May 6, 2029 residential heat-pump standard for electric storage units over 35 gallons** — into a clear "replace now vs. wait" recommendation tailored to one customer, one piece of existing equipment, and one site condition. This is the conversation that hits a plumbing shop's phones every time a homeowner reads a news headline about "water heater rule changes" or every time a property manager has a unit that is on its last legs and is trying to decide whether to like-for-like replace before the rules change or jump ahead to the new standard.

The shop technician knows the equipment, the install constraints, and the realistic price ranges. The customer wants a one-page document that explains, in plain language, what the rules actually require, what their three or four real options are, what each option will cost over a 10-year horizon, and what the install footprint looks like in their basement / garage / mechanical closet. This skill writes that document — grounded in the actual federal rule (DOE 10 CFR 430 final rule on consumer water heaters; DOE commercial water heater rule effective October 6, 2026), the actual install implications (drain pan, condensate, breaker amperage, ambient air volume for HPWH, condensate neutralizer for condensing gas), and the actual current state of state and utility rebates after the 25C federal tax credit expired on December 31, 2025.

This is the briefing that closes the job — not because it pressures the customer, but because it gives them the structured comparison their other three quotes did not.

## When to Use

- A customer's existing water heater is 8+ years old, leaking, or making noise — and they are asking "should I just replace with what I have, or upgrade?"
- A property manager or facilities director is planning a 2026–2027 commercial water heater capital purchase and wants to know whether the October 6, 2026 commercial rule applies to their replacement
- An electrification-curious homeowner heard about heat pump water heaters and wants to know if it makes sense for their house
- A landlord is replacing a water heater in a rental and wants to understand which option lowers operating cost without raising rebuild risk
- Pre-buy season (August–October) when shops want to give existing customers a structured "do this before the new commercial rule kicks in" briefing
- After a customer requests pricing on a tankless install but the shop's recommendation is actually a HPWH or a condensing gas tank — the briefing reframes the conversation around the rules, not the customer's initial assumption

**Do not use for:**
- Pure emergency-replacement scenarios (no hot water, leak flooding the basement) — the customer needs hot water tonight, not a 10-year cost projection. Use the Estimate Writer skill with a single recommended option instead.
- Commercial gas water heaters smaller than 105,000 BTU input (the new commercial condensing rule applies to specific size classes — write to the actual rule, not to the headline)
- Locations on well water with hardness above the manufacturer spec for HPWH or condensing models — the briefing should not include options the install will not support
- Customers who have already signed and approved an estimate — do not re-open a closed job

## Required Input

1. **Customer and site context**
   - Customer name and address (city / state — used to anchor state and utility rebate language)
   - Property type (single-family / multi-family unit / small commercial / mid commercial)
   - Use case (residential domestic hot water; commercial — restaurant / laundry / office / multi-family central; etc.)
   - Occupants or simultaneous-use load (people in the home; commercial peak GPM if known)

2. **Existing equipment to be replaced**
   - Fuel type (electric resistance, natural gas atmospheric, natural gas power-vent, propane, oil, heat pump)
   - Tank size in gallons (or "tankless" if applicable) and approximate age in years
   - Approximate input rating (BTU/hr for gas, kW or amperage for electric)
   - Vent configuration (atmospheric chimney, B-vent, direct-vent through wall, power-vent, condensing PVC)
   - Location (basement, garage, attic, mechanical closet, exterior — affects HPWH viability and condensate routing)
   - Condition signals (visible corrosion, weeping at fittings, sediment-flush history, anode-rod history, prior repair history)

3. **Site constraints that gate options**
   - Available 240V capacity at the panel and approximate panel headroom (HPWH typically wants a dedicated 30A circuit; some pull less)
   - Ambient air volume around the install location (HPWH manufacturers typically want 700–1,000+ cubic feet of unconditioned space, or ducted air)
   - Floor drain or condensate pump availability (HPWH and condensing gas both produce condensate — gallons per day in cold-climate HPWH cases)
   - Gas line size and current load (for upsizing to a higher-input condensing replacement)
   - Whether the closet / mechanical room has combustion air provisions that meet the new equipment's spec

4. **Customer financial framing**
   - Approximate budget the customer has expressed (or "no number yet")
   - Customer's expected hold time in the property (5 years / 10 years / forever / "we'll be selling within 3")
   - Whether the shop is prepared to quote financing — and which financing partner / typical terms

5. **Shop facts**
   - Brands the shop installs and is certified on (Rheem, A.O. Smith, Bradford White, Navien, Rinnai, Noritz, etc. — citation discipline matters; do not name brands the shop does not actually carry)
   - Warranty terms the shop offers on parts and labor by equipment class
   - Local jurisdiction permit requirement and inspection lead time
   - Whether the shop offers HPWH-specific installs (some shops do not yet have certified HPWH installers — disclose this honestly rather than offering an option the shop cannot deliver)

## Instructions

Produce a 7-section briefing scoped to **one customer, one site, one decision**. Do not write a generic "water heater rules explainer" — the customer can find that on the DOE website. The shop's value is the translation from rule to *this customer's* options.

### Section 1 — One-paragraph customer summary (50–70 words)

Open with the customer's situation in plain language. Name the equipment to be replaced, the age, the fuel type, the location, and the immediate triggering reason (failing, end of life, planned upgrade). End with one sentence that frames the decision: "You have three real options here, and the federal rules changing in [year] affect two of them differently."

This paragraph is the only thing the customer reads in 80% of cases. Treat it like a TL;DR.

### Section 2 — What the rules actually require, in plain English (4–6 short paragraphs)

Write to the rule that affects this customer's decision — do not restate the entire DOE rulebook.

For a residential customer with an electric tank over 35 gallons, anchor on the May 6, 2029 standard requiring heat pump technology for that size class. State the exact effective date (May 6, 2029, on equipment manufactured on or after that date), what it means in practice (manufacturers stop producing standard electric resistance tanks above 35 gallons; existing inventory will likely be available for some months after; the rule does not require homeowners to replace working equipment), and what it does NOT mean (it does not require replacement of a working unit; it does not apply to under-35-gallon units, gas units, or tankless units).

For a residential customer with an electric tank under 35 gallons, note the related changes: no UEF change but maximum first-hour rating capped at 50 gallons and maximum factory temperature setting capped at 135°F.

For a residential gas customer, note that the 2029 rule is much less restrictive on gas residential units; the practical implication for a gas customer is mostly that the venting and condensing-vs-non-condensing decision is unchanged in 2026.

For a commercial customer with a gas water heater above the rule's covered input range, anchor on the **October 6, 2026 commercial water heater standard requiring condensing efficiency**. State the date, what changes (manufacturers can no longer manufacture or import non-condensing commercial gas water heaters in the covered class on or after October 6, 2026), and what it means for the customer (a like-for-like replacement of an existing non-condensing commercial unit installed in 2027 or later will be a condensing model — different vent material, different vent path, condensate management required, possibly different gas line sizing).

In every case, distinguish clearly between "manufacturers must" and "homeowners must." The rules are manufacturing standards — they change what is available to install, not what is already installed.

End the section with one sentence on the federal **25C tax credit expiration on December 31, 2025**, so the customer understands that the federal tax credit they may have heard about is no longer available for 2026 installs, and that current incentives come from state programs, utility rebates, and the HEEHRA point-of-sale rebate program (where active in their state).

### Section 3 — Options table, 3–4 rows scoped to this site (table with columns)

Build a table with these columns:

| Option | Typical install cost (this shop, this site) | 10-year operating cost estimate | Install footprint / site work | Eligibility for current incentives | Shop recommendation rank |

Rows should be the actual options viable for this site — typically:
- **Like-for-like replacement** (same fuel, same size, same configuration) — the cheapest, fastest install; honest about whether it is still available given the customer's equipment class and timeline
- **Same-fuel efficiency upgrade** (e.g., atmospheric → power-vent or condensing gas; standard electric → higher-UEF resistance) — middle cost, modest operating cost improvement
- **Heat pump water heater (electric)** — higher equipment cost, lower operating cost, real install footprint requirements (ambient air volume, condensate, dedicated circuit) — only include if the site supports it; if not, say so explicitly in the row and explain why
- **Tankless (gas or electric)** — only if the customer's hot-water profile and gas line / electrical capacity support it

For the operating cost estimate, use the customer's local utility rate per kWh and per therm if known; if not, use a clearly labeled regional average and note the assumption. Show the math in one line: "$X/yr × 10 years = $Y" so the number is not a black box.

For incentive eligibility, name the program (state name, utility name, HEEHRA), the typical rebate amount range, and a note that final eligibility requires verification at install — do not promise a specific dollar amount the customer will receive.

The recommendation rank column should be 1 / 2 / 3 / 4 with one short reason. The shop's preferred option should rank 1 with the reason grounded in this customer's situation, not in generic marketing.

### Section 4 — Why we recommend [option X] for this customer (2–3 paragraphs)

This is the conversational core of the briefing. State the recommendation, then ground it in three things specific to this customer: (a) what is actually wrong with the existing unit and why deferring is risky or fine, (b) the site condition that makes the recommended option fit (or rules out an alternative), (c) the cost and operating profile against the customer's stated hold time and budget.

Be honest about tradeoffs. If the recommendation is HPWH, say what the customer will notice — quieter than they might expect, runs longer cycles, modestly cools the surrounding space, longer recovery on heavy-demand days unless sized correctly. If the recommendation is condensing gas, say that the install requires PVC venting, a condensate drain or pump, and a condensate neutralizer if running into copper or cast iron drains. If the recommendation is like-for-like replacement, say plainly: "the rules don't force you off this technology yet, and given your hold time of 3 years, the math doesn't favor switching."

Avoid manipulative urgency. The October 2026 and May 2029 dates are real and worth knowing, but most homeowners who replace a working water heater because of a rule date end up paying for a new water heater 5 years earlier than they had to.

### Section 5 — What the install actually involves at this site (1–2 paragraphs + a short bulleted "site work needed" list)

Translate the recommended option into the specific site work that has to happen at this customer's address. Examples:

- For a HPWH in a basement install: condensate routing to the floor drain, dedicated 30A 240V circuit (if not already present), permit pull, electrical inspection if a new circuit is run, anchoring per local seismic / California requirements where applicable, and one note on ambient temperature in the install location during winter.
- For a condensing gas commercial replacement: PVC vent run from the unit through the wall or roof, gas line verification (the new condensing unit may have a different input rating), condensate trap and neutralizer, possible combustion-air provision update, and a note on the local mechanical inspector's lead time.
- For a like-for-like atmospheric gas install: pan, pan drain, T&P discharge to a code-compliant termination, sediment trap on the gas line, expansion tank if the system has a check valve or PRV.

End the section with the permit fee range, the inspection lead time, and the realistic on-site time for the install (in hours or days).

### Section 6 — What this looks like in your home in 5 years (1 short paragraph)

Honest forward look. If the customer chooses like-for-like and the equipment lasts its expected service life, what does the next replacement decision look like? (For a 12-year service life on a gas tank installed in 2026, the next decision is in 2038 — well after both rule deadlines, and the customer will be replacing into a different equipment landscape.) If the customer chooses HPWH now, what does maintenance look like (filter cleaning, anode rod, refrigerant — none of which a homeowner is used to). If the customer chooses commercial condensing now, what is the condensate maintenance cadence and the typical heat exchanger service interval.

This section makes the briefing useful as a long-term reference document, not just a sales tool.

### Section 7 — Pricing summary and signature block

Restate the recommended option's total install price (parts, labor, permit, haul-away). Show financing options if the shop offers them. Show warranty terms (parts years, labor years, what voids it). Include a "questions before you decide" line with the technician's direct phone number. Include the customer signature line with date for the recommended option, and a "I prefer Option [_]" alternate line in case the customer goes with a different option from the table.

Do not include a signature line that approves an option not listed in the table. The customer's choice has to be a documented option for the shop's records.

## Output Discipline

- Use the customer's first name in the recommendation paragraph at least once. Use it sparingly — twice in the whole briefing is the right amount.
- Currency formatting: $X,XXX with a thousands separator. Operating cost estimates always include the assumed utility rate.
- Dates: write the federal effective dates in full ("October 6, 2026" / "May 6, 2029") at first mention, then short-form thereafter.
- If a piece of information is unknown or estimated, mark it explicitly: "Estimated — confirm at install" or "Verify utility rate at billing."
- Do not produce a briefing longer than two printed pages. If sections run long, tighten Sections 2 and 6 first.
- If the shop is not certified on HPWH and the site favors HPWH, name the limitation in Section 4 and recommend the next-best option the shop can deliver — do not steer the customer into an inferior option without disclosing why.

## Example Output (abridged)

**Customer:** Ramirez, 2218 Hawthorne Ln, Sacramento CA 95820
**Equipment to replace:** A.O. Smith 50-gallon natural gas atmospheric, 13 years old, basement install, weeping at the cold inlet, atmospheric B-vent into shared chimney with the furnace
**Hold time:** "Forever" (owners since 2009, no plans to move)

---

**Section 1 — Summary**

Mariana, your 13-year-old 50-gallon gas water heater is at the end of its expected service life and is showing signs of failure at the inlet. Like-for-like replacement is still available and is the cheapest path. The May 2029 federal rule does not affect gas tanks like yours, but two real upgrade options — a power-vent gas tank or a heat pump water heater — are worth comparing for a household planning to stay long-term.

**Section 2 — What the rules require**

The federal rule that changes water heater manufacturing kicks in on **May 6, 2029** for residential electric storage tanks larger than 35 gallons — those will need to be heat pump units after that date. Your unit is gas, so this rule does not directly require any change to your equipment.

The federal **25C tax credit expired on December 31, 2025**, so the federal tax credit some homeowners used in 2024–2025 is no longer available for 2026 installs. Current incentives in California for heat pump water heaters come from the **TECH Clean California** program and from your utility (SMUD in your area), and from the federal HEEHRA program where active. Ranges below are typical at this writing — final eligibility is verified at install.

**Section 3 — Options table (excerpt)**

| Option | Install cost | 10-yr operating cost | Footprint | Incentives | Rank |
|---|---|---|---|---|---|
| Like-for-like 50gal atmospheric gas | $2,400–$2,900 | ~$2,200 ($220/yr at $1.45/therm, 0.62 UEF) | Same as today | None | 3 |
| Power-vent 50gal gas | $3,400–$3,900 | ~$1,900 | Same plus power outlet within 6 ft, side-wall vent | None | 2 |
| 50-gal heat pump water heater (Rheem ProTerra) | $4,800–$5,600 | ~$650 ($65/yr at $0.28/kWh, 3.75 UEF) | Dedicated 30A 240V circuit, condensate to floor drain, basement install qualifies for ambient air | SMUD HPWH rebate $2,000–$3,000 typical; TECH CA varies; verify at install | 1 |

**Section 4 — Why we recommend the heat pump water heater for your home**

Mariana, given that you and Carlos plan to stay long-term, the operating cost difference compounds in your favor. At our local utility rates, the HPWH runs about $1,550 less in operating cost over 10 years than like-for-like, which roughly offsets the install premium even before incentives. Your basement install location has the air volume HPWHs need (we measured 1,200+ cubic feet during the visit), the floor drain is in the same room, and the panel has room for the dedicated circuit without an upgrade. The honest tradeoffs are: it runs longer cycles than a gas tank, it modestly cools the basement (a feature in summer, neutral in winter for an unconditioned space like yours), and it has a filter that needs cleaning every 6 months. None of those are dealbreakers; they are differences from what you have now.

If the SMUD rebate were not available we would still rank this option first, but the rebate makes it the clear choice.

**Section 5 — What the install involves**

One-day install. We pull the existing tank, run a new dedicated 30A 240V circuit from the panel (12 ft of conduit, one breaker), set the new HPWH on a code-compliant pan with drain to the existing floor drain, run condensate from the unit to the same drain, set the T&P discharge to code, and pull the City of Sacramento permit (typical fee $75–$120; inspection within 5 business days).

Site work needed: dedicated circuit (included), condensate routing (included), pan and pan drain (included), permit (included), haul-away of existing tank (included).

**Section 6 — In 5 years**

You will be 5 years into a 10–13 year expected service life on the HPWH. Maintenance: filter clean every 6 months (we leave you a written reminder), anode rod check at year 5 and replace at year 7–8, no refrigerant work expected in normal operation. By the next replacement decision (roughly 2036–2038), the residential heat pump rule will have been in effect for several years and HPWHs will likely be the default option at most price points.

**Section 7 — Pricing and approval**

Recommended option: **Rheem ProTerra 50-gal heat pump water heater, installed** — $5,250 plus permit. SMUD rebate (estimated $2,500) processed by us at install; net to you ~$2,750. Financing available: 12 mo same-as-cash via Service Finance, or 60 mo at 9.99% APR (~$112/mo).

Warranty: 10 years parts (manufacturer), 2 years labor (our shop). Tank leaks during the warranty period are full replacement; refrigerant work is covered by manufacturer.

Questions: call Tom direct at (916) 555-0142.

I approve **Option 1 — Heat Pump Water Heater** as quoted above:

Signature: ______________________ Date: __________

I prefer **Option [_]** instead — please re-quote.

---

## Notes for the Operator

- The two new federal rule dates (October 6, 2026 commercial; May 6, 2029 residential) are foundational facts. Do not soften or hedge them — they are written into the final DOE rules. Do soften any specific incentive dollar amount, because state and utility programs change quarterly.
- The 25C tax credit is genuinely expired for 2026 installs. Do not include it as available.
- HEEHRA rollout varies by state. Where a state has not yet activated HEEHRA, do not promise it as available — name the state-administered program by name (TECH Clean California, Mass Save, NYSERDA, Energize CT, etc.) or note that no current program applies.
- The briefing is designed to be screen-readable and printable in two pages. If the shop wants a one-pager version, drop Sections 5 and 6 first; never drop Section 3 (the table is the part the customer remembers).
- This skill pairs with the Estimate Writer skill: the Estimate Writer produces the final signed estimate document; this skill produces the comparison briefing the customer signs against.
