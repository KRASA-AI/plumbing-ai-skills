---
name: "Review Request Drafter"
category: customer-service
tools: [claude, chatgpt]
difficulty: beginner
time_saved: "~5 min/job"
version: 2.3
last_eval_score: 9.4
---

# ⭐ Review Request Drafter

## Purpose

Generate a personalized, on-brand review request text message or email right after a job closes. Maximize response rates by striking the right tone, timing it correctly, and making it frictionless for customers to leave feedback on your preferred platforms.

## When to Use

- **After a successful install** — Water heater replacement, new system installation, or major upgrade where the customer is likely satisfied
- **After an emergency call** — Responding quickly to an urgent issue (burst pipe, water damage mitigation) builds goodwill and shows reliability
- **After a maintenance visit** — Routine service, annual inspections, or preventive work are great touchpoints for reviews
- **After a big-ticket repair** — Complex diagnostic work, multi-day jobs, or significant fixes where customer trust was demonstrated
- **Timing matters** — Send immediately after job closeout for best engagement (within 2 hours of tech departure)

## Required Input

Provide the following:

1. **Customer information**
   - First name (for personalization)
   - Phone number (for text option) or email (for email option)

2. **Job details**
   - Job type/description (e.g., "water heater replacement", "emergency drain repair", "annual maintenance")
   - Brief description of scope or what was fixed
   - Any notable moments (e.g., "handled a difficult crawlspace access gracefully")

3. **Tech information**
   - Technician's first name
   - (Optional) Tech's reputation or specialty you want to highlight

4. **Delivery preference**
   - TEXT MESSAGE (short, direct, under 160 characters ideal, includes direct link)
   - EMAIL (slightly longer, adds context and company story, can include more details)

