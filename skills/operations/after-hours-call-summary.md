---
name: "After-Hours Call Summary"
category: operations
tools: [claude, chatgpt]
difficulty: beginner
time_saved: "~15 min/morning"
version: 2.0
last_eval_score: 9.5
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
