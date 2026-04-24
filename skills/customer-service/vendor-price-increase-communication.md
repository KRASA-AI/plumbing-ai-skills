---
name: "Vendor Price Increase Customer Communication"
category: customer-service
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~60–90 min per price-increase event to produce the decision matrix plus the full customer-comms packet; avoids the revenue leakage from pricing in-progress jobs at yesterday's cost and the trust damage from surprising members and pending-quote customers with a silent mid-cycle bump"
version: 1.0
last_eval_score: null
---

# Vendor Price Increase Customer Communication

## Purpose

Produce the complete decision matrix and customer-facing communication packet a plumbing shop needs when its supply houses and manufacturers push through a wave of price increases. In 2026 this is no longer a rare event — the PHCP-PVF industry has settled into quarterly waves, with April 2026 alone bringing Charlotte Pipe 10% on PVC/CPVC, Merit Brass 6–12% on brass fittings and nipples, Matco-Norca 2.5%, ICP Parts 4%, Honeywell 5%, IPEX 10%, Crane 5.3%, and National Comfort Products 7% — on top of continued upward pressure on copper, brass, and resin globally. The shop has to decide three things very quickly each time: which of its outstanding quotes, signed proposals, and in-progress jobs get grandfathered at the old price and which get re-quoted; how its membership-plan covered services and flat-rate pricebook items absorb the increase (or not); and how it tells customers about it without sounding like it is nickel-and-diming them.

This skill produces that full packet in six artifacts: a shop-internal decision matrix that routes every open commitment into grandfather / pass-through / absorb / re-quote; a customer-facing announcement for the shop's membership-plan holders and top commercial accounts (the ones who will notice first); a "your estimate is still honored through date X" confirmation template for customers sitting on an open quote; a pricebook-update briefing the dispatchers and office staff use when a customer asks "why did the price go up"; the technician kitchen-table script for the first two weeks after the new pricing goes live (customers will ask in person); and the internal tracking block for measuring the communication's landing — plan-cancel rate, quote-reconfirm rate, and the resulting margin delta.

The governing discipline across every artifact is transparency with restraint. The shop does not pretend the increase is not happening, does not blame "tariffs" or "inflation" as a shapeless excuse when the actual cause is two or three named manufacturers, does not apologize so much that the customer starts wondering if the shop is unstable, and does not bundle a sales upsell onto the price-increase note. The customer's question — *is this shop still fair, or are they using this event as cover?* — is what every piece of output has to answer cleanly.

The shop's upside here is quiet but real. Shops that communicate a price increase one week before it takes effect retain 97%+ of their membership-plan enrollees through the change; shops that let customers discover the increase on the next invoice lose 4–8% of members in the following 90 days. On pending quotes, clean "this price is honored through X" language converts roughly 65–75% of on-the-fence customers within two weeks — substantially higher than the baseline — because the deadline is credible and the communication is service-oriented, not salesy.

## When to Use

- One or more of the shop's primary supply houses or manufacturers has announced a price increase taking effect in the next 30–60 days
- The shop is planning its own pricebook refresh cycle and wants to get ahead of the inbound customer questions
- A material category the shop uses heavily (copper, brass, CPVC/PVC, fittings, water heaters, valves) has moved double-digits and the shop's current flat-rate pricing is now below cost on several jobs
- Annual or semi-annual pricebook refresh is due and the shop wants to frame it as a planned adjustment rather than a reactive one
- A specific large commercial account or property manager has flagged that they'll need advance notice of any pricing change per their service agreement

**Do not use this skill for:**

- A one-off material-cost spike on a single job — use Change Order Tracker to document the delta on that specific job, not a shop-wide communication
- Internal-only pricing strategy sessions that the customer will never see — that's a pricebook margin-analysis exercise for Pricebook Q&A
- A decision to increase labor rates independent of material costs — labor-rate changes have a different communication shape (workforce investment, insurance, technician retention) and should not be conflated with material pass-through
- Emergency pricing corrections (a pricebook error discovered mid-week, or a competitor doing something that forces a match) — those get handled quietly and individually, not with a shop-wide announcement
- Per-job markup negotiations with a single customer — that is a Change Order or Estimate Writer conversation, not a fleet-wide announcement

