---
name: "Plumbing Permit Application Drafter"
category: admin
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~45–75 min per permitted job — produces the permit-required decision, the scope-of-work narrative, the customer permit briefing, the day-before-inspection walkthrough checklist, and the multi-job permit tracker; avoids the inspection-day re-work loop and the customer-surprise call when the inspector flags something the shop didn't pre-flag"
version: 1.0
last_eval_score: 9.6
---

# Plumbing Permit Application Drafter

## Purpose

Produce the complete pre-submission package a plumbing shop needs to pull a residential or light-commercial permit cleanly: the permit-required decision (which jobs need one and which type — water heater swap-out, repipe, drain, gas line, sewer lateral, addition rough-in, fixture replacement, water service), the scope-of-work narrative the shop pastes into the city portal or hands to its permitting platform (PermitFlow, Zermit AI, ePermitHub), the customer briefing the shop sends before the work starts, the day-before-inspection walkthrough checklist the foreman uses to avoid the re-trip, and the multi-job permit tracker the office runs to keep every active permit from sliding past its expiration or scheduling its inspection too late.

The skill is built around the gap that the AI permitting platforms do not close. Zermit AI (launched March 2026) and PermitFlow (1,500+ municipalities and growing) have made the submission step itself substantially easier — the shop fills out a guided chat or upload form and the platform routes it to the jurisdiction. CivCheck (Denver deal announced April 21, 2026; Honolulu, Charleston, and others on the roster) is doing the same on the reviewer side, pre-checking applications against zoning, code, and fire requirements. Plan-review wait times in modernized jurisdictions have dropped from weeks to days. What none of those tools produce is the **shop's own decision and narrative inputs** — whether the job actually needs a permit at all, what to write in the scope-of-work field, what to tell the homeowner about cost and timeline, how to walk the job before the inspector arrives, and how to keep track of every active permit across the shop's job book. That is still the shop's work to do, and ad-hoc each time is where the re-work happens.

The real failure mode is not the application itself — most shops can fill in a form. The failure mode is the second visit: the inspector flags an unsleeved penetration through fire-rated assembly, an undersized TPR discharge pipe, a missing thermal expansion tank where the system has a backflow preventer, a hard-piped water heater connection where flex was needed, a drainage configuration that violates the local interpretation of UPC vs. IPC. The shop comes back, fixes it, schedules a re-inspection, and pays the re-inspection fee. The customer hears "we need a re-inspection" and the trust drops a notch even though the underlying work is correct. This skill's job is to compress as much of that risk as possible into the pre-submission and pre-inspection stages.

The discipline across every artifact is matching the depth of the work to the risk class of the permit. A water heater swap is a 5-minute permit decision and a one-paragraph scope. A whole-house repipe with a service upgrade is a 30-minute permit decision and a multi-page scope. The skill scales accordingly and refuses to produce a 200-word narrative for a job that fits in 30 words, or a 30-word narrative for a job that needs careful staging and inspection sequencing.

## When to Use

- The shop is taking a job that may or may not require a permit and needs the decision documented so the office and the tech are on the same page
- A permit is required and the shop is about to submit through its city portal, PermitFlow, Zermit AI, or directly via the AHJ counter — and needs a clean scope-of-work narrative
- The shop wants to brief the customer ahead of work starting on what the permit means, what it costs, who pays, how it affects timeline, and what inspection will look like
- A permitted job is approaching its inspection window and the foreman needs the day-before walkthrough checklist
- The office wants a single tracking artifact for every active permit (status, expiration, inspection booked, fees paid) because the count has grown past what a single spreadsheet tab can hold cleanly
- A specific high-risk permit class is in play (gas line, sewer lateral, water service, large repipe) and the shop wants the documentation tighter than usual
- A new technician or new field-supervisor needs the shop's standard permit-handling pattern in writing

**Do not use this skill for:**

