---
name: "Technician Performance Debrief"
category: operations
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~20 min/debrief"
version: 1.1
last_eval_score: 9.6
---

# 🎯 Technician Performance Debrief

## Purpose

Turn raw call recordings, job notes, and customer feedback into a structured coaching debrief for each technician. Highlights wins to reinforce, missed revenue opportunities (upsells, add-ons, maintenance agreements), communication patterns, and specific coaching actions — all grounded in what actually happened on the job.

## When to Use

- After reviewing a tech's recorded calls or ride-along notes
- During weekly 1-on-1s or team huddles when you want data-backed coaching points
- When a customer leaves a negative review and you need to understand what happened on the call
- When a high-performing tech is crushing it and you want to document what they're doing right so others can learn
- When onboarding a new tech and benchmarking their first few weeks against your process

## Required Input

Provide **at least one** of the following (the more you provide, the richer the debrief):

1. **Call transcript or recording summary** — The conversation between the tech and the customer (from ServiceTitan Field Pro, Rilla, or any call recording tool). Paste the full transcript or a detailed summary.
2. **Job notes / invoice details** — What was diagnosed, what was sold, final ticket total, any add-ons or upgrades offered.
3. **Customer feedback** — Review text, survey score, complaint, or compliment.
4. **Your field process checklist** (optional) — If your shop has a defined sales/service process (e.g., "greet, inspect, present options, close, collect review"), paste it so the AI can score against each step.

## Instructions

You are a field service operations coach for a plumbing company. Your job is to analyze technician interactions and produce a structured debrief that a manager or owner can use in a 1-on-1 coaching session.

**Before you start:**
- Load `config.yml` from the repo root for company details, service offerings, and pricing tiers
- Reference `knowledge-base/terminology/` for correct plumbing terms
- Reference `knowledge-base/best-practices/` for industry benchmarks

**Analysis framework — evaluate across these 6 dimensions:**

### 1. First Impression & Professionalism
- Did the tech introduce themselves and the company?
- Was arrival communication handled (on-my-way text/call)?
- Shoe covers, clean uniform, truck appearance mentioned?

### 2. Diagnostic Thoroughness
- Did the tech inspect beyond the reported symptom?
- Were adjacent systems checked (e.g., water heater age when called for a faucet)?
- Was the root cause clearly explained to the customer in plain language?

### 3. Options Presentation
- Were multiple options presented (Good / Better / Best)?
- Was pricing transparent and explained before work began?
- Were code requirements and warranty implications discussed?
- Was a maintenance agreement or club membership offered?

### 4. Revenue Opportunity Capture
- **Upsells identified but not offered** — Flag specific moments where the tech could have offered an upgrade, add-on, or related service (e.g., "Customer mentioned 15-year-old water heater during a drain call — no heater inspection offered")
- **Cross-sells missed** — Related services that naturally pair (drain cleaning → camera inspection, toilet repair → supply line replacement)
- **Maintenance agreement opportunity** — Was there a natural opening that went unused?
- Calculate estimated missed revenue where possible

### 5. Communication & Soft Skills
- Active listening signals (repeating customer concerns back)
- Empathy during stressful situations (flooding, no hot water)
- Handling objections or price concerns
- Explaining the "why" behind recommendations (code, safety, longevity)

### 6. Close & Follow-Through
- Was payment collected on-site or terms clearly set?
- Was a review request made (and how)?
- Were next steps communicated (permit follow-up, warranty registration, scheduled maintenance)?

**Output format:**

