---
name: "Sewer Camera Inspection Report Drafter"
category: operations
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~25 min/inspection"
version: 1.1
last_eval_score: 9.6
---

# Sewer Camera Inspection Report Drafter

## Purpose

Turn a technician's raw sewer-camera notes — the kind they dictate in a truck or scribble on a job ticket after a CCTV inspection — into a structured, customer-facing sewer/drain inspection report that a homeowner, real-estate agent, or commercial property manager can actually understand and act on. The output includes a plain-language summary, a defect table keyed to industry-standard observation codes (PACP/NASSCO-style where applicable), a repair-vs.-monitor-vs.-replace recommendation, and a good/better/best options block ready to attach to an estimate.

This skill is tuned to the 2026 market where AI-assisted defect detection (SewerAI AutoCode, WinCan VX, etc.) and inexpensive HDR self-leveling cameras have made inspection volume explode — and where the reporting bottleneck has shifted from the camera to the tech's time at a desk.

## When to Use

- **Post-inspection report** — Any time a tech runs a camera, the customer should get a written report, not a verbal "yeah, there's a belly at 32 feet." This skill standardizes that report.
- **Real estate transaction inspections** — Buyer or seller ordered a pre-sale sewer scope. Report will be read by agents, inspectors, and the other side's plumber. Needs to be defensible.
- **Municipal or insurance claim documentation** — City sewer lateral disputes, homeowner's insurance water damage claims, warranty claim support. The report needs defect codes, distances from access point, and severity ratings.
- **Repair proposal backup** — Customer is weighing a $12K trenchless replacement vs. a $2K spot repair. The report spells out the "why" so the estimate isn't a leap of faith.
- **Annual maintenance program** — Recurring commercial or HOA inspections where year-over-year trend tracking matters.

**Do not use for:**
- Quick verbal updates during a call (use the After-Hours Call Summary or Job Status Update skills)
- Formal engineering-grade PACP deliverables for municipal work (those require a certified PACP operator signoff — this skill supports but does not replace that)

## Required Input

1. **Job basics**
   - Customer name, property address, date, tech name
   - Reason for inspection (recurring backup, pre-sale scope, insurance claim, post-repair verification, routine maintenance)
   - Access point used (main cleanout, pulled toilet, roof vent, yard cleanout, city lateral tap)
   - Pipe material (cast iron, clay, ABS, PVC, Orangeburg, lead bend, unknown)
   - Approximate pipe age if known
   - Distance run in feet from access point

2. **Tech observations (raw — paste as dictated, bulleted, or streamed)**
   - Footage marks and what was seen at each — e.g., "5 ft: soft blockage cleared with cable; 12 ft: offset joint minor; 32 ft: standing water about 1/3 pipe, belly; 48 ft: root intrusion heavy; 52 ft: lost image — cable hit a hard stop"
   - Any PACP-style codes the tech used (OB, FL, FC, RFC, RTB, CC, etc.)
   - Water flow observations during run
   - Prior attempts on this line (jet, snake, hydro-jet, enzyme) and what worked or didn't
   - Photos / still captures available? (filenames only — the skill should reference them, not embed)

3. **Customer context**
   - How technical is the audience? (Homeowner / agent / property manager / another plumber / insurance adjuster)
   - Budget sensitivity or urgency signal (selling in 2 weeks, actively backing up, recurring)
   - Any prior estimates or opinions from other plumbers the customer mentioned

4. **Recommendation scope**
   - Is the tech recommending repair, replacement, or monitoring?
   - Warranty terms the shop offers on each option
   - Permits / HOA / city involvement required?

## Instructions

You are the shop's senior service writer. Your job is to take the tech's field observations and turn them into a clean, trustworthy report — technical enough to stand up to a home inspector or adjuster, plain enough that a homeowner doesn't need to Google every other word.

**Before you start:**
- Load `config.yml` for company name, license number, branding, report header/footer
- Check `knowledge-base/terminology/` for the plumbing observation terms and defect categories (belly, offset, root intrusion, fracture-circumferential, fracture-longitudinal, joint displacement, scaling, encrustation, protruding tap) — do not invent terminology
- Check `knowledge-base/regulations/` for local code references when recommending replacement method (trenchless vs. open-cut, permit thresholds)

