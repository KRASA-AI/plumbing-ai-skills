---
name: "Dormant Customer Reactivation Outreach"
category: customer-service
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~25 min per batch of 20 contacts; typical win-back batch of 200 contacts recoups 6–12 jobs"
version: 1.2
last_eval_score: 9.7
last_eval_date: 2026-06-22
notes_for_next_eval: "v1.2 (2026-06-22 evaluator cycle) adds v1.2.A — the AI-RX hybrid-posture send gate (AUTOMATED_OK vs HUMAN_FIRST) for OUTBOUND reactivation. This is the standing repo #1 priority (AI-RX hybrid-posture pass on remaining consumers) applied here: v1.1.B governed what the AI does DURING a call (reactive scope-limit transfers) but not WHICH contacts an AI may initiate outreach to autonomously vs which need a human first — the proactive send gate every other AI-RX consumer now carries (Pricebook Q&A v2.3.A, After-Hours Call Summary v2.2.A, Field Service Report Writer v1.1.B, Job Status Update Drafter v1.1.B). Adds a per-segment/per-contact classification table (low-stakes check-ins AUTOMATED_OK; commitment asks, commercial, high-AOV, plan-member-voice, prior-complaint, and stale-data contacts HUMAN_FIRST), a two-field schema extension (send_posture + reason), a human_first_share metric, and opt-out-rate-read-against-posture diagnostic. Matters more for outbound than almost anywhere — an autonomous dialer hitting the wrong segment is how a shop's number gets spam-flagged and the list equity this skill protects is burned. Strictly additive; all v1.0/v1.1 content preserved; lifted to 9.7. v1.3 vectors (carried): per-AI-platform metrics-format adapters for the v1.1.B JSON schema and seasonality-by-region calibration of the dormancy thresholds. v1.1 (2026-05-25) ships three additive sub-sections — Pete & Gabi Olivia case-study calibration (1,000 → 413 → 12 deals → $21,116 published benchmark), AI-voice reactivation adapter (joins the 7-skill AI-RX adapter thread), and bilingual Spanish variant (joins the 9-skill bilingual thread). Originally on the 9.5 floor since debut; v1.1 vector named in 05-18 Remaining Opportunities. v1.2 vectors: per-AI-platform metrics-format adapters for the v1.1.B JSON schema and seasonality-by-region calibration of the dormancy thresholds."
---

# Dormant Customer Reactivation Outreach

## Purpose

Turn the shop's long tail of past customers — the 500, 1,000, or 3,000 households that had one job done and then went quiet — into a predictable source of recurring revenue. This skill takes a segmented list of dormant customers (by time-since-last-service and job type) and drafts personalized, channel-appropriate win-back outreach: SMS first, then email, with a voice-agent script for the customers worth a live follow-up. It also produces the reply-handling playbook so whoever is working the responses knows how to book, how to de-escalate a complaint that surfaces, and how to close out a contact cleanly if the customer has moved or switched providers.

This is distinct from the Review Request Drafter (which fires within days of a job) and from the After-Hours Call Summary (which triages inbound). It is outbound, it is cohort-based, and the framing is always "check-in and care," not "we noticed you haven't paid us recently" — that tonal discipline is what separates reactivation that works from reactivation that gets shop numbers reported as spam.

Industry benchmarks: plumbing shops with a structured reactivation cadence recover 3–6% of dormant customers per campaign cycle at average job ticket; voice-AI-assisted reactivation reports up to 12% recovery on the 12–24 month cohort. The single biggest driver of recovery rate is segment-appropriate framing — a one-size-fits-all "we miss you!" blast underperforms a segmented cadence by roughly 3x.

## When to Use

- Quarterly win-back campaign against the shop's CRM / invoicing system export
- After a slow week where the tech calendar has open capacity and the shop wants to self-generate demand rather than pay for leads
- When rolling out a new service line (maintenance plan, tankless flush, water-quality testing) and the dormant list is the most qualified audience
- When a competitor closes or gets bought and customers in a ZIP code might be looking for a new provider
- Before a seasonal spike (pre-winter freeze prep, pre-holiday drain awareness) to fill the pre-booked calendar

