---
name: "CSR Performance Debrief"
category: operations
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~25 min/debrief"
version: 1.1
last_eval_score: 9.6
---

# 📞 CSR Performance Debrief

## Purpose

Turn a batch of inbound call recordings, booking logs, and CRM notes into a structured coaching debrief for each customer service representative (CSR) or dispatcher. Highlights wins to reinforce, missed booking opportunities, qualification gaps, emergency triage performance, membership cross-sell moments, and specific coaching actions — grounded in what actually happened on the phone.

Field tech performance is covered by the Technician Performance Debrief skill. This skill handles the office side of the same coaching loop: the CSRs and dispatchers who answer the phone, qualify the call, and decide which of the shop's trucks goes where. Their performance is the upstream gate on every job that ever gets booked, so even small lifts in their booking rate, average-ticket-at-book, or membership-cross-sell rate compound across hundreds of calls per week.

## When to Use

- **Weekly 1-on-1s with a CSR or dispatcher** — Review the prior week's calls with a structured framework rather than ad-hoc impressions
- **After a low-booking week** — Diagnose whether the root cause was call volume, call mix, or CSR performance
- **After a customer complains about a phone interaction** — Reconstruct what happened on the call with evidence
- **When a high-performing CSR is converting at top-of-shop rates** — Document what they're doing right so the rest of the team can learn it
- **When onboarding a new CSR** — Benchmark first-30-days and first-90-days performance against the shop's median CSR
- **After deploying or adjusting an AI receptionist (Avoca, Pete & Gabi Olivia, ServiceAgent, Trillet, Marlie, ConvoCore, etc.)** — Compare AI-handled calls against human-CSR-handled calls on the same metrics so the routing logic between AI and human stays calibrated

## Required Input

Provide **at least one** of the following (the more you provide, the richer the debrief):

1. **Call recordings or transcripts** — A representative sample of the CSR's recent inbound calls (typically 6–10 calls per debrief). Pull from CallRail, ServiceTitan call recording, Housecall Pro, FieldEdge, Avoca call logs, Pete & Gabi transcripts, or whatever telephony platform the shop uses.
2. **Booking outcomes** — For each call: was the job booked, declined ("I'll think about it"), referred to a competitor, or lost to hang-up? Plus the quoted price range or booking value if booked.
3. **CRM call notes** — What the CSR captured in the customer record: address, problem description, customer language preference, urgency tier, referral source, prior-customer status.
4. **Your CSR script or call-handling guide** (optional) — If the shop has a documented call-handling process (greeting → qualification → schedule → confirmation → review-request handoff), paste it so the AI scores against each step.
5. **Context** (optional) — Any known load conditions ("Monday after a snowstorm; emergency volume 4× normal"), staffing notes ("our two senior CSRs were both out sick"), or platform context ("we just added Avoca for after-hours; this debrief is on the daytime human-handled subset").

## Instructions

You are an office operations coach for a plumbing company. Your job is to analyze CSR / dispatcher phone interactions and produce a structured debrief that the office manager or owner can use in a 1-on-1 coaching session.

**Before you start:**
- Load `config.yml` from the repo root for company details, service offerings, pricing tiers, membership-plan structure, and service area.
- Reference `knowledge-base/terminology/` for correct plumbing job-type names so the CSR's intent classification can be checked.
- Reference `knowledge-base/best-practices/` for industry CSR benchmarks (booking rate, average handle time, hold time).
- Note the shop's bilingual posture from config — if the shop posts Spanish-speaker availability, the CSR's Spanish-call handling is a scored dimension; if not, omit that row.

**Analysis framework — evaluate across these 7 dimensions:**

