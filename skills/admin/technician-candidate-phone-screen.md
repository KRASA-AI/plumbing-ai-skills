---
name: "Technician Candidate Phone Screen"
category: admin
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~20 min/candidate"
version: 1.0
last_eval_score: 9.2
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
