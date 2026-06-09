---
name: "After-Hours Call Summary"
category: operations
tools: [claude, chatgpt]
difficulty: beginner
time_saved: "~15 min/morning"
version: 2.2
last_eval_score: 9.7
---

# 📞 After-Hours Call Summary

## Purpose

Turn a batch of overnight voicemails, missed-call logs, and answering-service notes into a prioritized morning briefing. Each call gets triaged by urgency, categorized by job type, and formatted so you (or your dispatcher) can start returning calls in the right order within 60 seconds of reading it.

## When to Use

- **Every morning** — Process the night's voicemails and missed calls before the first tech rolls out
- **After weekends / holidays** — Triage a larger backlog of calls accumulated over multiple days
- **When your answering service sends a batch** — Reformat their notes into your shop's standard triage format
- **When a tech forwards you voice notes** — Consolidate scattered messages into one organized briefing

## Required Input

Provide **one or more** of the following:

1. **Voicemail transcripts or summaries** — Paste the raw text from your phone system, answering service, or AI transcription tool. Include timestamps if available.
2. **Missed-call log** — Phone numbers with timestamps (the AI will note which callers left messages vs. hang-ups)
3. **Answering service notes** — The summary your live or AI answering service captured (caller name, issue, urgency, callback number)
4. **Context** (optional) — Any known details like "we had a water main break on Oak St yesterday" or "tech Marcus is off today"

## Instructions

You are the morning dispatcher for a plumbing company. Your job is to take a pile of overnight calls and turn them into a clean, prioritized action board that the owner or dispatcher can execute immediately.

**Before you start:**
- Load `config.yml` from the repo root for company details, service area, and hours
- Reference `knowledge-base/terminology/` for correct plumbing job-type names
- Note the company's business hours and after-hours policy from config

**Step 1 — Categorize each call by urgency tier**

| Tier | Label | Criteria | Target Response |
|------|-------|----------|-----------------|
| 🔴 | **EMERGENCY** | Active water flow, sewage backup, gas smell, no heat (winter), flooding | Call back within 15 min |
| 🟡 | **URGENT** | No hot water, single toilet/shower out, sump pump concern, slow drain with backup risk | Call back within 1 hour |
| 🟢 | **STANDARD** | Dripping faucet, running toilet, fixture replacement request, estimate request | Call back by end of business |
| ⚪ | **INFO / SPAM** | Vendor call, wrong number, solicitation, existing customer checking on scheduled work | Handle or discard |

**Step 2 — Extract key details from each call**

For every legitimate call, capture:
- **Caller name** (or "Unknown" if not provided)
- **Callback number** — formatted consistently
- **Address** (if provided)
- **Problem description** — translated into standard plumbing terminology
- **Key details** — water shut off? Affecting multiple fixtures? Tenant vs. owner? Insurance involved?
- **Timestamp** — when the call came in
- **Existing customer?** — note if the number matches a known customer (if answering service provides this)

**Step 3 — Flag revenue and scheduling signals**

- 🏷️ **High-value lead** — Whole-home repipe, sewer line, water heater replacement, remodel
- 🔁 **Repeat customer** — If the answering service notes indicate a returning customer
- ⏰ **Time-sensitive** — Customer mentioned a deadline (guests arriving, inspection scheduled, closing date)
- 📋 **Estimate request** — Customer specifically asked for a quote (not an emergency)

**Step 4 — Produce the morning briefing**

**Output format:**

```
═══════════════════════════════════════════════
  MORNING CALL BRIEFING
  [Company Name]  |  [Date]  |  [X] calls overnight
═══════════════════════════════════════════════

📊 QUICK STATS
  Total calls: [X]
  🔴 Emergencies: [X]  |  🟡 Urgent: [X]
  🟢 Standard: [X]     |  ⚪ Info/Spam: [X]
  Estimated revenue potential: $[range]

───────────────────────────────────────────────
🔴 EMERGENCIES — CALL BACK NOW
───────────────────────────────────────────────

  1. [Caller Name] — [Phone Number]
     ⏰ Called: [time]
     📍 Address: [if provided]
     🔧 Issue: [Problem in plumbing terms]
     📝 Details: [Key info — water shut off? Damage?]
     🏷️ [Flags: high-value, repeat customer, etc.]

───────────────────────────────────────────────
🟡 URGENT — CALL BACK WITHIN 1 HOUR
───────────────────────────────────────────────

  [Same format]

───────────────────────────────────────────────
🟢 STANDARD — CALL BACK BY END OF DAY
───────────────────────────────────────────────

  [Same format]

───────────────────────────────────────────────
⚪ INFO / NO ACTION NEEDED
───────────────────────────────────────────────

  [Brief one-liner per call]

───────────────────────────────────────────────
📋 DISPATCHER NOTES
───────────────────────────────────────────────

  - [Any patterns: multiple calls from same area?]
  - [Calls that might be related to each other]
  - [Suggested tech assignments if obvious matches]
  - [Callbacks that need specific info before returning]

═══════════════════════════════════════════════
```

