---
name: "Technician Candidate Phone Screen"
category: admin
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~20 min/candidate"
version: 1.2
last_eval_score: 9.6
---

# Technician Candidate Phone Screen

## Purpose

Turn a raw plumber or apprentice application into a ready-to-run phone screen — a tight, trades-appropriate interview script the hiring owner or recruiter can complete in 8–12 minutes, plus a structured post-call summary with a clear hire/maybe/pass recommendation. Built for the reality that good plumber candidates are usually on a job, in a truck, or under a sink — they can talk, but they can't type, sit for a video call, or click through an ATS form.

The skill is tuned to the 2026 trades hiring market, where the first shop to reach a candidate is usually the shop that hires them, and where AI-driven phone screening (Classet, Paradox, etc.) has compressed time-to-fill from weeks to days.

## When to Use

- **New application lands** — Indeed, ZipRecruiter, Craigslist, website form, word-of-mouth referral. Run this skill within the hour.
- **Cold-sourced candidate** — A journeyman you spotted at a supply house, a tech whose shop just closed, a referral from another trade.
- **Re-engaging a lapsed candidate** — Someone who applied 3–6 months ago and may be back on the market.
- **Pre-ride-along screen** — Before investing a half-day on a working interview, run a 10-minute phone screen to filter.
- **Apprentice screening** — Adapt the script for entry-level candidates where license questions are swapped for reliability, transportation, and learning posture.

**Do not use this skill for:**
- Final offer decisions (this is a screen, not an evaluation)
- Skill-based testing (use a working interview or bench test)
- Reference checks (separate workflow — see `invoice-follow-up-sequence.md` style for templating)

## Required Input

1. **Candidate info**
   - Name, phone, email
   - Source (Indeed, referral, etc.) and date applied
   - Résumé text, job history, or whatever was submitted — paste it raw, the skill will parse
   - Target role (Journeyman Plumber, Service Tech, Drain Tech, Apprentice, Foreman, etc.)

2. **Role requirements**
   - Required license/certification for your state (e.g., California C-36, Texas Journeyman, Florida CFC)
   - Years of experience required
   - Work type mix: service, new construction, remodel, commercial, drain cleaning, sewer, hydronic, gas
   - Truck situation: company truck vs. BYO-truck with allowance
   - On-call rotation expectations
   - Pay range and benefits headlines (so the screen can test fit without wasting time)

3. **Disqualifiers (if any)**
   - Hard no-go items: no valid driver's license, no current license where required, inability to pass background/drug, gaps you can't accept
   - Soft flags: e.g., more than 3 jobs in 2 years

4. **Screener context**
   - Who is running the call (owner, office manager, ops manager)
   - How much time they have (8 / 10 / 15 minutes)
   - Whether this is a live call or a ring-back after the candidate applied

## Instructions

You are the hiring assistant for a plumbing company. Your job has three parts: (1) build a focused phone-screen script from the candidate's application and the role spec, (2) structure the note-taking so the screener can capture answers while driving the conversation, and (3) produce a post-call summary with a hire/maybe/pass recommendation.

**Before you start:**
- Load `config.yml` for company name, locations served, voice guidelines, and any standard hiring questions the shop already uses
- Check `knowledge-base/regulations/` for the state licensing rules that apply — never guess a license number format or renewal cadence
- Check `knowledge-base/terminology/` to validate any trade jargon the candidate used (PEX-A vs. PEX-B, PACP sewer coding, Uniform vs. International plumbing code, etc.) so the screener can ask a credible follow-up

**Core principles:**

1. **Respect the candidate's time and situation.** Plumbers and apprentices are usually calling back between jobs. Opening line should ask if now is a good time and offer a ring-back window. Never make them sit through a 20-minute intake.

2. **Lead with the license / reliability knockouts.** If they don't have a valid driver's license, a working vehicle (for BYO shops), or the required state license/registration, the rest of the call is moot. Front-load the 3 questions that can end the call gracefully in 90 seconds.

3. **Ask for specifics, not summaries.** "Tell me about yourself" is a waste. "What was the last call you ran today?" or "Walk me through the last water heater you replaced — gas or electric, and why did you size it the way you did?" surfaces real skill in 60 seconds.

4. **Calibrate technical depth to the role.** A service tech needs diagnostic storytelling (symptom → suspect → test → confirm). A new-construction plumber needs rough-in and code fluency. A drain tech needs sewer-line judgment (jet vs. snake vs. dig). An apprentice needs attitude, transportation, and learning posture. The script should adapt, not ask the same 10 questions to everyone.

5. **Test for the intangibles.** Plumbing callbacks and bad reviews kill shops. Screen for: ownership of mistakes ("tell me about a callback — what happened and how did you handle it"), customer communication ("how do you explain a $3,200 repair to a homeowner who expected $500"), and truck stewardship ("walk me through how you load out for a typical service day").