**Do not use for:**
- Customers who explicitly opted out of marketing — exclude before drafting
- Customers with unresolved complaints or open disputes — route to owner / ops manager, not the reactivation queue
- Customers whose last job was a callback or warranty issue within 60 days — wait for the warranty window to close cleanly
- Customers flagged "do not service" internally (problem properties, unpaid balances, etc.)

## Required Input

1. **Customer cohort data (one row per household)**
   - First name and preferred channel (SMS / email / both); if unknown, default to SMS
   - Last service date and job type in plain language ("water heater replaced," "main line cleared," "disposal install," "slab leak repair," "bathroom remodel rough-in")
   - Last technician's first name if the shop has a "request your tech" culture — otherwise omit
   - ZIP code or neighborhood (for localized references — weather, seasonal triggers)
   - Optional: estimated household size, property type (SFH / multi-family / commercial), prior AOV

2. **Segment rules to apply**
   - **12–18 months dormant, last job was installed equipment** (water heater, softener, pump, tankless) → maintenance / flush / anode check angle
   - **18–36 months dormant, last job was a repair** (drain, leak, valve) → check-in and "anything new going on?" angle
   - **36+ months dormant** → reintroduction and current-offer angle; assume the customer may not remember the shop
   - **6–12 months dormant, prior maintenance plan lapsed** → plan renewal angle with price-lock language
   - **Commercial cohort** — different tone, no emojis, send email primary, SMS only if the on-file number is a cell

3. **Shop context**
   - Current promotions or credits available to offer (specific dollar amount or "$X off first service back" — no vague "great deals")
   - Service lines the shop wants to push this cycle (e.g., "we're pushing tankless flushes Q2")
   - Any capacity constraints ("we can take 15 extra appointments over the next 2 weeks")
   - Owner or tech name to sign from, and callback phone / booking link

4. **Compliance guardrails**
   - Confirm the cohort is filtered to only customers who have not opted out of marketing
   - Note whether the shop is in a state with strict consent requirements (TCPA for SMS is federal; some states add layers) — if any uncertainty, downgrade to email-only

## Instructions

You are the Dormant Customer Reactivation drafter for a plumbing shop. Your job is to produce a reactivation packet that a non-marketer on the shop side can pick up and execute with almost no editing.

Produce six sections in this order:

### 1. Cohort Summary and Framing

A 3–5 line read of what's in the list and how you're going to approach it. State the cohort size, dominant segments, the one unifying tonal principle for this batch, and any flags (seasonal timing, geographic clustering, service-line push). This is the paragraph the shop owner reads before approving the batch.

### 2. SMS Cadence (3-touch, per segment)

For each segment present in the cohort, produce three SMS touches, spaced roughly day 1, day 5, day 12. Rules:

- Under 320 characters each (two SMS max)
- First name only — no last name — and no "Dear" constructions
- Mention the actual prior job in plain language, not a generic "we serviced your home"
- Tech by first name if provided
- Exactly one call-to-action per message (booking link OR phone number, not both)
- No emojis unless the shop's brand uses them; if used, one max
- Third touch should be a clean "last note" that doesn't sound passive-aggressive — something like "we won't keep pinging you — if you'd ever like us back just text this number"
- Opt-out language on first touch per segment ("Reply STOP to opt out")

### 3. Email Variant (single touch, per segment)

One email per segment, 80–140 words body, short subject line (under 50 chars), ending with a booking link and a phone number. The email should be readable on a phone without scrolling past the CTA. Do not repeat the SMS wording — rewrite for the longer-form channel with a bit more context about what a check-up / flush / inspection actually involves.

### 4. Voice-Agent Callback Script (for the highest-value segment)

A conversational script (roughly 60–90 seconds of talk time) for either a human callback or an AI voice agent to run against the cohort most likely to convert — usually the 12–18 month installed-equipment cohort. Structure:

- Opening (one sentence): identify the shop, the tech who did the original job, and the reason for the call — a check-in, not a sales pitch
- Permission question ("is now an okay time for a quick question?")
- The actual question (service-specific: "has the water heater we installed been running okay?" / "how is the drain holding up since we snaked it?")
- Branching:
  - **"Yes, all good"** → mention the maintenance angle, offer to book, leave the booking option open without pressure
  - **"Actually, something's been off"** → route to the intake / dispatch flow; do not try to diagnose on the reactivation call
  - **"Not interested / moved / new plumber"** → thank them, mark the record, end the call in under 10 seconds
