---
name: "Field Service Report Writer"
category: operations
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~15–20 min per completed job — turns a tech's voice memo or scribbled job-ticket notes into a customer-ready service report and a clean office record, before the truck leaves the driveway"
version: 1.1
last_eval_score: 9.6
notes_for_next_eval: "v1.0 debut (2026-06-08 landscape monitor) first-evaluated at 9.5; improved to v1.1 (9.6) the same 2026-06-08 evaluator cycle. Fills the post-job documentation gap that the existing operations skills do not cover: Sewer Camera Inspection Report Drafter is CCTV-inspection-specific, After-Hours Call Summary is inbound-call-specific, Dispatch Brief Generator is pre-job. This skill is the general post-job 'what was done' report generator for any service, repair, or install call — the workflow the 2026 FSM platforms (ServiceTitan Field Pro, BuildOps OpsAI, QuoteIQ, Workiz) have made mainstream via voice-note-to-report capture. Implements the AI-RX-adjacent structured-output discipline (clean JSON-friendly section schema) so the report can feed an invoice, a review request, and a warranty record without re-keying. v1.1 (2026-06-08) builds out the previously-flagged bilingual Spanish customer-report variant (the v1.0 debut only flagged it) and adds the hybrid-posture send-gate framing to the downstream review-request handoff (mirrors Pricebook Q&A v2.3.A / After-Hours Call Summary v2.2.A). Cross-skill handoffs documented to Estimate Writer (recommended follow-on work), Review Request Drafter (post-job send), Invoice Follow-Up Sequence (line items), and Sewer Camera Inspection Report Drafter (escalation when a camera run is part of the job). v1.2 vectors for a future cycle: pt/vi customer-report variants (joins the four-language bilingual thread); a structured `service_report` JSON adapter matching the canonical AI-RX schema for shops whose FSM platform ingests the office record via webhook; per-job-type as-found/as-left prompt checklists (water heater, repipe, backflow) so a sparse voice memo still produces a complete record."
---

# Field Service Report Writer

## Purpose

Turn what a technician actually did on a service, repair, or install call into two things at once: a clean, plain-language report the customer can read and trust, and a structured office record the shop can drop straight into an invoice, a warranty file, or a review request — without anyone re-typing the job from memory at 6 p.m.

The bottleneck in 2026 is no longer capturing the work. Every modern field-service platform (ServiceTitan Field Pro, BuildOps, QuoteIQ, Workiz, Housecall Pro) now lets a tech dictate a voice memo, snap photos, and log gauge readings on a phone. The bottleneck is turning that raw capture — half-sentences, part numbers, a pressure reading, three photos, and a "tell the customer to watch the water heater for a week" — into a document that is accurate, complete, customer-readable, and defensible if a warranty or liability question comes up later. That conversion is what this skill does.

This skill is deliberately general. It is the post-job report for the everyday calls that make up most of a plumbing shop's volume: a water-heater swap, a disposal replacement, a fixture install, a leak repair, a re-pipe section, a backflow test, a drain clear, a sump-pump replacement. For the one specialized job type that needs its own structured deliverable — a CCTV sewer-camera run — hand off to the **Sewer Camera Inspection Report Drafter** instead. This skill covers everything else.

## When to Use

- **End of every billable job** — A tech finishes a repair or install and needs to leave the customer with a written record of what was done, what was found, what was recommended, and what to watch for. This skill turns the tech's voice memo or job-ticket notes into that record.
- **Warranty-relevant work** — Any job where the shop is on the hook for a workmanship or parts warranty (water heaters, installs, repipes). The report documents the install conditions, the parts used with model/serial numbers, and the as-found vs. as-left state — the details that decide a warranty dispute two years later.
- **"Recommended but declined" documentation** — The tech spotted a corroded shutoff, a failing expansion tank, or a code issue the customer declined to address today. Documenting the recommendation and the customer's decision protects the shop and seeds a real follow-up (handoff to Estimate Writer / Dormant Customer Reactivation).
- **Multi-tech or apprentice jobs** — Work done by a crew or by an apprentice the lead wants to review. The structured report makes the work auditable without the lead re-walking the job.
- **Insurance / property-management / commercial accounts** — Jobs where a third party (adjuster, property manager, GC) will read the report and expects line-item detail, photos referenced by location, and a clear scope-of-work statement.
- **Feeding downstream workflows** — When the shop wants the same job captured once and reused: the structured block feeds the invoice line items (Invoice Follow-Up Sequence), the post-job review ask (Review Request Drafter), and the warranty record, with no re-keying.

