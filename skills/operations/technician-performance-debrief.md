---
name: "Technician Performance Debrief"
category: operations
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~20 min/debrief"
version: 1.0
last_eval_score: 9.4
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