**Important guidelines:**
- Emergency calls always go first, regardless of call order
- If a caller sounds distressed or mentions active water damage, always classify as 🔴 even if the described problem seems minor — water damage escalates fast
- Translate customer language into plumbing terms (e.g., "water is coming up through the floor" → likely sewer backup or slab leak)
- Note when a customer has already shut off their water — this reduces urgency slightly but they still need prompt service
- If two calls reference the same address or issue, flag them as related
- For hang-ups or missed calls with no voicemail, still list them — a 2 AM missed call from a residential number is likely an emergency that went to a competitor

## Example Output

```
═══════════════════════════════════════════════
  MORNING CALL BRIEFING
  Reliable Plumbing  |  Mon 2026-04-13  |  6 calls overnight
═══════════════════════════════════════════════

📊 QUICK STATS
  Total calls: 6
  🔴 Emergencies: 1  |  🟡 Urgent: 2
  🟢 Standard: 2     |  ⚪ Info/Spam: 1
  Estimated revenue potential: $1,200–$6,500

───────────────────────────────────────────────
🔴 EMERGENCIES — CALL BACK NOW
───────────────────────────────────────────────

  1. Maria Gonzalez — (512) 555-0142
     ⏰ Called: 2:47 AM
     📍 Address: 4218 Elm Creek Dr
     🔧 Issue: Active sewer backup — water and waste
        coming up through both floor drains in basement
     📝 Details: Affects entire lower level. Has NOT
        shut off water. Two small children in home.
        Mentioned this happened once before "last winter."
     🔁 Repeat customer — previous backup suggests
        possible line issue (camera inspection opportunity)
     🏷️ High-value: Likely needs jetting + camera,
        possible line repair. Est. $800–$4,500.

───────────────────────────────────────────────
🟡 URGENT — CALL BACK WITHIN 1 HOUR
───────────────────────────────────────────────

  2. James Park — (512) 555-0287
     ⏰ Called: 11:22 PM
     🔧 Issue: No hot water — gas water heater pilot
        won't stay lit after multiple attempts
     📝 Details: 4-person household. Mentioned heater
        is "pretty old." Tried relighting per YouTube.
     🏷️ High-value: Possible replacement candidate.
        Est. $189 (thermocouple) to $3,200 (replacement).

  3. Unknown caller — (512) 555-0391
     ⏰ Called: 5:15 AM
     🔧 Issue: Toilet overflowing, won't stop running.
        Shut off valve at wall. Only bathroom in unit.
     📝 Details: Apartment tenant — needs landlord
        authorization. Has landlord's number ready.

───────────────────────────────────────────────
🟢 STANDARD — CALL BACK BY END OF DAY
───────────────────────────────────────────────

  4. David Chen — (512) 555-0518
     ⏰ Called: 9:45 PM
     🔧 Issue: Kitchen faucet dripping, wants estimate
        for replacement. "No rush."
     📝 Details: Mentioned interest in touchless faucet.
     📋 Estimate request — send scheduling link.

  5. Sarah Williams — (512) 555-0623
     ⏰ Called: 10:30 PM
     🔧 Issue: Wants quote on adding a hose bib to
        the side of the house for garden irrigation.
     📝 Details: New homeowner. Asked about "other things
        we should check" — great whole-home inspection lead.
     🏷️ High-value: Hose bib + potential whole-home
        inspection upsell. Est. $350–$1,200.

───────────────────────────────────────────────
⚪ INFO / NO ACTION NEEDED
───────────────────────────────────────────────

  6. (512) 555-0000 — 8:02 PM — Vendor robocall
     (water heater supplier promo). Discard.

───────────────────────────────────────────────
📋 DISPATCHER NOTES
───────────────────────────────────────────────

  - Maria G. (#1) is a repeat sewer backup — check
    CRM for her previous service history before calling.
    If line was only snaked last time, recommend camera
    this time.
  - James P. (#2) water heater age unknown but "pretty
    old" + pilot issues = replacement conversation.
    Send Marcus (best closer on water heaters).
  - Sarah W. (#5) is a new homeowner asking "what else
    should we check" — perfect whole-home inspection
    candidate. Book with your most consultative tech.
  - 2:47 AM missed call + voicemail from Maria —
    she may have already called another company. Call
    back ASAP to avoid losing the job.

═══════════════════════════════════════════════
```

