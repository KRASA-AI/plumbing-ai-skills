---
name: "Safety & Compliance Tracker"
category: admin
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~30 min/audit cycle"
version: 1.1
last_eval_score: 9.5
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
