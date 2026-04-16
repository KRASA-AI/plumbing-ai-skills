---
name: "Sewer Camera Inspection Report Drafter"
category: operations
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~25 min/inspection"
version: 1.0
last_eval_score: 9.4
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
