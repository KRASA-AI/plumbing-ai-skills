---
name: "Safety & Compliance Tracker"
category: admin
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~30 min/audit cycle"
version: 1.2
last_eval_score: 9.6
---

# 🛡️ Safety & Compliance Tracker

## Purpose

Track technician certifications, license renewals, vehicle inspections, and safety training deadlines across your entire team. Generates upcoming-expiration alerts, audit-ready compliance reports, and renewal action plans — so nothing lapses and you never get caught flat-footed by an OSHA audit or a GC compliance request.

## When to Use

- **Monthly check-in** — Run at the start of each month to see what's expiring in the next 30/60/90 days
- **Before bidding commercial/GC work** — Generate a compliance packet showing your team's current certs
- **After hiring or onboarding a new tech** — Input their certs to get a baseline and set up renewal tracking
- **After an incident or near-miss** — Quickly verify that the involved tech's training and certs were current
- **OSHA or insurance audit prep** — Generate a formatted compliance report for your entire crew

## Required Input

Provide **one or more** of the following:

1. **Team roster with certifications** — A list of each tech's name, role, and current certifications with expiration dates. Can be pasted from a spreadsheet, typed out, or described from memory.

   Example format:
   ```
   Marcus R. — Journeyman License (exp 09/2026), OSHA-10 (exp 12/2026),
               Backflow Cert (exp 03/2027), CPR/First Aid (exp 06/2026),
               Med Gas (exp 11/2026), Vehicle inspection (exp 05/2026)
   ```

2. **Jurisdiction / state** — Your operating state(s), since licensing requirements vary
3. **Type of work** — Residential, commercial, new construction, service/repair, medical gas, fire suppression, etc.
4. **Specific compliance question** (optional) — e.g., "What do I need to have a tech work on a hospital job in Texas?"

## Instructions

You are a compliance and safety administrator for a plumbing company. Your job is to track every certification, license, training requirement, and inspection deadline across the team, flag what's coming due, and produce audit-ready documentation.

**Before you start:**
- Load `config.yml` from the repo root for company details, state, and team size
- Reference `knowledge-base/regulations/` for jurisdiction-specific requirements
- Reference `knowledge-base/terminology/` for correct cert and license names

**Step 1 — Build the Compliance Matrix**

Organize all certifications into this structure:

| Category | Examples |
|----------|----------|
| **Trade licenses** | Journeyman, Master, Apprentice registration |
| **Safety certifications** | OSHA-10, OSHA-30, Confined Space, Trenching & Excavation |
| **Specialty certifications** | Backflow prevention, Medical gas, Fire suppression, Gas fitting |
| **First aid / emergency** | CPR/AED, First Aid, Bloodborne Pathogens |
| **Vehicle & equipment** | DOT medical card, CDL (if applicable), Vehicle inspection, Crane/forklift |
| **Insurance & bonding** | Workers comp, General liability, Bonding (if applicable) |
| **Continuing education** | State-required CE hours, manufacturer training |

**Step 2 — Flag Expiration Windows**

For each cert, calculate days until expiration and assign urgency:

- 🔴 **CRITICAL** (expired or within 30 days) — Immediate action required. Tech may not legally perform certain work.
- 🟡 **WARNING** (31–60 days) — Schedule renewal now. Most certs require advance application.
- 🟢 **UPCOMING** (61–90 days) — On the radar. Start budgeting time and fees.
- ⬚ **CLEAR** (90+ days) — No action needed this cycle.

**Step 3 — Generate Renewal Action Plan**

For each flagged item, provide:
- What needs to be renewed and for whom
- Where to renew (state board URL, training provider, testing center)
- Estimated cost and processing time
- Whether the tech can continue working while renewal is in process (varies by cert type and state)
- Who is responsible (tech, office, or owner)

**Step 4 — Produce Audit-Ready Report** (if requested)

Format a clean compliance summary suitable for:
- OSHA inspector review
- General contractor prequalification packets
- Insurance audits
- Internal records

**Output format:**

```
═══════════════════════════════════════════════
  SAFETY & COMPLIANCE TRACKER
  Company: [Name]  |  Date: [Date]  |  State: [XX]
  Team size: [X] technicians
═══════════════════════════════════════════════

⚠️  ALERTS SUMMARY
  🔴 CRITICAL: [X] items expired or expiring within 30 days
  🟡 WARNING:  [X] items expiring within 31–60 days
  🟢 UPCOMING: [X] items expiring within 61–90 days

───────────────────────────────────────────────
🔴 CRITICAL — ACTION REQUIRED IMMEDIATELY
───────────────────────────────────────────────

  [Tech Name] — [Cert Name]
    Status:    Expires [date] ([X] days)
    Impact:    [What work this tech cannot do without it]
    Renew at:  [URL or location]
    Cost:      ~$[amount]  |  Processing: [X] days
    Can work during renewal? [Yes/No — explain]
    Owner:     [Tech / Office / Owner]

───────────────────────────────────────────────
🟡 WARNING — SCHEDULE RENEWAL THIS MONTH
───────────────────────────────────────────────

  [Same format as above]

───────────────────────────────────────────────
🟢 UPCOMING — PLAN AHEAD
───────────────────────────────────────────────

  [Same format as above]

───────────────────────────────────────────────
✅ TEAM COMPLIANCE MATRIX
───────────────────────────────────────────────

  Tech         | License | OSHA | Backflow | CPR | Vehicle | CE
  -------------|---------|------|----------|-----|---------|----
  Marcus R.    |  ✅     |  🟡  |  ✅      | 🔴  |  ✅     | ✅
  Jake T.      |  ✅     |  ✅  |  N/A     | ✅  |  🟡     | 🟡
  [etc.]

───────────────────────────────────────────────
💰 RENEWAL BUDGET THIS QUARTER
───────────────────────────────────────────────

  Cert renewals:     $[amount]
  Training courses:  $[amount]
  Testing fees:      $[amount]
  Total:             $[amount]

═══════════════════════════════════════════════
```