- Close: confirm the best number on file and invite them to save the shop's number in their phone

### 5. Reply-Handling Playbook

A one-page cheat sheet for whoever is watching the inbound replies. Cover:

- Positive booking reply → confirm within 1 business hour, use the Pre-Visit Diagnostic Intake skill to capture details
- "What was the job again?" → the exact short answer pulled from the customer's history, not a generic one
- Complaint or unresolved issue surfaces → escalate to owner / ops, do not route to standard dispatch; acknowledge within 1 business hour with a personal response (not a template)
- Price-shopping / "how much?" reply → friendly hold on pricing until an intake is done, explain why, offer to book a free evaluation if that's a shop standard
- Wrong number / opt-out → mark the record immediately, do not send additional touches
- Ghost (no response after touch 3) → suppress from outreach for 9 months, drop to the quarterly rotation

### 6. Metrics to Watch

Name the 4–5 metrics the shop should track to know if the campaign worked and to tune the next cycle:

- Reply rate by touch (1, 2, 3) and by segment
- Book rate from replies
- Average ticket of reactivated customers vs. fresh leads this quarter
- Opt-out rate per 1,000 sends (flag if > 2% for SMS — indicates tonal or targeting miss)
- Complaint-surface rate (these are service-recovery opportunities; track separately from the booking funnel)

## Example Output

**Scenario:** A 6-tech shop in Charlotte, NC exports 412 dormant contacts. Segmentation: 78 in the 12–18mo installed-equipment cohort (mostly water heaters and tankless units), 201 in the 18–36mo repair cohort (mix of drain and fixture work), 61 in the 36+mo cohort, 22 in the 6–12mo lapsed-plan cohort, 50 commercial. Current offer: $29 water-heater flush or a $49 whole-home plumbing check with any service booked in the next 21 days. Shop owner: "Dan." Signs messages from the tech when known; "the Ridgeview Plumbing team" when not.

### 1. Cohort Summary and Framing

412 dormant households across 5 segments. The strongest book-rate candidates are the 78 installed-equipment households (12–18mo) — tanks installed 2024–2025 are due for a flush, and the shop has capacity to take 60 of those appointments over the next 3 weeks. Unifying tone: we're a neighborhood shop checking in, not a corporate marketer. Seasonal angle: Charlotte had an unusually wet March, which gives the repair cohort a natural "how's the line holding up?" opener without sounding pretextual. Flag: 22 commercial contacts get routed to email-only per the compliance guardrail; 9 contacts opted out of SMS historically — excluded from the SMS touches but kept in email.

### 2. SMS Cadence — 12–18mo Installed-Equipment Cohort (tech known)

**Touch 1 (Day 1)** — 285 chars

> Hey Sarah — this is Marcus from Ridgeview Plumbing. We installed the water heater at your place last June. Just wanted to check in — it's about due for the first flush, which helps it last a few years longer. $29 flat if we can get out this month. Want me to grab a time? Reply STOP to opt out.

**Touch 2 (Day 5)** — 240 chars

> Sarah, one more on the water heater flush — doing them Tue/Thu mornings next couple weeks, takes under an hour. If there's a better week just say the word. — Marcus, Ridgeview

**Touch 3 (Day 12)** — 180 chars

> Sarah, last note on this — if you'd ever like a flush or anything else looked at, this is my direct line. Won't keep pinging. Good to hear the tank's been running clean. — Marcus

### 2b. SMS Cadence — 18–36mo Repair Cohort (tech unknown, seasonal hook)

**Touch 1**
> Hi Dave — Ridgeview Plumbing checking in. We cleared the main line at your place a couple springs back and with all the rain this month we like to ping old customers. Everything draining okay? We're running $49 whole-home checks with any service through end of month if you want eyes on it. Reply STOP to opt out.

**Touch 2**
> Dave, still a few $49 check slots open this month if you'd like us back out. Takes about 45 min — we walk the whole house and flag anything looking borderline. — Ridgeview Plumbing team

**Touch 3**
> Dave, last one — save our number if you ever need us. Always good to have a plumber in the contacts. — Ridgeview

### 3. Email Variant — 36+mo Cohort (reintroduction)

**Subject:** A quick note from your old plumber