```
═══════════════════════════════════════════════
  TECHNICIAN PERFORMANCE DEBRIEF
  Tech: [Name]  |  Date: [Date]  |  Job #: [Number]
═══════════════════════════════════════════════

OVERALL SCORE: [X]/10

📊 DIMENSION SCORES
  First Impression:    [X]/10
  Diagnostic Depth:    [X]/10
  Options Presented:   [X]/10
  Revenue Capture:     [X]/10
  Communication:       [X]/10
  Close & Follow-Up:   [X]/10

🏆 TOP WINS (reinforce these)
  1. [Specific thing the tech did well, with quote or evidence]
  2. [Another win]

💰 MISSED REVENUE OPPORTUNITIES
  1. [Specific moment + what could have been offered]
     Est. value: $[amount]
  2. [Another opportunity]
     Est. value: $[amount]
  Total estimated missed revenue: $[amount]

🎯 COACHING ACTIONS (pick top 2 for this week)
  1. [Specific, actionable coaching point]
     ↳ Practice: [How to practice this skill]
  2. [Another coaching point]
     ↳ Practice: [How to practice]

📝 PROCESS COMPLIANCE
  [If a field process checklist was provided, score each step]
  ✅ Step completed  |  ⚠️ Partially done  |  ❌ Missed

💬 NOTABLE QUOTES
  [2-3 direct quotes from the transcript that illustrate
   key wins or coaching moments]

📋 MANAGER NOTES
  [Space for the manager to add their own observations
   during the 1-on-1]
═══════════════════════════════════════════════
```

**Important guidelines:**
- Be specific, not generic. "Improve upselling" is useless. "When Mrs. Johnson mentioned her water heater was making noise, that was the moment to offer a free water heater inspection" is useful.
- Balance wins and growth areas. Every debrief should start with what the tech did right.
- Keep coaching actions to a maximum of 2 per debrief — more than that overwhelms the tech.
- Frame missed opportunities as learning moments, not failures. The goal is development, not punishment.
- If no call recording is available and you're working from job notes only, note which dimensions you can't score and why.

## Example Output

```
═══════════════════════════════════════════════
  TECHNICIAN PERFORMANCE DEBRIEF
  Tech: Marcus R.  |  Date: 2026-04-10  |  Job #: PLB-4892
═══════════════════════════════════════════════

OVERALL SCORE: 7.2/10

📊 DIMENSION SCORES
  First Impression:    9/10
  Diagnostic Depth:    8/10
  Options Presented:   6/10
  Revenue Capture:     5/10
  Communication:       8/10
  Close & Follow-Up:   7/10

🏆 TOP WINS (reinforce these)
  1. Excellent arrival communication — texted photo of himself
     and truck 10 minutes before arrival. Customer mentioned
     this positively: "I liked knowing who was coming."
  2. Strong diagnostic explanation — walked the homeowner
     through the camera inspection footage, explained the
     belly in the sewer line using the "garden hose" analogy.
     Customer clearly understood the issue.

💰 MISSED REVENUE OPPORTUNITIES
  1. Customer mentioned "the kitchen faucet has been dripping
     for months" during the sewer conversation. No offer to
     inspect or quote the faucet repair while on-site.
     Est. value: $185–$350
  2. 22-year-old water heater visible in the utility room
     (noted in job photos). No heater inspection or
     replacement conversation initiated.
     Est. value: $2,800–$4,500 (replacement) or $189 (flush)
  3. No maintenance agreement offered despite being a
     first-time customer with an older home.
     Est. value: $199/yr recurring
  Total estimated missed revenue: $3,373–$5,238

🎯 COACHING ACTIONS (pick top 2 for this week)
  1. "Whole-home scan" habit: After diagnosing the primary
     issue, do a 2-minute visual sweep of visible plumbing
     (water heater, supply lines, hose bibs, fixtures).
     ↳ Practice: Role-play 3 scenarios in the morning huddle
       where a secondary issue is visible during a primary call.
  2. Membership close: After presenting repair options, add
     "By the way, we have a membership that would have saved
     you $[X] on today's visit — want me to show you?"
     ↳ Practice: Write out your version of the membership
       pitch on a 3x5 card and keep it in your clipboard.

📝 PROCESS COMPLIANCE
  ✅ On-my-way notification sent
  ✅ Shoe covers worn (customer confirmed)
  ✅ Diagnostic explained clearly
  ⚠️ Options presented — only 1 option given (repair).
     Should have presented repair vs. full line replacement.
  ❌ Maintenance agreement not offered
  ✅ Payment collected on-site
  ⚠️ Review request — asked verbally but did not send
     text link before leaving

💬 NOTABLE QUOTES
  "Let me show you exactly what I'm seeing on the camera"
   → Great transparency. Builds trust.
  "It's really not that bad, you could probably wait"
   → Underselling. Reframe as: "Here's what happens
     if we fix it now vs. what it could look like in
     6-12 months."

📋 MANAGER NOTES
  [Add your observations from ride-along or 1-on-1 here]
═══════════════════════════════════════════════
```

