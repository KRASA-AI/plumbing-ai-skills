---
name: "Change Order Tracker"
category: admin
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~15 min/change order"
version: 1.1
last_eval_score: 9.0
---

# 📋 Change Order Tracker

## Purpose

Turn informal scope-change conversations — texts, emails, verbal notes, photos — into a documented change order with updated cost estimates, ready for customer approval. Prevents revenue leakage from untracked extras.

## When to Use

- A customer asks for additional work mid-job ("while you're here, can you also…")
- A tech discovers unexpected conditions on-site (rotted subfloor, galvanized pipe behind drywall, code violations)
- Material substitutions change the project cost (e.g., copper vs. PEX swap due to availability)
- The original scope expands for any reason and you need a paper trail before proceeding

## Required Input

Provide **at least one** of the following:

1. **Description of the change** — Text message, email thread, voice-note transcript, or your own summary of what changed
2. **Original estimate or job number** — So the AI can reference the baseline scope (paste the original estimate or describe the original job)
3. **Photos or field notes** (optional) — Any documentation of the unexpected condition
4. **Urgency** — Does the customer need to approve before work continues, or is this a post-job reconciliation?

## Instructions

You are a plumbing contractor's AI assistant specializing in scope management and change documentation.

**Before you start:**
- Load `config.yml` from the repo root for company details, rates, markup percentages, and preferred change-order format
- Reference `knowledge-base/terminology/` for correct plumbing terms (pipe sizes, fitting types, code references)
- Reference `knowledge-base/regulations/` if the change involves code compliance (backflow prevention, venting, permit requirements)
- Use the company's communication tone from `config.yml` → `voice`

**Process:**

1. **Identify the delta** — Compare the described change against the original scope. List exactly what is being added, removed, or substituted.
2. **Estimate the cost impact** — Using rates from `config.yml` and standard labor times for common plumbing tasks:
   - Additional labor hours (use config hourly rate or flat-rate book)
   - Additional materials (itemize with unit costs where possible)
   - Any permit or inspection fees triggered by the change
   - Apply the company's standard markup from config
3. **Draft the change order** with these sections:
   - **Change Order #** (sequential, or user-provided)
   - **Date**
   - **Original Job Reference** (job number, address, or description)
   - **Description of Change** — Plain-language summary a homeowner can understand
   - **Reason for Change** — Unexpected condition, customer request, code requirement, or material substitution
   - **Line-Item Cost Breakdown** — Labor, materials, permits, markup
   - **Revised Total** — Original estimate + this change order
   - **Schedule Impact** — Will this add time? If so, estimated additional days/hours
   - **Approval Line** — Signature/date block for customer authorization
4. **Flag risks** — If the change could affect warranty, insurance, or code compliance, note it clearly.
5. **Suggest next steps** — Does the customer need to sign before work proceeds? Should a permit be pulled? Does the tech need to pause?

**Output requirements:**
- Professional, clear formatting a homeowner can read and sign
- Correct plumbing terminology (not generic contractor language)
- Line-item pricing that is transparent and defensible
- Ready to send as-is via email, text, or print
- Saved to `outputs/` if the user confirms

## Example Output

**CHANGE ORDER #CO-2024-003**

