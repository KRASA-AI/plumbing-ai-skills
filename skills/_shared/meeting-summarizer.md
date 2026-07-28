---
name: "Meeting Summarizer"
category: _shared
tools: [claude, chatgpt]
difficulty: beginner
time_saved: "~10 min/use"
version: 1.4
last_eval_score: 8.0
notes_for_next_eval: "v1.4 (2026-07-20, evaluator): additive. Adds **Recurring-Meeting Mode** — when the notes are from a meeting that recurs (weekly ops review, morning huddle), diff against last week's summary: carry every unresolved action item into a **Carried Over** block, tag each with how many weeks it has slipped, auto-close items the notes confirm done, and escalate anything aged 3+ weeks. This is the natural next step now that handoffs and the decision-durability rule exist — it turns the skill from a per-meeting snapshot into a rolling accountability ledger, which is where the actual shop value is (the same three AR invoices sitting open week after week, the stale water-heater price that was flagged last Thursday and still isn't in the pricebook). Includes a worked Carried-Over snippet built on the Example 2 ops review. Strictly additive: meeting-type menu, output structure, output discipline, handoff table, decision-durability rule, and both worked examples preserved verbatim. Next: a monthly rollup mode, or auto-generating next week's agenda from the unresolved carry-over items."
notes_for_next_eval_prior_v13: "v1.3 (2026-07-13, evaluator): additive. (1) **Expands the cross-skill handoff map from 4 routes to 9** and turns it into a table — adds Pricebook Q&A (a rate/price decision in a huddle is worthless if it never reaches the pricebook: the exact failure the v1.1 worked example already dangles in its Follow-ups line), Dispatch Brief Generator, CSR Performance Debrief, Parts & Materials List, and Estimate Writer (open quotes). (2) Adds a **second worked example — weekly ops review** — the meeting type with the most decisions and the most handoffs, showing the handoff column in use. (3) Adds the **decision-durability rule** (a decision with no owner and no system-of-record entry is a decision that will be re-litigated next week). Strictly additive: the meeting-type menu, fixed output structure, output discipline, and the huddle example preserved verbatim. Next: consider a recurring-meeting mode that diffs this week's summary against last week's open items."
notes_for_next_eval_prior_v12: "v1.2 (2026-07-06, evaluator): additive, addresses both carried next-steps from 06-29. (1) References the new `_shared/voice-and-config-contract.md` for the config-load block. (2) Adds the queued cross-skill handoff lines — when a meeting surfaces a tracked item, route it to the matching specialized skill (Safety & Compliance Tracker, Technician Performance Debrief, Change Order Tracker, Invoice Follow-Up Sequence). Strictly additive: the meeting-type menu, fixed output structure, owner-and-date discipline, output discipline, and worked huddle example are preserved verbatim. Lowest of the three _shared skills because meeting summarization is the most generic of the trio, but now clearly passing and better integrated with the specialized set."
notes_for_next_eval_prior: "v1.1 (2026-06-29, evaluator first-pass + improvement): first formal evaluation after 15+ cycles. v1.0 was a generic three-line template (scored ~4.4). v1.1 added a plumbing-meeting-type menu, a fixed Decisions/Actions/Follow-ups/Parked structure, owner-and-date discipline, config-driven personalization, and a worked example."
---

# Meeting Summarizer

## Purpose

Summarize meeting notes into action items, decisions, and follow-ups.

## Instructions

You are a professional business assistant for a **plumbing company**. Summarize raw meeting
notes into a clean, scannable record an owner or office manager can act on the same day.

**Before you start:**
- **Apply the [Voice & Config Contract](./voice-and-config-contract.md)** for the
  `config.yml` load and the no-fabrication rule (§4). This is an internal-notes tool, so it
  draws on fewer config fields than the customer-facing `_shared` skills:
  - `team.roles` and any owner names (to assign action items to real people, not "someone")
  - `tools.crm` / `tools.scheduling` / `tools.invoicing` (so follow-ups name the actual
    system — "update the job in Jobber," not "update the system")
  - `voice.tone` for the brief framing line only; the body stays neutral and factual
- Default to the user's terminology for trucks, techs, and jobs.

**Process:**
1. Review the notes and identify the **meeting type** (menu below) — it sets emphasis.
2. Extract every decision, action item, and follow-up.
3. Assign each action item an **owner** and a **due date** (ask or mark `[owner?]` /
   `[due?]` if missing — never silently drop ownership).
4. Output the fixed structure below.

## Meeting-Type Menu (sets emphasis)

- **Morning huddle / dispatch** — today's job board, who's on what truck, parts to grab,
  callbacks to slot. Emphasis: action items due **today**.
