---
name: "Job Status Update Drafter"
category: customer-service
tools: [claude, chatgpt]
difficulty: beginner
time_saved: "~3 min/update, ~15 min/job"
version: 1.1
last_eval_score: 9.7
notes_for_next_eval: "v1.1 (2026-06-15 evaluator cycle) closes two named gaps additively. (1) Built the bilingual Spanish lifecycle variant: the v1.0 skill listed 'non-English primary language, language preference' as a customer-context flag (Required Input #4) but never built the variant — the exact flagged-but-not-built pattern the repo lifts on. v1.1 builds the per-stage Spanish drafts (booked, reminder, on-the-way, running-late, complete, post-visit care) with a terminology table, the don't-auto-detect-from-name rule, and worked SMS examples; joins the repo bilingual thread. Lifted personalization 9 -> 10. (2) Added the AI-RX hybrid-posture send gate: this skill is a core lifecycle-messaging AI-RX consumer (status texts are exactly what an AI receptionist / automation fires) and was the named #1 next-cycle priority (hybrid-posture pass on remaining consumers). v1.1 classifies each stage AUTOMATED_OK vs HUMAN_FIRST with the same vocabulary as Pricebook Q&A v2.3.A / After-Hours Call Summary v2.2.A / Field Service Report Writer v1.1.B. Net 9.6 -> 9.7. Strictly additive; all v1.0 content preserved. v1.2 vectors: pt/vi stage variants; a structured status_event JSON adapter so an FSM webhook can fire the right stage draft automatically."
---

# Job Status Update Drafter

## Purpose

Draft the short, on-brand customer updates that go out across a job's lifecycle — booked, on-the-way, running-late, on-site, delay / parts run, wrapping up, complete, and (when needed) post-visit care notes. Each message is short enough for SMS, personal enough that the customer doesn't feel like they're getting an automated blast, and detailed enough to reduce the inbound "where's my plumber?" calls that eat dispatcher time.

This skill closes the loop between the Pre-Visit Diagnostic Intake (which books the job) and the Review Request Drafter (which goes out after close). It replaces the typical situation in a plumbing shop — where updates either don't happen or get fired off by the dispatcher in a rushed, typo-heavy one-liner — with a consistent set of touches that are demonstrably the #1 driver of customer satisfaction in service trades.

## When to Use

- **Booking confirmation** — As soon as a job is booked by phone, chatbot, or web form.
- **Evening-before reminder** — For next-day jobs, automated 5–7 PM the day before.
- **On-the-way** — When the tech hits "en route" in the field app, or the dispatcher manually flips the status.
- **Running late** — When the prior job is going long and the window for this customer is slipping.
- **On-site arrival** — When the tech knocks on the door (useful for absentee customers).
- **Delay / parts run** — When the tech needs to leave and come back, or order a part.
- **Wrap-up and complete** — When the tech is writing up and leaving.
- **Post-visit care notes** — Same day or next day, tied to the specific work performed.

**Do not use for:**
- Emergency / safety communications where liability or escalation is involved — use dispatcher or owner direct
- Sales / upsell offers disguised as status updates (customers hate this)
- Callback or complaint resolution (different workflow and tone)

## Required Input

1. **Job context**
   - Customer first name (for warmth) and preferred channel (SMS / email / both)
   - Job type in plain language (water heater replacement, drain clear, tankless flush, slab leak investigation, etc.)
   - Scheduled arrival window
   - Tech first name and truck description if the shop provides one ("white truck with blue logo")

2. **Current status and trigger**
   - Which stage is this update for — booked, reminder, on-the-way, late, on-site, delay, wrap, complete, post-visit?
   - Supporting detail for the stage:
     - Running late: how long, why (one-sentence honest reason, no over-explanation)
     - Delay / parts run: what's needed, where it's being picked up, revised ETA
     - Complete: what was done (1–2 sentences), warranty terms, payment status
     - Post-visit care: specific to the work (e.g., "do not use the disposal for 24 hours while the putty sets")

3. **Channel and tone**
   - SMS: under 320 characters (2 SMS max), no emojis unless brand uses them, one link maximum
   - Email: short subject line, 60–120 words body, one call-to-action
   - Tone: warm, professional, conversational — the way a trusted neighborhood plumber actually texts

4. **Customer context (optional but valuable)**
   - New customer vs. repeat (slightly warmer for repeat)
   - Any flags from intake (elderly, non-English primary language, language preference, prior issue resolved — mention proactively to rebuild trust)
   - Payment method on file? (affects wrap-up message)

## Instructions

You are the customer success assistant for a plumbing company. Your job is to draft the right message for the right stage in the job — not a generic status blast, but the specific update this specific customer should receive right now.