6. **Surface real comp expectations early.** Don't end the call without a two-way conversation about pay, schedule, on-call, and truck. A technically great candidate who expects $45/hour when the role pays $32 is a pass — and you both deserve to know in 10 minutes, not 10 days.

**Output sections (produce all four):**

### Section 1 — Pre-call prep sheet (1 page max)

- Candidate snapshot: name, source, target role, one-line thesis ("Journeyman with 7 yrs service, last shop was drain-heavy, says he wants more water heater / repipe work")
- Top 3 things to verify (e.g., CA C-36 license status, clean DL, availability for 1-week-out start)
- Top 3 flags from the application to probe (employment gap, self-employed period, license number not found in state search, résumé says "lead plumber" but only 4 years total)
- The 8–12 question script, grouped: (a) knockouts, (b) experience specifics, (c) technical probes for the target role, (d) fit/comp/logistics

### Section 2 — Knockout questions (90-second path to a clean no)

Exactly 3 questions, phrased so a "no" ends the call respectfully:
- License/registration status in your state, with number they can read off a card
- Valid driver's license and clean-enough MVR for company insurance (or own truck with appropriate coverage if BYO shop)
- Availability: start date, on-call willingness, any scheduling blockers (school pickup, second job, etc.)

### Section 3 — Role-calibrated interview script

8–12 questions tailored to the target role. Each question should include:
- The question as spoken
- What good / okay / bad answers sound like (2-3 lines each) so the screener can score while listening
- A follow-up probe if the first answer is thin

Always include at least one scenario question tied to the role:
- Service tech: "Homeowner calls — no hot water, 50-gal gas, 9 years old, pilot won't stay lit. Walk me through your visit."
- Drain tech: "Kitchen line backing up in a 1950s slab-on-grade, 70 ft to the cleanout. Jet, snake, or camera first — and why?"
- New-construction plumber: "You're roughing in a two-story with 3 baths and a laundry. Walk me through your DWV stack decisions."
- Apprentice: "You've never done this work before — what's the first thing you'd want to learn, and how do you like to be taught?"

### Section 4 — Post-call summary template

A one-page structure the screener fills in during or right after the call:
- Candidate name, date, screener, call length
- Knockouts: pass / fail (with detail)
- Experience snapshot: years, last 2 shops, reason for leaving, work-type mix
- Technical read: strong / okay / weak, with one verbatim quote that supports the read
- Intangibles read: ownership, communication, truck care — one line each
- Comp/logistics fit: pay expectation vs. range, start date, on-call, truck
- Recommendation: **HIRE (advance to working interview) / MAYBE (hold, or re-screen in 30 days) / PASS (with reason)**
- Next action and owner, with a date

**Tone and format:**
- The script is conversational, not corporate. No HR jargon. A plumbing owner should be able to read it straight off the page without cringing.
- Never insert language that sounds like a compliance script ("For quality and training purposes...") — it kills trust with trades candidates.
- Short sentences. Plain words. The kind of question a seasoned service manager would actually ask.

**Output requirements:**
- All four sections produced in one run, in order
- Questions must be role-calibrated — the output for an apprentice screen should not look like the output for a journeyman screen
- Every question must be answerable in under 60 seconds of candidate talk time
- The post-call template must fit on one page
- Save to `outputs/candidate-screens/{date}-{candidate-last-name}-{role}.md` if the user confirms

## Example Output

**SCENARIO:** Candidate Miguel Herrera applied via Indeed for Service Plumber. Résumé shows 6 years at two shops in Dallas, TX; Texas Journeyman license listed but number not provided; reason for leaving last shop blank; last job 3 weeks ago. Role requires TX Journeyman, 4+ years service experience, on-call 1 week in 4, company truck.

---

### Section 1 — Pre-call prep sheet

**Candidate:** Miguel Herrera — Service Plumber — Indeed, applied 04/13

**Thesis:** 6-year TX journeyman, two-shop history, service-heavy from résumé language ("water heaters, repipes, tankless installs"). 3-week employment gap and blank "reason for leaving" are the two things to probe.

**Verify:**
- Texas Master or Journeyman license number + TSBPE active status
- Clean DL, insurable for company truck
- Can start within 2 weeks, okay with 1-in-4 on-call

**Flags:**
- 3-week gap with no explanation — is he actively looking, or was he let go?
- "Lead tech" claim at second shop with 2 years there — plausible but worth a probe
- No mention of drain/sewer work — confirm the service mix he actually ran

---

### Section 2 — Knockout questions

1. *"Miguel, before we get rolling — can you read me your TX Journeyman or Master license number? I just want to make sure we're pulling up the right record on the TSBPE site."*
   - **Good:** Reads it off, matches TSBPE lookup as active.
   - **Bad:** "I don't have it handy" or "It's expired, I'm renewing" — not a hard no, but reschedule once it's verified.

2. *"Do you have a current Texas driver's license, and has your MVR been clean the last 3 years? Our insurance runs a check before we issue a truck."*
   - **Good:** Yes, clean, no accidents or moving violations.
   - **Flag:** One speeding ticket is fine; a DUI or at-fault accident in 3 years is usually a pass for insurance reasons.

