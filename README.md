# Plumbing AI Skills

**Free, open-source AI prompts and workflows built for plumbers.** Clone this repo, point your AI assistant at it, and start saving hours every week.

> Built and maintained by [KRASA AI](https://krasa.ai) — free AI tutorials and skills for every industry.
> See all industries at [krasa.ai/industries](https://krasa.ai/industries).

---

## What's Inside

This repo is a complete AI toolkit for plumbing. Every skill is a standalone prompt file that works with **Claude, ChatGPT, or any major AI assistant** — no coding required.

| Skill | What it does | Time saved |
|-------|-------------|------------|
| 📝 Estimate Writer | Turn rough scope notes into a branded, line-item estimate ready for customer approval. | ~20 min/estimate |
| 📞 After-Hours Call Summary | Transcribe and triage voicemails so you see the job type, urgency, and callback number first thing. | ~15 min/morning |
| ⭐ Review Request Drafter | Generate a polite, on-brand review request text or email right after the job closes. | ~5 min/job |
| 💰 Invoice Follow-Up Sequence | Draft a 3-touch follow-up sequence for unpaid invoices — friendly, firm, then final. | ~10 min/invoice |
| 🚚 Dispatch Brief Generator | Summarize job scope, customer history, recommended parts, and optimal route for the tech heading out. | ~10 min/dispatch |
| 📖 Pricebook Q&A | Ask plain-English questions about your pricebook and get instant answers with line-item references. | ~5 min/lookup |
| 📋 Change Order Tracker | Turn mid-job scope changes into documented change orders with cost breakdowns and customer approval. | ~15 min/change order |
| 🔧 Parts & Materials List | Generate a complete parts checklist by job type with code-required items flagged and a supply house PO draft. | ~10 min/job |

**Total time saved per use: ~90+ minutes across all skills.**

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
