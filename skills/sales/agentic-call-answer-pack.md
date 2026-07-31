---
name: "Agentic-Call Answer Pack"
category: sales
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~2 hrs to build once; prevents the auto-drop that silently forfeits AI-routed calls thereafter"
version: 1.0
last_eval_score: 9.6
notes_for_next_eval: "v1.0 (2026-07-20, evaluator, debut): first formal evaluation, scored 9.6 — six numbered artifacts (Answer Sheet, Phone-Pickup Protocol, CSR Quick-Reference Card, AI-Receptionist Configuration Notes, Consistency Reconciliation, Auto-Drop Red-Flag Checklist) plus a fully worked Bluegrass Plumbing example. Positioning confirmed clean against AI Search Visibility Content Pack — this skill converts the call, the visibility pack gets the shop called; no overlap. Front-matter last_eval_score was left null at debut and is corrected to 9.6 as of the 2026-07-28 cycle (no content change, hygiene fix only — see evals/results/2026-07-28/agentic-call-answer-pack.yml). Held, no change, at 07-28. Next: watch for the Answer Sheet's default question order needing revision if a competing assistant ships the same feature with a different question set."
---

# Agentic-Call Answer Pack

## Purpose

Get the shop *booked* when the caller is a customer's AI, not the customer. As of July 2026, US Google Search users can ask Google to phone local businesses on their behalf, and home repair — plumbing explicitly named — is one of the first categories in the rollout (announced at Google I/O 2026 and Google Marketing Live 2026; rolling out across the US over the summer, AI Pro and Ultra subscribers first). The homeowner types a question ("how much to replace a 50-gallon water heater, and can someone come today?"), and Google's conversational agent dials the shop, announces itself as an automated system calling for a real customer, asks a short list of questions — typically price, availability, service area, permit handling, and warranty — and reports a written summary back to the homeowner that compares the shop against competitors it also called.

This is a different lead surface than the AI Search Visibility Content Pack covers. That skill's job is getting the shop *selected* — cited and ranked well enough that the customer's AI dials it at all. This skill's job is the sixty seconds after the phone rings. The two failure modes are independent: a shop can win the citation and still lose the booking on a fumbled pickup.

The mechanic that makes this urgent: the agent does not leave a message and it does not wait. If the call lands on voicemail, an IVR phone tree, hold music, or a CSR who cannot answer a straight pricing question without transferring, the agent hangs up and dials the next contractor on the list. The homeowner never learns the shop was even called. There is no missed-call voicemail to return, no callback number in the log — the loss is invisible. A shop that is the top local recommendation can be quietly eliminated from the homeowner's comparison because the pickup did not clear the agent's bar. This pack builds the artifact that clears it.

## When to Use

- The shop wants to be ready for Google agentic calling (and the equivalent capabilities other assistants are shipping) before it costs bookings the shop never sees
- The shop runs a live front desk and needs whoever answers to satisfy an AI interviewer in the first minute without a transfer
- The shop runs its own AI voice receptionist and needs it configured so an AI-to-AI call completes cleanly instead of two bots deadlocking
- Onboarding a new CSR or answering service and standardizing what "a good pickup" contains
- Quarterly hygiene — reconciling the spoken answers against the shop's current pricebook, service area, and the entity facts published for AI search visibility, so the phone answer and the web answer never contradict each other

**Do not use for:**
- Replacing human judgment on a real emergency call — an actively leaking-tank homeowner is not an AI interviewer, and the answer sheet is a floor, not a script to read at a panicking customer
- Publishing firm, guaranteed prices — the pack produces *defensible ranges with what drives them*, never a single quoted number a caller can hold the shop to sight-unseen
- Any service the shop does not actually perform or any city it does not actually roll a truck to — an agent that catches a contradiction between the phone answer and the shop's public listings summarizes the shop unfavorably

## Required Input

1. **The questions to be ready for.** Default set the agent asks: price range for the named job, soonest availability, service area (does the shop cover this ZIP/neighborhood), permit handling (does the shop pull it), and warranty. Add any the shop hears often: diagnostic/service fee and waiver, brands carried, financing, emergency/after-hours coverage.

2. **Price bands from the pricebook.** Low / typical / high installed ranges for the shop's top 6–10 job types, with the one or two variables that move a job between bands. Pull these from the shop's live pricebook, not memory — the phone answer must match the estimate the tech later writes.

3. **Real availability language.** How the shop actually talks about timing — "same-day for emergencies if you call before noon," "typically 2–3 business days for scheduled installs" — not an aspirational claim the schedule can't support.