---

## v2.1 Additions (2026-05-18)

The v2.0 sections above are unchanged. The three sub-sections below are additive — they extend the skill rather than replace any prior content. Use them in addition to v2.0 when the trigger conditions named in each apply.

### v2.1.A — AI-RX Post-Job Overnight Triage Adapter

When the shop runs an AI receptionist on after-hours (Avoca, Pete & Gabi Olivia, ServiceAgent, Trillet, Marlie, ConvoCore, Smith.ai AI, Sameday, or shop-specific), the overnight call stream now arrives as structured JSON rather than a voicemail batch. The v2.1.A adapter consumes that JSON and emits the same morning briefing output — but with an additional triage layer that surfaces AI-RX-handled calls separately from voicemails and missed calls, so the morning dispatcher can see at a glance which calls the AI already booked, which it queued for human follow-up, and which were dropped (scope-limit miss).

**Trigger:** When invoked with input prefix `[AI-RX-OVERNIGHT]` or a JSON payload with `platform` field, layer the v2.1.A output blocks on top of the v2.0 morning briefing.

**AI-RX overnight-batch input schema (consumed by this skill, produced by AI-RX platforms per the Pricebook Q&A v2.2.A canonical schema):**

```json
{
  "batch_id": "AHC-<uuid>",
  "platform": "avoca | pete_gabi | service_agent | trillet | marlie | convocore | smith_ai | sameday | shop_custom",
  "shop_id": "<shop slug from config>",
  "window_start": "<ISO-8601>",
  "window_end": "<ISO-8601>",
  "calls": [
    {
      "call_id": "<uuid>",
      "received_at": "<ISO-8601>",
      "caller_name": "<string or null>",
      "callback_number": "<E.164>",
      "address": "<string or null>",
      "problem_description_raw": "<verbatim transcript snippet>",
      "problem_description_normalized": "<plumbing-terminology version>",
      "urgency_tier_ai_assigned": "EMERGENCY | URGENT | STANDARD | INFO",
      "ai_disposition": "BOOKED | QUEUED_FOR_HUMAN | SCOPE_LIMIT_TRANSFER | DROPPED",
      "booking_window": "<string or null>",
      "transfer_reason": "<string or null when SCOPE_LIMIT_TRANSFER>",
      "customer_language": "en | es | pt | vi | other",
      "existing_customer": <boolean>,
      "estimated_ticket_value_band": "<low-high range or null>",
      "transcript_url": "<URL or null>",
      "audio_url": "<URL or null>"
    }
  ]
}
```

**Note on customer_language allowed values:** The `en`, `es`, `pt`, `vi` set matches the values added by Review Request Drafter v2.4.C (2026-05-11). When the AI-RX platform doesn't yet support pt or vi, the field will arrive as `en` or `es` — the v2.1.A adapter does not back-fill or guess.

**New output blocks added to the v2.0 morning briefing:**

Insert a new section between the QUICK STATS block and the EMERGENCIES block:

```
───────────────────────────────────────────────
🤖 AI-RX OVERNIGHT — what the AI already handled
───────────────────────────────────────────────

  ✅ BOOKED (no action — confirm in CRM at 8 AM)
     1. [Caller Name] — [Phone]
        ⏰ Called: [time]  |  📍 [Address]
        🔧 Issue: [Normalized problem]
        📅 Booked window: [window]
        💰 Est. ticket value: $[range]

  📤 QUEUED FOR HUMAN (call back in priority order)
     2. [Caller Name] — [Phone]
        ⏰ Called: [time]
        🔧 Issue: [Normalized problem]
        📝 Why queued: [Why AI did not book — e.g., commercial estimate,
                       Spanish call when AI scope is English-only,
                       repair-vs-replace conversation, etc.]

  🚨 SCOPE-LIMIT TRANSFER (review the AI's routing rule)
     3. [Caller Name] — [Phone]
        ⏰ Called: [time]
        🔧 Issue: [Normalized problem]
        🚪 Transfer reason: [Why AI escalated]
        📊 Pattern: [Is this an isolated event or a routing-rule issue?]

  📵 DROPPED (call back, investigate why call ended)
     4. [Caller Name] — [Phone]
        ⏰ Called: [time]
        🔧 Issue: [Last known intent before drop]
        ⚠️ Investigation: [hang-up vs. AI confusion — flag for CSR Perf Debrief]
```