3. *"What would a realistic start date look like for you, and how do you feel about one week of on-call every four weeks?"*
   - **Good:** 2 weeks out, on-call is fine.
   - **Flag:** "I can't do on-call" — hard pass for this role; "I need 30 days" — fine, note and continue.

---

### Section 3 — Role-calibrated interview script (excerpt, 8 questions)

**Q4. Walk me through the last water heater you replaced. Gas or electric, what size, and why did you size it that way?**
- **Good:** Names the unit, explains family size / fixture count / recovery rate or tankless logic, mentions T&P, expansion tank on a closed system, code venting for gas.
- **Okay:** Gives size and install but no sizing logic.
- **Bad:** Vague ("standard 40-gallon, same as the old one"), no code references, no mention of expansion / venting.
- **Probe:** "Did you pull a permit on that one? What's the inspector in [city] usually looking for?"

**Q5. Scenario — homeowner calls, no hot water, 50-gal gas, 9 years old, pilot won't stay lit. Walk me through your visit.**
- **Good:** Checks thermocouple first (cheap fix), then gas supply / valve, then tank condition (age, anode, leaks). Talks through good-better-best before quoting. Mentions when they'd recommend replace vs. repair on a 9-year-old tank.
- **Okay:** Jumps to replacement without diagnosing.
- **Bad:** Can't articulate a diagnostic order, or quotes a number before inspecting.

**Q6. Tell me about a callback you owned in the last year. What happened, and how did you handle it?**
- **Good:** Takes ownership, explains what they missed, what they learned, how they made it right with the customer.
- **Okay:** Callback was a parts issue, not a workmanship issue — acceptable but probe for a workmanship example.
- **Bad:** "I don't really get callbacks." (Everyone gets callbacks. This answer is a red flag for either dishonesty or low self-awareness.)

*(Questions 7–11 continue: drain/sewer experience mix, code fluency probe specific to city, truck/stock management, customer communication on a big-ticket quote, reason for leaving last shop.)*

**Q12. Fit and logistics:**
- *"Our range for service plumbers with your experience is $30–$36/hr plus performance pay, company truck, and standard benefits. How does that line up with what you're targeting?"*

---

### Section 4 — Post-call summary template

**Candidate:** Miguel Herrera
**Date / screener / length:** 04/14/2026 — [Screener] — ___ min

