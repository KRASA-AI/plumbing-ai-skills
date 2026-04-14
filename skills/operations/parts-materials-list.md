---
name: "Parts & Materials List Generator"
category: operations
tools: [claude, chatgpt]
difficulty: beginner
time_saved: "~10 min/job"
version: 1.0
last_eval_score: 9.3
---

# 🔧 Parts & Materials List Generator

## Purpose

Generate a complete parts and materials list for a plumbing job based on the job description, scope notes, or estimate. Prevents mid-job supply runs, ensures the truck is loaded correctly, and gives the office a purchase-order draft for the supply house.

## When to Use

- Before dispatching a tech to a job — generate the truck-stock checklist
- When writing an estimate — itemize the materials section accurately
- After a site visit or inspection — convert field notes into a shopping list
- For recurring job types (water heater swap, repipe, drain clean) — quickly pull a standard materials template and adjust

## Required Input

Provide **at least one** of the following:

1. **Job description or scope notes** — What work is being performed (e.g., "Replace 40-gal gas water heater at 456 Oak Ave, existing copper supply lines, standard B-vent")
2. **Estimate or work order** — Paste the existing estimate so the AI can extract the materials section
3. **Job type shorthand** — If your company uses standard job codes (e.g., "WH-SWAP-GAS-40", "REPIPE-WHOLE-PEX"), provide the code and the AI will generate the standard list
4. **Special conditions** (optional) — Crawlspace access, long runs, code-specific requirements, customer material preferences

## Instructions

You are a plumbing contractor's AI assistant specializing in materials management and job preparation.

**Before you start:**
- Load `config.yml` from the repo root for preferred suppliers, standard brands, markup rates, and truck-stock defaults
- Reference `knowledge-base/terminology/` for correct fitting names, pipe specifications, and sizing conventions
- Reference `knowledge-base/regulations/` for code-required items (expansion tanks, earthquake straps, disconnect switches, etc.) based on the company's service area
- Reference `knowledge-base/best-practices/` for recommended installation standards

**Process:**

1. **Parse the job scope** — Identify every task that requires materials. Break multi-task jobs into individual material groups (e.g., "water heater install" + "gas line extension" = two material groups).

2. **Generate the materials list** with these columns:
   - **Item** — Specific part name using industry terminology (not "pipe" — say "¾" Type L copper, 10 ft stick")
   - **Spec** — Size, material, pressure rating, or model number where applicable
   - **Qty** — Quantity needed, with 10% overage built in for fittings and consumables
   - **Unit** — Each, foot, box, roll, etc.
   - **Supplier SKU** (if configured in config.yml)
   - **Est. Cost** — Unit price if available from config or pricebook

3. **Add standard consumables** — Items techs commonly need but forget to load:
   - Teflon tape, pipe dope, flux, solder (for copper jobs)
   - PEX crimp rings or expansion fittings (for PEX jobs)
   - Copper stub-outs, escutcheons, supply lines
   - Drop cloths, boot covers, cleanup supplies
   - Appropriate hangers, straps, and supports

4. **Flag code-required items** — Based on the service area in config, add items mandated by local code:
   - Expansion tanks (where required on water heater installs)
   - Seismic strapping (earthquake zones)
   - Drain pans and overflow routing
   - Backflow prevention devices
   - Proper venting components

5. **Group the output** into:
   - **Must-have (job-critical)** — Job cannot be completed without these
   - **Should-have (standard practice)** — Professional install quality requires these
   - **Good-to-have (truck stock)** — Common extras the tech may need on-site

6. **Add a purchase order summary** — Total estimated materials cost, supplier name, and a one-line order note suitable for calling or texting to the supply house.

**Output requirements:**
- Clean table format, easy to print or screenshot for the supply house run
- Correct plumbing part names and specifications (no vague descriptions)
- Quantities that account for real-world waste and overage
- Code-required items clearly flagged
- Saved to `outputs/` if the user confirms

## Example Output

**PARTS LIST — Water Heater Replacement (Gas, 50-gal)**
**Job:** #WO-4821 — 789 Maple Dr
**Tech:** Mike R.

### Must-Have (Job-Critical)

| Item | Spec | Qty | Unit | Est. Cost |
|------|------|-----|------|-----------|
| Rheem 50-gal gas water heater | G50-40N, 40K BTU, .62 UEF | 1 | ea | $689.00 |
| Water heater connector, flex | ¾" × 18", stainless braided | 2 | ea | $12.50 |
| Gas connector, flex | ½" × 24", coated stainless | 1 | ea | $18.00 |
| Gas shutoff valve | ½" FIP, brass, lever handle | 1 | ea | $14.00 |
| T&P relief valve | ¾", 150 PSI / 210°F | 1 | ea | $11.00 |
| T&P discharge tube | ¾" copper, 6 ft | 1 | ea | $8.50 |
| Dielectric unions | ¾" MIP × copper sweat | 2 | ea | $9.00 |

### Should-Have (Standard Practice)

| Item | Spec | Qty | Unit | Est. Cost |
|------|------|-----|------|-----------|
| Expansion tank | 2-gal, ¾" connection | 1 | ea | $42.00 |
| Earthquake straps (if req.) | Water heater strap kit | 1 | kit | $15.00 |
| Drain pan, aluminum | 24" round | 1 | ea | $12.00 |
| Pipe insulation | ¾" × 6 ft, foam | 2 | ea | $3.50 |
| Thread sealant tape | ½" PTFE, yellow (gas-rated) | 1 | roll | $2.50 |
| Pipe dope | Rectorseal #5, gas-rated | 1 | tube | $6.00 |

### Good-to-Have (Truck Stock)

| Item | Spec | Qty | Unit | Est. Cost |
|------|------|-----|------|-----------|
| ¾" copper couplings | Sweat | 4 | ea | $1.25 |
| ¾" copper 90° elbows | Sweat | 4 | ea | $1.75 |
| Lead-free solder | 1 lb spool | 1 | ea | $12.00 |
| Flux | water-soluble, 4 oz | 1 | ea | $5.50 |
| Drop cloth | 4' × 12', canvas | 1 | ea | $8.00 |

---

**Purchase Order Summary**
- **Estimated materials total:** $908.25
- **Supplier:** [From config — e.g., Ferguson Plumbing Supply]
- **Order note:** "WO-4821 — 50-gal gas WH swap, need Rheem G50-40N + standard install kit. Pickup by 7 AM tomorrow."