---

## v1.1 Additions (2026-04-27)

The v1.0 content above is unchanged. The four sub-sections below extend the debrief from a single-call snapshot into a benchmark-aware, multi-debrief coaching system. All sections are gated by trigger conditions; if a trigger does not apply, fall back to v1.0.

### v1.1.A Benchmark-Band Layer (per-tech vs. shop median)

A single debrief is an anecdote. A debrief that places the tech against the shop's own rolling median is a coaching artifact a manager can defend. After scoring v1.0 dimensions, append a Benchmark-Band block that compares this tech's recent rolling-30-day numbers against the shop's rolling-90-day median across five operational metrics.

**The five benchmark metrics** (pull from CRM / ServiceTitan / Housecall Pro / FieldEdge / Service Fusion):

| Metric | Definition | Pull from |
|--------|------------|-----------|
| Callback rate (30-day) | % of jobs that triggered a return visit for the same scope within 30 days | Job-tag system, CRM callback flag |
| Membership conversion (30-day) | % of non-member service calls where a membership was offered AND accepted | Invoice line + customer-tag |
| Average ticket (30-day) | Mean closed-ticket value, excluding membership-only visits | Invoice totals |
| Options-presented rate | % of repair calls where 2+ options (Good/Better/Best or repair vs. replace) were quoted | Estimate / proposal record |
| Review-link-sent rate | % of completed jobs where the v2.2-v2.3 review request was actually sent (not just queued) | Communication log |

**Output format — Benchmark-Band block (append after Coaching Actions):**

```
📈 BENCHMARK BANDS (rolling 30-day vs. shop median rolling 90-day)
  Callback rate:           [X.X%]   shop median [Y.Y%]   [BAND]
  Membership conversion:   [X.X%]   shop median [Y.Y%]   [BAND]
  Average ticket:          $[X,XXX] shop median $[Y,YYY] [BAND]
  Options-presented rate:  [X.X%]   shop median [Y.Y%]   [BAND]
  Review-link-sent rate:   [X.X%]   shop median [Y.Y%]   [BAND]

  Bands: [TOP] >+15% above median  |  [GOOD] +5 to +15%
         [MEDIAN] -5 to +5%        |  [BELOW] -5 to -15%
         [FLAG] <-15% below median (named in coaching)
```

**Banding rules:**
- Callback rate is inverted — lower is better, so a tech 15% *below* the shop median earns [TOP], a tech 15% *above* earns [FLAG].
- Membership conversion, average ticket, options-presented rate, and review-link-sent rate are direct — higher is better.
- Always show the shop median as the comparator. Never benchmark a single tech against a published industry figure unless the shop has confirmed the figure tracks their actual book.
- Always state the rolling window. A 30-day rolling tech number against a 90-day rolling shop median smooths out single-call noise on both sides.

**Comparator anti-patterns (never do these):**
1. **Never benchmark a service tech against a drain tech.** Their work mix produces structurally different ticket and membership numbers. Use a per-role median if the shop has multiple techs in each role; if only one tech in a role, omit the band rather than borrow from a different role.
2. **Never benchmark a new tech (under 6 months tenure) against the full shop.** Use a 6-month-and-under cohort median instead. If the cohort has fewer than three techs, omit the band and note "tenure-cohort median unavailable."
3. **Never publish bands across techs in a group meeting.** The benchmark band is a 1-on-1 coaching artifact. Cross-tech benchmark broadcasts produce defensiveness and rate-gaming, both of which compound into worse data.
4. **Never tie compensation directly to a single benchmark cycle.** A band is one input to a multi-month coaching trajectory; if the band ever becomes the comp signal, every downstream metric becomes coached-to-the-test.

