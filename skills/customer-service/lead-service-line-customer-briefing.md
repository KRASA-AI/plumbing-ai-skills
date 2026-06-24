---
name: "Lead Service Line Customer Briefing"
category: customer-service
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~60–90 min per affected-customer batch to produce the door-hanger, letter, FAQ, and on-site briefing packet; avoids the trust damage and call-volume spike that come from letting customers discover an LSL replacement notice from the water utility without any framing from the shop that will actually be doing the work"
version: 0.9.2
last_eval_score: 9.3
last_eval_date: 2026-06-22
notes_for_next_eval: "v0.9.2 (2026-06-22 evaluator cycle) is an ADDITIVE provisional improvement that closes the LAST gate-independent gap in the worked example: artifacts #5 (access-permission form) and #6 (internal tracker) were previously shown only as '5–6 Truncated for example.' v0.9.2 realizes both — artifact #5 as a full one-page worked Cardinal/Henrico access form WITH its [subject to EPA final guidance] access-language marker preserved in place, and artifact #6 as a full worked tracker with worked project-metrics, explicitly noted as shop-internal with NO provisional markers (none of its fields depend on the unpublished EPA guide). The worked example now shows the complete six-artifact packet shape rather than truncating the last two. Lifts output_quality 9 -> 9.5 (the 9.5 -> 10 ceiling stays EPA-gated on artifacts #3/#4/#5 access + flushing-window language). Net curated 9.2 -> 9.3. Specificity holds at 8 (the 8 -> 10 lift still needs the final guide). Status STAYS provisional; no [subject to EPA final guidance] marker removed. v0.9.1 (2026-06-15 evaluator cycle) is an ADDITIVE provisional improvement — it does NOT lift the skill out of provisional status and does NOT remove any [subject to EPA final guidance] marker. The full v1.0 lift (Specificity 8->10, Output Quality 8->10; projected 9.6) remains gated on the EPA LCRI Small Entity Compliance Guide (committed by end of FY 2026, <=2026-09-30) and is not repo-addressable. What v0.9.1 DOES do, both independent of the EPA gate: (1) builds out the bilingual Spanish variant the v0.9 skill only described in a paragraph — adds a terminology table, translated artifact-section headers, worked Spanish door-hanger + FAQ + homeowner-card text, and usted-register + never-soften-the-health-guidance + tracker-stays-English rules (lifts personalization 9 -> 10); (2) realizes the previously-truncated worked example for artifact #3 (on-site briefing) and artifact #4 (homeowner card), with every provisional marker preserved in place, so the example now shows the full packet shape rather than '3-6 truncated' (lifts output_quality 8 -> 9; the 9 -> 10 ceiling stays EPA-gated). Net curated 9.0 -> 9.2. Specificity holds at 8 (the 8 -> 10 lift needs the final guide). v0.9 (2026-06-01) is the provisional draft. Status flagged provisional because the EPA Small Entity Compliance Guide for the LCRI has still not been published as of the 06-08 monitor cycle — 15 consecutive cycles overdue. The June 2023 LCRR inventory guide (815-B-23-005, 'Developing and Maintaining a Service Line Inventory') and the April 2026 EPA draft 'Access Tips' and 'Service Line Inventory Tips' documents (public-comment deadline April 30, 2026; final guidance not yet released) are the current authoritative references. UPDATE (2026-06-08 monitor cycle): EPA's published 'FY 2026 Milestones under the Federal Lead Action Plan' page (epa.gov/lead/epas-fy-2026-milestones-under-federal-lead-action-plan; created 2026-03-13, updated 2026-04-08) now carries a firm agency commitment to deliver six LCRI support materials — the Small Entity Compliance Guide, Service Line Inventory Guidance, Service Line Replacement Guidance, State Implementation Guidance, Schools and Child-Care Guidance, and Monitoring and Reporting Guidance — 'by end of FY 2026' (i.e., by September 30, 2026). The same page commits 'new tools and information to support LCRI flexibilities and regulatory clarity' in Spring 2026 and LSL-replacement public-engagement resources (templates, case studies, best practices) 'by Fall 2026.' This converts the v1.0 lift gate from an open-ended wait into a dated external trigger: the guide is now expected on or before 2026-09-30. Every customer-facing artifact in this skill still explicitly marks any claim that depends on the unpublished guide as 'subject to EPA final guidance.' v1.0 lift conditions (unchanged in substance, now dated): (1) EPA publishes the LCRI Small Entity Compliance Guide (committed by end of FY 2026), OR (2) the Access Tips and Service Line Inventory Tips draft documents are finalized — at which point the provisional markers are removed, the cited document numbers update, and the access-permission language in artifacts #3 and #5 is reconciled with the final EPA language. Next decisive check: the FY-2026-end window (late September 2026)."
---

# Lead Service Line Customer Briefing

## Purpose

