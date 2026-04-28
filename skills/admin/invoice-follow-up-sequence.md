---
name: "Invoice Follow-Up Sequence"
category: admin
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~15 min/sequence"
version: 2.3
last_eval_score: 9.4
---

# 💰 Invoice Follow-Up Sequence

## Purpose

Draft a professional 3-touch follow-up sequence for unpaid invoices — friendly reminder, firm escalation, then final notice — tailored to plumbing-specific scenarios and payment friction points. Recovers cash faster while preserving customer relationships.

## When to Use

- **Day 7 overdue:** Customer likely forgot or payment got lost in the mail — friendly tone, assume good intent
- **Day 14 overdue:** No response to first touch — escalate professionally, reference payment terms, set clear deadline
- **Day 30+ overdue:** Final attempt before collections — formal notice, mention legal remedies (lien rights, collections agency), preserve relationship for future work
- **Warranty disputes:** Customer claims the work was faulty and refuses to pay — acknowledge concern, reference warranty policy from config, offer resolution path
- **"I paid the tech cash" scenarios:** Customer claims payment was made but invoice still outstanding — verify with field team, reconcile discrepancy, adjust if needed
- **Partial payments on multi-phase jobs:** Customer paid for Phase 1 but Phase 2 invoice is pending — reference scope breakdown, clarify remaining balance and next phase timeline
- **Disputed scope:** Customer disputes invoice amount or claims work wasn't completed as promised — review change orders and original estimate, offer walkthrough/inspection, provide itemized breakdown

## Required Input

Provide **all of the following** for best results:

1. **Invoice details:**
   - Invoice number (e.g., INV-2026-1847)
   - Invoice total amount
   - Date invoice was sent
   - Number of days overdue (or reference date to calculate from)

2. **Customer information:**
   - Customer name (first and last)
   - Customer email address
   - Customer phone number (for text versions)

3. **Job details:**
   - Job/work order number
   - Brief description of the work (e.g., "water heater replacement," "emergency burst pipe repair," "bathroom remodel – Phase 1")
   - Job address (city/state at minimum)
   - Date work was completed

4. **Payment context:**
   - Accepted payment methods (e.g., check, credit card, ACH transfer, Venmo)
   - Payment link or portal URL (if applicable)
   - Outstanding balance amount (may differ from invoice if partial payment received)
   - Any known payment friction (e.g., warranty dispute, payment method bounced, customer claim of prior payment)

5. **Company details** (if not in config.yml):
   - Company name
   - Contact phone number
   - Email address
   - Physical address (optional but recommended for final touch)

## Instructions

You are a plumbing contractor's AI assistant specializing in accounts receivable and relationship management.