> Hi [First Name],
>
> It's been a while — Ridgeview Plumbing helped out at your address back in [Year] with a [short job description]. We know three-plus years is a long time, so we're not assuming you remember us, and we don't want to fill your inbox.
>
> Just two things: (1) if anything on the plumbing side has been bothering you and you've been putting it off, we're running $49 whole-home checks through the end of the month with any service booked. (2) If you already have a plumber you love, great — save our number anyway. Emergencies never pick convenient days.
>
> [Booking link] or call [shop number].
>
> Thanks,
> Dan
> Ridgeview Plumbing

### 4. Voice-Agent Callback Script — 12–18mo Installed-Equipment Cohort

> Hi, is this Sarah? This is [agent name] calling from Ridgeview Plumbing — Marcus installed your water heater last summer. I'm not trying to sell you anything, just got a minute for a quick check-in call?
>
> [If no:] No problem, I'll let you go. Just wanted to say the unit's about due for its first flush if it's been running fine — we do them for $29. I'll text that info over and let you get back to your day. Thanks Sarah.
>
> [If yes:] Perfect. Real quick — has the water heater been running fine? Any noises, any temperature issues, anything weird?
>
> [If "all good":] Good to hear. The only thing I'd mention is the first flush — we recommend one at about 12–18 months, and you're right in that window. It's $29 if we do it with another service, or $69 standalone. Takes under an hour. Want to grab a slot this week or next?
>
> [If "something's been off":] Okay, I don't want to try to diagnose that over the phone — let me get Marcus or one of the guys out to actually look at it. What days tend to work for you?
>
> [If "not interested":] Understood. Last thing — is [phone on file] still the best number for you? Great. I'll make a note. Take care Sarah.

### 5. Reply-Handling Playbook

**"Yes book me"** → Confirm within 1 business hour. Run Pre-Visit Diagnostic Intake to capture problem detail, access notes, pets, parking. Pull the prior job history into the dispatch brief so Marcus walks in already knowing the context.

**"What did you do last time?"** → Pull from invoice. Answer like a human: "We replaced your 50-gal AO Smith on the left side of the garage, last June 14th. Let me know if that rings a bell." Do not send a link to the invoice as the first reply — send the short answer, offer the invoice second.

**"You guys charged me too much / I had an issue"** → Do not respond via the reactivation SMS number. Kick to Dan. Template: "Sarah, thanks for telling me — let me have Dan the owner reach out personally today. Better that he hears it from you directly than I try to relay." Dan calls within 2 business hours.

**"How much for X?"** → Hold pricing. "We don't quote sight-unseen because too often we guess wrong in either direction. $49 whole-home check is on us with any service — would you like to start there?" Do not negotiate. If they press, book an intake.

**Wrong number / STOP** → Immediate suppression, all channels. Log reason. Do not attempt recovery.

**No reply after touch 3** → Suppress 9 months. Add back to Q1 rotation next year.

### 6. Metrics to Watch

- Reply rate by touch and segment (expect 8–14% on touch 1 for installed-equipment, 4–7% on 36+mo)
- Book rate from replies (aim for 40%+ on the installed-equipment cohort, 20%+ on repair cohort)
- Average reactivated ticket vs. fresh-lead ticket this quarter (reactivated usually runs 15–25% higher — watch for the opposite, which means pricing bled)
- Opt-out rate per 1,000 SMS (flag above 2% — retune tone or cohort)
- Complaint-surface rate — separate bucket, track as service-recovery wins, these become the loudest advocates

---

## Notes for the Shop

- The cadence is explicitly three-touch, not eight-touch. Aggressive cadences burn list equity; this skill is designed for a list the shop can re-run quarterly for years.
- Never combine a reactivation message with a review request. Different intents, different channels, different emotional contract with the customer.
- If the shop runs this alongside Missed Call Text Back and After-Hours Call Summary, set suppression rules so a dormant customer who calls in doesn't then get a reactivation ping the same week.

---

## v1.1 Additions (2026-05-25)

The v1.0 six-section packet above remains the spine. Three additive layers ship below; each is gated by an explicit trigger condition so a shop that runs only English campaigns without an AI voice platform still produces the same v1.0 packet.

### v1.1.A — Pete & Gabi Olivia Inactive-Account Reactivation Case-Study Calibration

**Trigger:** always — applies whenever a cohort is loaded.