After the existing DISPATCHER NOTES block, insert:

```
───────────────────────────────────────────────
🤖 AI-RX OVERNIGHT METRICS (this batch)
───────────────────────────────────────────────

  AI calls handled:           [N]
  ↳ Booked by AI:             [N] ([%])
  ↳ Queued for human:         [N] ([%])
  ↳ Scope-limit transfer:     [N] ([%])
  ↳ Dropped:                  [N] ([%])

  Est. AI-booked revenue:     $[range]
  Est. queued revenue:        $[range]
  Est. revenue at risk (dropped): $[range]

  Routing-rule diagnostic:    [CALIBRATED | EXPAND AI WINDOW |
                               TIGHTEN AI SCOPE | REVIEW SPECIFIC CALL TYPES]
```

**Routing-rule diagnostic — auto-generate from the batch metrics (mirrors the CSR Performance Debrief v1.1.B rule so the two skills speak the same language):**

1. **CALIBRATED** — Scope-limit transfer rate ≤ 5% AND dropped rate ≤ 3%. No routing change needed.
2. **EXPAND AI WINDOW** — Booked rate ≥ shop's daytime human-CSR booked rate AND scope-limit ≤ 5%. Recommend extending AI-handled hours.
3. **TIGHTEN AI SCOPE** — Scope-limit transfer rate > 8% OR dropped rate > 6%. Recommend narrowing AI scope (e.g., AI handles after-hours intake-only; transfers all booking attempts to a morning human callback).
4. **REVIEW SPECIFIC CALL TYPES** — One or more job types underperform their expected booking rate by ≥ 20pp. Flag for a follow-up CSR Performance Debrief comparison block.

### v2.1.B — Programmable-Scope-as-Guardrail Pattern Note

The Superior Plumbing "Piper" case study (ServiceTitan / Feb 2026) achieved 67% close rate and reduced 7 CSR equivalents to 3 FT + AI by *tightly constraining* what the AI could attempt. The v2.1.B section formalizes the programmable-scope design pattern so a shop running this skill can use the morning briefing as the empirical evidence loop on whether the AI's current scope is correctly calibrated.

**The pattern (one paragraph for the morning briefing reader):**

> An AI receptionist is most effective when its scope is narrower than a senior human CSR's, not when it tries to match it. Calls outside its programmed scope route to a human callback. The morning briefing surfaces scope-limit transfers as the empirical signal on whether the scope is correctly drawn — too few transfers and the AI is over-reaching (look for dropped calls and low booking rates on the call types it shouldn't have attempted); too many transfers and the scope can probably be widened safely (look for transfer reasons that are routine call types the AI handles fine in other shops).

**Output addition — append to the AI-RX OVERNIGHT METRICS block when the routing diagnostic is TIGHTEN AI SCOPE or REVIEW SPECIFIC CALL TYPES:**

```
SCOPE-CALIBRATION NOTE
The Superior Plumbing pattern (ServiceTitan / Feb 2026): tight scope +
named teammate ("Piper" / "Olivia" / your-AI-name) consistently beats
broad scope + un-named AI. Three actions if the diagnostic is TIGHTEN:
  1. Add the most-frequent transfer reason as an explicit out-of-scope rule
     in the AI platform configuration.
  2. Re-record the AI's after-hours greeting to set caller expectations
     ("If you need a price quote on commercial work tonight, [AI name]
     will queue your callback for [human CSR name] in the morning").
  3. Run this skill again in 2 weeks; the transfer rate on that call type
     should fall below 5%.
```

**Cross-skill reference:** The CSR Performance Debrief v1.1.B AI-vs-Human comparative block consumes this skill's AI-RX OVERNIGHT METRICS payload as one of its inputs. The two skills produce a coherent picture: this skill answers "what did the AI do overnight" and CSR Performance Debrief answers "how did the AI's performance on a given call type compare to the human CSR's performance on the same call type." Together they close the AI-RX calibration feedback loop without requiring the office manager to manually correlate the two reports.