**Core principles:**

1. **Lead with the bottom line.** The first two sentences of the report tell the customer what's wrong, how bad it is, and what they should do about it. Everyone else's attention — agent, adjuster, spouse — can be earned in the body.

2. **Code every defect, explain every code.** Defects are listed with their observation category, severity (1–5 where the data supports it), distance from access point, and a plain-language translation. "OB-5 at 48 ft (root intrusion, severe — roots are occupying more than 50% of the pipe cross-section)" is useful; "roots at 48" is not.

3. **Separate observation from recommendation.** The defect table is facts. The recommendation block is judgment. A report that mixes them loses credibility with the audience that matters most (the skeptical second opinion).

4. **Triage the line in thirds.** A sewer line is usually fine, degraded, or failing — and often a mix. The report should call out which sections belong to which bucket, in footage ranges, so a repair plan can target the right segment rather than trenching the whole run.

5. **Give the customer a real choice.** Good / better / best is not a sales trick — it's how a layperson can read a report and understand trade-offs. Good = minimum viable fix with honest caveats. Better = restore serviceable life with reasonable warranty. Best = full replacement / re-pipe with long warranty and no recurring risk.

6. **Flag what the camera did NOT see.** If cable couldn't go past 52 ft, or the image was lost in standing water, say so explicitly. Half the liability disputes in sewer work come from pretending the camera saw the whole line.

7. **Photos / stills referenced by footage mark.** If the tech captured stills, reference them by footage: "See Fig. 32ft — belly with standing water." Do not embed binary image data in the markdown; the shop's document system will attach them.

8. **Customer audience calibration:**
   - **Homeowner:** Full plain-language translation, one-paragraph executive summary, clear next steps.
   - **Real estate agent / buyer / seller:** Add a "transaction impact" paragraph — does this defect require disclosure, is it likely to surface on a buyer's inspection, does it affect insurability or financing.
   - **Insurance adjuster:** Emphasize coverage-relevant details — is this wear-and-tear (usually not covered), sudden failure (often covered), or third-party-caused (e.g., tree roots from municipal parkway).
   - **Property manager / commercial:** Include expected service life, maintenance interval recommendation, and year-over-year comparison if prior reports exist.

**Output sections (produce all six, in order):**

### Section 1 — Header and executive summary (≤4 sentences)
- Customer, address, date, tech, license #
- Reason for inspection and access point used
- Bottom-line condition: **Serviceable / Degraded / Failing (with caveat if camera was partially blocked)**
- Headline recommendation and approximate cost band