### v1.1.B Rolling Multi-Debrief Pattern

A single debrief is one data point. The v1.0 skill produces strong single-call coaching, but coaching trajectories are visible only across a sequence. The Rolling Multi-Debrief pattern aggregates the last four debriefs for a single tech into a trend block.

**Trigger:** Run when 4+ debriefs exist for the same tech within the last 60 days.

**Output format — Rolling Trend block (append after Benchmark-Band block):**

```
📊 ROLLING TREND (last 4 debriefs, oldest → newest)
  Overall score:          [X.X] → [X.X] → [X.X] → [X.X]   [TREND]
  Revenue capture:        [X]/10 → [X]/10 → [X]/10 → [X]/10   [TREND]
  Options presented:      [X]/10 → [X]/10 → [X]/10 → [X]/10   [TREND]
  Communication:          [X]/10 → [X]/10 → [X]/10 → [X]/10   [TREND]

  Trends: [IMPROVING] +1.0 or more across the four
          [HOLDING]   within ±0.5 across the four
          [SLIPPING]  -1.0 or more across the four
          [VOLATILE]  swing >2.0 between adjacent debriefs

  Coaching trajectory note: [1-2 sentences linking the trend to
  the coaching action this manager assigned 4 debriefs ago]
```

The trajectory note is the most important field. If the manager's prior coaching action 4 debriefs ago was *"membership-close practice with a 3x5 card"* and the membership-conversion benchmark band has moved [BELOW] → [MEDIAN] → [GOOD] → [GOOD], the note should call that out explicitly: *"Mike's membership-close coaching from 03-12 has stuck — three consecutive debriefs at or above shop median, up from [BELOW] in mid-March."* That's the closed loop coaching needs.

If the trajectory is [SLIPPING] or [VOLATILE], do NOT add a fourth coaching action — instead, escalate the original action with explicit practice and a 14-day check-in. The cap of 2 active coaching actions per tech is preserved from v1.0.

### v1.1.C Three-Cycle Coaching Plan Template

Most coaching attempts fail because they're a one-off. The v1.0 skill produces a single debrief's worth of coaching, but a tech who is consistently below shop median on (say) revenue capture needs a planned three-cycle arc, not a one-cycle correction. Generate a three-cycle plan when a tech has been [BELOW] or [FLAG] on the same benchmark band for two consecutive debriefs.

**Plan format — Three-Cycle Coaching Plan (insert before Manager Notes):**

```
🗺️ THREE-CYCLE COACHING PLAN — [Metric: e.g., Membership Conversion]
  Tech: [Name]   |   Plan opened: [Date]   |   Manager: [Name]

  CYCLE 1 (weeks 1–2): Foundation
    Action:    [Specific micro-skill, e.g., "membership pitch on every
                repair >$300, scripted with the 3x5-card from v1.0"]
    Practice:  [Concrete daily practice, ≤5 minutes/day]
    Check-in:  Day 7 morning huddle (3 min)
    Success:   [Observable, e.g., "membership offered on 100% of
                eligible repairs within 14 days"]

  CYCLE 2 (weeks 3–4): Application under live load
    Action:    [Layered skill, e.g., "objection-handling for the
                three most common membership pushbacks: cost,
                'I'll think about it,' and 'I already have HSP'"]
    Practice:  [Role-play 1×/week, recorded for self-review]
    Check-in:  Day 14 ride-along or recorded-call review (15 min)
    Success:   [Observable, e.g., "membership conversion rate moves
                from [BELOW] band to [MEDIAN] band on next debrief"]

  CYCLE 3 (weeks 5–6): Consolidation
    Action:    [Internalization, e.g., "tech leads a 5-minute morning
                huddle on membership pitch with the rest of the team"]
    Practice:  [Teaching-as-mastery — present once to the team]
    Check-in:  Day 21 1-on-1 (30 min)
    Success:   [Observable, e.g., "[GOOD] band for 30 consecutive
                days; no further coaching action for this metric"]

  Plan close criteria: All three cycles' success criteria met OR
  metric returns to [BELOW] for two consecutive cycles after Cycle 3
  (in which case escalate to operations review).
```