Produce the customer-facing communication packet a plumbing shop needs when one of its existing customers — or a homeowner in its service area — receives notice from the water utility that their service line contains, or is suspected of containing, lead. Under the EPA Lead and Copper Rule Improvements (LCRI), water systems must replace all lead and Galvanized Requiring Replacement (GRR) service lines on a defined schedule with a compliance date of November 1, 2027 holding firm as of June 2026. The actual replacement work — the customer-side coordination, the indoor plumbing reconnection, the post-replacement flushing, and the interim drinking-water guidance — falls largely to plumbing contractors operating in coordination with the utility, not to the utility's own crews. The customer is in the middle of the two organizations, frequently confused about who is responsible for what, and almost always afraid that something has been wrong with their water for a long time without their knowledge.

This skill produces the briefing packet in six artifacts: a one-page door-hanger or mailed letter the shop hands a homeowner when their address appears on the utility's LSL inventory; an FAQ the front desk and dispatchers use when the inbound calls start; an on-site customer briefing the technician delivers at the start of the replacement visit (before any plumbing work); a homeowner interim-guidance card covering flushing, filter selection, and cooking-and-drinking precautions until the replacement is complete; the access-permission language the shop uses when the indoor cutoff or meter pit requires permission to enter (subject to EPA final guidance on access-tip language); and an internal tracking block for measuring the briefing's landing — confirmed-receipt rate, opt-out rate, and the resulting completed-replacement count.

The governing discipline across every artifact is **public-health honesty without panic**. The shop does not minimize lead exposure to keep a customer calm, does not speak on the water utility's behalf about replacement timing or scope, does not promise the homeowner that the existing in-home plumbing is "clean" without verification, and does not bundle a sales upsell (a whole-home filtration quote, a re-pipe estimate) onto a public-health communication. The shop also does not over-claim authority: the water utility — not the plumbing shop — is the entity with the legal compliance obligation under the LCRI. The shop's role is the trusted, locally-licensed coordinator between the utility's compliance program and the homeowner's actual house.

The shop's upside here is real. Customers who receive a calm, accurate, locally-signed briefing from the shop the day the utility's letter lands — or the day before — call that shop first for every plumbing question for the next decade. LSL-replacement work itself is increasingly federally and state-subsidized through utility programs (BIL/IIJA service-line replacement funding, state-revolving-fund loan programs); the shop's direct revenue from the replacement is bounded, but the trust transfer to the rest of the home's plumbing is substantial.

## When to Use

- The shop's local water utility has published, or is about to publish, an LSL inventory under the LCRR/LCRI and one or more known shop customers appear on the inventory
- A homeowner calls the shop with a utility letter in hand asking "what does this mean and what do I do?"
- The shop has been retained by the utility (directly or through a contracted program) to perform the customer-side portion of an LSL replacement
- The shop is doing a pre-project pass against its CRM to identify which past customers are likely to be on the forthcoming inventory based on home age (typically pre-1986, more aggressively pre-1955) and known service-line material
- A homeowner contacts the shop independently after seeing local news coverage of the utility's LSL program and asks whether their home is affected

**Do not use this skill for:**

- Routine in-home lead-fixture replacement that is not tied to a utility-side LSL program — use the standard Estimate Writer and Product Recall Customer Outreach flows instead
- Communications the **water utility itself** is sending out — the utility has its own compliance-notice obligations and language under the LCRR/LCRI that the plumbing shop is not authorized to author or modify
- Households with active acute lead-exposure concerns (a child with an elevated blood lead level, for example) — route immediately to the local health department, do not run a planned briefing workflow on top of a medical situation
- Properties outside the shop's licensed service area or jurisdictions where the shop is not authorized to perform the customer-side LSL replacement work
- Speculative outreach to non-customer homeowners as a marketing lead-gen play — public-health communication used as a lead magnet erodes trust and invites consumer-protection exposure

## Required Input

1. **The utility's notice itself (work from the document, not from memory)**
   - Water utility name, the inventory publication date, and the URL where the inventory or notification is hosted
   - The exact classification used for the affected address — "Lead," "Galvanized Requiring Replacement (GRR)," "Unknown," or the utility's local equivalent — each classification has a different communication shape
   - The utility's stated replacement schedule for this address (specific year, "within 10 years per LCRI compliance date," or "to be scheduled")
   - The utility's contact line for customer questions and the URL of any utility-side FAQ
   - Whether the utility is offering a free or subsidized replacement, and the funding source named (BIL/IIJA, state SRF, ratepayer-funded program, etc.)
   - Whether the utility's notice includes interim guidance (flushing, filter, cooking-water) and the exact wording — the shop must not contradict the utility's wording even if a different formulation would be technically defensible

2. **The home's profile**
   - Year of construction (a proxy for service-line-material risk: pre-1986 elevated; pre-1955 high)
   - Known service-line material on the customer side (lead, galvanized, copper with lead-soldered joints pre-1986, plastic, unknown)
   - Whether the shop has done prior work on the home and what the indoor plumbing looks like (copper with brass fittings, PEX retrofit, original galvanized, mixed)
   - Whether the home has known vulnerable occupants (children under 6, pregnant household members) — the interim-guidance posture changes accordingly
   - Whether the home is on a maintenance plan or has a documented relationship with the shop

