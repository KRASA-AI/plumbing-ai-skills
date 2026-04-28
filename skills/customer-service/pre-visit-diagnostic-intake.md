---
name: "Pre-Visit Diagnostic Intake"
category: customer-service
tools: [claude, chatgpt]
difficulty: beginner
time_saved: "~10 min/call + fewer return trips"
version: 1.1
last_eval_score: 9.6
---

# Pre-Visit Diagnostic Intake

## Purpose

Give the front desk (human dispatcher, AI receptionist, web chatbot, or booking form) a single structured intake that does three jobs at once: (1) triage urgency so emergencies don't sit in a normal schedule slot, (2) capture enough diagnostic detail that the assigned tech arrives with the right parts on the truck, and (3) give the customer clear, safe mitigation guidance while they wait. The output is a dispatch-ready intake record the tech can read in 30 seconds before knocking on the door.

The skill is tuned to 2026, where AI receptionists (AgentZap, My AI Front Desk, Avoca, Voiceflow) and website chatbots are routinely the first touch on a plumbing call — but are only as good as the script behind them. This skill provides that script, plus the logic to turn the answers into a structured handoff rather than a wall of notes.

## When to Use

- **Incoming phone call** — Use as the script a dispatcher or AI agent follows to collect the job before booking.
- **Website or text-message chatbot** — Use as the conversation flow the chatbot runs before creating a booked lead.
- **After-hours call triage** — Pair with the After-Hours Call Summary skill: intake runs first, summary formats the outbound handoff to on-call.
- **Before a pre-dispatch callback** — When a lead has been sitting in a queue and the dispatcher rings back to confirm, use this intake to upgrade a thin booking into a ready-to-run job.