**Knockouts:** ☐ License verified (TSBPE #_____) ☐ DL + MVR okay ☐ Start date / on-call fit

**Experience snapshot:**
- Years in trade: ___
- Last 2 shops + reason for leaving:
- Service / drain / new-construction / commercial mix:

**Technical read:** ☐ Strong ☐ Okay ☐ Weak
- Verbatim quote:
- One follow-up concern:

**Intangibles:**
- Ownership of mistakes:
- Customer communication:
- Truck stewardship:

**Comp / logistics fit:**
- Target pay: ___ | Our range: $30–$36/hr → ☐ Fit ☐ Gap
- Earliest start:
- On-call acceptable: Y / N

**Recommendation:** ☐ HIRE — advance to working interview ☐ MAYBE — ___ ☐ PASS — ___

**Next action / owner / by when:**

---

## v1.1 Additions (2026-04-25)

The v1.0 skill scored 9.2 on the 04-14 and 04-24 evals. The 04-14 and 04-24 Remaining Opportunities both called out a 5-question, 10-minute compressed variant — the v1.0 8–12 question script is the right tool for a deliberate hiring conversation but is longer than what a busy owner can run when a strong candidate calls back at 4:45 PM on a Friday. v1.1 adds the compressed variant, a behind-the-wheel-of-a-truck-now scenario flag, an SMS-pre-screen pattern, and an apprentice-specific compressed track. All v1.0 sections above are unchanged.

### Compressed Variant — 5 Questions, 10 Minutes

Use this variant when:

- The candidate calls back during a 10-minute window between jobs (most common)
- The owner has back-to-back commitments and needs to either advance or pass on the call before the next meeting
- The candidate has already passed a sourcing-side screen (referral verified, license verified, recent paystub seen) and the live call is a confirmation, not an investigation
- The shop's pipeline has 3+ candidates this week and the owner needs to triage faster

The compressed variant **does not replace** the v1.0 full screen for serious candidates. Run the compressed variant as a triage; advance HIRE-track candidates into the full v1.0 script either later that day or in a scheduled second call.

#### The 5 questions (in this order)

**Q1 — License + DL knockout (60 seconds total).** "Quickly — what's your [STATE] license number, and is your driver's license clean?"
- **Pass:** Reads the number, status is current, DL is clean. Continue.
- **Fail:** No license, expired license, DUI in last 3 years, no DL. Thank them, end the call respectfully, document the reason.

**Q2 — Last job in their own words (90 seconds).** "Walk me through the last call you ran today" (or yesterday, or last week if they're between jobs).
- **Listening for:** Specifics over generalities (named the unit, named the diagnostic step, named the customer interaction). Trade vocabulary used naturally. Comfort talking about what went wrong as much as what went right.
- **Pass shape:** "I had a tankless that wouldn't fire — Navien NPE-240A. Started with the gas pressure — 7" WC at the appliance, that was fine. Pulled the burner, found a corroded ignitor. Swapped it, tested, customer was happy."
- **Fail shape:** Vague ("just a typical service call"), defensive ("I don't want to badmouth my last shop"), or storytelling without technical content.

**Q3 — Pay range fit (60 seconds).** "Our range for this role is $X to $Y per hour plus performance pay, company truck, [benefits]. How does that compare to what you're targeting?"
- **Pass:** In-range or close, willing to discuss performance pay structure. Continue.
- **Soft flag:** $3-5/hr above range, asks about performance pay seriously. Worth the full v1.0 conversation.
- **Fail:** $10+/hr above range with no flexibility. Thank them, end gracefully — the gap is too large to bridge in a hiring negotiation.

**Q4 — Scenario (3 minutes total: 1 min question, 2 min answer + probe).**
- Service tech: "Customer called — toilet running constantly, second story, it's leaking through the kitchen ceiling downstairs. Water shutoff is in the basement. What do you do in the first 90 seconds?"
- Drain tech: "Customer says their main line is backing up, sewage in the basement floor drain. You arrive and there's standing water 2 inches deep. First three things you do?"
- New-construction: "GC calls — your DWV stack passes air pressure test on the second floor but loses pressure on the third floor. Where do you start looking?"
- Apprentice: "First day on the truck with me. We get a no-hot-water call. What do you bring inside, and what do you do when we walk in?"

The scenario is **role-calibrated** and **time-pressured** — you want to hear them think out loud, not deliver a polished answer. The probe ("and then what?" "what would you check next?") gets you the second layer.

**Q5 — Knockouts wrap (60 seconds).** "Three quick yes/no's. (1) On-call rotation — one week in four, are you in? (2) Earliest start date? (3) Anything you'd want to ask me before we either move forward or close the loop?"

The third sub-question is the most undervalued in trades hiring. Candidates who ask zero questions are usually not serious; candidates who ask one or two specific questions ("how is your bench-test structured?" "do techs share trucks or each have their own?") are usually serious.

#### Compressed-variant scoring

After the call, the owner records one of three outcomes within 60 seconds:

- **ADVANCE** → schedule the full v1.0 conversation within 48 hours; the compressed call is the green light, not the hire decision
- **PASS** → document the reason (license fail / pay gap / weak scenario / no-show on questions) and close the loop with the candidate within 24 hours via text
- **HOLD** → re-screen in 30 days (candidate is technically capable but timing or pay is off this cycle); set the calendar reminder

#### Compressed variant tonal note

The compressed variant is faster but not curter. Open warm ("Thanks for calling back, I've got 10 minutes — let's see if we should keep talking"), close warm ("If you don't hear from me by Tuesday, follow up — I'd rather you ping me than wonder"). Speed should not feel like dismissal.

### SMS Pre-Screen Pattern (2-message exchange, no call)

For candidates who applied through Indeed / ZipRecruiter where the standard reply is an SMS auto-message, send a 2-message qualifier before booking the phone screen:

**Message 1 (within 30 minutes of application):**

> Hi [NAME] — [SHOP] in [CITY]. Saw your application for [ROLE]. Quick 2 questions before we book a call:
> 1. Is your [STATE] license active? (just yes/no)
> 2. Earliest you could start if we moved forward fast — 1 week / 2-3 weeks / 30+ days?

**Expected reply window:** 4 hours. No reply in 24 hours = the candidate has likely already accepted somewhere else.

**Message 2 (after candidate replies):**

> Thanks. Got time for a 10-min call [TODAY] [TIME] or [TOMORROW] [TIME]? I'll keep it tight.

The SMS pattern works because it respects the candidate's situation (they're on a job, can't take a call, can text in 30 seconds). It also surfaces three things in two exchanges: license status, urgency, and responsiveness.

### Apprentice-Specific Compressed Track

For apprentice candidates (no license, no journeyman experience), substitute Q4 above with this scenario:

**Q4 (apprentice).** "Walk me through the last time you fixed something at your house — anything. Doesn't have to be plumbing. What broke, and what did you do?"

The answer reveals: do they have hands? Do they think before acting? Do they finish what they start? An apprentice who says "I've never really fixed anything" is a different conversation than one who says "I rebuilt the carb on my brother's lawn mower last summer and now it runs."

Substitute Q3 (pay range) with:

**Q3 (apprentice).** "Apprentices typically start at $18-22 in this market. Are you good with that, knowing the path is $30+ in 3-4 years if you stick with it and pass your hours?"

Apprentices fail this question by either (a) low-balling themselves out of negotiating posture or (b) demanding journeyman pay on day one. Both are early signals. The answer you want is "$20 sounds fine to start; what does the bump cycle look like as I hit hours?"

### When to Skip the Compressed Variant Entirely

Some candidates warrant the full v1.0 conversation from the first call, no triage:

- A referral from a current tech, a vendor rep, or a competitor's owner ("she just left ABC Plumbing, you should call her")
- A candidate with documented credentials the shop has been hunting (medical gas certification, RPZ tester, master plumber for a market expansion)
- A candidate who did the SMS pre-screen perfectly and is being offered a phone screen as the formal step
- A candidate whose last 18 months show the exact role mix the shop is hiring for

For these candidates, skip the compressed variant and run the full v1.0 conversation. Treat the 8-12 question conversation as the respect signal — these candidates have other shops calling them too.

---

## v1.2 Additions (2026-06-01)

The v1.1 skill held at 9.5 across six consecutive evaluator cycles (04-25 ship through 05-25). The 05-18 Remaining Opportunities #2 named the v1.2 vector explicitly: integration with the New Tech Onboarding Curriculum v1.0 Day-1 fluency-baseline drills so the phone screen pre-flags which fluency drills the candidate will need on Day 1. v1.2 ships that integration plus two additional sub-sections (an AI-RX phone-screen adapter for shops using AI-RX platforms to do first-touch candidate triage, and a bilingual Spanish variant). All v1.0 and v1.1 content above is preserved unchanged.

### Onboarding-Fluency Pre-Flag Integration

The v1.0 Section 4 post-call summary template gains a new FLUENCY-DRILL PRE-FLAG block that maps the candidate's verbal responses to the technical-probe questions (Q4–Q11 of the v1.0 8–12 question script, or Q4 of the v1.1 compressed variant when the compressed variant was the only call) onto the seven Day-1 fluency drills defined in New Tech Onboarding Curriculum v1.0.

The seven drills (canonical names from New Tech Onboarding Curriculum):

1. **water-heater-sizing** — recovery rate, family size, fixture count, tank-vs-tankless decision logic, expansion-tank-on-closed-system, T&P, code venting
2. **gas-pressure-test sequence** — manometer placement, drop tolerance window, leak isolation, post-test purge and pressure restoration
3. **DWV-stack reading** — vent sizing, fixture-unit math, branch interval rules, stack-vent vs. main-vent decision
4. **drain-cleaning-method selection** — jet vs. snake vs. cable, kitchen vs. main vs. lateral, slab-on-grade vs. crawlspace access strategy
5. **PEX-A-vs-B identification** — visual and physical identification, expansion-fitting compatibility, temperature-rating fit, recall-list awareness
6. **code-fluency by jurisdiction** — UPC vs. IPC vs. local amendments, permit-pulling cadence, inspector-relationship norms in the shop's primary jurisdiction
7. **customer-pricing conversation** — explaining a $3,200 repair to a $500-expecting homeowner, good-better-best framing, walking back from a sticker-shock reaction without giving away margin

**Pre-flag scoring for each drill** — one of three states:

- **CALIBRATED** — The candidate's verbal answer demonstrates fluency. Day-1 drill can be a confirmation pass (5–10 minutes verifying the verbal answer against shop-specific tools and pricebook) rather than a full learning session. Save the Day-1 slot for one of the GAP drills.
- **GAP** — The answer is incomplete or directionally wrong in a way that a working tech would not be wrong. Day-1 drill is a true learning session (45–90 minutes with a senior tech). Note which sub-skill within the drill was the gap so the senior tech can target the session.
- **UNTESTED** — The screen did not surface enough signal to score (the call did not reach the relevant technical probe, or the candidate's answer was too short to assess, or the role-calibration was off — e.g., a drain-tech candidate answered the water-heater-sizing question with no exposure). Day-1 drill should be run cold (full 45–90 minute drill with no assumed baseline).

**Output addition — append to v1.0 Section 4 post-call summary as a new sub-block:**

```
─────────────────────────────────────────────────
🎯 DAY-1 FLUENCY-DRILL PRE-FLAG
   Source: phone-screen technical probes
   Target consumer: New Tech Onboarding Curriculum v1.0
─────────────────────────────────────────────────

  Drill                         | Pre-flag    | Senior-tech note
  ------------------------------|-------------|------------------------------
  water-heater-sizing           | CALIBRATED  | Named recovery rate + closed-system expansion logic on Q4
  gas-pressure-test sequence    | GAP         | Knows manometer, missed the post-test purge step — drill the purge sequence specifically
  DWV-stack reading             | UNTESTED    | Service-tech role; v1.0 script did not include the DWV question — run cold
  drain-cleaning-method         | CALIBRATED  | Strong jet-vs-snake judgment on Q5 scenario
  PEX-A-vs-B identification     | UNTESTED    | Not probed in the compressed variant — run cold
  code-fluency (TX)             | GAP         | Knew IPC chapter numbers but unsure on TX local amendments — needs a local-jurisdiction walkthrough
  customer-pricing conversation | CALIBRATED  | Q11 answer demonstrated good-better-best framing naturally

  Day-1 drill priority order (senior-tech allocation):
   1. gas-pressure-test sequence (GAP — purge sequence)
   2. code-fluency TX local amendments (GAP — sub-area-specific)
   3. DWV-stack reading (UNTESTED — service-tech baseline unknown)
   4. PEX-A-vs-B identification (UNTESTED — could be a 15-min bench show)
   5. water-heater-sizing (CALIBRATED — confirmation pass only)
   6. drain-cleaning-method (CALIBRATED — confirmation pass only)
   7. customer-pricing conversation (CALIBRATED — confirmation via role-play only)

  Pre-flag generated 2026-06-01 from phone screen 2026-06-01.
  Feeds: outputs/onboarding-curriculum-{candidate-last-name}-day1.md (when hired)
─────────────────────────────────────────────────
```

**Hardening rules for the pre-flag integration:**

- **The pre-flag is a calibration signal, not a hiring signal.** A candidate with 3 GAPs and 2 UNTESTED scores can still be a HIRE — the pre-flag tells the onboarding plan what to do on Day 1, not whether to make the offer. The hiring decision remains on the v1.0 / v1.1 HIRE / MAYBE / PASS recommendation line.
- **CALIBRATED is a confirmation pass, not a skip.** Senior techs sometimes read CALIBRATED as "don't run the drill at all." That misses the calibration value (verifying the verbal answer against the shop's tools and pricebook in the actual shop environment). Confirmation pass is 5–10 minutes, not zero.
- **UNTESTED is not a skill gap.** A drill that was not probed in the call is unknown, not absent. Day-1 drill is run cold (full session). The most common source of UNTESTED is role-calibration: a drain-tech candidate's call won't include water-heater-sizing probes.
- **The 7-drill canonical list must match the New Tech Onboarding Curriculum v1.0 list exactly.** If the onboarding curriculum's drill names or canonical list ever change (which they have not in nine months), this skill's pre-flag block must be updated to match. The two skills' lists are a single source of truth.
- **Per-shop overlay.** Shops with a customized onboarding curriculum (a shop that has added an 8th drill — septic, hydronic, fire-suppression) get the pre-flag extended automatically by reading the shop's `outputs/onboarding-curriculum-*.md` for the local canonical list. The default 7-drill list is the fall-back.

### AI-RX Phone-Screen Adapter

JSON schema mirroring the Pricebook Q&A v2.2.A canonical AI-RX schema. Lets the SMS pre-screen pattern from v1.1 plus the live 10-minute compressed variant from v1.1 run on any of the nine AI-RX platforms in the canonical platform list (Avoca, Pete & Gabi Olivia, ServiceAgent, Trillet, Marlie, ConvoCore, Voiceflow, My AI Front Desk, Ring-a-Ding OpenClaw). This is the tenth schema-implementing skill across the AI-RX adapter thread.

**Trigger:** Apply when the input includes `[AI-RX]` at the start of the candidate intake, *or* when the input is a JSON request payload with a `platform` field set to one of the nine canonical platform identifiers.

**Output schema (mirrors canonical AI-RX schema):**

```json
{
  "skill_version": "1.2",
  "intake_type": "sms_pre_screen | compressed_phone_screen | full_phone_screen",
  "candidate_id": "[shop's internal candidate ID]",
  "platform": "[avoca | petegabi | serviceagent | trillet | marlie | convocore | voiceflow | myaifrontdesk | ringading]",
  "candidate_disposition": "ADVANCE_TO_FULL_SCREEN | HOLD_30_DAYS | PASS_WITH_REASON | NO_REPLY_24H_AUTO_CLOSE",
  "knockout_results": {
    "license_status": "pass | fail | unverified",
    "dl_mvr_status": "pass | fail | unverified",
    "start_date_fit": "pass | fail | needs_negotiation"
  },
  "fluency_pre_flag_partial": {
    "drills_probed": ["..."],
    "calibrated_count": 0,
    "gap_count": 0,
    "untested_count": 7
  },
  "pay_range_signal": "in_range | above_range_small | above_range_large | below_range",
  "scope_limit_triggered": false,
  "scope_limit_reason": null,
  "escalation_to_human": false,
  "escalation_reason": null,
  "next_action_owner": "ai_rx | shop_office | hiring_owner",
  "next_action_by": "[ISO timestamp]"
}
```

**Scope-limit-pattern rules (matching the Superior Plumbing "Piper" programmable-scope-as-guardrail pattern used across the nine AI-RX-consuming skills):**

The AI-RX phone screen escalates to human within 30 seconds when any of the following surface:

- **Any license-claim-verification request.** The AI-RX should not be confirming a state license number is active. License lookups go through state portals that the AI-RX does not have credentials for. Mark `knockout_results.license_status` as `unverified` and escalate.
- **Pay-negotiation beyond the published band.** If the candidate asks about negotiating outside the published $X–$Y range, escalate. AI-RX should not be making counter-offers.
- **Callback from a current shop's tech.** Relationship-sensitive — the candidate is currently employed at a competitor's shop and is making a tentative inquiry. Human-only, AI-RX should not engage at all beyond confirming the call is welcome and scheduling a callback with the hiring owner.
- **Reference-check-style questions** ("I worked with so-and-so at ABC Plumbing, do you know him?"). Reference checks are a separate workflow and require human relationship handling.
- **Any complaint about a current or former employer.** Escalate to human — these conversations carry legal and tonal risk that the AI-RX should not navigate.
- **Apprentice candidates with active learning-disability disclosure.** Accommodation conversations require human discretion. Escalate to the hiring owner.
- **Any tonal request for "a person to talk to."** Mirrors the Blanchard counter-thesis hybrid-posture guidance from the 06-01 monitor cycle — when a candidate explicitly asks for a human, transfer within 15 seconds without restating the question.

**Hardening rules for the AI-RX phone-screen adapter:**

- **AI-RX runs only the SMS pre-screen and the compressed variant.** AI-RX should not run the v1.0 full 8–12 question screen. The full screen carries the hiring conversation; AI-RX is triage. If the candidate clears the compressed variant with ADVANCE_TO_FULL_SCREEN, schedule a human-led full screen within 48 hours.
- **The pre-flag block from v1.2.A is partial under AI-RX.** AI-RX-collected pre-flag scores cover only the drills that were probed in the compressed variant's Q4 scenario (typically 1 drill — water-heater-sizing for service candidates, drain-cleaning-method for drain candidates, DWV-stack reading for new-construction candidates, customer-pricing-conversation for apprentice candidates). All other drills are UNTESTED. The full human-led screen completes the pre-flag.
- **Hybrid-posture deployment.** Per the 06-01 hybrid-posture calibration framing applied across the AI-RX adapter thread: AI-RX phone-screen is the right answer for after-hours (4:45 PM Friday callback), overflow (3 candidates calling at once during business hours), and Indeed/ZipRecruiter auto-reply SMS pre-screen. AI-RX should NOT be the default business-hours candidate-call answer when a human is available. The hiring conversation is a relationship-building moment.
- **Bilingual flag passes through.** When the candidate's intake is in Spanish (`candidate_language: es`), the AI-RX adapter routes to the v1.2.C Spanish variant below.
- **Audit trail.** Every AI-RX-handled candidate touch emits to `outputs/candidate-screens/{date}-{candidate-last-name}-{intake_type}.md` for the office's hiring record, matching the v1.0 Section 4 save-path convention.

### Bilingual Spanish Variant

Joins the bilingual thread as the twelfth Spanish-anchored skill across four languages (en/es/pt/vi). Adds Spanish versions of the v1.1 SMS pre-screen pattern (two-message exchange in Spanish), the v1.1 compressed-variant five-question script, and the v1.0 Section 4 post-call summary template. The v1.0 full 8–12 question screen and Section 1 prep sheet remain English-default; both are produced for the screener and the screener will read either language; the customer-facing artifacts (SMS, scripted compressed-call open and close, post-call summary if shared with the candidate) get the Spanish treatment.

**Trigger:** Apply when `candidate_language` is set to `es` (sourced from the application form, the SMS pre-screen Q1 reply, or the candidate's stated preference on the initial call), *or* when the input includes `[ES]` at the start of the candidate intake. Default to English when the language field is unconfirmed. Never auto-detect from the candidate's name — many Hispanic candidates prefer English-default in professional contexts, and many non-Hispanic candidates have applied through Spanish-language job-board placements and prefer Spanish.

**Spanish SMS pre-screen pattern (mirrors v1.1 two-message exchange):**

> **Message 1 (within 30 minutes of application):**
>
> Hola [NOMBRE] — soy de [NOMBRE DEL TALLER] en [CIUDAD]. Vi su solicitud para [PUESTO]. Dos preguntas rápidas antes de programar una llamada:
> 1. ¿Su licencia de fontanero en [ESTADO] está activa? (sí o no)
> 2. ¿Cuándo podría empezar si avanzamos rápido — 1 semana / 2-3 semanas / 30+ días?

> **Message 2 (after candidate replies):**
>
> Gracias. ¿Tiene 10 minutos para una llamada [HOY] [HORA] o [MAÑANA] [HORA]? La mantendré breve.

**Spanish compressed-variant five-question script (mirrors v1.1):**

- **Q1 — Licencia + DL knockout.** "Rápidamente — ¿cuál es su número de licencia de fontanero en [ESTADO], y está su licencia de conducir en regla?"
- **Q2 — Último trabajo en sus propias palabras.** "Cuénteme del último servicio que atendió hoy" (o ayer, o la semana pasada).
- **Q3 — Rango de pago.** "Nuestro rango para este puesto es de $X a $Y por hora más bonificación por desempeño, vehículo de la empresa, [beneficios]. ¿Cómo se compara con lo que está buscando?"
- **Q4 — Escenario (calibrado por rol).** For service tech: "Un cliente llamó — el inodoro del segundo piso no para de correr, hay agua filtrándose al techo de la cocina abajo. La llave de paso principal está en el sótano. ¿Qué hace en los primeros 90 segundos?"
- **Q5 — Cierre con knockouts.** "Tres rápidos sí o no. (1) ¿Acepta la rotación de guardia — una semana en cuatro? (2) ¿Fecha de inicio más temprana? (3) ¿Hay algo que le gustaría preguntarme antes de avanzar o cerrar el caso?"

**Plumbing-Spanish terminology (calibrated per CSR Performance Debrief v1.1.C, Vendor Price Increase Customer Communication v1.1, and Pricebook Q&A v2.2):**

- *fontanero* — plumber (formal register, used in license documents across most US Spanish-speaking plumbing markets). Use in formal Q1 license-verification and SMS Message 1.
- *plomero* — plumber (colloquial register, common in Texas, Florida, Southern California, and most of Mexico). Use in conversational copy and the scenario probe; warmer than *fontanero* and more likely to land naturally with candidates from those regions.
- *licencia* — license. *Licencia de fontanero* — plumbing license.
- *fuga* — leak. *Tubería* — pipe. *Llave de paso* — shutoff valve. *Calentador de agua* — water heater. *Calentador instantáneo* / *sin tanque* — tankless water heater. *Trampa P* — P-trap. *Desagüe* — drain. *Registro de limpieza* — cleanout.
- *guardia* — on-call rotation (more natural than the literal *en-llamada*). *Semana de guardia* — on-call week.
- *bonificación por desempeño* — performance pay (not *paga por desempeño*; bonificación carries the variable-pay register correctly).
- *empezar* — to start (a job). *Disponibilidad* — availability. *Comenzar* is also acceptable; *empezar* is the more common register in this conversation.
- *llamada de seguimiento* — follow-up call. *Programar* — to schedule.
- *prueba en el trabajo* / *prueba práctica* — working interview / bench test.

**Hardening rules for the Spanish variant:**

- **Native-write the Spanish phrasing; do not back-translate from English.** Back-translation produces stilted phrasing that erodes the relationship signal that the trades hiring conversation depends on. Generate from the structured candidate intake, not from the English script output.
- **Bilingual-candidate handoff guidance.** Continue in Spanish from the first Spanish reply or stated preference. Do not switch back to English mid-conversation to "match the résumé language" — résumés are often submitted in English for ATS-compatibility regardless of the candidate's preferred conversational language. Follow the candidate's lead.
- **Don't-auto-detect-from-name rule preserved.** Surname-based language assumption is the most common bilingual-hiring failure mode. Use the explicit `candidate_language` field, the application-form selection, or the SMS pre-screen Q1 reply as the language signal — never the name.
- **Dialect-register choice (fontanero vs. plomero).** Use *fontanero* in formal verification copy (Q1, SMS Message 1) and use *plomero* in conversational warmth copy (Q4 scenario, Q5 close). The candidate's own usage in the first reply is the strongest dialect signal — match it from Message 2 onward.
- **State-license terminology by jurisdiction.** Some state license names have established Spanish translations (TX *Plomero con Licencia*, CA *Plomero C-36*, FL *Plomero CFC*); others do not. When in doubt, keep the state-licensed credential name in English (e.g., "TX Journeyman Plumber") inside the Spanish sentence — license names are quasi-proper-nouns and Spanish-speaking candidates expect the official term.

### Cross-Skill Reference Pointers (v1.2)

- **New Tech Onboarding Curriculum v1.0** — downstream consumer of the v1.2.A FLUENCY-DRILL PRE-FLAG block. The seven canonical drill names must match exactly; the per-shop overlay reads `outputs/onboarding-curriculum-*.md` for customized lists.
- **Pricebook Q&A v2.2.A** — canonical source for the AI-RX adapter schema and the nine-platform identifier list mirrored in v1.2.B.
- **CSR Performance Debrief v1.1.C, Vendor Price Increase Customer Communication v1.1, Pricebook Q&A v2.2 Spanish variant** — shared plumbing-Spanish terminology calibration, shared formal-vs-colloquial register decisions, shared don't-auto-detect-from-name rule, shared native-write discipline.
- **Lead Service Line Customer Briefing v0.9** (shipped 2026-06-01) — joins the bilingual thread as the eleventh Spanish-anchored skill; this skill v1.2.C is the twelfth.
- **Safety & Compliance Tracker v1.2.C** (shipped 2026-06-01) — shares the lead-handling endorsement awareness; a candidate who claims to hold a state lead-handling endorsement should be flagged in the pre-flag block for Day-1 verification.

