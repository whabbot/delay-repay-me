# 05 - Portal spike: West Midlands Trains and Avanti claim portals

Date: 2026-10-20. Goal: find out what the claim portals for our target operators (West Midlands Railway, London Northwestern Railway, Avanti West Coast) need, what bot protection they use, and whether the final screen shows the values that will be submitted. That last point decides between the hand-off options B1 (browser extension) and B2 (agent-driven visible browser).

**Method.** Unlike slices 01–04, this spike fetched pages directly with plain HTTP requests from a cloud container. We did not log in, submit anything, or try to get past any challenge. We read the HTML of the WMT guest claim form, and the public JavaScript bundle and config of the Avanti portal. Field lists and screen text come from that source code, not from clicking through a live claim. The next step, a walk-through with a real past journey, still has to be done in a normal browser.

## 1. Summary

- **Both portals run on shared white-label platforms**, each covering several operators:
  - **West Midlands Railway and London Northwestern Railway** use **Tracsis Travel Compensation Services**' platform at `<operator>.delayrepaycompensation.com`. The footer reads "© Copyright 2026 Tracsis Travel Compensation Services Ltd". The same platform also serves **Greater Anglia** and **c2c**. A `chiltern.` subdomain exists too, but its page didn't render as a claim form, so Chiltern is unconfirmed. The `scotrail.` subdomain redirects to ScotRail's own site.
  - **Avanti** uses a separate platform, an Angular single-page app with the release tag `wcr-smart-repay`. Its own config lists the claim portals for **GWR, Hull Trains, TransPennine Express, South Western Railway, Avanti and Lumo**.
  - So **two integrations would cover roughly ten operators**.
- **Both portals end with a review screen before Submit**, so the values are visible at the end:
  - WMT has a **"Confirm your claim"** tab with summary boxes for your details, journey (stations, times, reason), ticket details and compensation details. Then come a visible reCAPTCHA v2 checkbox and the Submit button.
  - Avanti has a **"Review claim details"** step ("Please review the provided claim information to ensure it is correct"), which shows journey, ticket and compensation details plus the award amount. An invisible reCAPTCHA fires when Submit is clicked.
  - Under the rule we agreed, this points to **B2**.
- **The CAPTCHA sits exactly at our hand-off point.** On both portals the reCAPTCHA is attached to the final Submit, so the person has to do the last step. That matches the "draft, then the passenger submits" design.
- **Bot protection:** both portals sit behind Cloudflare.
  - The **portal** hosts (`*.delayrepaycompensation.com`, `delayrepay.avantiwestcoast.co.uk`) loaded normally with no challenge.
  - WMR's and LNR's **main websites** (`westmidlandsrailway.co.uk`, `londonnorthwesternrailway.co.uk`) returned a Cloudflare **managed challenge** to our cloud container. That includes WMR's terms-and-conditions page and robots.txt, which we therefore couldn't read.
- **The WMT portal does its own train and ticket lookups.**
  - Journeys are chosen from a list of trains identified by Darwin `RID`s (the run ID that Darwin, and so HSP, uses for each train).
  - Tickets are looked up by reference, and the portal reports whether the ticket was found and whether it has been claimed before.
  - So our delay check must use the same train identity as the portal, and the claim pack should give the RID.