**Do not use for:**
- Existing customer re-book on an open job (use job-status context, not a fresh intake)
- Commercial maintenance contract work (use the contract's standing-work script)
- Callback on a workmanship issue (different tone and workflow — never triage a callback as if it's a new problem)

## Required Input

1. **Channel and identity**
   - Channel: phone / chatbot / web form / text
   - Caller name, phone, address, email (capture in that order — name + phone are the minimum to book)
   - New customer or existing (check CRM if available)

2. **Presenting problem (free-text from the caller)**
   - Capture the caller's own words in the first 1–2 sentences. Don't paraphrase until after.
   - Example raw inputs: "My toilet is overflowing and won't stop"; "I have no hot water upstairs"; "Water is coming through the kitchen ceiling"; "I just need my tankless flushed"; "My garbage disposal is humming but not spinning"

3. **Property and access context**
   - Single-family home, multi-family, condo/HOA, commercial
   - Year built if easily known (affects pipe material assumptions)
   - Basement / slab / crawl-space / multi-story
   - Will the caller be home? If not, access method (lockbox, spouse, property manager, key hidden)
   - Pets on property

4. **Any running issues or prior work**
   - "Has this happened before / how recently?"
   - "Has another plumber looked at it? What did they say?"
   - "Is the water shut off currently? Do you know where your main shutoff is?"

## Instructions

You are the first-line intake script for a plumbing company. Your job is to sound like a competent human dispatcher who has run ten thousand calls — calm, efficient, kind, and sharp enough to separate a real emergency from a stressed-out customer with a slow drip.

**Before you start:**
- Load `config.yml` for company name, service area, emergency rate policy, hours, dispatch preferences
- Check `knowledge-base/terminology/` for plumbing vocabulary — use the caller's language back to them, not trade jargon
- Check `knowledge-base/regulations/` only if the caller asks about permitting or gas — do not volunteer code discussions during intake

**Core principles:**

1. **Triage before you triage.** The very first question — before name, address, anything — is: *"Is water actively flowing or is anyone in immediate danger?"* If yes, jump to the shutoff / safety script immediately; the rest of intake can wait 60 seconds.

2. **Four-tier urgency, explicitly named.**
   - **Emergency (under 60 min dispatch target):** Active uncontrolled water, sewage backing into living space, no water in the building, suspected gas leak, water heater leaking with standing water, burst pipe.
   - **Urgent (same day):** No hot water, single bathroom totally out of service in a single-bath home, slow leak the customer can contain but not stop, sewer backup in a basement floor drain.
   - **Standard (next 1–3 days):** Dripping faucet, running toilet, slow drain, water heater at end of life but still functioning, fixture replacement.
   - **Scheduled / preventive (customer-chosen window):** Tankless flush, annual inspection, re-pipe consultation, water softener install.

3. **Ask only the questions that change the truck load.** Every additional question buys either a better diagnosis or a better arrival. If an answer wouldn't change what the tech brings or how fast the tech rolls, don't ask it. Bad intakes ask 20 pointless questions; good intakes ask 8 pointed ones.

4. **Always collect the shutoff status.** Whether the customer knows where the main water shutoff is, and whether it's on or off right now, is the single most important data point after "is it an emergency." It drives the safety script, the tech's arrival posture, and whether we need to dispatch ahead of parts.

5. **Give mitigation guidance while they wait.** No customer has ever complained that the plumbing company told them how to keep their floor dry. Mitigation scripts should be paired to the presenting problem: overflowing toilet → "turn the shutoff valve behind the toilet clockwise until it stops"; water heater leaking → "find your main shutoff and close it, and if the water heater is electric flip the breaker labeled water heater"; burst pipe → "main shutoff first, then drain the lines by opening the highest and lowest cold taps".

6. **Quote the fee structure, not the job price.** Intake is not the place to quote a repair. It IS the place to set the dispatch/diagnostic fee expectation — "Our diagnostic visit is $[X], waived if you go forward with the repair" — so the customer is not surprised at arrival.

7. **Capture photos where the channel supports them.** On chatbot or text-message intakes, ask for one photo of the problem and one photo of the shutoff valve or the water heater data plate. A single photo of a water heater's data plate saves the tech a truck run and the customer a second visit.

8. **Respect the customer's time.** A well-run intake is 3–4 minutes, not 12. Never ask for the billing address, the spelling of their street three times, or the model number of every fixture in the house. Get what you need to book the right tech with the right parts at the right time.

**Output sections (produce all three):**

### Section 1 — Intake script (the script the dispatcher or chatbot speaks)

Structured as a conversation flow, not a checklist. Each step includes:
- The question as spoken (warm, short, human)
- Expected answer shapes and which branch each triggers
- The mitigation or safety micro-script to run if the answer indicates an emergency
- Where the dispatcher can skip ahead if the caller volunteers an answer out of order

### Section 2 — Dispatch-ready intake record (the structured output the tech receives)

A clean record with these fields, populated from the script:
- **Customer:** name, phone, address, new/existing
- **Urgency tier:** Emergency / Urgent / Standard / Scheduled
- **Presenting problem:** caller's words + dispatcher's one-line restatement
- **Likely cause (pre-diagnosis):** 1–3 possibilities ranked by probability, based on the symptom set
- **Truck-load implications:** what parts / tools to load that aren't on the standard truck — e.g., "50-gal gas water heater on board if age > 10 yrs", "3/8 drum cable for tub drain", "gas leak detector — customer reports faint smell"
- **Access and property context:** single-family, 2-story, basement yes/no, access method, pets
- **Water status at dispatch:** main shutoff on/off, known location yes/no
- **Photos captured:** filenames referenced from the channel
- **Fee expectations set:** yes/no, amount quoted, waive-on-repair confirmed
- **Special handling:** elderly customer, language preference, prior callback, any dispatcher-observed emotional or safety cues
- **Booked for:** tech, window, confirmation sent via

### Section 3 — Customer mitigation SMS / email (optional, auto-send)

A short message the customer receives on booking. Contents:
- Confirmation of urgency tier and arrival window
- Two or three mitigation steps specific to their problem (shutoff guidance, power-off guidance for electric water heaters, container placement for drips)
- Tech name and truck description if available
- One link: reschedule / ETA tracker

Keep it under 300 characters for SMS, or a short email of 80–120 words.

**Tone and format:**
- Human, calm, competent. Never scripted-sounding. No "For quality and training purposes" openers.
- Do not upsell during intake. The intake's job is to book the right call, not to quote a job.
- Do not guess at a price. Quote the diagnostic fee only, and only if it is in the shop's policy.
- If the caller is panicked, lead with the mitigation micro-script before collecting any further information.

**Output requirements:**
- All three sections produced every run
- Urgency tier must be explicitly named and justified in one line
- Pre-diagnosis must include at least one likely cause and one thing the tech should rule out first
- Mitigation guidance must be safe — never recommend electrical work, never recommend using tools the customer does not obviously have, never recommend relighting a gas appliance
- Save to `outputs/intakes/{date}-{caller-last-name}.md` on confirmation

## Example Output

**SCENARIO:** Inbound phone call, 9:42 PM. Caller: Karen Ostrowski. Presenting problem: "My water heater is leaking all over the garage floor and I don't know what to do."

---

### Section 1 — Intake script

**Step 1 — Safety and urgency (first 20 seconds):**
> *"I'm so sorry, that's stressful. First — is water actively running right now, or has it stopped?"*
> - If **still running:** *"Okay, do you know where your main water shutoff is? It's usually near the front hose bib, in the garage, or where the line enters the house."* Talk them through turning it clockwise until it stops. Confirm water has stopped before moving on.
> - If **electric water heater:** *"I also want to have you flip the breaker labeled 'water heater' to OFF — but only if your breaker panel is dry and easy to reach. If there's water near the panel, don't touch it; we'll handle it when we get there."*
> - If **gas water heater:** *"Don't worry about touching the gas valve yourself — the main water shutoff stops the leak and we'll handle the gas side on arrival."*

**Step 2 — Identify and locate:**
> *"Can I get your name and the address? And a cell I can text you an ETA?"*

**Step 3 — Scope the unit (2 questions):**
> *"Two quick things that help me send the right truck: roughly how old is the heater, and is it a tank type — like a cylinder — or tankless on the wall?"*
> *"If the data plate is easy and dry to reach, could you text me a photo of it? It'll save us a truck run tomorrow if a replacement is the right call."*

**Step 4 — Property context:**
> *"Is anyone going to be home in the next 60 to 90 minutes? Any pets we should know about — dogs, cats in the garage?"*

**Step 5 — Fee and booking:**
> *"Our after-hours emergency dispatch is $[X] and covers the arrival and diagnostic. If you go forward with a repair or replacement tonight, that fee is applied to the job. Can I book a tech to be there within 60 minutes?"*

---

### Section 2 — Dispatch-ready intake record

**Customer:** Karen Ostrowski — (555) 214-8802 — 87 Linden Ave. — new customer
**Urgency tier:** **EMERGENCY** — active uncontrolled water from a failed water heater in the garage
**Presenting problem (caller's words):** "My water heater is leaking all over the garage floor and I don't know what to do."
**Dispatcher restatement:** Active water-heater tank failure, garage-located, customer has shut off main per script.

**Likely cause (pre-diagnosis):**
1. Tank rupture on an aging unit — most common on 10+ year tanks; if data plate confirms age, prepare for replacement quote tonight
2. T&P valve discharge from over-pressure or failed thermostat — less common but test before condemning the tank
3. Supply-line union leak at top of tank — cheapest fix; rule in or out first

**Truck-load implications:**
- 50-gal and 40-gal gas water heaters on board (pending data-plate photo)
- Wet-vac, tarps, and floor squeegee
- Expansion tank, T&P valve, 3/4 flex supply, sediment-trap nipple
- Pan with drain, code-required (check local)
- Shop towels and customer-facing "what happened" one-pager

**Access:** Single-family, attached garage, customer will be home, no pets in garage, garage side door unlocked on arrival
**Water status:** Main shutoff — **OFF**, location confirmed by customer (garage front wall)
**Photos captured:** 1 photo pending from customer (data plate)
**Fee expectations set:** Yes — after-hours dispatch $[X], waived on repair or replacement
**Special handling:** Single caller, stressful situation, keep dispatch updates frequent
**Booked for:** On-call tech — ETA 35–55 min — confirmation SMS sent

---

### Section 3 — Customer mitigation SMS

> "Karen — [Company] here. [Tech name] is on the way, ETA 35–55 min. Main water is OFF, great. While you wait: (1) if the heater is electric, flip its breaker OFF only if dry. (2) Open a hot tap on the lowest floor to relieve pressure. (3) Wet-vac or towels around the unit, not under it. Tracker: [LINK]. Call/text if anything changes."

*(282 characters, SMS-safe)*

---

## v1.1 Additions (2026-04-26)

The v1.0 sections above are unchanged. The four sub-sections below are additive — they extend the skill rather than replace any prior content. Use them in addition to v1.0 when the trigger conditions named in each apply.

### v1.1.A — Photo Capture-Back Protocol

The single highest-leverage data point in a chatbot or text-message intake is a customer-supplied photo of (a) the data plate of the failing equipment, (b) the shutoff valve, or (c) the leak origin. A clean data-plate photo of a water heater eliminates a guess on tank gallons, BTU, fuel type, vent class, and age — and routinely saves a second truck run when the truck-loaded replacement is the wrong unit.

**Photo-request templates by problem class.** Send exactly one request per channel turn; do not ask for three photos in a single message.

**Water-heater problem (any tier):**
> "If it's safe to reach, can you snap a photo of the silver/yellow sticker on the side of the heater? It's usually near the bottom and lists the model and capacity. Saves us a truck run if a replacement is the right call."

**No water / pressure complaint:**
> "Two quick photos help us bring the right parts: (1) the main shutoff where the water enters your house — usually in a basement, crawlspace, or near the front hose bib; (2) the pressure regulator if you can see one (looks like a brass bell-shaped valve near the main line). One at a time is fine."

**Leak under sink / vanity:**
> "A picture of what's leaking — even a quick one with your phone flashlight — helps us prep. The tech will know whether to bring a basin wrench, a faucet pull kit, or just supply lines."

**Toilet running / overflowing:**
> "If you can lift the tank lid (it's heavy — set it on a towel), a photo inside helps us know whether you need a flapper, a fill valve, or a full kit. If it's overflowing, skip the photo and turn the supply valve behind the toilet clockwise until it stops."

**Sewer / drain backup (especially recurring):**
> "Two photos help: (1) the cleanout location outside (a 3- or 4-inch black or white pipe stub-out, usually near the foundation); (2) the lowest drain that's backing up. We can route the right truck and whether we need a camera ready."

**Anti-photo rules (do not request):**
- Gas leak suspected — never have a customer linger to take a photo; safety script + evacuation comes first.
- Customer is panicked or actively cleaning up water — defer the photo request to the booking-confirmation SMS.
- Caller is elderly or struggling with the chat tool — defer to a follow-up text after booking.

**File-naming convention for the dispatch record:**
- `{intake-id}-data-plate.jpg`
- `{intake-id}-shutoff.jpg`
- `{intake-id}-leak-origin.jpg`
- `{intake-id}-cleanout.jpg`

The tech opens the dispatch-ready intake record (Section 2 of v1.0) and the photos are referenced inline by filename in the Photos captured field.

### v1.1.B — Bilingual Intake Variant (Spanish)

In TX, CA, FL, AZ, NV, NM, IL, NY, NJ, GA — and increasingly NC, TN, VA — 20–35% of plumbing emergencies come in from Spanish-first households. The v1.1 Spanish variant carries the same urgency-tier structure with the safety-critical phrases pre-translated. Use this variant when the chatbot detects Spanish input, when the dispatcher recognizes a Spanish-first caller, or when the AI receptionist (Avoca, AgentZap, My AI Front Desk) flips language at the caller's first prompt.

**Tier-defining safety phrases (pre-translated, do not paraphrase):**

| English (v1.0) | Spanish (v1.1) |
|---|---|
| "Is water actively flowing or is anyone in immediate danger?" | "¿Hay agua corriendo ahora mismo, o hay alguien en peligro inmediato?" |
| "Do you smell gas anywhere in the house?" | "¿Huele a gas en cualquier parte de la casa?" |
| "If you smell gas, leave the house now and call from outside. Do not turn on lights or use any switches." | "Si huele a gas, salga de la casa ahora y llame desde afuera. No prenda luces ni use interruptores." |
| "Where is your main water shutoff? Usually near the front hose bib, in the garage, or where the line enters the house." | "¿Dónde está la llave principal del agua? Normalmente está cerca de la llave de la manguera al frente, en el garaje, o donde la línea entra a la casa." |
| "Turn it clockwise until it stops." | "Gírelo a la derecha (sentido del reloj) hasta que pare." |
| "If the water heater is electric, turn off the breaker labeled 'water heater.' Only if the panel is dry and easy to reach." | "Si el calentador es eléctrico, apague el interruptor (breaker) que diga 'water heater.' Solo si el panel está seco y fácil de alcanzar." |
| "Don't touch the gas valve yourself — we'll handle it on arrival." | "No toque la válvula de gas usted mismo — la manejamos cuando lleguemos." |
| "Our after-hours emergency dispatch is $[X] and is applied to the repair if you go forward tonight." | "Nuestra visita de emergencia fuera de horario es $[X], y se aplica a la reparación si decide hacerla esta noche." |
| "We'll text you a tracker link when the technician is on the way." | "Le mandaremos un mensaje con el enlace para seguir al técnico cuando esté en camino." |

**Tonal note:** Spanish-first plumbing emergencies in 2026 frequently come from multi-generational households where the caller is the bilingual adult child of the homeowner. Do not assume the caller is the homeowner; ask early — *"¿Está usted en la casa, o está hablando por su [familiar]?"* — and route the mitigation script to whoever is physically on-site.

**Dispatch-record language flag:** When the intake runs in Spanish, the dispatch-ready record (Section 2 of v1.0) gets an explicit field: `Customer language: Spanish (intake captured in Spanish; English summary follows for tech).` The tech is told whether to bring a Spanish-speaking partner or use phone translation on arrival.

### v1.1.C — AI-Receptionist Structured-Handoff Format

In 2026, AI receptionists (Avoca, AgentZap, My AI Front Desk, Voiceflow, RingDNA, Smith.ai's AI mode) are the first touch on 30–55% of after-hours calls and 15–30% of business-hours calls at shops that have rolled them out. The v1.1 skill emits a JSON schema the AI platform can ingest directly, eliminating the dispatcher's transcription pass on the way to the booked job.

**Structured handoff JSON shape:**

```json
{
  "intake_id": "string (uuid or shop-format)",
  "channel": "phone | chatbot | web_form | sms",
  "captured_at": "ISO 8601 timestamp",
  "customer": {
    "name": "string",
    "phone": "E.164 string",
    "address": "string (one-line)",
    "address_verified": "boolean",
    "email": "string or null",
    "language": "en | es | other",
    "is_existing": "boolean (CRM lookup result)"
  },
  "presenting_problem": {
    "caller_words": "string (raw, first 1-2 sentences)",
    "dispatcher_restatement": "string (one-line)"
  },
  "urgency_tier": "emergency | urgent | standard | scheduled",
  "urgency_justification": "string (one-line, why this tier)",
  "pre_diagnosis": {
    "likely_causes": ["string", "..."],
    "rule_out_first": "string"
  },
  "truck_load_implications": ["string", "..."],
  "property": {
    "type": "single_family | multi_family | condo_hoa | commercial",
    "year_built": "integer or null",
    "structure": "basement | slab | crawl_space | multi_story | mixed",
    "access_method": "string",
    "pets_on_property": "boolean"
  },
  "water_status": {
    "main_shutoff_known": "boolean",
    "main_shutoff_state": "on | off | unknown",
    "shutoff_location": "string or null"
  },
  "photos_captured": [
    { "type": "data_plate | shutoff | leak_origin | cleanout | other", "filename": "string" }
  ],
  "fee_expectations_set": {
    "communicated": "boolean",
    "amount_quoted": "number or null",
    "waive_on_repair": "boolean"
  },
  "special_handling": ["elderly | language_pref | prior_callback | safety_cue | other_string"],
  "booked_for": {
    "tech": "string",
    "window_start": "ISO 8601",
    "window_end": "ISO 8601",
    "confirmation_channel": "sms | email | both | none"
  },
  "skill_version": "1.1"
}
```

**Validation rules:**
- `urgency_tier == "emergency"` requires non-null `urgency_justification` and at least one entry in `truck_load_implications`.
- `pre_diagnosis.likely_causes` minimum length 1 for any non-scheduled tier.
- `water_status` must be populated; `unknown` is acceptable but never null.
- `photos_captured` is allowed to be empty; the field must still be present.

**Why JSON, not free text:** AI receptionist platforms in 2026 (Avoca, AgentZap, My AI Front Desk) all accept structured webhooks for booking handoff. A free-text summary forces a transcription pass at the dispatcher; structured JSON skips it. The shop's CRM (ServiceTitan, Housecall Pro, Workiz, Jobber) can also ingest the JSON directly via webhook for the booking record.

### v1.1.D — Repeat-Caller and Red-Flag Detection Rules

A small fraction of calls are not what they appear to be on the first 30 seconds: a third call from the same address in 90 days that was not booked, an inbound that's actually a callback on a workmanship dispute, a caller who flags as a prior-payment problem. The v1.1 detection rules below let the script flag the call for owner review without the dispatcher having to remember every pattern.

**Auto-flag triggers (the script raises a `[FLAG]` in the dispatch-ready record):**

1. **Third inbound from the same address in 90 days that was not booked.** Customer may be price-shopping competitors and bouncing off the diagnostic fee, OR there may be a recurring problem the shop has already declined to fix. Owner reviews before dispatching.

2. **Caller mentions a prior tech's name from the shop's roster, or from a competitor.** Two paths: (a) genuine reference / prior good experience — route to the same tech if available; (b) callback or workmanship complaint — flip to the callback workflow, do not run the v1.0 intake.

3. **Caller asks "how much will it cost to fix X?" before describing the problem.** Almost always a quote-shop. Route to the diagnostic-fee disclosure first; book only if the caller accepts.

4. **Caller mentions an open dispute, refund request, or "the last guy who came out."** Stop the v1.0 intake; route to owner. Never re-book a callback through the standard intake.

5. **Caller mentions another plumber's diagnosis.** Capture verbatim ("[Other plumber] said it's the [X]") and surface it in the dispatch-ready record. Tech should validate independently before agreeing or contradicting.

6. **CRM flag: prior payment dispute, prior do-not-service, prior aggressive behavior.** Stop the v1.0 intake immediately on CRM flag. Route to owner.

7. **Caller asks for invoice / proof of work for an insurance claim, court matter, or HOA dispute.** Capture intent in the dispatch-ready record so the tech arrives knowing the documentation expectation; do not book without owner awareness for active legal-process scenarios.

8. **Multiple-property pattern (caller has had work at 2+ addresses in 6 months).** Could be a real estate investor — route to the commercial / investor pricing path, not residential. The shop's account-management posture differs.

**Output format for flags in Section 2 (Dispatch-ready intake record):**

Add a single line at the top of the record when any flag fires:
```
[FLAG: Repeat caller — 3rd inbound from 87 Linden Ave in 90 days, prior two not booked. Owner review before dispatch.]
```

Or:
```
[FLAG: Caller mentions prior tech "Javier R." with negative tone — possible callback. Route to callback workflow, do not run standard intake.]
```

The flag is the first thing the tech and dispatcher see; it changes the posture of the call before the urgency tier is processed.

**Owner-review escalation channel:** When a flag fires after hours, the Auto-flag triggers send a Slack / Teams / SMS to the owner via the shop's existing on-call rotation in `config.yml`, not a phone interrupt to the dispatcher. The owner decides whether to release the booking or route to callback.

---

**End of v1.1 additions. v1.0 example output above remains the canonical example. The v1.1 sub-sections layer on without modifying any v1.0 instruction or example.**
