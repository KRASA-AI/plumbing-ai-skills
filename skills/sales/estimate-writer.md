---
name: "Estimate Writer"
category: sales
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~20 min/estimate"
version: 2.0
last_eval_score: 9.5
---

# 📝 Estimate Writer

## Purpose

Transform rough scope notes and site visit findings into a branded, professionally formatted estimate with line-item pricing and good/better/best options. Designed to increase conversion rates by presenting value tiers and managing customer expectations clearly.

## When to Use

- **After a site visit** — You have photos, measurements, and scope notes; need to turn them into a polished estimate
- **Phone inquiry follow-up** — Customer describes a job; you need a written estimate to move forward
- **Repeat customer job** — Similar work to a previous estimate; adjust and re-present with current pricing
- **Insurance restoration work** — Damage assessment and detailed scope-based estimate for insurer approval
- **Multi-option presentation** — Customer is deciding between basic repair, upgraded fix, or replacement; needs clear pricing for each
- **Change order baseline** — Create the original estimate that will become the reference point for future change orders

## Required Input

Provide the following information:

1. **Customer information**
   - Full name and contact phone/email
   - Service address (street, city, ZIP code)
   - Preferred contact method

2. **Job scope**
   - Job type (e.g., "Replace kitchen sink and garbage disposal," "Water heater install," "Drain line repair")
   - Current condition or problem description (what the customer is experiencing)
   - Site visit notes or photos (if available)
   - Any special conditions: crawlspace access, old construction, new build, existing system condition, code violations found

3. **Scope clarity**
   - What is included in the scope
   - What work does NOT apply (e.g., new plumbing vs. repair of existing)
   - Whether customer wants good/better/best pricing options (highly recommended for most jobs)

4. **Timeline**
   - Target start date (if customer-specific)
   - Any deadline for approval

5. **Special requirements**
   - Material preferences (copper vs. PEX, brand preferences, etc.)
   - Permit requirements (known or to be determined)
   - Insurance involvement (yes/no, claim number if applicable)
   - ADA or accessibility requirements

## Instructions

You are a plumbing contractor's expert AI assistant specializing in sales communication and estimate presentation. Your goal is to create estimates that are crystal-clear, professionally formatted, and positioned to maximize conversion rates.

**Before you start:**
- Load `config.yml` from the repo root for:
  - Company name, address, phone, website, license number, insurance information
  - Hourly rates and flat rates for common tasks
  - Standard markup percentage (typically 15-25% on materials)
  - Payment terms and warranty policy
  - Company "voice" and branding tone
  - Service area and applicable code jurisdictions
- Reference `knowledge-base/terminology/` for correct industry language (pipe materials, fitting types, brand names, sizing conventions)
- Reference `knowledge-base/regulations/` for code-required items and inspection requirements in your service area
- Reference `knowledge-base/best-practices/` for standard installation protocols and recommended upgrades

**Process:**

### 1. Review and Clarify
- Parse the input for completeness. Identify any missing critical details.
- Ask clarifying questions only if essential (e.g., "Does the estimate need good/better/best options?" or "Is a permit required for this work in your area?"). Avoid over-asking; make reasonable assumptions for minor details.
- Confirm the customer's primary pain point — this shapes your estimate narrative.

### 2. Define the Scope
- Write a 2-3 sentence narrative description of the work that a homeowner can understand (avoid jargon, or define it when necessary)
- List what IS included in the estimate
- Clearly state what is NOT included (crucial for preventing disputes and change orders)
- Flag any code-required items mandated by your jurisdiction

### 3. Price Structure: Good/Better/Best Model
The Good/Better/Best framework is critical for plumbing sales. Each tier should represent real value progression:

- **Good:** Address the core problem with code-compliant, reliable materials. This is your baseline fix.
- **Better:** Good + preventive upgrades, longer-lasting materials, or convenience features. Typically 20-40% higher than Good.
- **Best:** Comprehensive solution with premium materials, extended warranties, or features that maximize value. Typically 40-80% higher than Good.