## Required Input

1. **The price-increase event itself (pull directly from the vendor's announcement, not from memory)**
   - Which manufacturers or supply houses are announcing — name each one, do not say "our suppliers"
   - Percentage increase by product category (PVC/CPVC pipe, brass fittings, copper fittings, valves, water heaters, HVAC parts, etc.), with the effective date for each
   - Which of those product categories the shop actually uses heavily — not every announced increase matters to every shop
   - Whether the increase is a list-price change, a surcharge, or a re-absorption of a previously itemized tariff surcharge (the communication shape differs)
   - Whether the shop has any pre-effective-date inventory it can hold at the old cost, and for how long

2. **The shop's open commitments**
   - Signed proposals or estimates that have not yet been scheduled or started — count, total dollar value, expiration dates
   - Jobs currently in progress where materials have not yet been ordered — count and expected completion
   - Active membership plans and their pricing structure — flat monthly fee, what's included, renewal date
   - Service-agreement commercial accounts that have contractual pricing protection — which accounts, what the agreement says about mid-term price changes, notice requirements
   - Warranty callbacks scheduled in the next 60 days — these should generally not be re-priced

3. **The shop's pricing policy decisions (the skill will help you make these, but it needs the starting posture)**
   - Default grandfather window for signed proposals (typical industry practice: 30 days from signature, or 14 days from the effective date of the increase, whichever is shorter)
   - Whether the shop is going to absorb part of the increase on membership-plan services or pass it through in full
   - Whether the shop's flat-rate diagnostic / service-call fee is moving (if yes, this is the piece customers notice most viscerally — separate from the material pass-through)
   - Target gross-margin floor the shop refuses to go below (typical: 55% on service, 40% on install)

4. **Shop context**
   - Shop name, owner or ops manager to sign the communication from
   - Primary service area (city and region)
   - Tone register (neighborhood / premium / value / old-school family) — must match every other customer communication the shop sends
   - Email and SMS platform the shop uses, and whether customers are segmented by channel preference
   - Whether a branded letterhead is available for the commercial-account print version

5. **Compliance guardrails**
   - Do not quote a percentage increase the shop has not verified in writing from the vendor's own announcement
   - Do not blame "the economy" or "inflation" in shapeless terms when the actual cause is two or three named manufacturers — the specific naming is what makes the note credible
   - For commercial accounts on service agreements, check the contract's change-notice requirements before the announcement goes out; some require 30, 60, or 90 days written notice and an opt-out window
   - Do not combine a price-increase announcement with a marketing promotion, a membership-upsell offer, or a review request in the same message

## Instructions

You are the Vendor Price Increase Communication drafter for a plumbing shop. Produce six artifacts in the order below. Do not skip sections — the packet's value is that the owner, office, and techs all work from the same single decision set.

### 1. Shop-Internal Price-Increase Decision Matrix

A one-page matrix the owner and ops manager work from to route every open commitment. Structure:

- **Increase summary (2–3 lines):** Which vendors are moving, the weighted-average effective increase on the shop's typical material mix (calculated, not guessed — for example: "Charlotte Pipe 10% on PVC/CPVC + Merit Brass 6% on fittings + Matco-Norca 2.5% on valves, weighted by our rolling-90-day spend mix, nets to an effective 6.8% increase on our typical residential service call material load and 5.1% on our typical install material load")
- **Effective date the shop is adopting** — usually aligned to the latest supplier effective date in the wave, not the earliest
- **Grandfather window** — explicit: "signed proposals dated before [date] are honored at the old price through [date]"
- **Absorb / pass-through decision by category:**
  - Membership-plan included services — absorb this wave; revisit at annual renewal
  - Flat-rate service calls — pass through on the new pricebook effective [date]; round to the nearest $5 or $10
  - Install quotes — pass through in full; new quotes from [date] forward reflect the new material cost
  - Warranty callbacks — always absorbed, no exception
- **Diagnostic / service-call fee** — separate line: moving or holding; this is the number customers see first
- **Service-agreement commercial accounts** — which accounts get a 30-day notice letter, which accounts are contractually protected through their next renewal
- **Inventory posture** — how much of the old-cost inventory the shop is holding and how long that buys breathing room

### 2. Customer-Facing Announcement — Membership Plan Holders and Top Commercial Accounts

Two paired drafts — an email for membership plan holders, and an email for the top 10–20 commercial accounts the shop knows will notice. Rules:

- Subject line under 65 characters; neutral and informative, not alarming. Bad: "IMPORTANT: Price Increase Notice." Better: "A note on materials pricing, effective [date]."
- Lead sentence states the change in one line with the effective date — do not bury it below a greeting and a paragraph of context
- Name the actual drivers specifically — two or three manufacturers by name, with category — rather than "rising costs" in shapeless generalities. Specific-and-cited is what makes the note credible; shapeless is what makes customers suspicious.
- State the shop's grandfather posture for open commitments in the same email, not in a separate follow-up — customers with a pending quote want to know they are protected in the same breath
- For membership-plan holders, explicitly tell them their monthly plan fee and included services are not changing — this is the single most important reassurance in the email and it belongs up high
- State what is changing for their non-plan work (flat-rate service calls, install quotes) and by roughly how much — a directional range like "3–7%" is fine if the shop does not want to publish exact line items
- Close with a low-stakes call to action ("If you have a quote open with us, reply to this email and I'll confirm your pricing is still honored") — do not attach a sales promotion or a membership upsell
- Signed by the owner or ops manager by name, not "the team"

Produce separate variants for:

- Membership plan holders (email — warm, reassurance-forward)
- Top commercial accounts and property managers (email — businesslike, with an attached printable PDF version on letterhead for AP-file keeping)
- Contractual service-agreement accounts (email plus a compliance-formatted notice letter if the agreement requires written notice; include the contractually required notice period explicitly)

### 3. Pending-Quote Confirmation Template

A short, warm template the office sends to every customer with an open quote that was dated before the increase's effective date. Rules:

- Subject line: "Your [water heater / drain / etc.] quote from [date] — honored through [date]"
- Body reconfirms the price quoted, the scope summary, the original quote date, and the shop's grandfather deadline
- Explicit statement that if the customer schedules the work on or before the grandfather deadline, the quoted price holds — no fine print, no catches
- Single call to action: reply to confirm a preferred week, or call the shop's direct line
- Do not restate the entire scope or line-item detail — that's in the original quote, and restating it invites re-negotiation
- Send individually, personalized with the customer's name and the specific job — not as a mass-merge; customers who feel this is a mail-merge assume the grandfather offer is performative

### 4. Pricebook-Update Dispatcher / Office Briefing

A short, internal-only briefing for the front desk, dispatcher, and CSR team to read on the morning the new pricebook goes live. Structure:

- What changed, in one paragraph, for internal comprehension (not customer-facing)
- The two or three customer questions the office should expect, with the approved plain-language answers for each:
  - "Why did my quote just go up?" — because material costs moved; we held the old price for [X] days after the manufacturers announced, and new quotes from [date] forward reflect the new cost
  - "Why is the service-call fee higher than last time?" — named increase on [material categories], effective [date]; the fee moved from $X to $Y
  - "Does my membership plan cost more now?" — no; your monthly fee and included services are unchanged; we revisit plan pricing at your renewal date
- What the office should NOT say:
  - Do not blame "inflation" in shapeless terms
  - Do not apologize excessively — one "I know pricing going up is never fun" is plenty; three is a credibility drain
  - Do not offer an ad-hoc discount on the phone to retain a wavering customer — that is an owner decision, not a CSR decision; escalate
- Escalation: which calls the CSR routes to the owner or ops manager (angry member threatening to cancel; commercial account invoking their service agreement; any customer asking for the shop's pricing policy in writing)
- The specific day the new pricebook is live and the day the grandfather window for pre-effective-date quotes closes

### 5. Technician Kitchen-Table Script (First Two Weeks Post-Effective)

A 45–60 second script the technician uses at the customer's kitchen table if the customer asks about the pricing on the invoice or the estimate. Rules:

- Acknowledge the customer's question without defensiveness — "good catch" is fine; "let me explain" is better than "I don't control pricing"
- Name the drivers specifically — same manufacturers the office is naming in the email
- Give the customer the shop's posture on their specific situation:
  - If they are a membership-plan holder: their plan pricing is unchanged
  - If they have a quote from the shop dated before the effective date: it's still honored through the grandfather window
  - If their current job material is priced at the new cost: here is what the category of material moved and here is what that means for their specific invoice
- Offer one low-stakes option if the customer seems to hesitate: "If you want to think it over, the quote I just gave you is good for 30 days — take a day" — do not improvise a discount
- Close with a question that lets the customer steer: "Do you want me to keep going today or come back when you've had a chance to think?" — customers who feel rushed into a price conversation leave the interaction distrustful even when they buy

Length discipline: the script runs 45–60 seconds at a normal speaking pace. Anything longer and the technician stops sounding confident and starts sounding like they are defending the shop.

### 6. Internal Tracking and Follow-Up

A simple tracker and the metrics the shop watches for the next 90 days to confirm the communication landed:

- **Membership-plan retention:** total members on the day of the announcement vs. total members on day 90; target floor is 97% retention through the event (mature shops typically run 96–99% through a well-communicated increase vs. 92–96% through a silent one)
- **Quote-reconfirm rate:** of the pending quotes sent the Section 3 template, how many reconfirmed and booked within the grandfather window (target: 65–75%, substantially above the baseline reply rate for a 30+ day-old quote)
- **Commercial-account notice compliance:** a simple yes/no list — did every service-agreement account that required written notice get it, with the contractually required lead time, on shop letterhead, delivered in the contractually required channel
- **Effective margin delta:** on invoices booked after the effective date, compare realized gross margin to the shop's target floor; escalate any job coming in below floor to the owner for review
- **Customer-sentiment signal:** unsolicited replies to the announcement email — "thanks for the heads-up" replies outnumbering "cancel my plan" replies by 10x or more is the signal that the communication landed
- **Pricebook discipline:** spot-check that flat-rate service-call and diagnostic pricing matches the announced new number on the invoices and proposals going out — drift here is what makes customers assume the shop is making it up as it goes
- Escalation: any membership cancellation attributed to the increase; any commercial account invoking a contractual opt-out; any invoice where the old pricebook value was used after the effective date (an internal error, not a customer-facing one — correct it and note the root cause)

## Example Output

**Scenario:** Cardinal Plumbing Co. (8 techs, Richmond, VA area; rolling-90-day material spend approximately $48,000/mo) is reviewing the April 2026 PHCP-PVF price-increase wave. The specific drivers hitting Cardinal's typical mix are Charlotte Pipe (+10% on PVC and CPVC effective March 26, 2026), Merit Brass (+8% weighted on brass nipples, fittings, and valves effective March 23), Matco-Norca (+2.5% effective April 1), and IPEX (+10% on select fittings effective April 6). Cardinal's Winchester supply house has absorbed the March moves through inventory carryover but is now passing the April adjustments through as-of-April 20. Cardinal holds 23 signed residential proposals dated before April 15 (total value $162,400), 41 active Preferred-tier membership plans at $22/month, and 6 service-agreement commercial accounts (3 require 30-day written notice per their agreements). The owner, Dan Harrelson, is adopting an effective date of May 5, 2026, holding signed proposals dated before April 15 at the old price through May 5, absorbing the increase on membership-plan-included services through the members' renewal dates, and moving the flat-rate service-call diagnostic fee from $89 to $95.

### 1. Shop-Internal Decision Matrix

**Increase summary.** Four named moves on Cardinal's typical material mix: Charlotte Pipe +10% PVC/CPVC effective 3/26, Merit Brass +8% weighted on fittings effective 3/23, Matco-Norca +2.5% effective 4/1, IPEX +10% on select fittings effective 4/6. Weighted by Cardinal's rolling-90-day spend mix (32% PVC/CPVC & plastics, 24% brass fittings and valves, 18% copper, 14% fixtures, 12% other), net effective move on residential service-call material load is 6.4% and on residential install material load is 5.8%.

**Effective date Cardinal is adopting.** May 5, 2026.

**Grandfather window.** Signed proposals dated on or before April 15, 2026 are honored at their quoted pricing through May 5, 2026. Proposals dated April 16 through May 4 are honored at their quoted pricing if scheduled and started by May 19, 2026 (a tighter two-week runway — these customers were quoted while Cardinal already knew the wave was coming). Proposals dated May 5 and forward are priced against the new pricebook.

**Category posture:**

| Category | Decision |
|---|---|
| Membership-plan included services (PRV check, main valve exercise, anode check, seasonal water heater flush, drain snake up to 50 ft) | Absorb through each member's renewal date; revisit at renewal |
| Membership-plan discounted non-included work | Pass-through at 10% discount off new pricebook (same discount structure, new base) |
| Flat-rate service-call diagnostic fee | Pass through; $89 → $95 effective May 5 |
| Residential install quotes | Pass through; new quotes from May 5 forward reflect new material cost |
| Commercial service calls (non-agreement) | Pass through; updated pricebook effective May 5 |
| Warranty callbacks | Absorb; no exception |
| Maintenance scheduled and confirmed before May 5 but performed after | Honored at old price if confirmed in the CRM with a job number before May 5 |

**Service-call diagnostic fee.** Moving from $89 to $95. This is the most-noticed number by repeat customers; surface it explicitly in the announcement rather than letting them discover it on the next invoice.

**Service-agreement commercial accounts.** Six active: River North Industrial Park, Hampton Court HOA, Saint Matthews Medical Office Building, The Dunlop Hotel, 421 Cary Street Restaurants, and Mid-Atlantic Storage. Three require 30-day written notice per their agreements (River North, Hampton Court, Dunlop). Send compliance-formatted notice letters dated April 24 so the 30-day window closes May 24, with the new pricing effective for work quoted after that date. The other three agreements renew in Q3 2026 and contractual pricing holds until then.

**Inventory posture.** Winchester Supply has confirmed Cardinal can pull old-cost pipe inventory through approximately May 10. This means the first five working days after May 5 the shop is running at slightly better margin than the new pricebook assumes — absorb any small cost-estimate misses in those five days rather than re-quoting customers.

### 2a. Announcement — Membership Plan Holders

**Subject:** A note on materials pricing, effective May 5

> Hi [First Name],
>
> Quick note from Cardinal Plumbing. Between late March and mid-April, a handful of the manufacturers we buy from — Charlotte Pipe, Merit Brass, Matco-Norca, and IPEX — pushed through price increases on plastic pipe, brass fittings, and valves. After running the math on our typical material mix, the net effect on our residential work is roughly a 6% bump on materials.
>
> We're holding the old pricing through May 5, then moving to our updated pricebook that day. Two specific things I want you to know:
>
> **Your Preferred plan is not changing.** Your $22/month fee stays the same, and all the services included in your plan — annual water heater flush, anode check, PRV check, main shutoff exercise, drain snake coverage — stay the same, at the same price, through your renewal date. We'll revisit plan pricing at renewal, not now.
>
> **Our diagnostic / service-call fee is moving from $89 to $95** effective May 5. That's the one number you'll likely notice the next time you book a call. Everything else on your plan and your plan discount on non-included work stays on the same structure.
>
> If you have a quote from us sitting in your inbox right now: it is still honored at the quoted price through May 5 if it's dated on or before April 15. Reply to this email if you'd like me to confirm your specific quote is protected — I'll reply the same day with a yes/no and a reconfirmation number.
>
> As always, thanks for being on the plan. It's the single best lever we have to keep pricing fair and predictable for you, and it is genuinely what helps us keep the same eight techs around for the long haul.
>
> Dan Harrelson
> Owner, Cardinal Plumbing Co.
> 804-555-0100

### 2b. Announcement — Commercial Accounts (Email)

**Subject:** Pricing notice — materials adjustment effective May 5, 2026

> Hi [Property Manager / Facilities Contact],
>
> Brief pricing notice on our work at [Property Name].
>
> Between late March and mid-April, Charlotte Pipe, Merit Brass, Matco-Norca, and IPEX pushed through price increases on plastic pipe, brass fittings, and valves ranging from 2.5% to 10% by category. Weighted against our typical commercial service material mix, the net effective adjustment works out to about 5.8%.
>
> Cardinal's updated pricebook takes effect on May 5, 2026. Specifically:
>
> - Any proposal we have given you dated on or before April 15, 2026 is honored at the quoted pricing through May 5. If you have an open proposal in that window and want to schedule before the deadline, please reply and we'll get it on the books.
> - Proposals dated April 16 through May 4 are honored through May 19, 2026 (two-week runway).
> - New quotes from May 5 forward reflect the updated pricebook.
> - Our flat-rate commercial service-call diagnostic fee is moving from $129 to $139.
>
> If your account has a service agreement with Cardinal: your contractual pricing protection is unchanged through your agreement renewal date. Where your agreement requires 30-day written notice of a pricing change, we are sending that notice separately today on letterhead, dated April 24, with the new pricing effective for work quoted after May 24.
>
> Happy to walk through any of this on a call. I know mid-year adjustments are never the note a facilities manager wants in their inbox, but I'd rather get ahead of it than have you find it on an invoice.
>
> Dan Harrelson
> Owner, Cardinal Plumbing Co.
> 804-555-0100

### 2c. Service-Agreement Notice Letter (Compliance Format, Letterhead)

> **[Cardinal Plumbing Co. letterhead]**
>
> April 24, 2026
>
> [Property Manager Name]
> [Property Management Company]
> [Address]
>
> **Re: Service Agreement — [Property Name] — 30-Day Notice of Pricing Adjustment**
>
> Dear [Name],
>
> This letter serves as formal 30-day written notice of a pricing adjustment under Section [X] of our Service Agreement dated [original agreement date], as amended. Pursuant to that section, Cardinal Plumbing Co. is notifying you of the following change:
>
> **Adjustment:** Effective May 24, 2026, Cardinal Plumbing Co.'s commercial service pricebook reflects a weighted average increase of 5.8% on materials, driven by announced price increases from Charlotte Pipe (10% on PVC and CPVC), Merit Brass (weighted 8% on brass nipples, fittings, and valves), Matco-Norca (2.5%), and IPEX (10% on select fittings), effective between March 23 and April 6, 2026. Our flat-rate commercial service-call diagnostic fee is moving from $129 to $139 on the same date.
>
> **Scope:** The adjustment applies to work quoted on or after May 24, 2026. Work in progress under a signed proposal and work quoted before May 24, 2026 are honored at the original pricing.
>
> **Your options under Section [Y] of the Agreement:** You may (a) accept the adjusted pricing and continue the agreement on its current term, (b) request a meeting to discuss scope adjustments, or (c) exercise any opt-out provision available under the Agreement. Please communicate your election in writing by May 20, 2026.
>
> Thank you for the continued partnership. Please reach me directly at 804-555-0100 or dan@cardinalplumbing.com with any questions.
>
> Sincerely,
>
> Dan Harrelson
> Owner, Cardinal Plumbing Co.

### 3. Pending-Quote Confirmation (Individual Outreach)

**Subject:** Your water heater quote from March 28 — honored through May 5

> Hi [First Name],
>
> Quick confirmation on the quote I sent you March 28 for the 50-gallon gas water heater replacement at [address]: the quoted price of $2,385 is still honored through May 5, 2026.
>
> Reason I'm reaching out: we're updating our pricebook on May 5 to pass through material increases from a handful of our manufacturers, and I want to make sure the quote you have in your inbox is protected from that change. As long as the work is scheduled to start on or before May 5, you're on the old pricing.
>
> If you'd like to move forward, just reply with a week that works for you — Tuesdays and Thursdays have the most availability right now — and I'll put you on the schedule and send a confirmation.
>
> No pressure, just wanted to get this cleared up for you before the change.
>
> Thanks,
>
> Marcus
> Cardinal Plumbing Co.
> 804-555-0100

### 4. Pricebook-Update Office Briefing (Internal, May 5 Morning)

> **Today, May 5, is effective day on the new pricebook.**
>
> **What changed.** Four of our manufacturers — Charlotte Pipe (PVC/CPVC +10%), Merit Brass (fittings +8% weighted), Matco-Norca (+2.5%), IPEX (fittings +10%) — pushed price increases between March 23 and April 6. After Dan ran the math, our residential material load is up about 6%, our install material load is up about 5.8%. We held the old pricing for three weeks to give our plan members and our open-quote customers a grandfather window. Today is when the new pricebook goes live.
>
> **What you'll hear from customers (and what to say):**
>
> *"Why did my service-call fee go up?"* — Our diagnostic and service-call fee moved from $89 to $95. That's Charlotte Pipe, Merit Brass, Matco-Norca, and IPEX all raising prices at once, so we adjusted the pricebook to match. We held the old pricing for three weeks so plan members and anyone with an open quote were protected.
>
> *"Does this mean my Preferred plan is costing more?"* — No. Your monthly $22 is unchanged and all your included services — water heater flush, anode check, PRV check, main valve exercise, drain snake coverage — are the same price to you at your renewal. We don't touch plan pricing mid-term.
>
> *"My quote from [date] — is that honored?"* — If the quote is dated on or before April 15, it's honored through today; if the work starts on or before today we hold the quoted price. If the quote is dated between April 16 and May 4, it's honored through May 19. I can pull the quote number and confirm if you have it handy.
>
> **What not to say:**
>
> - Don't say "everything is going up because of inflation." Name the manufacturers — Charlotte Pipe, Merit Brass, Matco-Norca, IPEX. Specificity is what makes the note credible.
> - Don't apologize more than once per call. One "I know pricing going up is never fun" is plenty. Three is a credibility drain.
> - Don't offer a discount on the phone to keep a wavering customer. Route that to Dan or Colleen.
>
> **Escalate to Dan immediately:**
>
> - Any plan member saying "I want to cancel my membership"
> - Any commercial account invoking a contractual opt-out
> - Any customer asking for our pricing policy in writing
>
> **Grandfather window closes May 5** (today) for quotes dated on or before April 15. Any quote in that batch still unbooked as of today moves to the new pricebook for any subsequent quoting.

### 5. Technician Kitchen-Table Script

> **Customer:** "Huh — the price is a little higher than I remember from last year."
>
> **Technician:** "Good catch — you're right that our pricing moved. Four of the manufacturers we buy from — Charlotte Pipe, Merit Brass, Matco-Norca, and IPEX — raised their prices by five to ten percent each on plastic pipe, brass fittings, and valves between late March and early April. We held our pricing for three weeks so our plan members and anyone with an open quote were protected, and then we updated the pricebook on May 5. On the materials for this job specifically, you're looking at [brief specific: about $X more than last year] on the parts. Labor is unchanged.
>
> [If they're a plan member:] Your monthly plan and all the services included in it are not changing — we don't touch plan pricing mid-term. Your plan discount on the non-included work is the same structure against the new base.
>
> [If they have an older quote:] If you have a written quote from us dated on or before April 15, that price is still honored through today. Let me know if you want me to pull it and we'll go off that number instead.
>
> If you want to think it over, the quote I just gave you is good for 30 days — you can take a day or two. Do you want me to keep going today or come back when you've had a chance to think it over?"

### 6. Internal Tracking — 90-Day Window (May 5 through August 3)

| Metric | Target | Day 30 | Day 60 | Day 90 |
|---|---|---|---|---|
| Preferred-plan retention (baseline 41 members) | ≥ 97% (40 of 41) | [fill] | [fill] | [fill] |
| Quote reconfirm rate (pending quotes dated ≤ 4/15, N=23) | 65–75% scheduled by 5/5 | [fill] | — | — |
| Commercial service-agreement notice compliance | 3 of 3 with 30-day window | Confirm delivered 4/24 | — | — |
| Effective gross margin on post-5/5 invoices (service) | ≥ 55% floor | [fill] | [fill] | [fill] |
| Effective gross margin on post-5/5 invoices (install) | ≥ 40% floor | [fill] | [fill] | [fill] |
| Unsolicited email replies to announcement | "thanks for heads-up" : "cancel" ≥ 10 : 1 | [fill] | — | — |
| Invoices issued with pre-5/5 pricebook in error | 0 | [fill] | [fill] | [fill] |

**Escalations (for Dan's desk, weekly during the 90-day window):**

- Any plan cancellation citing the price-increase communication as a reason — Dan calls personally within 48 hours
- Any commercial account requesting a meeting under their agreement opt-out provision
- Any job closing below the 55%-service / 40%-install gross-margin floor
- Any week where more than one customer asks for Cardinal's pricing policy in writing — indicates the communication did not land for that cohort, adjust messaging

---

## Notes for the Shop

- Name the manufacturers. "Charlotte Pipe, Merit Brass, Matco-Norca, and IPEX" lands differently than "our suppliers." The specificity is what separates a credible pass-through from an opportunistic shop using "inflation" as cover.
- One week of lead time on the communication is the single highest-leverage thing the shop can do. Two days is too short — customers feel sprung on. Three weeks is too long — the communication fades before the effective date arrives. One week with the effective date clearly stated is the sweet spot.
- Do not absorb the increase on membership-plan-included services forever. Absorb through the member's renewal date, then revisit at renewal with a full plan review. Members have different inflation tolerance at renewal than they do in the middle of a term.
- The diagnostic / service-call fee move is the number customers notice first. Surface it in the announcement, not in the fine print. Burying it invites "are they hiding other stuff too?" suspicion.
- For commercial accounts on service agreements, check the written notice requirement before the announcement goes out — some agreements require 30, 60, or 90 days. Missing the contractual window is a breach, not a paperwork error.
- On the kitchen table, a technician who sounds defensive about pricing makes the customer distrust the shop more than the customer distrusted the pricing itself. Calm, specific, named-drivers — that's the posture.
- Do not bundle a membership-plan upsell, a review request, a spring-tune-up promotion, or any other marketing offer into the price-increase email. Single topic, single call to action, signed by name. Mixed-purpose emails read as manipulative on this specific topic.
- Pair this skill with Estimate Writer (for re-quoting post-grandfather), Change Order Tracker (for in-progress jobs that cross the effective date and need documentation), Invoice Follow-Up Sequence (for the three-week window when customers are especially price-sensitive about invoices), and Pricebook Q&A (which holds the authoritative new line-item pricing).
- If the shop has not done a price-increase communication in the last 18 months, expect a higher-than-normal retention risk on the first one. Subsequent waves are less destabilizing because customers have learned the shop's pattern is transparent and scheduled, not ad-hoc.
