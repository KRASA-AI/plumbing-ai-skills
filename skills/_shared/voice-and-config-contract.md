---
name: "Voice & Config Contract"
category: _shared
type: reference
version: 1.0
last_updated: 2026-07-06
notes_for_next_eval: "v1.0 (2026-07-06, evaluator): new shared reference artifact — the top pending shared-consolidation item carried since 2026-06-08 and named explicitly in the 06-29 summary as the highest-value next consolidation. Not a runnable skill; it is the single config-mapping + voice contract that the three _shared skills (Email Drafter, Meeting Summarizer, Review Responder) reference instead of each repeating a config-load block. Over time the nine Spanish-anchored specialized skills can also point their terminology/voice tables here. Additive: retires duplication, changes no existing skill's output. Next: migrate the specialized skills' repeated voice tables onto this contract; fold in the long-carried bilingual-spanish-tone-guide."
---

# Voice & Config Contract

**This is a reference file, not a runnable skill.** It defines the single, canonical way
every `_shared` skill (and, over time, the specialized skills) loads and applies
`config.yml`. Instead of each skill repeating a "load these fields" block, each skill says
"apply the Voice & Config Contract" and adds only the fields unique to its job.

## 1. Load order

Read `config.yml` once at the start of any drafting task. If it is missing, ask the user
for the three fields you cannot fake — `company.name`, `voice.tone`, and a callback number
— and proceed with clearly marked `[confirm: ...]` placeholders for everything else.

## 2. The field map (what each field is for)

| config field | Use it for |
|---|---|
| `company.name` | Sign every customer-facing output. Never leave a draft unsigned. |
| `company.service_area` | Location references, "we serve …", scheduling context. |
| `company.website` | Signature block; review/booking CTAs. |
| `company.location` | Regional tone, permit/jurisdiction context. |
| `team.roles` + owner names | Assign action items and owners to **real people**, never "someone." |
| `tools.crm` / `scheduling` / `invoicing` | Name the actual system ("update the job in Jobber," not "the system"). |
| `pricing.rates.standard_service_call` / `hourly_rate` | Ground any money reference; never invent a rate. |
| `pricing.payment_terms` | Payment lines in quotes, invoices, job-complete notes. |
| `pricing.financing` (bool) | Only mention financing if **true**; never if false. |
| `pricing.average_job_size` | Right-size tone and follow-up urgency. |
| `services.core` / `specialties` / `excluded` | Reference only work the shop actually does; never offer excluded work. |
| `services.customer_type` | Residential vs. commercial register. |
| `voice.tone` | The single most important field — match it literally (see §3). |
| `voice.always_use` | Open with one where natural. |
| `voice.never_use` | Never emit these words (in plumbing, usually "cheap"/"discount" — lead with value + warranty instead). |
| `voice.followup_style` | Cadence for any multi-touch output. |

## 3. Voice rules (apply to every customer-facing output)

1. **Match `voice.tone` literally.** If it says "the neighbor you trust," write like a
   neighbor, not a corporation.
2. **Open with an `always_use` phrase** where it reads naturally — never force it.
3. **Never emit a `never_use` word.** Reframe around value, warranty, and workmanship.
4. **Sign with `company.name`** (and website + callback number if present).
5. **Financing:** one optional line only if `pricing.financing` is true *and* money is on
   the table; otherwise silent.

## 4. The no-fabrication rule (applies to every skill)

Never invent a price, warranty term, appointment time, part number, rate, or rebate the
user did not provide. Ask, or leave a clearly marked `[confirm: ...]` placeholder. This
rule outranks fluency — a draft with an honest placeholder is correct; a draft with a
confident wrong number is a liability.

## 5. Public-writing privacy rule (customer-facing published output)

When the output is **public** (review replies, social, anything a stranger reads), never
confirm a customer's address, what was wrong with their plumbing, what they paid, or
whether they are a customer at all beyond what they themselves disclosed. Treat service
details like protected information; move specifics to a private channel.

## 6. Bilingual pattern (shared)

Nine specialized skills already ship a Spanish variant; the `_shared` skills should offer
the same when the shop serves Spanish-speaking customers. When asked for a bilingual
version:

- Translate for **meaning and warmth, not word-for-word.** Keep the same `voice.tone`.
- Use the customer's regional Spanish where known; default to neutral Latin-American Spanish.
- Keep trade terms the customer will recognize (e.g., *calentador de agua* for water heater,
  *fuga* for leak, *destape* for drain clearing) rather than over-formal equivalents.
- Never machine-translate a `never_use`/`always_use` phrase literally — carry its *intent*.
- Output English first, then the Spanish version under a clear `— Español —` divider, unless
  the user asks for Spanish only.

*(This section is the seed of the long-carried `_shared/bilingual-spanish-tone-guide.md`;
the specialized skills' per-skill Spanish tables can migrate here next.)*