### v2.1.C — Customer-Language Routing for Multilingual Overnight Calls

The bilingual thread now spans four languages (English, Spanish, Brazilian Portuguese, Vietnamese) per the Review Request Drafter v2.4.C ship on 2026-05-11. The v2.1.C addition makes the morning briefing surface the language of each call so the dispatcher knows which bilingual CSR (or which translated callback script) to use without listening to the voicemail first.

**Trigger:** Apply whenever the `customer_language` field is present in the AI-RX overnight batch, OR when voicemail transcripts contain a non-English segment ≥ 5 seconds in length.

**Output addition — append to each call entry in every triage block:**

```
  🗣️ Language: [en | es | pt | vi | other — confidence:high/medium/low]
  ↳ Recommended callback: [Bilingual CSR name from config / translated script ID]
```

**Don't-auto-detect-from-name rule (consistent across the bilingual thread):** Do NOT infer the customer's preferred language from their name. The name "Martinez" is not a Spanish-preference signal — many Martinezes prefer English and will be insulted by a Spanish callback they did not ask for. Only use:

- An explicit `customer_language` field from the AI-RX platform (highest confidence).
- A non-English voicemail segment ≥ 5 seconds (medium confidence; flag as such).
- An existing customer's stored language preference from prior calls in the CRM (high confidence when set; do not back-fill from name).

When confidence is medium, the recommended callback line reads: `"Try [bilingual CSR] in [language]; revert to English if customer answers in English"` rather than committing to the language. When confidence is low or absent, default to English with the bilingual CSR on standby. This protects against the over-correction failure mode where shops with good bilingual posture insult bilingual-but-English-preferred customers.

**Cross-skill reference:** When the language is `es`, `pt`, or `vi`, the recommended callback maps to the Review Request Drafter v2.4.C bilingual templates for the corresponding language and the Pre-Visit Diagnostic Intake v1.1 (v1.2 in flight) bilingual intake fields. The morning briefing thus seeds the downstream multilingual handoff for the day.

---

**End of v2.1 additions. v2.0 example output above remains the canonical example. The v2.1 sub-sections layer on without modifying any v2.0 instruction or example. Eight-cycle additive-only streak holds on this skill (v1.0 → v2.0 was a structural rewrite shipped 2026-04-14; v2.0 → v2.1 returns to the additive-only pattern).**

---

## v2.2 Additions (2026-06-08)

The v2.0 and v2.1 sections above are unchanged. The single sub-section below is additive. It applies the repo-wide hybrid-posture calibration framing (06-01 Remaining Opportunities #1, the highest-priority next-cycle target; canonical source: Pricebook Q&A v2.3.A) to this skill's AI-RX overnight adapter. After-Hours Call Summary is the most natural home for the framing because its entire domain *is* the after-hours / overflow window — the exact deployment modes the hybrid-posture thesis says AI-RX is right for. Use it in addition to v2.1 when the AI-RX overnight batch is present.

### v2.2.A — Hybrid-Posture Mode on the AI-RX Overnight Batch

The Blanchard / ServiceForge counter-thesis (Contractor Magazine, May 12 2026 — ~1 in 3 homeowners hang up when AI answers; 78% prefer human-answering when reviews are comparable) is often read as an argument against AI-RX. The hybrid-posture reframing (06-01 monitor cycle) is the opposite: it says AI-RX is *right* for after-hours and overflow and *wrong* as a business-hours default — which means the overnight batch this skill processes is squarely in AI-RX's strong zone. v2.2.A makes the morning briefing surface, per call, which posture mode the AI-RX ran in and whether it correctly escalated a caller who asked for a human, so the owner can confirm the AI is firing and transferring in the right places.

**Trigger:** When the v2.1.A AI-RX overnight batch is present, consume the two new per-call fields below if the platform emits them; when the platform does not yet emit them, default `hybrid_posture_mode` to `AFTER_HOURS` (the structurally correct mode for an overnight batch) and treat absent escalation data as none.

**Input schema addition to the v2.1.A overnight-batch call object:**

```json
{
  "hybrid_posture_mode": "AFTER_HOURS | OVERFLOW | BUSINESS_HOURS_OVERRIDE",
  "human_available": false,
  "escalation_to_human": false,
  "escalation_reason": "PREFERS_HUMAN | SAFETY_ESCALATION | COMPLEX_INTAKE | null"
}
```

The modes and escalation reasons carry the canonical meaning from Pricebook Q&A v2.3.A and Pre-Visit Diagnostic Intake v1.2.B. For an overnight batch, `AFTER_HOURS` is the dominant mode; `OVERFLOW` appears when the daytime window bleeds into a surge; `BUSINESS_HOURS_OVERRIDE` should be rare-to-absent in a *night* batch and, if present, is itself worth a dispatcher note.

**New disposition added to the v2.1.A `ai_disposition` enum:**

```json
"ai_disposition": "BOOKED | QUEUED_FOR_HUMAN | SCOPE_LIMIT_TRANSFER | PREFERS_HUMAN_TRANSFER | DROPPED"
```

`PREFERS_HUMAN_TRANSFER` is distinct from `SCOPE_LIMIT_TRANSFER`: the caller was inside the AI's scope but explicitly asked for a person (or hit a safety escalation). This is a *correct* transfer, not a scope miss — and separating the two keeps the routing-rule diagnostic honest (a `PREFERS_HUMAN_TRANSFER` should never count against the AI's scope calibration).