**Purpose:** v1.0 ships expected book-rate ranges (3–6% per campaign cycle at average ticket; up to 12% on voice-AI-assisted 12–24 month cohort) as industry rule-of-thumb. v1.1 grounds those ranges in published economics from the Pete & Gabi Olivia inactive-account reactivation case study so the shop owner sees a concrete revenue projection before approving the batch — not an estimate range that could be 2x either direction.

**The published benchmark:**

- 1,000 inactive accounts loaded into the Olivia voice-AI reactivation flow
- 413 conversations initiated (41.3% dial-to-conversation rate)
- 12 deals booked (1.2% inactive-to-deal rate; 2.9% conversation-to-deal rate)
- $21,116 in booked revenue
- Average reactivated ticket: ~$1,760

**EXPECTED-YIELD output block (inserted between section 1 Cohort Summary and section 2 SMS Cadence):**

```
EXPECTED YIELD — based on Pete & Gabi Olivia 1,000-account benchmark
─────────────────────────────────────────────────────────────────────
Cohort size:                412 dormant households
Channel mix:                SMS 390 + email-only 22 commercial

Projected conversations:    ~170  (41% of SMS cohort; voice-AI assisted)
                            +     22  (commercial email opens at typical
                                      ~15-20% engagement)

Projected deals:            ~5    (1.2% of cohort × adjustment for shop's
                                   segment mix — installed-equipment cohort
                                   is ~2x the average, so weight up)
                            Range: 4–9 deals across the 412-account batch

Projected revenue:          ~$8,800 (5 deals × shop's reactivated-AOV)
                            Range: $7,000–$15,800
                            (Shop AOV bands set in config.yml under
                            reactivated_ticket_avg; defaults to the
                            $1,760 Pete & Gabi benchmark if unset.)

Calibration check:          If actual conversation rate is < 25%, the
                            cohort filtering or the SMS opener is the
                            problem. If conversation rate is > 50% but
                            deal rate is < 1%, the SMS-to-call handoff is
                            the problem. If deal rate is > 4%, the cohort
                            was either pre-qualified upstream (rare) or
                            the campaign is being measured incorrectly.
```

**Segment-by-segment weighting** (multiplied against the 1.2%-of-cohort baseline):

| Segment | Weight | Rationale |
|---|---|---|
| 12–18mo installed-equipment | **2.0x** | Equipment due for first flush / anode check — the highest-intent cohort. Pete & Gabi's published case study skews toward this segment. |
| 18–36mo repair cohort | **1.0x** | Baseline. Seasonal hook (e.g. spring rain → main line) lifts to ~1.2x. |
| 36+mo reintroduction | **0.4x** | Many customers in this cohort have already switched providers or moved. |
| 6–12mo lapsed-plan | **1.5x** | Plan-renewal angle with price-lock language; high-trust group. |
| Commercial cohort | **0.8x** | Lower volume but higher AOV; works on email primary, longer decision cycle. |

**How this changes the cohort owner's experience:** v1.0 left the shop owner to guess the ROI before approving the campaign and to argue with the bookkeeper after if the campaign underperformed. v1.1 produces a defensible projection up front, a per-segment weighted breakdown, and a calibration cross-check so the owner can diagnose underperformance against published benchmarks rather than hand-waving.

**Anti-pattern guard:** the EXPECTED-YIELD block uses the word "projected" and includes a range, not a point estimate. The shop should not present the projection as a guarantee to the bookkeeper or as a quota to the CSR running the replies. The Pete & Gabi benchmark is one shop's published number; reasonable variance applies.

### v1.1.B — AI-Voice Reactivation Adapter

**Trigger:** the shop runs the v1.0 section 4 voice-agent callback script on an AI-voice platform (Pete & Gabi Olivia, Avoca AI, Air AI, Voice.ai, AgentZap, MyAIFrontDesk, Voiceflow, Allo, or ServiceTitan AI Voice Agent).

**Purpose:** v1.0 produces the script for either a human callback or an AI voice agent but does not specify the output schema the AI emits back into the shop's CRM and the section 6 metrics block. v1.1 ships the JSON schema explicitly so any of the nine AI-RX platforms can run the script and the outcomes flow back into the same tracker the human CSR uses.

**JSON schema (mirrors Pricebook Q&A v2.2.A canonical AI-RX schema):**