**Before you start:**
- Load `config.yml` from the repo root for:
  - Company name, branding, phone, address
  - Standard payment terms (e.g., "Net 15" or "Due on completion")
  - Late fee policy (if applicable — e.g., 1.5% monthly interest after 30 days)
  - Communication voice/tone (professional, friendly, firm, formal, etc.)
  - Legal remedies available in your jurisdiction (mechanic's lien, collections agency, small claims threshold)
- Reference `knowledge-base/terminology/` for plumbing-specific terms to use when describing scope
- Reference `knowledge-base/best-practices/` for industry norms on payment disputes and warranty claims
- Reference `knowledge-base/regulations/` for lien law and payment rights in your state/jurisdiction (critical for final notice)

**Process:**

### 1. Validate the Input

Review the provided details. If critical information is missing (invoice number, customer name, amount, days overdue), ask clarifying questions. Do not proceed without at least invoice amount, days overdue, and customer contact info.

### 2. Assess the Scenario & Set Tone Progression

Determine which scenario applies and set the appropriate tone trajectory:

- **Standard overdue (no dispute):** Friendly → Professional/Firm → Formal/Legal
- **Warranty dispute:** Empathetic → Solution-focused → Formal with resolution offer
- **Cash payment claim:** Apologetic/collaborative → Investigate → Formal once verified
- **Partial payment context:** Clarifying → Motivating → Compelling

### 3. Draft Touch 1 (Friendly Reminder — Day 7 Overdue)

**Assumes:** Payment may have been overlooked, lost in transit, or customer simply forgot.

**Tone:** Warm, helpful, no pressure. Make payment as frictionless as possible.

**Email Structure:**
- **Subject line:** Friendly, mentions invoice number for easy reference
  - Example: "Quick follow-up on Invoice #INV-2026-1847 — Water Heater Replacement"
  - Avoid: "PAST DUE," "URGENT," or aggressive language
- **Opening:** Thank customer for the work, assume good intent
  - "Thanks for choosing [Company Name] for your water heater installation! We wanted to check in..."
- **Body:**
  - Reference the job briefly (what was done, when it was completed)
  - State the invoice amount clearly
  - Provide easy payment options with a direct link if possible
  - Include payment instructions (where to mail check, how to pay online, etc.)
  - Optional: mention that no action is needed if payment is already in transit
- **Closing:** Light, professional sign-off
  - "Please let us know if you have any questions — we're here to help!"
  - No guilt or pressure language

**Text Message Option (if phone provided):**
- Keep under 160 characters or break into 2 messages
- Example: "Hi [Name], this is [Company Name]. Just checking in on INV-2026-1847 ($X,XXX) from your water heater install on [date]. Reply with any questions or visit [link] to pay. Thanks!"

**Key points to include:**
- Invoice number (for their reference)
- Invoice amount
- Brief description of completed work
- At least one easy payment method
- Direct contact info (email or phone to ask questions)

---

### 4. Draft Touch 2 (Professional Escalation — Day 14 Overdue)

**Assumes:** Customer received first notice; this is a gentle but clear escalation. Something may be genuinely wrong (disputed amount, service concern, financial hardship).

**Tone:** Professional, concerned, but firm. Acknowledge they may have a reason for not paying. Open door for dialogue while setting a deadline.

**Email Structure:**
- **Subject line:** More direct but still professional
  - Example: "Action needed: Invoice #INV-2026-1847 now 14 days overdue"
  - Avoid: "FINAL NOTICE" (save that for Touch 3)
- **Opening:** Reference the previous message without being condescending
  - "We sent a courtesy reminder about this invoice two weeks ago and haven't heard back. We want to make sure everything is okay..."
- **Body:**
  - Restate invoice number, amount, and job description
  - Explicitly reference the payment terms from config (e.g., "Our terms are Net 15, due by [specific date]")
  - Provide the same payment options as Touch 1
  - **Key addition:** Acknowledge that there may be an issue
    - "If there's a problem with the work, a billing error, or if you have questions, please reach out directly so we can resolve it."
    - "If payment was sent, please disregard this notice and let us know so we can update our records."
  - **Clear deadline:** "We need to hear from you or receive payment by [date 5–7 days out]."
  - Optional: mention late fee if applicable
    - "Please note our standard payment terms include a [X%] monthly interest charge on balances over 30 days."
- **Closing:** Professional but warmer than a bill collector
  - "We value you as a customer and want to resolve this quickly. Please respond or pay today."

**Text Message Option:**
- Example: "Hi [Name], following up on INV-2026-1847 ($X,XXX) due [original date]. Payment needed by [deadline]. Reply or call [phone] if there's an issue. Thanks, [Company Name]"

**Plumbing-specific additions (if applicable):**
- **Warranty question:** "If you have concerns about the quality of the work, please let us know — we stand behind our warranty (reference warranty period from config). We're happy to inspect or adjust."
- **Scope dispute:** "If the invoice amount seems high or you believe the scope changed, we can review the work order and original estimate together."
- **Cash payment claim:** "We also want to verify: Did you pay our technician cash on-site? If so, please send us a photo of your receipt and we'll update our records immediately."

---

### 5. Draft Touch 3 (Final Notice — Day 30+ Overdue)

**Assumes:** This is the last friendly attempt before escalating to collections, liens, or legal action. Tone is firm, formal, and professional — but still preserves the door for resolution.

**Tone:** Formal, professional, serious. This is a legal/business notice. Reference applicable laws in your jurisdiction.

**Email Structure:**
- **Subject line:** Formal and direct
  - Example: "FINAL NOTICE — Invoice #INV-2026-1847 Payment Required by [date]"
- **Opening:** State the situation plainly
  - "This is our final notice regarding Invoice #INV-2026-1847 for $[amount], which is now [X] days overdue."
- **Body:**
  - Restate all invoice details: number, amount, job description, original due date, current status
  - Reference the payment terms one final time
  - State that previous payment requests have gone unaddressed
  - **Legal/remedies language (customize per jurisdiction):**
    - For states with mechanic's lien laws: "If payment is not received by [date], we may file a mechanic's lien against the property at [address] as permitted under [State] law."
    - For all jurisdictions: "This account is subject to collection action, which may affect your credit rating."
    - General fallback: "If we do not receive payment or hear from you by [date], we will pursue all available legal remedies and may refer this account to a collections agency."
  - **Final opportunity for dialogue:**
    - "If there is a legitimate issue with the work, a billing error, or a hardship situation, please contact us immediately. We are willing to work with you, but we need communication."
  - **Clear, final deadline:** "Payment in full (or contact us) required by [specific date — typically 7–10 days out]."
  - **Payment instructions:** Reiterate all payment methods one last time
- **Closing:** Professional, no emotional language
  - "Please treat this matter with urgency. We look forward to resolving this with you directly."

**Text Message Option (if applicable):**
- Example: "FINAL NOTICE: INV-2026-1847 ($X,XXX) now 30+ days overdue. Payment or contact required by [date]. Continued non-payment may result in lien filing or collections action. Reply [phone] or email [email]."

**Critical legal additions:**
- Research and reference the specific lien law / collection process for your state/jurisdiction
- Include a deadline that gives the customer reasonable time to respond (7–10 days minimum)
- Make it clear this is the final notice before formal legal action
- Do NOT threaten actions you cannot legally take (know your jurisdiction)

---

### 6. Plumbing-Specific Scenario Handling

**Scenario A: Warranty Dispute (Customer claims work was faulty)**

- **Touch 1:** Acknowledge the concern, emphasize your warranty commitment
  - "We stand behind all our work with [X-year] warranty. If something isn't working as expected, let's fix it."
- **Touch 2:** Offer to inspect, reference warranty policy from config
  - "We'd like to send a technician to review the installation and address your concerns at no cost."
  - "Our warranty covers [specific list from config]. Please tell us what's not working so we can schedule a visit."
- **Touch 3:** Reframe as relationship issue, not just money
  - "We value our reputation and want to make this right. However, we need communication. Please contact us by [date] or we will pursue collection of the outstanding balance."

**Scenario B: "I Paid the Tech Cash" Claim**

- **Touch 1:** No reference to this — if customer mentions it, note it for Touch 2
- **Touch 2:** Acknowledge and investigate
  - "We appreciate you noting that you may have paid our technician in cash. We need to verify this with our team to update your account. Can you send us a photo of your receipt or confirm the date/tech name?"
  - Set deadline for verification (3–5 days)
- **Touch 3:** If verification shows cash payment, apologize and close invoice. If unverified, proceed with standard final notice language.

**Scenario C: Partial Payment on Multi-Phase Job**

- **Touch 1:** Clarify the situation
  - "Thank you for paying Phase 1 ($X) on [date]. This invoice is for Phase 2 work completed on [date]."
  - "Here's the schedule: Phase 2 is due [date], Phase 3 follows on [date]."
- **Touch 2:** Motivate Phase 2 payment by connecting to Phase 3
  - "Paying Phase 2 by [date] allows us to schedule Phase 3 for [date]. Contact us if you'd like to adjust the timeline."
- **Touch 3:** Final notice emphasizes contract terms
  - "Phase 2 payment ($X) is now 30+ days overdue. We cannot proceed with Phase 3 until this is settled. Final payment deadline: [date]."

**Scenario D: Disputed Scope or Amount**

- **Touch 1:** Invite dialogue
  - "If you have questions about the invoice or the work performed, we'd love to discuss it. Please reply with your concerns."
- **Touch 2:** Offer detailed breakdown and walkthrough
  - "We're attaching an itemized breakdown showing labor, materials, and markup. If you'd like us to review the work on-site, we can schedule a walkthrough."
  - Reference the original estimate or change orders that were approved
- **Touch 3:** Formal, but reference the resolution offer
  - "We have made multiple attempts to resolve this dispute. If you believe the invoice is incorrect, please provide specific documentation by [date]. Otherwise, payment is due in full."

---

### 7. Output Assembly

For each touch, generate:

1. **Email version** — Full, ready-to-send email with subject line
2. **Text version** — Condensed message for SMS/phone contact (if phone provided)
3. **Timing note** — When to send (Day 7, Day 14, Day 30, etc.)
4. **Key variables** — Highlight fields the user should customize (customer name, company name, phone/email, payment link, legal deadline)

**Output requirements:**
- Professional formatting, proper grammar, no typos
- All contact info included (phone, email, payment portal)
- Correct plumbing terminology if referencing specific work
- Customizable template — clearly mark [BRACKETS] for variables the user must fill in
- Tone progression is clear and appropriate
- Compliance with applicable lien/collection laws (reference the jurisdiction)
- Ready to send with minimal editing
- Saved to `outputs/` if the user confirms

---

## Example Output

**SCENARIO:** Water heater installation, $2,850 invoice, customer in California, 7 days overdue, no prior response, standard payment terms Net 15, company accepts check/credit card/ACH.

---

### TOUCH 1 — FRIENDLY REMINDER (Day 7)

**Timing:** Send 5–7 days after invoice date

**Email:**

**Subject:** Quick follow-up on Invoice #INV-2026-1847 — Water Heater Replacement

Dear Sarah,

Thank you for choosing **Reliable Plumbing** for your water heater replacement! We hope the new unit is working beautifully.

We're reaching out because we haven't received payment for **Invoice #INV-2026-1847** ($2,850.00), which was sent on April 5th. The work was completed on April 5th at **789 Maple Drive, Anytown**.

**No action needed if payment is already on its way!** However, if you haven't sent it yet, here are the easiest ways to pay:

- **Credit/Debit Card:** Visit our payment portal at [link] (no fees)
- **Bank Transfer (ACH):** Reply to this email and we'll send our banking details
- **Check:** Mail to Reliable Plumbing, 123 Main St, Anytown, CA 90210
- **Phone:** Call us at (555) 123-4567 to pay by phone

If you have any questions about the invoice or the work, we're happy to help. Just reply here or give us a call.

Thanks so much!

**Reliable Plumbing**
(555) 123-4567
support@reliableplumbing.com
Hours: Mon–Fri 8 AM–5 PM

---

**Text Message Option:**

Hi Sarah, thanks for choosing Reliable Plumbing! Just checking in on invoice INV-2026-1847 ($2,850) from your water heater install on 4/5. Pay here [link] or call (555) 123-4567. Thanks!

---

### TOUCH 2 — PROFESSIONAL ESCALATION (Day 14)

**Timing:** Send 12–15 days after invoice date (or 5–7 days after Touch 1)

**Email:**

**Subject:** Action needed: Invoice #INV-2026-1847 now 14 days overdue

Dear Sarah,

We sent a courtesy reminder about your invoice two weeks ago and haven't heard back. We want to make sure everything is okay with the work and the installation.

**Here's where we stand:**

- **Invoice #:** INV-2026-1847
- **Amount:** $2,850.00
- **Service:** Water heater replacement (40 gal gas → 50 gal Rheem, installed 4/5/2026)
- **Due Date:** April 20th (our standard terms are Net 15)
- **Days Overdue:** 14 days

**Payment Options** (same as before):
- Online portal: [link]
- ACH/Bank transfer: Reply to email
- Check: Mail to 123 Main St, Anytown, CA 90210
- Phone: (555) 123-4567

**If there's a problem or question**, we want to hear about it. Sometimes invoices get lost, there's a billing question, or the work didn't meet expectations. Please reach out directly:

- Is there an issue with the water heater or installation?
- Do you see an error on the invoice?
- Did you already send payment? (Please let us know so we can update our records!)

**We need to hear from you or receive payment by [April 29th].** After that, we'll have to pursue other options. Please don't leave us hanging — a quick email or call will solve this.

We value you as a customer and want to keep things smooth. Let's resolve this today.

Thanks,

**Reliable Plumbing**
(555) 123-4567
support@reliableplumbing.com

---

**Text Message Option:**

Hi Sarah, following up on INV-2026-1847 ($2,850) due 4/20. Payment needed by 4/29. If there's an issue with the water heater, we can fix it. Reply or call (555) 123-4567. Thanks!

---

### TOUCH 3 — FINAL NOTICE (Day 30+)

**Timing:** Send 28–30+ days after invoice date

**Email:**

**Subject:** FINAL NOTICE — Invoice #INV-2026-1847 Payment Required by [May 12th]

Dear Sarah,

This is our final notice regarding Invoice #INV-2026-1847. This invoice is now 35 days overdue and payment remains outstanding.

**Invoice Details:**
- **Number:** INV-2026-1847
- **Amount:** $2,850.00
- **Original Due Date:** April 20th, 2026 (Net 15 terms)
- **Service:** Water heater installation at 789 Maple Drive, Anytown, CA
- **Work Completed:** April 5th, 2026
- **Current Status:** 35 days past due

We have sent two previous payment requests (April 12th and April 18th) without response. We have a responsibility to our business to collect payment for work completed and approved by you.

**What happens next if we don't hear from you:**

Under California law, we reserve the right to file a **mechanic's lien** against the property at **789 Maple Drive, Anytown, CA** if payment is not received. Additionally, this account may be referred to a collections agency, which can negatively impact your credit rating.

**Your options to resolve this immediately:**

1. **Pay in full** using any of these methods:
   - Online: [link]
   - ACH/Bank transfer: Reply with your request
   - Check: Mail to 123 Main St, Anytown, CA 90210
   - Phone: (555) 123-4567

2. **Contact us immediately** if there is a legitimate issue with the work, a billing error, or if you have already paid. We are willing to work with you, but we need communication.

**Deadline:** We must receive payment or hear from you by **[May 12th, 2026]**. After that date, we will proceed with collection action and lien filing.

We would much prefer to resolve this with you directly and maintain a positive relationship. However, we cannot move forward without action on your part.

Please treat this matter with urgency and contact us today.

**Reliable Plumbing**
123 Main Street
Anytown, CA 90210
(555) 123-4567
support@reliableplumbing.com

---

**Text Message Option (if preferred):**

FINAL NOTICE: INV-2026-1847 ($2,850) now 35 days overdue. Payment or contact required by 5/12. Continued non-payment will result in lien filing and collections action. Call (555) 123-4567 immediately.

---

**Key Variables to Customize for Your Business:**

- [Company Name] — Your actual company name
- [Phone] — Your business phone
- [Email] — Your business email
- [Address] — Your mailing address
- [Payment Link] — Your online payment portal URL
- [Customer Name] — Customer first/last name
- [Invoice #] — The actual invoice number
- [Amount] — The dollar amount
- [Job Description] — What was installed/repaired
- [Job Address] — Customer's property address
- [Due Date] — Based on your Net X terms (e.g., Net 15 = 15 days from invoice)
- [Escalation Date] — Day 14 overdue date
- [Final Deadline] — Day 30–35 overdue; set 7–10 days from when you send this notice
- [State] — Your state (for lien law reference; research your specific statute)
- [Payment Methods] — Edit to match what your company actually accepts

---

**Customization Tips:**

- **Tone adjustment:** If your company voice is more casual or formal, adjust the language while keeping structure intact
- **Late fees:** If your config includes late fees or interest, add it to Touch 2 and Touch 3 (not Touch 1)
- **Warranty:** If the customer disputes the work, incorporate the warranty policy from config into the escalation
- **Lien language:** Research your state's mechanic's lien statute; adjust the legal language to match your jurisdiction
- **Multi-touch timing:** Adjust the day counts (7, 14, 30) to match your business preferences — these are standard but flexible

---

## v2.1 Additions

### State-Lien-Deadline Quick Reference (for Touch 3)

Mechanic's lien filing deadlines vary wildly by state and by whether the owner is a direct customer or a GC subbed you. Use this as a starting-point reference and always confirm the current statute before filing — deadlines change and pre-lien-notice rules (e.g., CA's 20-day preliminary notice) are often stricter than the lien-filing window itself.

| State | Residential lien deadline (from last work/supply) | Pre-lien notice required? |
|-------|----------------------------------------------------|----------------------------|
| California | 90 days | Yes — 20-day Preliminary Notice |
| Texas | 15th day of 3rd month after project ends (residential owner-occupied: 15th of 3rd month after each month of work) | Yes — 3rd month after non-payment |
| Florida | 90 days | Yes — Notice to Owner within 45 days of first work |
| Arizona | 120 days | Yes — 20-day Preliminary Notice |
| Colorado | 4 months (residential) | No statewide pre-notice, but recommended |
| Georgia | 90 days | Yes — Notice of Commencement response |
| New York | 4 months (single-family) / 8 months (other) | No pre-notice required |
| Illinois | 4 months | Yes — Notice within 60 days for owner-occupied |
| North Carolina | 120 days | Yes — Notice to Lien Agent within 15 days of first work |
| Washington | 90 days | Yes — Pre-Claim Notice to owner |

**How to use this table in Touch 3:**
- Pull the user's state from `config.yml`.
- If the state is in the table and the clock is running out (e.g., Day 30 overdue + 90-day lien window = ~60 days left to file), make the lien language concrete: *"Under [State] law, our lien-filing window on this project closes on [specific date]. We would prefer to resolve this with you directly."*
- If pre-lien notice was missed, do NOT threaten a lien you can no longer legally file — shift to the collections-agency and credit-reporting language instead.
- For commercial / GC-subbed work, the deadlines differ — this table is residential-direct only.

### Payment-History-Aware Schedule Adjustment

Not every customer deserves the same 7 / 14 / 30 cadence. Pull payment history from the CRM (or ask the user) and adjust:

| Customer Profile | Recommended Cadence | Rationale |
|------------------|---------------------|-----------|
| **Repeat customer, always pays on time** | Stretch: Day 10 / Day 21 / Day 40 | Assume good intent; a stale envelope is more likely than a deadbeat |
| **Repeat customer, sometimes slow (1–2 prior > 30 days)** | Standard: Day 7 / Day 14 / Day 30 | The default is tuned for this segment |
| **New customer, no history** | Standard: Day 7 / Day 14 / Day 30 | Default caution |
| **New customer, high-ticket (> $5K)** | Compress: Day 5 / Day 12 / Day 25 | Risk is elevated; compress the window to preserve lien-filing options |
| **Prior-disputed or prior-non-pay** | Compress + tone shift: Day 5 / Day 10 / Day 20, Touch 1 skips "assume good intent" warmth | This customer has already told you who they are |
| **Insurance restoration (waiting on adjuster)** | Parallel track: Day 14 to customer, Day 7 to adjuster | Adjuster delay is common; don't pressure the homeowner for money they can't release yet |

**How to apply:**
- Ask the user for the customer's prior invoice count and on-time rate, or pull from CRM if available.
- Adjust the day counts in the Touch 1 / 2 / 3 cover language and in the "Timing" lines of the output.
- Flag the selected profile in the output so the dispatcher / AR lead can sanity-check.

### Warranty-Dispute Hardening (companion to Scenario A)

When the claim is that "the work failed," use this structure before sending any follow-up:

1. **Request specifics in Touch 1 warmth:** "What exactly isn't working? Is it a leak, a no-flow, a noise, a pressure issue, a temperature issue?"
2. **Tech-side review BEFORE Touch 2:** Pull the invoice, photos from the job, and any callback record. If the claim is plausible and within warranty, offer a no-cost inspection in Touch 2 before restating the balance.
3. **Reframe payment and warranty as separate tracks:** "We're sending a tech to look at [specific concern] on [date]. That's our warranty commitment. The invoice for the completed work is due in parallel." This prevents the customer from using a warranty concern as a permanent payment blocker.
4. **If inspection confirms workmanship defect:** Do NOT send Touch 3. Credit the disputed portion, issue a corrected invoice, and close the loop.
5. **If inspection rules out workmanship defect:** Document the findings, send a photo/report summary, and proceed with Touch 3 on the full original balance.

## v2.2 Additions

### Expanded Lien-Deadline Reference (+5 states)

The v2.1 table covered the 10 states most plumbing shops encounter by volume. The v2.2 addition extends the reference to 15 states, adding five states with unusual deadline math that has caught shops off-guard in the last two cycles of AR disputes reviewed. Same usage rules apply — pull state from config, confirm the current statute before filing, and do not threaten a lien that pre-lien-notice timing has already foreclosed.

| State | Residential lien deadline (from last work/supply) | Pre-lien notice required? | Unusual-math note |
|-------|----------------------------------------------------|----------------------------|-------------------|
| Pennsylvania | 6 months (from last work) for lien filing; 4 months for formal notice of intent | Yes — Formal Notice of Intent 30 days before filing | Two-step process: Notice of Intent first, then Claim — do not skip the Notice |
| New Jersey | 90 days (from last work) | Yes — Notice of Unpaid Balance within 60 days on residential | Residential Construction Lien Fund adds a separate statutory process for 1–2 family homes |
| Massachusetts | 90 days from last work (Notice of Substantial Completion / Termination); 30 days to file lien statement after that | Yes — Notice of Contract at project start preferred | Filing window is a two-stage trigger; easy to miss the 30-day inner window |
| Ohio | 75 days (residential) from last work | Yes — Notice of Furnishing for subcontractors only | Direct contracts with homeowner do not require Notice of Furnishing, but document the contract clearly |
| Michigan | 90 days from last work | Yes — Notice of Furnishing within 20 days of first work for subs | Homestead / residential affidavit requirements are strict — follow form exactly |

**Combined with v2.1, the skill now covers 15 states**: CA, TX, FL, AZ, CO, GA, NY, IL, NC, WA (v2.1) + PA, NJ, MA, OH, MI (v2.2). Together these 15 states cover roughly 70% of US plumbing-shop invoice volume by market.

**When to escalate to counsel rather than leaning on the table:**
- Any commercial / GC-subbed job (deadlines differ substantially from residential-direct — do not rely on this table)
- Any lien amount over the state's small-claims cap where counsel is going to be involved anyway
- Any state not in the combined 15-state table (research the current statute directly)
- Any prior disputed or bonded-off lien claim on the same project

### Shared Lien-Deadlines Reference Pointer

This skill's 15-state lien table is now the canonical source for lien-deadline logic across the plumbing skills repo. Two other financially-sensitive skills should reference this table rather than duplicate it:

- **Estimate Writer** — when quoting a large project (over ~$3,000 residential or any commercial), the estimate should include a state-specific one-liner on the shop's lien rights. Pull the state's lien deadline from the table above and use the standard language: *"[Shop] preserves its statutory lien rights under [State] law. Under current [State] statute, our lien-filing window extends [X days/months] from the last day of work on this project."*
- **Change Order Tracker** — when a change order significantly extends project duration (triggering a new "last day of work" date), update the implicit lien-filing date accordingly. A large CO near the end of a long project can accidentally *extend* the shop's lien-filing window — which is usually in the shop's favor but has to be tracked.

If a future cycle breaks the table out into a standalone `_shared/lien-deadlines.md` reference, this skill becomes one of several consumers of that reference. Until then, this skill is the source.

### Partial-Payment Handling Template

A common pattern that v2.1 did not cover: the customer pays *something* but not the full invoice amount. Three sub-patterns, each with distinct handling:

**Sub-pattern A — Partial payment with a stated reason** ("I'm paying $1,500 of the $2,100; the last $600 is for the fixture I'm still not happy with").

- Do not cash the payment and go silent. Confirm the partial in writing, explicitly restate what remains outstanding, and tie it to the specific concern.
- Template: *"Received $1,500 on [date]. Remaining $600 is on hold pending resolution of [specific concern]. Our tech [Name] will be out on [date] to address. We'll zero the balance or produce the inspection report at that visit — not both going backward."*
- If the concern is warranty-plausible: run the v2.1 Warranty-Dispute Hardening sub-template before pushing for the remaining balance.

**Sub-pattern B — Partial payment with no reason given** (customer wires $1,500 on a $2,100 invoice with no explanation).

- Within 1 business day, reach out to confirm intent. Do not assume the payment was a typo, and do not assume the remaining balance is disputed. Ask.
- Template: *"Thanks for the $1,500 on the [date] job. I want to make sure I have our records right — is the remaining $600 coming separately, or is there a concern I should know about so we can get it resolved?"*
- The absence of a stated reason is the risk signal; the follow-up is the control.

**Sub-pattern C — Partial payment as an installment the shop did not agree to** (customer decides on their own to pay in three parts).

- Do not accept the installment schedule by silence. If the shop has not agreed to payment terms in writing, a series of partials is informal credit extension and can complicate a lien claim later.
- Template: *"Thanks for the partial — I want to flag that we don't have a formal payment plan on this invoice. Can we get one set up so we're both clear on the schedule? I can send a simple plan that works for your cash flow and keeps everything on paper."*
- Preserve lien rights by formalizing: a written payment plan that references the original invoice date preserves the "last day of work" anchor for lien-deadline purposes in most of the 15 tabled states.

### Collection-Agency Handoff Discipline

For the rare case the 3-touch cadence exhausts and the lien window has closed or the amount does not justify a lien, the handoff to a collection agency is the final step. Three rules before handing off:

1. **Final Letter of Notice.** Send one final certified letter before the handoff stating the balance, the shop's attempts to resolve it (list the touch dates), and the intention to transfer to a third-party collections agency on a specific date (give the customer 10 business days). A certified letter with this content generates 15–25% recovery on its own in most plumbing-shop AR data — cheaper than an agency's 25–50% cut.
2. **Package the file correctly.** The agency needs: original invoice, signed work authorization, all touch-point correspondence with date stamps, any change orders, any photos or documentation from the job. An incomplete file reduces the agency's recovery rate substantially.
3. **Credit-reporting threshold.** Only accounts over the state's fair debt collection threshold (usually $1,000) should be reported to credit bureaus. Below that, agency letters and soft-collection calls are the tool; credit reporting on small balances creates more reputational risk than it recovers.

### Cross-Reference with Product Recall Workflow

Added in v2.2 because of a new adjacency: if an invoice dispute involves a product that has since been recalled, handle the payment track and the recall track separately — do not entangle them.

- The invoice for the original work (labor, unaffected materials) remains payable. The customer's recall-side remedy is with the manufacturer, not with the shop.
- Reference the Product Recall Customer Outreach skill's handoff-to-manufacturer language. The shop's liability on a recalled-product defect is typically limited; do not credit the full invoice out of an abundance of caution unless the shop has actual fault.
- If the customer is withholding payment *because* of a recall, run the warranty-dispute hardening sub-template (v2.1) with the recall as the specific concern, separate the two tracks explicitly, and keep the payment conversation with the shop while the remedy conversation goes to the manufacturer.

## v2.3 Additions (2026-04-27)

The v1.0 / v2.1 / v2.2 content above is unchanged. The four sub-sections below extend the skill into a runtime lien-window calendar, an explicit insurance-restoration AR track, Spanish bilingual touches, and a one-tap-payment-link friction-reduction discipline.

### v2.3.A Lien-Window Countdown Block (turns the table into runtime urgency)

The v2.1 + v2.2 combined 15-state lien table is the canonical reference, but a static table doesn't tell the AR lead *when* the window closes on this specific invoice. The countdown block below converts the table into runtime numbers for the invoice in front of the user. Generate it whenever Touch 2 or Touch 3 is being drafted on a residential-direct invoice in any of the 15 tabled states.

**Countdown block format (insert after the Touch 3 invoice details, before the legal/remedies language):**

```
🗓️ LIEN-WINDOW COUNTDOWN
  State:               [State name]
  Last day of work:    [YYYY-MM-DD]
  Days since LDOW:     [N] days
  Pre-lien notice:     [REQUIRED — sent on YYYY-MM-DD | NOT SENT | NOT REQUIRED]
  Lien deadline:       [YYYY-MM-DD]   ([N] days remaining)
  Counsel-trigger:     [<30 days remaining → escalate to counsel TODAY |
                        30–60 days → counsel review THIS WEEK |
                        >60 days → continue 3-touch cadence]
```

**Calculation rules:**
- Last day of work (LDOW) is the anchor for every state's deadline math. If a change order extended the project (per Change Order Tracker), use the new LDOW from the latest CO completion. A late CO usually *extends* the lien window in the shop's favor, but only if the LDOW is documented.
- Pre-lien notice deadline runs from the *first* day of work or supply, not LDOW. If the pre-lien notice deadline has already passed and was missed, the countdown block surfaces `Pre-lien notice: NOT SENT — lien claim foreclosed` and the Touch 3 legal language must shift to collections-only (do not threaten a lien that pre-lien-notice timing has already foreclosed; the v2.1 rule is repeated here for clarity).
- Counsel-trigger thresholds are conservative on purpose — under 30 days remaining is too tight to file without legal review for most shops.

**Worked example (California, residential-direct):**
- Job completed 2026-02-15 (LDOW)
- 20-day Preliminary Notice sent 2026-02-12 (within the 20-day window from first work)
- Today is 2026-04-27
- Days since LDOW: 71
- CA residential lien deadline: 90 days from LDOW = 2026-05-16
- Days remaining: 19
- **Counsel-trigger: <30 days remaining → escalate to counsel TODAY**

The countdown block becomes the AR lead's single source of truth for "do I need to make a lien decision this week?". Without it, shops routinely watch lien windows close while running the standard 3-touch cadence on autopilot.

### v2.3.B Insurance-Restoration AR Track (explicit drill-down)

The v2.1 cadence table flagged "Insurance restoration (waiting on adjuster)" as a distinct profile but didn't drill into the actual workflow. Insurance-restoration AR is structurally different from homeowner-direct AR in three ways: the payer is the carrier (not the homeowner), the schedule runs on adjuster cycle (not Net 15 from invoice date), and the work usually happens before the carrier's check is cut. The track below replaces the standard 3-touch cadence on insurance jobs.

**Indicator signals (apply this track when any are true):**
- Job is mitigation work after a water loss (broken pipe, slab leak, sewer backup with category 1–3 water damage).
- Customer mentions a claim number or adjuster name during intake.
- Quote was approved by the adjuster, not by the homeowner sign-off alone.
- Payment is being routed through a third-party payee (mortgage company or carrier check made out to the homeowner *and* the shop).

**Parallel two-track cadence:**

**Customer-facing track (3 touches, slower cadence):**
- **Touch 1 (Day 14):** Soft check-in. *"We know insurance-claim payments take time. We want to keep you in the loop and give you a heads-up if we hit any roadblocks with the adjuster."* No invoice-due framing; the homeowner is not the bottleneck.
- **Touch 2 (Day 30):** Status request. *"Have you received the carrier's settlement statement? Once you have it, the next step is endorsing and forwarding the check (or coordinating mortgage-company release if the loss exceeds the policy's release threshold)."*
- **Touch 3 (Day 60+):** Escalate to direct call, not a formal final notice. The homeowner did not cause the delay and a final-notice letter to the homeowner damages the relationship without recovering money.

**Adjuster-facing track (parallel, 7-day cadence):**
- **Day 7:** Email the adjuster the work-completion package — Xactimate-aligned line items, photos, completion certificate, depreciation recovery if applicable. Carriers pay faster when the package matches their software's line-item structure.
- **Day 14:** Email the adjuster a status query referencing the claim number and last-action date.
- **Day 21:** Call the adjuster. Email-only escalation past Day 21 produces sub-optimal payout speed; the call is the lever.
- **Day 30:** If still no payment, contact the adjuster's supervisor with a CC to the homeowner.
- **Day 45:** If still no payment, file a complaint with the state's department of insurance referencing the claim, completion date, and timeline of unpaid work.

**Mortgage-company release rule:**
- If the loss exceeds the policy's release threshold (typically $10,000 or $25,000 depending on carrier), the mortgage company holds the check until the work is verified and signed off. The shop must coordinate the release with the mortgage company directly, not just rely on the homeowner — most homeowners don't know the release process and the funds sit unreleased for weeks.

**Customer-vs-insurance balance split:**
- Some claims pay only the depreciated value initially; the recoverable depreciation is released after the work is completed and documented. The shop should track the customer-portion (deductible + non-recoverable items) and the insurance-portion (depreciated value first, then RCV release) separately on the invoice. The customer-portion is collectable on standard cadence; the insurance-portion is on the parallel track above.

### v2.3.C Spanish Bilingual Variants of Touch 1 / Touch 2 / Touch 3

Cross-skill consistency with Pre-Visit Diagnostic Intake v1.1 (Spanish safety phrases) and Review Request Drafter v2.3 (Spanish job-type templates). When the customer record carries `customer_language: Spanish`, all three touches go out in Spanish. The translations below preserve the v1.0 / v2.1 tone progression (warm → professional/firm → formal/legal).

**Tone notes for Spanish-language AR contexts:**
- Use *usted* throughout (formality is more important in money conversations than in service conversations).
- The standard Spanish term for invoice is *factura*. *Cuenta* (bill) is colloquial but reads slightly less formal — use *factura* in writing.
- *Pago* (payment), *vencimiento* (due date), *atrasado* (overdue), *plan de pago* (payment plan), *gravamen* (lien — note: regional variation; *embargo* is also used in some regions but carries broader connotation, prefer *gravamen* in legal-notice contexts).

**Touch 1 — Recordatorio amistoso (Spanish, Day 7):**

> Asunto: Recordatorio rápido — Factura #INV-2026-1847
>
> Estimado/a [Nombre],
>
> Gracias por elegir **[Nombre de la empresa]** para su [tipo de trabajo]. Esperamos que todo esté funcionando bien.
>
> Le escribimos porque aún no hemos recibido el pago de la **Factura #INV-2026-1847** ($X,XXX), enviada el [fecha]. El trabajo se completó el [fecha] en **[dirección]**.
>
> **No se preocupe si el pago ya está en camino.** Si todavía no lo ha enviado, aquí están las opciones más fáciles:
>
> - Tarjeta de crédito/débito: visite [enlace al portal] (sin cargos adicionales)
> - Transferencia bancaria (ACH): responda a este correo y le enviaremos los datos
> - Cheque: enviar por correo a [dirección]
> - Por teléfono: llame al [teléfono] para pagar por teléfono
>
> Si tiene alguna pregunta sobre la factura o el trabajo, estamos para ayudar. — **[Nombre de la empresa]**

**Touch 2 — Escalación profesional (Spanish, Day 14):**

> Asunto: Acción necesaria — Factura #INV-2026-1847 con 14 días de atraso
>
> Estimado/a [Nombre],
>
> Le enviamos un recordatorio amistoso hace dos semanas y aún no hemos recibido respuesta. Queremos asegurarnos de que todo esté bien con el trabajo y la instalación.
>
> **Resumen de la situación:**
>
> - Factura #: INV-2026-1847
> - Monto: $X,XXX
> - Servicio: [descripción]
> - Fecha de vencimiento: [fecha]
> - Días de atraso: 14
>
> **Si hay un problema o una pregunta**, queremos saberlo. A veces las facturas se pierden, hay un error, o el trabajo no cumplió con lo esperado. Por favor, contáctenos directamente.
>
> **Necesitamos saber de usted o recibir el pago antes del [fecha límite].** Después de esa fecha, tendremos que tomar otras medidas. Una respuesta rápida resuelve esto.
>
> Lo valoramos como cliente. — **[Nombre de la empresa]**

**Touch 3 — Aviso final (Spanish, Day 30+):**

> Asunto: AVISO FINAL — Factura #INV-2026-1847, pago requerido antes del [fecha]
>
> Estimado/a [Nombre],
>
> Este es nuestro aviso final con respecto a la Factura #INV-2026-1847. Esta factura está ahora con [N] días de atraso y el pago sigue pendiente.
>
> Hemos enviado dos solicitudes de pago anteriores ([fecha 1] y [fecha 2]) sin respuesta. Tenemos la responsabilidad con nuestra empresa de cobrar el trabajo completado y aprobado por usted.
>
> **Bajo la ley de [Estado], nos reservamos el derecho de presentar un gravamen mecánico (*mechanic's lien*) contra la propiedad en [dirección]** si no recibimos el pago. Adicionalmente, esta cuenta puede ser referida a una agencia de cobranza, lo cual puede afectar negativamente su historial de crédito.
>
> **Sus opciones para resolver esto inmediatamente:**
>
> 1. Pagar el saldo completo: [opciones de pago]
> 2. Contactarnos inmediatamente si hay un problema legítimo, un error, o si ya pagó.
>
> **Fecha límite:** Debemos recibir el pago o saber de usted antes del **[fecha]**. Después de esa fecha, procederemos con la acción de cobranza y la presentación del gravamen.
>
> Preferiríamos resolver esto directamente con usted. — **[Nombre de la empresa]**

If the customer's language is unconfirmed, default to English. Do NOT auto-detect from the customer's name — the same caveat that applies to Review Request Drafter v2.3 applies here: presumption when wrong damages the AR conversation more than it helps.

### v2.3.D One-Tap-Payment-Link Friction-Reduction Discipline

The single largest friction reduction in plumbing-trade AR is making payment one-tap. Every published vendor case study (Stripe / Square / Plaid / GoCardless / Service Fusion / ServiceTitan billing 2024–2026 numbers) shows the same pattern: a one-tap payment link in Touch 1 lifts response by 30–40% over a portal URL that requires a login, and a portal URL with autofilled invoice number lifts response by another 8–12% over a generic portal URL. The discipline below operationalizes this.

**Touch 1 link discipline:**
- The link in Touch 1 must be a one-tap payment link, not a portal homepage. Examples: Stripe Payment Link with the invoice pre-loaded, ServiceTitan / Housecall Pro / Service Fusion / Jobber pay-by-link URL, Square Invoice payment link.
- The link must be tracked. Use a UTM or shop-side parameter so the AR lead can see which invoices were opened-but-not-paid (a high-value coaching signal — opened-but-not-paid means friction at the payment-method step, not at the awareness step).
- The link must NOT be shortened through a generic shortener (bit.ly / tinyurl / t.co) — major email clients flag those as suspicious and depress open rates. Use the platform's native short-URL or the shop's own domain shortener.

**Touch 2 link discipline:**
- Keep the same one-tap link from Touch 1. Don't introduce a second link in Touch 2 — link consistency reduces friction.
- Add a "click here to set up a payment plan" link (separate, distinct) for customers who haven't paid because they can't pay in full. The plan-setup link should land on a form that captures down payment + installment cadence + auto-debit consent in a single page.

**Touch 3 link discipline:**
- The one-tap link is now last in the touch (after the lien-countdown block, after the legal language) — the urgency of the legal language is the lift, the link is the path. Reversing the order in Touch 3 is the v2.1 finding that surfaced in shop-side data.
- Add a second link to a written-payment-plan-setup form. The customer who hits Touch 3 and hasn't paid is overwhelmingly a customer who *can't* pay in lump sum, not one who *won't* pay; offering a plan formally at this point recovers 12–18% of accounts that would otherwise go to collections.

**Suppression rule when the shop's payment portal is degraded:**
- If the payment portal has been down or degraded in the last 24 hours (Stripe outage, ServiceTitan billing degradation, etc.), pause Touch 2 and Touch 3 for 48 hours and reopen with a brief "we had a payment-portal issue on [date]" acknowledgment. Sending a payment ask during a known portal outage produces a wave of frustrated replies that compress the AR lead's bandwidth right when the portal is also recovering.

**Cross-skill references:**
- **Estimate Writer v2.0** — the lien-rights one-liner Estimate Writer adds to large quotes ($3K residential, any commercial) draws the LDOW anchor from the v2.3.A countdown logic; once the work begins, the same LDOW feeds the AR cadence here.
- **Change Order Tracker v1.2** — extends LDOW; the lien-window countdown auto-recalculates when a CO closes.
- **Pre-Visit Diagnostic Intake v1.1** — `customer_language` field drives the Spanish bilingual variant selection in v2.3.C.
- **Review Request Drafter v2.3** — share Spanish-language tone discipline; same `customer_language` field.
- **Vendor Price Increase Customer Communication** — when an invoice was issued during a known price-wave window, soften the Touch 1 framing to "we know our pricing changed during this window — happy to walk through any line item."
- **Product Recall Customer Outreach** — confirms the v2.2 partial-payment-recall separation; the AR track stays with the shop, the recall remedy track goes to the manufacturer, and they do not entangle.