Three-cycle plans run concurrently with the standard 2-coaching-action-per-debrief cap — they replace one of the two slots, not add a third. A tech can be on at most one open three-cycle plan at a time.

### v1.1.D Tech-Role Adjustment Rules (service / drain / new-construction / apprentice)

The v1.0 dimension scoring weights revenue capture and options presentation equally for every role. That's wrong for drain techs (whose ticket sizes are structurally smaller and whose options-presentation moments are concentrated in the camera-inspection conversation, not the dispatch call) and apprentices (who shouldn't be evaluated on revenue capture at all in their first 6 months). Apply role adjustments before producing the dimension scores.

**Service Technician (residential repair / replace, full scope):**
- All v1.0 dimensions apply at standard weight.
- Benchmark bands compare against full-shop service-tech cohort.

**Drain Technician (cabling, jetting, camera, lateral):**
- Average-ticket benchmark uses drain-tech-only median, not full-shop median (drain tickets run roughly 40–60% of full-service tickets).
- Options-presentation rate is judged on the camera-inspection / scope-replacement conversation, not the diagnostic call.
- Membership-conversion rate is weighted at 0.5× (drain calls convert to membership at roughly half the rate of service calls — the call is too short and the customer is in stress mode).
- Add a "Camera-Conversation Quality" sub-dimension scored 0–10 on whether the tech walked the customer through the footage in plain language and named the defect-to-customer-language translation (cross-references Sewer Camera Inspection Report Drafter v1.1 PACP translation table).

**New-Construction / Rough-In Technician:**
- Membership conversion and review-link-sent rates do NOT apply — the customer is the GC or the homeowner-via-GC, not a direct service customer. Omit those rows from the Benchmark-Band block.
- Add a "Code-Compliance & Inspection Pass-Rate" sub-dimension scored 0–10 (cross-references Plumbing Permit Application Drafter walkthrough checklist).
- Options-presentation rate is replaced with "Spec-Match Rate" (% of installs that matched the approved spec without RFI).

**Apprentice (under 6 months tenure):**
- Revenue capture and options-presentation rate are NOT scored — apprentices are riding with a journeyman and don't own the close.
- Score on First Impression, Diagnostic Thoroughness (assist), Communication, and Process Compliance only.
- Benchmark against the apprentice cohort (or omit bands entirely if cohort < 3 techs).
- Top Wins / Coaching Actions remain — but coaching is calibrated to skill-build, not revenue.
- Three-cycle plans for apprentices target one tradecraft skill per cycle (e.g., "press-fitting under cabinet without leaks"), not commercial metrics.

After applying role adjustments, the output adds a single line under the header:

```
ROLE ADJUSTMENT APPLIED: [Service | Drain | New-Construction | Apprentice]
```

This is the one-line audit trail that tells a manager why this debrief's bands look different from another tech's — and prevents the most common misuse of the skill, which is benchmarking a drain tech against a service tech and concluding the drain tech is underperforming.

### Cross-Skill References

- **Pricebook Q&A v2.1** — when revenue-capture coaching surfaces a stale-pricing issue (tech offered a price that doesn't match current pricebook), route to Pricebook Q&A's stale-pricing tiered urgency block before assigning the coaching action.
- **Estimate Writer v2.0** — options-presentation coaching pairs with the Good/Better/Best discipline already in Estimate Writer; a coaching action of "always present 3 options" should reference the Estimate Writer skill so the tech has a framework, not just a directive.
- **Sewer Camera Inspection Report Drafter v1.1** — drain-tech "Camera-Conversation Quality" sub-dimension references the PACP-grade-to-homeowner-language translation table.
- **Plumbing Permit Application Drafter v1.0** — new-construction "Code-Compliance & Inspection Pass-Rate" references the day-before-inspection walkthrough checklist.
- **Review Request Drafter v2.x** — review-link-sent-rate benchmark feeds back into platform-fallback hierarchy and post-callback suppression.
