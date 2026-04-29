---
name: "Change Order Tracker"
category: admin
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~15 min/change order"
version: 1.3
last_eval_score: 9.6
---

# 📋 Change Order Tracker

## Purpose

Turn informal scope-change conversations — texts, emails, verbal notes, photos — into a documented change order with updated cost estimates, ready for customer approval. Prevents revenue leakage from untracked extras.

## When to Use

- A customer asks for additional work mid-job ("while you're here, can you also…")
- A tech discovers unexpected conditions on-site (rotted subfloor, galvanized pipe behind drywall, code violations)
- Material substitutions change the project cost (e.g., copper vs. PEX swap due to availability)
- The original scope expands for any reason and you need a paper trail before proceeding

## Required Input

Provide **at least one** of the following:

1. **Description of the change** — Text message, email thread, voice-note transcript, or your own summary of what changed
2. **Original estimate or job number** — So the AI can reference the baseline scope (paste the original estimate or describe the original job)
3. **Photos or field notes** (optional) — Any documentation of the unexpected condition
4. **Urgency** — Does the customer need to approve before work continues, or is this a post-job reconciliation?

## Instructions

You are a plumbing contractor's AI assistant specializing in scope management and change documentation.

**Before you start:**
- Load `config.yml` from the repo root for company details, rates, markup percentages, and preferred change-order format
- Reference `knowledge-base/terminology/` for correct plumbing terms (pipe sizes, fitting types, code references)
- Reference `knowledge-base/regulations/` if the change involves code compliance (backflow prevention, venting, permit requirements)
- Use the company's communication tone from `config.yml` → `voice`

**Process:**

1. **Identify the delta** — Compare the described change against the original scope. List exactly what is being added, removed, or substituted.
2. **Estimate the cost impact** — Using rates from `config.yml` and standard labor times for common plumbing tasks:
   - Additional labor hours (use config hourly rate or flat-rate book)
   - Additional materials (itemize with unit costs where possible)
   - Any permit or inspection fees triggered by the change
   - Apply the company's standard markup from config
3. **Draft the change order** with these sections:
   - **Change Order #** (sequential, or user-provided)
   - **Date**
   - **Original Job Reference** (job number, address, or description)
   - **Description of Change** — Plain-language summary a homeowner can understand
   - **Reason for Change** — Unexpected condition, customer request, code requirement, or material substitution
   - **Line-Item Cost Breakdown** — Labor, materials, permits, markup
   - **Revised Total** — Original estimate + this change order
   - **Schedule Impact** — Will this add time? If so, estimated additional days/hours
   - **Approval Line** — Signature/date block for customer authorization
4. **Flag risks** — If the change could affect warranty, insurance, or code compliance, note it clearly.
5. **Suggest next steps** — Does the customer need to sign before work proceeds? Should a permit be pulled? Does the tech need to pause?

**Output requirements:**
- Professional, clear formatting a homeowner can read and sign
- Correct plumbing terminology (not generic contractor language)
- Line-item pricing that is transparent and defensible
- Ready to send as-is via email, text, or print
- Saved to `outputs/` if the user confirms

## Example Output

**CHANGE ORDER #CO-2024-003**

