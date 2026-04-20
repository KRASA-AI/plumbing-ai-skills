---
name: "Smart Leak Detection Install Briefing"
category: sales
tools: [claude, chatgpt]
difficulty: intermediate
time_saved: "~45 min per customer briefing; replaces a verbal explanation + a follow-up 'what do I tell my insurance?' back-and-forth most shops handle inconsistently"
version: 1.0
last_eval_score: null
---

# Smart Leak Detection Install Briefing

## Purpose

Produce a customer-facing briefing that translates the 2026 home-insurance landscape around smart leak detection — several major carriers now *require* or heavily discount for an installed smart leak-detection device on renewal — into a clear "which device, why, where it installs, what it costs, and what the letter to the insurer says" recommendation for one customer at one property. This is the conversation that hits a plumbing shop's phones in two distinct moments: (1) a homeowner got a renewal notice or a "recommended upgrade" letter from their insurer (Farmers, State Farm, Mercury, Nationwide, Amica, Travelers, Chubb, UPC, etc.) and called the shop asking "can you install one of these?" and (2) the shop is already on site doing another job (water heater replacement, repipe, bathroom remodel) and the tech wants to attach a leak-sensor install to the same visit.

The skill writes the briefing in a way that does three things at once: explains the insurer landscape truthfully (which carriers discount which devices, approximate discount bands, which few are starting to *require* the device at renewal), recommends a specific product class and specific install location based on the home's plumbing (whole-home flow monitor with shutoff at the service entry vs. point sensors at high-risk fixtures vs. DIY), and produces the signed letter the homeowner can send to their insurance agent documenting that the device was professionally installed — which is what most carriers require to actually unlock the discount.

The "letter to insurer" piece is the unique gap. Most shops can quote the install. Most sensor manufacturers have a generic install-certificate PDF. Very few shops produce the letter that bridges the two and maps product serial numbers, shop license info, install date, and the specific carrier's discount requirements into a document the agent can file. That letter is what closes the loop and gets the homeowner's discount applied at renewal rather than lost in a follow-up email.

## When to Use

- A homeowner calls after receiving a renewal notice or "discount available" letter from their insurer asking about smart leak detection devices
- A homeowner is being told by their carrier (Farmers in several states has begun this; Mercury's 2026 program expanded; Nationwide's Phyn partnership offers 15%; State Farm, Amica, UPC, Chubb all offer discounts) that they must install a device to maintain coverage or to get a discount at renewal
- The shop is on site for a water heater replacement, repipe, or bathroom remodel and the tech wants to attach a leak-sensor install (natural pairing with the Water Heater Standards Briefing — same trip, same permit if applicable, same hole in the wall)
- A property manager or landlord is deciding whether to install whole-home leak protection across a portfolio of rentals to reduce claims frequency
- A high-value home (>$1M replacement cost) has a water-damage claim history and the insurer has flagged a condition on the renewal
- A homeowner is planning an extended absence (snowbird, travel, vacation home) and wants shutoff-valve leak detection for peace of mind

**Do not use for:**
- Emergency active-leak situations — the customer needs the water shut off now, not a 6-page briefing. Use the Estimate Writer skill for the repair and discuss the install at follow-up.
- Multi-unit commercial properties with complex plumbing layouts that need an engineered design — this skill writes a single-residence briefing, not a commercial risk-management plan.
- Customers who have not confirmed their insurer's current discount or requirement in writing — do not invent discount percentages or mandates. If the customer is unsure, include a one-line "call your agent and confirm" step as the first action item rather than guessing.

## Required Input

1. **Customer and property context**
   - Customer name, property address (city and state — used to anchor carrier and state-law specifics)
   - Property type (single-family detached, townhome, condo with shared plumbing, small multi-family the owner occupies)
   - Square footage and approximate number of wet rooms (bathrooms, kitchens, laundry, mechanical)
   - Year built and year of last major repipe (influences which risk the sensor is really managing — copper pinhole risk vs. PEX vs. polybutylene legacy vs. galvanized)
   - Whether the home is a primary residence, second home, or rental (changes both the insurer requirements and the product recommendation)
   - Whether the homeowner is a snowbird or travels for extended periods (tilts strongly toward whole-home with auto-shutoff)