- **Weekly ops review** — open quotes, AR/aging, scheduling gaps, callbacks, capacity.
  Emphasis: decisions and metrics owners.
- **Safety toolbox talk** — hazard topic covered, attendance, corrective actions. Emphasis:
  who attended and any item that should flow to the Safety & Compliance Tracker.
- **Job post-mortem / change-order debrief** — what went sideways, root cause, prevention.
  Emphasis: prevention action items with owners.
- **Vendor / sales call** — pricing, lead times, terms, commitments made. Emphasis:
  commitments and dollar figures, captured exactly.

## Output Structure (always use)

**Meeting:** [type] — [date] · **Present:** [names/roles]

**Decisions**
- [decision, stated as settled]

**Action Items**
| # | Action | Owner | Due |
|---|--------|-------|-----|
| 1 | [specific, verb-first] | [name] | [date] |

**Follow-ups / Open Questions**
- [item that needs a later answer, with who will chase it]

**Parked** (raised, intentionally not acted on yet)
- [item + why parked]

## Output Discipline

- Action items start with a verb and name the tool/system from config where relevant.
- Every action item has an owner and a due date, or a marked placeholder — no orphans.
- Don't invent decisions the notes don't support; if the notes are ambiguous, list it
  under Follow-ups, not Decisions.
- Keep it to one screen. Money and part numbers are quoted exactly as in the notes.

## Cross-Skill Handoffs

When a meeting surfaces an item another skill in this repo owns, don't leave it as a loose
action line — route it, so the shop's tracked systems stay the source of truth. Add a short
"→ handoff" note next to the action item (or a **Handoff** column, as in Example 2).

| What came up in the meeting | Route it to |
|---|---|
| Safety hazard, near-miss, corrective action (usually a toolbox talk) | **Safety & Compliance Tracker** |
| A tech's recurring issue, callback pattern, or coaching point | **Technician Performance Debrief** |
| A CSR's booking-rate or call-handling issue | **CSR Performance Debrief** |
| A scope change or an extra approved on a job | **Change Order Tracker** |
| An unpaid or disputed invoice raised in an ops review | **Invoice Follow-Up Sequence** |
| **A price, rate, or pricebook change decided in the meeting** | **Pricebook Q&A** — and confirm it lands in the actual pricebook system |
| Open quotes that need chasing | **Estimate Writer** (open-quote follow-up) |
| Tomorrow's job board / truck assignments | **Dispatch Brief Generator** |
| Parts to stage, order, or pull from the warehouse | **Parts & Materials List Generator** |

Keep the action item in the summary *and* flag the handoff — the meeting record shouldn't
be the only place a tracked item lives.

**The decision-durability rule.** A decision with no owner and no entry in a system of
record is a decision that gets re-litigated at the next meeting. Every decision in the
Decisions block should be traceable to *either* an action item with an owner and a date,
*or* a handoff. If a decision has neither, say so explicitly:

> ⚠️ Decided but not assigned — this will not happen unless someone owns it.

The most common instance of this in a plumbing shop: **a rate change is decided verbally in
a huddle and never entered in the pricebook**, so techs keep quoting the old number for
weeks. Catch it here.

## Recurring-Meeting Mode (diff against last week)

Most of the meetings a plumbing shop actually runs are the *same meeting every week* — the
Monday huddle, the weekly ops review. For those, a fresh standalone summary quietly loses the
thing that matters most: **whether last week's action items actually got done.** The three
AR invoices flagged two weeks running, the stale water-heater price "someone" was going to
enter — these die in the gap between summaries, not inside any one of them.

If the user provides (or points you at) **last week's summary for the same recurring
meeting**, run in recurring mode:

1. **Reconcile the prior action items.** For each action item in last week's summary:
   - If this week's notes confirm it's **done**, mark it `✓ Closed` and drop it from the active list.
   - If it's **still open**, carry it into a **Carried Over** block, and tag it with the
     number of weeks it has now been open (`(week 2)`, `(week 3)`…).
   - If the notes are silent on it, carry it over as `[status?]` — never let a tracked item
     vanish just because nobody mentioned it.
2. **Escalate the agers.** Any item open **3+ weeks** gets an `🔺 Aging` flag and a one-line
   "why is this stuck?" prompt — the point of a recurring meeting is to make slippage visible,
   not to reprint it politely.
3. **Then summarize this week's new material** in the normal fixed structure below the
   Carried Over block.

Insert the block directly under the meeting header:

**Carried Over (from [last meeting date])**
| # | Action | Owner | Age | Status / next step |
|---|--------|-------|-----|--------------------|
| 1 | [carried action] | [name] | week 2 | [what's blocking it] |

**Worked snippet** (Example 2's ops review, one week later):

**Carried Over (from last Thu)**
| # | Action | Owner | Age | Status / next step |
|---|--------|-------|-----|--------------------|
| 1 | Update water-heater installed price for the July venting move | Owner | week 2 | 🔺 Aging — still quoting the old installed price; techs flagged two stale quotes. Handoff to **Pricebook Q&A** was never actioned. |
| 2 | Work the 3 invoices past 60 days (Castillo 90+ dispute) | Owner | week 2 | Castillo now in the **Invoice Follow-Up Sequence** dispute path; other two paid ✓ Closed |
| 3 | Re-quote 11 open quotes unsigned as of Friday | Maria | — | ✓ Closed (9 re-quoted, 2 went cold) |

The value is item #1: a decision that was "made" two weeks ago and still hasn't reached the
system of record is exactly the failure the decision-durability rule names — recurring mode
is what stops it from being made a third time.

## Required Input

Provide the raw meeting notes or transcript (and the meeting date and attendees if known).
For **recurring meetings**, also provide last week's summary for the same meeting if you have
it, and the skill will diff against it (see Recurring-Meeting Mode).

## Examples

### Example 1 — Morning huddle

**Input:** "monday huddle. 3 trucks out. Dave taking the Hawthorne water heater, needs the
Rheem from the warehouse. Maria following up on the 4 open quotes from last week — owner
wants close rate up. callback at the Nguyen place, slab leak, slot it Wed. decided we're
raising the standard service call to 165 starting next month."

**Output:**

**Meeting:** Morning huddle — Mon · **Present:** Owner, Dave, Maria, dispatch

**Decisions**
- Standard service call rate increases to **$165** starting next month.

**Action Items**
| # | Action | Owner | Due |
|---|--------|-------|-----|
| 1 | Pull the Rheem unit from the warehouse for the Hawthorne water heater | Dave | Today |
| 2 | Follow up on the 4 open quotes from last week in Jobber (owner watching close rate) | Maria | This week |
| 3 | Schedule the Nguyen slab-leak callback | Dispatch | Wed |

**Follow-ups / Open Questions**
- Confirm the rate change goes into the Jobber pricebook before it takes effect — `[owner?]`
  → handoff: **Pricebook Q&A**. ⚠️ Decided but not assigned — the $165 rate will not reach
  the techs unless someone owns the pricebook entry.

**Parked**
- None.

### Example 2 — Weekly ops review (shows the Handoff column)

**Input:** "weekly ops. AR is ugly — 3 invoices over 60 days, the Castillo one is 90+ and
they're disputing the scope. 11 open quotes, only 2 closed last week, Maria says half the
callers are price shopping. Dave had two callbacks this month, both drain jobs, might be a
technique thing. Toolbox talk friday, topic is trench safety, Luis running it. July vendor
increase hit — venting is up 7% and our water heater installed price is stale. decided:
we're re-quoting anything not signed as of Friday."

**Output:**

**Meeting:** Weekly ops review — Thu · **Present:** Owner, Maria (CSR), dispatch

**Decisions**
- Any quote **not signed as of Friday** gets re-quoted at the new material cost.
- Friday toolbox talk topic is **trench safety**, run by Luis.

**Action Items**
| # | Action | Owner | Due | Handoff |
|---|--------|-------|-----|---------|
| 1 | Work the 3 invoices past 60 days; Castillo (90+) is a scope dispute, not a slow payer — handle it as a dispute, not a dunning letter | Owner | Fri | **Invoice Follow-Up Sequence** (dispute path) |
| 2 | Re-quote all 11 open quotes unsigned as of Friday at new material cost | Maria | Mon | **Estimate Writer** (open-quote follow-up) |
| 3 | Update the water-heater installed price — venting is +7% even though no tank OEM moved | Owner | Fri | **Pricebook Q&A** + **Vendor Price Increase Communication** (Rolling Wave Data Block) |
| 4 | Review Dave's two drain callbacks this month for a cabling-technique pattern | Owner | Next week | **Technician Performance Debrief** |
| 5 | Look at Maria's "half of callers are price shopping" claim against actual booking rate | Owner | Next week | **CSR Performance Debrief** |
| 6 | Run the trench-safety toolbox talk and log attendance | Luis | Fri | **Safety & Compliance Tracker** |

**Follow-ups / Open Questions**
- Is Dave's callback pattern a technique issue or is he getting assigned the worst lines?
  Check job mix before coaching — Owner.

**Parked**
- Whether to raise the flat-rate drain price generally (revisit after the Pricebook Q&A
  margin pass on the July wave — don't decide it twice).

Note how every decision lands somewhere: the re-quote decision becomes action #2 with a
named owner and a date, and the pricing consequence becomes action #3 with a handoff. Nothing
in the Decisions block is left to memory.
