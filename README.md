# Plumbing AI Skills

**Free, open-source AI prompts and workflows built for plumbers.** Clone this repo, point your AI assistant at it, and start saving hours every week.

> Built and maintained by [KRASA AI](https://krasa.ai) — free AI tutorials and skills for every industry.
> See all industries at [krasa.ai/industries](https://krasa.ai/industries).

---

## What's Inside

This repo is a complete AI toolkit for plumbing. Every skill is a standalone prompt file that works with **Claude, ChatGPT, or any major AI assistant** — no coding required.

| Skill | What it does | Time saved |
|-------|-------------|------------|
| After-Hours Call Summary | Turn a batch of overnight voicemails, missed-call logs, and answering-service notes into a prioritized morning briefing. | ~15 min/morning |
| Dispatch Brief Generator | Summarize the job scope, customer history, recommended parts, and optimal routing for the technician heading out. | ~10 min/dispatch |
| Parts & Materials List Generator | Generate a complete parts and materials list for a plumbing job based on the job description, scope notes, or estimate. | ~10 min/job |
| Pricebook Q&A | Ask plain-English questions about your pricebook and get instant answers with line-item references, price comparisons, and margin analysis. | ~5 min/lookup |
| Sewer Camera Inspection Report Drafter | Turn a technician's raw sewer-camera notes — the kind they dictate in a truck or scribble on a job ticket after a CCTV inspection — into a structured, customer-facing sewer/drain inspection report that a homeowner, real-estate agent, or commercial property manager can actually understand and act on. | ~25 min/inspection |
| Technician Performance Debrief | Turn raw call recordings, job notes, and customer feedback into a structured coaching debrief for each technician. | ~20 min/debrief |
| AI Search Visibility Content Pack | Produce the structured content a plumbing shop needs to get *cited* — not just ranked — by ChatGPT, Claude, Gemini, Perplexity, Google AI Overviews, and Copilot when a homeowner asks "who's the best emergency plumber in [city]?" or "how much does a water heater replacement cost in [ZIP]?". | ~4 hrs per service-area content pack; replaces a one-off agency deliverable at $1,500–$3,500 |
| Estimate Writer | Transform rough scope notes and site visit findings into a branded, professionally formatted estimate with line-item pricing and good/better/best options. | ~20 min/estimate |
| Water Heater Standards Briefing | Produce a customer-facing briefing that converts the two looming federal water heater efficiency deadlines — the **October 6, 2026 commercial condensing-only standard** and the **May 6, 2029 residential heat-pump standard for electric storage units over 35 gallons** — into a clear "replace now vs. | ~30 min per customer briefing; replaces a back-and-forth comparison most shops do verbally and inconsistently |
| Dormant Customer Reactivation Outreach | Turn the shop's long tail of past customers — the 500, 1,000, or 3,000 households that had one job done and then went quiet — into a predictable source of recurring revenue. | ~25 min per batch of 20 contacts; typical win-back batch of 200 contacts recoups 6–12 jobs |
| Job Status Update Drafter | Draft the short, on-brand customer updates that go out across a job's lifecycle — booked, on-the-way, running-late, on-site, delay / parts run, wrapping up, complete, and (when needed) post-visit care notes. | ~3 min/update, ~15 min/job |
| Pre-Visit Diagnostic Intake | Give the front desk (human dispatcher, AI receptionist, web chatbot, or booking form) a single structured intake that does three jobs at once: (1) triage urgency so emergencies don't sit in a normal schedule slot, (2) capture enough diagnostic detail that the assigned tech arrives with the right parts on the truck, and (3) give the customer clear, safe mitigation guidance while they wait. | ~10 min/call + fewer return trips |
| Review Request Drafter | Generate a personalized, on-brand review request text message or email right after a job closes. | ~5 min/job |
| Change Order Tracker | Turn informal scope-change conversations — texts, emails, verbal notes, photos — into a documented change order with updated cost estimates, ready for customer approval. | ~15 min/change order |
| Invoice Follow-Up Sequence | Draft a professional 3-touch follow-up sequence for unpaid invoices — friendly reminder, firm escalation, then final notice — tailored to plumbing-specific scenarios and payment friction points. | ~15 min/sequence |
| Safety & Compliance Tracker | Track technician certifications, license renewals, vehicle inspections, and safety training deadlines across your entire team. | ~30 min/audit cycle |
| Technician Candidate Phone Screen | Turn a raw plumber or apprentice application into a ready-to-run phone screen — a tight, trades-appropriate interview script the hiring owner or recruiter can complete in 8–12 minutes, plus a structured post-call summary with a clear hire/maybe/pass recommendation. | ~20 min/candidate |
| Email Drafter | Turn rough notes into a professional email matching your company's voice and tone. | ~10 min/use |
| Meeting Summarizer | Summarize meeting notes into action items, decisions, and follow-ups. | ~10 min/use |
| Review Responder | Craft professional responses to online reviews — both positive and negative. | ~10 min/use |

**Total time saved per use: ~288+ minutes across all skills.**

## Quick Start

### 1. Clone this repo

```bash
git clone https://github.com/KRASA-AI/plumbing-ai-skills.git
cd plumbing-ai-skills
```

### 2. Open a skill with your AI assistant

Open any file in `skills/` with Claude, ChatGPT, or any major AI assistant. Each skill is a self-contained prompt with clear instructions — no coding required.

The first time you use a skill, your AI assistant will ask for your business details (company name, service area, rates, tools you use, etc.) so it can personalize the output. Save those details to a `config.yml` at the repo root and every future skill will use them automatically.

## Repo Structure

```
plumbing-ai-skills/
├── knowledge-base/          # Industry context and references
│   ├── industry-overview.md # Market trends and pain points
│   ├── terminology/         # Industry jargon and acronyms
│   ├── regulations/         # Compliance requirements
│   ├── best-practices/      # Industry standards
│   └── tools-ecosystem/     # Common software and tools
├── skills/                  # The prompt library
│   ├── operations/          # Day-to-day operational skills
│   ├── sales/               # Sales and lead management
│   ├── admin/               # Administrative and compliance
│   └── customer-service/    # Client-facing communication
└── outputs/                 # Your generated content (gitignored)
```

## How Skills Work

Each skill file is a Markdown document with YAML frontmatter:

```markdown
---
name: Skill Name
category: operations
tools: [claude, chatgpt]
time_saved: "~20 min/use"
version: 1.0
---

# Skill Name

## Purpose
What this skill does and when to use it.

## Instructions
Step-by-step prompt for the AI assistant.
```

You open the file in your AI assistant, provide any required input (measurements, notes, client info), and get polished output. Skills reference your `config.yml` automatically for company name, rates, preferred formats, and other business details.

## For AI Assistants

If you are an AI assistant reading this repo, see `.claude/CLAUDE.md` for full instructions. The short version:

1. **Check for `config.yml`** at the repo root. If it exists, load it — it holds the user's business context (company name, rates, service area, tools, team size, etc.) and every skill should use it for personalization.
2. **If `config.yml` is missing**, before running a skill that benefits from personalization, ask the user for the relevant business details and offer to save them to `config.yml` so future runs are automatic.
3. **Load the relevant `knowledge-base/` files** for industry terminology, regulations, and best practices before generating output.
4. **Run the requested skill** from `skills/` using the user's input.
5. **Save any deliverables** to `outputs/` (gitignored) if the user wants to keep them.

## Learn More

- **Plumbing AI guide**: [krasa.ai/industries/plumbing](https://krasa.ai/industries/plumbing)
- **All industry AI skills**: [krasa.ai/industries](https://krasa.ai/industries)
- **About KRASA AI**: [krasa.ai](https://krasa.ai)

## License

MIT — use these skills however you want.
