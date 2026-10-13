---
name: "Review Responder"
category: _shared
tools: [claude, chatgpt]
difficulty: beginner
time_saved: "~10 min/use"
version: 1.6
last_eval_score: 8.3
notes_for_next_eval: "v1.6 (2026-10-13, evaluator): additive. Adds an **AI-Receptionist / Automation Complaint Reviews** playbook — the new review genre that follows shops adopting AI voice agents and answering services ('I got a robot,' 'nobody called back'): treat it as a responsiveness complaint, be honest about what answered, show the human path, fix offline, and route an internal note to the After-Hours Call Summary / CSR Performance Debrief / Agentic-Call Answer Pack owners; with avoid-phrases and a worked 2-star Google example. Everything prior preserved verbatim. Next: none queued — re-read fresh."
notes_for_next_eval_prior_v15: "v1.5 (2026-07-28, evaluator): additive, closes the one carried next-step from 07-20. Adds a **5-Star A/B Note** — two response styles (Warm/relationship vs. Brief/efficient) for 5-star and warm-4-star reviews, with guidance on when each fits: Warm for a shop leaning on personal-relationship positioning or a low volume of 5-stars where each reply is a chance to reinforce the relationship; Brief for a shop with high 5-star volume where a long reply to every one starts to look automated, or where the owner's time is the binding constraint. Includes both variants written against the same input so the difference is concrete, not just described. Scored +0.1 (reference/technique addition, not a new capability) — same tier as the 07-20 per-platform table. Strictly additive: all tier playbooks, the fake/extortion block, response-timing rules, the Local-SEO note, the Per-Platform Format & Length table, the bilingual note, output discipline, and all three worked examples preserved verbatim. Next: none currently queued — the _shared skill trio has now closed every next-step from its last four cycles; watch for a natural next capability rather than force one."
notes_for_next_eval_prior_v14: "v1.4 (2026-07-20, evaluator): additive, closes the one carried next-step from 07-13. Adds a **Per-Platform Format & Length** table (Google Business Profile, Yelp, Facebook, Nextdoor, BBB) with the practical length target and the front-load rule for each surface, plus a truncation note (Google collapses a long reply behind a 'More' fold in the mobile app, so the concession and the offer-to-fix must land in the first ~1-2 lines or a skimming prospect never sees them). This is the reputation-management mechanics layer the tier playbooks assume but never spelled out. Strictly additive: v1.3's tier playbooks, fake/extortion block, response-timing rules, Local-SEO note, bilingual note, output discipline, and all three worked examples preserved verbatim. Next: an owner-response A/B note if a shop wants to test warmth vs. brevity on 5-star replies."
notes_for_next_eval_prior_v13: "v1.3 (2026-07-13, evaluator): additive, closes the one carried next-step from 07-06. (1) Adds the worked **mixed 3-star example** — the tier that had a playbook but no example, and the hardest tier to write well (the response has to be gracious without conceding, and it is read by more prospects than any other tier). (2) Adds a **Local-SEO note**: responses are indexed and read by prospects comparing shops, so name the city/service naturally once, never keyword-stuff — a real, commonly-botched reputation-management practice. (3) Adds a **response-timing rule** (respond within 24-48h; negative reviews same business day) so the skill produces a cadence, not just a draft. Strictly additive: v1.2's tier playbooks, fake/extortion block, bilingual note, output discipline, and both prior examples preserved verbatim. Next: a per-platform character-limit table if a shop reports truncation on Yelp/Facebook."
notes_for_next_eval_prior_v12: "v1.2 (2026-07-06, evaluator): additive deepening, addresses both carried next-steps from 06-29. (1) References the new `_shared/voice-and-config-contract.md` for the config-load + public-privacy rules. (2) Adds the fake/extortion/wrong-business review flagging sub-block that was explicitly queued at 06-29 — a decision aid for spotting non-genuine reviews, a calm public holding response, and the platform-report path, without accusing publicly. (3) Adds a bilingual (Spanish) note pointing at the shared contract. Strictly additive: all v1.1 tier playbooks, output discipline, and both worked examples preserved verbatim. Next: a worked mixed (3-star) example."
notes_for_next_eval_prior: "v1.1 (2026-06-29, evaluator first-pass + improvement): first formal evaluation after 15+ cycles unevaluated. v1.0 was the generic three-line template (scored ~4.6). v1.1 added star-rating-tiered playbooks (5-star, 3-4 star, 1-2 star), the public-privacy rule, offline de-escalation, config-driven personalization, platform length notes, and 5-star + 1-star examples. Fills the request->respond loop opposite Review Request Drafter."
---

# Review Responder

## Purpose

Craft professional responses to online reviews — both positive and negative.

## Instructions

