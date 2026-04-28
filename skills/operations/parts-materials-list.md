---
name: "Parts & Materials List Generator"
category: operations
tools: [claude, chatgpt]
difficulty: beginner
time_saved: "~10 min/job"
version: 1.1
last_eval_score: 9.5
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

---

## v1.1 Additions (2026-04-26)

The v1.0 sections above are unchanged. The four sub-sections below are additive — they extend the skill rather than replace any prior content. Use them in addition to v1.0 when the trigger conditions named in each apply.

### v1.1.A — Same-Day Supply-House Fallback Hierarchy

When the truck-stock + primary supply-house run cannot satisfy the list before the job's start time, follow this fallback order. The point is to keep the tech moving rather than calling the office for permission to chase parts.

**Order of fallback (cheapest to most expensive per truck-hour):**

1. **Primary trade supply house** (Ferguson, Winsupply, Hajoca, F.W. Webb, Morrison Supply, Wesco — whichever is the shop's `config.yml` primary). Will-call counter; volume-discount account pricing.
2. **Secondary trade supply house** (the shop's #2 in `config.yml`). Same channel, slightly worse pricing, often closer for the cross-town job.
3. **Home Depot Pro / Lowe's Pro** (or equivalent retail). Pro Desk pricing if the shop has an account; full-margin retail otherwise. Use only when the trade counter cannot deliver inside the same-day window.
4. **Hardware-store / local plumbing-only outlet** (Ace, True Value, regional independent). Last-resort for one specific fitting; expect 1.5–2× pricing on items the shop normally pays trade-counter rates for.
5. **Manufacturer rep direct** (rare, but the right call for a high-end fixture or specialty part — Toto, Kohler Signature, Navien, Bradford White rep on the cell phone). 24–72 hr lead time; only use if the customer has agreed to wait.

**Cutoff-time discipline:**

- **Will-call cutoff (most trade counters):** 6:30 a.m. for same-day will-call pickup at most metro Ferguson / Winsupply branches; 7:00 a.m. at most regional Hajoca / Morrison branches; confirm in `config.yml`.
- **Last-call window for tech to start before 9 a.m. job:** Order placed by 6:00 a.m. = trade-counter pickup. Order needed after 7:00 a.m. = retail Pro Desk fallback.
- **After 4 p.m. for next-morning job:** Pre-pull on the trade counter for next-day will-call. Most counters hold a 24-hr will-call.
- **Saturday discipline:** Most trade counters are closed by 12:00 noon Saturday. After noon Saturday, retail Pro Desk is the only same-day channel until Monday 6:30 a.m.

**Output addition (when fallback is needed):**

Add a "Sourcing Plan" block to the Purchase Order Summary:
```
SOURCING PLAN
Primary:    [supplier] — [items] — pickup by [time]
Fallback A: [supplier] — [items if A] — pickup by [time]
Fallback B: [supplier] — [items if B] — pickup by [time]
Trigger:    [time] [outcome that flips A → B]
```

Example:
```
SOURCING PLAN
Primary:    Ferguson Will-Call (Highland) — Rheem G50-40N + flex kit — pickup 6:30 a.m.
Fallback A: Winsupply (Eastside) — same items — pickup 7:00 a.m. — if Ferguson stock-out
Fallback B: Home Depot Pro (Glenwood) — Rheem Performance 50-gal NG (sub-equivalent) — pickup 7:30 a.m. — only if both trade counters stock-out
Trigger:    6:00 a.m. confirmation call to Ferguson; if no, route to Winsupply by 6:15
```

### v1.1.B — Truck-Stock vs. Supply-House Split Rule

Most missed parts are not exotic — they are common items the tech assumed were on the truck and were not. The v1.1 rule below splits items by their canonical home so the materials list never asks the supply house for what should already be on board.

**Always-on-truck (rotate weekly to keep stocked, do not list on a supply-house run):**

- ½", ¾", 1" copper sweat fittings (couplings, 90° elbows, 45° elbows, tees, caps): minimum 6 of each per size
- ½", ¾", 1" PEX-A or PEX-B fittings + crimp/expansion rings: minimum 12 of each per size
- ½", ¾" galvanized + brass nipples (close, 2", 3", 4", 6"): 4 of each
- Plumber's putty, pipe dope (Rectorseal #5), Teflon tape (white + yellow gas-rated), wax rings (standard + extra-thick)
- 5-pack of stainless steel flex supply lines: ½" × 12", ½" × 16", ½" × 20", ¾" × 18" water heater connectors
- One earthquake-strap kit (in any seismic zone)
- One 2-gal expansion tank (jurisdictions that mandate)
- One spare T&P valve, one ¾" sweat ball valve, one ¾" CPVC ball valve
- Cleanup: drop cloths, boot covers, shop towels, contractor bags

**Always-supply-house (never load to truck, always pulled per-job):**

- Water heaters, garbage disposals, toilets, faucets (the unit itself; flex connectors and stop valves are truck stock)
- Whole-house repipe stock (long copper / PEX runs > 50 ft)
- Tankless heat exchangers, descaling pumps for tankless service
- Fixtures the customer is choosing (vanities, tubs, shower valves, kitchen faucets)
- Permits — the office pulls these, not the supply-house run

**Truck-stock check sub-output:**

When generating a parts list, the v1.1 skill explicitly tags each Must-Have row as either `[TRUCK]` or `[SUPPLY]`. The supply-house run only carries `[SUPPLY]` items plus any `[TRUCK]` items the tech reports as below minimum. Cuts the average supply-house pickup line by 4–7 SKUs per job.

Example sub-tag in the Must-Have table:
```
| Item | Spec | Qty | Source | Est. Cost |
| ¾" copper coupling | sweat | 4 | [TRUCK] | — |
| Rheem G50-40N | 50-gal NG WH | 1 | [SUPPLY] | $689.00 |
| Wax ring, extra-thick | for new flange height | 1 | [TRUCK] | — |
| Earthquake strap kit | code-required | 1 | [TRUCK if zoned] / [SUPPLY] | $15.00 |
```

### v1.1.C — Standardized Job-Code Templates (Ten Most Common)

Most plumbing shops run 70–80% of their volume through the same 8–12 job types. Pre-built templates for those types eliminate the parse-and-list step on the third water heater swap of the day. The v1.1 templates below are reference shapes — the skill still personalizes from `config.yml` (preferred brands, markup, supply houses), but the structure is locked.

**Template index (paste the code into the input and the skill produces the list):**

| Code | Job class | Avg list size | Avg cost band |
|---|---|---|---|
| `WH-SWAP-GAS-40` | 40-gal NG/LP atmospheric water heater swap | 14–18 items | $750–$1,150 |
| `WH-SWAP-GAS-50` | 50-gal NG/LP atmospheric water heater swap | 14–18 items | $850–$1,300 |
| `WH-SWAP-ELEC-50` | 50-gal electric water heater swap | 12–15 items | $700–$1,050 |
| `WH-SWAP-TANKLESS-NG` | Tank-to-tankless conversion, NG | 22–28 items | $2,400–$3,600 |
| `WH-FLUSH-TANKLESS` | Annual tankless service / descale | 6–8 items | $80–$140 |
| `MAIN-LINE-CLEAR-CABLE` | Main sewer line clear, cable | 4–6 items | $20–$60 |
| `MAIN-LINE-CLEAR-JET` | Main sewer line clear, hydro-jet | 8–12 items | $40–$110 |
| `TOILET-SWAP-STD` | Like-for-like toilet replacement | 8–10 items | $260–$520 |
| `FAUCET-SWAP-LAV` | Single-handle lavatory faucet swap | 6–8 items | $40–$90 (parts only) |
| `GARB-DISP-INSTALL` | New garbage disposal install / replacement | 8–10 items | $120–$280 |

Each template carries:
- Standard Must-Have / Should-Have / Good-to-Have allocation
- Truck-stock vs. supply-house tagging (see v1.1.B)
- Common code-required items for the job class (expansion tank, earthquake strap, sediment trap)
- Two-item "what to bring as backup" callout (the parts the tech wishes were on the truck the third time it happened)

**Template invocation:** Pass the code as input — e.g., `Code: WH-SWAP-GAS-50, Address: 789 Maple Dr, Existing tank: Bradford White 9 yrs, Vent: B-vent atmospheric, Notes: tight clearance` — and the skill produces a list pre-tuned to the template, then layers in the per-job specifics.

### v1.1.D — Returns Discipline and Restock Tagging

Over-pulling fittings is normal; it is not normal to lose money on returns. The v1.1 returns rule below makes the supply-house run reversible.

**Same-day return rules (most trade counters; verify in `config.yml`):**

- Unopened, in original packaging, with the original receipt: full credit, 30 days at most counters; 60 days at Ferguson with the account on file.
- Opened but unused (e.g., one fitting from a box of 25): partial credit at counter discretion; usually only on the unused units, not the partial.
- Cut-to-length copper / PEX: non-returnable once cut. Order the next-larger standard length and credit the remainder if returned in full.
- Special-order items (water heaters in specific configurations, tankless units with rep pricing): non-returnable once invoiced; the rep can sometimes intervene if the unit is unopened.
- Restocking fee threshold: most counters charge 15% on opened items; some charge 25% on opened-and-unused special order. Ferguson typically waives on the same-day swap-out (return + buy a substitute on the same ticket).

**Output addition: Returnable column.**

When the v1.1 skill outputs the Must-Have / Should-Have / Good-to-Have table, add a "Return?" column with one of: `YES (unopened)`, `NO (cut/special-order)`, `PARTIAL (counter discretion)`. The tech then knows at the end of the day which items can go back tomorrow morning vs. which to absorb into truck stock.

Example column addition:
```
| Item | Spec | Qty | Source | Est. Cost | Return? |
| ¾" Type L copper, 10 ft stick | sweat | 2 | [SUPPLY] | $58.00 | YES (unopened — keep banded) |
| Rheem G50-40N | 50-gal NG WH | 1 | [SUPPLY] | $689.00 | NO (special-order, but exchange OK) |
| Wax ring, extra-thick | for new flange height | 1 | [TRUCK] | — | YES |
```

**Returns log:**

At end-of-day, the tech (or the office) tallies a one-line return-log entry:
```
WO-4821 — 50-gal gas WH swap — Ferguson Highland — Returnable: 2x ¾" Type L 10ft stick ($116) — Returnable by: 2026-05-26 — Carrying: yes
```

Three-line discipline: cut returns line items the shop forgets about, often $40–$120 per job, often $1,500–$4,000/year.

---

**End of v1.1 additions. v1.0 example output above remains the canonical example. The v1.1 sub-sections layer on without modifying any v1.0 instruction or example.**