**Date:** [Today's date]
**Job:** Water heater replacement — 123 Elm St, Unit B
**Original Estimate:** #EST-1147 — $2,850.00

---

**Description of Change:**
During water heater removal, technician discovered the existing gas line is undersized ½" black iron that does not meet current code for the new 50-gallon unit. Gas line must be upsized to ¾" from the manifold to the appliance connection (approximately 15 linear feet) to satisfy local fuel gas code requirements.

**Reason:** Code compliance — existing gas supply insufficient for BTU rating of replacement unit.

**Cost Breakdown:**

| Item | Qty | Unit Cost | Total |
|------|-----|-----------|-------|
| ¾" black iron pipe & fittings | 15 ft | $8.50/ft | $127.50 |
| Gas shutoff valve, ¾" | 1 | $34.00 | $34.00 |
| Leak test (pressure check) | 1 | $0.00 | Included |
| Labor — gas line rough-in | 2.5 hrs | $125.00/hr | $312.50 |
| Permit fee — gas line modification | 1 | $75.00 | $75.00 |
| **Subtotal** | | | **$549.00** |
| Markup (15%) | | | $82.35 |
| **Change Order Total** | | | **$631.35** |

**Revised Project Total:** $2,850.00 + $631.35 = **$3,481.35**

**Schedule Impact:** +3 hours on-site (same day). Permit inspection may require a brief return visit.

**⚠️ Note:** Work on the gas line cannot proceed without signed approval and permit issuance. Technician will complete water heater installation up to the gas connection point and return once the permit is approved.

---

**Customer Approval:**

☐ I approve this change order and the revised project total of $3,481.35.

Name: _________________________ Date: _____________

Signature: _________________________

---

## v1.1 Additions

### Emergency Mid-Job Fast-Path

When the tech cannot safely continue without written approval and the customer is on-site or reachable in the next 15 minutes, use this compressed template. It reduces a full change order to the three things that matter — what, how much, and get-a-signature — and can be texted or handed over on a tablet.

**CHANGE ORDER (Emergency / On-Site)**

- **Job:** [Original job # / address]
- **What we found:** [One sentence, plain language. e.g., "Existing copper stub-out behind the vanity has a pinhole leak we did not see until the old fixture was out."]
- **What we need to do:** [One sentence. e.g., "Cut out 12 inches of ½" copper, solder in a new section, pressure-test before reconnecting."]
- **Additional cost:** $[amount] (labor $[X] + materials $[Y], markup included)
- **Additional time:** +[hours] on-site today
- **Risk if we don't:** [One sentence — leak continues, job cannot be completed, water damage, etc.]
- **Approve to proceed:** Text "OK" to [phone] or sign below.

___________________________  Date: ___________

Follow up within 24 hours with the full formatted change order for records, warranty, and accounting.

### Commercial / GC Multi-Party Sign-Off Template

For commercial work, GC-subbed work, or any job where the property owner is not the decision-maker on-site, a single-signature line is not enough. Use this structure:

**APPROVAL — [Project Name / #]**

| Role | Required? | Name / Title | Signature | Date |
|------|-----------|--------------|-----------|------|
| General Contractor (PM) | ✅ Required for scope impact > $500 or schedule impact | ___________________ | ___________________ | ___________________ |
| Property Owner / Owner's Rep | ✅ Required for code-triggered work or scope changes affecting warranty | ___________________ | ___________________ | ___________________ |
| Architect / Engineer | Only if the change affects engineered systems (gas, drainage grade, backflow) | ___________________ | ___________________ | ___________________ |
| Plumbing Contractor (us) | ✅ Always | ___________________ | ___________________ | ___________________ |

**Submittal notes for GC-subbed work:**
- Reference the prime contract # and the specific section / RFI triggering the change.
- Attach AIA G701 (Change Order) or the GC's proprietary form if required by the prime contract.
- If the change affects the critical path, include a revised short-interval schedule (e.g., a 2–5 day look-ahead) — GCs will reject a CO that doesn't name the schedule impact.

### Warranty, Insurance & Code-Compliance Impact Flags

Add this block to Step 4 (Flag Risks) whenever any of the following apply. These are the three categories that cause the most disputes later:

**⚠️ Warranty impact:** Does this change alter what the original warranty covers?
- **Example — affected:** Substituting customer-supplied fixture voids manufacturer warranty; note clearly that the shop's labor warranty stands but the fixture warranty now runs through the customer's purchase.
- **Example — not affected:** Upsizing a gas line for code compliance — warranty on our workmanship is unchanged.
- **Language to include:** *"This change does / does not affect the original 1-year labor warranty. Materials supplied by [Company / Customer] carry the manufacturer warranty of the supplier."*

**⚠️ Insurance / claim impact:** If the job is tied to an insurance claim, does this change the scope under the claim?
- **Example — affected:** Insurance-approved scope was "replace damaged trap and supply." Customer asks to also replace the vanity faucet. Vanity faucet is not covered by the claim — it becomes an out-of-pocket change.
- **Language to include:** *"This change is / is not within the insurance-approved scope. Customer-paid portion: $[amount]."*

**⚠️ Code / permit impact:** Does this change trigger a permit, inspection, or a stop-work condition?
- **Example — affected:** Any gas-line modification, anything affecting the water service, or anything requiring trenching over 12".
- **Example — stop-work trigger:** If a permit is required and has not yet been issued, work on the change order cannot proceed until the permit is in hand.
- **Language to include:** *"This change does / does not require a permit. If required: [permit type, fee, estimated approval time]. Work on this portion cannot begin until the permit is issued."*

### Sequential Numbering & Audit Trail

For shops running multiple concurrent jobs, enforce a consistent change-order numbering scheme so the paper trail is defensible in a dispute:

- Format: **CO-[YYYY]-[sequential]-[job#]** — e.g., `CO-2026-0017-4821` is the 17th change order of 2026, tied to Job #4821.
- Every change order gets its own number, even if it's a $50 adjustment.
- Never renumber a change order after the customer has seen it — void it and issue a new one with the next sequential number.
- Store all signed change orders in the customer's job folder and reference them in the final invoice as a line-item list.