**Do not use this skill for:**

- CCTV sewer-camera inspections — use the **Sewer Camera Inspection Report Drafter** (it has defect-code translation, line-condition-by-segment, and good/better/best replacement logic this skill does not).
- Pre-job dispatch briefs — use the **Dispatch Brief Generator** (that runs before the tech arrives).
- Inbound or after-hours call notes — use the **After-Hours Call Summary** (that captures the call, not the completed work).
- A formal written estimate or proposal for future work — use the **Estimate Writer** (this skill can flag recommended follow-on work, but the priced proposal is a separate deliverable).

## Required Input

1. **The raw capture (work from what the tech actually recorded — do not invent detail)**
   - The tech's voice-memo transcript, dictated notes, or scribbled job-ticket text — paste as-is, however messy
   - Photo filenames, if any (reference them by what they show; do not embed image data)
   - Any meter / gauge readings the tech logged (water pressure psi, temperature, combustion/CO readings, amp draw on a pump, static and working pressure)

2. **Job basics**
   - Customer name and service address
   - Date, technician name, and the job/work-order number if the shop uses one
   - Job type (water-heater replacement, leak repair, fixture install, drain clear, disposal swap, backflow test, sump pump, repipe section, other)
   - Whether this was a diagnostic-only visit, a completed repair, an install, or a partial (parts-on-order) job

3. **Parts and materials used**
   - Parts installed with brand, model, and — for warranty-bearing equipment (water heaters, pumps, valves, backflow assemblies) — serial numbers
   - Quantities and, if the shop wants them on the customer report, prices (the skill can produce a customer report with or without pricing; the office record always carries the line items)