4. **Service-area truth.** The exact cities/ZIPs the shop rolls trucks to, matching the service-area list published on the website and Google Business Profile. Mismatches here are the most common auto-drop cause.

5. **Permit and warranty facts.** Whether the shop pulls permits (and for which jobs), and the actual warranty terms in defensible form ("10-year tank / 2-year labor"), not vague "lifetime" language.

6. **Answering setup.** Who or what picks up during business hours, after hours, and on overflow — live CSR, answering service, the shop's own AI voice agent, or voicemail — so the pack can be tuned to each path.

## Instructions

You are producing an Agentic-Call Answer Pack: an internal, pre-loaded artifact the shop keeps at the phone so that any answerer — human or the shop's own AI — satisfies a customer's AI interviewer in the first sixty seconds and earns the booking or the callback rather than the hang-up. Produce six sections.

### 1. The Answer Sheet

A one-screen reference card holding the shop's defensible answer to each question the agent asks, in the order the agent tends to ask them. For each question: the spoken answer in one or two sentences, and the single variable that changes it. Rules:

- **Lead with the answer.** "Standard 40- or 50-gallon replacement runs about $1,800 to $2,900 installed, including permit and haul-away" — not "well, it depends on a lot of factors." The agent scores a direct answer far higher than a hedge, and a hedge with no number reads as evasive.
- **Always give a range, never a single guaranteed price.** Anchor low/typical/high and name what moves it (gas-line resizing, code upgrades, fuel change). A range with a reason is the honest answer *and* the answer the agent summarizes well.
- **Availability in concrete windows**, not "as soon as possible."
- **Service area answered as yes/no plus the covered radius** so the agent can confirm the homeowner's location in one turn.
- **Permit and warranty stated in specific, defensible terms.** "We pull the permit and handle the inspection." "10-year tank, 2-year labor."

### 2. Phone-Pickup Protocol

The behavior rules for the human or system answering. The agent is scoring for a fast, direct, complete pickup:

- **Answer live and identify the shop in the first breath.** Every ring toward voicemail is a step toward the next contractor getting the job.
- **When the caller announces it is an automated assistant calling for a customer, do not gatekeep it.** Do not demand the customer's name and callback number before answering the question — that pattern gets the agent to disconnect. Answer the questions first; capture booking details after.
- **No dead air, no "let me transfer you," no "hold while I check."** A transfer or a hold is a hang-up. The Answer Sheet exists precisely so the first person to pick up can answer without moving the call.
- **Give the range; do not refuse to talk price.** "I can't give any price over the phone" is a top auto-drop trigger. The defensible range is the correct answer.
- **Close with a bookable next step** the agent can relay: "We can hold a same-day slot — the customer can confirm and we'll text the window," or a direct booking link/number.

### 3. CSR Quick-Reference Card

A trimmed, laminate-at-the-desk version of the Answer Sheet for a live human: the five default questions, the shop's one-line answer to each, and the two things never to say (no single guaranteed price, no "I can't discuss price by phone"). Written so a CSR three weeks into the job can field an AI interviewer without escalating.

### 4. AI-Receptionist Configuration Notes (if the shop runs its own voice agent)

If the shop already answers with an AI voice agent, an inbound Google agent produces an AI-to-AI call. Two bots can deadlock — mutual "how can I help you?" loops, or the shop's agent trying to qualify a caller that is itself an agent. Configure the shop's voice agent to:

- Recognize the automated-assistant announcement and switch to a **direct-answer mode** that states the price range, availability, service area, permit, and warranty without running its full human-qualification script.
- Pull the price ranges from the same pricebook source the Answer Sheet uses, so the AI-to-AI answer and the human answer never diverge.
- Offer a booking action (hold a slot, send a link) rather than looping.
- Keep a human-handoff path for genuine emergencies, consistent with the repo's hybrid AI-receptionist posture (AI for after-hours/overflow/triage; live human default-on for business-hours inbound).

### 5. Consistency Reconciliation

The agent cross-checks what it hears on the phone against what it can read on the shop's website, Google Business Profile, and directory listings, and it summarizes contradictions unfavorably. Reconcile the Answer Sheet against the shop's published entity facts — the same service-area list, hours, license, and warranty language used in the AI Search Visibility Content Pack's Shop Entity Block. Flag any mismatch (a ZIP the phone claims but the website omits; a warranty stated two different ways) and align them. The phone answer and the web answer must be the same answer.

### 6. Auto-Drop Red-Flag Checklist

The short list of things that get a shop dropped mid-call regardless of how good its ranking was. Audit the answering setup against it:

- Rings to voicemail, an IVR tree, or hold music before a person or system answers
- CSR refuses to give any price, or can only give a price after a transfer
- Answerer demands the customer's callback number before answering anything
- Service area claimed on the phone that the shop's own listings don't confirm
- Warranty or availability stated differently than the website says
- Dead air longer than a few seconds while the answerer looks something up

## Example Output

**Scope:** Bluegrass Plumbing Co., Louisville KY, residential. Live CSR during business hours, own AI voice agent after hours. Top jobs: water heater replacement, drain cleaning, sewer line. $99 diagnostic waived with service. Pulls Louisville Metro permits. 10-year tank / 2-year labor warranty. Service area: Louisville + Jefferson County ZIPs matching the GBP listing.

### 1. Answer Sheet (water heater replacement)

| Agent asks | Spoken answer | What moves it |
|---|---|---|
| Price? | "A standard 40- or 50-gallon replacement runs about $1,800–$2,900 installed — that includes the unit, labor, the Louisville Metro permit, and haul-away. Tankless conversions run $4,200–$7,500." | Gas-line resizing, code upgrades (expansion tank, pan), fuel change |
| How soon? | "Same-day for active leaks if they call before noon; scheduled replacements are usually within 2 business days." | Emergency vs. scheduled |
| Do you cover [ZIP]? | "Yes — we cover Louisville and Jefferson County, including that ZIP." | Yes/no against the covered list |
| Permit? | "We pull the Louisville Metro permit and handle the inspection — it's included in the quote." | — |
| Warranty? | "10-year warranty on the tank, 2-year on our labor." | — |

### 2. Phone-Pickup Protocol (excerpt)

> Answer live: "Bluegrass Plumbing, this is Dana." If the caller says it's an automated assistant calling for a customer, don't ask for a callback number yet — answer the price, timing, and service-area questions straight from the Answer Sheet, then say: "We can hold a same-day slot; the customer can confirm and we'll text the arrival window." Never transfer an AI caller and never say we can't discuss price by phone — give the range.

### 3. CSR Quick-Reference Card

> **The 5 questions, in order:** price → timing → service area → permit → warranty. Answers above. **Never say:** a single guaranteed price; "I can't give prices over the phone." **Always end with:** a bookable next step.

### 4. AI-Receptionist Configuration Notes (excerpt)

> After-hours agent: on detecting an automated-assistant caller, skip the "what's going on with your plumbing today?" qualification flow and go straight to the price/timing/area/permit/warranty block, pulling ranges from the live pricebook. Offer to hold a morning slot. Hand off to the on-call human only for active-leak emergencies.

### 5. Consistency Reconciliation (excerpt)

> Website service-area page lists 40202–40223; GBP lists the same; Answer Sheet aligned. Warranty stated identically ("10-year tank / 2-year labor") on the phone card, the website, and GBP. No mismatch. Flagged and fixed: the old phone script said "financing available" while the site says "financing as low as ~$55/mo" — aligned both to the site language.

### 6. Auto-Drop Red-Flag Checklist (result)

> Business hours: live pickup ✓. After hours: AI agent answers on ring 2 ✓ (no voicemail path in the window Google calls). Price given as a range without transfer ✓. Service area matches listings ✓. One fix: the old after-hours greeting had ~8 seconds of hold music before the agent engaged — removed, because that alone can trigger a hang-up.

---

## Notes for the Shop

- This pack does not get the shop *called* — that is the AI Search Visibility Content Pack's job. Google picks who to dial from local rankings and how clearly the shop's public information answers common questions. Build the visibility first; this pack converts the call the visibility earns.
- The loss is invisible, which is why it is dangerous. There is no voicemail and no missed-call log when an agent hangs up. The only way to know it is happening is to assume it is and be ready.
- Ranges beat refusals every time. The instinct to protect margin by not quoting over the phone is exactly what forfeits the booking here. A range with a stated reason is both the honest answer and the one that wins the summary.
- Keep the phone answer and the web answer identical. The agent reads both and penalizes contradictions. Any time the pricebook, service area, hours, or warranty changes, update the Answer Sheet and the published entity facts in the same pass.
- Re-run the reconciliation quarterly and whenever the pricebook moves — especially after a vendor price-increase wave, when the ranges on the Answer Sheet can silently fall behind the estimates the techs are writing.
- This is a fast-moving surface. Google is first and named plumbing at launch, but the customer's-AI-calls-the-shop pattern is not Google-specific; treat the Answer Sheet as the shop's standing readiness for any assistant that starts phoning contractors on a homeowner's behalf.