**New output block — insert inside the 🤖 AI-RX OVERNIGHT section, after the SCOPE-LIMIT TRANSFER group:**

```
  🙋 PREFERS-HUMAN / SAFETY TRANSFER (the AI correctly handed off)
     5. [Caller Name] — [Phone]
        ⏰ Called: [time]
        🔧 Issue: [Normalized problem]
        🤝 Why transferred: [PREFERS_HUMAN — caller asked for a person |
                            SAFETY_ESCALATION — gas/active-hazard script ran]
        ✅ Correct handoff — count as an AI win, not a scope miss.
        📞 Morning action: confirm the overnight on-call actually picked up;
           if the transfer dropped to voicemail, this is a call-back-NOW lead.
```

**Addition to the 🤖 AI-RX OVERNIGHT METRICS block:**

```
  ↳ Prefers-human / safety transfers: [N] ([%])   ← correct handoffs, not scope misses

  Posture-mode mix this batch:
    AFTER_HOURS:            [N]
    OVERFLOW:              [N]
    BUSINESS_HOURS_OVERRIDE: [N]   ← if >0 in a NIGHT batch, flag for review
```

**Routing-rule diagnostic adjustment (refines the v2.1.A rule):**

- **Exclude `PREFERS_HUMAN_TRANSFER` and `SAFETY_ESCALATION` from the scope-limit transfer rate.** The v2.1.A CALIBRATED / TIGHTEN-SCOPE thresholds are computed on *scope-miss* transfers only. A shop whose AI correctly transfers every caller who asks for a person should read as CALIBRATED, not TIGHTEN-SCOPE. Mixing the two would punish the AI for doing the right thing.
- **A high `PREFERS_HUMAN_TRANSFER` rate (>20% of AI calls) is a positioning signal, not a scope signal.** It usually means the after-hours greeting is making callers feel they reached "just a robot." The fix is the v2.1.B named-teammate greeting ("you've reached Olivia, [Company]'s after-hours assistant — I can book your emergency right now or get a person on for you"), not narrowing the AI's scope. Surface this as a SCOPE-CALIBRATION NOTE variant when the rate crosses the threshold.

**Hardening rules (inherited from Pricebook Q&A v2.3.A):**

- **Mode is per-call, not per-shop.** The briefing reports the mix; it does not assume one mode for the batch.
- **`PREFERS_HUMAN` and `SAFETY_ESCALATION` transfers are always correct handoffs.** Never recommend tightening AI scope to reduce them.
- **The mode field flows in from upstream.** Pre-Visit Diagnostic Intake v1.2.B sets the mode and escalation at first touch; this skill reports it at the morning review. The two skills close the loop: intake decides the posture in the moment, the briefing audits whether the posture was right overnight.

**Cross-skill reference:** The CSR Performance Debrief v1.1.B AI-vs-Human comparative block should likewise exclude `PREFERS_HUMAN_TRANSFER` and `SAFETY_ESCALATION` from any AI scope-miss comparison; the two skills already share the routing-rule vocabulary, and v2.2.A keeps them aligned on the corrected definition.

---

**End of v2.2 additions. v2.0 example output above remains the canonical example. The v2.1 and v2.2 sub-sections layer on without modifying any prior instruction or example.**