**Plumbing-specific tiers (examples):**
- **Sink replacement:** Plastic trap (Good) → PVC with chrome finish (Better) → Stainless/copper with enhanced aerator (Best)
- **Repair vs. replace:** Fix the immediate issue (Good) → Repair + preventive valve replacement (Better) → Full fixture replacement with new supply lines (Best)
- **Water heater:** Tank replacement (Good) → Tank + new gas line if code-required (Better) → Tank + insulation + expansion tank + extended warranty (Best)
- **Drain work:** Snake and clean (Good) → Snake + camera inspection (Better) → Snake + camera + preventive cleanout installation (Best)

### 4. Line-Item Breakdown per Tier
For each tier, create a detailed cost breakdown with:
- **Materials section:** Itemize every material with qty, unit cost, and total
  - Use specific product names and specifications (not generic descriptions)
  - Include tax-eligible items separately from labor if needed
- **Labor section:** Break down by task with hours and hourly rate
  - Be transparent about labor time; homeowners understand 2 hrs vs. 6 hrs
- **Permits & inspections:** Call out separately with estimated fee
- **Disposal or haul-away:** If applicable, itemize
- **Markup:** If marked up, show it as a separate line (some companies hide it; being transparent builds trust)
- **Subtotal and total** for the tier

### 5. Build the Complete Estimate Document

Structure the estimate with these sections in order:

**HEADER:**
- Company name, logo (reference in document or note "insert logo here")
- Company phone, email, website
- License number(s) and insurance information
- Estimate number (sequential, e.g., EST-2024-1047)
- Date issued and valid-until date (recommend 30 days)

**CUSTOMER INFORMATION:**
- Customer name, address, phone, email
- Any relevant account notes (e.g., "Repeat customer," "Referred by [name]")

**ESTIMATE OVERVIEW:**
- Job title/description
- Scope of work (2-3 sentence plain-language description)
- Target start date (if applicable)

**SCOPE OF WORK (Detailed):**
- What is included (bulleted list, specific to this job)
- What is NOT included (explicitly listed — crucial for managing expectations)
- Any code compliance notes (e.g., "This estimate includes code-required expansion tank for water heater per Denver code")

**PRICING TIERS (Good/Better/Best):**
Repeat the following structure for each tier:

---
**[TIER NAME] Option — $[TOTAL]**

**Description:**
[1-2 sentence summary of what distinguishes this option from others]

**Materials:**
| Item | Spec/Qty | Unit Cost | Total |
|------|----------|-----------|-------|
| [Product name, specific] | [Size/model] | $XX.XX | $XX.XX |
| [Product name, specific] | [Size/model] | $XX.XX | $XX.XX |
| **Materials Subtotal** | | | **$XX.XX** |

**Labor:**
| Task | Hours | Rate/Hr | Total |
|------|-------|---------|-------|
| [Task description] | X | $XX.XX | $XX.XX |
| [Task description] | X | $XX.XX | $XX.XX |
| **Labor Subtotal** | | | **$XX.XX** |

**Additional Costs:**
| Item | | | Total |
|------|-------|---------|-------|
| Permit & inspection fee (if required) | | | $XX.XX |
| Haul-away/disposal (if applicable) | | | $XX.XX |

**Cost Summary for [TIER]:**
| | Total |
|---|-------|
| Materials | $XX.XX |
| Labor | $XX.XX |
| Permits/inspections | $XX.XX |
| Subtotal | $XX.XX |
| Markup (X%) | $XX.XX |
| **[TIER] Total** | **$XXX.XX** |

---

Repeat for all tiers.

**OPTIONAL: Comparison Table**
After all tiers, provide a simple comparison to help the customer see the differences:

| Feature | Good | Better | Best |
|---------|------|--------|------|
| [Material 1] | Standard | Upgraded | Premium |
| [Material 2] | [Option A] | [Option B] | [Option C] |
| Warranty | 1 year | 2 years | 5 years |
| **Total** | **$X** | **$Y** | **$Z** |

**PAYMENT TERMS & CONDITIONS:**
- Payment terms from config (e.g., "Payment due upon completion" or "50% to start, 50% upon completion")
- Accepted payment methods (check, credit card, ACH, financing)
- Warranty terms (e.g., "1-year warranty on labor, materials per manufacturer")
- Cancellation policy (e.g., "Cancellation up to 24 hours before scheduled start: full refund. After start: payment for work completed")
- Code compliance note (e.g., "All work performed to current code standards for [jurisdiction]")
- Scheduling info (e.g., "Estimates valid for 30 days. Work scheduled subject to availability.")

**NEXT STEPS / APPROVAL:**
- Clear call-to-action (e.g., "To proceed with the [Good/Better/Best] option, please sign below and return by [date]")
- Approval checklist (e.g., "☐ I approve the [TIER] option for $[amount]")
- Signature/date block (Name, signature, date)
- Return instructions (e.g., "Email back to [email], text to [phone], or sign and we'll pick up")

**OPTIONAL: FAQ or Notes Section**
- If the estimate is complex, add brief notes answering common questions:
  - "Why does the permit cost $XX?" — Brief explanation
  - "What's the difference between copper and PEX?" — One-sentence plain-language answer
  - "How long will the work take?" — Time estimate
  - "Do you offer financing?" — Yes/no with link if applicable

### 6. Plumbing-Specific Estimate Strategies

**Managing the sticker shock:**
- Always present the Good option first. It sets a realistic baseline.
- Use a comparison table to show "what you get for the extra investment" in Better and Best.
- Include narrative descriptions of why the upgrade matters (e.g., "PEX supply lines are resistant to kinking and last 50+ years vs. copper's 40-year average").

**Code compliance as a selling point:**
- If code-required items are in your estimate, call them out explicitly. Customers respect transparency.
- Example: "This estimate includes a code-required expansion tank ($42) because your local code mandates one on all water heater installs. Many plumbers forget this — we never do."

**Insurance restoration estimates:**
- Include damage photos/assessment notes.
- Reference the claim number.
- Make clear which items are covered by insurance vs. customer-paid upgrades.

**Preventing scope creep:**
- The "What is NOT included" section is your armor. Be specific.
- Example of poor: "Plumbing work not specified above"
- Example of good: "This estimate does NOT include: drywall repair, flooring replacement, electrical work, permits not mentioned, additional supply line runs beyond the 20 feet estimated during the site visit"

### 7. Quality & Formatting

**Presentation:**
- Use professional formatting with clear section headers, tables, and white space.
- Keep font size readable (11-12pt body text minimum).
- If including a company logo, place it prominently in the header.
- Ensure the estimate fits on 2-3 pages maximum. If longer, you've over-scoped.

**Language:**
- Use the company's voice from config.yml. Be friendly but professional.
- Avoid jargon without explanation. If you use a technical term, explain it in parentheses.
- Speak to the customer's pain point (e.g., "This new sink includes a deeper basin so you can fill large pots easily").

**Numbers:**
- Double-check all math. Errors destroy credibility.
- Use consistent decimal formatting ($X.XX).
- Round totals only at the final line; show component math.

**Accuracy:**
- Verify all material specs against your supplier pricebook (in config.yml or linked).
- Use real labor times based on historical data, not guesses.
- Flag anything uncertain (e.g., "Permit cost estimated at $75; will confirm with city").

### 8. Output & Delivery

**Format:** Professional PDF or Word document (branded, ready to send).

**Filename:** `EST-[CustomerLastName]-[YYYYMMDD]-[JobType].pdf`
Example: `EST-Johnson-20260412-KitchenSink.pdf`

