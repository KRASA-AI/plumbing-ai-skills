---
name: "Product Recall Customer Outreach"
category: customer-service
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~45 min per recall event to produce the full outreach packet; avoids the legal and reputational cost of handling a recall ad-hoc and unlocks the service-call attach rate that comes from being the shop that notified the customer"
version: 1.0
last_eval_score: null
---

# Product Recall Customer Outreach

## Purpose

Produce the complete outreach and on-site protocol packet a plumbing shop needs when a product the shop has sold or installed gets a CPSC, manufacturer, or regulatory recall. This is a recurring, entirely predictable event for any shop that has been in business more than a few years — tankless water heaters (VESTA VST October 2025, Navien 2018, Rheem and A.O. Smith historical), tank-type water heaters, pressure-reducing valves, expansion tanks, polybutylene and defective PEX fittings, faucets failing NSF/ANSI 61 lead limits (the Amazon-sold BASDEHEN / Qomolangma / HGN / Kicimpro / VFAUOSIT / NICTIE recalls in 2024–2025), backflow preventers, and fill valves all hit the recall cycle with regularity. The shop's choices are: ignore it and carry the liability, react ad-hoc and lose time and confidence on each event, or run a repeatable workflow that protects the customer, the technician, and the shop at once.

This skill produces that repeatable workflow in six artifacts: a shop-internal triage summary, an SMS plus email to known-affected past customers, a phone script for the inbound calls the recall is about to generate, a technician-facing on-site stop-use / tag-out protocol for CO and life-safety recalls, the handoff language that draws the correct line between what the shop can do and what the manufacturer is responsible for, and an internal tracking block for measuring the outreach.

The governing discipline across every artifact is honesty and restraint. The shop does not speak for the manufacturer, does not promise repair timelines or replacement terms it has not verified in writing, does not minimize a life-safety hazard to keep a customer relaxed, and does not bolt a sales upsell ("while we're there, want a quote on a new tankless?") onto the recall conversation — customers who feel pitched during a safety event stop trusting the shop, and the long-tail cost of that is larger than any same-visit revenue.

The shop's upside here is real but quiet. Customers who get a warm, competent recall notification from the plumber who installed their unit — before the manufacturer's letter, or alongside it — refer three to five times more often than customers who handle the recall on their own, and the shop becomes the default choice when the customer eventually replaces the unit.

## When to Use

- A recall affects a product the shop has sold, installed, or serviced — use even if the shop only sold a handful of units, because the liability profile is binary
- A customer calls or emails the shop asking "I just got this letter — what do I do?" and the shop does not have a ready script
- A technician arrives at a service call and identifies a recalled unit running in the home, whether or not the customer knows
- The shop is doing a pre-season or annual outreach pass (for example, before a summer tankless-flush campaign) and wants to cross-reference the install history against any open CPSC recalls
- The shop's supply house or manufacturer rep notifies the shop of a recall before it hits CPSC publicly

**Do not use this skill for:**

- Warranty defects that are not a formal recall — use the standard warranty-claim process and the Invoice Follow-Up Sequence / Change Order Tracker instead
- Recalls on products the shop has never sold or touched — outreach without a genuine install link is spam and invites legal exposure
- Situations where the shop is itself the defendant in a product-liability matter — route to the owner and counsel, not to a customer-outreach queue
- Customers who have already opted out of shop marketing and have no known affected install — a recall is not a loophole around the opt-out
- Non-safety product notices (voluntary service bulletins, firmware updates, cosmetic defects) that do not carry an injury or property-damage risk — these can be handled as a regular Job Status Update or a single-line email, not the full recall packet

## Required Input

1. **The recall itself (pull directly from the source, not from memory)**
   - Official source: CPSC recall number and URL, or the manufacturer's recall page
   - Hazard type in plain language — carbon monoxide, fire, scald, lead leaching, water damage, structural failure — and one sentence of mechanism
   - Affected products: brand, model numbers, serial-number ranges, date-of-manufacture ranges, any color or label markers
   - Remedy offered by the manufacturer: free repair, free replacement, refund, or hybrid
   - Manufacturer contact: toll-free, email, recall-registration URL, hours of operation
   - CPSC-required consumer action (typical pattern: stop use immediately for CO / fire hazards; continue use with CO alarm coverage for lower-risk recalls; stop drinking / cooking use for lead-leach recalls)