- **The claimant chooses the delay band themselves** on WMT (15+ / 30+ / 60+ / 120+ minutes, or strike action), and the delay type (delayed, cancelled, didn't stop). This is where verified delay data adds value. The tool says which band the evidence supports, and shows its source.

## 2. West Midlands Trains (WMR + LNR): Tracsis platform

| Item | Finding |
| --- | --- |
| Claim URL | `https://westmidlandsrailway.delayrepaycompensation.com/index.cfm?action=myclaims.add` (LNR: `londonnorthwesternrailway.` subdomain) |
| Platform | Tracsis Travel Compensation Services. ColdFusion app (`index.cfm`), behind Cloudflare and an AWS load balancer |
| Other operators on it | Greater Anglia and c2c (confirmed: claim form with the Tracsis footer). Chiltern: subdomain exists, page didn't render as a form. ScotRail: subdomain redirects to its own site |
| Account | Guest claims allowed. Afterwards you can turn the claim into a "My Delay Repay" account by setting a password, and logged-in users get saved details |
| Flow | One page with tabs: **Personal details → Journey details → Ticket details → Compensation details → Confirm** |
| Journey fields | Date of journey, scheduled departure time (hour and minute), boarding and destination stations, then "Select your journey" (a list of trains with RIDs). Then delay length (15+/30+/60+/120+ or strike), delay type, missed connection, multiple passengers, multiple tickets |
| Ticket fields | Paper or e-ticket. "Digital tickets with a QR code" vs "All other tickets". Ticket number or UTN, collection ref, smartcard no., start and end stations, valid from and to, cost, class. Up to about 7 tickets per claim |
| Ticket evidence | File upload: `image/*` or PDF. Barcode-picture upload is enabled; automatic UTN extraction from the barcode is switched off for WMR |
| Ticket lookup | The portal searches for the ticket. Messages include "found and has not been used for a claim previously", "found and has been used for a claim previously" and "Sorry, we could not find your ticket" (then it asks for more information) |
| Compensation | Bank transfer (sort code and account), IBAN/SWIFT, card (via a Global Payments hosted page in an iframe), Amazon Pay, Gift Aid / charity option |
| Final screen | "Confirm your claim": summary boxes for details, journey, ticket and compensation. Terms text includes a Fraud Act 2006 warning. reCAPTCHA **v2 checkbox**. Submit button |
| After submit | Claim reference number shown on screen, "process within 24 hours … up to 10 working days" |
| Terms | The submit text links to `westmidlandsrailway.co.uk/terms-and-conditions` (LNR: `londonnorthwesternrailway.co.uk/terms-and-conditions`). The page is the same for both: WM Trains Ltd's website terms. They were read from text pasted from a normal browser, and are covered in section 2a below |

## 2a. WM Trains Ltd terms and conditions (WMR and LNR)

Source: https://www.westmidlandsrailway.co.uk/terms-and-conditions and https://www.londonnorthwesternrailway.co.uk/terms-and-conditions, read on 2026-10-20 from text pasted from a normal browser. The two pages are identical apart from the brand name. The claim form's Submit text says you agree to "the terms and conditions of the Delay Repay scheme", but it links to these **website** terms. No separate Delay Repay scheme terms are linked. The scheme rules themselves are in the Passenger's Charter and the National Rail Conditions of Travel.

**There's no clause on bots, scraping, automated access or third-party claims.** The clauses that matter for this project:

| Clause (short quote) | Relevance | How we stay inside it |
| --- | --- | --- |
| Acceptable use: you will not "use any software, routine or device to interfere or attempt to interfere … with the operation or functionality of this Web site" | The clause is about *interfering* with the site, not about using software at all. Filling the form in your own browser doesn't stop the site working. | Fill the form only. Never get around validation, the reCAPTCHA, or the portal's own ticket and journey checks. |
| Acceptable use: you will not "deface, alter or interfere with the front end 'look and feel' of this Web site" | **The one that matters for design.** A browser extension or agent that adds panels or overlays to the portal page could arguably "alter the look and feel". | Never add UI to the portal page. Show the evidence in a separate window, side panel or extension pop-up, never inside the page. |
| Acceptable use: no action that "imposes an unreasonable or disproportionately large load" | Only bulk or repeated automated traffic would hit this. | One claim at a time, at a person's pace. Don't poll or crawl the portal, and don't use its lookup APIs as a data source: delay data comes from HSP. |
| Acceptable use: no attempt to "obtain unauthorised access" | | Use only your own details and your own session. Never store or share portal passwords. |
| Proprietary rights: no copying or publishing of site material "or the underlying software code"; personal non-commercial copying allowed | Our public repo must not contain the portal's code or assets. | Portal HTML and JS read during the spike stayed in a local scratch folder. The repo only records facts about the form (field names, step order) and short quotes. |
| Links: "You may only link to this Web site with Our express written permission" | Strictly read, this covers deep links in the claim pack and docs. In practice Trainline, Train Badger and others link to these forms, and the claim form itself is on a Tracsis domain. **Low risk.** | Keep links to what's needed: one link to the claim form per claim pack. |
| Booking terms: "The National Rail Conditions of Travel entitle Customers to the same levels of compensation or refund entitlements regardless of where they purchase their ticket." | Confirms that TrainPal tickets have the same compensation rights as tickets bought direct. (This is in WMR's own Trainline-run booking terms, which otherwise don't apply to TrainPal purchases.) | Not applicable |

The claim form also warns that knowingly submitting a fraudulent claim may be an offence under the Fraud Act 2006. This is another reason the tool only drafts claims for journeys it can tie to a real ticket and checked train data, and why a person makes the declaration by pressing Submit.

## 3. Avanti West Coast: `wcr-smart-repay` platform

| Item | Finding |
| --- | --- |
| Claim URL | `https://delayrepay.avantiwestcoast.co.uk/en/` |
| Platform | Angular single-page app (release `wcr-smart-repay`). API under `/api`. Its config lists the claim portals for GWR, Hull Trains, TPE, SWR, Avanti and Lumo (`tocDrUrl`) |
| Account | Login and registration flow (email verification code). Earlier research says tickets bought elsewhere need a portal account; confirm on a walk-through |
| Flow | **Your details → Journey → Ticket → Compensation → Review → Confirmation** |
| Rules in config | `minDelayDuration: 15`, journey search window from 15 to 30 minutes, one ticket image per ticket, claim types `DELAY_REPAY` and `PREAPPROVED` (automated) |
| Compensation | Bank transfer, card, charity, National Rail voucher |
| Final screen | "Review claim details": shows journey, ticket and compensation details plus the award amount, then Submit. **Invisible reCAPTCHA** that runs on the Submit click |
| Terms | Avanti's website terms contain **no clause on automated access or scraping**. Content use is limited to "your own personal, non-commercial use". The portal's own terms of use weren't separately read |

## 4. What this means for the hand-off

| Option | Fit with what we found |
| --- | --- |
| **A. Claim pack (copy and paste)** | Works on the phone. WMT's form has a lot of conditional fields, but a pack ordered tab by tab (with the RID / train choice, delay band, ticket reference and ticket image) keeps it manageable. |
| **B1. Browser extension** | It would work: both portals are ordinary web forms, and the extension would run in the person's own browser behind Cloudflare. On phones it needs Firefox for Android or Safari on iOS. Per-portal selectors are needed for both platforms. |
| **B2. Agent-driven visible browser** | **Viable, and preferred under our rule**, because both portals show a review screen before Submit. The agent fills the tabs or steps and stops at Confirm / Review. The person checks the portal's own summary alongside our evidence, ticks the reCAPTCHA (WMT) and clicks Submit. Risks: reCAPTCHA may give an automated browser harder challenges, and Cloudflare could start challenging. Desktop only. |

## 5. Still to do

1. **A walk-through with a real past WMT journey** in a normal browser, stopping before Submit. Check:
   - the conditional fields for a TrainPal e-ticket (QR code vs ticket number), and whether the portal finds TrainPal tickets;
   - what the Confirm summary actually shows.
2. ~~Read WMR's terms and conditions.~~ Done, see section 2a.
3. **Read the Avanti portal's own terms of use**, and confirm the registration requirement for tickets bought elsewhere.
4. **Check whether HSP's RIDs match the portal's train list** for the same journey. Every train in the portal's "Select your journey" list is identified by its RID.
5. **Rules on which operator to claim from.** WMR says to claim from the operator whose train was delayed, and allows one claim per journey. This matters on routes where LNR and Avanti overlap (e.g. Birmingham–Euston), where the ticket may be valid on either.

## 6. Other notes

- **Train Badger** (`trainbadger.app/delay-repay/west-midlands-railway`) turned up in search as a Delay Repay tool we hadn't seen before. Not investigated.
- Tracsis, which runs the WMT, Greater Anglia and c2c portals, is the company that bought and later wound down Delay Repay Sniper (see `03-independent-tools-and-analogues.md`).

## Sources

- WMR claim form (fetched directly): https://westmidlandsrailway.delayrepaycompensation.com/index.cfm?action=myclaims.add
- LNR, Greater Anglia, c2c claim forms (fetched directly): `https://{londonnorthwesternrailway,greateranglia,c2c}.delayrepaycompensation.com/`
- Avanti claim portal and config bundle (fetched directly): https://delayrepay.avantiwestcoast.co.uk/en/
- Avanti Delay Repay page: https://www.avantiwestcoast.co.uk/help-and-support/delay-repay
- Avanti website terms: https://www.avantiwestcoast.co.uk/about-us/Policies-and-Procedures/Terms-and-Conditions
- WMR Delay Repay pages (via search; the site challenges the container): https://www.westmidlandsrailway.co.uk/delay-repay, https://www.westmidlandsrailway.co.uk/contact-us/frequently-asked-questions/delay-repay-faqs
- LNR Delay Repay page (via search): https://www.londonnorthwesternrailway.co.uk/about-us/delay-repay
- Train Badger (via search): https://trainbadger.app/delay-repay/west-midlands-railway