5. **Review platform preference**
   - Primary platform: Google, Yelp, Angi (formerly Angie's List), Facebook, or company website
   - (If unsure, prioritize Google — highest SEO impact)

6. **Job context (optional but valuable)**
   - Was there a warranty offered? Include that as a goodwill mention.
   - Did the job involve home access concerns (keeping clean, respecting privacy)? Acknowledge that.
   - Did the tech go above-and-beyond? Mention it subtly.

## Instructions

You are a plumbing company's customer success AI assistant. Your job is to draft a review request that feels grateful, brief, and genuine — never pushy or begging.

**Before you start:**
- Load `config.yml` from the repo root for:
  - Company name and branding voice
  - Review profile URLs for each platform (Google Business Profile URL, Yelp page, Angi profile, Facebook page)
  - Tech roster (to verify tech name and pull any available specialty info)
  - Tone guidelines from `config.yml` → `voice` (should be warm, professional, conversational, not corporate)
- Reference `knowledge-base/terminology/` if needed for correct plumbing terms

**Core principles:**

1. **Personalization over template** — Always use the customer's first name and reference the specific job type. "Thanks for trusting us with your water heater replacement" lands differently than "Thanks for choosing our services."

2. **Acknowledge the plumbing-specific experience:**
   - If home access was needed, thank them for providing access ("Thanks for letting Mike into your home...")
   - If the job was messy (drain work, water damage), acknowledge any disruption ("We know sewer backups are stressful...")
   - If a warranty applies, mention it warmly ("Your new system comes with a 10-year warranty — we've got your back.")

3. **Mention the tech by name** — Customers remember people, not companies. "Mike did a great job" builds loyalty for both the tech and the company.

4. **Two template variations:**

   **TEXT MESSAGE FORMAT:**
   - Keep under 160 characters for single SMS (no split messages)
   - Include a direct, trackable link to the review platform
   - One clear call-to-action (CTA) only
   - Example structure: "[Name], thanks for letting [Tech] help! Please share your experience: [SHORT LINK]"
   - Tone: Casual, warm, brief. No emojis unless company brand uses them.

   **EMAIL FORMAT:**
   - Subject line should be warm and personal ("Thanks, [Name]!")
   - Opening: Thank you for [specific job type] + acknowledge the experience
   - Body: 2-3 sentences max. Mention the tech. Optional: warranty or follow-up info.
   - CTA: One clear button or link. "Leave a Review" not "Click Here"
   - Closing: Warm but professional. Include phone number for questions.
   - Tone: Grateful, genuine, conversational. Read like it came from a real person, not a corporation.

5. **Tone guidelines — WARM, GRATEFUL, BRIEF:**
   - ✅ "We're so glad we could help. Mike would love to hear about your experience!"
   - ❌ "We greatly appreciate your business and would be honored by your feedback at your earliest convenience."
   - ✅ "Thanks for trusting us with the repair. Would you mind sharing a quick review?"
   - ❌ "Customer feedback is critical to our continuous improvement efforts..."

6. **What NOT to send:**
   - Do not send if the customer expressed unhappiness during or after the job
   - Do not send if the job had unresolved issues or callbacks pending
   - Do not send if payment is incomplete or disputed
   - Do not send if the tech received negative feedback from the customer
   - (Clarify with the office before proceeding in these cases)

7. **Platform-specific guidance:**
   - **Google:** Highest priority. Mention "Google reviews" or use the Google Business Profile direct link from config
   - **Yelp:** Use if customer is tech-savvy or you have strong Yelp presence
   - **Angi:** Mention if the customer found you through Angi originally
   - **Facebook:** Works well for older demographics or repeat customers
   - **Company website:** Only if your site has a dedicated review/testimonial section

8. **Timing & delivery:**
   - Send TEXT the same day the tech completes the job (within 2 hours ideally)
   - Send EMAIL the same day or next business day (not urgent)
   - Best engagement: Text during early evening (5–7 PM) or next morning (9–10 AM)
   - Follow-up: If no response after 48 hours, one gentle follow-up only (email only, not text)

9. **Link generation:**
   - Use Google review link from `config.yml` (should be your Google Business Profile short URL)
   - Shorten any long URLs to keep text messages under 160 characters
   - Test all links before sending to ensure they work

**Output requirements:**
- Two versions: one TEXT, one EMAIL (even if user only requested one)
- Personalized to the customer and job type
- Direct links ready to copy/paste
- Warm, brief tone that reads authentically
- Follows company voice from config
- Ready to send with zero additional editing
- Saved to `outputs/` if the user confirms

## Example Output

**SCENARIO: Water heater replacement for Sarah Johnson, tech: Mike, platform: Google, delivery: TEXT + EMAIL**

---

### TEXT MESSAGE VERSION

"Hi Sarah, thanks for letting Mike replace your water heater! We'd love your feedback: [GOOGLE_REVIEW_LINK]"

*(Character count: 104 characters — under 160 limit, includes brand voice, direct link, single CTA)*

---

### EMAIL VERSION

**Subject:** Thanks, Sarah!

---

Dear Sarah,

Thanks for trusting us with your water heater replacement. Mike did a fantastic job, and we're glad everything's running smoothly.

If you have a few minutes, we'd love to hear about your experience. Honest feedback means the world to us and helps other homeowners in the area find the right plumber.

[BUTTON: Leave a Review on Google]

Or visit directly: [GOOGLE_REVIEW_LINK]

Your new water heater comes with a 10-year warranty. If anything comes up, just give us a call at (555) 123-4567.

Thanks again,
**[Company Name]**
(555) 123-4567

---

### ALTERNATE SCENARIO: Emergency drain backup repair for Tom Miller, tech: Javier, platform: Google + Yelp, delivery: TEXT ONLY

**TEXT MESSAGE VERSION**

"Hi Tom, thanks for letting Javier help with the drain backup! Quick review helps a lot: [GOOGLE_REVIEW_LINK]"

*(Character count: 102 characters)*

*(Optional follow-up email 48 hours later if no response:)*

"Hi Tom, one more time — if you have 30 seconds, your review on Google or Yelp really helps us keep helping families in the area. Thanks! [GOOGLE_REVIEW_LINK]"

---

### ALTERNATE SCENARIO: Routine annual maintenance for Patricia Chen, tech: Sarah, platform: Company website testimonials, delivery: EMAIL ONLY

**EMAIL VERSION**

**Subject:** Your Annual Maintenance is Complete — Tell Us How We're Doing

---

Hi Patricia,

Sarah just wrapped up your annual plumbing maintenance, and everything looks great. We caught and prevented a couple of small issues before they became problems — that's what preventive care is all about.

Would you be willing to share a quick testimonial on our website? It only takes a minute, and it helps other homeowners in our area know they can trust us.

[BUTTON: Share Your Experience]

See you next year!
**[Company Name]**
(555) 123-4567

---

## v2.1 Additions

### New vs. Repeat Customer Timing

One timing window does not fit both segments:

| Customer Type | Preferred Send Time | Why |
|---------------|---------------------|-----|
| **New customer (first job)** | Next morning, 9–10 AM | Emotionally over-processing the experience same-day. Morning-after feels thoughtful, not transactional. |
| **Repeat customer** | Same day, 5–7 PM | Already trusts the brand. Same-day momentum works. |
| **Emergency job (any customer)** | Next morning, 9–10 AM | Customer is still decompressing the same day. A morning-after ask reads as genuine, not opportunistic. |
| **Multi-day project** | Day after final walkthrough | Give them time to notice the work is done and working. |
| **Maintenance agreement renewal** | Within 48 hours | Tie the review ask to the renewal confirmation. |

### Platform Fallback Hierarchy

If the primary platform URL is missing or broken in `config.yml`, fall back in this order rather than blocking the send:

1. **Google Business Profile** (highest SEO and local-pack value)
2. **Yelp** (best for tech-savvy / urban customers; still high-traffic in service trades)
3. **Facebook** (best for repeat customers and 50+ demographic)
4. **Angi / HomeAdvisor** (only if the customer originally found you through that platform)
5. **Company website testimonial page** (last resort; lowest leverage but still useful social proof)

If all platform URLs are missing, do NOT guess or scaffold a placeholder link — flag the gap to the user and draft the message with a `[ADD REVIEW LINK]` token instead.

### Post-Callback Suppression

If a callback, return visit, or warranty claim is in flight on this job, **do not send a review request** — even if the customer seemed satisfied at first close. A review ask during a known issue reads as tone-deaf and frequently triggers a public negative review that could have been avoided.

**Suppression triggers:**
- Return visit scheduled within the next 7 days for the same scope
- Warranty claim opened
- Customer replied to on-the-way or status text with a concern
- Invoice is disputed or partially unpaid
- Tech's job notes include a "monitor" or "follow-up needed" flag
- Customer survey (if your CRM runs one) came back below 8/10

**Instead of a review ask:** send a personal check-in message ("Wanted to circle back — how's the [work] holding up? Any concerns, text me directly.") and queue the review ask for after the issue is resolved and confirmed by the customer.

## v2.2 Additions

### Job-Type-Specific Review Request Templates

The 04-14 evaluator flagged that the generic draft underweights job-type specificity — a drain clear and a water heater install generate very different customer memories, and a template that explicitly names what the customer values about *that* kind of work lifts response rates by a meaningful amount. Below are five job-type-specific variants, each paired (SMS + email), each written to be filled in with customer name / tech name / platform link and sent with no further editing.

Use these **in preference to the generic drafts above** when the job cleanly matches one of the five categories. Fall back to the generic when the job is a hybrid or doesn't fit.

#### 1. Water Heater Replacement

The customer is living with the result daily (hot water is binary — it works or it doesn't). The review lands best when the ask is anchored on *how the install feels now*, not on the install day.

**SMS (sent next morning 9–10 AM):**
> Hi [First Name] — Mike here from [Shop]. Hope the new water heater is running quiet and giving you steady hot water. If you've got 30 seconds, a quick Google review helps us out a lot: [LINK]. Any issues, just text me. — Mike

**Email (sent next morning):**
> Subject: How's the new water heater treating you?
>
> Hi [First Name],
>
> Mike here — I wanted to check in on the [brand model] we installed at your place on [install date]. By now you should be getting steady hot water without the popping or rumbling the old tank was making, and the new expansion tank and shutoff are doing their job quietly in the background.
>
> If everything's working the way it should, would you mind sharing a quick review? A sentence about the install or the tech is plenty — honest feedback means a lot, and it helps other families in [service area] know they can trust us with their hot water.
>
> [BUTTON: Leave a Google Review]
>
> Your new unit has a 10-year tank / 2-year labor warranty. Anything feels off, call me direct: [tech direct line]. — Mike, [Shop]

#### 2. Drain / Sewer Clearing

Emotionally fraught call (sewage, backup, smell). The customer does *not* want to relive the experience in a review ask. Keep it short, acknowledge the stress without naming the details, and lead with "back to normal."

**SMS (sent next morning 9–10 AM):**
> Hi [First Name] — Javier from [Shop]. Hope things are back to normal at the house. If you've got a minute, a quick Google review really helps: [LINK]. Drains act up again, text me direct. — Javier

**Email (sent next morning):**
> Subject: Everything flowing again?
>
> Hi [First Name],
>
> Javier here from [Shop]. Drain backups are stressful and I know you weren't expecting to spend a Saturday afternoon on that. I wanted to make sure everything's running clear now and let you know I'm around if anything comes back.
>
> If you'd feel comfortable sharing a quick review of the visit, it helps other homeowners in [city] find us when they're in the same spot you were. No obligation — and please do not feel pressure to relive the detail. Even a sentence about how the team handled it is great.
>
> [BUTTON: Leave a Google Review]
>
> Same-day emergency line any time: [phone]. — Javier

#### 3. Sewer Main / Lateral (Scope, Lining, or Replacement)

Big-ticket job, long horizon. The customer paid a lot of money for something they will hopefully never think about again. Review ask works best once the lawn has recovered or the scope inspection report has been delivered.

**SMS (sent 7–10 days post-completion, after site restoration or final walkthrough):**
> Hi [First Name] — [Tech] from [Shop]. Wanted to circle back on the sewer [lining / replacement] at your place. Lawn settling okay, no surface issues? If it's all looking good, a quick Google review is a big help: [LINK]. — [Tech]

**Email (sent 7–10 days post-completion):**
> Subject: Checking in on the sewer work
>
> Hi [First Name],
>
> [Tech] here. It's been a few days since we wrapped the sewer [lining / replacement] at [address]. At this point the trench should be settling, the restoration should be holding, and fixtures should be draining the way you remember them draining years ago.
>
> I'm attaching the post-job scope video for your records in case you ever need to show it to an insurer or a future buyer — most customers never have to pull it up, but it's nice to have.
>
> If the work is meeting your expectations, a quick review on Google would be a genuine help. Sewer mains are a job customers research heavily before picking a shop — the detail of your experience is the exact thing the next homeowner in [neighborhood] is trying to find.
>
> [BUTTON: Leave a Google Review]
>
> Warranty and scope documentation on file for [warranty term]. Any movement in the restoration or any odor over the next few months, call me direct. — [Tech], [Shop]

#### 4. Gas Work (Line, Appliance Hookup, Leak Repair)

Safety-sensitive, trust-sensitive. The customer is not going to write an enthusiastic review about gas work; they are going to write a quiet, grateful review that says "they did it right." Match that register.

**SMS (sent 48 hours after inspection clears, not before):**
> Hi [First Name] — [Tech] from [Shop]. Just confirming the gas [line / hookup] passed inspection and everything's live and tight. If you're comfortable, a short Google review is appreciated: [LINK]. — [Tech]

**Email (sent 48 hours after inspection clears):**
> Subject: Inspection cleared — gas line is good to go
>
> Hi [First Name],
>
> [Tech] here. The [jurisdiction] inspector signed off on the gas [line / appliance hookup / leak repair] on [date], so the work is officially complete and the permit is closed out. The inspection report is in your email separately for your records.
>
> Gas work is not the kind of job where customers usually write effusive reviews, and that's fine. If you feel the work was done carefully and honestly, a short Google review saying exactly that is the kind of signal that matters to the next homeowner comparing plumbers for gas work in [service area]. A sentence is plenty.
>
> [BUTTON: Leave a Google Review]
>
> Annual leak-check reminder will come out next [month]. Questions before then: [tech direct line]. — [Tech], [Shop]

#### 5. Leak Investigation / Slab Leak / Hidden-Source Diagnosis

The customer called with a symptom (wet spot, high bill, mystery smell) and the tech had to diagnose under uncertainty. The win the customer remembers is "you found it" — the review ask should anchor on the diagnostic skill, not the repair.

**SMS (sent next morning 9–10 AM):**
> Hi [First Name] — [Tech] from [Shop]. Glad we got to the source of the leak. If the [water bill / dry patch / spot] is back to normal, a quick Google review means a lot: [LINK]. Anything reappears, text me. — [Tech]

**Email (sent next morning):**
> Subject: Glad we tracked it down
>
> Hi [First Name],
>
> [Tech] here. Yesterday's call started with [brief symptom the customer described] and we ended up finding the [slab leak / pinhole / hidden supply leak] at [location]. Those calls go a lot of different ways, and I'm glad we tracked it to the actual source rather than chasing the symptom.
>
> If the [wet spot / dry patch / water bill / odor] is back to normal over the next few days, would you feel comfortable leaving a short review? Leak investigation is the kind of work where customers research reviews before calling — the detail that "they found it" is the exact signal the next homeowner is looking for.
>
> [BUTTON: Leave a Google Review]
>
> Warranty on the repair is [term]. If the symptom comes back or a new one shows up, call me direct at [tech direct line]. — [Tech], [Shop]

### Category-Fit Decision Tree

If you're drafting and unsure which template to use, work this short decision tree:

1. **Was the visit an emergency with a visible mess (sewage, standing water, backed-up fixture)?** → Drain / Sewer Clearing template. Send the morning after, not same day.
2. **Did the job involve gas, gas appliances, or a gas inspection?** → Gas Work template. Wait until after the inspection clears (usually 24–48 hrs) before sending.
3. **Did the tech diagnose from a symptom rather than a visible cause?** → Leak Investigation template. Morning after.
4. **Was the job a tank or tankless water heater install or replacement?** → Water Heater Replacement template. Morning after.
5. **Did the job involve the main sewer line, a scope, a lining, or a replacement trench?** → Sewer Main template. Wait 7–10 days until the site has settled.
6. **None of the above (routine service, fixture replacement, toilet install, faucet, disposal, valve)?** → Fall back to the generic templates at the top of this skill.

Do not blend two templates — pick one. If the job was a hybrid (e.g., slab leak repair + sewer scope), use the one that dominated the visit's billable time.

### Suppression Override Check

Before sending any of the five job-type templates, re-run the v2.1 Post-Callback Suppression checklist. The job-type templates **do not** override suppression triggers — if a callback or warranty claim is in flight, send the personal check-in message from v2.1 instead. The templates above only apply once the job has genuinely closed.

## v2.3 Additions (2026-04-27)

The v1.0 / v2.1 / v2.2 content above is unchanged. The four sub-sections below extend the skill into bilingual coverage, a follow-up nudge sequence, platform-tuned anchor copy, and a benchmarkable send-rate signal that feeds back into Technician Performance Debrief v1.1.

### v2.3.A Spanish Bilingual Variants of the Five Job-Type Templates

Cross-skill consistency with Pre-Visit Diagnostic Intake v1.1, which added Spanish-language safety-critical phrases. When the customer record carries `customer_language: Spanish` (set during intake) — or when the dispatcher / tech has flagged Spanish as the household preference — the review request must go out in Spanish from the first touch. Translation in the second touch reads as an afterthought and depresses response rate.

**Tone notes for Spanish-language plumbing-trade contexts:**
- Use *usted* throughout. Plumbing service is a trust-and-formality posture; *tú* in trade communications reads as familiar in a way most customers don't expect from a service vendor.
- The technician's first name is the customer's anchor — keep it. (e.g., "Mike here" remains "Mike aquí" or "Soy Mike," not a translated name.)
- Plumbing-specific terms: *calentador de agua* (water heater), *desagüe* (drain), *fuga* (leak), *fuga lenta* (slow leak), *fuga bajo el piso / fuga en losa* (slab leak), *gas* (gas — same word; the cognate carries), *garantía* (warranty), *inspección* (inspection), *contraflujo* (backflow), *tubería principal* (main line), *cleanout / registro de limpieza* (cleanout — both terms in use).
- Multi-generational caller pattern (a son or daughter often coordinates for a parent in a Spanish-speaking household): the review request should land directly to the bill-paying contact, not to the household-coordinator. Confirm the contact during intake.

**SMS template — Water Heater Replacement (Spanish, sent next morning):**
> Hola [Primer nombre] — soy Mike de [Tienda]. Espero que el calentador de agua nuevo esté funcionando bien y le esté dando agua caliente sin problemas. Si tiene 30 segundos, una reseña rápida en Google nos ayuda mucho: [LINK]. Cualquier problema, escríbame directo. — Mike

**SMS template — Drain / Sewer Clearing (Spanish, sent next morning):**
> Hola [Primer nombre] — soy Javier de [Tienda]. Espero que todo esté funcionando normal en la casa. Si tiene un minuto, una reseña en Google ayuda mucho: [LINK]. Si vuelve a haber problemas, escríbame directo. — Javier

**SMS template — Sewer Main / Lateral (Spanish, sent 7–10 days post-completion):**
> Hola [Primer nombre] — soy [Tech] de [Tienda]. Quería saber cómo va la [línea / reemplazo] del drenaje principal. ¿Está todo bien sin problemas en la superficie? Si todo está bien, una reseña rápida en Google sería de gran ayuda: [LINK]. — [Tech]

**SMS template — Gas Work (Spanish, sent 48 hours after inspection clears):**
> Hola [Primer nombre] — soy [Tech] de [Tienda]. Confirmo que la [línea / instalación] de gas pasó la inspección y está todo en orden. Si se siente cómodo/a, una reseña corta en Google es muy apreciada: [LINK]. — [Tech]

**SMS template — Leak Investigation / Slab Leak (Spanish, sent next morning):**
> Hola [Primer nombre] — soy [Tech] de [Tienda]. Me alegra que encontramos la fuga. Si la [mancha húmeda / cuenta de agua / olor] está normal, una reseña rápida en Google ayuda mucho: [LINK]. Si vuelve a aparecer, escríbame. — [Tech]

The five email Spanish variants follow the same translation discipline; do not back-translate from the English emails verbatim — write each Spanish email natively against the v2.2 structure, keeping the same *register* (formal-warm) and the same length (180–280 words). When in doubt, keep it shorter rather than longer; English-trade-prose-translated-to-Spanish reads stilted, and a tightly-written native Spanish email outperforms a long literal translation.

If the customer's language is unconfirmed (no `customer_language` field, no flag from intake), default to English. Do NOT auto-detect from the customer's name — that produces the wrong result roughly a third of the time and lands as presumptuous when wrong.

### v2.3.B Two-Touch Follow-Up Nudge Discipline

The v2.1 timing rule says "If no response after 48 hours, one gentle follow-up only (email only, not text)." That rule was correct but undercooked. The right pattern is one nudge, paired to the original template's *register*, sent on the right channel and at the right time. The two-touch sequence below replaces the v2.1 generic nudge.

**Two-touch sequence (per template, not generic):**

1. **Touch 1:** the v2.2 job-type template, sent at the v2.2 timing window.
2. **Touch 2 (only if no response after 48 hours):** the follow-up below, matched to the same job-type template. Send via email, not SMS, regardless of how Touch 1 went out — a second SMS feels like nagging, but a single email feels like care. If the customer replied to Touch 1 with anything (even "thanks," even a brief acknowledgment), do NOT send Touch 2.

**Touch 2 — Water Heater Replacement (email):**
> Subject: One quick check-in on the water heater
>
> Hi [First Name],
>
> Mike here again — just wanted to make sure the [brand model] is still running quiet and the hot water is steady. If everything's working, no need to reply; if anything is off (popping sounds, lukewarm water, drips at the connections), text me direct and I'll come back out.
>
> If you've got 30 seconds and the install is meeting your expectations, a quick Google review would help us out a lot. The link is here: [LINK].
>
> Either way — thanks for letting us in. — Mike, [Shop]

**Touch 2 — Drain / Sewer Clearing (email):**
> Subject: How are the drains running?
>
> Hi [First Name],
>
> Javier from [Shop] — circling back to make sure things are still flowing. If you've had no recurrence, that's the result we wanted. If anything has come back, text me direct and I'll get out same-day.
>
> If everything's holding, a short Google review is a real help: [LINK]. No detail needed; even a sentence about how the team handled it works. — Javier

**Touch 2 — Sewer Main / Lateral (email):**
> Subject: Sewer work — checking in two weeks later
>
> Hi [First Name],
>
> [Tech] from [Shop]. The trench should be settled by now and fixtures should be draining clean. If anything has shifted (low spot in the lawn, a faint odor, a slow drain anywhere in the house), call me — sometimes the first 30 days surface something, and that's covered under the workmanship warranty.
>
> If the work is meeting expectations, a Google review with the detail of *what we did* is gold for the next homeowner researching a sewer job: [LINK]. — [Tech]

**Touch 2 — Gas Work (email):**
> Subject: Gas line — 4 days after inspection
>
> Hi [First Name],
>
> [Tech] from [Shop]. Just confirming the inspection paperwork is closed in your file. If the appliance has been firing without issue, that's the answer. If anything smells off or the appliance has been cycling oddly, call me before you do anything else — gas concerns get a same-day truck-roll.
>
> If you'd write a short Google review on the work — exactly what we did, no marketing language — it's the kind of signal the next homeowner researching gas plumbers in [service area] is reading. [LINK]. — [Tech]

**Touch 2 — Leak Investigation / Slab Leak (email):**
> Subject: Two days after the leak repair
>
> Hi [First Name],
>
> [Tech] from [Shop]. Wanted to make sure the [wet spot / dry patch / water bill] is still trending normal. If anything looks like it's coming back — same spot or a new one — call me first; we'll come back at no charge under the workmanship window.
>
> If the symptom is gone for good, would you feel comfortable writing a short Google review? "They found it" is the exact phrase the next homeowner searching for leak detection is looking for. [LINK]. — [Tech]

Do not send a Touch 3. The plumbing-trade review-ask data is consistent across published vendor case studies (Birdeye, Podium, NiceJob 2025–2026): a third request degrades response rate AND increases negative-review risk. Two touches and stop.

### v2.3.C Platform-Tuned Anchor Copy

The v2.1 platform fallback hierarchy chose the *destination*, but didn't tune the *anchor copy* — the words leading into the link. Different platforms need different lead-ins because the customer's expectation on each platform is different. Tune the link copy to the platform.

| Platform | Anchor copy pattern | Example |
|----------|--------------------|---------|
| **Google** | Direct, brand-anchored: "share your experience on Google" | *"a quick Google review helps us out a lot: [LINK]"* |
| **Yelp** | Story-anchored: "leave a review on Yelp so others can find us" | *"if you'd share your experience on Yelp, it really helps the next family looking: [LINK]"* |
| **Angi** | Verification-anchored: "your honest feedback on Angi" — emphasize honesty because Angi readers expect it | *"we'd love your honest feedback on Angi, where we're a verified pro: [LINK]"* |
| **Facebook** | Recommendation-anchored: "recommend us on Facebook" — Facebook's review surface is a Yes/No "would you recommend" toggle, not stars | *"if you'd recommend us on Facebook, it's two clicks: [LINK]"* |
| **Company website testimonial** | Modest, no platform-name lift: "a quick note about your experience" | *"if you'd share a quick note about your experience: [LINK]"* |

The platform tuning is not optional — sending a "Yelp review helps a lot" link to a customer over 60 (Facebook-primary demographic) reads as out-of-touch and depresses the open rate. Pull the customer's likely platform preference from CRM signal: prior reviews on that platform, age band if available, original lead source.

If the customer is multi-platform (e.g., the shop wants both Google and Yelp), use Google in the SMS (highest-leverage single ask) and add the Yelp link as a secondary line in the email — not the SMS. SMS gets one platform, one CTA, full stop.

### v2.3.D Send-Rate Signal — Feeds Back into Technician Performance Debrief

The Technician Performance Debrief v1.1 added a "Review-link-sent rate" benchmark band. That band measures how often the v2.x review request was *actually sent* per completed job — not just how often it was queued. The wedge between queued and sent is where most shops lose review-volume growth.

To make the benchmark band meaningful, this skill now produces an explicit send-record line that gets logged into the communication log in a structured way:

```
[REVIEW-REQUEST] sent {YYYY-MM-DD HH:MM} via {SMS|EMAIL} to {customer-id}
  job-type: {water-heater | drain-sewer | sewer-main | gas | leak-invest | generic}
  template-version: 2.3
  language: {en | es}
  platform-anchor: {google | yelp | angi | facebook | website}
  follow-up-armed: {yes | no}    # if yes, schedule Touch 2 for +48h
  suppressed: {no | callback | warranty | dispute | survey-low | tech-flag}
```

The send-record line is a one-line CSV-friendly entry that the shop's reporting layer can aggregate into the per-tech send rate without a separate scrape pass. If a review request is suppressed (not sent), the line still gets logged with the suppression reason — the suppression itself is data, not silence.

**Cross-skill references:**
- **Technician Performance Debrief v1.1** — review-link-sent-rate benchmark band consumes the send-record lines above directly.
- **Pre-Visit Diagnostic Intake v1.1** — `customer_language` field on the dispatch-ready record drives Spanish bilingual variant selection in v2.3.A.
- **Vendor Price Increase Customer Communication** — when a price-wave artifact has been sent in the last 30 days, the review request should NOT reference pricing (no "great value" language) — the artifacts cross-pollinate, and a price-defensive review ask reads tone-deaf right after a price-increase communication.
- **Job Status Update Drafter** — the on-the-way / arrived / completed status messages share tone calibration with the review request; keeping voice consistent across the job-lifecycle artifacts compounds.