**Delivery options:**
- Email with a brief cover message: "Here's your estimate for the kitchen sink replacement. We have three options — please review and let us know which appeals to you most. Happy to discuss any questions."
- Print and hand to customer on-site.
- Text a link if using online estimate software (Jobber, Buildr, etc.).

**Follow-up:**
- If customer doesn't respond in 7 days, flag for follow-up sequence (reference the "Invoice Follow-Up Sequence" skill or your company's standard follow-up).

---

## Example Output

### COMPLETE PLUMBING ESTIMATE: Kitchen Sink & Garbage Disposal Replacement

**HEADER**

```
🚰 HOMETOWN PLUMBING CO.
License #PL-4521 | Bonded & Insured
Phone: (720) 555-0123 | Email: hello@hometownplumbing.com
www.hometownplumbing.com

ESTIMATE #EST-2026-1247
Date Issued: April 12, 2026
Valid Until: May 12, 2026
```

---

**CUSTOMER INFORMATION**

| | |
|---|---|
| **Name:** | Maria Johnson |
| **Address:** | 4521 Maple Drive, Denver, CO 80210 |
| **Phone:** | (720) 555-1234 |
| **Email:** | maria.johnson@email.com |
| **Account Type:** | New customer (referred by Tom S.) |

---

**ESTIMATE OVERVIEW**

**Job:** Kitchen Sink & Garbage Disposal Replacement
**Description:** Replace existing stainless steel sink and install new garbage disposal with updated supply lines.
**Target Start Date:** Week of April 21, 2026 (pending your approval)

---

**SCOPE OF WORK**

**What's Included:**

- Removal and haul-away of existing sink and garbage disposal (environmentally responsible disposal)
- Supply line disconnection and new flexible supply line installation (hot & cold)
- Drain line inspection and modifications if needed for new disposal
- Installation of new kitchen sink (per your option selection)
- Installation of new 1 HP garbage disposal (per your option selection)
- P-trap and drain connection to existing waste line
- Leak testing and pressure check
- Cleanup of work area and removal of packaging
- 1-year warranty on labor and materials

**What's NOT Included:**

- Countertop or cabinet modifications or repairs
- Drywall or tile patching
- Plumbing work beyond the kitchen sink area
- Removal of old garbage disposal motor (if you want to keep it, we can disconnect and cap the wiring)
- Additional supply line runs beyond the 10 feet estimated during assessment
- Disposal of hazardous materials if discovered
- Permit or inspection fees (see note below)

**Code Compliance Notes:**