```json
{
  "call_id": "rea_2026-05-25_0042",
  "ai_platform": "pete_gabi | avoca | air_ai | voice_ai | agentzap | myaifrontdesk | voiceflow | allo | servicetitan_voice",
  "customer_language": "en | es | pt | vi",
  "cohort_segment": "12_18mo_install | 18_36mo_repair | 36plus_mo | 6_12mo_lapsed_plan | commercial",
  "prior_job": {
    "job_type": "water_heater_install | drain_clear | leak_repair | tankless_install | softener_install | other",
    "install_date": "2024-06-14",
    "tech_first_name": "Marcus"
  },
  "permission_granted": true,
  "ai_disposition": "ALL_GOOD_BOOKED | ALL_GOOD_DECLINED | ISSUE_SURFACED_DISPATCH | NOT_INTERESTED_OPT_OUT | NO_ANSWER | VOICEMAIL_LEFT",
  "scope_limit_reason": "complaint_surface | warranty_dispute | injury_reported | customer_requested_owner | null",
  "booked_appointment": {
    "service_code": "WH_FLUSH | DRAIN_CHECK | WHOLE_HOME_CHECK | PLAN_RENEWAL | null",
    "appointment_window": "2026-05-27T10:00-12:00 | null",
    "expected_ticket": 29.00
  },
  "call_duration_sec": 87,
  "registration_for_followup": true
}
```

**Branch-to-disposition mapping (mirrors the v1.0 section 4 branching tree):**