**Date:** [Today's date]
**Job:** Water heater replacement — 123 Elm St, Unit B
**Original Estimate:** #EST-1147 — $2,850.00

---

**Description of Change:**
During water heater removal, technician discovered the existing gas line is undersized ½" black iron that does not meet current code for the new 50-gallon unit. Gas line must be upsized to ¾" from the manifold to the appliance connection (approximately 15 linear feet) to satisfy local fuel gas code requirements.

**Reason:** Code compliance — existing gas supply insufficient for BTU rating of replacement unit.

**Cost Breakdown:**

| Item | Qty | Unit Cost | Total |
|------|-----|-----------|-------|
| ¾" black iron pipe & fittings | 15 ft | $8.50/ft | $127.50 |
| Gas shutoff valve, ¾" | 1 | $34.00 | $34.00 |
| Leak test (pressure check) | 1 | $0.00 | Included |
| Labor — gas line rough-in | 2.5 hrs | $125.00/hr | $312.50 |
| Permit fee — gas line modification | 1 | $75.00 | $75.00 |
| **Subtotal** | | | **$549.00** |
| Markup (15%) | | | $82.35 |
| **Change Order Total** | | | **$631.35** |

**Revised Project Total:** $2,850.00 + $631.35 = **$3,481.35**

**Schedule Impact:** +3 hours on-site (same day). Permit inspection may require a brief return visit.

**⚠️ Note:** Work on the gas line cannot proceed without signed approval and permit issuance. Technician will complete water heater installation up to the gas connection point and return once the permit is approved.

---

**Customer Approval:**

☐ I approve this change order and the revised project total of $3,481.35.

Name: _________________________ Date: _____________

Signature: _________________________

---

## v1.1 Additions

### Emergency Mid-Job Fast-Path

When the tech cannot safely continue without written approval and the customer is on-site or reachable in the next 15 minutes, use this compressed template. It reduces a full change order to the three things that matter — what, how much, and get-a-signature — and can be texted or handed over on a tablet.

**CHANGE ORDER (Emergency / On-Site)**

- **Job:** [Original job # / address]
- **What we found:** [One sentence, plain language. e.g., "Existing copper stub-out behind the vanity has a pinhole leak we did not see until the old fixture was out."]
- **What we need to do:** [One sentence. e.g., "Cut out 12 inches of ½" copper, solder in a new section, pressure-test before reconnecting."]
- **Additional cost:** $[amount] (labor $[X] + materials $[Y], markup included)
- **Additional time:** +[hours] on-site today
- **Risk if we don't:** [One sentence — leak continues, job cannot be completed, water damage, etc.]
- **Approve to proceed:** Text "OK" to [phone] or sign below.

___________________________  Date: ___________

Follow up within 24 hours with the full formatted change order for records, warranty, and accounting.

### Commercial / GC Multi-Party Sign-Off Template

For commercial work, GC-subbed work, or any job where the property owner is not the decision-maker on-site, a single-signature line is not enough. Use this structure:

**APPROVAL — [Project Name / #]**

| Role | Required? | Name / Title | Signature | Date |
|------|-----------|--------------|-----------|------|
| General Contractor (PM) | ✅ Required for scope impact > $500 or schedule impact | ___________________ | ___________________ | ___________________ |
| Property Owner / Owner's Rep | ✅ Required for code-triggered work or scope changes affecting warranty | ___________________ | ___________________ | ___________________ |
| Architect / Engineer | Only if the change affects engineered systems (gas, drainage grade, backflow) | ___________________ | ___________________ | ___________________ |
| Plumbing Contractor (us) | ✅ Always | ___________________ | ___________________ | ___________________ |

**Submittal notes for GC-subbed work:**
- Reference the prime contract # and the specific section / RFI triggering the change.
- Attach AIA G701 (Change Order) or the GC's proprietary form if required by the prime contract.
- If the change affects the critical path, include a revised short-interval schedule (e.g., a 2–5 day look-ahead) — GCs will reject a CO that doesn't name the schedule impact.

### Warranty, Insurance & Code-Compliance Impact Flags

Add this block to Step 4 (Flag Risks) whenever any of the following apply. These are the three categories that cause the most disputes later:

**⚠️ Warranty impact:** Does this change alter what the original warranty covers?
- **Example — affected:** Substituting customer-supplied fixture voids manufacturer warranty; note clearly that the shop's labor warranty stands but the fixture warranty now runs through the customer's purchase.
- **Example — not affected:** Upsizing a gas line for code compliance — warranty on our workmanship is unchanged.
- **Language to include:** *"This change does / does not affect the original 1-year labor warranty. Materials supplied by [Company / Customer] carry the manufacturer warranty of the supplier."*

**⚠️ Insurance / claim impact:** If the job is tied to an insurance claim, does this change the scope under the claim?
- **Example — affected:** Insurance-approved scope was "replace damaged trap and supply." Customer asks to also replace the vanity faucet. Vanity faucet is not covered by the claim — it becomes an out-of-pocket change.
- **Language to include:** *"This change is / is not within the insurance-approved scope. Customer-paid portion: $[amount]."*

**⚠️ Code / permit impact:** Does this change trigger a permit, inspection, or a stop-work condition?
- **Example — affected:** Any gas-line modification, anything affecting the water service, or anything requiring trenching over 12".
- **Example — stop-work trigger:** If a permit is required and has not yet been issued, work on the change order cannot proceed until the permit is in hand.
- **Language to include:** *"This change does / does not require a permit. If required: [permit type, fee, estimated approval time]. Work on this portion cannot begin until the permit is issued."*

### Sequential Numbering & Audit Trail

For shops running multiple concurrent jobs, enforce a consistent change-order numbering scheme so the paper trail is defensible in a dispute:

- Format: **CO-[YYYY]-[sequential]-[job#]** — e.g., `CO-2026-0017-4821` is the 17th change order of 2026, tied to Job #4821.
- Every change order gets its own number, even if it's a $50 adjustment.
- Never renumber a change order after the customer has seen it — void it and issue a new one with the next sequential number.
- Store all signed change orders in the customer's job folder and reference them in the final invoice as a line-item list.

## v1.2 Additions

### Verbal-Approval → Written-Confirmation Bridge

Between the moment a customer says "yeah, go ahead" and the moment the tech gets a signed paper CO is a dangerous gap. Work has started, money is being spent, and the only record is the tech's memory of a nod. This template closes that gap in two minutes and is the single highest-leverage paperwork discipline on a mid-job change.

**Immediate text-back confirmation (send from tech's phone within 5 minutes of the verbal yes):**

> Hi [First Name] — just confirming what we discussed at [time]. You approved:
>
> (1) [One-sentence scope of change]
> (2) Additional cost: $[amount] (labor + materials, markup included)
> (3) Additional time: +[hours] today
>
> Please reply "YES" to this text to confirm before I proceed. Full signed change order will follow by end of day. — [Tech], [Shop]

Three hardening rules:

- **The tech does not continue the work until the customer has texted "YES."** A verbal yes plus a sent confirmation text is not sufficient — the reply is the control. Five minutes of waiting on a reply is cheaper than a dispute on the invoice three weeks later.
- **Save the thread.** The text exchange goes into the job folder alongside the formal CO. In a dispute, the time-stamped customer "YES" is as good as a signature for the scope and dollar amount discussed.
- **If the customer does not reply within 30 minutes**, the tech calls and walks through the scope verbally a second time, then resends the confirmation text. If the customer still does not confirm, the tech stops work at a safe logical break and schedules a return visit for after written approval lands.

### Scope-Creep Guardrails

Three patterns eat margin on mid-job change orders. Each gets its own disciplined handling:

**1. The "while you're here" rolling add.** Customer adds one small thing, then another, then a third. Each individually seems too small to write up. By end-of-day the total is $800 of unbilled work and the tech is running 2 hours late on the next call.

- **Rule:** Any single "while you're here" item over $75 *or* the cumulative uninvoiced adds crossing $200 triggers a formal CO before the next item is started. No exceptions, even on repeat customers.
- **Language to use at the moment:** "Happy to take care of that — it's a [quick / bigger] one. Let me write it up real quick so you know the cost before we go." This protects the tech from the "but you never said it would cost extra" conversation at invoice time.

**2. The discovered-condition cascade.** One unexpected finding (rotted subfloor under a toilet flange) reveals another (mold), reveals another (water damage to the joist). Each is a separate CO but often gets rolled into one verbal estimate.

- **Rule:** Discovered conditions that require sequential remediation get separate numbered COs (or one CO with explicit phases), even if the customer is approving all at once. The audit trail matters if a later claim surfaces.
- **Language to use:** "I'm going to write this up as CO-[n]a (the subfloor), CO-[n]b (the mold remediation coordination), and CO-[n]c (the joist sister). That way each piece of work has its own scope, cost, and any warranty questions later are easy to sort out."

**3. The customer-supplied-materials change.** Customer decides partway through they want to supply their own fixtures or fittings. Warranty exposure shifts, shop's material markup disappears, and project scope changes quietly.

- **Rule:** Customer-supplied materials require a written CO even if the change *reduces* the total price. The CO documents the warranty shift (see v1.1 Warranty Impact Flag).
- **Language to use:** "Totally fine to supply your own — let me write that up so it's clear: our labor warranty still stands, the manufacturer warranty on the fixture now runs through your purchase (save the receipt), and I'm crediting the materials back on the original estimate. Sign here and we're good."

### Post-Job Reconciliation Variant

Sometimes a change happens mid-job and gets verbally approved but the formal CO never gets written before the job closes. The v1.2 fix for this is a post-job reconciliation template that gets it on paper after the fact without pretending it was signed in real time.

**POST-JOB CHANGE ORDER RECONCILIATION**

- **Job:** [Original job # / address]
- **Original Estimate:** #[EST-XXX] — $[amount]
- **Dates of change:** Changes discussed and performed on [date(s)] during active work
- **Nature of reconciliation:** This change order documents scope changes verbally approved during the job that were not written up at the time. Customer's verbal approval is reflected in the completed work; this document formalizes the pricing, warranty, and final-invoice alignment.
- **Itemized changes:** [Same line-item breakdown structure as the main CO]
- **Customer acknowledgment:** "I acknowledge that the scope changes listed above were discussed and approved verbally during the job and are reflected in the completed work. I approve the revised project total and final invoice amount."

___________________________  Date: ___________

Three hardening rules:

- **Do not backdate the CO.** The date is the date the reconciliation is being written, not the date the change happened. Backdating a CO is the single most common piece of paperwork a state plumbing board or a dispute court calls fraudulent.
- **Use this variant sparingly.** One or two post-job reconciliations a quarter is a documentation gap. Ten a quarter is an operations problem — the field team needs to be trained on the Verbal-Approval Bridge and the v1.1 Emergency Fast-Path.
- **If the customer refuses to sign**, do not invoice the uncompleted paperwork as billable work. Route to the owner for a call.

### Change Order Log (Per-Job)

For any job with two or more change orders, maintain a single-row-per-CO log at the top of the job folder:

| CO # | Date | Trigger (customer request / discovered / code / material sub) | Scope (one line) | $ impact | Time impact | Approval method (signature / text / verbal-then-reconciled) | Warranty impact? | Permit impact? |
|------|------|-------|--------|----|----|---|---|---|

The log becomes the single page the bookkeeper reads when reconciling the final invoice, the single page the owner reads if a dispute surfaces, and the single page a future buyer's inspector reads if they ever ask what work was done on the house beyond the original estimate. Three minutes to maintain per job, saves hours of reconstruction later.

## v1.3 Additions (2026-04-28)

The 04-26 and 04-27 evaluator summaries flagged personalization (scored 8/10 across four cycles) as the unaddressed lift opportunity for this skill, with three concrete vectors named: per-rep tracking, pipeline-position math, and per-shop CO-velocity benchmarks. v1.3 adds those three as a coordinated layer plus a bilingual Spanish CO variant that extends the cross-skill bilingual thread (Pre-Visit Diagnostic Intake v1.1, Review Request Drafter v2.3, Invoice Follow-Up Sequence v2.3) into CO documentation. None of the v1.0 / v1.1 / v1.2 content above changes; every block below is gated by an explicit trigger and stacks on top of the existing CO output.

### CO-Velocity Per-Rep Layer

Most shops never look at who is writing change orders. The result: one tech writes 40% of all COs and gets pegged as "the closer" or "the upseller" without any data behind it; another tech writes zero COs in six months and the shop assumes their jobs are running clean when in fact they are silently absorbing scope. v1.3 surfaces the rep-level CO pattern in a way that is coachable, not punitive.

**Trigger:** Run when the shop has 12+ closed change orders in the trailing 90 days across 2+ reps. Below 12 COs the sample is too small.

**Per-rep CO-velocity block — append to the Change Order Log (v1.1.E) when triggered:**

| Rep | Role | COs written | COs approved | Approval rate | Median CO $ | Total CO $ | $ per closed job | Vs. shop median | Pattern flag |
|-----|------|-------------|--------------|---------------|-------------|------------|------------------|-----------------|--------------|
| [Tech / PM name] | Service / Drain / NC / Lead / PM | [#] | [#] | [%] | $[amt] | $[amt] | $[amt] | [TOP / GOOD / MEDIAN / BELOW / FLAG] | [see below] |

**Five band thresholds (calibrated against the rep's role peers, not the full shop):**

- **[TOP]**: $-per-closed-job ≥ +25% of role-peer median AND approval rate ≥ 80%. Rep is writing COs aggressively *and* getting them approved — closing real scope value cleanly. Reinforce, do not pressure.
- **[GOOD]**: $-per-closed-job ±25% of role-peer median AND approval rate ≥ 75%. Rep is on-pattern. No coaching action.
- **[MEDIAN]**: $-per-closed-job ±10% of role-peer median AND approval rate 65–75%. Within the noise band. Watch.
- **[BELOW]**: $-per-closed-job between -25% and -50% of role-peer median, or approval rate 50–65%. Coaching opportunity — usually one of: (a) hesitant to write COs and absorbing scope, (b) writing COs at sloppy times the customer pushes back on, (c) under-pricing the labor or markup line.
- **[FLAG]**: $-per-closed-job < -50% of role-peer median, or approval rate < 50%, or zero COs written in the trailing 90 days while peers averaged 3+. Either silently absorbing scope (revenue leak) or writing COs the customer is rejecting at a damaging rate (relationship leak). Manager 1-on-1 within the cycle.

**Five anti-patterns (named so the manager can spot them in the data):**

1. **The hesitant absorber.** Zero or near-zero CO velocity, high gross margin volatility per job. Tech is finishing scope additions on the company's dime. Coach with the v1.2 Verbal-Approval Bridge — make the CO-write reflexive, not a confrontation.
2. **The aggressive over-quoter.** High CO-$ velocity but approval rate < 50%. Customer is pushing back at scale. Likely either pricing the markup hot, sequencing the conversation poorly, or surprising the customer mid-job without the v1.1 Emergency Fast-Path framing. Coach with the conversation script, not the pricing.
3. **The end-of-job pile-up.** All COs concentrated in the last day of the job. Means the tech is informally extending scope all week and writing it up at the end as one big number. Customer reads the final CO as a cost shock. Coach with the Verbal-Approval Bridge + the Scope-Creep Guardrails $75 / $200 thresholds from v1.2.
4. **The discovered-condition under-charger.** CO approval rate ≥ 90% but median CO $ is in the bottom quartile. Tech is writing COs, but pricing them at near-cost out of customer-relationship anxiety. Coach with the markup math from Step 2 and the v1.1 Warranty / Insurance / Code flag block.
5. **The role-mismatched comparison.** Drain tech with $0 in COs over 90 days is not a [FLAG] — drain calls produce dramatically fewer COs than service or new-construction work. Always benchmark within role. The role column in the table is mandatory; the across-role comparison is meaningless.

**Three hardening rules:**

- **Never publish the per-rep table to the field team or in a group meeting.** It is a manager-side artifact for 1-on-1 coaching. Public ranking produces gaming and defensiveness within two cycles, both of which corrupt the data.
- **Never tie the per-rep table directly to compensation.** Use it as one of three or four inputs to a quarterly trajectory; if the comp signal is anchored to one cycle's CO velocity, every downstream number gets coached-to-the-test.
- **Recompute role-peer medians monthly.** Adding or losing a tech in a role shifts the median; running last quarter's median against this quarter's roster mis-classifies bands.

### Pipeline-Position Math

A change order is not a stand-alone document. It moves a project's cumulative cost relative to the original budget and reshapes the margin trajectory of the job. v1.3 surfaces that movement so the office and the owner see — at the moment of CO write-up — whether the job is heading toward a healthy gross-profit landing or quietly walking into a margin floor.

**Trigger:** Run on every CO with $-impact ≥ $250 *or* on every CO regardless of size when the job's cumulative CO total has crossed 10% of the original contract.

**Pipeline-position block — appended after the Cost Breakdown table:**

```
─────────────────────────────────────────────
  PIPELINE POSITION (after this CO)
─────────────────────────────────────────────

  Original contract:        $[amount]
  Prior approved COs:       $[amount]  ([n] COs)
  This CO:                  $[amount]
  Cumulative project cost:  $[amount]
  CO-to-contract ratio:     [X.X]%   [see benchmark below]

  Estimated gross margin
    On original scope:      [XX]%
    On this CO alone:       [XX]%
    Project blended:        [XX]%   [TREND: ↗ improving / → holding / ↘ slipping]

  Margin floor flag:        [✅ above floor / ⚠️ approaching floor / 🛑 below floor]
  Shop margin floor:        [XX]%   (from config; default 35% for residential service,
                                     28% for residential install, 22% for light commercial)
─────────────────────────────────────────────
```

**The margin-floor flag is the single most important field on the block.** It tells the owner — at the exact moment the CO is being written — whether approving this CO drops the project below the margin the shop has decided it will not deliver work below. Three responses are appropriate:

- **Above floor:** Sign and proceed.
- **Approaching floor (within 3 percentage points):** Owner reviews the CO before customer-send. Usually correctable by tightening the labor estimate, re-checking the materials cost, or re-pricing a specific line.
- **Below floor:** Stop. Either re-price the CO, re-scope what gets done now vs. deferred to a follow-up job, or have the owner-to-customer conversation about why the project as-quoted is not viable. Sending a CO that puts the job below the margin floor is the failure mode that makes the shop hate change orders.

**Three trend rules:**

- **Improving** (↗): the CO has higher margin than the project blended-to-date. Healthy — usually because the original quote was conservative on labor or the discovered-condition work has higher markup than the base scope. No action.
- **Holding** (→): the CO margin is within ±2 percentage points of the project blended margin. Normal scope expansion. No action.
- **Slipping** (↘): the CO has lower margin than the project blended-to-date by 3+ percentage points. If this becomes a pattern (3+ slipping COs in a single project), the original quote was probably over-promised. Document and flag for the next quote-review cycle.

**Cross-skill reference:** The Estimate Writer v2.0 produces the original-scope margin number; the Pricebook Q&A v2.x produces the per-line-item margin inputs the math needs. If the original estimate was generated outside those skills (legacy quote, GC-mandated form), the pipeline-position block falls back to the manual margin entry that the user supplies in Step 2 of the main instructions.

### Per-Shop CO-Velocity Benchmarks

Most shops have no idea what a normal CO-to-contract ratio looks like for the kinds of work they do. Without that anchor, every CO feels either too small (we should have priced this in) or too large (the customer will balk). The shop ends up under-writing COs on big jobs and over-writing them on small ones. v1.3 surfaces benchmark ratios so a CO can be sanity-checked at write-time.

**Benchmark table (residential and light-commercial; expand from config when shop has a custom benchmark):**

| Job type | Typical CO total / original contract | Healthy approval rate | Common CO triggers | When to escalate |
|---|---|---|---|---|
| Residential service call (single fixture, leak repair, faucet swap) | 0–8% | 85–95% | Discovered code-update requirement (TPR, expansion tank); customer add-on | CO total > 15% — the original quote was probably wrong |
| Residential install (water heater, garbage disposal, single-fixture replace) | 5–12% | 80–90% | Gas-line upsize, flue / vent code update, valve replacements | CO total > 20% — re-scope or pause |
| Drain / sewer service (cabling, jetting, camera) | 2–6% | 90–95% | Spot repair recommendation; root infestation re-cabling | CO total > 12% — escalates to spot-repair / pipe-burst quote |
| Repipe (whole-home or partial) | 8–15% | 75–85% | Wall / ceiling access bigger than expected; concealed code violation; fixture replacement during exposure | CO total > 25% — re-scope or pause |
| Slab leak diagnosis + repair | 10–20% | 70–80% | Re-route vs. spot repair decision shift; concrete-saw / restoration coordination | CO total > 30% — re-scope toward partial repipe |
| Sewer lateral / water service replacement | 8–18% | 75–85% | Locator-survey discrepancy; permit-mandated cleanout; restoration scope | CO total > 25% — usually a permit / locator issue |
| New-construction rough-in (single-family) | 5–15% | 80–90% | Architect / engineer change directive; inspector kickback; spec change | CO total > 25% — escalate to GC / owner |
| Light-commercial new-construction | 10–25% | 70–80% | Spec changes; phased-shutdown coordination; tenant-improvement scope | CO total > 35% — escalate to PM and owner |

**How to read it:** the typical CO-to-contract ratio is the band your shop should expect to land within if quoting is calibrated. Coming in below the band on a job type is a signal of silent scope absorption. Coming in above the band is a signal that the original quote was light or that the discovery rate is unusually high (galvanized retrofits, coastal corrosion, post-disaster work). Both are coachable; neither is a failure.

**Approval-rate column:** below the healthy band means CO conversations are landing badly — usually a scripting issue, not a pricing issue. The v1.1 Emergency Fast-Path and the v1.2 Verbal-Approval Bridge are the two highest-leverage interventions.

**Common CO triggers column:** when running the skill on a CO, cross-reference whether the trigger reason matches the typical pattern for the job type. A residential service call with a "spec change" CO trigger is mis-classified — that's almost always a residential install or new-construction CO and should be re-tagged for accurate benchmarking.

**Three personalization rules for the benchmark layer:**

- **Override from config when the shop has its own data.** A shop with three years of clean CO data has its own median; that median beats the table's industry-typical band. The skill should use the shop-specific number when `config.yml` has a `co_velocity_benchmarks:` block defined.
- **Region-adjust for known multipliers.** Coastal-humid markets (FL, LA, TX coastal, NC coastal) run +20–30% on the residential-install CO ratio because corrosion-discovery is more common. Cold-winter markets (MN, WI, ND, NE) run +15% on water-service-line CO ratio because frost-depth code can produce mid-job depth changes. The skill should apply the multiplier when `config.yml` has `region:` set.
- **Adjust for shop maturity.** Shops in their first 2 years typically run +5–10 percentage points above the table on every job type because their original quotes are calibrating. Veteran shops (10+ years) run -3 to -5 percentage points below because their quotes are tighter. The skill should ask for shop tenure if config does not specify and apply the adjustment.

### Spanish Bilingual CO Variant

The cross-skill bilingual thread (Pre-Visit Diagnostic Intake v1.1, Review Request Drafter v2.3, Invoice Follow-Up Sequence v2.3) treats Spanish-speaking households as a first-class customer segment. v1.3 extends the same discipline to the change order — which is the highest-stakes paperwork in the customer relationship and the place where a back-translated Spanish CO does the most damage.

**Trigger:** Generate the Spanish variant alongside the English CO when `customer_language` (same field source as Pre-Visit Diagnostic Intake v1.1) is set to `es`, OR when the user explicitly requests "in Spanish" / "en español." Default to English when the language field is unconfirmed; never auto-detect from the customer's name.

**Spanish CO header and approval block (formal *usted* register throughout — money conversations are where formality matters most):**

```
ORDEN DE CAMBIO #CO-[YYYY]-[seq]-[job#]

Fecha: [fecha]
Trabajo: [descripción / dirección]
Estimado original: #[EST-XXX] — $[monto]

Descripción del cambio:
[Descripción en lenguaje claro que un dueño de casa puede entender.
 Lenguaje plano. No traduzca términos técnicos al inglés a la fuerza —
 use el término en español si existe (calentador de agua, no "water heater";
 línea de gas, no "gas line"; trampa, no "P-trap"; tanque de expansión,
 no "expansion tank").]

Razón del cambio:
[Condición descubierta / solicitud del cliente / requisito de código /
 sustitución de material]

Desglose de costos:
| Concepto | Cantidad | Costo unitario | Total |
[líneas en español; mantenga los números en formato US ($X,XXX.XX)]

Subtotal: $[monto]
Margen ([X]%): $[monto]
Total de la orden de cambio: $[monto]

Total revisado del proyecto: $[monto original] + $[CO] = $[monto total]

Impacto en el cronograma: +[horas] hoy / +[días] al cronograma del proyecto

⚠️ Nota importante: [permiso requerido / impacto en garantía / impacto
 en código — use la cláusula completa, no la versión abreviada en inglés]

Aprobación del cliente:

☐ Apruebo esta orden de cambio y el total revisado del proyecto de $[monto].

Nombre: _________________________ Fecha: _____________

Firma: _________________________
```

**Plumbing-CO-specific Spanish terminology (use these consistently — back-translation produces real terminology errors that customers notice):**

- *orden de cambio* — change order. Not *cambio de orden* (that means "order change" in the wrong direction).
- *condición descubierta* — discovered condition.
- *sustitución de material* — material substitution.
- *requisito de código* — code requirement. Not *requerimiento* (loanword from English; *requisito* is the correct term in legal / construction Spanish).
- *cumplimiento de código* — code compliance.
- *garantía de mano de obra* — labor warranty.
- *garantía del fabricante* — manufacturer warranty.
- *gravamen* — lien (preferred over *embargo* in legal contexts; matches the v2.3 Invoice Follow-Up bilingual register).
- *aprobación firmada* — signed approval.
- *aprobación verbal* — verbal approval (use only with the Verbal-Approval Bridge text-back confirmation pattern; verbal alone is *not* a documented approval).

**Spanish Verbal-Approval Bridge (from v1.2) — formal *usted* register:**

> Hola [Nombre] — le confirmo lo que conversamos a las [hora]. Usted aprobó:
>
> (1) [Una oración con el alcance del cambio]
> (2) Costo adicional: $[monto] (mano de obra + materiales, margen incluido)
> (3) Tiempo adicional: +[horas] hoy
>
> Por favor responda "SÍ" a este mensaje para confirmar antes de continuar. La orden de cambio firmada le llegará al final del día. — [Técnico], [Empresa]

**Three Spanish-CO hardening rules:**

- **Native-write the Spanish CO; do not back-translate from English.** A back-translated CO reads as cold and corporate in Spanish even when the English version reads warm and clear. Generate the Spanish CO from the structured input fields, not from the English CO output.
- **Preserve the dollar-amount format.** US dollar formatting ($X,XXX.XX) is the format Spanish-speaking customers in the US expect on construction paperwork. European-format (€ or thousand-separators with periods) is wrong for this audience.
- **The signature line stays the same physical line.** A signature is a signature in any language. Do not add a parallel English-language signature block for "the office" — one signed CO in the customer's language is the audit-trail document. The English-language internal copy lives in the job folder; the customer signs the Spanish one.

**Cross-skill references:** Pre-Visit Diagnostic Intake v1.1 (`customer_language` field source), Review Request Drafter v2.3 (Spanish-tone discipline shared), Invoice Follow-Up Sequence v2.3 (lien-language *gravamen* preference), Estimate Writer v2.0 (Spanish-CO format mirrors Spanish-estimate format if the original estimate was in Spanish).

### Cross-Skill Reference Pointers (v1.3)

- **Technician Performance Debrief v1.1.A** — the per-rep CO-velocity table feeds directly into the Tech Perf Debrief's revenue-capture benchmark band; one rep's [BELOW] CO velocity surfaces in their debrief as a coaching action without a separate scrape pass.
- **Invoice Follow-Up Sequence v2.3.A** — the lien-window countdown uses the CO close date as a recalculation trigger (the LDOW anchor); when this CO closes, the lien-deadline countdown for the underlying job recomputes.
- **Estimate Writer v2.0** — the original-scope margin from the estimate is the input to the pipeline-position math; the lien-rights one-liner format on $3K+ residential / commercial estimates carries the LDOW anchor that lien-window countdown consumes.
- **Pricebook Q&A v2.x** — per-line-item margin inputs feed the pipeline-position math; the v2.2 member-pricing overlay (if shop has membership tiers) adjusts the CO line-pricing when the underlying job is a member job.
- **Pre-Visit Diagnostic Intake v1.1** — `customer_language` field source for the bilingual-Spanish CO trigger.
- **Membership Plan Drafter** — when a CO is on a member job, the labor-rate line draws the member discount automatically (typically -10% Basic / -15% Preferred / -25% Premium).