2. **The shop's exposure**
   - Count of units the shop sold or installed that fall in the affected range (if known from invoicing / CRM)
   - Rough install-date distribution (which years of past customers are most affected)
   - Whether any affected units are on current maintenance-plan accounts (these are the highest-trust, highest-priority outreach group)
   - Whether any affected units are in commercial accounts (different escalation path — usually goes to the property manager / PM / GC)
   - The shop's own posture: did the shop recommend this brand proactively, was it a supply-house default, was it a customer-supplied unit that the shop installed for labor only (the tonal answer changes)

3. **Shop context**
   - Owner / ops manager to sign the outreach from
   - Shop phone number that is answered in business hours and the after-hours / emergency line
   - Whether the shop is offering a complimentary on-site inspection for affected units (recommended for life-safety recalls even when the manufacturer is providing the repair)
   - Any jurisdictional nuance — CO-detector laws, state consumer-protection notice requirements, state water-quality notice obligations

4. **Compliance guardrails**
   - Do not quote a remedy, timeline, or financial term on the manufacturer's behalf that the shop has not verified in the manufacturer's own published recall notice
   - Do not tell a customer that their existing homeowner's or property insurance will or will not cover anything related to the recall — refer that question to their carrier
   - Do not bundle the recall outreach with a marketing message, coupon, or unrelated service offer in the first-touch SMS or email

## Instructions

You are the Product Recall Outreach drafter for a plumbing shop. Produce six artifacts in the order below. Do not skip sections — the skill's value is that the shop has a single packet to execute from rather than a half-built set of pieces that pull everyone's attention during the crunch of a recall.

### 1. Shop-Internal Recall Triage Summary

A 6–10 line summary the owner and dispatcher can read in 60 seconds to know what they are dealing with. Include:

- The hazard in one sentence, in plain language, with the mechanism and the severity level (CO / fire / scald = life safety; lead / chemical leach = delayed health; water damage = property only)
- The exact brand and model numbers affected, plus serial-range language
- The manufacturer's remedy in one sentence, with the direct line the customer must call or URL the customer must register on
- The shop's exposure count — total affected installs, plus the count on current maintenance plans and the count in commercial accounts
- The timing posture — "customers have likely already received the manufacturer's letter / customers have not yet been notified"; adjust tone accordingly
- One flag line: any known safe-to-use-with-caution guidance (for example, CO alarms present, cold-water-only use) that the shop will repeat consistently across every channel

### 2. Past-Customer Outreach: SMS + Email

Two drafts, one SMS and one email, each paired so a customer on either channel gets the same information with the same tone. Rules:

- SMS under 320 characters (two messages max). Include the hazard category in plain language within the first 40 characters; do not bury the safety information below a greeting
- Email subject line under 65 characters. The subject must signal safety information, not marketing — for a CO recall something like "Safety notice: tankless water heater we installed"
- Neither message may start with "Good news!" or any other upbeat framing. The tone is neighborly, serious, and brief
- Name the product by brand and model, not "your water heater" — the customer may have two units in the home and need to know which one is affected
- State the manufacturer's remedy verbatim where possible, with the manufacturer's direct contact and the CPSC recall URL
- Explicitly name whose responsibility the repair is ("the manufacturer, VESTA.DS, is providing the repair at no cost") and what the shop is offering ("we will come out at no charge to confirm the model and serial, check the venting, and tag the unit for the technician the manufacturer sends")
- Include the immediate-action instruction from the CPSC notice ("Please stop using this unit" for life-safety, "You can keep using the unit but please ensure your CO alarms are working" for lower-severity)
- Single clear call to action — one phone number OR one booking link, not both
- Opt-out language on SMS only if the shop is obligated under the state's consumer-notice rules; recall notices are generally not "marketing" under TCPA but err conservative

Produce separate variants for:

- Residential customers with the affected unit still within shop warranty
- Residential customers outside shop warranty but still reachable (historical install)
- Commercial / property-manager accounts (email primary, different tone, include unit count affected in the account)

