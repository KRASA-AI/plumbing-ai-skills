---
name: "Invoice Follow-Up Sequence"
category: admin
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~15 min/sequence"
version: 2.0
last_eval_score: 8.8
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