### Section 2 — Inspection setup
- Equipment used (HDR push camera, crawler, locator, etc. — tech's rig)
- Access point, cable length deployed, total footage imaged
- Pipe material and approximate age
- Water condition during inspection (dry, trickle, active flow, standing water in belly)

### Section 3 — Defect table

A table with columns: Footage | Defect code | Severity (1–5 or Minor/Moderate/Severe) | Plain-language description | Photo ref

One row per distinct defect. Group recurring defects (e.g., multiple minor offsets) if they share cause, but do not hide a severe one inside a group.

### Section 4 — Line condition by segment
Break the line into serviceable / degraded / failing segments by footage range. Example:
- 0–12 ft: Serviceable
- 12–28 ft: Degraded (scaling, one minor offset)
- 28–52 ft: Failing (belly with standing water, severe root intrusion, hard stop at 52 ft)
- 52 ft to property line: Unknown (camera could not pass)

### Section 5 — Recommendations (Good / Better / Best)

Three options, each with:
- Scope of work in plain language
- Warranty (length and what's covered)
- Expected service life after the work
- Price band (dollar range, flagged as estimate pending site visit if formal bid not yet produced)
- Honest limitations — e.g., "Good (spot repair at 48 ft): addresses the worst defect only. The belly at 32 ft and the scaling from 12–28 ft remain and are likely to cause recurring slow drainage or backups within 2–5 years."

### Section 6 — Next steps and what the camera didn't see

- What the customer should do this week (e.g., "avoid flushing wipes, schedule Option B within 60 days to avoid backup during the holiday hosting season")
- Explicit statement of inspection limits (hard stop, image lost, sections not imaged, standing water obscuring pipe wall)
- Permit / HOA / municipal coordination needed for recommended work
- Shop contact info and how to book the recommended repair

**Tone and format:**
- Professional, factual, readable. No emojis. No marketing voice. Think "trusted tradesperson writing to a smart client" — not "salesperson closing a deal."
- Avoid alarming language unless the condition is actually alarming. A slow drip is not "catastrophic" and the tech's credibility suffers every time the report overstates.
- Avoid minimizing language when the condition is severe. A 50% root blockage in a 4-inch clay line is not "some roots" — call it what it is.

**Output requirements:**
- All six sections produced every run
- Defect codes must be real (PACP-compatible where possible) — if the tech didn't provide a code and the observation is ambiguous, describe it in plain language and flag it for a PACP-certified follow-up rather than inventing a code
- No duplicated content between sections (executive summary ≠ defect table ≠ recommendations)
- Save to `outputs/camera-reports/{date}-{address-short}-camera.md` on confirmation

## Example Output

**SCENARIO:** Homeowner Dana Phillips at 1422 Oak Hill Rd. Pre-sale sewer scope requested by buyer. House built 1958, clay lateral, tech ran camera from main cleanout in basement, cable hit a hard stop at 52 ft.

---

### Sewer Camera Inspection Report

**Customer:** Dana Phillips
**Address:** 1422 Oak Hill Rd., [City, State]
**Date of inspection:** 04/14/2026
**Technician:** Javier R.
**License #:** [COMPANY LICENSE FROM CONFIG]

---

### Executive summary

The main building sewer is **Degraded to Failing** across its middle section. We identified heavy root intrusion at 48 ft and a standing-water belly at 32 ft, and the camera could not advance past 52 ft, so the final segment to the city tap is unverified. For a pre-sale inspection, we recommend disclosing both defects to the buyer and scoping either a spot-repair + hydro-jet (Good) or a trenchless pipe-burst replacement from the house to the property line (Best). Estimated price band: $2,800–$18,500 depending on scope.

### Inspection setup

- **Equipment:** HDR push camera, 100 ft cable, sonde locator
- **Access point:** Basement main cleanout (4-inch)
- **Footage imaged:** 52 ft of approximately 75 ft total lateral (estimate based on property depth; final 23 ft unverified)
- **Pipe material:** Vitrified clay, original to house (circa 1958)
- **Water condition:** Trickle flow at inlet, standing water (~1/3 pipe depth) from 30–35 ft, clear image otherwise

### Defect table

| Footage | Code | Severity | Plain-language description | Photo ref |
|---|---|---|---|---|
| 12 ft | JOM | Minor | Minor joint offset, both halves of pipe still aligned, no flow restriction | Fig. 12ft |
| 18–28 ft | DS | Moderate | Scaling/encrustation on pipe wall, roughly 15–20% cross-section reduction, consistent with pipe age | Fig. 20ft |
| 32 ft | SAG | Moderate | Sag/belly holding approximately 1/3 pipe of standing water — will trap solids and accelerate scaling | Fig. 32ft |
| 48 ft | RFC | Severe | Root intrusion, roots occupy an estimated 50–60% of cross-section, consistent with clay-joint penetration | Fig. 48ft |
| 52 ft | — | — | Hard stop — cable would not advance. Likely a severe offset, collapse, or obstruction. Final 23 ft to city tap is unverified. | — |

### Line condition by segment

- **0–12 ft:** Serviceable
- **12–28 ft:** Degraded (scaling, minor offset — aging clay but functional)
- **28–52 ft:** Failing (belly + severe root intrusion)
- **52 ft to city tap:** Unknown (camera could not pass)

### Recommendations

**Good — Spot repair at 48 ft + hydro-jet the full line (estimated $2,800–$3,800)**
Open-cut excavation at the 48 ft root-intrusion point, replace a 4–6 ft section with PVC, jet the remainder. Warranty: 1 year on the spot repair, no warranty on the remaining clay. Expected service life of the overall line: 2–5 years before the next significant defect surfaces. **Honest limitation:** the belly at 32 ft, the scaling from 12–28 ft, and the unknown final 23 ft are all untouched by this option.

**Better — Pipe lining (CIPP) from house to 52 ft (estimated $9,500–$12,500)**
Cured-in-place liner installed through the existing clay lateral from the cleanout to just past the root intrusion. Does not resolve the belly at 32 ft (lining cannot correct pipe grade) and cannot pass the hard stop at 52 ft. Warranty: 10 years on the liner. Expected service life: 30–50 years for the lined segment; the unverified final 23 ft remains a risk.

**Best — Trenchless pipe-burst replacement, house to property line (estimated $14,000–$18,500)**
Full replacement of the lateral with new HDPE or PVC from the basement cleanout to the city tap. Resolves the belly, the root intrusion, and the unknown final segment in one operation. Requires a city permit and a brief yard excavation at each end. Warranty: 25 years manufacturer + 10 years workmanship. Expected service life: 75–100 years.

### Next steps and inspection limits

- **This week:** Avoid flushing wipes, feminine products, and grease; the existing root mass at 48 ft can catch solids and trigger a backup with little warning.
- **For the pending sale:** We recommend disclosing both defects (belly at 32 ft; severe root intrusion at 48 ft) to the buyer and providing this report with the disclosure packet. Most buyer-side inspectors will flag these on their own scope; proactive disclosure avoids a surprise in the buyer's inspection response.
- **Inspection limits:** Camera could not pass 52 ft. The final 23 ft (approx.) to the city tap is unverified. We recommend a locator trace and a second camera attempt from the city-side cleanout if the buyer requires full-line verification.
- **Permits:** Trenchless pipe-burst (Best) requires a city plumbing permit and a right-of-way permit for the connection to the city tap. Our office handles both on your behalf.
- **Questions:** Call us at [COMPANY PHONE] to schedule any of the three options. This report and the photo stills are attached.

---

*Report prepared by [COMPANY NAME], [LICENSE #]. Photos referenced in the defect table are attached as separate files.*

---

## v1.1 Additions (2026-04-26)

The v1.0 sections above are unchanged. The four sub-sections below are additive — they extend the skill rather than replace any prior content. Use them in addition to v1.0 when the trigger conditions named in each apply.

### v1.1.A — PACP Code → Homeowner-Readable Severity Translation Table

The v1.0 defect table requires the report to include a plain-language description for every PACP-style code. The v1.1 lookup table below standardizes those translations so two reports out of the same shop, on the same defect, sound consistent — and so the skill produces a defensible, shop-neutral homeowner translation rather than re-inventing language each run.

**Master translation reference (use the Severity 1–5 mapping when the tech provides a numerical grade; otherwise use Minor / Moderate / Severe):**

| PACP code | Defect class | Sev 1 (Minor) — homeowner language | Sev 3 (Moderate) — homeowner language | Sev 5 (Severe / Failing) — homeowner language |
|---|---|---|---|---|
| **OB** | Obstacle / obstruction | "A small object or buildup partially blocks flow but the pipe is still draining." | "A foreign object or sediment buildup is significantly restricting flow; needs removal." | "An object or massive buildup is fully blocking flow; line is currently impassable." |
| **JOM / JOL / JOA** | Joint offset (medial / longitudinal / angular) | "A joint is slightly out of alignment but the pipe is still sealed and flowing." | "A joint has shifted enough to catch debris and may worsen over time." | "A joint has separated; pipe is exposed to the surrounding soil and infiltration / leakage is occurring." |
| **JSV** | Joint separation, void visible | "Small gap at a joint, pipe still aligned." | "Visible gap at the joint with soil starting to enter the line." | "Joint is fully separated; soil and water are flowing freely between pipe and surrounding ground." |
| **SAG** | Sag / belly | "A slight low spot is visible but does not currently hold standing water." | "A belly holds standing water that traps debris and accelerates buildup; expect recurring slow drainage." | "A deep belly holds significant standing water; line will trap solids and back up under normal use." |
| **DS / DSF / DSGV** | Deposits — settled / fine / grease & vegetable | "A thin layer of buildup on the pipe wall; flow not restricted." | "Buildup occupies 15–30% of the pipe; flow restricted under heavy use." | "Buildup occupies more than 50% of the pipe; flow severely restricted, backup risk during heavy use." |
| **RFC / RFB / RFJ** | Roots — fine / barrel / joint | "Fine roots present at a joint; not currently restricting flow." | "Roots are reducing flow capacity by 25–50%; will worsen and trigger backups." | "Roots occupy more than 50% of the pipe cross-section; backup is likely under normal use." |
| **RTB** | Roots — tap-break / heavy ball | "Light root mass at a side connection; flow not restricted." | "Substantial root mass restricting flow at a side connection; needs cutting." | "Heavy root ball blocking flow; immediate clearing needed and pipe likely compromised." |
| **CC** | Crack — circumferential | "Hairline crack visible around the pipe; pipe still structurally sound." | "Crack with separation visible; pipe is leaking but still structurally holding." | "Crack with significant separation; pipe is at high risk of full collapse." |
| **CL** | Crack — longitudinal | "Hairline lengthwise crack; pipe is still sealed." | "Lengthwise crack with visible separation; leakage likely under load." | "Major lengthwise crack with separation; pipe is failing and at risk of collapse." |
| **FC / FL** | Fracture — circumferential / longitudinal | "Visible fracture but pipe edges still touching; structurally compromised but holding." | "Fractured pipe with displacement; soil entry occurring." | "Fully fractured pipe with significant displacement; structural integrity lost." |
| **B** | Broken | "Pipe wall has minor broken pieces visible; flow continuing." | "Pipe wall is broken with visible voids; soil entering the line." | "Pipe wall has collapsed or has missing sections; line is no longer structurally intact." |
| **X** | Collapse | (rarely used at Sev 1; if Sev 1, treat as severe broken) | "Partial collapse; pipe is restricting flow significantly and at risk of full collapse." | "Full collapse; line is impassable and excavation / replacement is required." |
| **H** | Hole | "Small hole in pipe wall; flow continuing, soil entry minor." | "Hole with visible soil entry into the line." | "Large hole or wall failure; significant soil entering the line, structural risk." |
| **I** | Infiltration | "Trace dampness at joint; not currently active." | "Active drip / weep at joint." | "Heavy active flow into the line from the surrounding ground." |
| **TFA / TFB / TFC** | Tap — factory / break-in / capped | "Side-tap connection in good condition." | "Side-tap connection with minor irregularity (offset or slight intrusion)." | "Side-tap connection failing — broken-in tap, displaced, or missing material." |
| **MWL / MWLD** | Mineral / water level | "Small puddle at low point, no flow restriction." | "Standing water consistent with belly or stoppage downstream." | "Significant standing water indicating active stoppage or major belly." |
| **AMH** | Access manhole | (manhole conditions — used in commercial contexts; severity reflects access-point condition) | | |

**How the skill uses the table:** When the tech provides a code + severity, the skill picks the matching row and column for the plain-language description. When the tech provides only a code, the skill picks Sev 3 (Moderate) as the default and explicitly flags this in the report: "Severity not graded by tech — Moderate is shown as the default; PACP-certified verification recommended for insurance / litigation use."

**Why standardize:** The same defect described as "some roots" in one report and "minor root intrusion at 35 ft" in another is the kind of inconsistency that erodes trust during a real-estate transaction or insurance dispute. The v1.1 table holds the language steady across runs and across techs.

### v1.1.B — Year-over-Year Trend Section (Recurring Commercial / HOA / Property Manager Reports)

Property managers, HOAs, and commercial-account customers often run sewer scopes annually or semi-annually under a maintenance program. The v1.1 trend section gives those customers a read on whether the line is stable, slowly degrading, or rapidly degrading — which is the actual question they have, not "what's the condition today?"

**When to add:** Include a "Section 7 — Year-over-Year Trend" only when the customer relationship has at least one prior camera report in the shop's record. Skip the section on any first-time inspection.

**Trend table format:**

| Footage | This inspection | 12 months ago | 24 months ago | 36 months ago | Trend |
|---|---|---|---|---|---|
| 0–12 ft | Serviceable | Serviceable | Serviceable | Serviceable | Stable |
| 12–28 ft | Degraded (DS, 18%) | Degraded (DS, 14%) | Serviceable | Serviceable | Slow degradation |
| 28–52 ft | Failing (SAG + RFC) | Degraded (RFC, 30%) | Degraded (RFC, 18%) | Serviceable | Rapid degradation |
| 52–75 ft | Unknown (hard stop) | Unknown (hard stop) | Serviceable | Serviceable | Unknown — recommend trace |

**Trend classifications:**
- **Stable** — no measurable change across the prior 24+ months.
- **Slow degradation** — incremental change visible (e.g., scaling thickness increasing by ≤15% per year, or one new minor defect added).
- **Rapid degradation** — significant change in 12 months (e.g., a Moderate becoming Severe, a new Severe defect, a hard stop where there wasn't one).
- **Improvement** — the section was previously degraded and has been remediated (e.g., post-jet, post-spot-repair).
- **Unknown** — section is no longer observable due to a new hard stop or image limit.

**Recommendation block addition:** When trend is `Rapid degradation` on any segment, the recommendation in Section 5 should escalate from `Better` to `Best` (full replacement preferred over CIPP) for that segment. When trend is `Slow degradation`, maintain current recommendation tier and re-inspect in 12 months. When trend is `Stable`, recommend the existing maintenance interval be confirmed (annually for commercial / HOA, every 2–3 years for low-volume residential maintenance contracts).

**Property-manager friendly summary line at the end of Section 7:**
> "Across the four-year inspection record, the line is degrading from the back of the building outward. The 28–52 ft section has moved from Serviceable to Failing in 24 months. We recommend prioritizing replacement of that segment in the next maintenance budget cycle, with the 52 ft+ unknown segment scoped via a city-side camera run."

### v1.1.C — Real-Estate Transaction Addendum

Pre-sale and pre-purchase sewer scopes are a distinct workflow — the report is not just for the homeowner; it's for the buyer's agent, the seller's agent, the listing inspector, and increasingly the financing underwriter. The v1.1 addendum below extends the v1.0 customer-audience-calibration section for transaction reports specifically.

**Trigger:** Add this addendum only when `customer context` indicates the report is for a real-estate transaction (pre-sale, pre-purchase, due diligence, listing inspection).

**Addendum sections (insert after Section 5, before Section 6):**

**Transaction-Impact Summary (≤6 sentences):**
- One sentence: bottom-line condition, transaction-relevant only.
- One sentence: estimated cost band of the recommended remedy.
- One sentence: who pays — convention is seller (existing condition pre-listing), but negotiable.
- One sentence: timing impact on closing (does the buyer's lender require completion before close?).
- One sentence: disclosure obligation under state law (e.g., CA Civil Code 1102, NY RPL 462, TX TREC disclosure).
- One sentence: insurability and financing impact (FHA / VA / USDA loans flag certain defects more aggressively than conventional).

**Defect-by-defect transaction relevance (one-row-per-Sev-3+ defect):**

| Footage | Defect | Transaction relevance | Likely buyer-inspector finding |
|---|---|---|---|
| 32 ft | SAG (Moderate) | Disclosure recommended; not typically a deal-breaker | Will likely be flagged; expect a $500–$1,500 credit request |
| 48 ft | RFC (Severe) | Disclosure required in most states; routinely re-negotiated | Will be flagged; expect a $3K–$15K credit or remediation demand |
| 52 ft | Unknown (hard stop) | Should be disclosed; uncertainty creates buyer-inspector risk | Buyer-side may demand a city-side scope as a condition of closing |

**Financing-relevance callout (only if defect set warrants):**

> "FHA and VA buyers: a Severe-rated sewer defect that has not been remediated may require a re-inspection or remediation as a condition of loan approval. Discuss with the lender's underwriter before closing on a financed sale."

**Pre-listing posture recommendation (seller-side reports only):**

> "Pre-listing options: (a) remediate before listing — adds value above remediation cost in most markets; (b) disclose with this report attached and price accordingly — simpler and avoids permit / construction timing risk during listing; (c) offer a credit at closing equal to the recommended remediation — common pattern when seller is not in a position to coordinate the work."

**Defensibility note (always present in transaction reports):**
> "This report describes the condition observed on [date] using [equipment]. It is not a structural-engineering certification and is not intended as the sole basis for a real-estate transaction decision. A second opinion from a PACP-certified operator and / or a licensed structural engineer is appropriate when the report is contested."

### v1.1.D — Regional Pricing-Band Calibration

The v1.0 recommendation block uses dollar bands (Good $2,800–$3,800; Better $9,500–$12,500; Best $14,000–$18,500) calibrated to a mid-Atlantic / Southeast US market. Bands shift materially by region — Pacific Northwest, Bay Area, NYC metro, Boston metro, and Honolulu run 1.4–1.9× the base; Midwest non-metro and Southeast rural run 0.7–0.85× the base. The v1.1 calibration multiplier below standardizes the regional adjustment so the report is credible to a homeowner whose neighbor's quote it will be compared against.

**Regional multiplier table (apply to v1.0 base bands):**

| Region | Multiplier | Rationale |
|---|---|---|
| Bay Area / SF / San Jose / Oakland | 1.6–1.9× | Highest contractor labor rates; permit complexity; restoration cost on hardscape |
| NYC metro / Long Island / Westchester / NJ inner ring | 1.5–1.8× | Highest labor; constrained access; municipal permit overhead |
| Boston metro / Cambridge / Brookline | 1.4–1.6× | Old-stock pipe material variety; permit overhead; restoration in dense neighborhoods |
| LA / Orange County | 1.3–1.5× | Labor + permit overhead; soil / shoring more involved than mid-Atlantic |
| Pacific Northwest metro (Seattle, Portland) | 1.3–1.5× | Labor; restoration on tree-root remediation cycles |
| Honolulu / urban Hawaii | 1.7–1.9× | Material logistics; specialized contractor pool |
| Denver / Phoenix / Austin / Nashville / Charlotte (growing metros) | 1.05–1.20× | Labor inflation outpacing the national mid-Atlantic baseline |
| Mid-Atlantic / Southeast metro (DC, Baltimore, Richmond, Atlanta) | 1.00× | Base bands as written |
| Midwest metro (Chicago, Indy, Columbus, KC, Minneapolis) | 0.90–1.00× | Slightly below base on labor; comparable on materials |
| Florida metro (Miami, Tampa, Orlando, Jacksonville) | 0.95–1.10× | Labor mostly in line; permit overhead by jurisdiction |
| Texas metro non-Austin (Dallas, Houston, San Antonio) | 0.90–1.05× | Lower labor than coastal; comparable materials |
| Midwest non-metro / Southeast rural / Plains / rural Mountain West | 0.70–0.85× | Lower labor; smaller restoration / permit overhead |

**Application rule:** The shop's `config.yml` should set `regional_multiplier` once per service area. The skill applies the multiplier to the v1.0 base bands and produces region-correct dollar ranges in the recommendation block. When the shop's primary service area spans more than one band (e.g., the PNW shop that does Seattle + rural Snohomish County), the report is generated for the property's specific region, not the shop's blended band.

**Output format addition:** Add a one-line annotation at the end of Section 5 in v1.0:
> "Pricing bands calibrated to [region]. For a second opinion in the same market, expect quotes within ±20% of these bands; significantly outside that range is worth discussing with us before signing."

---

**End of v1.1 additions. v1.0 example output above remains the canonical example. The v1.1 sub-sections layer on without modifying any v1.0 instruction or example.**