- v1.0 "Yes, all good" → maintenance angle → book → `ALL_GOOD_BOOKED` (with `booked_appointment` populated)
- v1.0 "Yes, all good" → maintenance angle → decline → `ALL_GOOD_DECLINED` (no appointment; flag for the quarterly re-rotation)
- v1.0 "Actually, something's been off" → route to dispatch → `ISSUE_SURFACED_DISPATCH` (transfer to human dispatcher or book a paid intake)
- v1.0 "Not interested / moved / new plumber" → `NOT_INTERESTED_OPT_OUT` (immediate suppression, all channels)
- No human answer → `NO_ANSWER` (re-try per the v1.0 three-touch cadence, do NOT escalate to live human)
- Voicemail → `VOICEMAIL_LEFT` (leave the v1.0 script's "I'll text the info over" close; count as touch 1)

**Scope-limit-pattern rules (always-transfer states, per Superior Plumbing "Piper" pattern):**

- Any call where the customer surfaces a complaint or unresolved issue from the prior job — transfer to human within 30 seconds. The AI does not attempt service recovery. (Per v1.0 section 5 reply-handling playbook: complaints route to the owner, not standard dispatch.)
- Any call where the customer reports an injury, property damage, or warranty dispute — transfer to human and flag for the owner.
- Any call where the customer asks to speak to the owner by name — transfer immediately.
- Any commercial-cohort call — these are routed to email-primary per v1.0; AI does not dial commercial.

**Metrics-block back-fill (extends v1.0 section 6 metrics):**

The AI-RX disposition counts flow into the section 6 metrics block exactly:

- v1.0 "Reply rate by touch and segment" — now disaggregated into `human_reply_rate` and `ai_voice_pickup_rate` so the shop sees whether the AI is competing with or complementing the SMS cadence.
- v1.0 "Book rate from replies" — disaggregated into `ai_booked` and `human_booked` so the shop sees whether the AI is closing on its own or warming the lead for a human CSR.
- New `scope_limit_transfer_rate` row — surfaces how often the AI hit a transfer condition. If it's > 20% the scope is mis-calibrated and the v1.0 section 4 script needs a tighter pre-filter.

**Cross-skill loop:** the AI-RX disposition emits forward into the Dispatch Brief Generator v1.2.A AI-RX Morning-Board Ingestion Adapter (an `ALL_GOOD_BOOKED` reactivation call shows up in the next morning's brief as a booked job with the "reactivated dormant" tag), and the metrics-block back-fill emits into the CSR Performance Debrief v1.1.B AI-vs-Human comparative block (so the AI-voice reactivation channel can be benchmarked against the human-CSR reactivation channel side-by-side).

### v1.1.C — Bilingual Spanish Variant

**Trigger:** `config.yml` flags `bilingual: true` with Spanish in the language list, OR a specific customer record on the cohort flags `customer_language: es`.

**Purpose:** the bilingual thread now spans nine skills (joined this cycle by Product Recall Customer Outreach v1.1.B and this v1.1.C). A reactivation campaign in English to a Spanish-dominant household reads as a translation error, not a check-in — and confirms the customer's suspicion that the shop only remembered them because of a marketing list.

**Spanish drafts produced (one per segment, mirror the v1.0 sections 2 / 3 / 4):**

**12–18mo installed-equipment (Spanish, tech known):**

> Hola Sarah, soy Marcus de Ridgeview Plumbing. Instalamos su calentador de agua en junio pasado. Solo quería ver cómo va — ya es hora del primer lavado, ayuda a que dure unos años más. $29 si podemos ir este mes. ¿Le aviso un horario? Responda STOP para no recibir más mensajes.

**18–36mo repair (Spanish, tech unknown, seasonal hook):**

> Hola David — Ridgeview Plumbing pasando saludos. Limpiamos su tubería principal hace un par de primaveras, y con tanta lluvia este mes nos gusta llamar a los clientes. ¿Todo drena bien? Tenemos revisiones completas de la casa por $49 con cualquier servicio hasta fin de mes. Responda STOP para no recibir más mensajes.

**36+mo reintroduction (Spanish email):**

**Asunto:** Una nota rápida de su antiguo plomero

> Hola [Nombre],
>
> Hace tiempo — Ridgeview Plumbing le ayudó en su casa en [Año] con [descripción corta del trabajo]. Sabemos que tres años es mucho, así que no asumimos que se acuerde de nosotros, y no queremos llenarle el correo.
>
> Solo dos cosas: (1) si algo del lado de la plomería le ha estado molestando y lo ha estado posponiendo, estamos haciendo revisiones completas de la casa por $49 con cualquier servicio reservado hasta fin de mes. (2) Si ya tiene un plomero de confianza, perfecto — guarde nuestro número de todas formas. Las emergencias nunca eligen un buen día.
>
> [Enlace de reserva] o llame al [número de la tienda].
>
> Gracias,
> Dan
> Ridgeview Plumbing

**6–12mo lapsed-plan (Spanish):**

> Hola [Nombre], Dan de Ridgeview Plumbing. Vi que su plan de mantenimiento venció en [mes]. Podemos renovarlo al mismo precio de antes si responde esta semana — después tendría que ser al precio actual. ¿Le funciona?

**Voice-agent callback script (Spanish, 12–18mo cohort):** full Spanish version of the v1.0 section 4 script, with the same branching tree. Plumbing-Spanish terminology calibrated per CSR Performance Debrief v1.1.C and Product Recall Customer Outreach v1.1.B:

- **calentador de agua** (water heater) / **calentador sin tanque** (tankless)
- **lavado** or **mantenimiento del calentador** (flush / WH maintenance)
- **desatasco de tubería** (drain clear)
- **revisión completa de la casa** (whole-home check)
- **plan de mantenimiento** (maintenance plan)
- **válvula de cierre** (shut-off valve)

**Don't-auto-detect-from-name rule (preserved across the bilingual thread):** the trigger is the per-customer-record flag, the prior-job intake language, or the inbound-call language — not the surname on the invoice.

**Bilingual-household handoff guidance:** if the SMS goes out in English to a Spanish-dominant decision-maker and the reply comes back in Spanish (very common — the English-named utility account holder forwards the text to a Spanish-dominant spouse or adult child), continue the conversation in Spanish from that point. Do not switch back to English on the next touch to "match the name on the account."

**Cross-skill handoff:** if the reactivation call books an appointment, the resulting Pre-Visit Diagnostic Intake inherits `customer_language: es` and the bilingual handoff continues end-to-end (intake → dispatch brief → tech visit → review request via Review Request Drafter v2.4.C Spanish template).

## v1.2 Additions (2026-06-22)

### v1.2.A — AI-RX Hybrid-Posture Send Gate (outbound reactivation)

**Trigger:** the shop runs reactivation outreach (SMS, email, or the v1.1.B voice-agent script) through any automation or AI-voice platform — i.e., whenever a message or call could be *initiated by software rather than a person*.

**Purpose:** the v1.1.B adapter governs what the AI does *during* a call (the reactive scope-limit / always-transfer states). It does not govern the prior question every other AI-RX consumer in the repo now answers explicitly — *which* contacts an AI may dial or text **on its own** versus which a human must touch **first**. This is the standing repo-wide priority (AI-RX hybrid-posture pass on remaining consumers) applied to outbound reactivation, and it matters more here than almost anywhere else: an autonomous system cold-dialing the wrong dormant segment is the single fastest way to get the shop's number reported as spam and burn the list equity this skill exists to protect. This sub-section adds the proactive **send gate** so each contact is classified **AUTOMATED_OK** (the AI may initiate the touch unattended) or **HUMAN_FIRST** (a person reviews or makes the first contact before any automated follow-up) — the same vocabulary as Pricebook Q&A v2.3.A, After-Hours Call Summary v2.2.A, Field Service Report Writer v1.1.B, and Job Status Update Drafter v1.1.B.

**Per-segment / per-contact send-gate classification:**

| Cohort / condition | Send posture | Why |
|---|---|---|
| 18–36mo repair cohort, no flags | **AUTOMATED_OK** | Lowest-stakes, highest-volume, neutral "check-in" framing. The cohort this automation exists for. |
| 12–18mo installed-equipment, no flags | **AUTOMATED_OK** | Highest-intent, service-specific, benign maintenance ask. |
| 36+mo reintroduction | **AUTOMATED_OK (email-first)** | Many have moved or switched; lead with the lower-friction email channel before any voice dial. |
| 6–12mo lapsed-plan | **HUMAN_FIRST (or named-sender automated)** | Price-lock / renewal language is a commitment ask — send under a named person, or have the CSR glance at the list before it fires. |
| **Commercial cohort** | **HUMAN_FIRST** | Already email-primary per v1.0; B2B relationships are not opened by an autonomous dialer. |
| Any contact with a prior complaint, warranty issue, or open dispute on the record | **HUMAN_FIRST** | These are excluded from the reactivation queue entirely per v1.0 "Do not use for"; if one slips through, a human owns the first touch. |
| High prior AOV (e.g., a past $8k+ repipe / remodel customer) | **HUMAN_FIRST** | A high-value relationship deserves a person's first contact, not a templated blast. |
| Maintenance-plan / Preferred-tier customer | **HUMAN_FIRST for voice; AUTOMATED_OK for SMS/email** | The relationship is the asset; a live voice from the shop reads as care, an AI dial reads as churn. |
| Any contact where the cohort data is stale or unverified (bounced number, returned mail) | **HUMAN_FIRST** | Verify before automating; spamming a wrong number is how opt-out rates spike. |

**Rule of thumb:** automate the neutral, low-commitment, well-verified check-ins; put a human first on anything that is a commitment ask, a high-value relationship, a known sensitivity, or unverified data.

**Schema addition** — extends the v1.1.B JSON with one field so the send gate is auditable:

```json
{
  "send_posture": "AUTOMATED_OK | HUMAN_FIRST",
  "send_posture_reason": "low_stakes_checkin | high_intent_maintenance | commitment_ask | commercial | prior_complaint | high_aov | plan_member_voice | stale_data | null"
}
```

**Metrics-block extension (adds to v1.0 section 6 / v1.1.B back-fill):**

- New `human_first_share` row — % of the batch routed HUMAN_FIRST. If it trends toward zero the gate is being ignored (everything is being automated); if it trends high the shop is leaving automation value on the table. Healthy batches usually land 15–35% HUMAN_FIRST depending on cohort mix.
- `opt_out_rate` is now read **against** `send_posture`: if opt-outs concentrate in AUTOMATED_OK contacts, the automated opener or the cohort filter is the problem; if they concentrate in HUMAN_FIRST contacts, the human sender's script is the problem.

**Anti-pattern guard:** the send gate is **not** a quality ranking of customers — it is a risk-and-relationship routing decision. A HUMAN_FIRST contact is not "worth less"; usually the opposite. And the gate never overrides the v1.0 exclusions: opted-out, do-not-service, and open-complaint contacts are removed before classification, not routed to HUMAN_FIRST.

**Cross-skill agreement:** the `send_posture` classification agrees with the same job's downstream postures — a HUMAN_FIRST reactivation that books an appointment carries that relationship-sensitivity signal into the Pre-Visit Diagnostic Intake and the Dispatch Brief Generator v1.2.A morning board, so a high-AOV or plan-member reactivated customer is not then handed to a fully-automated downstream touch.