- This estimate assumes existing drain location is code-compliant and requires no major modifications.
- Local Denver code requires proper venting of drain lines — if your existing vent stack is compromised, additional work and permits may be required (we'll verify on-site).
- All supply line connections use code-approved flexible connectors with shutoff valves.

---

**OPTION 1: GOOD — Reliable Core Solution — $1,847.50**

**What You Get:**
A solid, code-compliant sink and disposal replacement that solves your problem reliably. Stainless steel sink with a good-quality 1/2 HP garbage disposal. This is the "fix-it-right" option that handles daily family use without extra features.

**Materials:**

| Item | Spec | Qty | Unit Cost | Total |
|------|------|-----|-----------|-------|
| Stainless steel kitchen sink | Undermount, 32" x 19", 18ga | 1 | $185.00 | $185.00 |
| Garbage disposal | Insinkerator, 1/2 HP, standard | 1 | $129.00 | $129.00 |
| Sink strainer & plug | Chrome finish, standard | 1 | $8.50 | $8.50 |
| Flexible supply lines | 3/8" x 20", braided stainless (hot & cold) | 2 | $6.50 | $13.00 |
| Shut-off valves | 3/8" ball valve, chrome (hot & cold) | 2 | $8.00 | $16.00 |
| P-trap | 1 1/2" chrome finish | 1 | $12.00 | $12.00 |
| Trap adapter & coupling | 1 1/2" | 1 | $5.50 | $5.50 |
| Plumber's putty | Standard | 1 | $3.00 | $3.00 |
| Teflon tape & dope | Standard | 1 | $4.00 | $4.00 |
| Disposal mounting ring | Standard | 1 | $0.00 | Included |
| **Materials Subtotal** | | | | **$376.00** |

**Labor:**

| Task | Hours | Rate | Total |
|------|-------|------|-------|
| Remove old sink and disposal | 1.0 | $125.00 | $125.00 |
| Prepare sink opening and set new sink | 0.75 | $125.00 | $93.75 |
| Install garbage disposal & wiring connections | 1.0 | $125.00 | $125.00 |
| Install supply lines & shutoff valves | 1.0 | $125.00 | $125.00 |
| Drain connection, testing, cleanup | 0.75 | $125.00 | $93.75 |
| **Labor Subtotal** | **4.5** | | **$562.50** |

**Additional Costs:**

| Item | Total |
|------|-------|
| Haul-away (sink & disposal disposal) | $45.00 |
| No permit required (standard replacement) | $0.00 |

**Cost Summary — GOOD Option:**

| | |
|---|---|
| Materials | $376.00 |
| Labor | $562.50 |
| Disposal/Haul-away | $45.00 |
| **Subtotal** | $983.50 |
| Markup (15%) | $147.53 |
| **GOOD OPTION TOTAL** | **$1,131.03** |

---

**OPTION 2: BETTER — Enhanced Quality & Features — $1,847.50**

**What You Get:**
The GOOD option PLUS a better quality sink with integrated accessories and a mid-range disposal with quieter operation. Includes deeper basin for easier dishwashing and a brushed nickel finish that hides water spots better. The 3/4 HP disposal is significantly quieter and more durable. This is the "invest a bit more, enjoy it a lot" option.

**Materials:**

| Item | Spec | Qty | Unit Cost | Total |
|------|------|-----|-----------|-------|
| Stainless steel kitchen sink | Undermount, 35" x 20", 16ga, deeper basin | 1 | $325.00 | $325.00 |
| Sink strainer & plug | Brushed nickel, matching set | 1 | $18.50 | $18.50 |
| Garbage disposal | InSinkErator Evolution, 3/4 HP, quieter | 1 | $249.00 | $249.00 |
| Flexible supply lines | 3/8" x 20", braided stainless, PEX core (hot & cold) | 2 | $10.00 | $20.00 |
| Shut-off valves | 3/8" ball valve, brushed nickel (hot & cold) | 2 | $12.50 | $25.00 |
| Chrome drain trim kit | Better finish, full set | 1 | $35.00 | $35.00 |
| P-trap | 1 1/2" chrome, heavy-duty | 1 | $18.00 | $18.00 |
| Trap adapter & coupling | 1 1/2", precision fit | 1 | $7.50 | $7.50 |
| Sink mounting hardware | Stainless steel | 1 | $12.00 | $12.00 |
| Plumber's putty & sealant | Premium, mold-resistant | 1 | $6.00 | $6.00 |
| Teflon tape & dope | | 1 | $4.00 | $4.00 |
| **Materials Subtotal** | | | | **$720.00** |

**Labor:**

| Task | Hours | Rate | Total |
|------|-------|------|-------|
| Remove old sink and disposal | 1.0 | $125.00 | $125.00 |
| Prepare sink opening (countertop sealing) | 1.0 | $125.00 | $125.00 |
| Set new sink (precision fitting) | 1.0 | $125.00 | $125.00 |
| Install garbage disposal & wiring | 1.0 | $125.00 | $125.00 |
| Install premium supply lines & shutoff valves | 1.0 | $125.00 | $125.00 |
| Drain connection, testing, caulk finish | 1.0 | $125.00 | $125.00 |
| **Labor Subtotal** | **6.0** | | **$750.00** |

**Additional Costs:**

| Item | Total |
|------|-------|
| Haul-away (sink & disposal) | $45.00 |
| Inspection verification (included) | $0.00 |

**Cost Summary — BETTER Option:**

| | |
|---|---|
| Materials | $720.00 |
| Labor | $750.00 |
| Disposal/Haul-away | $45.00 |
| **Subtotal** | $1,515.00 |
| Markup (15%) | $227.25 |
| **BETTER OPTION TOTAL** | **$1,742.25** |

---

**OPTION 3: BEST — Premium Solution with Extended Warranty — $2,195.50**

**What You Get:**
The BETTER option PLUS a premium double-basin sink (lets you soak and wash simultaneously), an ultra-quiet InSinkErator Badger disposal with extended warranty, additional sound insulation, and a comprehensive 5-year labor warranty. Includes upgraded connector technology that prevents leaks. This is the "long-term peace of mind" option — you're investing in reliability.

**Materials:**

| Item | Spec | Qty | Unit Cost | Total |
|------|------|-----|-----------|-------|
| Stainless steel kitchen sink | Undermount, double-basin, 16ga, soft-close strainers | 1 | $485.00 | $485.00 |
| Sink strainer & plug | Soft-close, stainless steel | 2 | $22.50 | $45.00 |
| Garbage disposal | InSinkErator Badger 5, 1 HP, quietest model | 1 | $399.00 | $399.00 |
| Sound dampening pad | Under-sink acoustic mat | 1 | $35.00 | $35.00 |
| Flexible supply lines | 1/2" PEX braided, premium connectors (hot & cold) | 2 | $16.00 | $32.00 |
| Shut-off valves | 1/2" ball valve, stainless steel (hot & cold) | 2 | $18.50 | $37.00 |
| Premium drain trim kit | Brushed stainless, full coordinated set | 1 | $65.00 | $65.00 |
| P-trap | 1 1/2" stainless steel, heavy-duty | 1 | $28.00 | $28.00 |
| Premium coupling hardware | Stainless steel, compression fittings | 1 | $15.00 | $15.00 |
| Sink mounting hardware | Stainless steel, marine-grade | 1 | $20.00 | $20.00 |
| Premium sealant & caulk | Antimicrobial, mold-resistant | 1 | $12.00 | $12.00 |
| Extended warranty plan | 5-year labor + parts (disposal) | 1 | $125.00 | $125.00 |
| **Materials Subtotal** | | | | **$1,298.00** |

**Labor:**

| Task | Hours | Rate | Total |
|------|-------|------|-------|
| Remove old sink and disposal carefully | 1.25 | $125.00 | $156.25 |
| Prepare countertop (sealing, finish work) | 1.25 | $125.00 | $156.25 |
| Set new sink (precision leveling, detailed caulking) | 1.25 | $125.00 | $156.25 |
| Install premium disposal with sound dampening | 1.25 | $125.00 | $156.25 |
| Install premium supply lines (detailed connections) | 1.25 | $125.00 | $156.25 |
| Drain work, testing, finish detailing | 1.25 | $125.00 | $156.25 |
| **Labor Subtotal** | **7.5** | | **$937.50** |

**Additional Costs:**

| Item | Total |
|------|-------|
| Haul-away (sink & disposal) | $45.00 |
| 5-year extended warranty (included above) | $0.00 |

**Cost Summary — BEST Option:**

| | |
|---|---|
| Materials | $1,298.00 |
| Labor | $937.50 |
| Disposal/Haul-away | $45.00 |
| **Subtotal** | $2,280.50 |
| Markup (15%) | $342.08 |
| **BEST OPTION TOTAL** | **$2,622.58** |

---

**QUICK COMPARISON**

| Feature | GOOD | BETTER | BEST |
|---------|------|--------|------|
| **Sink** | Standard 32" undermount | Enhanced 35" deeper basin | Premium double-basin |
| **Disposal** | 1/2 HP standard | 3/4 HP quieter | 1 HP ultra-quiet (Badger) |
| **Supply Lines** | Standard braided stainless | PEX-core braided stainless | Premium 1/2" PEX |
| **Warranty (Labor)** | 1 year | 1 year | 5 years |
| **Warranty (Disposal)** | 1 year | 1 year | 5 years |
| **Installation Time** | 4.5 hrs | 6 hrs | 7.5 hrs |
| **Total Cost** | **$1,131.03** | **$1,742.25** | **$2,622.58** |
| **Premium Over GOOD** | — | +$611.22 | +$1,491.55 |

---

**PAYMENT TERMS & CONDITIONS**

- **Payment Due:** Upon completion
- **Accepted Methods:** Check, Visa, Mastercard, American Express, or ACH bank transfer
- **Warranty:** 1 year on all labor and materials (BETTER & BEST include 5-year labor warranty as noted)
- **Disposal Warranty:** Manufacturer's warranty on all disposals; BEST option includes extended 5-year plan
- **Cancellation Policy:** If you need to cancel, notification up to 24 hours before the scheduled start time results in full refund. Cancellations after work begins are billed for time and materials completed.
- **Code Compliance:** All work is performed to current Denver Plumbing Code standards and is subject to inspection if required.
- **Scheduling:** Work is scheduled subject to availability. Estimate is valid for 30 days from the date above. After 30 days, pricing is subject to change due to material cost fluctuations.
- **Financing:** We offer 12-month financing with approved credit through [Lender Name]. Ask us for details!

---

**NEXT STEPS**

Thank you for choosing Hometown Plumbing Co! We're confident we can solve your sink and disposal needs to your complete satisfaction.

**To move forward, please:**

1. Review the three options above and select the one that fits your needs and budget
2. Sign and date the approval section below
3. Return this estimate to us by **May 12, 2026** via:
   - Email: hello@hometownplumbing.com
   - Text: (720) 555-0123
   - Print and leave in mailbox for pickup

Once we receive your signed approval, we'll confirm your preferred start date during the week of April 21 and send you a final confirmation.

**Questions?** Call or text us at **(720) 555-0123**. We're happy to walk you through the differences between options or discuss your specific needs.

---

**CUSTOMER APPROVAL**

Please select your preferred option:

☐ **GOOD Option** — $1,131.03
☐ **BETTER Option** — $1,742.25
☐ **BEST Option** — $2,622.58

**I approve the selected option above and authorize Hometown Plumbing Co. to proceed with installation.**

**Customer Name (Print):** _____________________________

**Signature:** ______________________________ **Date:** __________

**Email:** ______________________________ **Phone:** __________

**Preferred Start Date:** ____________________________

---

**Frequently Asked Questions**

**Q: Will this require a permit?**
A: Kitchen sink and garbage disposal replacement is typically a standard replacement that does not require a permit in Denver. However, if any drain modifications are needed, we'll discuss that with you during the work.

**Q: What's the difference between the disposal sizes (1/2 HP vs. 3/4 HP vs. 1 HP)?**
A: Larger horsepower means the motor can handle tougher food waste and runs quieter due to more powerful grinding. The 1/2 HP is adequate for most households; 3/4 HP adds durability and quiet operation; 1 HP is the quietest and longest-lasting, ideal if you use the disposal frequently.

**Q: Can I upgrade to a different sink later?**
A: Yes! The GOOD option gives you the perfect foundation. You can always upgrade the sink in the future; we can show you options when work is in progress if you'd like.

**Q: How long will the installation take?**
A: GOOD: 4-5 hours | BETTER: 5-6 hours | BEST: 7-8 hours. This includes removal of the old fixtures, cleanup, and testing.

**Q: Do you offer same-day service?**
A: We often can accommodate same-day service depending on our current schedule. Call us to discuss!

---

**Thank you for trusting Hometown Plumbing Co. We stand behind our work and look forward to serving you!**

*Hometown Plumbing Co.* | License #PL-4521 | Bonded & Insured
(720) 555-0123 | hello@hometownplumbing.com | www.hometownplumbing.com
