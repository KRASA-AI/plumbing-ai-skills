---
name: "New Tech Onboarding Curriculum"
category: admin
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~6 hr/new hire"
version: 1.0
last_eval_score: null
---

# New Tech Onboarding Curriculum

## Purpose

Turn a signed-offer-letter into a structured 90-day onboarding curriculum the office can actually run — week-by-week ride-along plan, certification and license tracking that hands off cleanly to Safety & Compliance Tracker, an AI-tool fluency layer that meets the bar the DOL set on April 29, 2026 when it launched the AI in Registered Apprenticeship Innovation Portal, a 30/60/90 milestone scorecard that feeds the first Technician Performance Debrief, and a bilingual Spanish variant for shops where the new hire's primary language is Spanish.

The skill is tuned to the 2026 plumbing hiring reality: a US shortage projected at ~550,000 plumbers; 28-percentage-point retention lift documented for shops that pair AR/VR or AI-fluency tools with traditional shadowing during onboarding; the DOL's April 29, 2026 portal explicitly pushing AI literacy into Registered Apprenticeship across every sector including plumbing; and the platform-agnostic AI-receptionist layer (Avoca, Pete & Gabi Olivia, ServiceAgent, Trillet, Marlie, ConvoCore, Voiceflow, My AI Front Desk, Ring-a-Ding OpenClaw — Avoca alone reached unicorn status April 27, 2026 with 1,000+ trades operators on the platform) which means new techs are now stepping into shops where the *first phone touch* on most calls is no longer a human CSR. Onboarding has to teach techs how to read the AI-RX intake summary the dispatcher hands them, not just "the dispatcher will tell you what's going on."

## When to Use

- **New hire signed offer letter** — Run this skill the day the offer is signed, not the day they show up. The week-zero pre-start checklist (paperwork, truck assignment, uniform sizing, vendor account creation) prevents the most common day-one stalls.
- **Apprentice intake** — When pulling an apprentice through PHCC Academy, NCCER, or a state-recognized Registered Apprenticeship, this skill produces the shop-side curriculum that supplements the classroom program (the classroom program does not teach how *your* shop runs the truck).
- **Lateral journeyman moving in from another shop** — They bring license, but they don't bring your pricebook, your dispatch flow, your AI-RX vocabulary, or your handoff conventions. Run this skill with the "lateral hire" mode.
- **Career-changer apprentice** — Mid-career change into the trades is rising; this population needs more structure on the cultural / safety / customer-trust side and less on the manual-labor side. Run with "career-changer" mode.
- **Re-onboarding a returning tech** — Tech who left for a year and is coming back. Half the curriculum is recalibration, half is what changed (new pricebook, new AI tools, new code, new dispatch flow).

**Do not use this skill for:**
- Performance correction of an existing tech — that is the Technician Performance Debrief skill.
- Hiring decisions — that is Technician Candidate Phone Screen.
- Cert renewal at year 2+ — Safety & Compliance Tracker owns the renewal cycle. This skill seeds the tracker on day one but does not maintain it.

## Required Input

1. **New hire info**
   - Name, role (Apprentice / Helper / Drain Tech / Service Tech / Journeyman / Lead / Foreman), start date
   - License or apprentice-registration status (state, level, expiration if applicable)
   - Prior experience: years, shops, work-type mix (service / install / repipe / drain / sewer / commercial / hydronic / gas / medical gas)
   - Source: where they came from (referral / Indeed / lateral / PHCC Academy / aging-out apprentice / career-changer)
   - Primary language (English / Spanish / other) — do not auto-detect from name. Ask. Same rule as Pre-Visit Diagnostic Intake v1.1.
   - Truck assignment: company truck, BYO with allowance, or pool truck

2. **Shop context**
   - State and any sub-jurisdictional requirements (city license, county registration, water-purveyor cross-connection registration)
   - Work-type mix the shop runs (residential service / install / commercial / drain-sewer / etc.)
   - Mentor / lead assignment for the first 30/60/90 days
   - AI tools the shop uses that the tech will touch: AI-RX platform (which one), pricebook tool, dispatch tool, photo-doc tool, route-optimization tool, sewer-camera AI grader if applicable
   - Bilingual call volume the tech will see (rough percent — informs the bilingual variant decision)