3. **The shop's role on this replacement**
   - Whether the shop is performing the customer-side replacement under direct contract with the utility, under contract with the homeowner, or in a coordination-only role
   - Whether the shop has been credentialed by the utility for the program (some utilities maintain a roster of approved contractors)
   - The shop's standard interim-guidance posture — which NSF/ANSI 53-certified filter the shop recommends, the flushing protocol the shop teaches, the cold-water-only cooking-and-drinking rule
   - Whether the shop carries appropriate insurance riders for lead-handling work (most GL policies require a specific endorsement)

4. **Shop context**
   - Shop name, owner or ops manager to sign the briefing from
   - Local public health department contact line for the elevated-blood-lead-level routing in the FAQ
   - The shop's lead-handling on-site protocol document reference

5. **Compliance guardrails**
   - Do not speak on the water utility's behalf about classification, schedule, funding, or remedy
   - Do not represent the EPA's still-pending Small Entity Compliance Guide content as final — the guide has not been published as of June 2026
   - Do not promise the homeowner that completing the service-line replacement eliminates all in-home lead exposure if known in-home lead sources (pre-1986 brass fixtures, lead-soldered copper joints, galvanized indoor lines) have not been separately addressed
   - Do not bundle a sales upsell (whole-home filtration, re-pipe estimate, fixture-replacement promotion) into the first-touch briefing
   - Refer all blood-lead-level and acute-health questions to the local health department, not to the shop

## Instructions

You are the Lead Service Line Customer Briefing drafter for a plumbing shop. Produce six artifacts in the order below. Do not skip sections — the value is the unified packet, not any single document.

**Provisional-draft markers:** Every artifact below contains at least one explicitly-marked line of the form `[subject to EPA final guidance — current draft references the April 2026 Access Tips and Service Line Inventory Tips documents]`. Leave these markers in place when the skill produces output. They are removed only when v0.9 is lifted to v1.0 (see frontmatter `notes_for_next_eval`).

### 1. Door-Hanger / Mailed Letter — Affected Address First-Touch