### 3. Inbound Call + Email Response Script

A short, branching script the front desk, dispatcher, or AI receptionist runs when a customer reaches out saying "I got a letter about my water heater / faucet / etc." Structure:

- Opening acknowledgment (one sentence; calm, confirming the shop is aware of the recall)
- Verification step — ask for the model number and serial, and ideally the date of install; confirm whether the unit is in the affected range before continuing
- Branching:
  - **Confirmed affected, life-safety recall (CO / fire)**: reinforce the stop-use instruction; confirm the customer has working CO alarms; offer to dispatch a technician today or tomorrow to tag the unit and, on CO-risk units, to shut off the gas supply at the appliance valve
  - **Confirmed affected, non-life-safety recall (lead-leach, slow defect)**: reinforce the limited-use guidance from the CPSC notice; offer the no-charge inspection; avoid urgency language that the hazard does not actually warrant
  - **Confirmed not affected** (model or serial not in range): reassure clearly and document the call; offer to send a short email confirming the check was done
  - **Customer uncertain about model / serial**: walk them through how to find the data plate; offer to send a tech out if they cannot locate it safely
- Handoff language — what the manufacturer is responsible for (repair, replacement, refund), what the shop will do (inspection, tag-out, coordination with the manufacturer's authorized technician when applicable), and what the customer needs to do personally (register with the manufacturer; do not skip this step or the free repair will not be authorized)
- Close — confirm the next step, name a specific next date or time, offer the shop's direct line, and log the call

### 4. Technician On-Site Stop-Use / Tag-Out Protocol

The protocol the technician follows when dispatched to an affected unit. This is the shop-side operational script, not a customer document. Structure:

- Pre-arrival: confirm the affected model and serial from the office record; bring a CO meter, a lockout/tag-out card, an appropriate shut-off tool, and a printed copy of the manufacturer's recall notice
- On arrival: greet the customer, confirm the unit location, and request permission to inspect
- Verification: match the data-plate model and serial number to the recall notice in writing; photograph the data plate; photograph any visible defect (cracked exhaust, damaged vent, corroded fitting, serial-range match); file the photos to the job record
- For CO-hazard recalls: meter the area around the unit and the nearest living-space vent; if CO is elevated (> 9 ppm ambient per most jurisdictions), evacuate and follow the shop's CO-incident protocol rather than continuing the recall workflow
- Tag-out: affix a bright, customer-visible tag naming the hazard, the manufacturer, the date, and the technician; for gas units, close the appliance gas valve and tag it; for electric units, pull the disconnect or throw the breaker and tag it; for water-contact recalls, explain the limited-use guidance and do not turn off service unless the customer consents
- Customer briefing: walk the customer through the data-plate match, show the photos, point to the tag, and restate — verbally and in writing — that the manufacturer is responsible for the repair, here is their direct line, here is the recall URL, here is what to expect from them (typical repair window, what they will send)
- Leave-behind: a printed one-page summary the customer can hand to the manufacturer's authorized technician when they arrive
- Back at the shop: enter the job into the recall tracker (section 6), flag the customer for a 30-day check-in, and forward the data-plate photos to the shop's records

### 5. Handoff-to-Manufacturer Language (Customer-Facing)

A short block of plain language, suitable for repeating on the phone, in the email, and on the tech's leave-behind document, that draws the responsibility line:

- What the manufacturer is responsible for (the remedy — free repair, replacement, or refund per the CPSC notice), and the direct contact
- What the shop is doing on the customer's behalf (the inspection, the tag-out, coordinating with the manufacturer's authorized technician if the shop has that relationship)
- What the customer must do personally (register their unit with the manufacturer at the recall URL — the manufacturer will not process the repair without this step)
- What the shop cannot do (diagnose or repair the recalled defect under the manufacturer's warranty authority; the shop is not authorized to issue replacement parts or serial-level remedy approvals)
- The insurance question deflected cleanly — refer to the customer's homeowner's policy carrier for coverage questions

Write this in the voice of the shop, not the manufacturer. Do not attempt to reassure the customer that the manufacturer will be fast or thorough if the shop does not know that to be true.

### 6. Internal Tracking + 30-Day Follow-Up

A simple tracker the shop maintains across the life of the recall event, plus the follow-up cadence:

- One row per affected customer: name, address, date of install, model, serial, date of shop outreach, channel (SMS / email / phone), customer response category (confirmed receipt and will call manufacturer / asked shop to coordinate / declined contact / unreachable)
- 30-day check-in column: date the shop followed up to ask "did the manufacturer get you squared away?" — the single highest-leverage thing a shop can do on a recall is the unprompted 30-day follow-up; it is what the manufacturer almost never does and what customers remember
- Escalation column: any customer whose manufacturer-side remedy stalled beyond 60 days, flagged for the owner to personally reach out and advocate
- Replacement-opportunity column (handled carefully): customers who decline the manufacturer repair and elect to replace the unit entirely — these convert to sales jobs but are booked through the normal estimate flow, not via the recall outreach channel; separation of intent is important
- Metrics to watch:
  - Outreach coverage: % of known-affected installs contacted within 7 days of the recall's publication
  - Confirmed-remedy rate at 30 / 60 / 90 days: % of contacted customers who have completed the manufacturer's repair
  - Customer-sentiment signal: unsolicited reply rate (a "thanks for letting me know" reply on the outreach is a strong signal and typically precedes a referral within a year)
  - Replacement conversion (tracked separately from outreach metrics)
  - Incident rate: any reported injury, property damage, or near-miss on an affected unit — this is a legal-escalation trigger, not a marketing metric

## Example Output

**Scenario:** Cardinal Plumbing Co. (8 techs, Richmond, VA area) installed approximately 47 VESTA VST-brand tankless water heaters between June 2020 and May 2024, sourced through two regional plumbing supply houses. On October 16, 2025, CPSC published recall 26-026: VESTA.DS Recalls VST Brand Tankless Water Heaters Due to Carbon Monoxide (CO) Poisoning Hazard and Risk of Serious Injury and Death, covering series VT, VR, and VR Plus, models VRS/VRP/VTS/VTP-150 and -199, with approximately 36,700 units sold in the US. The hazard mechanism is a cracking exhaust duct that allows combustion gases to escape inside the home. The remedy is a free repair by a certified technician dispatched by VESTA.DS; consumers are directed to 888-505-5525 or recallrtr.com/condensingwaterheater. It is now April 2026 and Cardinal's owner wants to run a structured outreach pass against the 47 known-affected customers. Of those, 9 are on Cardinal's Preferred-tier maintenance plan, 4 are commercial accounts (2 multi-family properties and 2 restaurants), and 34 are standard residential. Owner to sign from: "Dan Harrelson, Owner, Cardinal Plumbing Co."

### 1. Shop-Internal Recall Triage Summary

Active CPSC recall 26-026 on VESTA VST tankless water heaters. Hazard is carbon monoxide poisoning — the exhaust duct can crack and vent combustion gases into the home. This is a life-safety recall; stop-use is the CPSC-directed posture for residential installs without verified CO alarm coverage. Affected models are VRS/VRP/VTS/VTP-150 and -199, plus "Plus" variants, in series VT, VR, and VR Plus. Remedy is a free repair performed by a VESTA-certified technician; customers must register at recallrtr.com/condensingwaterheater or call 888-505-5525. Cardinal's exposure: 47 known installs, of which 9 are on the Preferred maintenance plan (highest priority — we have a current relationship and likely a recent visit), 4 are commercial (2 multi-family, 2 restaurants — route to property managers and restaurant owners, not unit occupants), and 34 are standard residential. Manufacturer's letter has started hitting mailboxes in the last two weeks based on three inbound calls we have already taken; assume approximately half our list has received the notice and half has not. Consistent guidance across every channel: if the home has working CO alarms in sleeping areas and near the unit, the customer can leave the unit in place while they schedule the manufacturer's repair; if CO alarm coverage is uncertain, the prudent posture is gas-valve shut-off and cold-water-only use until the repair is complete.

### 2a. SMS — Residential, Maintenance-Plan Customer (High Trust)

> Safety notice on your VESTA VST tankless water heater from Cardinal Plumbing. CPSC recall for a carbon monoxide risk — cracked exhaust duct. VESTA is doing free repairs: 888-505-5525 or recallrtr.com/condensingwaterheater. Please register your unit with them today. We'll come out at no charge to check your venting and confirm your CO alarms while you wait on their tech. Call Cardinal at 804-555-0100. — Dan

### 2b. Email — Residential, Maintenance-Plan Customer

**Subject:** Safety notice — VESTA VST tankless water heater we installed at your home

> Hi [First Name],
>
> This is Dan at Cardinal Plumbing. I want to make sure you saw the CPSC recall that came out in October on the VESTA VST tankless water heater — the model we installed at your home in [install month / year]. The issue is a cracked exhaust duct that can release carbon monoxide into the home. CPSC recall number 26-026; more at cpsc.gov/Recalls/2026/VESTA-DS-Recalls-VST-Brand-Tankless-Water-Heaters.
>
> What VESTA is doing: a free repair performed by one of their certified technicians. You need to register your unit directly with them to get the repair scheduled — they will not process it without the registration. Phone is 888-505-5525 (8:30 a.m. to 6 p.m. ET, Monday through Friday), or register online at recallrtr.com/condensingwaterheater. Please do this today if you haven't already.
>
> What Cardinal is doing: because you're on our Preferred plan, we want to come out at no charge to confirm the model and serial against the recall list, verify the exhaust run visually, and check that your CO alarms are in working order before VESTA's technician arrives. This is peace of mind, not a sales visit. If our visit uncovers any reason to shut the unit down until VESTA's tech gets there, we will handle the tag-out and the gas-valve shut-off and walk you through what to do for hot water in the meantime.
>
> The one thing I want to be clear on: the repair itself has to come from VESTA's authorized technician. Cardinal is not authorized to perform the recall repair under VESTA's warranty, even though we installed the unit. That's a manufacturer rule and not something we can work around.
>
> Any questions, please reach me directly at 804-555-0100 or reply to this email.
>
> Dan Harrelson
> Owner, Cardinal Plumbing Co.

### 2c. Email — Commercial Account (Multi-Family Property)

**Subject:** Safety notice — VESTA VST tankless water heater at [Property Name]

> Hi [Property Manager],
>
> Cardinal Plumbing reaching out with a life-safety recall notice on the VESTA VST tankless water heater we installed at [Property Name and Address] on [install date]. CPSC recall 26-026 was published October 16, 2025 for a carbon monoxide hazard — the unit's exhaust duct can crack and release CO into the space. This affects [unit count] units at your property: [list of unit numbers or install locations].
>
> VESTA.DS is providing the repair at no cost through a certified technician they dispatch. Each affected unit has to be registered individually at recallrtr.com/condensingwaterheater or by calling 888-505-5525. I would recommend registering all [unit count] this week and asking VESTA for a single consolidated scheduling window so their technician can knock them all out in a visit or two rather than dragging this across months.
>
> From our side, Cardinal can come out this week at no charge to verify each unit's model and serial, check the exhaust run, and confirm the CO alarm coverage in each affected space. Given this is a multi-family property, I would prioritize getting eyes on the units with sleeping areas closest to the install location first.
>
> Let me know when works and I'll put it on the schedule. Please do not wait on the CO alarm check — if you have any uncertainty about alarm coverage in any affected unit, it's worth getting the gas valve closed at that unit until we confirm.
>
> Dan Harrelson
> Owner, Cardinal Plumbing Co.
> 804-555-0100

### 3. Inbound Call + Email Response Script

> **Opening (dispatcher):** Thanks for calling Cardinal — yes, we're aware of the VESTA VST tankless recall, and I'm glad you called us. Do you have a moment so I can walk through it with you and make sure we get you set up correctly?
>
> **Verification:** Could you grab the data plate off the front of the unit when you have a second? I'm looking for the model number — something starting with VRS, VRP, VTS, or VTP — and the serial number. If you can't get to it safely we can send a tech out.
>
> **If confirmed affected:**
>
> The recall is for a carbon monoxide risk — the exhaust duct on your unit can crack and let combustion gases into the home. Two things I want to mention right now. First, do you have working CO alarms in your hallways or near bedrooms? [If yes: good, that's your safety layer while you schedule the repair.] [If no or uncertain: I would very much recommend either getting an alarm set up today or letting us come shut the gas valve at the unit so you're not on combustion until VESTA's tech gets out.]
>
> Second, the way the recall works is VESTA is paying for the repair and sending their own certified technician to do it. You need to register the unit directly with them — they won't process it without that step. The number is 888-505-5525 or the website is recallrtr.com/condensingwaterheater. Can you write that down or would you rather I text it to you?
>
> Here's what we can do for you, at no cost: come out in the next day or two, confirm the model and serial against the recall list, check the exhaust run for any visible cracking, and make sure your CO alarms are good. If we see anything that makes us want to shut the unit down until VESTA's tech gets there, we will tag it out and walk you through the hot-water situation in the meantime.
>
> The only thing I want to be straight about: Cardinal can't perform the repair under VESTA's warranty, even though we installed the unit. That has to be their authorized tech. We do the inspection and the tag-out, they do the repair.
>
> When would you like us out? [Schedule]
>
> **If confirmed not affected:**
>
> Good news — your unit's serial is outside the recall range. I'll send you a short email confirming we checked so you've got it in writing. If you have any family or neighbors with a VESTA tankless, the recall is 26-026 on cpsc.gov and it's worth them checking.
>
> **If customer can't find model or serial:**
>
> No problem. The data plate is usually on the front cover of the unit, below the temperature display, or on the side near the gas connection. If it's tucked in a tight closet or attic and you'd rather not pull it, just say the word and I'll send a tech out tomorrow to get the numbers and do the inspection at the same visit.

### 4. Technician On-Site Stop-Use / Tag-Out Protocol — VESTA VST Recall

> **Pre-arrival (dispatcher-loaded brief):** Customer name, address, install date, VESTA model on file, install-side supply-house origin. Tools: CO meter, lockout/tag-out cards, spanner for the manual gas valve at the appliance, printed copy of CPSC recall 26-026, and Cardinal's one-page leave-behind.
>
> **On arrival:** Introduce yourself by name, confirm the customer is the owner or authorized decision-maker, and ask permission to inspect the water heater. Explain you'll be there about 20 minutes.
>
> **Data-plate verification:** Locate the data plate. Read the model and serial against the recall notice in writing — do not eyeball it. Photograph the data plate at a legible resolution. Save to the job record.
>
> **Visible-defect check:** Open any accessible exhaust-duct access panel that does not require tools beyond a screwdriver. Photograph the duct. Flag any visible cracking, sooting, or heat discoloration. If the duct is cracked or shows soot, escalate immediately — the unit is off-limits as of that observation regardless of CO meter reading.
>
> **CO meter sweep:** Meter ambient air at the unit, at the first return vent in the living space, and in the nearest sleeping area. Log readings. Any reading above 9 ppm ambient is a CO-incident — follow Cardinal's CO-incident protocol (ventilate, evacuate if elevated, call utility) rather than continuing the recall workflow.
>
> **Tag-out (default posture for this recall):** Close the appliance-side manual gas valve. Affix a Cardinal tag-out card: brand (VESTA), model, serial, hazard (CO per CPSC 26-026), date, technician name, and the manufacturer's direct line (888-505-5525). Leave the tag on the valve, not on the wall — a wall tag gets removed during housecleaning, a valve tag does not.
>
> **Customer briefing:** Walk the customer to the unit. Point to the tag. Show them the data-plate photo and the recall notice. Restate: VESTA is sending their tech to do the repair; call 888-505-5525 or register at recallrtr.com/condensingwaterheater; until VESTA's tech arrives, the gas valve stays closed and the unit stays off; cold-water service is unaffected; hot-water is unavailable at this unit. Confirm the customer has working CO alarms covering the unit area and nearest sleeping area; if not, install one from the truck stock or recommend they pick one up today.
>
> **Leave-behind:** Hand the customer Cardinal's one-page summary with the tag number, the VESTA recall URL, the manufacturer's direct line, Cardinal's direct line, and the confirmation that Cardinal cannot perform the manufacturer's repair but will coordinate with VESTA's technician when they arrive.
>
> **Back at the shop:** Log the visit in the recall tracker. Flag the customer for a 30-day check-in. Upload the data-plate and duct photos. Do not close the job ticket until the 30-day follow-up is complete.

### 5. Handoff-to-Manufacturer Language (Customer-Facing)

> What VESTA is responsible for: the repair itself, at no cost to you. A VESTA-certified technician performs the work. You need to register your unit directly with VESTA at recallrtr.com/condensingwaterheater or by calling 888-505-5525 so they can authorize and schedule the repair. If you skip the registration step, the repair will not be processed.
>
> What Cardinal Plumbing is doing for you: confirming your unit is on the affected list, visually inspecting the exhaust run, checking your CO alarm coverage, and if warranted tagging the unit out at the gas valve until VESTA's technician arrives. Coordinating with that technician when they get scheduled. Following up with you thirty days from today to make sure the repair was completed cleanly.
>
> What Cardinal cannot do: perform the recall repair under VESTA's warranty authority. That is a manufacturer rule. Even though we installed your unit, we are not authorized to issue replacement parts or close out the recall-repair ticket on VESTA's behalf.
>
> On insurance: if you're asked whether your homeowner's policy covers anything related to this recall, please ask your carrier directly. We are not in a position to answer that on their behalf.

### 6. Internal Tracking + 30-Day Follow-Up

| Customer | Address | Install date | Serial | Outreach date | Channel | Response | Tech-visit date | VESTA-repair confirmed date | 30-day follow-up | Flag |
|---|---|---|---|---|---|---|---|---|---|---|
| Marcus L. (Preferred plan) | Glen Allen, VA | 2022-04-15 | VRS-199-[…] | 2026-04-23 | SMS + email | "Already registered, tech coming next Thu" | 2026-04-24 | [pending] | 2026-05-24 | — |
| Hampton Court HOA (4 units) | Short Pump, VA | 2021-07 / 2022-01 | [4 serials] | 2026-04-23 | email to PM | "Getting you in this week" | 2026-04-25 | [pending] | 2026-05-25 | Commercial — PM contact |

**Metrics Dan should watch:**

- Outreach coverage: 47 known-affected installs; target 100% contacted within 7 days of this outreach push (so by April 30, 2026)
- VESTA-repair-confirmed rate at 30 / 60 / 90 days
- Unsolicited reply rate to the email — "thanks for the heads-up" replies are Cardinal's referral pipeline for the next year
- Escalation count — any customer whose VESTA-side remedy has not been resolved at 60 days; owner calls personally
- Incident rate — any report of CO symptom, property damage, or near-miss on an affected unit, escalate immediately to Dan and Cardinal's GL carrier; do not route through normal dispatch

---

## Notes for the Shop

- Do not attach a sales offer or upsell to the first-touch recall message. The customer is worried; adding "while we're there, want a quote on a replacement?" to the SMS is read as opportunistic and is the single fastest way to lose the referral tail that this event actually generates.
- The replacement conversation is real — some customers will decline the manufacturer's repair and elect to replace the unit outright — but it belongs in a separate conversation, booked through the normal estimate flow, after the shop has done the inspection visit and the customer has had a day or two to decide.
- Keep the tracker. Most shops handle their first recall ad-hoc, lose track of who was contacted and who wasn't, and are unable to answer a liability-side question cleanly six months later. The tracker is the defense.
- On life-safety recalls, move faster than the manufacturer's letter. The shop that reaches the customer first is the shop the customer trusts. This is especially true for customers who installed the unit with a supply-house brand they do not have a direct relationship with.
- The 30-day follow-up is the highest-leverage action on the entire workflow. It is also the action shops skip most often. Do not skip it.
- For CO-hazard recalls specifically, never leave a visit without confirming the customer has at least one working CO alarm covering the unit area and the nearest sleeping area. If they don't, install one from truck stock or insist the customer pick one up before you leave.
- Pair this skill with the Job Status Update Drafter for the 30-day follow-up message and with the Safety & Compliance Tracker for logging which technicians completed recall-specific inspection visits (useful for GL insurance renewal).