**Before you start:**
- Load `config.yml` for company name, voice guidelines, standard sign-off, tracker/reschedule links, warranty language
- Check `knowledge-base/terminology/` only if the job type has language that needs to be translated for homeowners (e.g., "we replaced the flapper and flush valve" → "we replaced the rubber seal and the handle-lever assembly inside the tank")
- Check the Review Request Drafter skill to avoid duplicating its language — the completion message is the handoff, not the review ask

**Core principles:**

1. **Each stage has a job to do.** Booked = confirms the customer was heard and sets the expectation. Reminder = reduces no-shows and re-confirms the window. On-the-way = reduces inbound calls and gives the customer a chance to move their day. Running late = protects trust with honesty, never spin. On-site = important for absentee customers. Delay / parts run = turns a potentially bad moment into a moment of service recovery. Complete = closes the loop, warranty, payment, what-to-do-now. Post-visit care = the message that drives repeat business more than any other.

2. **Honest on-time, honest late.** If the tech is on time, say so. If the tech is running 40 minutes late, say 40 minutes — don't say "slight delay." Customers forgive a plumber who's late; they don't forgive one who lied about it.

3. **Name the tech.** Customers form a relationship with a person, not a company. "Javier is on the way in our white truck" lands differently than "A technician is en route."

4. **One link max per message.** Whichever link is most useful for that stage — live tracker for on-the-way, reschedule for reminder, review request for complete (but never in the same message as the completion itself — that's its own workflow).

5. **Plain-language job descriptions.** "Tankless descale and sediment flush" becomes "annual tankless water heater cleaning." "Re-seat and re-wax" becomes "reset the toilet with a new wax seal." The homeowner should recognize what they paid for.

6. **Never quote price changes via SMS.** If the job scope changed and the price is different, the tech is on-site and should have that conversation in person with a written change order (see Change Order Tracker skill) — never drop a new number into a status text.

7. **Post-visit care is the quietly brilliant message.** Send it the same evening or the next morning. Pair it tightly to the work: water heater installed → "give it 90 minutes to come up to temp, and let us know if any taps run hotter than expected." Disposal replaced → "run cold water 30 seconds before and after you use it for the first week." This is the message customers screenshot and save.

**Output sections (produce in order):**

### Section 1 — Stage, channel, and one-line intent

State which stage this is and what the message is trying to do in one sentence. This keeps the draft honest and gives the dispatcher a reason to say yes before sending.

### Section 2 — Primary draft (SMS by default, or email if preferred channel is email)

The actual message, ready to send. Include character count for SMS or word count for email.

### Section 3 — Alternate draft in the other channel

Same stage, different channel. Some dispatchers or automations will use both.

### Section 4 — "When to NOT send" note (if applicable)

Short bullet on when this stage's message should be suppressed:
- On-the-way skipped if the customer explicitly asked no pre-arrival contact
- Reminder skipped for same-day urgent/emergency bookings
- Running-late skipped if delay is under 10 minutes (creates more anxiety than it solves)
- Complete skipped if the tech did not actually complete the work (a return visit is scheduled — use delay / parts run instead)

**Tone and format:**
- No emojis unless the brand uses them in `config.yml`
- No exclamation points stacked — one is fine, two looks automated
- Contractions are encouraged ("we're", "you'll", "it's") — they read human
- Never use "dear customer" or "valued customer" — use the first name
- Never start with "Just following up" on a status message — it's a status message, not a follow-up

**Output requirements:**
- Stage explicitly named
- SMS drafts under 320 characters (2 SMS or fewer); email drafts 60–120 words
- Tech first name and job-type plain-language description always included where relevant
- Link count: one or zero per message
- Save to `outputs/status-updates/{date}-{customer-last-name}-{stage}.md` on confirmation

## Example Output

**SCENARIO:** Customer Priya Ramachandran. Job type: 50-gal gas water heater replacement. Tech: Sam. Window: 12–2 PM. Stage to draft: **running 35 minutes late** because the prior job's pan drain needed a repair the tech hadn't anticipated.

---

### Section 1 — Stage, channel, intent

**Stage:** Running late (35 min)
**Channel:** SMS (preferred) + email alternate
**Intent:** Protect trust by telling the customer the honest delay, give them the choice to reshuffle if they need to, offer a live tracker link instead of another "I'll text you when I'm close."

### Section 2 — SMS draft (primary)

> "Priya — quick heads-up from [Company]. Sam is running about 35 min behind the 12–2 window — the prior job needed an extra fix we couldn't leave unfinished. New ETA is 2:35. Live tracker: [LINK]. Text back if this no longer works and we'll re-book on you. Thanks for the patience."

*(298 characters)*

### Section 3 — Email draft (alternate)

**Subject:** Heads-up — Sam running ~35 min behind your water heater window

> Hi Priya,
>
> Quick note: Sam is running about 35 minutes past the 12–2 PM window for your water heater replacement. The job ahead of yours needed an extra fix we couldn't leave unfinished, and we'd rather be straight with you than give you a vague ETA.
>
> New ETA: **2:35 PM**. You can watch his live location here: [LINK].
>
> If that no longer works for your day, just reply or text (555) 123-4567 and we'll reschedule on us.
>
> Thanks for the patience,
> [Company]

*(92 words)*

### Section 4 — When to NOT send

- Skip if the delay is under 10 minutes — more anxiety than it solves.
- Skip if the customer already rescheduled themselves after the original booking.
- Do not send if the tech has already arrived before the message goes out.

---

### Alternate stage examples (abbreviated)

**COMPLETE — SMS, 50-gal gas WH replacement, payment on file**

> "Priya — Sam just wrapped your new water heater install. Give it about 90 min to come fully up to temp. You'll see the receipt and 10-yr warranty in your email. Any hot-water taps not feeling right in the next 24 hrs, text me back and we'll pop out. Thanks for having us!"

*(275 characters)*

**POST-VISIT CARE — EMAIL, next morning**

**Subject:** Two quick notes about your new water heater

> Hi Priya,
>
> Sam here. A couple of quick things now that your new 50-gallon gas unit has had a full night to settle:
>
> 1. First hot bath or shower of the day might run a shade hotter than your old unit for the first week. Your thermostat is set to 120°F — a safe level — but newer tanks hold temperature more efficiently.
> 2. You'll hear an occasional tick from the expansion tank on the cold-water line. That's normal as the tank cycles and isn't a leak.
>
> Your full 10-year warranty paperwork is attached. If anything at all feels off, just reply to this email — it goes right to me.
>
> — Sam, [Company]

*(114 words)*

**BOOKED — SMS**

> "Hi Priya — you're booked with [Company] tomorrow 12–2 PM for your water heater replacement. Your tech is Sam (white truck, blue logo). Need to move it? Reply here or [LINK]. See you tomorrow."

*(196 characters)*

**REMINDER — SMS (evening before)**

> "Hi Priya — just a heads-up for tomorrow's 12–2 PM window with Sam for your water heater replacement. A heads-up if a dog is home, and we'll see you then. Reschedule: [LINK]."

*(175 characters)*

**ON-THE-WAY — SMS**

> "Priya — Sam is on the way, ETA about 25 min. White truck with blue logo. Live tracker: [LINK]."

*(97 characters)*

---

## v1.1 Additions (2026-06-15)

The v1.0 sections above are unchanged. The two sub-sections below are additive: they build the Spanish lifecycle variant the v1.0 skill flagged but did not build (Required Input #4 names a language-preference flag), and they wire the per-stage messages into the repo-wide AI-RX hybrid-posture send framing so an automated status sequence fires the right stage in the right way.

### v1.1.A — Bilingual Spanish Lifecycle Variant (built)

**Trigger:** Produce the Spanish draft when the job's `customer_language` is `es` — carried from the Pre-Visit Diagnostic Intake record (`customer_language: en|es|pt|vi|other`), the CRM's stored preference, or an explicit field. **Don't-auto-detect-from-name rule** (consistent across the repo's bilingual thread): never infer Spanish preference from a surname; use an explicit language field or stored CRM preference only. When a customer's language is unknown, default to the shop's primary language and let the first human touch confirm.

**What translates:** the customer-facing SMS/email body for every stage. Links, the company name, the tech's name, addresses, and any tracker/reschedule URL stay as-is. Numbers and time windows stay in their original form (12–2 PM stays 12–2 PM).

**Terminology table (English stage term → customer-register Spanish; usted register throughout):**

| English | Spanish (customer message) |
|---|---|
| you're booked | ya está agendado / agendada |
| arrival window | ventana de llegada |
| running late / about 35 min behind | con un retraso de unos 35 min |
| on the way / en route | en camino |
| live tracker | rastreo en vivo |
| reschedule | reagendar |
| we wrapped your install | terminamos su instalación |
| warranty | garantía |
| what to watch for | qué vigilar |
| reply or text us | responda o envíe un mensaje |
| thanks for your patience | gracias por su paciencia |

**Worked Spanish SMS drafts (same Priya / 50-gal gas water-heater job as the v1.0 example):**

- **BOOKED:** "Hola Priya — ya está agendado con [Company] mañana de 12–2 PM para el reemplazo de su calentador de agua. Su técnico es Sam (camioneta blanca, logo azul). ¿Necesita cambiarlo? Responda aquí o [LINK]. Nos vemos mañana."
- **REMINDER (evening before):** "Hola Priya — recordatorio de su ventana de mañana 12–2 PM con Sam para su calentador de agua. Si hay un perro en casa, avísenos. Reagendar: [LINK]."
- **ON-THE-WAY:** "Priya — Sam va en camino, llega en unos 25 min. Camioneta blanca con logo azul. Rastreo en vivo: [LINK]."
- **RUNNING LATE:** "Priya — un aviso rápido de [Company]. Sam lleva unos 35 min de retraso sobre la ventana de 12–2 — el trabajo anterior necesitó un arreglo extra que no podíamos dejar a medias. Nueva hora estimada: 2:35. Rastreo: [LINK]. Si ya no le funciona, responda y lo reagendamos. Gracias por su paciencia."
- **COMPLETE:** "Priya — Sam terminó la instalación de su calentador nuevo. Déle unos 90 min para llegar a temperatura. El recibo y la garantía de 10 años le llegan por correo. Si alguna llave de agua caliente no se siente bien en 24 h, respóndame y pasamos. ¡Gracias por confiar en nosotros!"
- **POST-VISIT CARE (next morning):** "Hola Priya — soy Sam. Dos notas de su calentador nuevo: (1) el primer baño del día puede salir un poco más caliente la primera semana; está a 120°F, un nivel seguro. (2) Puede oír un leve tic del tanque de expansión — es normal, no es una fuga. Su garantía va adjunta por correo. Cualquier cosa, respóndame."

**Register and safety rules:**
- Use the formal **usted** register throughout, consistent with the repo's customer-facing Spanish convention.
- An honest-late message is honest in Spanish too: state the real delay in minutes, never soften it ("un pequeño retraso" is not acceptable for a 35-minute delay).
- Never put a price or change-order number into a Spanish status text either — the v1.0 "never quote price changes via SMS" rule applies in both languages.
- Keep each Spanish SMS within the same 2-SMS / 320-character budget; Spanish runs ~15–20% longer than English, so trim adjectives before links.

### v1.1.B — AI-RX Hybrid-Posture Send Gate (per stage)

This skill sits between the Pre-Visit Diagnostic Intake (which now sets `HYBRID_POSTURE_MODE` and flags `PREFERS_HUMAN` / `SAFETY_ESCALATION` / `COMPLEX_INTAKE` / `REPEAT_CALLER_FLAG`) and the Review Request Drafter. When a shop runs an AI receptionist or an automated status sequence, the lifecycle messages should not all fire the same way. v1.1.B classifies each stage with the repo-wide vocabulary (canonical source: Pricebook Q&A v2.3.A; applied in After-Hours Call Summary v2.2.A and Field Service Report Writer v1.1.B).

**Per-stage default send posture:**

| Stage | Default posture | Why |
|---|---|---|
| Booked | AUTOMATED_OK | Confirmation; routine. |
| Reminder | AUTOMATED_OK | Routine; reduces no-shows. |
| On-the-way | AUTOMATED_OK | Time-sensitive, benefits from automation speed. |
| Running late | **HUMAN_FIRST if** the delay >45 min, the customer was flagged `PREFERS_HUMAN`/elderly, or it's the second slip on the same job; else AUTOMATED_OK | A trust-bearing moment; a big or repeated slip should carry a human voice, not a bot text. |
| On-site arrival | AUTOMATED_OK | Useful for absentee customers; low risk. |
| Delay / parts run | **HUMAN_FIRST** | Service-recovery moment; the revised plan and ETA should come from a person. |
| Wrap-up / complete | **HUMAN_FIRST if** large-ticket replacement, multi-day job, property-manager/insurance/commercial reader, elderly/`PREFERS_HUMAN` flag, or a corrected safety issue the customer should hear by voice; else AUTOMATED_OK | Relationship-bearing close; mirrors Field Service Report Writer's review-request gate. |
| Post-visit care | AUTOMATED_OK | The "quietly brilliant" message; safe to automate, and consistency is the value. |

**Rules:**
- **HUMAN_FIRST** does not mean "don't send the text" — it means a human touch (tech or office) precedes or replaces the automated send for that stage; the automation follows, it does not lead. The drafted message is still produced; the gate governs *who sends it and when*.
- Any `SAFETY_ESCALATION` flag from intake overrides every posture to HUMAN_FIRST for that job and routes per the v1.0 "Do not use for emergency / safety communications" rule.
- A `status_event` produced by an FSM webhook can carry the posture inline: `{stage, send_posture: HUMAN_FIRST|AUTOMATED_OK, reason}` so the automation routes correctly without re-deciding.

**Handoff note:** the completion stage's posture should agree with the Field Service Report Writer's `downstream.review_request.send_posture` for the same job — if the field report set HUMAN_FIRST, the completion status message is HUMAN_FIRST too, and the review request follows the human touch. The three skills speak one hybrid-posture vocabulary so the post-job sequence (status complete → field report → review ask) is coherent end to end.

---

**End of v1.1 additions. The v1.0 stages, principles, and examples remain canonical; the Spanish variant and the send-gate layer on without modifying any v1.0 instruction.**