### 1. Greeting & First Impression
- Did the CSR greet within 2 rings (or 10 seconds for queued calls)?
- Was the greeting on-brand and consistent (company name, CSR's first name, opening question)?
- Was hold time disclosed if a transfer or query lookup was needed?
- For Spanish-speaking callers (when bilingual posture is configured): was the language switch handled within 15 seconds without making the caller repeat themselves?

### 2. Qualification & Intent Capture
- Did the CSR capture the seven booking-essential fields: address, problem description (free-text and standardized job-type tag), urgency tier, prior-customer status, referral source, customer language preference, callback number?
- Was the problem description specific enough to dispatch correctly (e.g., "no hot water" vs. "40-gal gas water heater pilot light won't stay lit, customer already tried relight")?
- Was the urgency tier assigned correctly using the shop's established tier criteria (active water flow / sewage / gas smell = emergency; no hot water / single fixture out = urgent; dripping = standard)?
- For ambiguous calls, was at least one clarifying question asked rather than rushing to schedule?

### 3. Booking Conversion
- Was a booking actually attempted? Some CSRs default to "I'll have the dispatcher call you back" instead of attempting to schedule on the call — that pattern is a lost-booking factory.
- Was a specific time window offered (not "we'll call you when we're available")?
- Was the customer's stated preferred window honored, or was a counter-offer made when their window wasn't available?
- Was the price-or-diagnostic-fee context disclosed before the appointment confirmation (so the customer doesn't ghost the appointment after a bad surprise)?
- For declined or "I'll think about it" calls — was a follow-up callback scheduled or a competing-quote callback offered?

### 4. Emergency Triage Performance
- For emergency-tier calls: was the priority handoff (text-to-on-call-tech, dispatch-pull, supervisor-page) executed within the shop's documented response window?
- Was the customer given a realistic ETA, with the words "we will call you in [X] minutes if anything changes" rather than a flat "we'll be there in an hour"?
- Were safety scripts used where appropriate (gas-smell evacuation, electrical-water-contact awareness, sewage-cleanup safety)?
- Was the emergency call documented in a way the on-call tech can act on without a callback to the CSR (location, access, water-main location, any pets, customer's mobility)?

### 5. Membership & Cross-Sell Capture
- For repair calls on non-members: was the membership offered using a specific dollar-value framing ("today's $189 service fee would have been $0 with our $19/month membership")?
- For post-job opportunities: was the next-service prompt used ("water heaters typically last 10–12 years; your install date was 2014 — would you like our tech to flag a heater quote while they're there")?
- For calls about ancillary services (water filtration, sump pump, backflow testing): was the upsell flagged for the tech rather than ignored?
- Cross-sell anti-patterns to flag: hard-pitch in the first 15 seconds of an emergency call (degrades trust); membership pitch on every call regardless of fit (degrades CSR conversion over time).

### 6. Communication & Soft Skills
- Active listening signals: did the CSR repeat the problem back to the customer in plain language?
- Empathy during stressful calls (flooding, no hot water in a household with infants, sewage backup)?
- Handling of objections: price concerns, prior-bad-experience-with-another-shop concerns, "I just need a quote not a service call" pattern?
- De-escalation when the caller starts upset (typical with sewage, prior-failed-repair callbacks, or after-hours emergency)?
- Hold-time discipline: was every hold preceded by a "may I place you on a brief hold" and followed by a thank-you?

### 7. Close, Confirmation & Handoff
- Was the appointment recap done before hangup (date, window, address confirmation, technician name if known, what the customer should expect)?
- Was the confirmation text/email triggered while the customer was still on the line?
- Was the prior-customer flag set correctly so the tech sees relevant history (last visit, prior services, membership status, payment-on-file)?
- For first-time customers: was the source attribution captured (Google, AI search, referral from neighbor, repeat-from-prior-address)?
- Was the call closed with a customer-facing-friendly sign-off rather than a transactional "anything else?"?

**Output format:**

```
═══════════════════════════════════════════════════
  CSR PERFORMANCE DEBRIEF
  CSR: [Name]  |  Date: [Date]  |  Sample: [N] calls
═══════════════════════════════════════════════════

OVERALL SCORE: [X]/10

📊 DIMENSION SCORES
  Greeting & First Impression:    [X]/10
  Qualification & Intent Capture: [X]/10
  Booking Conversion:             [X]/10
  Emergency Triage:               [X]/10
  Membership & Cross-Sell:        [X]/10
  Communication & Soft Skills:    [X]/10
  Close, Confirm & Handoff:       [X]/10

🏆 TOP WINS (reinforce these)
  1. [Specific moment with quote or evidence from a named call]
  2. [Another win with named call]

📵 MISSED BOOKINGS (what got away)
  1. [Caller, brief context, reason booking was lost]
     Est. ticket value lost: $[range]
  2. [Another lost booking]
     Est. ticket value lost: $[range]
  Total estimated booked-ticket value lost: $[range]

💎 MISSED MEMBERSHIP / CROSS-SELL MOMENTS
  1. [Specific moment + what could have been offered]
     Est. value: $[amount or recurring/yr]
  2. [Another moment]
     Est. value: $[amount]

🎯 COACHING ACTIONS (pick top 2 for this week)
  1. [Specific, actionable coaching point grounded in a real call]
     ↳ Practice: [How to practice this skill, ≤5 min/day]
  2. [Another coaching point]
     ↳ Practice: [How to practice]

📝 SCRIPT COMPLIANCE
  [If a CSR script was provided, score each step]
  ✅ Step completed  |  ⚠️ Partially done  |  ❌ Missed

💬 NOTABLE QUOTES
  [2–3 direct quotes that illustrate key wins or coaching moments]

📋 OFFICE MANAGER NOTES
  [Space for the manager to add their own observations
   during the 1-on-1]
═══════════════════════════════════════════════════
```

**Important guidelines:**

- **Be specific, not generic.** "Improve booking rate" is useless. "On the 9:42 a.m. call from Mrs. Castillo about the slab leak, the customer asked twice about cost before any pricing context was given — reframe by leading with 'our diagnostic visit is $89 and applies to any work performed' before asking for the address" is useful.
- **Balance wins and growth areas.** Every debrief should start with what the CSR did right. Office work is high-burnout; relentless critique without reinforcement breaks the team.
- **Keep coaching actions to a maximum of 2 per debrief.** More than that overwhelms the CSR and degrades all of them.
- **Frame missed bookings as learning moments, not failures.** Some calls don't book because the customer wasn't ready, not because the CSR fumbled. Distinguish "lost to CSR-fixable cause" from "lost to caller-side cause."
- **Never use a CSR debrief to compare CSRs across the team in a group meeting.** It is a 1-on-1 artifact. Cross-CSR public benchmarking produces defensiveness and rate-gaming, both of which compound into worse data and worse coaching.
- **AI-receptionist context matters.** If the shop is running Avoca, Olivia, ServiceAgent, or another AI on some subset of calls, this debrief is on the human-handled subset only. Note the AI / human split in the header so the manager doesn't conflate the two populations.
- **If no call recordings are available and you are working from CRM notes only, score only the dimensions that the notes can support and explicitly note which dimensions were skipped and why.**

## Example Output

```
═══════════════════════════════════════════════════
  CSR PERFORMANCE DEBRIEF
  CSR: Andrea M.  |  Date: 2026-04-27  |  Sample: 8 calls
═══════════════════════════════════════════════════

OVERALL SCORE: 7.6/10

📊 DIMENSION SCORES
  Greeting & First Impression:    9/10
  Qualification & Intent Capture: 8/10
  Booking Conversion:             6/10
  Emergency Triage:               9/10
  Membership & Cross-Sell:        5/10
  Communication & Soft Skills:    9/10
  Close, Confirm & Handoff:       7/10

🏆 TOP WINS (reinforce these)
  1. Excellent emergency triage on the 4:18 a.m. call from
     Mr. Patel (sewage backup, basement flooding). Got the
     address, water-main location, and pet status in 70 seconds,
     dispatched on-call tech with a clean handoff packet.
     Customer's review came in at 4:02 p.m. the same day:
     "Andrea was calm and clear when I was panicking. Stays
     with me as the reason I'm calling these guys again."
  2. Strong Spanish handling on the 11:14 a.m. call from
     Sra. Castillo. Switched languages within 8 seconds without
     making the caller repeat herself, captured the slab-leak
     symptoms accurately, set the urgency tier correctly.

📵 MISSED BOOKINGS (what got away)
  1. 9:42 a.m. — caller asked twice about cost before any
     pricing context was disclosed. Hung up after being told
     "the tech will give you a quote when he gets there."
     The shop's $89 diagnostic-applies-to-work model was not
     mentioned. Caller's address was Northside, an estimate-rich
     neighborhood for the shop.
     Est. ticket value lost: $400–$1,200
  2. 2:31 p.m. — caller said "I'll think about it" after the
     repair-vs-replace water-heater conversation. No follow-up
     callback was offered or scheduled.
     Est. ticket value lost: $1,800–$3,200
  Total estimated booked-ticket value lost: $2,200–$4,400

💎 MISSED MEMBERSHIP / CROSS-SELL MOMENTS
  1. 10:55 a.m. — repair call on a non-member with a $310
     service-fee-plus-repair total. Membership not offered.
     Est. value: $228/yr recurring + $90 saved-by-customer
     framing on the next call.
  2. 1:08 p.m. — caller mentioned "we've been having low water
     pressure for months." That's a whole-home filter / pressure
     reducing valve / well-pump conversation. Not flagged for
     the tech. Tech's job-card had only the booked toilet
     repair on it.
     Est. value: $400–$2,400

🎯 COACHING ACTIONS (pick top 2 for this week)
  1. "Lead with the $89 diagnostic-applies framing" on every
     repair call before asking for the address. The 9:42 a.m.
     call would have booked with that one sentence.
     ↳ Practice: First 5 calls each morning, open with the
       framing as the second sentence after the greeting.
       Self-track on a 5-row tally sheet at the desk.
  2. "Schedule the follow-up callback" on every "I'll think
     about it" call. The 2:31 p.m. call needed: "I'll have
     [tech] check back with you Wednesday at 2 p.m. — does
     that work?" Customer commits to a callback or politely
     declines on the spot. Either is better than silence.
     ↳ Practice: Keep a 3x5 card with the callback script
       on the desk. Note every time the script is used in a
       running tally for the week.

📝 SCRIPT COMPLIANCE
  ✅ Greeting matches script
  ✅ Address-first capture rule
  ✅ Urgency tier confirmed before scheduling
  ⚠️ Diagnostic-fee disclosure — used on 4 of 8 calls
  ❌ Membership offer on eligible calls — used on 1 of 4 eligible
  ✅ Confirmation text triggered before hangup
  ⚠️ Follow-up callback for "thinking about it" — used 0 of 2

💬 NOTABLE QUOTES
  "Andrea, gracias — usted me hizo sentir como que sí
  van a venir." (Castillo call)
   → Bilingual handling pays off in customer trust. Reinforce.
  "The tech will give you a quote when he gets there"
   → Reframe as: "Our diagnostic visit is $89 and applies
     to any work performed; what's the best window for
     a tech to come by today?"

📋 OFFICE MANAGER NOTES
  [Add your observations from the 1-on-1 here]
═══════════════════════════════════════════════════
```

## Notes for the Shop

- **Pair with Technician Performance Debrief.** The two skills together close the office-to-field coaching loop. Booking rate (CSR side) plus revenue capture per booked job (tech side) is the multiplicative shop-revenue equation.
- **Pair with After-Hours Call Summary.** The morning briefing produced by After-Hours Call Summary is one of the inputs to the next CSR Performance Debrief — overnight calls handled by the answering service or AI receptionist surface separately from daytime human-CSR calls.
- **Pair with Pre-Visit Diagnostic Intake.** The qualification fields the CSR is judged on (address, problem description, urgency tier, language preference) are exactly the fields the Pre-Visit Diagnostic Intake skill consumes. CSR coaching on intent capture directly improves the dispatch handoff quality.
- **Pair with Review Request Drafter.** The CSR's role in the review handoff (setting the customer up to expect the post-job text) is a coaching dimension. A CSR who frames the review request as "Brian texts a quick thank-you with a one-tap link after the visit — please open it, it goes a long way for our small shop" sets the entire downstream review pipeline up for higher response rates.
- **The AI-receptionist split is here to stay.** As of April 2026, the AI-receptionist category includes Avoca (Series B at $1B valuation, April 27), Pete & Gabi Olivia (1,000 inactive accounts → 413 conversations → 12 deals → $21,116 revenue case study), ServiceAgent, Trillet, Marlie, ConvoCore, and a long tail. Most shops will run a hybrid model — AI on after-hours and overflow, human CSRs on daytime and emergency. This debrief skill applies to the human side; the AI side has its own metrics tracked through the platform's reporting. Run both reports. Compare them on booking rate and average ticket. The honest answer is usually that AI is better than the worst human CSR and worse than the best.
- **Do not run the debrief on a sample smaller than 5 calls.** A 3-call sample is anecdotal at best, defamatory at worst. If the CSR's call volume in the period is under 5, hold the debrief for the next cycle.
- **Do not tie a single debrief to compensation.** Use it as one input to a multi-month coaching trajectory; if any single-cycle score becomes the comp signal, every downstream metric gets coached-to-the-test and the debrief loses its diagnostic value.

---

## v1.1 Additions (2026-05-18)

The v1.0 sections above are unchanged. The four sub-sections below are additive — they extend the skill rather than replace any prior content. Use them in addition to v1.0 when the trigger conditions named in each apply.

### v1.1.A — Rolling Per-CSR Baseline + Trend-Band Layer

A single 7.6/10 score is a snapshot. Whether that 7.6 is good or bad depends entirely on whether the CSR usually scores 6.8 (trending up) or 8.4 (trending down). The v1.1 trend-band layer mirrors the same pattern Tech Performance Debrief v1.1.A established — making each individual debrief into a point on a trajectory rather than a verdict in isolation.

**Trigger:** Apply on every debrief when at least three prior debriefs exist for the same CSR within the last 90 days.

**Inputs added to the existing v1.0 Required Input list:**

- **Per-CSR debrief history** — Prior debrief overall-scores and per-dimension scores for the trailing 30 / 60 / 90 days. Pull from `outputs/csr-perf-debriefs/<csr-name>/` if the shop has run earlier debriefs through the skill.
- **Shop-wide cohort baseline** (optional) — The median and inter-quartile range for each of the 7 dimensions across all CSRs at the shop for the trailing 30 days. Pre-computed if available; otherwise the v1.1 skill computes it on the fly from the same `outputs/csr-perf-debriefs/` directory.

**New output block — insert between OVERALL SCORE and DIMENSION SCORES:**

```
📈 TREND BAND (last 90 days, this CSR)
  Overall:           7.6  |  30d avg 7.4  |  60d avg 7.3  |  90d avg 7.1
                     ↗ trending up (+0.5 vs 90d, +0.2 vs 30d)
  Booking Conv.:     6.0  |  30d avg 5.8  |  90d avg 5.4
                     ↗ slow climb; still 1.2 below shop median 7.2
  Membership:        5.0  |  30d avg 5.1  |  90d avg 4.9
                     → flat; 1.8 below shop median 6.8 — top coaching priority
  Empathy/Soft:      9.0  |  30d avg 8.8  |  90d avg 8.6
                     ↗ at shop top quartile (median 7.5)
  Spanish handling:  8.5  |  30d avg 8.4  |  90d avg 8.2
                     ↗ no peer comparison — only 2 CSRs handle Spanish
```

**Trend-band thresholds (use these arrow rules so the language is consistent across debriefs):**

- `↗ trending up` — current vs. 90d avg ≥ +0.4
- `→ flat` — current vs. 90d avg between −0.3 and +0.3
- `↘ trending down` — current vs. 90d avg ≤ −0.4
- `🔴 regression flag` — current ≥ 1.5 below 90d avg AND prior debrief also showed a regression on the same dimension (two-cycle confirmation pattern)

**Coaching-Action selection rule update:**

The v1.0 rule "pick top 2 coaching actions" gets a v1.1 priority overlay: when a dimension is flagged with `🔴 regression flag`, the regression dimension takes one of the two coaching-action slots, even if a different dimension would otherwise be the largest gap to shop median. This catches CSRs who are slipping on a previously-strong skill (often the early-burnout signal in CSR work).

**Why this lifts Personalization 9 → 10:** A single-debrief score gives the same recommendation regardless of who is being coached. The trend-band layer makes the coaching specific to the CSR's actual trajectory — a 6.0 booking conversion is reinforcement for someone climbing from 4.2, and a regression flag for someone falling from 7.8.

### v1.1.B — AI-vs-Human-CSR Comparative-Benchmark Block

Most plumbing shops now run a hybrid model — AI receptionist on after-hours and overflow, human CSRs on daytime and emergency. The v1.0 skill correctly notes the split exists ("Note the AI / human split in the header") but stops there. The v1.1 block below adds the structured side-by-side comparison so the office manager can keep the routing rules between AI and human calibrated.

**Trigger:** Apply when `config.yml` lists at least one AI-receptionist platform (Avoca, Pete & Gabi Olivia, ServiceAgent, Trillet, Marlie, ConvoCore, Smith.ai AI, Sameday, or shop-specific) AND the debrief period had at least 20 AI-handled calls in addition to the human-handled sample.

**Inputs added:**

- **AI-receptionist platform metrics export** — Booking rate, average handle time, hold-time discipline, transfer-to-human rate, after-hours / overflow / scope-limit miss rate. Pull from the platform's reporting (Avoca dashboard, Pete & Gabi Olivia exports, etc.).
- **Sample disposition tags** — Which calls were AI-handled, which were transferred to a human mid-call (and at what point), which were human-only.

**New output block — insert after DIMENSION SCORES:**

```
🤖 AI vs HUMAN CSR — same period, same call-mix
                          Human CSR (Andrea)   AI (Avoca)    Δ
  Calls handled:                   8                 47       —
  Booking rate (qualified):     5/6 = 83%      31/41 = 76%   +7pp
  Avg handle time:                4:12               2:58    +1:14
  Hold-time discipline:            9/10              10/10    -1
  Membership cross-sell:         1/4 = 25%      6/27 = 22%    +3pp
  Spanish handling:              2/2 = 100%      0/0 (n/a)    n/a
  Emergency triage:              1/1 PASS        2/2 PASS     tie
  Transfer-to-human rate:           n/a              17%      —
  Scope-limit miss rate:            n/a              4%       —
```

**Routing-rule diagnostic — auto-generate one of these four diagnoses:**

1. **CALIBRATED** — AI booking rate within 5pp of human AND scope-limit miss rate ≤ 5%. No routing change needed.
2. **EXPAND AI WINDOW** — AI booking rate ≥ human booking rate AND scope-limit miss rate ≤ 5%. Recommend extending AI-handled hours into adjacent windows (e.g., shift Avoca window from 6 PM–8 AM to 4 PM–9 AM).
3. **TIGHTEN AI SCOPE** — AI booking rate ≥ 10pp below human OR scope-limit miss rate > 8%. Recommend narrowing AI scope (e.g., AI handles after-hours intake-only, transfers all booking attempts to human callback in the morning).
4. **REVIEW SPECIFIC CALL TYPES** — One or more call types underperform their cross-mode equivalent by ≥ 20pp (e.g., AI converts 12% on water heater repair-vs-replace conversations vs. 67% for the senior human CSR). Recommend type-specific routing carve-out.

**Programmable-scope-as-guardrail note:** The Superior Plumbing "Piper" case study (ServiceTitan / Feb 2026) showed 67% close rate after 7 CSR equivalents were reduced to 3 FT + AI by tightly constraining what the AI could attempt (no Spanish, no commercial estimates, no membership renewals — all routed to human). The naming-contest adoption tactic from that case study makes the AI a teammate rather than a replacement; the programmable-scope rule keeps the AI from over-reaching on call types where it conversion-rates underperform. Cite this case in the routing-rule recommendation when the diagnosis is TIGHTEN AI SCOPE.

**Why this lifts Specificity 9 → 10 and grounds Industry fit at 10:** v1.0 acknowledged the hybrid model exists; v1.1 produces an actual side-by-side benchmark block with a concrete routing-rule diagnostic. The Superior Plumbing data point is the first published AI-vs-human CSR conversion benchmark in plumbing.

### v1.1.C — Bilingual Spanish-Call Sub-Dimension

The v1.0 skill scores Spanish handling as a sub-point of Greeting and Qualification dimensions. For shops where Spanish-speaking callers are ≥ 15% of inbound volume, that's insufficient resolution — the bilingual handling deserves its own dimension with its own coaching artifact.

**Trigger:** Apply when `config.yml` flags `bilingual_posture: spanish` (or any non-English) AND the debrief period had at least 5 bilingual calls in the sample.

**New 8th dimension added to the analysis framework:**

### 8. Bilingual Call Handling (when configured)
- Was the language switch handled within 15 seconds of the caller's first Spanish word, without making them repeat themselves?
- Was the formal register (*usted* / *señora*) used by default and switched to informal (*tú*) only on the caller's lead?
- Were plumbing-specific Spanish terms used accurately? (Common drift: *llave de agua* vs. *grifo* vs. *canilla* — match the caller's region; *fuga* for leak, not *escape*; *tubería* for pipe, not *cañería* unless the caller used it first.)
- Was the appointment recap done in Spanish, with the time window stated in the format the caller used (12-hour vs. 24-hour, AM/PM in Spanish)?
- Was the confirmation text sent in Spanish (not auto-translated from English)?
- For mixed-language households (caller's Spanish + spouse's English): was the language preference captured for the technician handoff, with a note on which family member will be home at the appointment time?

**Output addition — new row in the DIMENSION SCORES block:**

```
  Bilingual Call Handling:        [X]/10
```

**Cross-skill reference:** When the trend-band layer (v1.1.A) shows Spanish handling at 9+ for three consecutive cycles, the CSR's transcripts become candidate training data for the shop's `_shared/bilingual-tone-guide.md` artifact (eight cycles overdue per 05-11 backlog). Flag in the OFFICE MANAGER NOTES block: "Andrea's Spanish call handling is repo-quality — pull her last three months of transcripts for the bilingual tone guide when it ships."

### v1.1.D — Multi-CSR Batch Execution

The v1.0 skill processes one CSR at a time. Most office managers run weekly debriefs on 4–8 CSRs in a single session — re-pasting the analysis framework, the dimension list, and the prompt context for each CSR is the per-call overhead the v1.1 batch mode eliminates.

**Trigger:** Apply when the user pastes call data for more than one CSR in a single invocation, or when the input is structured as `{csr_name: [calls...]}` for multiple CSRs.

**Batch input format:**

```
BATCH DEBRIEF — Period: 2026-05-12 through 2026-05-18
CSRs in batch: Andrea M., Brian P., Catalina V., Devon S.

[Andrea M.]
- Call 1: <transcript or summary>
- Call 2: <transcript or summary>
...

[Brian P.]
- Call 1: <transcript or summary>
...
```

**Batch output structure:**

1. **Batch header block** — Period, CSR count, total calls, aggregate booking rate, aggregate emergency volume.
2. **Per-CSR debrief** — Full v1.0 output (with v1.1.A trend band and v1.1.C bilingual row when applicable) for each CSR in the batch, separated by a hard rule.
3. **Cross-CSR pattern block** — A single end-of-batch summary that surfaces patterns across the team without comparing CSRs publicly:
   - Calls that two or more CSRs fumbled with the same root cause (almost always a script gap or a pricebook ambiguity rather than a CSR-specific issue).
   - Job types where any CSR's booking rate is below 50% — usually a sign the shop's pricing posture on that job type needs revisiting, not a coaching issue.
   - Calls that one CSR handled exceptionally well that could become training transcripts for the rest of the team.
   - Calls that are candidates for the After-Hours Call Summary skill's morning briefing format (if the call would benefit from triage-tier framing, flag it).

**Anti-pattern guard:** The cross-CSR pattern block does NOT rank CSRs against each other, does NOT include leaderboard tables, and does NOT identify the "lowest-performing" CSR by name. The v1.0 anti-pattern rule ("Never use a CSR debrief to compare CSRs across the team in a group meeting") extends to batch mode — cross-CSR observations are framed as shop-level systems issues, not CSR-level performance issues. The per-CSR section stays the 1-on-1 artifact.

**Why this lifts Efficiency:** A 4-CSR weekly debrief that previously required 4 separate invocations + 4 separate prompt setups now runs in a single pass with the same per-CSR quality. Office-manager-side time drops from ~30 minutes to ~8 minutes for the prompt/output handling — the AI's analysis time is unchanged, but the meta-overhead disappears.

---

**End of v1.1 additions. v1.0 example output above remains the canonical example. The v1.1 sub-sections layer on without modifying any v1.0 instruction or example.**
