---
name: "Dormant Customer Reactivation Outreach"
category: customer-service
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~25 min per batch of 20 contacts; typical win-back batch of 200 contacts recoups 6–12 jobs"
version: 1.0
last_eval_score: null
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