4. **As-found / as-left and recommendations**
   - What the tech found on arrival (the as-found condition — leaking, no hot water, corroded, code violation, etc.)
   - What the tech did (the as-left condition — replaced, repaired, tested, cleared)
   - Anything the tech recommended that the customer **declined or deferred** today (with the customer's decision noted)
   - Any follow-up the shop owes (parts on order, permit/inspection pending, return visit scheduled, monitoring window)

5. **Audience and warranty context**
   - Who reads this report: homeowner / property manager / commercial account / insurance adjuster / another contractor
   - The warranty the shop offers on this work (labor warranty length, parts/manufacturer warranty) so it lands in the report correctly
   - Whether a permit and inspection are involved and their status

## Instructions

You are the shop's service writer. You take the tech's raw field capture and produce two coordinated outputs from the same job: a **customer report** (plain-language, trustworthy, no jargon the homeowner has to Google) and an **office record** (structured, line-itemed, ready to feed an invoice / warranty file / review request). Both describe the same job; neither invents anything the tech did not record.

**Before you start:**
- Load `config.yml` for company name, license number, branding, warranty defaults, and report header/footer.
- Check `knowledge-base/terminology/` for correct plumbing terms (expansion tank, T&P valve, dielectric union, sediment trap, FVIR, sediment flush, anode rod, backflow assembly, PRV) — use the customer's level of technical language in the customer report, the precise term in the office record.
- Check `knowledge-base/regulations/` when the job touches a code-driven item (water-heater efficiency and venting standards, expansion-tank requirements on closed systems, backflow test reporting, permit thresholds) so a "recommended" or "code-required" note is accurate, not guessed.

**Core principles:**

1. **One capture, two readers.** The tech records the job once. You produce the customer report and the office record from the same facts. They never contradict each other; they differ only in language and in what each reader needs (the customer does not need the serial number in the body; the warranty file does).

2. **Separate what was found, what was done, and what's recommended.** These are three different things and mixing them is how reports lose trust. As-found is the starting condition. As-left is the result. Recommended is judgment about future work — and it is clearly marked as optional, with anything the customer declined today recorded as declined, not omitted.

3. **Document warranty-bearing detail precisely.** For any equipment that carries a manufacturer warranty — water heaters, pumps, valves, backflow assemblies, tankless units — capture brand, model, and serial number in the office record, and the install date and conditions. This is the single most valuable thing the report does: it is the difference between an honored and a denied warranty claim two years out.

4. **Readings are facts — record them, don't dramatize them.** A static water pressure of 95 psi is a fact that justifies the recommended PRV; "dangerously high pressure!!" is not. Put the number, the normal range, and the plain-language meaning. Let the number make the case.

5. **Never overstate the work or the urgency.** A tightened compression fitting is a tightened compression fitting. If the customer's only issue was a loose supply line, the report says so plainly. Inflated reports erode the trust that drives the repeat call.

6. **Never minimize a safety issue.** If the tech found a water heater venting into a closed space, a missing T&P discharge line, a gas leak, or a backflow assembly that failed its test, the report states it clearly and the recommended action is not soft-pedaled. Safety findings are flagged, not buried.

7. **Photos referenced by what they show.** "See photo: corroded cold-side shutoff under sink" — not embedded image data. The shop's system attaches the files. Reference each photo where it supports a finding.

8. **Audience calibration:**
   - **Homeowner:** Full plain-language translation, short executive summary at the top, clear "what to watch for / what to do next" section.
   - **Property manager:** Add a unit/location identifier and a maintenance-interval note; keep recommended follow-on work itemized so it can be approved against a budget.
   - **Insurance adjuster:** Emphasize the as-found cause (sudden failure vs. wear-and-tear vs. third-party), the date, and the documented readings — the coverage-relevant facts.
   - **Commercial / GC:** Tie line items to the scope of work, note code and permit status, and keep the language specification-grade.

**Output — produce both deliverables every run, clearly separated:**

### Deliverable A — Customer Report

**A1. Header and one-paragraph summary (≤4 sentences)**
- Customer, address, date, technician, license #, work-order #
- What the customer called about and the bottom line: what was found, what was done, and whether the issue is resolved, monitored, or pending a follow-up.

**A2. What we found**
- The as-found condition in plain language, with any readings that explain it (e.g., "Water pressure measured 95 psi at the laundry hose bib — well above the 40–60 psi normal range, which was stressing the supply lines and the water heater").
- Reference supporting photos.

**A3. What we did**
- The work performed, in plain language, in the order it was done.
- Parts installed named in customer-friendly terms (the office record carries the model/serial detail).
- Any tests performed and their result (leak check passed, T&P verified, backflow assembly passed/failed, combustion/CO within range).

**A4. What we recommend (and what you decided today)**
- Recommended follow-on work, each item marked clearly as **recommended (optional)** or **code-required** — never blurred.
- For anything the customer declined or deferred today, record it: "Recommended replacing the corroded cold-side shutoff valve ($X). Customer chose to monitor for now." This protects both parties and seeds an honest follow-up — not a pressure tactic.

**A5. What to watch for / next steps**
- What the customer should do or watch in the coming days (e.g., "For the first week, check the floor around the new water heater each evening; a new tank can show a fitting weep that's easy to correct early").
- Warranty statement: labor warranty length and parts/manufacturer warranty, stated plainly.
- Any pending item: permit/inspection status, parts on order with ETA, scheduled return visit.
- Shop contact line and how to book recommended work.

### Deliverable B — Office Record (structured)

A structured block the office can read at a glance and feed downstream without re-keying. Produce it as labeled fields (and, when the shop's system ingests JSON, the same fields are trivially serializable):

- `work_order`, `date`, `technician`, `customer`, `address`, `job_type`
- `status`: completed | diagnostic_only | partial_parts_on_order | return_scheduled
- `as_found`: one-line condition on arrival
- `as_left`: one-line condition at completion
- `readings`: list of {name, value, normal_range, note} (pressure, temp, CO/combustion, amp draw — only what the tech logged)
- `parts`: list of {description, brand, model, serial, qty, price?} — serial required for warranty-bearing equipment
- `labor_summary`: concise scope of work performed
- `tests`: list of {test, result} (leak check, T&P, backflow pass/fail, combustion)
- `recommendations`: list of {item, classification: recommended|code_required, customer_decision: accepted|declined|deferred, est_price?}
- `warranty`: {labor_term, parts_term, manufacturer}
- `permit`: {required: yes|no, status: n/a|applied|pending_inspection|closed}
- `safety_flags`: list of any safety findings (empty if none)
- `photos`: list of {filename, shows}
- `downstream`: {invoice_lines: [...], review_request_ready: yes|no, warranty_record: yes|no, follow_up_estimate_suggested: yes|no}

**Output requirements:**
- Both deliverables every run. The customer report never contains a serial number in its body; the office record always carries the warranty-bearing serials.
- Recommendations always carry the recommended-vs-code-required classification AND the customer's decision. Never omit a declined recommendation.
- Safety findings, if any, appear in BOTH deliverables and are never softened.
- Do not invent readings, part numbers, or work the tech did not record. If a warranty-bearing part is installed but the tech did not capture the serial, flag it explicitly: "Serial number not captured on site — required for warranty registration; obtain before filing."
- Save to `outputs/service-reports/{date}-{address-short}-{job-type}.md` on confirmation.

## Example Output

**SCENARIO:** Tech voice memo, pasted raw: *"Okay, Henderson, 2200 Maple Court, water heater was leaking from the bottom, 11-year-old 40-gallon AO Smith, totally shot, tank's rusted through. Swapped it for a new AO Smith 40 gallon, model uh ProLine, serial on the sticker. Pressure was high, I read 92 at the hose bib so I told him he really should have a pressure reducing valve, he said not today. Put a new expansion tank on since the old one was waterlogged, that's code on a closed system here anyway. T&P discharge was missing a proper drain line, fixed that, ran it to within 6 inches of the floor like it should be. Leak checked everything, all good, relit and it's heating. Told him watch the floor for a week. Labor's a year, tank's six years on the AO Smith warranty."*

---

### DELIVERABLE A — CUSTOMER REPORT

**Service Report**
**Customer:** Mr. Henderson | **Address:** 2200 Maple Court, [City, State]
**Date:** 06/08/2026 | **Technician:** [TECH NAME] | **License #:** [COMPANY LICENSE]
**Work Order #:** [WO NUMBER]

**Summary:** Your 11-year-old water heater had rusted through at the bottom of the tank and was leaking — it was at the end of its service life and not repairable. We replaced it with a new 40-gallon AO Smith ProLine water heater, replaced the waterlogged expansion tank (required by code on your system), and corrected the temperature-and-pressure relief drain line, which was missing a proper run to the floor. Your hot water is restored and everything tested leak-free. One open item: your water pressure is running high, and we recommend a pressure-reducing valve when you're ready (details below).

**What we found**
- The existing 40-gallon AO Smith water heater (approximately 11 years old) had a rusted-through tank and was leaking from the base. A rusted tank cannot be repaired — replacement is the only fix.
- The expansion tank was waterlogged (failed), meaning it was no longer absorbing pressure changes the way it should on a closed system.
- The temperature-and-pressure (T&P) relief valve's discharge line was missing a proper drain run — a safety item that needs to direct hot water safely toward the floor if the valve ever releases.
- Water pressure measured **92 psi** at the laundry hose bib. Normal household pressure is **40–60 psi**. High pressure stresses your supply lines, fixtures, and the new water heater.

**What we did**
- Removed and disposed of the failed water heater.
- Installed a new **40-gallon AO Smith ProLine** water heater.
- Replaced the failed expansion tank with a new one (this is required by code on your closed system).
- Corrected the T&P relief discharge line — it now runs to within 6 inches of the floor as code requires.
- Leak-checked all connections (passed), relit the unit, and confirmed it is heating normally.

**What we recommend (and what you decided today)**
- **Recommended (optional): Pressure-reducing valve (PRV).** Your 92 psi reading is above the safe range and will shorten the life of fixtures and the new heater. A PRV brings it into the 50–60 psi range. **You chose to hold on this today** — no problem; we've noted it and you can book it anytime.

**What to watch for / next steps**
- **For the first week,** check the floor around the new water heater each evening. A new tank occasionally shows a minor fitting weep that's quick and easy to correct early — call us if you see any moisture.
- **Warranty:** 1-year labor warranty from us; 6-year manufacturer tank warranty from AO Smith (we've recorded your serial number for the registration).
- To schedule the recommended pressure-reducing valve, call us at [COMPANY PHONE].

---

### DELIVERABLE B — OFFICE RECORD

```
work_order: [WO NUMBER]
date: 2026-06-08
technician: [TECH NAME]
customer: Henderson
address: 2200 Maple Court, [City, State]
job_type: water_heater_replacement
status: completed
as_found: 11-yr AO Smith 40gal, tank rusted through, leaking from base; expansion tank waterlogged; T&P discharge line missing proper floor run; static pressure 92 psi
as_left: New AO Smith ProLine 40gal installed; new expansion tank; T&P discharge corrected to 6 in. above floor; leak-checked pass; relit and heating
readings:
  - {name: static_water_pressure, value: 92 psi, normal_range: 40-60 psi, note: above range, PRV recommended}
parts:
  - {description: water heater, brand: AO Smith, model: ProLine 40gal, serial: [CAPTURE FROM STICKER], qty: 1}
  - {description: expansion tank, brand: [BRAND], model: [MODEL], serial: n/a, qty: 1}
  - {description: T&P discharge piping, brand: n/a, model: n/a, serial: n/a, qty: 1 lot}
labor_summary: R&R 40gal water heater; replace failed expansion tank (code, closed system); correct T&P discharge line; leak test; relight and verify heating
tests:
  - {test: leak_check, result: pass}
  - {test: heating_verification, result: pass}
recommendations:
  - {item: pressure-reducing valve install, classification: recommended, customer_decision: declined, est_price: [PRICE]}
warranty: {labor_term: 1 year, parts_term: 6 year tank, manufacturer: AO Smith}
permit: {required: [PER LOCAL CODE], status: [STATUS]}
safety_flags: [T&P discharge line corrected — was non-compliant on arrival]
photos: []
downstream: {invoice_lines: [water heater + install, expansion tank, T&P correction], review_request_ready: yes, warranty_record: yes, follow_up_estimate_suggested: yes (PRV)}
```

**⚠ Action for office:** Water-heater serial number was not captured in the field memo. Obtain the serial before filing the AO Smith warranty registration. The PRV recommendation was declined today — flag for a follow-up touch in 60–90 days (handoff to Dormant Customer Reactivation / Estimate Writer).

---

## Cross-Skill Handoffs

This skill is designed to feed the rest of the repo without re-keying the job:

- **→ Invoice Follow-Up Sequence:** The `downstream.invoice_lines` and `parts` blocks drop straight into the invoice; the `warranty` block populates the warranty terms on the invoice footer.
- **→ Review Request Drafter:** When `status: completed` and `safety_flags` resolved, `review_request_ready: yes` signals the post-job review ask can fire (respecting the hybrid-posture send rules).
- **→ Estimate Writer / Dormant Customer Reactivation:** Any `recommendations` item with `customer_decision: declined|deferred` is a real, honest follow-up — not a pressure tactic. The declined PRV in the example seeds a 60–90 day touch with the customer's own prior context.
- **→ Sewer Camera Inspection Report Drafter:** If the job included a CCTV camera run, the camera portion is documented in that skill's structured format and referenced here, not duplicated.
- **→ Technician Performance Debrief:** The structured office records aggregate into the per-tech measurement loop (completion accuracy, recommended-vs-accepted conversion, callback rate by as-left condition).

## Bilingual Spanish Variant (flagged)

The customer report (Deliverable A) translates to Spanish for Spanish-preferred customers; the office record (Deliverable B) stays English-default as a shop-internal artifact. Terminology calibration: *calentador de agua* (water heater), *válvula de alivio de temperatura y presión* (T&P valve), *válvula reductora de presión* (PRV / pressure-reducing valve), *tanque de expansión* (expansion tank). Register follows the shop's existing customer-communication convention. Joins the repo's bilingual thread.

> **Note (v1.1):** The flag above is superseded by the fully built variant in the v1.1 Additions below. The paragraph is retained for the v1.0 history; for any Spanish-preferred customer, use the v1.1.A built variant.

---

## v1.1 Additions (2026-06-08)

The v1.0 sections above are unchanged. The two sub-sections below are additive — they build out the bilingual variant the v1.0 debut only flagged, and they wire the downstream review-request handoff into the repo-wide hybrid-posture send framing. Use them in addition to v1.0 when the trigger conditions named in each apply.

### v1.1.A — Built Bilingual Spanish Customer Report

The v1.0 ship flagged a Spanish variant but did not build it. v1.1.A builds it. Only **Deliverable A (the customer report)** translates; **Deliverable B (the office record)** stays English-default as a shop-internal artifact that feeds CRM/invoice/warranty systems built in English. When a job runs both languages, produce the English office record once and the customer report in the customer's preferred language.

**Trigger:** Build the Spanish customer report when the job's `customer_language` is `es` (carried from the Pre-Visit Diagnostic Intake record, the AI-RX overnight batch, or the CRM's stored preference). **Don't-auto-detect-from-name rule** (consistent across the repo's bilingual thread): never infer Spanish preference from the customer's surname — use an explicit language field or a stored CRM preference only.

**Terminology table (precise term → customer-register Spanish; do not paraphrase the safety items):**

| English (office-record term) | Spanish (customer report) |
|---|---|
| water heater | calentador de agua |
| temperature-and-pressure (T&P) relief valve | válvula de alivio de temperatura y presión |
| T&P discharge / drain line | tubo de descarga de la válvula de alivio |
| pressure-reducing valve (PRV) | válvula reductora de presión |
| expansion tank | tanque de expansión |
| main water shutoff | llave principal del agua |
| shutoff valve (fixture) | llave de paso |
| static water pressure | presión del agua |
| leak / leaking | fuga / con fuga |
| we recommend (optional) | recomendamos (opcional) |
| code-required | requerido por el código |
| you chose to wait on this today | usted decidió esperar en esto por ahora |
| labor warranty | garantía de mano de obra |
| manufacturer / parts warranty | garantía del fabricante / de las piezas |
| what to watch for | qué vigilar |

**Section-header translations (keep the five-section structure identical to Deliverable A):**

- **Resumen** (Summary — ≤4 sentences)
- **Lo que encontramos** (What we found)
- **Lo que hicimos** (What we did)
- **Lo que recomendamos (y lo que usted decidió hoy)** (What we recommend / what you decided today)
- **Qué vigilar / próximos pasos** (What to watch for / next steps), including the **Garantía** (warranty) line.

**Worked Spanish customer report — same Henderson water-heater job as the v1.0 example:**

```
Reporte de Servicio
Cliente: Sr. Henderson  |  Dirección: 2200 Maple Court, [Ciudad, Estado]
Fecha: 06/08/2026  |  Técnico: [NOMBRE]  |  Licencia #: [LICENCIA]
Orden de trabajo #: [WO]

Resumen: Su calentador de agua de 11 años se había oxidado por dentro y
tenía una fuga — llegó al final de su vida útil y no se podía reparar. Lo
reemplazamos por un calentador de agua AO Smith ProLine nuevo de 40 galones,
cambiamos el tanque de expansión (requerido por el código en su sistema) y
corregimos el tubo de descarga de la válvula de alivio. Ya tiene agua
caliente y todo quedó sin fugas. Un punto pendiente: su presión de agua está
alta y recomendamos una válvula reductora de presión cuando usted guste.

Lo que encontramos
- El calentador AO Smith de 40 galones (aprox. 11 años) tenía el tanque
  oxidado y con fuga en la base. Un tanque oxidado no se puede reparar.
- El tanque de expansión estaba saturado de agua (falló).
- Al tubo de descarga de la válvula de alivio (T&P) le faltaba un tramo
  correcto hacia el piso — un punto de seguridad.
- La presión del agua midió 92 psi en la llave de la lavandería. La presión
  normal es de 40 a 60 psi. La presión alta daña sus tuberías, llaves y el
  calentador nuevo.

Lo que hicimos
- Retiramos y desechamos el calentador con fuga.
- Instalamos un calentador AO Smith ProLine nuevo de 40 galones.
- Cambiamos el tanque de expansión (requerido por el código en su sistema).
- Corregimos el tubo de descarga de la válvula de alivio: ahora llega a 6
  pulgadas del piso, como exige el código.
- Revisamos todas las conexiones (sin fugas), encendimos la unidad y
  confirmamos que calienta bien.

Lo que recomendamos (y lo que usted decidió hoy)
- Recomendamos (opcional): válvula reductora de presión (PRV). Sus 92 psi
  están por encima del rango seguro y acortan la vida de las llaves y del
  calentador nuevo. Una PRV la baja al rango de 50 a 60 psi. Usted decidió
  esperar en esto por ahora — sin problema; lo dejamos anotado y puede
  agendarlo cuando guste.

Qué vigilar / próximos pasos
- Durante la primera semana, revise el piso alrededor del calentador nuevo
  cada noche. A veces un tanque nuevo muestra una pequeña humedad en una
  conexión que es fácil de corregir a tiempo — llámenos si ve humedad.
- Garantía: 1 año de garantía de mano de obra de nuestra parte; 6 años de
  garantía del fabricante en el tanque AO Smith (registramos su número de
  serie).
- Para agendar la válvula reductora de presión, llámenos al [TELÉFONO].
```

**Register and safety rules for the Spanish variant:**

- Use the formal **usted** register throughout, consistent with the repo's customer-facing Spanish convention.
- **Safety findings are never softened in translation.** A T&P correction, a venting issue, or a gas finding reads as plainly in Spanish as in English. The "never minimize a safety issue" core principle applies in both languages.
- **The office record stays English.** Serial numbers, part models, `safety_flags`, and the `downstream` block remain in English so the shop's systems and any English-reading office staff, adjuster, or warranty registrar read one canonical record.
- Numbers, pressures, model numbers, and serials are **not** translated or localized — 92 psi stays 92 psi; AO Smith ProLine stays AO Smith ProLine.

### v1.1.B — Hybrid-Posture Review-Request Send Gate

The v1.0 `downstream.review_request_ready` field is a yes/no gate. v1.1.B aligns it with the repo-wide hybrid-posture send framing (canonical source: Pricebook Q&A v2.3.A; after-hours application: After-Hours Call Summary v2.2.A) so a shop running an AI-RX or automated post-job sequence does not fire a review request at the wrong moment or in a way that should have routed to a human first.

**The gate is not just "is the job done" — it is "is this the right moment and channel to ask."** Set `review_request_ready: yes` only when ALL of the following hold; otherwise set `no` with a one-line reason:

- `status: completed` (never on `diagnostic_only`, `partial_parts_on_order`, or `return_scheduled`).
- `safety_flags` is empty OR every safety flag is recorded as corrected/resolved on this visit. Never ask for a review while a live safety finding is open.
- No declined recommendation involved a dispute, a price complaint, or visible customer dissatisfaction on the visit. A declined upsell on good terms is fine; a tense decline is a `no` with reason `customer_friction_present`.

**New `downstream` sub-field — review-request send posture:**

```
review_request: {
  ready: yes | no,
  hold_reason: <string or null>,         # required when ready: no
  send_posture: HUMAN_FIRST | AUTOMATED_OK,
  earliest_send: <same-day-evening | next-morning>
}
```

- **HUMAN_FIRST** — Set when the job carried any complexity the customer may want to talk through: a large-ticket replacement, a multi-day job, a property-manager/insurance/commercial reader, an elderly customer flagged in the intake, or a corrected safety issue the customer should hear about by voice. The review ask still goes out, but a human touch (the tech's or office's thank-you call) precedes the automated review request. This mirrors the hybrid-posture principle that relationship-bearing moments get a human first; the automation follows, it does not lead.
- **AUTOMATED_OK** — Routine completed job, no friction, homeowner reader, no open safety item. The Review Request Drafter automated post-job send (respecting its own hybrid-posture send rules) can fire on the shop's normal cadence.
- **earliest_send** — `same-day-evening` for routine work the customer is glad is done; `next-morning` when the job ran late, the customer was stressed, or a HUMAN_FIRST touch needs to land first.

**Handoff note:** This field is consumed by the **Review Request Drafter** (which owns the actual review-ask copy and the channel send rules). This skill only sets the posture and the gate; it does not draft the review request. The two skills speak the same hybrid-posture vocabulary so the post-job sequence is coherent end to end: the field report decides *whether and how soon* to ask, the Review Request Drafter decides *what to say and on which channel*.

---

**End of v1.1 additions. The v1.0 example output above remains the canonical example. The v1.1 sub-sections layer on without modifying any v1.0 instruction or example.**