You are responding **publicly** on behalf of a **plumbing company** to a customer review
(Google, Yelp, Facebook, etc.). The response is read by every future customer who checks
the shop's rating, so it is a marketing asset and a reputation defense at the same time.

**Before you start:**
- **Apply the [Voice & Config Contract](./voice-and-config-contract.md)** — it defines the
  `config.yml` load, the voice rules, the no-fabrication rule, and the public-writing privacy
  rule (§5) that govern this skill. This skill relies especially on:
  - `company.name` (sign as the shop / owner, warmly), `company.service_area`, owner name
  - `voice.tone`, `voice.always_use`, `voice.never_use`
  - `pricing.financing` only if relevant; `services` for honest references to what the shop does
- Reminder of the contract's public-privacy rule, because it governs every line here: this is
  **public** writing — never confirm the customer's address, what was wrong with their
  plumbing, what they paid, or whether they are a customer at all beyond what they themselves
  disclosed. Move anything specific to a private channel.

**Process:**
1. Read the review and note the **star rating** and the **specific points** raised.
2. Pick the matching tier playbook below.
3. Draft a response in the shop's voice. Ask one clarifying question only if you need a fact
   to respond safely (e.g., whether the complaint is from an actual customer).
4. Output the ready-to-post response.

## Tier Playbooks