- Commercial new-construction permitting where the GC, MEP engineer, and architect are running the permit themselves and the plumbing shop is a sub — that's a coordination conversation, not a permit-pull
- Pure service work that does not require a permit anywhere (snake a drain, replace a faucet trim, clear a clog, residential disposal swap) — the decision is "no permit," not a full skill output
- Variance / appeal / hardship applications where the shop is asking for something non-standard — those need a code consultant or the engineer of record, not a prompt skill
- Jobs in jurisdictions where the shop has never worked and has no contact with the AHJ — first job in a new jurisdiction warrants a phone call to the building department before any permit drafting
- Work the shop is intentionally doing without a permit (which it should not be) — the skill will not produce cover for that

## Required Input

1. **The job itself**
   - Service address (city, county, state) — jurisdictional posture matters
   - Brief description of work in plain language: what's being installed, removed, modified
   - Property type (single-family detached, townhome, condo, light-commercial, multifamily 2–4 unit)
   - Year of construction if known (governs which code cycle applies under grandfather provisions)
   - Whether there is an HOA architectural-review requirement layered on top of the AHJ permit
   - Whether the work is part of a larger remodel under a separate building permit (in which case the plumbing scope rolls up under that)

2. **The shop's jurisdiction-specific knowledge**
   - Code basis the AHJ enforces (UPC, IPC, state-amended IPC, NSPC, local-amended UPC) — and the cycle (2018, 2021, 2024)
   - Whether the AHJ uses an online portal, a third-party platform (PermitFlow / Zermit AI / ePermitHub), or a counter intake
   - Typical plan-review turnaround in this jurisdiction (1 day, 5 days, 2 weeks, 4+ weeks)
   - The AHJ's specific quirks the shop has learned: required handouts, photo documentation, expansion-tank rule, sleeving rule, dielectric-union interpretation, panel-grounding-bond verification, soil-pipe joint method, water-service trenching depth, gas-pipe depth, sewer cleanout location requirement
   - The local re-inspection fee and the local pattern for what triggers it most commonly

3. **The shop's own posture decisions**
   - Permit fee: pass through to customer, embed in the proposal, or absorb on small jobs (typical shops pass through anything over $200 and embed anything under)
   - Whether the shop pulls the permit or asks the homeowner to pull it (shop-pulled is the right answer 95%+ of the time; homeowner-pulled is a yellow flag that the shop is hedging liability and the customer should be informed why)
   - Whether the customer will be home for the inspection, or the shop's foreman will meet the inspector
   - Inspection-scheduling preference (first-available, batch-with-other-job-in-the-area, customer-driven)

## Instructions

You are producing the **Permit Application Drafter Package** for a plumbing shop. It contains five artifacts. Match the depth of each artifact to the risk class of the job. A water-heater swap gets the short version of every artifact; a repipe-plus-service-upgrade gets the long version.

### Risk classification (do this first, internally, before writing anything)

Classify the job into one of three risk tiers. State the tier explicitly at the top of Artifact 1.

- **Tier 1 (low):** Like-for-like fixture replacement, water heater swap-out (same fuel, same location, same capacity ±20%), single-fixture rough-in within an existing wet wall, sub-meter installation. Plan review is typically over-the-counter or auto-approved. Inspection is a single visit.
- **Tier 2 (medium):** Repipe sections (kitchen, bath, partial), fuel-change water heater swap, water service replacement (1″ or under, no easement), drain re-routing within the building, addition rough-in for one bathroom, gas line for a single appliance. Plan review is days, not minutes. Inspection has a rough-in and a final.
- **Tier 3 (high):** Whole-house repipe, sewer lateral replacement (especially with traffic-control or right-of-way work), main water service upgrade (1.5″+ or with meter upgrade), commercial backflow assembly install, multiple-appliance gas line system, addition with multiple bathrooms, anything across a fire-rated assembly, anything in a historic district. Plan review is weeks. Inspection has rough-in, top-out, and final at minimum, plus possible engineering letter and pressure tests.

### Artifact 1 — Permit-Required Decision and Submission Routing

A short structured block, 15–40 lines depending on tier. Include:

- **Tier (1/2/3) and rationale** — one line.
- **Permit required:** yes / no / probably / call AHJ. If no, stop the skill here and note why no permit is required (pure repair, falls under building-permit "minor work" exemption, etc.). If "call AHJ," produce the question to ask and the contact path; do not draft the rest of the package until the answer is back.
- **Permit type** — the specific permit category in this AHJ's vocabulary (e.g., "Residential Plumbing Permit – Water Heater Replacement," "Plumbing Permit – Service Upgrade," "Combination Permit – Plumbing+Mechanical+Electrical for water heater fuel change"). If two are needed, list both.
- **Code basis** — UPC 2024, IPC 2021, etc., and any local amendments that bear on this scope.
- **Submission route** — direct portal, PermitFlow, Zermit AI, ePermitHub, in-person counter, fax (some rural AHJs are still fax). Include the URL or phone number and the expected turnaround.
- **Estimated permit fee** — best estimate from the AHJ's fee schedule; flag if the shop should call to confirm.
- **Plan-review turnaround estimate** — days/weeks, with the historical median for this AHJ if known.
- **Inspections required** — list each (rough-in, top-out, final, gas pressure test, backflow test, etc.) and the typical sequencing.
- **Posture decisions:**
  - Who pulls the permit (shop or homeowner, with rationale)
  - How the fee is handled in the proposal (pass-through line item, embedded, absorbed)
  - Whether the customer will be on-site for inspection or the foreman will meet the inspector
- **Any flags from the AHJ's local quirks that affect this scope** — short bullets, no more than 5

### Artifact 2 — Scope-of-Work Narrative for the Application

The text the shop pastes into the permit portal's scope-of-work field, hands to PermitFlow / Zermit AI's intake chat, or attaches to the application packet. Match length to tier:

- **Tier 1:** 30–80 words. One paragraph. State exactly what is being removed and what is being installed (manufacturer + model + capacity), the connection method, the venting where applicable, the location, and the code basis.
- **Tier 2:** 100–250 words. Two to four paragraphs. Add: existing condition being addressed, proposed new layout in plain language, materials list summary (pipe type and size, fitting class, fixture supply lines), pressure-test plan, scheduled inspection sequence.
- **Tier 3:** 300–600 words. Five+ paragraphs. Add: existing-conditions assessment, proposed system design with sizing rationale where it differs from minimum code, demolition and protection plan, sequencing of work relative to other trades, pressure-test methodology and witness plan, special conditions (fire-rated assembly penetrations, sleeve and firestop method, expansion-tank sizing), and the engineer-of-record reference if one is involved.

The narrative is **factual and specific**. No marketing language. No "high-quality" or "professional craftsmanship." Inspectors read this looking for what the shop is doing and how. Adjectives make them suspicious; specifics make them comfortable.

Always include:
- Material specifications by name and class (e.g., "Type L copper for hot/cold distribution; PEX-A oxygen-barrier for radiant; cast iron no-hub for DWV horizontals; Schedule 40 PVC for DWV verticals where allowed")
- Pipe sizing where it deviates from minimum code or where the calculation matters
- Fixture-unit and DFU totals on anything Tier 2 or above
- Pressure-test plan: medium (water or air), pressure (psi), duration (minutes/hours)
- Code citations only where the inspector is likely to want to see them — for unusual conditions, for variances from the default, for items the shop has worked with this AHJ on before

### Artifact 3 — Customer Permit Briefing (text or short email)

What the shop sends the homeowner before work starts so they know what the permit means. 6–10 short sentences for Tier 1, 10–20 for Tier 2 and 3.

The briefing answers, in this order, the questions the customer is going to ask:

1. **Why this job needs a permit** — one sentence, factual, not defensive.
2. **What the permit costs and how it shows up on the proposal** — one sentence. State the dollar amount or range, and where it appears on the proposal.
3. **What the inspector is looking for** — one or two sentences in plain language. Not a code lecture. Something like "the inspector will verify the gas connection is leak-free and the water-heater discharge pipe is the right size and routed correctly."
4. **When the inspection will happen** — one sentence. State the typical window (e.g., "the day after we finish, between 9 AM and 1 PM, the inspector will call ahead").
5. **Whether the customer needs to be home** — one sentence, clear yes/no. If yes, explain why; if no, explain who from the shop will be there.
6. **What happens if the inspector flags something** — one or two sentences. State that the shop covers the cost of any re-inspection that comes from a shop-side issue. Do not pretend re-inspections never happen.
7. **What the customer gets at the end** — one sentence. The signed-off permit card, copies for the file, anything that goes into the closing packet for a future buyer's home inspection.

Do **not** include: code citations, jurisdiction-specific jargon, defensive language about why the shop did or didn't recommend additional work. The briefing is service-oriented, not legal.

### Artifact 4 — Day-Before-Inspection Walkthrough Checklist

The foreman's pre-inspection checklist, scaled to the tier and the job specifics. Format as a checklist the foreman can actually carry.

The checklist is divided into three sections:

**Section A — General (every job, every tier):**
- Permit card posted at the job site, visible from the street side
- Approved plans (if applicable) at the job site
- Work area accessible to the inspector (no locked doors, dogs secured, clear walkway)
- All test gauges installed and pressurized where applicable
- Job-photo set captured of any work that will be covered before the inspection happens
- Shop's contact phone for the inspector visible on the permit card

**Section B — Scope-specific (generated from the job):**
- A 5–25 item list specific to the work being inspected
- For water heater: TPR discharge size and routing, expansion tank presence and pressurization, dielectric unions if metallic-to-CPVC transition, vent slope and termination, gas-line pressure test pass, drain-pan presence on second-floor installs, seismic strapping per local requirement
- For repipe: pressure test current, all fittings of approved class visible, all penetrations sleeved through fire-rated assemblies, manifold accessible, fixture supply stops accessible, PEX support per manufacturer spec
- For gas: leak test current, sediment trap on each appliance branch, shutoff within 6 feet of appliance, line-size verification at largest demand
- For drain/DWV: cleanout locations and accessibility, vent terminations, slope verification, joint method per code, no flat vents
- For sewer lateral: cleanout location, slope, bedding, backfill compaction documentation if required, traffic-control plan if in right-of-way
- For backflow: device type matches application, test cocks accessible, witness-test scheduled with the inspector or with a certified tester per AHJ rule

**Section C — Local AHJ quirks (every job in a known jurisdiction):**
- The 2–5 specific things this AHJ has flagged on this shop's prior work or on shops generally
- Examples (jurisdiction-specific): "X County requires the expansion tank on the cold side, not the hot," "Phoenix AHJ wants the TPR discharged to within 6″ of slab and turned 90° toward floor drain," "Loudoun County requires copper soil pipe for the first 5′ inside the foundation," "Boston PHCC interpretation requires dielectric union on every metallic-to-metallic dissimilar transition not just at the heater"

### Artifact 5 — Permit Tracker

A multi-job tracking block the office runs continuously. The format is a structured table the shop can paste into a spreadsheet, a Google Sheet tab, or its job-management software.