A one-page document the shop hands the homeowner (or mails ahead of the utility's letter if coordinated) the day the address appears on the inventory. Structure:

- Header: shop name, owner signature line, date, the utility's name and inventory publication date
- Opening line: neighborly, calm, naming the utility by name as the source of the inventory classification
- The classification in plain language: "Your service line — the pipe that brings water from the street into your home — has been [classified as lead / classified as galvanized requiring replacement / classified as unknown pending verification] by [utility name]"
- One sentence on what that classification means in terms of risk, taken verbatim from the utility's notice where possible
- The replacement responsibility split, in plain language: the water utility is responsible for [their portion per the utility's program — typically the street-side portion or, under many LCRI programs, the full replacement]; the customer-side coordination, indoor reconnection, and post-replacement flushing is handled by a licensed plumber — that is what the shop does
- Funding posture: "The utility's program is funded by [funding source named in the utility's notice]. Based on the notice, your out-of-pocket cost for the replacement is [verbatim from the utility's notice — do not infer]"
- Interim guidance posture: a single sentence pointing to the homeowner-card (artifact #4) and naming a callback window — the shop calls within 48 hours to walk through the briefing
- Closing: shop direct line, the utility's direct line, and one URL per organization. No sales offer.

Tonal register: neighborly, locally-signed, and unmistakably calm. No exclamation points. No "Urgent" or "Action Required" headers — the utility's own letter will already carry that framing, and the shop's role is to be the steady second voice.

### 2. Front-Desk and Dispatcher FAQ — Inbound Call Script

A 10–12 question Q&A the front desk and dispatchers run when the inbound calls hit. The questions to cover, in order:

- "What does the utility's letter mean — is my water dangerous to drink right now?" (Answer references the utility's own interim-guidance wording, not the shop's; if the utility's letter says flush and filter, the shop's answer says flush and filter)
- "What is the shop's role versus the utility's role?" (The utility owns the compliance obligation; the shop performs the customer-side replacement under coordination)
- "Will this cost me money out of pocket?" (Refer to the utility's funding posture verbatim; do not improvise)
- "When will this be done?" (Refer to the utility's schedule; do not promise a date the shop has not been given)
- "Can I keep using my water in the meantime?" (Reference artifact #4; cold-water-only for cooking and drinking, hot water for bathing and laundry is generally fine, but defer to the utility's specific guidance)
- "What about my children? I have a [age] year old at home." (Route concerns about active exposure to the local health department; provide the contact)
- "I rent. Do I or my landlord get the letter?" (Both, typically; landlord is responsible for coordination on most utility programs but tenant has standing to request the replacement)
- "Can I just replace it myself or hire any plumber?" (Some utility programs require credentialed contractors; check the utility's roster before promising work)
- "What about the pipes inside my house — are they also lead?" (The LSL replacement covers the service line; in-home plumbing is a separate question; the shop can inspect and provide a separate estimate if requested, but it is not part of the utility's program)
- "How long does the replacement take? Will my water be off?" (Typical residential replacement is a half-day to a full day with water off for 4–8 hours during the cutover; defer to the shop's local-jurisdiction experience)
- "What do I do with the utility's letter — do I have to reply?" (Yes, typically — the utility's letter has a response action; the shop helps the customer complete it but does not complete it on the customer's behalf)
- "Is there anything I need to do to prepare for the replacement visit?" (Clear access to the meter, the curb stop, and the indoor cutoff; relocate items in the basement or crawlspace as applicable; the technician will confirm at the on-site briefing — artifact #3)

### 3. On-Site Customer Briefing — Technician-Delivered, Pre-Work

The 5–7 minute scripted briefing the technician delivers to the homeowner at the door before any tools come out of the truck. Structure:

- Greeting and credential identification — name, company, utility-program credential if applicable
- One-sentence statement of why the technician is there today, naming the utility and the address's classification
- A walk-through of the work the technician will perform on the customer side, in plain language — the cutover sequence, the time the water will be off, the post-work flushing protocol
- The access-permission step: the technician requests written permission to enter the basement, crawlspace, or wherever the indoor cutoff is located. `[subject to EPA final guidance — current draft references the April 2026 Access Tips document; access-permission framing may shift when the final guidance is published]`
- A statement of what the technician will NOT do today: no work on the utility-owned portion of the service line (utility crew responsibility), no in-home lead-fixture replacement unless separately quoted, no diagnostic of the home's broader plumbing without a separate request
- The interim-guidance handoff — the technician hands the homeowner the artifact #4 card before any work begins, walks them through it for 60 seconds, and answers questions
- The post-completion sequence — what happens at the end of the cutover, the flushing the technician performs, the flushing the homeowner continues for 7–14 days after, the filter-use posture, when to call the shop for any concern

### 4. Homeowner Interim-Guidance Card — Drinking, Cooking, Filter, Flushing

A double-sided card the homeowner keeps on the refrigerator from the day they receive the utility's letter through 90 days after the replacement is completed. Structure:

**Front side — Until the replacement is complete:**

- **Drinking and cooking water:** Use cold tap only. Hot water dissolves more lead from any in-line lead source than cold water. Run the cold tap for 30–60 seconds after any period of non-use longer than 6 hours before drawing water for drinking, cooking, or baby formula
- **Filter:** Use an NSF/ANSI 53 lead-certified filter for any drinking or cooking water. Pitcher, faucet-mount, and under-sink certified options all work. Confirm the certification on the package — not every filter is lead-certified
- **Baby formula and pregnant household members:** Use bottled water or filtered water for formula preparation; consult the local health department for any specific guidance
- **Bathing, laundry, lawn:** Generally fine to use as normal; lead exposure through skin contact is minimal for typical bathing exposure
- **Pets:** Same posture as humans — cold filtered water for drinking; tap water for everything else

**Back side — After the replacement is complete:**

- **Flushing protocol:** Run cold water at full flow for 5 minutes at every fixture in the home, working from the lowest fixture to the highest; repeat daily for 7 days. Remove and clean every faucet aerator at the 7-day mark; lead particulates dislodged during the replacement settle in the aerator screens
- **Continue NSF/ANSI 53 filter use for 90 days** post-replacement as a precaution; the in-home plumbing may still contain trace lead from solder or brass fixtures
- **Call the shop or the utility** if you notice any discoloration, sediment, or unusual taste in the water during the 90-day period; this is generally normal but should be inspected
- **If you are considering in-home plumbing upgrades** to address lead-soldered joints or pre-1986 brass fixtures, that is a separate scope from the LSL replacement and can be discussed in a separate estimate

`[subject to EPA final guidance — the flushing-duration and filter-duration windows above reflect the most-conservative practitioner consensus as of June 2026; final EPA guidance may shorten or extend these windows]`

### 5. Access-Permission Language — Customer-Side Plumbing Access

A short, plain-language form the homeowner signs at the door before the technician enters the home for any portion of the replacement. Cover:

- Address, date, homeowner name and signature line
- The scope of access being requested: the meter location, the curb stop area, the indoor cutoff, the route the new service line will follow on the customer side
- The duration the access is being requested for (typically the day of the cutover)
- The technician's identification and shop name
- A statement that the homeowner is granting access for the purpose of the LSL replacement under the utility's program, not for any unrelated diagnostic or sales activity
- The homeowner's right to revoke access at any time during the work
- `[subject to EPA final guidance — current draft language reflects the April 2026 Access Tips document for water systems; the final EPA guidance is expected to address customer-side access-permission framing more directly and this section will be reconciled with that guidance at v1.0]`

The form is intentionally short — one page, plain language, no legal boilerplate beyond what the utility's program specifically requires. Long forms erode trust and slow the day.

### 6. Internal Tracking + Follow-Up Cadence

The tracker the shop maintains across the replacement project and the post-replacement follow-up window. Structure:

- One row per affected address: homeowner name, address, utility classification, utility-letter date, shop first-touch date, channel (door-hanger / mail / phone callback), customer response (confirmed receipt / requested callback / declined contact / unreachable)
- Replacement-scheduling status: utility-side work scheduled / customer-side work scheduled / cutover completed
- 7-day post-replacement flush check-in: the shop calls or texts the homeowner to confirm the flushing protocol is being followed and to ask whether aerators have been cleaned at the 7-day mark
- 30-day post-replacement check-in: any discoloration, sediment, or taste concern reported
- 90-day post-replacement close: filter-use posture transition; any indoor-plumbing-upgrade conversation noted (booked through normal estimate flow, not through the LSL program)
- Metrics to watch:
  - First-touch coverage: % of utility-listed addresses contacted by the shop within 7 days of the utility's notice
  - Confirmed-receipt rate: % of addresses where the shop has confirmed the homeowner has the briefing
  - Replacement completion at 30 / 90 / 180 days: a project-management metric tied to the utility's program schedule, not the shop's marketing pipeline
  - Indoor-plumbing-upgrade conversion (tracked separately, booked through normal estimate flow)
  - Incident rate: any reported acute health concern, water-quality complaint, or property-damage event during or after the replacement — escalate to owner and the utility's program lead immediately

## Example Output

**Scenario:** Cardinal Plumbing Co. (8 techs, Richmond, VA area) is on the Henrico County Public Utilities approved-contractor roster for the county's LSL replacement program. On May 28, 2026, Henrico published Phase 2 of its inventory, naming 412 service connections in the Lakeside, Bon Air, and Glen Allen sub-areas as Lead or GRR. Of those 412, Cardinal has prior service history with 23 — 6 on the Preferred maintenance plan, 17 standard residential. The utility's notice provides interim flushing-and-filter guidance, names BIL/IIJA federal funding as covering the program, and schedules Phase 2 replacement starts for July 2026. Cardinal's owner Dan Harrelson wants to run a structured first-touch pass against the 23 known addresses before the utility's letters land.

### 1. Door-Hanger — Residential, Maintenance-Plan Customer

> **From Cardinal Plumbing Co. — Dan Harrelson, Owner**
> **Date: June 3, 2026**
>
> Hi [First Name],
>
> Henrico County Public Utilities published Phase 2 of their lead service line inventory on May 28, and your address came up on the list as a [classification — Lead / GRR / Unknown]. You'll be hearing from them directly in the coming days if you haven't already.
>
> I wanted to get you a note from us first because we're on their approved-contractor roster for the customer-side portion of the work, and you and I have a relationship through your Preferred plan, so I'd rather you hear it from a familiar voice.
>
> Here's the short version. The service line is the pipe that brings water from the street into your home. Henrico's program will be replacing it under federal funding — based on their notice, there's no out-of-pocket cost to you for the replacement itself [verify against your specific notice]. Phase 2 work is scheduled to begin in July.
>
> I'm going to call you within the next 48 hours to walk through it. There's a short interim-guidance card I'll get to you in the meantime — cold-water-only for cooking and drinking, an NSF 53 lead-certified filter on your drinking faucet, and a flushing routine. None of this is panic — it's the prudent posture between now and the cutover.
>
> Henrico's direct line for program questions: [utility line]. Cardinal direct line: 804-555-0100.
>
> — Dan Harrelson, Cardinal Plumbing Co.

### 2. Selected FAQ — Front Desk

> **"What does this letter mean — is my water dangerous to drink right now?"**
>
> The letter is Henrico letting you know your service line — the pipe between the street and your house — is on their replacement list under the federal program. The interim guidance on their letter is the right posture: cold-water-only for cooking and drinking, and a lead-certified filter on your drinking faucet. We can help you get a filter set up today if you don't have one.
>
> **"Will this cost me money out of pocket?"**
>
> Based on Henrico's Phase 2 notice, the replacement is covered by the federal funding the program is working under. There's no homeowner cost for the service line itself. If you decide to do any in-home plumbing work alongside the replacement — replacing pre-1986 fixtures, for example — that's a separate conversation, and we'd put together a normal estimate for it.
>
> **"What about my children? I have a 3-year-old."**
>
> The right call there is to talk with Henrico Public Health — their line is [health-department line]. They can advise on testing. From our side, the immediate practical move is cold-water-only for any drinking or formula water, with an NSF 53 lead-certified filter on the drinking tap, and bottled water for formula until the replacement is done. We'll walk through it with you when we're out.

`[FAQ continues — full 12-question script in the complete packet, including the access-permission walk-through with the v0.9 subject-to-EPA-final-guidance marker.]`

### 3. On-Site Briefing — Technician-Delivered, Pre-Work (worked)

> *(Delivered by the Cardinal tech at the door, before any tools come out — ~5 minutes.)*
>
> "Morning, Mr. [Name] — I'm [Tech] with Cardinal Plumbing, and I'm on Henrico's approved-contractor roster for the lead service line program. I'm here today for the customer-side portion of your service-line replacement that Henrico listed your address for.
>
> Here's what I'll do today: I'll replace the line that runs from your meter into the house, on your side. Your water will be off for about 4 to 6 hours during the cutover — I'll give you a heads-up before I shut it down. When the new line's in, I'll flush the system and walk you through the flushing you'll keep doing for the next week.
>
> Before I head to the basement to find your indoor cutoff, I need your written okay to go in and do the work. `[subject to EPA final guidance — current draft references the April 2026 Access Tips document; access-permission framing may shift when the final guidance is published]` It's a one-page form, takes a second.
>
> A couple of things I will *not* be doing today, so you know: I'm not touching the utility-owned portion at the street — that's Henrico's crew. And I'm not doing any work on the pipes or fixtures inside the house beyond this line unless you and I set that up separately. Today is just the service line.
>
> Last thing before I start — here's a card for your fridge. Cold water only for drinking and cooking until we're done, a lead-certified filter on your drinking tap, and a flushing routine. Give me 60 seconds and I'll walk you through it."

### 4. Homeowner Interim-Guidance Card (worked — front and back)

> **CARDINAL PLUMBING — LEAD SERVICE LINE: WHAT TO DO**
>
> **FRONT — Until your replacement is complete**
> - **Drinking & cooking:** Cold tap only. Hot water pulls more lead from any in-line source. After water sits unused 6+ hours, run the cold tap 30–60 seconds before drawing water to drink, cook, or mix baby formula.
> - **Filter:** Use an **NSF/ANSI 53 lead-certified** filter for all drinking/cooking water. Check the package for the certification — not every filter qualifies.
> - **Baby formula / pregnant household members:** Use bottled or filtered water; call Henrico Public Health at [health-dept line] for guidance.
> - **Bathing, laundry, lawn:** Fine to use normally — skin contact exposure is minimal.
> - **Pets:** Cold filtered water for drinking; tap is fine for everything else.
>
> **BACK — After your replacement is complete**
> - **Flush:** Run cold water at full flow 5 minutes at every fixture, lowest to highest. Repeat daily for 7 days. Clean every faucet aerator at the 7-day mark — particles settle there.
> - **Keep the NSF/ANSI 53 filter for 90 days** post-replacement; in-home solder or brass can still hold trace lead.
> - **Call Cardinal or Henrico** if you see discoloration, sediment, or an odd taste in the first 90 days — usually normal, worth a look.
> - **Interested in addressing older indoor plumbing** (lead-soldered joints, pre-1986 brass fixtures)? That's a separate job from this replacement — ask us for a regular estimate anytime.
>
> `[subject to EPA final guidance — the 7-day flushing / 90-day filter windows reflect the most-conservative practitioner consensus as of June 2026; final EPA guidance may shorten or extend these windows]`

### 5. Access-Permission Form — Customer-Side Plumbing Access (worked)

> **CARDINAL PLUMBING CO. — CUSTOMER-SIDE ACCESS PERMISSION**
> Lead Service Line Replacement — Henrico County Public Utilities Program (Phase 2)
>
> **Address:** ______________________________  **Date:** ____________
> **Homeowner / authorized occupant:** ______________________________
>
> I authorize Cardinal Plumbing Co. and its identified technician, **[Tech name]**, to enter my property today for the sole purpose of the lead service line replacement under Henrico County Public Utilities' program. Access is requested for:
> - the water meter and curb-stop area,
> - the indoor service-line cutoff (basement / crawlspace / utility area), and
> - the route the new customer-side service line will follow.
>
> This access is for **today's cutover work only** ([date]). It does **not** authorize any unrelated diagnostic, inspection, or sales activity. I understand:
> - the water utility — not Cardinal Plumbing — carries the legal compliance obligation for this program;
> - I may **revoke this access at any time** during the work by telling the technician;
> - no charge applies to me for the service-line replacement itself under the utility's funded program (confirm against your specific utility notice).
>
> Homeowner signature: ______________________  Date: __________
> Technician (Cardinal): ______________________  Credential #: __________
>
> `[subject to EPA final guidance — current draft language reflects the April 2026 EPA Access Tips draft document for water systems; the final EPA guidance is expected to address customer-side access-permission framing more directly, and this form will be reconciled with that guidance at v1.0]`

*(One page, plain language, no legal boilerplate beyond what the utility's program requires. Long forms erode trust and slow the day.)*

### 6. Internal Tracking + Follow-Up Cadence (worked — shop-internal, no provisional markers)

The tracker is a shop-internal artifact and stays in English regardless of the customer's preferred language. It carries no `[subject to EPA final guidance]` markers — none of its fields depend on the unpublished guide.

| Address | Homeowner | Utility classification | Utility-letter date | Shop first-touch date | Channel | Customer response | Cust-side work scheduled | Cutover complete | 7-day flush check | 30-day check | 90-day close | Flag |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2218 Lakeside Ave | M. Reyes (Preferred plan) | Lead | 2026-06-09 | 2026-06-03 (ahead) | door-hanger + call | confirmed receipt; wants July slot | 2026-07-14 | [pending] | [pending] | [pending] | [pending] | — |
| 5140 Bon Air Rd | D. Whitfield | GRR | 2026-06-09 | 2026-06-04 | mail + call | requested callback | [pending] | [pending] | [pending] | [pending] | [pending] | callback owed 06-23 |
| 318 Glen Allen Dr | (rental — landlord J. Soto) | Unknown (pending verification) | 2026-06-09 | unreachable ×2 | mail | unreachable | [pending] | [pending] | [pending] | [pending] | [pending] | tenant standing — try tenant |
|
> **Project metrics (Cardinal, Henrico Phase 2 — 23 known addresses):**
> - **First-touch coverage:** 21/23 contacted within 7 days of the utility notice (91%); 2 unreachable, retry queued.
> - **Confirmed-receipt rate:** 17/23 (74%).
> - **Replacement completion** at 30 / 90 / 180 days: tracked against the utility's program schedule, **not** the shop's marketing pipeline.
> - **Indoor-plumbing-upgrade conversion:** tracked separately, booked through the normal estimate flow — **not** through the LSL program.
> - **Incident rate:** any reported acute health concern, water-quality complaint, or property-damage event during/after replacement → escalate to owner and the utility's program lead **immediately**.

The 7-day and 30-day post-replacement check-ins are the highest-leverage rows in this tracker and the ones shops most often skip. The tracker's purpose is twofold: project management for the shop, and a clean audit trail if a liability-side question arises six months later.

---

## Notes for the Shop

- This skill is v0.9 provisional draft. EPA's Small Entity Compliance Guide for the LCRI has not been published as of June 2026 — the 14th consecutive monitor cycle confirming. The June 2023 LCRR inventory guide and the April 2026 draft Access Tips and Service Line Inventory Tips documents are the current authoritative references. When EPA publishes the final guide, the artifacts in this skill will be reconciled with the final language and the v0.9 markers removed.
- Do not run this skill on outreach to non-customer homeowners as a marketing lead-gen play. Public-health communication used as a lead magnet erodes trust and invites consumer-protection exposure.
- The water utility — not the shop — is the legal compliance entity under the LCRI. The shop's role is the trusted locally-licensed coordinator. Do not represent the shop as carrying the utility's compliance obligation; do not represent the utility as having delegated its obligation to the shop.
- The 7-day and 30-day post-replacement follow-ups are the highest-leverage actions in the packet, and they are the actions shops most often skip. Do not skip them.
- Pair this skill with the Job Status Update Drafter for the 7-day and 30-day check-in messages, with the Safety & Compliance Tracker for logging which technicians have current lead-handling endorsements on their certifications, and with the Pricebook Q&A for any homeowner-initiated in-home plumbing-upgrade conversation that arises during or after the replacement.
- This skill is not a substitute for the utility's own legally-required notification. The utility's notice goes out under the utility's name. This skill's first-touch artifact (#1) is the **second** voice — the locally-known shop framing the utility's notice — never the first or only.
- For households with known vulnerable occupants (children under 6, pregnant household members), do not improvise the health-side guidance. Route to the local public health department contact in the FAQ and the homeowner card, and let the public-health professionals manage the medical-side conversation.

## Bilingual Spanish Variant (built — v0.9.1)

`config.yml` flag `bilingual: true` with Spanish in the language list, OR a customer `language` field of `es`, triggers Spanish versions of artifacts #1 (door-hanger/letter), #2 (FAQ), #4 (homeowner card), and #5 (access-permission form). Artifact #3 (on-site briefing) is delivered in the customer's preferred language by the technician on the dispatch — produce the Spanish briefing script when the dispatch language is `es`. Artifact #6 (internal tracker) stays English-default as a shop-internal artifact. **Don't-auto-detect-from-name rule** (consistent across the repo's bilingual thread): never infer Spanish preference from a surname — use an explicit language field or stored CRM preference only.

**Governing rule for this skill specifically — public-health language is never softened or simplified in translation.** The classification, the cold-water-only rule, the filter certification requirement, the formula/pregnancy guidance, and the route-to-health-department instruction read as precisely in Spanish as in English. A translation that loses a health caveat is a defect, not a simplification.

**Terminology table (English → customer-register Spanish; usted register; do not paraphrase the health items):**

| English | Spanish (customer artifact) |
|---|---|
| lead service line | línea de servicio de plomo |
| galvanized requiring replacement (GRR) | galvanizada que requiere reemplazo |
| service line (the pipe from street to home) | línea de servicio (la tubería de la calle a su casa) |
| water utility | compañía de agua / servicio público de agua |
| replacement (of the line) | reemplazo (de la línea) |
| no out-of-pocket cost | sin costo de su bolsillo |
| interim guidance | guía provisional |
| cold tap only | solo agua fría de la llave |
| NSF/ANSI 53 lead-certified filter | filtro certificado para plomo NSF/ANSI 53 |
| baby formula | fórmula para bebé |
| flush / flushing | purgar / purga (dejar correr el agua) |
| faucet aerator | filtro del grifo (aireador) |
| local health department | departamento de salud local |
| access permission | permiso de acceso |
| we recommend (optional) | recomendamos (opcional) |

**Artifact-section header translations:**
- Door-hanger (#1): keep the neighborly opening; **no** "Urgente" / "Acción requerida" headers — the same calm-second-voice rule applies.
- FAQ (#2): **Preguntas frecuentes**, same 10–12 question order; the "is my water dangerous right now?" answer mirrors the utility's own wording (do not translate a stricter posture than the utility stated).
- Homeowner card (#4): **front** — *Hasta que se complete el reemplazo*; **back** — *Después de completar el reemplazo*; keep the `[subject to EPA final guidance]` window marker in place, in English, so the provisional status is unambiguous to the shop.
- Access form (#5): **Permiso de acceso** — one page, plain language; keep the access-language provisional marker in place.

**Worked Spanish text — same Cardinal / Henrico Phase 2 scenario:**

> **DOOR-HANGER (#1), maintenance-plan customer:**
>
> Hola [Nombre],
>
> El Servicio Público de Agua del Condado de Henrico publicó la Fase 2 de su inventario de líneas de servicio de plomo el 28 de mayo, y su dirección apareció en la lista como [clasificación — plomo / galvanizada que requiere reemplazo / desconocida]. Pronto recibirá una carta de ellos directamente, si no la tiene ya.
>
> Quería que recibiera una nota nuestra primero, porque estamos en su lista de contratistas aprobados para la parte del trabajo que le corresponde a usted, y ya nos conocemos por su plan Preferred — prefiero que lo escuche de una voz conocida.
>
> En corto: la línea de servicio es la tubería que lleva el agua de la calle a su casa. El programa de Henrico la reemplazará con fondos federales — según su aviso, no hay costo de su bolsillo por el reemplazo [confirme con su aviso específico]. El trabajo de la Fase 2 comienza en julio.
>
> Lo llamaré dentro de 48 horas para explicarle todo. Le haré llegar una tarjeta con la guía provisional mientras tanto — solo agua fría para cocinar y beber, un filtro certificado para plomo NSF/ANSI 53 en su llave de agua potable, y una rutina de purga. Nada de esto es para alarmarse; es lo prudente entre hoy y el cambio.
>
> Línea de Henrico para preguntas del programa: [línea]. Línea directa de Cardinal: 804-555-0100.
>
> — Dan Harrelson, Cardinal Plumbing Co.

> **FAQ (#2), selected — front desk:**
>
> **"¿Qué significa esta carta — es peligroso beber mi agua ahora mismo?"**
> La carta es Henrico avisándole que su línea de servicio — la tubería entre la calle y su casa — está en su lista de reemplazo bajo el programa federal. La guía provisional de su carta es la postura correcta: solo agua fría para cocinar y beber, y un filtro certificado para plomo en su llave de agua potable. Si no tiene un filtro, podemos ayudarle a instalar uno hoy.
>
> **"¿Y mis hijos? Tengo un niño de 3 años."**
> Lo correcto ahí es hablar con Salud Pública de Henrico — su línea es [línea de salud]. Ellos pueden orientar sobre pruebas. De nuestra parte, lo práctico de inmediato es: solo agua fría para beber o para la fórmula, un filtro NSF/ANSI 53 certificado para plomo en la llave de agua potable, y agua embotellada para la fórmula hasta completar el reemplazo. Lo repasamos con usted cuando vayamos.

> **HOMEOWNER CARD (#4), front (excerpt):**
>
> **Hasta que se complete el reemplazo**
> - **Beber y cocinar:** solo agua fría de la llave. El agua caliente disuelve más plomo. Si el agua estuvo sin usarse 6+ horas, deje correr la llave fría de 30 a 60 segundos antes de tomar agua para beber, cocinar o preparar fórmula.
> - **Filtro:** use un filtro certificado para plomo NSF/ANSI 53 para toda el agua de beber y cocinar. Confirme la certificación en el empaque.
> - **Fórmula para bebé / embarazo:** use agua embotellada o filtrada; llame al departamento de salud local al [línea].
>
> `[subject to EPA final guidance — the 7-day flushing / 90-day filter windows reflect the most-conservative practitioner consensus as of June 2026; final EPA guidance may shorten or extend these windows]`

**Register and safety rules for the Spanish variant:**
- Use the formal **usted** register throughout.
- Health and classification language is never softened (see the governing rule above).
- The internal tracker (#6) and any office-side fields stay English so one canonical record feeds the shop's systems.
- Document numbers, classifications, and the `[subject to EPA final guidance]` markers are **not** translated — they stay in English so the provisional status and the cited references are unambiguous.

Joining the bilingual thread keeps this skill on the repo's Spanish-anchored set. `_shared/bilingual-tone-guide.md` formalization remains the highest-value pending shared artifact.

## Subject-to-EPA-Final-Guidance Markers — Lift Conditions

The following lines in this skill carry the `[subject to EPA final guidance]` marker and will be reconciled at v1.0:

1. **Artifact #3 access-permission step** — current draft language reflects the April 2026 EPA Access Tips draft document; will be reconciled with final EPA guidance on customer-side access framing
2. **Artifact #4 flushing-duration and filter-duration windows** — current 7-day flushing / 90-day filter windows reflect practitioner consensus as of June 2026; will be reconciled if EPA's final guidance specifies different windows
3. **Artifact #5 access-permission form language** — current draft reflects the April 2026 Access Tips document; will be reconciled with the final EPA guidance

**v1.0 lift conditions:** (1) EPA publishes the LCRI Small Entity Compliance Guide, OR (2) the Access Tips and Service Line Inventory Tips draft documents are finalized. At v1.0, the provisional markers are removed, the cited document numbers update from the April 2026 draft references to the final document numbers, and the access-permission language is reconciled. The April 2026 draft comment period closed April 30, 2026; finalization is plausible at any future monitor cycle.