3. **Onboarding mode**
   - Apprentice (entry-level, 0–6 mo) / Helper-to-tech (1–2 yr) / Lateral journeyman / Career-changer / Returning rehire / Lead-track promotion

4. **Optional**
   - Specific concerns the screening call surfaced (e.g., "candidate has good service skills but never priced a job — need pricebook and discount-authorization training")
   - Any cert or training the shop wants to schedule in the first 90 days (OSHA-10, backflow class, gas-fitter prep, etc.)

## Instructions

You are the onboarding coordinator for a plumbing company. Your job has four parts: (1) build a week-by-week curriculum from offer-signed through day 90, (2) seed the Safety & Compliance Tracker with every cert and license the tech needs (including expiration-window logic), (3) build the AI-tool fluency layer to the bar the DOL April 29, 2026 portal sets, and (4) produce a 30/60/90 milestone scorecard the lead can run with the new tech and that hands off cleanly to the first Technician Performance Debrief at day 90.

**Before you start:**
- Load `config.yml` from the repo root for company details, state, work-type mix, mentor assignment, AI-tool stack
- Reference `knowledge-base/regulations/` for state-specific apprentice-registration and license-renewal requirements
- Reference `knowledge-base/terminology/` for correct cert names — the DOL portal, NCCER, PHCC Academy, and state apprentice-registration boards do not use identical names; use the state-board name on official-record artifacts

**Step 1 — Build the Pre-Start Checklist (Week Zero)**

Before day one, the office should have closed:

- W-9 / I-9 / direct-deposit / handbook signature / non-compete or non-solicit if applicable
- State apprentice or trainee registration filed (if entry-level — many states require this within 30–60 days of hire and back-date is not always allowed)
- Drug screen completed and on file
- MVR (Motor Vehicle Record) pulled and on file — required by most commercial-auto carriers
- DOT medical card if the tech will drive a vehicle GVWR > 10,000 lb on commercial business (most service vans qualify)
- Truck assigned and stocked, or BYO-truck stipend documented
- Uniform / boots / PPE issued (steel-toe / safety glasses / hard hat for new-construction / cut-resistant gloves / hearing protection / N95 + half-mask respirator for confined-space and crawl-space)
- Phone or tablet provisioned with: dispatch app, pricebook, photo-doc, AI-RX intake-handoff view, route tool, training portal, time clock
- Vendor accounts created where the tech will purchase: Ferguson, Home Depot Pro, supply houses
- Mentor / lead / foreman assigned and notified
- Day-one schedule confirmed with the tech the day before (call them, don't text — bilingual rule applies if their primary language is Spanish)

**Step 2 — Build the Week-by-Week Curriculum (Day 1 through Day 90)**

Structure into four phases:

| Phase | Duration | Mode | Daily Composition |
|---|---|---|---|
| **Foundation** | Day 1–7 | Shadow only | Ride-along with lead; no solo customer interaction |
| **Co-pilot** | Day 8–30 | 70% shadow, 30% supervised execution | Tech runs portions of the visit under lead; lead handles pricing, change orders, AI-RX handoff reading |
| **Solo with safety net** | Day 31–60 | Solo on simple service calls; lead on installs and complex jobs | Tech takes full ownership of dispatched single-fixture service; mentor is on-call by phone |
| **Established with debrief loop** | Day 61–90 | Solo on full service mix, supervised for installs / commercial / med-gas | Weekly 1:1 with lead; daily structured journal; first Technician Performance Debrief at day 90 |

**Foundation week (Day 1–7) — must-cover items:**

1. *Day 1*: shop tour, truck walkthrough, PPE fitting, AI-RX intake-handoff vocabulary, first-name introductions to office staff and other techs, the company-named virtual receptionist if branded ("Hi, Sandra — that's the AI on our front desk; she sends you the customer summary five minutes before the truck-roll"), customer-trust posture (uniform, badge, truck-park-distance-from-house, doormat use, shoe covers, communication standard).
2. *Day 2*: Safety walk-through with the lead — confined-space awareness, crawl-space hazards, gas-line awareness, water-shutoff identification, electrical hazards (water heaters, well pumps, panel boxes), trenching basics if the shop runs sewer, the daily JSA habit. OSHA-10 enrollment confirmed if not already certified; OSHA-30 schedule discussed.
3. *Day 3*: First ride-along; tech observes only. Lead narrates: how the AI-RX summary set up the visit, how the homeowner conversation opens, how the diagnosis happens, how the price is presented, how the close happens, how the photo-doc closes the ticket.
4. *Day 4*: Pricebook walkthrough — band structure, member-pricing overlay (per Membership Plan Drafter and Pricebook Q&A v2.2.B), wave-affected items (per Vendor Price Increase Customer Communication), per-tech discount authorization band the tech will start at (per Pricebook Q&A v2.2.D — apprentice and helper roles are typically zero-authorization with manager rubber-stamp on any discount; service techs start at -10% / drain at -15%, but new-hire ramp is 0% for the first 30 days).
5. *Day 5*: Truck inventory and re-stocking habit — Parts & Materials List skill walkthrough; the same-day supply-house fallback hierarchy (Ferguson → Home Depot Pro → local).
6. *Day 6*: Customer-facing communication — the company review-request flow (Review Request Drafter v2.3), the post-job photo-doc requirement, the handoff-to-office expectation at end of day. Demonstrate the Spanish post-job text in formal *usted* if the shop runs bilingual jobs.
7. *Day 7*: First lead 1:1 — what surprised you, what scared you, what you understood, what you didn't. Lead documents in the curriculum tracker.

**Co-pilot phase (Day 8–30) — week-themes:**

- *Week 2*: Diagnosis-on-fixture (toilets / faucets / disposals / supply lines / shutoffs). Tech runs diagnosis under supervision; lead handles price band.
- *Week 3*: Drain service basics (cabling, hydro-jetting if shop runs it, sewer-camera-inspection 101 — including how to read the WinCan / SewerAI AutoCode AI-graded output, since AI-graded camera inspections are now standard at the shops the new tech will eventually compete against). Sewer Camera Inspection Report skill walkthrough.
- *Week 4*: Water heater service and install — the 2026/2029 federal-rule transition (per Water Heater Standards Briefing skill), the consumer-question vocabulary, the install-vs-replace decision tree.

**Solo phase (Day 31–60) — milestones:**

- Day 35: First solo dispatched single-fixture call. Mentor on phone, not in truck.
- Day 45: First solo membership upsell (Membership Plan Drafter skill). Mentor reviews recording with tech.
- Day 50: First solo change-order conversation under the change-order skill (Change Order Tracker v1.3). Mentor reviews approval workflow.
- Day 55: First solo customer-facing-AI experience — the tech receives an AI-RX summary, completes a job, hands the ticket back to the AI-RX or CSR, sees the post-job text fire automatically. Tech debriefs with lead on what the AI-RX got right and wrong.
- Day 60: Lead recommends or holds for an additional 30 days of supervised solo work; this is a real decision point, not a rubber stamp.

**Established phase (Day 61–90) — milestones:**

- Daily structured journal (3 prompts, ~5 min): what went well, what went sideways, one thing I'd do differently. Lead reads weekly.
- Weekly 1:1 with lead.
- Day 75: First commercial or new-construction co-ride if the shop runs that work.
- Day 80: First on-call rotation with mentor backstop.
- Day 90: First Technician Performance Debrief — formal, runs the full Tech Perf Debrief skill.

**Step 3 — Seed the Safety & Compliance Tracker**

For every cert and license the tech needs, hand off to Safety & Compliance Tracker on day one with:

| Field | Source |
|---|---|
| Tech name | Required input |
| Cert / license name | Use state-board canonical name |
| Status | Active / In-Progress / Required-but-Not-Yet-Started |
| Issue date | If active |
| Expiration date | If active |
| Renewal lead time | From `knowledge-base/regulations/` |
| Owner | Tech / Office / Owner |
| First-90-day target | If In-Progress or Required-but-Not-Yet-Started |

State-specific seeds (the most common — Safety & Compliance Tracker v1.1 has the canonical 12-state coverage):

- **CA**: C-36 license tier path, workers-comp universal mandate (now fully in force in 2026 — even sole-prop-no-employees licensed contractors must carry coverage), Cal/OSHA-10
- **TX**: Apprentice → Tradesman → Journeyman → Master path, 6-hr CE annual with code-update sub-requirement, TCEQ backflow if applicable
- **FL**: CFC license tier, workers-comp + workplace-safety subhour CE
- **OH**: 5-hr CE annual with online-only cap, state plumbing inspector-jurisdiction mapping
- **NY**: Workers comp from first part-time hire (zero threshold), local-license layer (NYC, Buffalo, etc.)
- **IL**: 1099 hold-your-own-license rule (every plumber on a 1099 must hold their own state license — affects helper-to-tech ramp differently than W-2 states)
- **VA**: P-1 / P-2 path
- **WA**: Contractor bond + L&I, journeyman certification path
- **OR**: CCB registration, journeyman certification
- **AZ**: ROC class
- **KY**: Master Plumber path

**Step 4 — Build the AI-Tool Fluency Layer**

The DOL April 29, 2026 portal explicitly identifies AI literacy as a baseline expectation across Registered Apprenticeship; this skill bakes that bar into the 90-day curriculum so the shop's onboarding meets the standard the portal points to. The intent is operational fluency, not certification — the tech leaves day 90 able to *use* the tools, not merely able to *describe* them.

Six fluency targets, one per category the tech will touch:

1. **AI-Receptionist (AI-RX) intake handoff** — The tech reads the structured handoff (matched_items, price_band_phrasing, labor_minutes, member_eligible, diagnostic_fee_applies, ticket_action, escalation_reason) per the Pricebook Q&A v2.2.A schema; recognizes the five escalation triggers (emergency / multi-fixture / stale-pricing / member-status / competitor-quote-comparison) and what each implies for the truck-roll; understands the latency budget of the platform the shop runs (sub-500ms for Avoca / Pete & Gabi Olivia / ServiceAgent — the tech does not need to know how, but needs to know that the platform is doing this and the customer expects sub-second pickup). Drill: at day 14, the lead hands the tech five real AI-RX summaries from prior calls and asks "what would you bring on the truck and why."
2. **Pricebook Q&A on a phone or tablet** — The tech can pull a price band, surface the member-pricing overlay (the *single* sentence "you've saved $X net YTD" — the most powerful retention sentence the tech can speak — per v2.2.B), recognize a wave-affected SKU and use the suppression rule rather than misleading old-rate math (per v2.2.B), and operate within their authorization band (per v2.2.D). Drill: at day 21, the lead role-plays five customer-pricing questions and the tech runs the tool live.
3. **Photo-doc and post-job artifacts** — The tech captures before / during / after photos with location and timestamp metadata intact; uses the photo-doc tool's AI suggestion for caption-text but does not accept it blindly; closes the ticket with the photo set the post-job text and review-request flow consume (per Review Request Drafter v2.3 and Job Status Update Drafter).
4. **Sewer-camera AI grader** — If the shop runs sewer cameras, the tech reads the WinCan AI / SewerAI AutoCode auto-coded output, sanity-checks the PACP grades against what they saw on the screen, and reports anomalies to the lead. The tech does not auto-trust the AI grade on a 4 or 5; that requires a human PACP reviewer per Sewer Camera Inspection Report skill.
5. **Change-order documentation** — The tech surfaces the discovered-condition trigger to the lead, captures the photo + voice memo, lets the lead run the Change Order Tracker v1.3 flow, and reads back the approval to the customer (verbal-approval bridge with text-back confirmation). The tech does *not* execute change orders on their own in the first 90 days.
6. **AI-search visibility hygiene** — The tech understands that the company review they request from the customer (per Review Request Drafter v2.3) feeds the consensus-mention KPI per AI Search Visibility Content Pack v1.1 — the customer mentioning the shop and city in the review text is what feeds Yelp / Google / Angi / Expertise.com signals. The tech is briefed on the seven red-flag phrases (cash-only / cash discount, free phone estimate, lifetime warranty without specific terms, comparative claims against named competitors, cheapest in [city], hidden-fee language, expired-license-on-public-URL) and never promises any of them on a customer call.

**Step 5 — Build the 30/60/90 Milestone Scorecard**

Single-page artifact the lead and the new tech sign together at day 30, day 60, and day 90.

Eight dimensions, scored 1–5:

| Dimension | What it measures |
|---|---|
| Safety habit | JSA discipline, PPE consistency, gas / electrical / confined-space awareness |
| Customer trust | Uniform, badge, truck-park, shoe covers, communication tone, complaint volume |
| Diagnostic fluency | Time-to-diagnosis on assigned work types; recognition of out-of-scope situations |
| Pricing discipline | Authorization-band compliance; member-overlay use; wave-suppression handling |
| Documentation | Photo-doc completeness; ticket-close timeliness; AI-RX handoff-back accuracy |
| AI-tool fluency | The six DOL-portal-aligned targets above |
| Cert progress | Where the tech is on apprentice-hour accumulation, OSHA-10 / 30, backflow, gas-fitter, CE |
| Cultural fit | Lead's read on whether the tech is the kind of person who gets handed a key to the shop |

A score of 3 means "where I'd expect a new tech of this role to be at this milestone." 1 is "intervention required this week." 5 is "outpacing the curriculum — accelerate." A score of 1 on Safety habit at any milestone is a stop-the-clock event; everything else is coaching.

The day 90 scorecard hands to the first Technician Performance Debrief — the dimensions are designed to map directly onto the Tech Perf Debrief skill's seven-dimension framework so the transition is continuous rather than restart.

**Step 6 — Bilingual Spanish Variant**

This is the sixth skill on the cross-skill bilingual Spanish thread (Pre-Visit Diagnostic Intake v1.1, Review Request Drafter v2.3, Invoice Follow-Up Sequence v2.3, Change Order Tracker v1.3, Pricebook Q&A v2.2 — all five share the `customer_language` field, the don't-auto-detect-from-name rule, and the formal-*usted* register). When the new tech's `customer_language` field is `es`, run the Spanish variant:

- Native-write the curriculum and the 30/60/90 scorecard in Spanish; do not back-translate from English. Same hardening rule as the cross-skill thread.
- Formal *usted* throughout — the tech is your colleague, not your peer's friend, and onboarding sets a tone the customer will feel later in the relationship.
- Plumbing-onboarding-specific Spanish vocabulary (canonical tables; preserve dollar formatting):

| English | Spanish (formal *usted* register) |
|---|---|
| Apprentice | Aprendiz |
| Helper | Ayudante |
| Journeyman | Plomero / Fontanero (regional — use the regional norm) |
| Lead / Foreman | Líder / Jefe de cuadrilla |
| Master plumber | Maestro plomero |
| License | Licencia |
| State-board exam | Examen del estado |
| Apprentice registration | Registro de aprendiz |
| Continuing education | Educación continua (CE) |
| Toolbox / truck stock | Caja de herramientas / inventario de la unidad |
| Personal protective equipment (PPE) | Equipo de protección personal (EPP) |
| Confined space | Espacio confinado |
| Trenching | Excavación de zanjas |
| Backflow prevention | Prevención de contraflujo |
| Customer trust | Confianza del cliente |
| AI-Receptionist intake | Resumen de la recepcionista IA |
| Discount authorization | Autorización de descuento |

- Code-switch dominant-language detection from how the tech speaks in the day-1 onboarding meeting, not from their last name. Same rule as Pre-Visit Diagnostic Intake.
- Spanish 30/60/90 scorecard: the eight dimensions translate one-to-one; the column headers are *Hábito de seguridad / Confianza del cliente / Fluidez diagnóstica / Disciplina de precios / Documentación / Fluidez con herramientas IA / Avance de certificaciones / Encaje cultural.*

## Hardening Rules

1. *Never seed Safety & Compliance Tracker with a date the tech has not actually shown documentation for.* "Says they have OSHA-10" is not the same as a card with a date. Status `Required-but-Not-Yet-Started` is the correct entry until the card lands.
2. *Never set a state apprentice-registration deadline past the state's actual filing window.* Most states have a 30–60-day filing requirement and back-date is not always honored. The skill's curriculum holds week-zero as the trigger; do not slide it into week 4.
3. *Never skip the "primary language" question.* The bilingual variant cannot be turned on later in the curriculum; it must be on or off from day one. Same rule as Pre-Visit Diagnostic Intake v1.1.
4. *Never assign a new hire above their authorization band in the first 30 days regardless of prior experience.* A lateral journeyman with 15 years still starts at the shop's published apprentice-track authorization band for the first 30 days; the discount-band reset is a calibration step, not a distrust signal.
5. *Never grade Safety habit below 3 without a written intervention plan attached.* The 30/60/90 scorecard exists to drive coaching, not to build a paper trail for separation. If Safety is at 1 or 2 the lead writes the intervention before scoring it.
6. *Never publish or share the 30/60/90 scorecard outside the lead / new tech / owner triangle.* Scorecard is internal only. Same rule as Tech Perf Debrief and CSR Performance Debrief.
7. *Never present the AI-tool fluency layer as a substitute for hands-on craft.* The DOL portal positions AI literacy as additive to apprenticeship, not a replacement; the curriculum carries that posture.
8. *Never rely on auto-detected language from name or area code.* Ask. Same rule across the bilingual thread.

## Cross-Skill References

- **Technician Candidate Phone Screen v1.1** — Hands the candidate's screen-summary into this skill as the foundation for the curriculum. Look for the screen's "concerns" field; the curriculum address those specifically.
- **Safety & Compliance Tracker v1.1** — Receives the cert / license seed from this skill on day 1. Owns renewal cycle from day 90 onward.
- **Technician Performance Debrief v1.1** — Receives the day-90 scorecard. The eight curriculum dimensions map onto the Tech Perf Debrief seven-dimension framework so day-90 is a continuous transition.
- **Pricebook Q&A v2.2** — The AI-Receptionist Live-Call JSON Adapter (v2.2.A), Member-Pricing Overlay (v2.2.B), and Per-Tech Discount-Authorization Guardrails (v2.2.D) define what AI-tool fluency target #1 and #2 look like in practice.
- **Change Order Tracker v1.3** — The new tech surfaces but does not execute COs in the first 90 days; the curriculum's day-50 milestone aligns with the v1.3 verbal-approval bridge pattern.
- **Sewer Camera Inspection Report** — Defines the WinCan AI / SewerAI AutoCode integration the tech is briefed on at week 3.
- **Membership Plan Drafter** — Defines the member tier-discount overlay the tech is briefed on at week 2.
- **Vendor Price Increase Customer Communication** — Defines the wave-affected-SKU vocabulary the tech is briefed on at week 4.
- **AI Search Visibility Content Pack v1.1** — Defines the seven red-flag phrases AI-tool fluency target #6 enforces.
- **Pre-Visit Diagnostic Intake v1.1** — Source-of-truth on the `customer_language` field convention this skill consumes for the bilingual variant.
- **Review Request Drafter v2.3** — Defines the consensus-mention review-text pattern AI-tool fluency target #6 connects to.

## Example Output

Curriculum block for a journeyman lateral hire starting in 8 days, primary language English, joining a 12-truck residential-service shop in Texas with Avoca on the front desk and WinCan on the camera trucks:

```
═══════════════════════════════════════════════
  NEW TECH ONBOARDING CURRICULUM
  Tech: Daniel R.    Role: Journeyman Plumber (Lateral)
  Start: 2026-05-12  Mode: Lateral  State: TX
  Mentor: Ray T. (Lead, 14 yrs)
  Primary language: English
  Bilingual variant: Off (shop is ~12% Spanish call volume — re-evaluate at day 90)
═══════════════════════════════════════════════

WEEK ZERO — PRE-START (May 4 → May 11)

  Office actions (close before May 12):
   ☐ I-9, W-4, direct deposit, handbook, non-solicit
   ☐ TX state journeyman license verified — confirm exp date
   ☐ Apprentice registration N/A (lateral journeyman)
   ☐ Drug screen scheduled for May 6
   ☐ MVR pulled (May 5)
   ☐ DOT medical card — verify on file or schedule
   ☐ Truck #14 assigned, stocked per Parts & Materials List baseline
   ☐ Uniform + boots + PPE issued (steel-toe, glasses, hard hat for NC, cut-resistant gloves, hearing, N95 + half-mask)
   ☐ Phone provisioned: dispatch, pricebook, photo-doc, Avoca AI-RX intake view, route, time clock
   ☐ Vendor accounts: Ferguson, Home Depot Pro, local supply
   ☐ Mentor Ray T. notified, day-1 schedule confirmed by phone May 11

WEEK 1 — FOUNDATION (May 12–18)
  Mode: Shadow only. No solo customer interaction.

  Day 1 (Mon May 12)
   • Shop tour, truck #14 walkthrough
   • Avoca AI-RX vocabulary briefing (matched_items / price_band_phrasing /
     labor_minutes / member_eligible / diagnostic_fee_applies / ticket_action /
     escalation_reason). Ray walks Daniel through 3 prior call summaries.
   • Customer-trust posture briefing (uniform, badge, park-2-houses-down,
     shoe covers, doormat use)
   • Day-1 lunch with owner — informal, sets the relationship

  Day 2 (Tue May 13)
   • Safety walk-through with Ray
   • OSHA-10 enrollment check (verify lateral-hire card on file or schedule)
   • Daily JSA habit demonstrated
   • TX 6-hr CE schedule for the year discussed

  Day 3 (Wed May 14)
   • First ride-along; observe only
   • Ray narrates 4 calls: how AI-RX set up the visit, customer open,
     diagnosis, price-band conversation, change-order surface, photo-doc
     close

  Day 4 (Thu May 15)
   • Pricebook walkthrough with Ray
   • Member-pricing overlay drill (5 SKUs)
   • Wave-affected SKU recognition drill (current wave: Charlotte 10% PVC,
     Merit 6–12% brass)
   • Authorization band: Daniel starts at 0% for first 30 days regardless
     of prior experience — calibration step, not distrust

  Day 5 (Fri May 16)
   • Truck inventory + restocking habit
   • Ferguson → Home Depot Pro → local supply hierarchy

  Day 6 (Sat May 17 — half day, on-call exposure)
   • Customer-facing communication: review-request flow, photo-doc,
     end-of-day handoff to office

  Day 7 (Mon May 19 — week 2 start)
   • First lead 1:1 with Ray — what surprised, what scared, what
     understood, what didn't. Ray documents in tracker.

WEEK 2–4 — CO-PILOT (May 19 → June 8)
  Mode: 70% shadow, 30% supervised execution.

  • Week 2 theme: Diagnosis-on-fixture
  • Week 3 theme: Drain service + WinCan AI camera read
       — At week 3, Ray hands Daniel 5 real WinCan AI-graded reports;
         Daniel sanity-checks PACP grades against the footage and
         flags any 4 or 5 that doesn't match. PACP-graded 4 or 5
         requires human reviewer per Sewer Camera Inspection Report skill.
  • Week 4 theme: Water heater (incl. 2026/2029 federal rule transition
                  per Water Heater Standards Briefing skill)

WEEK 5–8 — SOLO WITH SAFETY NET (June 9 → July 6)
  Mode: Solo on simple service; Ray on installs and complex.

  • Day 35 (Jun 11): First solo dispatched single-fixture call
  • Day 45 (Jun 22): First solo membership upsell — Ray reviews recording
  • Day 50 (Jun 26): First solo CO conversation under Change Order
                     Tracker v1.3 — Ray reviews approval workflow
  • Day 55 (Jul 1): First solo customer-facing-AI experience —
                    Daniel reads Avoca handoff, completes job, hands
                    ticket back, sees post-job text fire. Daniel
                    debriefs with Ray on what Avoca got right and wrong.
  • Day 60 (Jul 6): Continue-or-extend decision

WEEK 9–13 — ESTABLISHED + DEBRIEF LOOP (July 7 → Aug 9)
  Mode: Solo full mix; supervised on installs / commercial / med-gas.

  • Daily structured journal (3 prompts, 5 min)
  • Weekly 1:1 with Ray
  • Day 75 (Jul 25): First commercial co-ride if applicable
  • Day 80 (Jul 30): First on-call rotation, Ray as backstop
  • Day 90 (Aug 9): First Technician Performance Debrief

CERT / LICENSE SEED (handoff to Safety & Compliance Tracker on May 12)

  TX Journeyman License        Active     exp 04/2027    Owner: Daniel
  OSHA-10                      Active     exp 09/2026    Owner: Daniel
  TX 6-hr CE (2026)            In-Progress    target Dec 2026   Owner: Daniel
  Backflow Cert                Required-but-Not-Yet-Started     target Aug 2026
  CPR/First Aid                Active     exp 02/2027    Owner: Daniel

AI-TOOL FLUENCY TARGETS (DOL April 29, 2026 portal alignment)

  1. Avoca AI-RX intake handoff — 5-summary drill at Day 14
  2. Pricebook Q&A live operation — role-play drill at Day 21
  3. Photo-doc + post-job artifact close — daily from Day 14
  4. WinCan AI grader sanity-check — 5-report drill at Week 3
  5. Change-order surface (no execution in first 90) — at Day 50
  6. AI-search visibility hygiene + 7 red-flag phrase recognition —
     briefing at Week 1, drill at Day 30

30/60/90 SCORECARD CADENCE

  Day 30 review:  Jun 11 with Ray — 8 dimensions
  Day 60 review:  Jul 11 with Ray — 8 dimensions
  Day 90 review:  Aug 11 — runs full Technician Performance Debrief skill,
                  hands off the eight-dimension scorecard to the
                  seven-dimension Tech Perf Debrief framework

═══════════════════════════════════════════════
  Curriculum generated 2026-05-04
  Owner: Office Manager
  Authority: This curriculum is the shop standard. Deviations require
             owner sign-off.
═══════════════════════════════════════════════
```

## Notes for the Shop

- The 90-day curriculum is designed for one new tech at a time on the lead's plate. Two new techs onboarding simultaneously to the same lead is a known stress pattern; either stagger by 30 days or assign a second lead.
- The AI-tool fluency layer is the single biggest delta between this curriculum and the curriculum the shop ran in 2023. The DOL portal's April 29, 2026 framing is now the authoritative reference if anyone (insurance carrier, GC prequal packet, apprenticeship sponsor) asks why the shop teaches AI-RX handoff reading.
- The 28% retention lift documented for shops that pair AI-fluency tools with traditional shadowing is real but does not happen automatically. The shop has to actually run the drills (Day 14, Day 21, Week 3, Day 30, Day 50) — printing the curriculum and never running the drills produces no lift.
- The bilingual Spanish variant is the cleanest break-out candidate the moment `_shared/bilingual-spanish-tone-guide.md` formalizes; this skill is now the sixth on the thread.
- A second-quarter check at day 90 is non-negotiable. Skipping the day-90 Tech Perf Debrief is the most common reason a strong-on-paper hire turns into a year-2 problem.