Columns:
1. **Job name / customer last name** (short)
2. **Address** (street + city)
3. **Permit number** (once issued)
4. **Permit type and tier** (1/2/3)
5. **Submission date**
6. **Approval date**
7. **Permit expiration date** (most AHJs: 6 months from issuance, void if no inspection within 180 days; some are 12 months)
8. **Inspections required** (rough-in / top-out / final / gas test / etc.)
9. **Inspection booked / completed** (per inspection in the sequence)
10. **Permit fee paid** (date, amount, receipt #)
11. **Status** (submitted / under review / approved / inspection scheduled / passed / closed / expired-warning)
12. **Owner / foreman responsible** (name, so escalation is unambiguous)
13. **Notes** (any AHJ correspondence, plan-review comments, re-inspection items)

The skill should produce the tracker pre-populated with the current job's row plus a **status-of-the-shop summary** at the bottom: total open permits, count expiring in 30/60/90 days, count awaiting inspection scheduling, count with re-inspection pending. This is the artifact the office runs as a standing weekly review.

## Output Format

Produce all five artifacts in order. Use the headers exactly as listed (Artifact 1 / 2 / 3 / 4 / 5 with descriptive subheaders). Keep formatting clean — use short headers, bullet lists where the structure helps, and prose where the structure doesn't help.

For the customer briefing (Artifact 3), include a labeled "TEXT version" (under 800 characters for SMS) and an "EMAIL version" (the full briefing) only if the shop's input includes a phone number or email preference; otherwise default to email.

For the tracker (Artifact 5), produce a markdown table for the columns and a short prose paragraph for the status-of-the-shop summary.

## Example Output

**Input:** Cardinal Plumbing Co., Richmond VA. Job: 50-gallon natural-gas water heater swap-out at 4218 Forest Hill Ave., Richmond. Existing unit is a 12-year-old 50-gal Bradford White, leaking from the bottom. Replacing with a Rheem Performance Plus 50-gal NG (XG50T12HE40U0). Same location (basement utility room), same fuel, same capacity. Existing TPR discharge runs to floor drain 8 feet away in 3/4″ copper. Existing expansion tank present. Customer: Janet Tomlinson, occupied homeowner, will be home for inspection.

---

### Artifact 1 — Permit-Required Decision and Submission Routing

**Tier:** 1 (low). Like-for-like water heater replacement, same fuel, same location, same capacity.

**Permit required:** Yes. City of Richmond requires a residential plumbing permit for any water heater installation, replacement, or relocation per City Code Chapter 8, Article II, in conjunction with Virginia Uniform Statewide Building Code (USBC, 2021 edition referencing IPC 2021).

**Permit type:** Residential Plumbing Permit – Water Heater Replacement (single appliance).

**Code basis:** Virginia USBC 2021 → IPC 2021 + IRC 2021, Chapter 28 (Water Heaters). No Richmond-specific amendments bear on this scope.

**Submission route:** Richmond ePortal (citizenserve.com/Portal/portal.aspx?portal=Richmond). Online submittal, typical same-day or next-business-day turnaround for residential plumbing of this scope. Permit fee approximately $80 (verify on submittal — fee schedule was last updated October 2025).

**Inspections required:** Single final inspection. No rough-in (existing connections being reused). Combo gas-pressure test verified at the final inspection.

**Posture decisions:**
- Cardinal pulls the permit (default for any permitted work).
- Permit fee passed through as a separate line on the proposal — Cardinal's threshold for embed-vs-pass-through is $100; this is below, but standard practice on permits is to surface them on the proposal so the customer sees the AHJ involvement explicitly. Embed.
- Janet will be home for the inspection. Cardinal foreman will be on-site to meet the inspector.

**Local AHJ flags for Richmond on water heater jobs:**
- Richmond inspectors verify the TPR discharge is full-port, terminated 6″ above the receptor (floor drain in this case), with no traps or threading on the discharge end.
- Expansion tank presence is verified (already present in this scope; Cardinal will pressurize to the incoming static pressure measured at the start of the job).
- Sediment trap on the gas line at the appliance is verified — Cardinal will install one even if the existing line has one, as part of the new connection.
- Combustion-air verification — basement utility room volume and the existing high/low louver venting in the door must be re-confirmed.
- Earthquake / seismic strapping — not required in Richmond (not in seismic design category D).

### Artifact 2 — Scope-of-Work Narrative for the Application

> Replace existing 50-gallon natural-gas atmospheric-vent water heater (Bradford White, 12 years in service, leaking from tank) with new 50-gallon natural-gas atmospheric-vent water heater (Rheem Performance Plus XG50T12HE40U0, 40,000 BTU/hr input, 0.62 UEF) in same basement utility room location. Reuse existing 3/4″ copper hot/cold distribution connections with new dielectric unions. Reuse existing 3/4″ TPR discharge to floor drain (verified full-port, 8 ft run, terminated 6″ above floor drain). Reuse existing thermal expansion tank, repressurized to 60 psi to match incoming static. Reuse existing 1/2″ black-iron gas supply with new flexible gas connector and new sediment trap at appliance. Reuse existing single-wall galvanized vent (Type B not required for atmospheric appliance per IPC 2021 Chapter 5). Combustion air confirmed adequate per existing high/low louver intake in utility-room door. Pressure-test plan: hot/cold distribution to 80 psi with water, 15 minutes; gas-line drop pressurized at full system pressure with soap-bubble leak test at every joint. Final inspection only.

(189 words — Tier 1 upper end, justified by the gas + venting + TPR detail the inspector will look for.)

### Artifact 3 — Customer Permit Briefing

**EMAIL version (default):**

> Hi Janet,
>
> Quick note on the permit for your water heater replacement on Wednesday.
>
> The City of Richmond requires a residential plumbing permit for any water-heater install or replacement — it's a standard step, not a flag of anything unusual. Cardinal pulls the permit on your behalf; you'll see the permit fee ($80) on your proposal as a separate line.
>
> The day after the install, a Richmond city inspector will come out to verify the gas connection, the temperature-pressure relief discharge, and the venting are all done correctly. He'll typically call between 9 AM and 1 PM to give you a 30-minute heads-up. You'll need to be home (or have someone home) to let him in. Our foreman will also be there to meet him.
>
> If the inspector flags anything that's on us, Cardinal covers the re-inspection fee and the fix — no charge to you. We've never had a re-inspection on a like-for-like water heater swap in Richmond, but I'd rather you know the policy in advance than be surprised.
>
> When the inspection passes, we'll mail you the signed permit card to keep with your home-improvement records. It'll matter to a future buyer's home inspector, so it's worth filing.
>
> Any questions before Wednesday — text or call.
>
> — Marcus, Cardinal Plumbing

(228 words — Tier 1 upper end, includes the gas-and-vent detail because Janet is technically minded based on the intake call notes.)

**TEXT version** (sent the morning of the install):

> Hi Janet — Marcus from Cardinal. Heads-up: Richmond inspector will come Thursday between 9 and 1 to check the new water heater. He'll call ahead. Need someone home to let him in; I'll be there too. Permit's pulled and on the proposal. We mail you the signed card after. Any questions, text me.

(304 characters.)

### Artifact 4 — Day-Before-Inspection Walkthrough Checklist

**Section A — General**
- [ ] Richmond permit card posted on the utility-room door, visible
- [ ] Job-photo set captured: connections, sediment trap, TPR discharge, expansion tank gauge reading, vent
- [ ] Janet confirmed home Thursday 9 AM – 1 PM
- [ ] Marcus on-site by 8:45 AM
- [ ] Cardinal contact number on the permit card

**Section B — Scope-specific (water heater swap)**
- [ ] TPR valve installed, full-port, threading on inlet end only
- [ ] TPR discharge: 3/4″ copper, full-port, terminated 6″ above floor-drain receptor, no traps, no threading on the discharge end
- [ ] Expansion tank pressurized to 60 psi (incoming static); gauge reading photographed
- [ ] Gas sediment trap installed at appliance (3″ minimum drip leg)
- [ ] Flex gas connector listed for natural gas, length within manufacturer spec, no kinks
- [ ] Dielectric unions installed on hot and cold connections
- [ ] Atmospheric vent slope ≥ 1/4″ per foot rise to chimney
- [ ] Combustion-air louvers in utility-room door unobstructed; high louver clear, low louver clear
- [ ] Drain pan present (basement install, but Richmond does not require pan in below-grade utility room with floor drain — confirmed not flagged)
- [ ] Thermostat set to 120°F (anti-scald, IPC 2021 default)
- [ ] All shutoffs labeled (cold inlet, gas)

**Section C — Richmond AHJ quirks**
- [ ] TPR termination height re-verified (6″ above receptor — Richmond inspectors measure)
- [ ] Sediment trap presence is the most-cited Richmond water-heater finding; verified
- [ ] Combustion-air calculation noted on the permit card (utility room volume × 50 cu ft per 1,000 BTU/hr; 40,000 BTU/hr requires 2,000 cu ft equivalent through louvers — confirmed via existing louver area)

### Artifact 5 — Permit Tracker (current job + status-of-the-shop summary)

| Job | Address | Permit # | Type / Tier | Submitted | Approved | Expires | Inspections | Status | Foreman | Fee | Notes |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Tomlinson | 4218 Forest Hill Ave, Richmond | (pending) | WH Replace / T1 | 2026-04-25 | — | — | Final only | Submitted | Marcus | $80 (pending) | Like-for-like NG WH; final-only inspection scheduled for 2026-05-01 AM window |

**Status-of-the-shop summary (as of 2026-04-25):**

Cardinal currently has 9 active residential permits open across Richmond, Henrico, Chesterfield, and Hanover. Two are expiring within 30 days (both kitchen-renovation rough-in permits awaiting customer scheduling) — Marcus to call both customers this week to book the rough-in inspection. Three are awaiting initial inspection scheduling (one whole-house repipe in Henrico, two water heater swaps in Chesterfield). One has a pending re-inspection from a flagged TPR discharge routing on a Henrico job from April 18 — Marcus rescheduled the re-inspection for April 29; no fee per Cardinal's standard policy on shop-caused re-inspections. Three are clean and awaiting final closeout. Tomlinson is the 10th, just added.

---

## Pairs With

- **Estimate Writer** — the proposal Tomlinson signed already has the permit-fee line item Cardinal embedded; the permit-required decision in Artifact 1 confirms the line item is correctly placed.
- **Change Order Tracker** — if the inspector flags something that turns into added scope (rare on Tier 1, common on Tier 3), the change order is documented through that skill, not by re-running this one.
- **Job Status Update Drafter** — Artifact 3's email is the inspection-window heads-up; the post-inspection "passed, signed permit card mailed Tuesday" update is the Job Status Update skill's territory.
- **Safety & Compliance Tracker** — Artifact 5 (the permit tracker) lives alongside the certification / license / training tracker; both are weekly office reviews.
- **Pre-Visit Diagnostic Intake** — the intake artifact for the original water-heater-leaking call is what produced the inputs (capacity, fuel, location, age) this skill consumed.

## Notes

- **The AI permitting platforms (PermitFlow, Zermit AI, ePermitHub, CivCheck on the reviewer side) handle submission and routing — they do not produce the decision, the narrative, the customer briefing, or the inspection prep.** This skill complements those platforms; it does not replace them. A shop using PermitFlow should hand PermitFlow the Artifact 2 narrative as the scope-of-work input.
- **The permit-fee passthrough decision is intentionally surfaced.** Customers who see the permit fee on the proposal as a separate line trust the shop more than customers who get a bundled number; the increase in trust is worth more than the marginal customer who would have balked at seeing the fee. Cardinal's $100 threshold is on the conservative side — many shops surface every permit fee regardless of size.
- **Re-inspection responsibility is stated explicitly in the customer briefing.** The shop covers re-inspections caused by shop-side issues. If the AHJ changes its mind mid-project (rare, but happens), the shop covers it and quietly absorbs the cost — that is part of running a permitted job. Re-inspections caused by a homeowner-initiated scope change (homeowner asks for an additional fixture mid-job that wasn't on the original permit) are a change-order conversation handled separately.
- **The Richmond example is illustrative, not normative.** Any AHJ-specific detail in the example (TPR height, sediment-trap interpretation, combustion-air calculation, pan-required-or-not) should be re-verified for the shop's actual jurisdiction before submission. The skill's value is the structure and the prompts to reach into the shop's local-AHJ knowledge — not the specific rules.
- **Tier 3 jobs may require an engineer of record.** Whole-house repipe with service upgrade, sewer lateral with right-of-way work, multi-appliance gas systems, anything in a historic district with façade implications — at the higher end, the shop is not the only signature on the package. The skill's Artifact 1 will flag the engineer-of-record requirement; do not produce Artifact 2 without confirming that engagement first.