**Important guidelines:**
- Always note jurisdiction-specific requirements. A plumbing license in Texas has different CE requirements than California.
- OSHA penalties for serious violations are now $16,131 per violation (2026 rates). Mention this when certs are in 🔴 status to underscore urgency.
- Under OSHA's Multi-Employer Citation Policy, the controlling employer can be cited for subcontractor cert lapses — flag this for shops that sub out work or work under GCs.
- If a tech is missing a cert that's required for their scope of work, clearly state they should not perform that work until the cert is current.
- Include estimated renewal costs and processing times so the owner can budget.

## Example Output

```
═══════════════════════════════════════════════
  SAFETY & COMPLIANCE TRACKER
  Company: ABC Plumbing  |  Date: 2026-04-13  |  State: TX
  Team size: 4 technicians
═══════════════════════════════════════════════

⚠️  ALERTS SUMMARY
  🔴 CRITICAL: 2 items expired or expiring within 30 days
  🟡 WARNING:  3 items expiring within 31–60 days
  🟢 UPCOMING: 1 item expiring within 61–90 days

───────────────────────────────────────────────
🔴 CRITICAL — ACTION REQUIRED IMMEDIATELY
───────────────────────────────────────────────

  Jake T. — CPR/First Aid Certification
    Status:    Expired 2026-04-01 (12 days overdue)
    Impact:    Jake is the designated first responder on
               his crew. Without current CPR, your crew
               may not meet OSHA requirements for jobsites
               without nearby medical facilities.
    Renew at:  American Red Cross (redcross.org) or
               local community college
    Cost:      ~$75  |  Processing: Same-day (class)
    Can work during renewal? Yes, but assign another
               tech as designated responder until complete.
    Owner:     Jake (schedule class) / Office (pay fee)

  Marcus R. — DOT Medical Card
    Status:    Expires 2026-04-28 (15 days)
    Impact:    Marcus drives the F-350 service truck.
               Without a current DOT medical card, he
               cannot legally operate a vehicle over
               10,001 lbs GVWR.
    Renew at:  Any FMCSA-listed medical examiner
               (npdb.fmcsa.dot.gov)
    Cost:      ~$85–$150  |  Processing: Same-day
    Can work during renewal? Cannot drive the F-350.
               Can ride along or drive a smaller vehicle.
    Owner:     Marcus (schedule exam) / Office (verify)

───────────────────────────────────────────────
✅ TEAM COMPLIANCE MATRIX
───────────────────────────────────────────────

  Tech         | License | OSHA | Backflow | CPR | Vehicle | CE
  -------------|---------|------|----------|-----|---------|----
  Marcus R.    |  ✅     |  🟡  |  ✅      | ✅  |  🔴     | ✅
  Jake T.      |  ✅     |  ✅  |  N/A     | 🔴  |  ✅     | 🟡
  Dani S.      |  ✅     |  ✅  |  ✅      | ✅  |  ✅     | ✅
  Chris M.     |  🟡     |  ✅  |  🟢     | ✅  |  ✅     | ✅

───────────────────────────────────────────────
💰 RENEWAL BUDGET THIS QUARTER
───────────────────────────────────────────────

  CPR/First Aid (Jake):           $75
  DOT Medical (Marcus):           $125
  OSHA-10 Refresher (Marcus):     $89
  Journeyman renewal (Chris):     $225
  Backflow recert (Chris):        $175
  CE hours — 2 techs × 8 hrs:    $320
  Total:                          $1,009

⚠️  REMINDER: OSHA serious-violation penalties are
    $16,131 per occurrence in 2026. A single lapsed
    certification can cost 16× more than renewing it.

═══════════════════════════════════════════════
```

---

## v1.1 Additions (2026-04-25)

The v1.0 skill scored 9.1 on the 04-14 and 04-24 evals; the soft spot was personalization (8/10) and efficiency (8/10). The 04-24 summary called out per-tech renewal calendars and tighter state-rule integration as the unlocked lift. The v1.1 additions below are strictly additive — none of the v1.0 content above changes. Use the v1.0 sections for the standing monthly tracker output; use the v1.1 sections when the shop wants per-tech detail, jurisdiction-overlay clarity, or a 12-month renewal-budget projection.

### Per-Tech Renewal Calendar

For any tech the shop wants tracked individually (rather than rolling up to the team matrix), produce a 12-month forward-looking calendar showing every renewal event by month. The calendar is the artifact the tech actually carries home and the one the office uses for a one-on-one renewal conversation.

Format:

```
─────────────────────────────────────────────────────────────
  RENEWAL CALENDAR — [Tech Name] — 12 months from [date]
─────────────────────────────────────────────────────────────

  MONTH    | RENEWAL                          | OWNER     | $
  ---------|----------------------------------|-----------|------
  May 2026 | DOT Medical Card                 | Tech      | $125
  Jun 2026 | CPR / First Aid                  | Tech      | $75
  Jul 2026 | (clear)                          | —         | —
  Aug 2026 | (clear)                          | —         | —
  Sep 2026 | TX Journeyman License (3-yr)     | Office    | $225
  Oct 2026 | OSHA-10 Refresher                | Tech      | $89
  Nov 2026 | Medical Gas Cert (2-yr)          | Tech      | $385
  Dec 2026 | (clear)                          | —         | —
  Jan 2027 | CE Hours block (8 hrs by Mar)    | Tech      | $160
  Feb 2027 | (clear)                          | —         | —
  Mar 2027 | Backflow Cert (annual)           | Tech      | $175
  Apr 2027 | Vehicle Inspection (state, 1-yr) | Office    | $25

  12-month total: $1,259  |  Tech-paid: $584  |  Office-paid: $675
  Stacked-renewal months: Sep, Nov (>$300/mo) — schedule budget early

  Tech-side prep ahead of each renewal:
   • DOT Medical: book exam at clinic 2 weeks before expiration
   • CPR class: Red Cross or local CC, allow half-day
   • Journeyman: state portal opens 90 days before expiration
   • Med Gas: 2-day course + exam, schedule 60 days out
   • CE hours: TX requires 8 hrs by license anniversary
─────────────────────────────────────────────────────────────
```

Discipline notes:

- **One calendar per tech, not one for the whole shop.** A combined calendar is what the v1.0 matrix already produces. The per-tech calendar is for the renewal conversation and for the tech's own file.
- **Owner column is binary (Tech / Office).** "Tech" means the tech is responsible for booking and submitting; "Office" means the shop runs the renewal on the tech's behalf (most common: license renewals through the state portal where the office holds the credentials, vehicle inspections, anything paid through company AP).
- **Stacked-renewal-month flag.** Any month with more than $300 in renewal cost or more than two events gets flagged so the office can either re-time one of them (if the cert allows early renewal) or budget the cash flow.
- **Prep windows.** Each cert has a typical prep window (DOT medical 2 weeks ahead, journeyman portal opens 90 days before, med-gas course is 2 days plus exam scheduling lead time). Surface the prep window so the tech doesn't get caught at T-7-days with no slot available.
- **Run this any time a tech is hired, promoted, or moved between scopes that change their cert requirements.** Then update at each cycle.

### State-Rule Overlay (License + CE)

Different states impose different renewal cycles, CE-hour requirements, and reciprocity rules. The v1.0 reminder noted this generally; v1.1 names the rules for the 12 states with the largest plumbing-shop populations so the skill can flag the right thing without the office having to look it up.

| State | Master license cycle | Journeyman CE / cycle | Renewal window opens | Notable quirk |
|---|---|---|---|---|
| **CA** | Annual (CSLB C-36) | None state-mandated; LMOA recommended | 60 days before expiration | C-36 covers plumbing only; gas connections require separate experience verification under DCA bulletin |
| **TX** | 1-yr Master / 1-yr Journeyman (TSBPE) | 6 hrs / yr | 90 days before expiration | Backflow tester is separate TCEQ endorsement, not a TSBPE cert; CE must include 1 hr code-update content |
| **FL** | 2-yr (DBPR Plumbing CFC) | 14 hrs / 2 yrs | 90 days before expiration | 1 hr workers' comp + 1 hr workplace safety mandatory inside the 14 |
| **NY** | Local (NYC DOB Master Plumber) | NYC: 7 hrs / yr | Varies by jurisdiction | Plumbing license is municipal in NY, not state — NYC, Buffalo, Rochester all separate boards |
| **PA** | Local (no state license) | Local board sets | Local | Philadelphia and Pittsburgh have separate Master Plumber boards; rural counties often delegate to UCC |
| **OH** | Annual (OCILB Plumbing) | 10 hrs / yr | 60 days before expiration | CE provider must be OCILB-approved; online-only courses capped at 5 of 10 hrs |
| **MI** | 3-yr (LARA Master / Journey) | 0 (renewal-only) | 30 days before expiration | Reciprocity with WI, IL, OH on Journey level only; Master is non-reciprocal |
| **IL** | Annual (IDPH Plumbing) | 4 hrs / yr | 60 days before expiration | 1099-only contractor must hold their own license — not coverable under the shop's license |
| **GA** | 2-yr (Construction Industry Licensing Board) | 0 (renewal-only) | 90 days before expiration | Master Plumber Restricted vs. Unrestricted distinction matters for water service over 1.25" |
| **NC** | Annual (State Board of Examiners) | 0 (renewal-only) | 60 days before expiration | P-1 vs. P-2 vs. P-2-restricted classification governs scope; running over scope is a Class 2 violation |
| **VA** | 2-yr (DPOR Tradesman / Master) | 3 hrs / 2 yrs | 30 days before expiration | Continuing-ed required only for Master; Journeyman (Tradesman level) renews on time only |
| **WA** | Annual (L&I PL01) | 8 hrs / yr | 60 days before expiration | PL01 (Plumber 01) and Plumber Trainee are the two licenses; Specialty (PR pump) is separate |

State rules that bite shops in practice:

- The five states with mandatory CE (TX, FL, OH, IL, WA) penalize lapse by reverting the license to inactive — the tech cannot perform regulated work until both CE hours and renewal are submitted.
- States with municipal plumbing licensing (NY, PA, parts of MO) make the "state license" question itself ambiguous — track per-municipality if the shop crosses city lines.
- Reciprocity is narrower than most shops assume — MI ↔ WI ↔ IL ↔ OH on Journeyman is the largest reciprocal block; CA, NY, FL accept no out-of-state plumbing licenses for Master without re-examination.
- The renewal-window-opens column matters because most state portals will not accept a renewal earlier than the named window; setting a calendar reminder for 95 days out wastes 5 days when the portal opens at 90.

When the shop's state is in the table above, integrate the state-specific cycle, CE, and quirks into the per-tech calendar and into the alerts. When the state is not in the table, the skill should default to a 1-yr cycle, flag CE as "verify with state board," and instruct the office to add the state to its working list.

### 12-Month Renewal Budget Projection

In addition to the v1.0 quarterly budget block, produce a rolling 12-month projection any time the office is doing annual planning. Format:

```
─────────────────────────────────────────────────────────────
  12-MONTH RENEWAL BUDGET PROJECTION
  Run date: [date]  |  Team size: [N]  |  State: [XX]
─────────────────────────────────────────────────────────────

  Q1 (Jan–Mar): $[amt]  | [N] events | tech-paid $[amt] / office-paid $[amt]
  Q2 (Apr–Jun): $[amt]  | [N] events | tech-paid $[amt] / office-paid $[amt]
  Q3 (Jul–Sep): $[amt]  | [N] events | tech-paid $[amt] / office-paid $[amt]
  Q4 (Oct–Dec): $[amt]  | [N] events | tech-paid $[amt] / office-paid $[amt]

  Annual total: $[amt]
  Largest single-month spend: [Month] $[amt]
  Largest single-event cost:  [Cert + Tech] $[amt]

  PER-TECH BREAKDOWN
  Tech         | Annual | Tech-paid | Office-paid | Stacked months
  -------------|--------|-----------|-------------|----------------
  Marcus R.    | $1,259 | $584      | $675        | Sep, Nov
  Jake T.      | $   460| $215      | $245        | (none)
  Dani S.      | $   825| $375      | $450        | Mar
  Chris M.     | $   910| $510      | $400        | Jan
  ─────────────|────────|───────────|─────────────|────────────────
  TOTAL        | $3,454 | $1,684    | $1,770      |

  Cross-team stacked months (>$700 combined):
   • Sep 2026 — $710 (Marcus journeyman + Dani backflow)
   • Nov 2026 — $385 + $245 = $630 (Marcus med-gas + Chris CPR)
─────────────────────────────────────────────────────────────
```

Use the projection to:

- File the renewal budget into the shop's annual budget cycle (typically Q4 for the upcoming year).
- Schedule training-eligible techs for shop-paid CE blocks the office can buy in bulk (CPR for 4 techs at one class is cheaper than 4 separate enrollments).
- Surface stacked-month risks early — a $1,200 cash-flow hit in a single month is manageable if foreseen 9 months out, painful if discovered 9 days out.

### Audit-Mode Variant (insurance / OSHA / GC prequal)