**5-star (and warm 4-star)** — short and genuine. Thank them by first name, echo one
specific thing they mentioned (the tech's name, the same-day fix), reinforce the warranty
or the relationship, invite them back. 2-4 sentences. Don't upsell hard.

**3-4 star (mixed)** — thank them, acknowledge the specific gap they noted without being
defensive, state briefly how the shop handles that, and offer to make it right offline.
Keep it gracious — a well-handled mixed review reads better to prospects than a flawless one.

**1-2 star (negative)** — the goal is to look reasonable to the *next reader*, not to win
the argument. Structure:
1. Thank them for the feedback / acknowledge the frustration (no groveling, no "we're so
   sorry you feel that way" non-apologies).
2. Take responsibility for the experience without admitting legal fault or disputing facts
   publicly.
3. Move it offline immediately: give the owner's name and a direct number/email and ask
   them to reach out so it can be resolved.
4. One short line, if true, on the shop's standard (warranty, callback policy) — stated as
   who the shop is, not as a rebuttal.
Never argue, never reveal job/payment details to "correct" them, never threaten. If the
review looks fake or like an extortion attempt, still respond calmly for the public record
and flag it for the owner to report through the platform — don't accuse publicly.

## Fake / Extortion / Wrong-Business Review Handling

Before responding to a negative review, sanity-check whether it is even a genuine customer.
Google and Yelp both allow removal of reviews that violate their policies, but only if you
respond correctly and report them — a public accusation can get *your* response flagged
instead. Watch for these signals (any one is a yellow flag; two or more is a strong flag):

- **No record of the job** — name, address, or dates match nothing in the CRM.
- **Wrong business** — details describe a service the shop doesn't offer, a location it
  doesn't serve, or a competitor's tech name.
- **Pay-to-remove pressure** — the reviewer (or a follow-up message) offers to delete the
  review for money, a free job, or a discount. This is extortion; do not pay.
- **Bulk / bot pattern** — reviewer's history is a burst of 1-stars across unrelated
  businesses, or generic wording with no specifics.
- **Ex-employee / competitor tells** — internal knowledge no customer would have, or
  language aimed at hurting rather than resolving.

**How to respond when a review is likely fake:** post one calm, short holding response for
the public record — *do not accuse, do not argue, do not confirm or deny any customer
relationship.* Then hand the removal to the owner. Template:

> "Thank you for the feedback. We take every review seriously, but we don't have a record of
> service matching this. If we've worked together, please reach [owner] directly at [number]
> so we can make it right — we'd genuinely like to help. — [Company]"

Then, in a separate note to the owner (not posted publicly), flag:
1. Which signals fired and why you suspect it isn't genuine.
2. The exact platform-report path — Google: the review's ⋮ → "Report review" → the matching
   policy (off-topic, conflict of interest, fake engagement); Yelp: "Report review" flag.
3. A reminder to **never pay** an extortion demand and to screenshot any pay-to-remove
   message before responding.

Escalate to the owner rather than deciding unilaterally when the review *might* be a real
customer with a distorted account — when in doubt, treat it as genuine and de-escalate offline.

## Bilingual responses

If the shop serves Spanish-speaking customers and the review is in Spanish (or the owner
wants a Spanish reply), follow the bilingual pattern in the Voice & Config Contract (§6):
translate for warmth and meaning, keep the same `voice.tone`, and carry the intent of
`always_use`/`never_use` rather than translating them literally.

## Response Timing (part of the deliverable)

A good response posted late is worth less than a decent one posted fast — prospects read the
*most recent* reviews and the shop's replies to them.

- **1-2 star:** same business day. If the owner needs to check the job first, post the
  short acknowledgment ("Thank you — I'm looking into this now and will reach out today")
  and follow up in the same thread once resolved.
- **3-4 star:** within 24 hours.
- **5-star:** within 48 hours. Don't let them sit unanswered — an unreplied wall of 5-stars
  reads as an absent owner.
- **After an offline resolution:** if the customer updates or removes the review, thank
  them once, briefly. Never ask them to change the rating as a condition of the fix.

## Local-SEO Note (why the wording matters beyond the one customer)

Review responses are public, indexed, and read by prospects comparison-shopping shops in
the same town. Two rules:

- **Name the service and the city once, naturally** — "glad we could get your water heater
  back up in [city]" — because that is how the response reads to a prospect who is skimming
  for "does this shop do what I need, near me."
- **Never keyword-stuff.** "Best emergency plumber [city] drain cleaning water heater
  repair" in a review reply is transparently spammy to a human, and it makes the shop look
  desperate to the exact person deciding whether to call. One natural mention, maximum.

## Per-Platform Format & Length

The tier playbooks set the *content*; the platform sets how much of it a prospect actually
sees. The single rule that matters across all of them: **front-load the concession and the
offer-to-fix.** A prospect skimming on a phone reads the first line or two and moves on, and
several surfaces literally hide the rest behind a fold.

| Platform | Practical length | What to know |
|---|---|---|
| **Google Business Profile** | 2-5 sentences | The reply shows under the review; on mobile a longer reply collapses behind **"More"** — put the acknowledgment and the direct contact in the first ~1-2 lines, before the fold. Most-read surface; treat it as primary. |
| **Yelp** | 3-5 sentences | Public comment vs. a private Direct Message — for a negative review, post a short public reply *and* send the offer-to-resolve by DM. Yelp is touchy about anything that reads as incentivizing reviews; keep the public reply purely about service. |
| **Facebook / Recommendations** | 2-4 sentences | Threaded and casual; a warmer register fits. Replies are visible to the reviewer's network, so it doubles as light social proof — but never tag or name the customer beyond the first name they used. |
| **Nextdoor** | 2-4 sentences | Hyper-local and neighbor-to-neighbor; the city/service mention from the Local-SEO note lands naturally here, and neighbors read owner replies closely. Same-day on anything negative — Nextdoor threads pile on fast. |
| **BBB** | Slightly longer OK | More formal, complaint-resolution framing; factual and process-oriented ("we've reached out directly to schedule the re-visit") reads better than warmth. Still no private job or payment details. |

If a reply must run long (a detailed negative response), write it so the first sentence stands
alone as a complete, reasonable-sounding acknowledgment — that is the sentence most prospects
read, and on Google it may be the only one they see before the fold.

## 5-Star A/B Note (two valid styles — pick one and stay consistent)

The 5-star tier playbook above is deliberately short, but "short and genuine" still leaves
room for two different, both-correct styles. Which one fits depends on the shop, not the
review:

- **Warm / relationship style** — a full 3-4 sentences, echoes a specific detail, invites
  them back by name-checking the tech again. Fits a shop that positions on personal
  relationship and neighborliness, or one with a lower volume of 5-stars where each reply is
  worth the extra beat.
- **Brief / efficient style** — 1-2 sentences, still genuine, no filler. Fits a shop getting
  a high volume of 5-stars, where a long, similar-sounding reply under every single one starts
  to read as templated (prospects notice), or where the owner is doing this themselves between
  jobs and needs it fast.

Neither is "more correct" — pick one and apply it consistently so the shop's reply voice
reads as a deliberate choice, not inconsistency. Same input, both styles:

**Input:** "Dave came out same day, fixed our water heater, super clean and friendly. Highly
recommend!"

**Warm / relationship:**
> Thank you, Karen! We're glad Dave got your hot water back the same day — he's one of the
> good ones. We stand behind the work, so if anything ever comes up, just call. Thanks for
> choosing us, and welcome back anytime. — Example Plumbing Co

**Brief / efficient:**
> Thanks, Karen — glad Dave got you fixed up same-day. We're here if you need us again. —
> Example Plumbing Co

If the shop hasn't stated a preference, default to Warm for the first few replies you draft
and ask which style they'd rather standardize on; don't silently switch styles reply to reply.

## AI-Receptionist / Automation Complaint Reviews

Shops increasingly answer after-hours and overflow calls with an AI voice agent, an
answering-service script, or an auto-text — and a new kind of negative review follows: "I got a
robot," "the AI took my info and nobody called back," "it booked me for the wrong day." These
read as tech complaints but are really **responsiveness** complaints, and prospects reading
them are asking one thing: *if I call this shop, will a person actually help me?*

**Playbook (any star tier):**
1. **Name the real failure, not the tool.** Acknowledge the missed callback, the wrong booking,
   or the wait — that's what hurt. Don't defend or explain the software, and never blame the
   vendor publicly.
2. **Be honest about what answered.** If an automated system or answering service took the
   call, don't imply a staff member did. Never claim "a team member spoke with you" unless one
   did. Saying plainly that the shop uses an after-hours system *and* how a human follows up is
   more reassuring to prospects than a vague apology.
3. **Show the human path.** Give the direct line (from `company.phone`) or say a named person
   (owner/office manager role from config) will reach out — one sentence, no policy lecture.
4. **Fix-forward, privately.** Offer to make it right offline; never restate the job details,
   address, or what the customer said on the recording (public-privacy rule, contract §5).
5. **Internal note (not posted):** flag the review for whoever owns phone handling — it is a
   data point for the After-Hours Call Summary, CSR Performance Debrief, and Agentic-Call
   Answer Pack (callback timing, transfer rules, the "leave a message" dead end) rather than a
   one-off reputation task.

**Avoid:** "Our system shows…" (sounds like the robot is still talking), "We're sorry you
didn't like our new technology" (defensive), and promising to stop using automation unless the
owner has actually decided that.

**Worked example (2-star, Google):**

> *Review:* "Called at 9pm with water under my sink. Some AI answered, said a plumber would call
> me back. Nobody did until 11am the next day. Fixed fine but that wait was ridiculous."
>
> *Response:* "Thanks for telling us, and we're sorry — a 14-hour wait for a callback with water
> under the sink isn't the response we promise, whoever answers the phone. Our after-hours line
> is set up to get an on-call tech to you quickly, and that night it didn't. We're glad the
> repair held, and we've reviewed how evening leak calls get escalated so they reach a person
> sooner. If there's anything else we can do, please call [office manager role] directly at
> [company.phone]. — [company.name]"
>
> *Internal note:* 9pm active-leak call, callback at 11am next day → escalation rule gap.
> Route to After-Hours Call Summary owner.

## Output Discipline

- Match `voice.tone`; never use any `never_use` word.
- Keep responses short — Google/Yelp readers skim. 5-star: 2-4 sentences. Negative: ~4-6
  sentences max.
- Use the reviewer's first name once if they posted under one.
- No private details, ever. No invented facts. Sign with the shop or owner name.

## Required Input

Paste the review text (and the star rating and reviewer name if not obvious). Note if you
believe the review is not from a real customer.

## Examples

**5-star input:** "Dave came out same day, fixed our water heater, super clean and friendly.
Highly recommend!"

**Response:**
Thank you, Karen! We're glad Dave got your hot water back the same day — he's one of the
good ones. We stand behind the work, so if anything ever comes up, just call. Thanks for
choosing us, and welcome back anytime. — Example Plumbing Co

---

**1-star input:** "Way overpriced and the guy left a mess. Won't use again."

**Response:**
Thank you for the feedback, and I'm sorry your experience didn't meet the standard we hold
ourselves to — a clean worksite and clear pricing are non-negotiable for us. I'd like to
understand what happened and make it right. Please reach me directly: Tom, owner, at
(916) 555-0142 or tom@exampleplumbing.com. Every job we do is backed by our workmanship
warranty, and I want the chance to stand behind this one. — Tom, Example Plumbing Co

---

**3-star input (mixed):** "Work itself was fine, no complaints about the repair. But the
window was 8-12 and the tech didn't show until almost 2, and nobody called me. I took a
half day off for this."

**Response:**
Thank you for the honest review, Priya — and you're right, that's on us. The repair holding
up is the baseline; keeping you posted when a window slips is part of the job too, and we
missed it. We text an updated ETA when a tech gets held on a prior call, and that clearly
didn't reach you. I've flagged it with dispatch so it doesn't repeat. If you'll give me a
call at (916) 555-0142, I'd like to make the lost half day right. Thanks for trusting us
with the repair in the meantime. — Tom, Example Plumbing Co

**Why this works (the mixed tier is the one shops get wrong):**
- It **concedes the specific gap** (the missed ETA call) without conceding the work — the
  customer already said the repair was fine, so defending it would look tone-deaf.
- It states **what the shop's standard actually is** (an ETA text when a window slips) as
  identity, not as an excuse — a prospect reading this learns the shop *has* a policy.
- It offers a concrete remedy **offline**, and does not negotiate the rating.
- No non-apology ("sorry you feel that way"), no over-apology, no discount promised that
  the owner didn't authorize.