2. **Insurance carrier and program specifics from the customer**
   - Carrier name (Farmers, State Farm, Mercury, Nationwide, Amica, Travelers, Chubb, UPC, USAA, etc.)
   - The exact discount percentage or requirement language the customer has been given (the customer should provide the renewal letter or the agent's email — do not guess)
   - The approved-device list the carrier has published, if available (Moen Flo, Phyn Plus, LeakSmart, StreamLabs, Flume, Dome Leak Sensor, etc. — carriers often have specific approved lists)
   - Whether the program requires professional installation and what documentation the carrier needs (most require an installer's license number and an install date)

3. **Plumbing site conditions that gate the install**
   - Service entry location — where the main water line enters the house (basement, garage, mechanical closet, slab penetration, outside wall) — and whether there is at least 10–14" of straight pipe run on a ¾" or 1" line to accept a whole-home flow monitor
   - Main shutoff accessibility (is there already a functional main shutoff, or will the flow monitor *become* the shutoff?)
   - Electrical availability near the main line (whole-home units need 120V — some use plug-in, some hardwire)
   - Wi-Fi signal strength at the install location (most devices are cloud-connected)
   - Number and location of highest-risk fixtures for point sensors (under-sink supply lines, dishwasher, washing machine, water heater pan, ice maker, toilet shutoffs in upper floors)
   - Whether the home has a well pump or irrigation system that would false-trigger a flow monitor and requires learning-mode tuning

4. **Budget and product-preference framing**
   - Whether the customer has a carrier discount that would offset a portion of the install (discount value over 3–5 years is the right ROI frame, not single-year)
   - Price sensitivity (DIY point sensors at ~$20–$40 each vs. pro-installed whole-home at ~$650–$1,200 all-in)
   - Preference for brand ecosystem (Apple Home, Google Home, SmartThings, standalone app) — some sensors pair with specific ecosystems
   - Whether the customer wants auto-shutoff on alert (valve closes automatically on detected leak) or alert-only (phone notification, no auto-close) — this is the single biggest install-cost fork

5. **Shop facts**
   - Which devices the shop is certified/approved to install (Moen Flo has a pro install certification; Phyn has a professional installer program; LeakSmart, Flume, StreamLabs have less formal programs)
   - Shop's flat-rate install price by device class (whole-home flow+shutoff, whole-home flow-only, professional point-sensor package)
   - Shop's license number and state license expiration date (needed for the letter to insurer)
   - Shop's standard workmanship warranty on this class of install (most shops run 1 year parts/labor on the install)

## Instructions

Produce a six-section briefing scoped to **one customer, one property, one insurance program**. The briefing is not a generic "smart leak detection buying guide" — the customer can find dozens of those. The shop's value is the translation from *this customer's* insurer requirement, *this customer's* plumbing, and *this shop's* install capability into a signed, specific recommendation + a letter the agent can file.

### Section 1 — One-paragraph customer summary (50–80 words)

Open with the customer's situation in plain language. Name the property, the carrier, the specific discount or requirement the customer received, the triggering reason ("your insurer's renewal letter asks for professional install of an approved leak detection device by [date]"), and the recommendation in one sentence ("we recommend the [product] installed at the main line on the basement wall — it is on your carrier's approved list and qualifies for the full [X%] discount").

This is the paragraph the homeowner forwards to their spouse and to their insurance agent. Write it so both audiences get the right signal.

### Section 2 — The insurance landscape, specific to this carrier (4–6 short paragraphs)

Write to the customer's specific carrier and the specific letter or policy language they received — not a general survey of the whole industry. If the customer has provided the carrier's approved-device list, work within that list. If not, name the customer's carrier and the devices that carrier has historically approved, and explicitly flag that the customer should confirm the current list with their agent before ordering.

Cover, in short paragraphs:

- **What the customer's carrier is offering or requiring.** Discount percentage (typical range: 3%–15% of the water-damage peril portion of the premium; some programs run 5%–10% of the total homeowner premium), whether it is a renewal condition (a small but growing number of programs require install on high-value homes) or purely a discount (the large majority), and the documentation the carrier needs (typically: installer name, installer license #, install date, device make/model, and device serial number).
- **What the 2026 market context is without overstating.** Several carriers (Farmers in multiple states, Mercury across AZ, CA, GA, IL, NJ, NV, OK, TX, VA as of 2026, Nationwide through its Phyn partnership, Amica, State Farm, UPC, Chubb) now have formal programs. Some partnerships subsidize the hardware (Nationwide customers get 15% off Phyn; Mercury has rebates; some carriers subsidize through agent credits). Do not invent specific percentages for any carrier the customer has not already confirmed — instead, reference the letter or agent conversation the customer provided.
- **What the customer should confirm with their agent in writing before the install.** (1) The specific approved device list. (2) The exact discount percentage applied to which premium line item. (3) Whether the install must be completed before renewal to apply this year, or whether it will apply at next renewal. (4) What documentation the carrier needs post-install to apply the discount — most want a completed install certificate with the serial number.
- **What the insurance conversation is NOT.** The install does not typically make the home uninsurable without it (few programs actually require it as a condition of coverage; most make it a condition of discount or a condition of maintaining a specific coverage like service-line coverage). The device does not "replace" homeowner responsibility — water-damage claims still follow standard policy terms.

End the section with one sentence about who in the insurance process actually matters: the agent is the right contact for confirming the discount; the underwriter is who decides if a condition applies at renewal; the claims adjuster is who decides if a specific future claim is covered — the three are different roles and the customer should not assume a helpful answer from one binds the other two.

### Section 3 — Device comparison, 3–4 rows scoped to this property (table)

Build a table with these columns:

| Device | Type | Typical all-in install price (this shop, this site) | Auto-shutoff on leak? | On this carrier's approved list? | Fit for this property | Shop recommendation rank |

Include 3–4 real devices that are credible options for this specific home:

- **Moen Flo** (whole-home flow monitor with integral motorized shutoff valve, professional install) — best for homes with a clean ¾" or 1" main line and the customer wants auto-shutoff
- **Phyn Plus** (whole-home pressure-wave-analytic flow monitor with integral shutoff, professional install) — strong fit where the customer is with Nationwide (15% hardware discount + insurance discount), or where the customer wants the most detailed fixture-level leak analytics
- **LeakSmart** or **StreamLabs** or **Flume Bridge+** — flow-monitor alternatives with varying shutoff options; StreamLabs clamps on (non-invasive) which matters where the main line can't be cut during the visit
- **Professionally installed point-sensor package** (Dome Leak Sensor, Moen Point, or the shop's preferred point sensor brand, 4–6 placements at highest-risk fixtures) — best for homes where the service entry is inaccessible, or as a complement to a whole-home unit, or where the carrier approves point sensors specifically

The table should make one tier the clear shop recommendation based on *this property's* site conditions. Do not tie on the recommendation rank — pick one, briefly explain why the others are ranked lower for this site.

### Section 4 — Site install plan (bulleted, 6–10 items)

What the tech will do on install day, written so the customer and the insurance agent both understand what is happening:

- Install location (main water line at the [basement / garage / mechanical closet] wall, after the main shutoff, before the first branch)
- Required plumbing modifications (cutting a 12" section, sweating or press-fitting the flow monitor, adding a union before and after for future service)
- Required electrical (plug-in 120V within 6 ft, or hardwire with a dedicated outlet — disclose which)
- Wi-Fi configuration and firmware registration in the app
- Point-sensor placements (list specific fixtures — under kitchen sink, under each bathroom vanity, at washing machine, water heater pan, dishwasher, ice maker supply)
- Leak-test procedure on install day (open a downstream fixture briefly to verify the monitor reads flow; optionally trigger an auto-shutoff test with the customer watching)
- Customer walkthrough of the app (where to see alerts, how to set vacation mode, how to whitelist irrigation/well activity, how to share access with a spouse or property manager)
- Documentation the tech leaves on site (install certificate with serial number, shop license number, install date, warranty card)
- Typical install time (1.5–3 hours for whole-home with shutoff; 45–75 min for a point-sensor package)
- Any permit requirement (most jurisdictions do not permit a device install inline with existing plumbing that does not change the pressure or drain system — confirm local)

### Section 5 — Letter to insurer (drafted, ready to sign)

A short letter the customer signs and sends to their insurance agent. Structure:

- Dated on install day, addressed to the customer's agent (name and agency)
- One paragraph stating the install was completed by a licensed plumbing contractor on [date] at [address]
- Product details: manufacturer, model, serial number, whole-home vs. point
- Shop details: business name, license number, license state and expiration, technician name, contact phone and email
- Scope of install: professional install including [plumbing cut-in / electrical / app configuration / leak test]; device is active and paired to the customer's account
- One paragraph requesting the carrier apply the [specific discount the customer confirmed with their agent] effective [renewal date or current billing cycle per carrier policy]
- Request for written confirmation that the discount has been applied
- Attachments listed: install certificate, device photo showing serial, shop invoice, shop license (copy or number)

The letter is written in a tone the agent will recognize as a standard risk-mitigation documentation request — professional, specific, no salesmanship. Keep to one page.

### Section 6 — 12-month follow-up plan for the shop

What the shop does after the install to close the loop and protect the attachment opportunity. Three items:

- **Day 14 call** — shop calls the customer to confirm the discount was applied to the renewal or current policy. If the carrier has not applied it yet, shop offers to resend the letter to the specific underwriter or claims contact.
- **Month 6 check-in** — automated SMS asking whether the device has alerted on any event and whether the customer has understood the alert flow. This is a light-touch service moment that reminds the customer the shop stands behind the install.
- **Month 11 renewal reminder** — email 30 days before the insurance renewal, asking the customer to re-confirm that the discount carried over and reminding them that any plumbing changes in the home (new fixtures, remodel, appliance changes) might benefit from a sensor-rebalance visit.

## Example Output

**Scenario:** A 2004-built 3,100 sqft two-story single-family home in Chandler, AZ. Customer: Janet and Paul Reyes. Primary residence. Copper repipe done in 2019. Insurer: Mercury. The Reyeses received a 2026 renewal letter stating that installing an approved whole-home leak detection device would qualify for their "Smart Home Water Protection" discount (7% of the water-damage peril portion of their premium) and that Mercury's approved devices include Moen Flo and Phyn Plus. Home has a basement mechanical room where the service entry is clean ¾" copper with 18" of straight run; 120V outlet is 4 ft away; Wi-Fi signal in the mechanical room is strong. Paul is a snowbird and is out of the home Dec–March each year. Shop: Desert Valley Plumbing, license AZ ROC #118744, install price for Moen Flo with shutoff $1,095 all-in, point sensor package (6 sensors professionally placed) $485 all-in. Recommending Moen Flo based on site fit + snowbird use case.

### Section 1 — Customer summary

Janet and Paul, your 2004 Chandler home is a strong fit for a whole-home leak detection install. Your Mercury renewal letter offers the Smart Home Water Protection discount (7% of the water-damage portion of your premium) with a professionally installed Moen Flo or Phyn Plus. We recommend the Moen Flo installed at the main line in your basement mechanical room — it is on Mercury's approved list, fits your service-entry geometry, and gives you the auto-shutoff you want for your December–March snowbird months.

### Section 2 — The Mercury landscape, specific to you

Mercury's 2026 Smart Home Water Protection program offers a discount on your homeowner policy for customers who install an approved whole-home leak detection device. Per the renewal letter you shared, the discount is 7% of the water-damage peril line item on your premium — that is not the same as 7% of your total premium, and the dollar value depends on how Mercury has allocated the peril across your policy. Based on the letter you received, the program applies in Arizona.

Mercury's approved-device list as of the letter you received includes Moen Flo and Phyn Plus. Other carriers may have broader lists (Amica, State Farm, Nationwide all publish different approved lists), but since your carrier is Mercury and the letter is specific, we'll stay inside the Moen Flo / Phyn Plus lane and not recommend a device that might not count.

Mercury requires a professional install documented with the installer's license number, the install date, the device make/model, and the device serial number. The install certificate we leave on site meets that requirement; we also provide a signed cover letter addressed to your agent (Section 5 below) that includes everything Mercury typically asks for.

Before we schedule the install, please email your Mercury agent to confirm two things in writing: (1) the exact discount percentage will apply on this year's renewal (our understanding is yes based on your letter, but agents sometimes specify a minimum enrollment window) and (2) whether the discount is applied proactively by the underwriter or whether you need to submit the install certificate through a specific portal. This is a 10-minute email on your side and it locks the discount.

One thing the insurance piece is not: the Moen Flo install is not Mercury's condition of coverage. If you did not install the device, your coverage still applies at renewal — you would just miss the 7% water-damage discount. A small number of high-value-home programs (some Chubb and AIG private-client policies) are starting to make the install a condition of maintaining certain coverages like service-line or sump-failure endorsements, but that is not the case with Mercury here.

Finally, note that the agent, the underwriter, and the claims adjuster are three different roles. The agent confirms the discount; the underwriter decides if the condition sticks at renewal; the claims adjuster decides if a specific future leak claim is covered. Keep your install documentation in your file — if you ever have a claim, you will want the install date and serial number in a place you can find in five minutes.

### Section 3 — Device comparison for your home

| Device | Type | Install price (all-in, this site) | Auto-shutoff on leak? | On Mercury's approved list? | Fit for your property | Shop recommendation rank |
|---|---|---|---|---|---|---|
| Moen Flo | Whole-home flow monitor + integral shutoff | $1,095 | Yes (automatic) | Yes | Excellent — clean ¾" run in basement, 120V outlet in place, snowbird use benefits from auto-shutoff | **1 — recommended** |
| Phyn Plus | Whole-home pressure-wave flow + integral shutoff | $1,285 | Yes (automatic) | Yes | Good — analytics are the best in class, but price premium over Flo isn't justified here since Mercury discount is device-agnostic between these two | 2 |
| StreamLabs Control | Whole-home ultrasonic clamp-on + separate motorized shutoff | $1,395 | Yes (via separate valve) | Partial — approved list varies by state; please confirm with Mercury before ordering | 3 — but only a fit if the copper line couldn't be cut in | 3 |
| Moen Flow Smart Sensor package (6 point sensors, no whole-home) | Point sensors only | $485 | No (alerts only) | Mercury's approved list specifies whole-home for this discount; point-only likely would not qualify for the 7% | Only as a complement, not a replacement | Not recommended as primary |

### Section 4 — Install plan

- Install location: main water line in the basement mechanical room, after the existing main shutoff, before the first branch to the water heater and softener
- Plumbing modifications: cut a 12" section of ¾" copper, sweat-install the Moen Flo with copper unions before and after for future service, restore pressure and leak-test at full house pressure
- Electrical: plug into the existing 120V GFCI outlet 4 ft from the install location; no hardwiring needed
- Wi-Fi configuration: register the device in the Moen Flo app on Janet's phone, add Paul as a secondary account, configure alert thresholds for typical Chandler household use (will tune for the first 14 days to learn the baseline)
- Leak test: open the laundry cold hose bib briefly to confirm the monitor reads flow; trigger one simulated auto-shutoff with both Janet and Paul present so they see the valve close and reopen
- Customer walkthrough: how to see alerts, how to set vacation/away mode for the snowbird months, how to whitelist the irrigation controller so morning drip zones don't trigger a false positive
- Documentation left on site: Moen install certificate with device serial, Desert Valley Plumbing license info (AZ ROC #118744), install date, 1-year parts-and-labor warranty card
- Total time on site: 2 hours 15 minutes typical
- Permit: not required in Chandler for inline device install that doesn't change the supply or drain system configuration (confirmed with the local jurisdiction)

### Section 5 — Letter to Mercury agent

**Desert Valley Plumbing**
1442 S Arizona Ave, Chandler, AZ 85286
AZ ROC License #118744 (expires 08/31/2027)
(480) 555-0192 | service@desertvalleyplumbing.com

[Install Date]

Mercury Insurance — Attention: [Agent Name], Agency [Agency Name]
[Agent Email] / [Agent Address]

Re: Smart Home Water Protection discount — Policy #[policy number], Janet and Paul Reyes, [property address]

Dear [Agent Name],

This letter documents the professional installation of a smart leak detection device at the Reyes residence in Chandler, AZ, performed by our licensed technician on [install date].

Product installed:
- Manufacturer / Model: Moen Flo Smart Water Monitor and Shutoff (Model 900-001)
- Device serial number: [serial]
- Device type: Whole-home flow monitor with integral motorized shutoff valve
- Install location: Main water supply line, basement mechanical room, after main shutoff, before first branch

Installation scope:
- Professional plumbing cut-in on existing ¾" copper supply line with union fittings
- Device paired to customer's Moen Flo account (Janet Reyes, primary) with secondary access (Paul Reyes)
- Leak-detection firmware registered and live as of the install date
- Auto-shutoff function tested with customer present
- 1-year parts-and-labor warranty on the install from Desert Valley Plumbing

Installer / Company details:
- Company: Desert Valley Plumbing, LLC
- Arizona ROC License #: 118744 (active, expires 08/31/2027)
- Technician: [Tech Name]
- Technician contact: (480) 555-0192

We understand Mercury's Smart Home Water Protection program offers a 7% discount on the water-damage peril portion of the Reyeses' homeowner premium, and that the Moen Flo is on Mercury's approved device list. We respectfully request that the discount be applied effective the Reyes policy's current billing cycle or next renewal, per Mercury's standard application policy, and that written confirmation be sent to the policyholders at the address on file.

Please let us know if Mercury requires any additional documentation beyond this letter and the attached materials.

Attachments: Moen Flo install certificate with serial number, device placement photo, Desert Valley Plumbing invoice #[invoice], Desert Valley Plumbing AZ ROC license copy

Thank you,

[Shop Owner Signature]
[Shop Owner Name], Owner — Desert Valley Plumbing, LLC

Acknowledged by the policyholder:

Janet Reyes __________________ Date __________
Paul Reyes __________________ Date __________

### Section 6 — 12-month follow-up plan

- **Day 14:** Desert Valley calls the Reyeses to confirm whether the Mercury discount was applied. If not yet applied, offer to resend the cover letter directly to the agent or underwriter contact the agent supplied.
- **Month 6 (October):** Automated SMS from the shop: "Hi Janet — it's been about 6 months since we installed your Moen Flo. Has it alerted on anything or have you had any issues with the app? Just checking in. — Desert Valley Plumbing." No pitch, no upsell.
- **Month 11 (March, before April renewal):** Email 30 days before the Reyeses' Mercury renewal asking them to confirm the discount is still on the policy and reminding them that the snowbird vacation-mode settings may need a tune after they return for the summer. If they've done a remodel or added fixtures during the year, offer a 20-minute sensor-rebalance visit.

---

## Notes for the Shop

- **Do not invent carrier-specific discount percentages.** Every carrier's program is different and changes frequently. The customer's renewal letter or agent email is the source of truth; if the customer cannot produce one, the first action item in the briefing is "email your agent and ask for the specifics in writing." This discipline protects the shop if a customer ever disputes what was promised.
- **The letter to insurer is the differentiator.** Moen, Phyn, and LeakSmart all ship install certificates. A shop-signed cover letter that maps the certificate to the specific carrier's discount requirement is what 90% of homeowners never get from their installer — and it is the thing that actually triggers the discount in the agent's system. Never skip Section 5.
- **Pair with Water Heater Standards Briefing.** A homeowner replacing a water heater is already spending $3k–$6k on plumbing and the tech is already in the mechanical room. Attaching a Moen Flo install to the same trip is a natural upsell with very little incremental labor. The Water Heater Standards Briefing and this skill can be produced together and stapled into the same customer packet.
- **Pair with Membership Plan Drafter (Complete tier).** The Complete tier of a shop's membership plan is a natural home for ongoing smart-leak-device check-ups — firmware updates, battery swaps on point sensors, annual sensor-placement review after remodels. Do not double-charge members for the device install, but the ongoing support becomes a real benefit.
- **Snowbirds and vacation homes are the highest-ROI install.** A home that sits empty for 2–4 months with a failed supply line is the single costliest water-damage claim category in the country. If a customer has a second home, or travels for extended periods, the auto-shutoff capability is the specific feature that prevents the six-figure claim. Frame the recommendation around that use case when applicable.
- **Do not promise an alert response.** The device alerts the customer, and the customer decides what to do. The device does not bring a plumber automatically. Some customers hear "smart" and assume the shop gets the alert — clarify on install day that the customer (and anyone with shared app access) gets the alert, and the customer should then call the shop if the leak is active.
- **Know when NOT to recommend.** A whole-home flow monitor on a home with a poorly tuned well pump cycle or an irrigation system that was never whitelisted will false-alert constantly and drive the customer to uninstall it within 90 days. If the site conditions suggest that risk, recommend the point-sensor package instead (or whole-home with a longer install-day learning-mode visit).