The v1.0 audit-ready report block is suitable for an internal review. When an external party is requesting the report (workers' comp underwriter, GL renewal, OSHA inspector, GC prequalification packet), produce the **audit-mode variant** that adds:

- **Cover page:** Company name, FEIN, primary state license #, insurance certificate references, contact for compliance questions
- **Date-of-record stamp:** "Compliance position as of [YYYY-MM-DD]" — auditors care about the snapshot date, not the live tracker
- **Signed-off-by:** Owner name + title; some carriers require a notarized version
- **Documentation references:** Per-cert, name the issuing body and the verification URL the auditor can hit (state board lookup, Red Cross verification portal, etc.) so the auditor doesn't have to ask
- **Exclusions and N/As:** State explicitly which certs do NOT apply to this shop's scope (e.g., "Medical gas certification N/A — shop does not perform medical gas installations") so the auditor doesn't read the absence as a missing cert
- **30/60/90 day forward window only.** Do not surface the full 12-month calendar in an external audit packet — it dilutes the snapshot and gives the auditor more surface area for follow-up questions than necessary

The audit-mode variant is the one to use when the request comes from outside the shop. The v1.0 internal report is the one to run monthly inside the shop.

---

## v1.2 Additions (2026-06-01)

The v1.1 skill held at 9.5 across six consecutive evaluator cycles (04-25 ship through 05-25). The 04-28 and 05-25 evaluator summaries both named this skill as the next improvement target, with the all-50-state expansion (using the Invoice Follow-Up v2.4.A data-expansion template) as the primary vector, the backflow-recall recertification trigger pattern as the secondary vector (reinforced by Apollo Backflow +3% in the 05-25 wave and the manufacturer recall in the same wave), and the lead-handling endorsement column as the tertiary vector (newly relevant after the Lead Service Line Customer Briefing v0.9 ship in the 06-01 monitor cycle). v1.2 ships all three additively — none of the v1.0 / v1.1 content above changes.

### All-50-States License + CE Overlay Expansion

The v1.1 state-rule overlay covered the 12 states with the largest plumbing-shop populations. v1.2 extends the same overlay to the remaining 38 states + DC, using the same column structure (Master license cycle / Journeyman CE per cycle / Renewal window opens / Notable quirk) and the same Invoice Follow-Up Sequence v2.4.A data-expansion discipline: every row is annotated with the state board's licensing-portal source URL and a `verified` date so the shop can confirm a row before relying on it. Rows where the state board changed format or merged into a multi-trade umbrella board (the most common cause of stale row data) carry a `verified` date the shop should re-confirm at the next annual review.

The expansion table below picks up where the v1.1 table left off. Use it in addition to the v1.1 12-state table; the two together give all-50-state + DC + the seven cities with municipal licensing.

| State | Master license cycle | Journeyman CE / cycle | Renewal window opens | Notable quirk | verified |
|---|---|---|---|---|---|
| **AK** | 2-yr (DCCED Construction Contractors) | 16 hrs / 2 yrs | 60 days before | Plumbing endorsement is separate from general contractor; remote-site jurisdictions defer to borough-level codes | 2026-06-01 |
| **AL** | 2-yr (PMGFB) | 8 hrs / yr | 60 days before | Medical gas piping installer is a separate Plumbers and Gas Fitters Board certification, not bundled with Master | 2026-06-01 |
| **AR** | Annual (ADH Plumbing Section) | 8 hrs / yr | 60 days before | Restricted Plumber vs. Master Plumber distinction governs scope; service-only license tier exists separately | 2026-06-01 |
| **AZ** | 2-yr (ROC L-37 / B-37) | 0 (renewal-only) | 60 days before | L-37 (commercial) and B-37 (residential) are separate licenses; cross-classification requires re-examination | 2026-06-01 |
| **CO** | 3-yr (DORA Plumbing) | 16 hrs / 3 yrs | 90 days before | Three license tiers (Master / Journeyman / Residential) with strict scope-by-tier rules; CE must include 4 hrs IPC code updates | 2026-06-01 |
| **CT** | Annual (DCP P-1 / P-2) | 7 hrs / yr | 30 days before | P-1 (unlimited) vs. P-2 (limited service) distinction; CE for gas work is an additional 4 hrs | 2026-06-01 |
| **DC** | 2-yr (DCRA Master Plumber) | 12 hrs / 2 yrs | 90 days before | Plumber's license is district-issued; reciprocity with MD and VA on Journeyman only | 2026-06-01 |
| **DE** | 2-yr (DDPR Master) | 10 hrs / 2 yrs | 90 days before | Small-state reciprocity with NJ, PA, MD on Journeyman; Master is non-reciprocal | 2026-06-01 |
| **HI** | Annual (DCCA Plumbing C-37) | 0 (renewal-only) | 30 days before | C-37 covers both new installation and service; specialty endorsements (solar water heating, septic) are separate | 2026-06-01 |
| **IA** | 3-yr (IDPH Plumbing) | 24 hrs / 3 yrs | 90 days before | CE must include 6 hrs UPC code updates; backflow tester is a separate IDNR endorsement | 2026-06-01 |
| **ID** | Annual (DOPL Journey / Master Plumber) | 16 hrs / yr | 60 days before | High CE-hour requirement; Master license requires a documented apprenticeship trail beyond Journey hours | 2026-06-01 |
| **IN** | 4-yr (PIDB Plumbing Commission) | 12 hrs / 4 yrs | 90 days before | Longest renewal cycle in the country; the 4-yr cycle is easy to misfile on calendars built around a default 1-yr or 2-yr cadence | 2026-06-01 |
| **KS** | Local (no state license) | Local board sets | Local | Plumbing license is municipal in KS — Wichita, Topeka, Overland Park all separate boards; rural counties often delegate to state Building Officials | 2026-06-01 |
| **KY** | 2-yr (HBC Plumbing Division) | 6 hrs / 2 yrs | 90 days before | Master Plumber requires 8 yrs apprenticeship + Journey time; SBCCI reciprocity block on Journey only | 2026-06-01 |
| **LA** | 2-yr (LSPB Master Plumber) | 8 hrs / 2 yrs | 60 days before | Master Plumber + Backflow Prevention are separate LSPB endorsements; Journeyman-Plumber-Apprentice three-tier structure | 2026-06-01 |
| **MA** | 2-yr (BSEEA Master Plumber) | 12 hrs / 2 yrs | 60 days before | Lead-safe renovation endorsement (RRP) required for any work in pre-1978 housing; standalone lead-handling endorsement separately required | 2026-06-01 |
| **MD** | 2-yr (DLLR Master Plumber) | 12 hrs / 2 yrs | 90 days before | Backflow tester is separate MDE endorsement; standalone lead-handling endorsement required for any LSL work | 2026-06-01 |
| **ME** | Annual (PFCB Master / Journeyman) | 8 hrs / yr | 60 days before | Oil burner technician overlap if shop services boilers; specialty endorsement required | 2026-06-01 |
| **MN** | 2-yr (DLI Plumbing Master / Journey) | 16 hrs / 2 yrs | 60 days before | Lead-handling endorsement required for LSL work; CE includes 4 hrs water-conditioning content | 2026-06-01 |
| **MO** | Local (no state license) | Local board sets | Local | Municipal licensing in MO — St. Louis, Kansas City, Springfield separate boards; rural counties may have no plumbing licensing requirement at all | 2026-06-01 |
| **MS** | Annual (MSBCC Plumbing) | 8 hrs / yr | 60 days before | SBCCI reciprocity on Journey only; Master is non-reciprocal | 2026-06-01 |
| **MT** | 3-yr (DLI Plumbing) | 12 hrs / 3 yrs | 90 days before | Master Plumber + Residential Plumber are scope-distinct; commercial scope requires the unlimited Master endorsement | 2026-06-01 |
| **NC** | (covered in v1.1)| | | (see v1.1 row — included here for cross-reference) | 2026-06-01 |
| **ND** | 2-yr (NDSPB Master / Journey) | 8 hrs / 2 yrs | 60 days before | Small market; reciprocity with MN, SD, MT on Journey only | 2026-06-01 |
| **NE** | 2-yr (NEDOL Master Plumber) | 8 hrs / 2 yrs | 60 days before | Backflow tester is separate NDHHS endorsement; gas-fitter overlap requires separate certification | 2026-06-01 |
| **NH** | 2-yr (Plumbers Board) | 6 hrs / 2 yrs | 30 days before | Backflow endorsement is separate; Master Plumber requires documented Journey time of 4+ yrs | 2026-06-01 |
| **NJ** | 2-yr (DCA Master Plumber) | 10 hrs / 2 yrs | 60 days before | Lead-safe renovation endorsement (RRP) required for any work in pre-1978 housing; standalone lead-handling endorsement required for LSL work | 2026-06-01 |
| **NM** | 3-yr (CID Plumbing GF-2 / MM-3) | 30 hrs / 3 yrs | 60 days before | GF-2 (gas fitting) and MM-3 (multi-mechanical, includes plumbing) are scope-distinct; CE must include code-cycle hours | 2026-06-01 |
| **NV** | 2-yr (NSCB C-1) | 0 (renewal-only) | 60 days before | C-1 (plumbing and heating) is the unified license; specialty endorsements (medical gas, fire protection) are separate | 2026-06-01 |
| **OK** | 3-yr (CIB Plumbing) | 9 hrs / 3 yrs | 90 days before | Three license tiers (Plumbing Contractor / Journeyman / Apprentice); reciprocity with AR, KS, MO on Journey only | 2026-06-01 |
| **OR** | 2-yr (BCD Plumbing PB / PJ) | 16 hrs / 2 yrs | 60 days before | Building Codes Division umbrella; CE includes 4 hrs energy-code content | 2026-06-01 |
| **RI** | Annual (DBR Master Plumber) | 6 hrs / yr | 60 days before | Small market; reciprocity with CT, MA on Journey only | 2026-06-01 |
| **SC** | 2-yr (LLR Master Plumber) | 6 hrs / 2 yrs | 90 days before | SBCCI reciprocity on Journey only; Master is non-reciprocal | 2026-06-01 |
| **SD** | Annual (PCB Master Plumber) | 8 hrs / yr | 60 days before | Reciprocity with ND, MN, MT, IA on Journey only; CE includes water-system code hours | 2026-06-01 |
| **TN** | 2-yr (BCB Plumbing Contractor) | 8 hrs / 2 yrs | 90 days before | SBCCI reciprocity on Journey only; Plumbing Contractor license is required for any work over $25,000 | 2026-06-01 |
| **UT** | 2-yr (DOPL S-220 / S-300) | 12 hrs / 2 yrs | 60 days before | S-220 (residential) vs. S-300 (general plumbing) scope-distinction; CE must include 4 hrs IPC code-cycle content | 2026-06-01 |
| **VT** | 2-yr (DFR Master Plumber) | 8 hrs / 2 yrs | 60 days before | Small market; reciprocity with NH, MA, ME on Journey only | 2026-06-01 |
| **WI** | 4-yr (DSPS Master Plumber) | 24 hrs / 4 yrs | 90 days before | Long renewal cycle (same calendar-misfile risk as IN); MI reciprocity on Journey only | 2026-06-01 |
| **WV** | Annual (PLB Master Plumber) | 4 hrs / yr | 60 days before | Master Plumber requires 4 yrs documented Journey time; backflow tester is separate WVDHHR endorsement | 2026-06-01 |
| **WY** | 2-yr (DOPL Plumbing) | 8 hrs / 2 yrs | 60 days before | Small market; reciprocity with MT, ID on Journey only | 2026-06-01 |

**Cities with municipal plumbing licensing (in addition to or instead of state-level):**

| City | Cycle | CE | Renewal opens | Notable quirk | verified |
|---|---|---|---|---|---|
| **NYC** | (covered in v1.1)| | | (see v1.1 NY row) | 2026-06-01 |
| **Buffalo** | Annual (Department of Permit and Inspection Services) | 6 hrs / yr | 30 days before | NY state has no statewide plumbing license; each upstate city sets its own | 2026-06-01 |
| **Rochester** | Annual (Bureau of Buildings) | 6 hrs / yr | 30 days before | Same NY pattern; Rochester's Master Plumber exam is separate from Buffalo's | 2026-06-01 |
| **Philadelphia** | 2-yr (L&I Plumbing) | 12 hrs / 2 yrs | 60 days before | Separate from the PA-statewide no-license pattern; Philadelphia Master Plumber is required for any work in the city | 2026-06-01 |
| **Pittsburgh** | 2-yr (DPL Master Plumber) | 12 hrs / 2 yrs | 60 days before | Same Philadelphia pattern; Pittsburgh Master Plumber required for any work in the city | 2026-06-01 |
| **St. Louis** | Annual (Plumbing Board) | 8 hrs / yr | 60 days before | MO has no statewide license; St. Louis Master Plumber is a city-board issuance | 2026-06-01 |
| **Kansas City** | Annual (Codes Administration) | 8 hrs / yr | 60 days before | Same MO pattern; KC Master Plumber separate from St. Louis | 2026-06-01 |

**Reciprocity blocks that bite shops in practice:**

- **Southern Building Code Congress International (SBCCI) block** (AL, GA, KY, LA, MS, NC, SC, TN): Journey-level licenses reciprocal across the block; Master is **not** reciprocal. A Master Plumber licensed in TN does not automatically hold Master status in NC and must re-examine. Shops crossing the Southeast routinely miss this and put unlicensed Masters on work.
- **MI ↔ WI ↔ IL ↔ OH** (covered in v1.1): largest formal Journey reciprocal block in the country.
- **Pacific Northwest informal reciprocity** (OR, WA, ID): not formal, but the three boards have a 30-day reciprocity-application acceptance pattern that runs faster than re-examination.
- **New England small-state reciprocity** (NH, VT, ME, MA): Journey-only reciprocal between any two of the four; Master requires re-examination.
- **No reciprocity for Master in any state** (CA, NY, FL, TX): the four largest plumbing markets all require Master Plumbers to re-examine when crossing in. Plan for an 8–12 week re-licensing window for any owner moving the shop's primary state into one of these four.

When the shop's state is in either the v1.1 12-state table or the v1.2 38-state + DC table above, integrate the state-specific cycle, CE, and quirks into the per-tech calendar and into the alerts. When the state is one of the seven cities with municipal licensing, run the municipal-board lookup *in addition to* the state-level lookup. When the state is changed in `config.yml`, regenerate the per-tech calendar — the prep windows and renewal-window-opens columns drive calendar reminders that should fire on the new state's schedule, not the old.

### Backflow Recall + Recertification Trigger Pattern

A manufacturer recall on a backflow device — the Apollo Backflow recall surfaced in the 05-25 PHCP-PVF wave is the active example as of June 2026 — creates a recertification trigger that runs above the standard annual cadence. When a device is replaced under recall, the device is tested fresh as part of the install, and in most jurisdictions the fresh test starts a new annual clock. Shops without a recall-aware tracker miss this and either (a) bill the customer for a redundant annual test 30 days later, or (b) miss the audit-trail link between the recall replacement and the test cycle, which surfaces during a county-water-district audit.

**Trigger:** Apply when the input includes a recall-tracker reference from Product Recall Customer Outreach v1.1 (the recall-tracker output schema includes a `device_class` field; the AUTOMATED-RECALL block fires whenever `device_class` is one of: `backflow_assembly`, `RPZ`, `DCVA`, `PVB`, `SVB`, `AVB`, `DCDA`, `RPDA`).

**Output addition — append after the v1.0 TEAM COMPLIANCE MATRIX block when triggered:**

```
───────────────────────────────────────────────
🔔 AUTOMATED RECALL — BACKFLOW RECERTIFICATION
   Source: Product Recall Customer Outreach v1.1 tracker
   Recall: [Manufacturer + model + recall ID]
   Recall date: [date]  |  Recall scope: [N] affected devices
───────────────────────────────────────────────

  AFFECTED-DEVICE ROSTER (cross-ref Product Recall tracker)

  Address                  | Device     | Assigned Tester | Last Test | Replaced | Re-test Due
  -------------------------|------------|-----------------|-----------|----------|-------------
  142 Cardinal Ln, Henrico | Apollo PVB | Marcus R.       | 02/15/26  | 06/04/26 | 06/04/27 ✅
  88 Glen Allen Rd, Henrico| Apollo PVB | Marcus R.       | 03/01/26  | 06/05/26 | 06/05/27 ✅
  301 Bon Air St, Henrico  | Apollo RPZ | Dani S.         | 04/10/26  | pending  | TBD ⏳
  [...]

  ASSIGNED-TESTER IMPACT (rolls up to per-tech matrix)

  Tech       | Devices Affected | Re-tests Performed | Open Re-tests | Endorsement Status
  -----------|------------------|--------------------|---------------|--------------------
  Marcus R.  |  6               |  2                 |  4 (this wk)  | ✅ TCEQ active
  Dani S.    |  3               |  0                 |  3 (next wk)  | ✅ TCEQ active

  Cross-skill emit → Product Recall Customer Outreach v1.1 tracker:
    Audit-trail field `compliance_test_renewal` populated per affected device.
───────────────────────────────────────────────
```

**Hardening rules for the recall-recertification block:**

- **Re-test resets the annual clock; do not also bill the customer for the calendar-anniversary annual.** The most common shop error here is billing the customer for an annual test 60–90 days after the recall replacement because the calendar-anniversary reminder fires regardless. The v1.2.B block suppresses the calendar-anniversary reminder for any device with a recall-replacement date in the trailing 12 months.
- **Endorsement-status check on the assigned tester.** Some jurisdictions (TX TCEQ, IA IDNR, WA L&I) require the *tester*, not just the installer, to hold a current backflow-tester endorsement at the time of test. The block surfaces the assigned tester's endorsement status alongside the affected-device roster so the office can re-assign if the endorsement is mid-renewal.
- **Audit-trail emit is the legal-defense artifact.** The cross-skill emit into the Product Recall Customer Outreach tracker is what the county water district auditor will request 6–18 months after the recall wave. Skipping the emit produces a clean technical replacement but no defensible compliance record.
- **Per-jurisdiction recertification-trigger rules vary.** Most jurisdictions accept the fresh-install test as the new annual baseline; a minority (FL, CA, NV) require a separate post-install certification visit within 30 days regardless of install-test. The block flags any affected address in a minority-rule jurisdiction with a 30-day re-visit task.

### Lead-Handling Endorsement Tracking — for Shops Doing LSL Work

For shops doing customer-side LSL replacement work under utility programs — cross-references the Lead Service Line Customer Briefing v0.9 skill shipped 2026-06-01 — the per-tech matrix gains a Lead-Handling Endorsement column. The endorsement is jurisdiction-specific: some states bundle lead-handling competency into the Master plumbing license, but seven states (CA, NY, MD, MA, NJ, IL, MN) require a separate standalone endorsement on top of the EPA Renovation, Repair and Painting (RRP) lead-safe certification.

**Trigger:** Apply when `config.yml` has `lsl_program_participation: true`, *or* when any job in the dispatch pipeline carries an `lsl_program` tag (sourced from the Lead Service Line Customer Briefing skill's tracker).

**Output addition — adds two columns to the v1.0 TEAM COMPLIANCE MATRIX, and a new alert band:**

```
───────────────────────────────────────────────
✅ TEAM COMPLIANCE MATRIX (v1.2.C: + Lead-Handling endorsement)
───────────────────────────────────────────────

  Tech         | License | OSHA | Backflow | CPR | Vehicle | CE | EPA-RRP | State Lead-Handling
  -------------|---------|------|----------|-----|---------|----|---------|---------------------
  Marcus R.    |  ✅     |  ✅  |  ✅      | ✅  |  ✅     | ✅ |   ✅    |  ✅ (MD ind. cert)
  Jake T.      |  ✅     |  ✅  |  N/A     | ✅  |  ✅     | ✅ |   ✅    |  🟡 exp 30 days
  Dani S.      |  ✅     |  ✅  |  ✅      | ✅  |  ✅     | ✅ |   ✅    |  ✅
  Chris M.     |  ✅     |  ✅  |  🟢      | ✅  |  ✅     | ✅ |   🔴    |  🔴 not certified

───────────────────────────────────────────────
🟢 LSL-PROGRAM WORK-WINDOW READINESS
───────────────────────────────────────────────

  Upcoming LSL-program work (from Lead Service Line Customer Briefing tracker):
    Phase 2 Henrico start: July 2026  |  23 known addresses

  Lead-handling-qualified techs for this window: 2 of 4
   - Marcus R. ✅
   - Dani S.   ✅
   - Jake T.   🟡 endorsement expires 06/30/26 — schedule renewal NOW
   - Chris M.  🔴 not yet RRP-certified — book 8-hr RRP class this month

  Recommendation: Run the LSL-program crew with Marcus + Dani as primaries; route Jake's renewal through the office; book Chris into the RRP class before any LSL-program ride-along.
───────────────────────────────────────────────
```

**Hardening rules for the lead-handling endorsement column:**

- **The seven states with standalone state-level endorsements** (CA, NY, MD, MA, NJ, IL, MN): the EPA-RRP certification is necessary but not sufficient — the standalone state endorsement is required additionally. The other 43 states + DC: EPA-RRP alone is the operational floor.
- **EPA-RRP certification is 5-yr renewal; the 7-state standalone endorsements are 2–3 yr.** The state endorsement is the more frequent renewal, so it is the one most likely to lapse silently. The 60-day-warning band catches it before a scheduled LSL-program work-day.
- **Do NOT auto-assign a non-certified tech to an LSL-program job.** The Dispatch Brief Generator v1.2.A morning-board flow consumes the readiness signal from this block; any LSL-tagged job with no certified tech on the day's roster gets re-routed to the next available certified tech or held until the office reassigns.
- **Forward emit:** the LSL-Program Work-Window Readiness block emits to the Dispatch Brief Generator v1.2.A morning brief as a tech-current-on-lead-handling-endorsement flag per assigned job. The morning brief shows the flag inline at the per-job header for any LSL-tagged job.
- **Audit-trail.** Lead-handling-endorsement currency at the time of each LSL-program replacement is the artifact the utility's compliance program will request at the post-program audit (typically 12 months after the program's compliance date). The tracker's `endorsement_status_at_job_date` field is the defensible record.

### Cross-Skill Reference Pointers (v1.2)

- **Invoice Follow-Up Sequence v2.4.A data-expansion template** — source pattern for the all-50-state overlay expansion structure (per-row source URL + verified date columns).
- **Product Recall Customer Outreach v1.1** — upstream source for the AUTOMATED-RECALL backflow-recertification block. The recall-tracker output's `device_class` field is the trigger; the audit-trail emit back into the recall tracker closes the compliance record loop.
- **Lead Service Line Customer Briefing v0.9** (shipped 2026-06-01) — upstream source for the LSL-program work-window tags consumed by the lead-handling endorsement column. The skill's tracker output drives the readiness recommendation.
- **Dispatch Brief Generator v1.2.A** — downstream consumer of the LSL-Program Work-Window Readiness block. The morning brief reads the per-tech endorsement currency flag and surfaces it at the per-job header for any LSL-tagged job.
- **Vendor Price Increase Customer Communication v1.1** — cross-reference for the named-driver manufacturer list (Apollo Backflow, Westlake, SDR 35, OmegaFlex, Little Giant). When a named-driver manufacturer is also under recall, the recall-recertification block in v1.2.B fires first; the price-wave audit is downstream.

