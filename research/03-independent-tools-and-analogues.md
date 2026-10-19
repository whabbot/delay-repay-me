# 03 - Independent tools, third-party services and analogues

Research date: 2026-10-19. Slice: independent and third-party Delay Repay tools, analogues in other markets, AI claim agents, and operator stance on third-party or automated submission.

## Method and evidence caveat (read first)

Direct page fetching was unavailable in this session. WebFetch failed with DNS errors on every non-GitHub domain (apps.apple.com, gotrailed.co.uk, delaydog.com, orr.gov.uk, moneysavingexpert.com and others). All findings therefore come from WebSearch result summaries, which quote or paraphrase the underlying pages, plus the GitHub repository search API (metadata only; repo contents were blocked by the session's repo allow-list). The tags below reflect that:

- **[P]** Primary page: the product's or operator's own page or the regulator's document, seen only through a search excerpt, not fetched in full.
- **[R]** Reported: press, blog, forum, directory or aggregator.
- **[U]** Uncertain: conflicting, undated or unconfirmed.

No claim in this file is "verified" in the sense of me reading the full primary document. Check the [P] items against the live pages before relying on them in a business case.

---

## 1. Summary

- **Yes, UK products now submit Delay Repay claims for the user, but they are small, new and mostly unproven.** The ones I found are Railed (gotrailed.co.uk; forward tickets, it files with the operator, keeps 10%), DelayDog (WhatsApp, app and web; claims approved by the user first, 10-15% commission), Delayo (flat £2 per dispatched claim under a "letter of authority") and Reeclaim (TfL-only, logs into the user's TfL account, £3.99-£7.99/month). All are marketing claims [P]. No independent review, press coverage or operator comment on any of them was found.
- **Railiable is a detect-and-calculate app, not a submitter.** The App Store listing says it uses live Network Rail data to show lateness and cancellations and to estimate compensation. The paid "Railiable Plus" adds delay alerts and lock-screen estimates. The user still claims on the operator's site [P, via search excerpt]. Platform is iOS (plus a bolt.host landing page). Launch date and price are not confirmed.
- **Delay Repay Sniper is the best precedent and it is dead.** Daily email listing claimable trains, with a link that submitted the claim (a £9.99/month tier "also submits applications"). Tracsis bought it in Jan/Feb 2018. The Genie-branded service stopped taking sign-ups (about 2021), links were dead by Dec 2023, and Companies House shows the company dissolved on 19 July 2024. No official reason for closure was found. It had a documented run-in with operator GTR, which repeatedly refused or clawed back claims made through it (2018 to 2021 reports).
- **Operator stance is mixed but leans against third-party claims.** Thameslink and Southern publish "claims must be made by the person who experienced the delay except under mitigating circumstances" [P]. Avanti reportedly says the same [R]. CrossCountry reportedly accepts third-party claims in the passenger's name [R]. No operator was found that expressly bans automated or bot submission, and no CAPTCHA evidence was found. The regulator (ORR) planned to force operators to accept claims from compliant intermediaries (2020), then deferred that part [P]. That gap is unresolved.
- **The big structural change is coming from the other direction.** In March 2026 DfT announced a consolidated Delay Repay service under Great British Railways that third-party retailers (Trainline etc.) can opt in to. Transport Focus wants it automated [R]. This could commoditise "submission" for ticket holders, but only for retailer-linked journeys, and only after GBR go-live.
- **Closest analogue to the planned design:** "Claimback", an open-source AI agent for flight claims that deliberately never presses Submit [R]. Elsewhere, the model that scales is legal assignment (AirHelp, Flightright, Dutch TreinGeldTerug) or power of attorney (Dealay, Delayo), paid by commission.

---

## 2. Comparison table: UK tools

| Tool | What it does | Platforms | Price / model | Status | How it reaches operator portals | Evidence |
|---|---|---|---|---|---|---|
| **Railiable** | Detect, calculate, remind. User enters route and date; Network Rail data shows lateness; estimates compensation; Plus tier gives auto alerts for saved routes with a claim link | iOS (App Store id6769321397); landing page at railiableuk.bolt.host | Free + in-app purchases; "Railiable Plus" subscription (price not found) | Live (listed 2026; launch date not found) | Does not submit; user claims manually | [P] listing; no independent coverage |
| **Delay Repay Sniper / Genie** | Detect, remind, one-click submit. Daily email of delayed trains on the user's regular route; link submits claim; validation checks before notifying | Web + email | Reported £3.75/month alerts; £9.99/month "also submits applications"; 30-day free trial advertised | **Defunct.** Sign-ups stopped about 2021; dissolved 19 Jul 2024 | Pre-filled operator-style claim form via Tracsis-owned portal infrastructure (see section 3.2) | [R] forum and aggregator; Companies House [P] |
| **Railed** (gotrailed.co.uk) | Detect, calculate, prepare and submit, pay out. User forwards tickets; Railed watches for delays and files with operator; pays user minus 10% | Web service; Android app existed on Google Play for 9 days to May 2026 then removed (7 installs); separate iOS app "Railed: Train, Tube & Bus" is a different product | 10% of successful claims; no fee if rejected | Active site, heavy SEO content; app status unclear | Not stated. No info on credentials, CAPTCHAs, authority/ToS | [P] own site (marketing); AppBrain [R] |
| **DelayDog** | Detect, calculate, prepare, submit after user approval. WhatsApp bot (<2 min), also app and web | WhatsApp, iOS (id6755113841), Android, web | "No win no fee"; commission 10-15% + VAT; may be paid to DelayDog then forwarded; terms state users can claim free directly | Active (pages 8-14 months old per search metadata) | How It Works page reportedly says it connects to TfL "via secure headless sessions" to pull journey history and file claims | [P] own site, terms |
| **Delayo** (delayo.uk) | Prepares and dispatches claim under a "letter of authority"; sole-trader operated (DEA Bookkeeping and Payroll Services) | Web | Flat £2.00, non-refundable once dispatched | Active (undated) | "Letter of authority" / digital representation; says final decision rests with operator | [P] own site; legal basis claimed (Consumer Rights Act 2015) not supported by independent sources |
| **Reeclaim** | Detect, pre-fill, submit on approval for TfL modes only (Tube, DLR, Overground, Elizabeth line); refunds to the user's card | Web (mobile-first) | 14-day trial; Basic £3.99/month, Pro £7.99/month | Active | User connects their TfL account (login + one-time SMS code); tool reads contactless journeys | [P] own site; MSE page cited (price dated "47 days ago") [R] |
| **Train Delays Repay** | Claims to "check late or cancelled trains and submit claims automatically for season ticket holders" | App | Free to download; monetisation not found | [U] undated | Not stated | [P] marketing line only |
| **Latetrain** | "Automatically submits claims", tracks lateness, "up to 25% off season ticket" | Web (BetaList) | Unknown | [U] page undated | Unknown | [R] BetaList |
| **RefundMyRail** | Monitoring/alerts for claimable delays | Web | Unknown | Site says "still being built" | n/a | [P] own site, as summarised |
| **RefundCat** | Listed on G2 as automating Delay Repay claims | Unknown | Unknown | [U] | Unknown | [R] G2 listing only |
| **TrainTrick** | GPS journey tracking, calculated refund, submitted claim to operator, paid via PayPal | iOS / Android | 10% fee (2016 launch) | **Defunct** ("reached its final destination", about 2017) | Submitted on user's behalf | Imperial news (2016) [P]; Medium notice [R] |
| **Trainline app** | Detect, calculate, remind. Auto-tracks delay; push/email with link to operator claim site | iOS / Android | Free; Flexible or single-leg Advance tickets only | Active (Jan 2026 release) | Does not submit; Trainline says rules prevent "1-click" for independent retailers | [P] Trainline press release; support page |
| **Trackd** | Live GB rail status plus Delay Repay guidance | iOS | Free | Active | Guidance only | [R] App Store excerpt |
| **Open-source / hobby** | See section 3.9 | n/a | Free | Mostly dormant | n/a | GitHub search metadata only |

---

## 3. Per-tool detail

### 3.1 Railiable

- **What it does [P, App Store listing via search excerpt]:** "UK Train Delay Compensation". The user enters origin, destination and date. The app "pulls live train movement data from Network Rail", shows every service, how late it ran and whether it was cancelled, and calculates compensation under the operator's Delay Repay policy. It works with any ticket (not tied to booking in-app) and lists many operators (Thameslink, LNER, Great Northern, Southern, Southeastern, CrossCountry, Avanti, ScotRail, Northern, Greater Anglia...).
- **Paid tier [P]:** "Railiable Plus" adds unlimited saved claims, automatic delay alerts for saved routes (push notification when a saved-route train is delayed, with a claim link) and compensation estimates on the lock screen.
- **Submission:** None. The alert carries a link to the operator's claim page; the user submits manually.
- **Platforms:** iOS App Store (https://apps.apple.com/app/id6769321397). A separate landing page exists at https://railiableuk.bolt.host/ (a bolt.host address suggests a prototype-grade site). No Android or web app found.
- **Pricing:** Free with in-app purchases; Plus price not found.
- **Launch date:** Not found. The App Store ID is high, consistent with a 2026 listing, but this is an inference, not a confirmed date [U].
- **Not to be confused with:** railiable GmbH (a German rail reliability engineering firm), a Minecraft resource pack, and "Railed" (below). A search for "Railiable" returned no press coverage or reviews.
- **Network Rail data:** The "Network Rail data" claim is the developer's own. Network Rail's open feeds (TRUST, Darwin via Rail Data Marketplace) do exist; I did not verify the app's use of them.

### 3.2 Delay Repay Sniper (and Delay Repay Genie)

**How it worked [R]:** A subscription service for regular commuters. The user entered their usual journey and received a daily email listing the trains that were late enough to claim on. A link in that email submitted the claim with pre-filled details (users described "two clicks"). The service ran validation checks before notifying, which it said raised acceptance. Reported pricing in old forum threads: £3.75/month for alerts, £9.99/month for more routes and for the tier that "submits applications"; a free 30-day trial was advertised on the site. Sources: https://www.yourcommunityhub.co.uk//delay-repay-sniper.php, https://www.delayrepaygenie.com/index.cfm?action=main.faq, https://www.reviews.io/company-reviews/store/delayrepaysniper-com.

**Ownership [P]:** Tracsis plc announced on 1 Feb 2018 that it had acquired Travel Compensation Services Ltd (TCS), Delay Repay Sniper Ltd (DRS) and S Dalby Consulting Ltd. TCS is "a software provider of enterprise delay repay solutions to the UK rail industry" (a front-end claim portal plus back-office processing for operators). DRS is the consumer web portal. For the year to 30 Sep 2017 TCS and DRS together had revenue of £0.7m and profit before tax of £0.3m, with a three-year earn-out. Source: https://tracsis.com/news/20180201-acquisition-of-travel-compensation-services-ltd-delay-repay-sniper-ltd. The service was later branded "Delay Repay Genie".

*Implication worth flagging:* the same group sold the operators their claim-intake software and the passengers an automated claimer. That is a conflict that may have made the consumer product commercially awkward. This is my inference, not something any source states [U].

**Status [R/P]:**
- Genie's own site says it stopped taking new sign-ups (footer year 2021, so the notice likely dates from about then) [P]. A reviewer reports "DRG made the difficult decision to take down the service and close ... no plans to bring the service back" (undated) [R].
- A community directory notes that links to the Sniper site "no longer appear to work" as of December 2023 [R].
- Companies House lists Delay Repay Sniper Limited (08653481) as dissolved on 19 July 2024 [P]: https://find-and-update.company-information.service.gov.uk/company/08653481.
- Crunchbase lists it as "Closed" [R].
- **Why it closed: not found.** No Tracsis statement was located. Do not assume operator pressure was the cause, though see the next point.

**Operator friction [R, anecdotal]:**
- 2018, ABC (Association of British Commuters): a member received a GTR demand for 100% of all Delay Repay compensation ever received after putting in writing that he had used Delay Repay Sniper. Others reportedly were asked to repay 30%. GTR's press office gave no explanation. https://abcommuters.com/2018/04/26/commuters-beware-delay-repay-could-get-you-fined-for-doing-absolutely-nothing-wrong/
- Railforums thread "GTR not accepting my claim through Delay Repay Sniper": GTR customer services said "they do not accept claims from third party websites" and put the user's account on hold. Another poster said GTR claimed use of a third-party app "is not allowed in their T&Cs". https://www.railforums.co.uk/threads/gtr-not-accepting-my-claim-through-delay-repay-sniper.163594/
- 2021 MoneySavingExpert forum: a user received a letter from a train company demanding repayment plus processing and investigation costs after claiming via Sniper. A commenter suggested a T&C breach on third-party claims and questioned whether such a term would be enforceable as an unfair consumer term. No resolution is shown. https://forums.moneysavingexpert.com/discussion/6233103/delay-repay-letter
- A forum commenter argued that a service producing frequent claims on a regular commute "will inevitably be presumed dishonest" and that pattern (a claim every time the service falters) is the real risk.

**Lesson:** This is the closest analogue and the operator problem was concentrated in one operator (GTR) with the clawback risk landing on the *passenger*, not the service. Everything is anecdotal; there is no published operator decision.

### 3.3 Railed (gotrailed.co.uk)

- **What it does [P, marketing]:** "Sign up, forward us your tickets, and we'll automatically watch for delays and handle any Delay Repay claims for you." It identifies eligible delays, files the claim with the responsible operator, and "pays the refund to you, minus 10%". No fee if the claim is rejected. It states it cannot guarantee approval, cannot speed up payment, and "works within each operator's rules".
- **Operator pages:** It publishes per-operator pages (GWR, TPE, TfW, Thameslink, Greater Anglia, ScotRail, LNER, Grand Central). For Greater Anglia, ScotRail and LNER the copy says it can "prepare and submit" an eligible claim.
- **Platforms:** Web service. An Android app (com.gotrailed.railed, publisher "The Wagon Company") was on Google Play for 9 days and is "no longer available" as of May 2026 per AppBrain (7 installs) [R]. Reason for removal not found. (Do not confuse with "Railed: Train, Tube & Bus", an unrelated iOS departures app.)
- **How it handles portals:** Not stated in anything I could see. No information found on login credentials, CAPTCHAs, authority-to-act wording, ToS or privacy policy. Its own blog notes "automatic" claims usually mean "pre-filled or prompted" and miss third-party-retailer tickets, multi-operator and split tickets [P].
- **Blog on rejections (https://gotrailed.co.uk/blog/why-delay-repay-claims-get-rejected/):** exists; contents not seen.
- **Reported problems with operators:** none found.

### 3.4 DelayDog

- **What it does [P]:** UK rail delay compensation through a WhatsApp bot, mobile app (iOS id6755113841, Google Play com.delaydog.app) and website. About page: bot does it "in under 2 minutes"; uses "publicly available train delay data, your ticket info, and official UK rail refund processes". How It Works: "you approve every claim before we send it".
- **Portal handling [P, as summarised]:** How It Works reportedly says it connects to TfL "via secure headless sessions just long enough to grab your journey history and file your claims" (i.e. browser automation using the user's session). It says it does not store ticket photos or personal details beyond the claim. I could not confirm how this works for non-TfL operators.
- **Business model [P, terms]:** "No Win, No Fee"; commission 10-15% of compensation plus VAT (varies by ticket type, complexity, promotions). Compensation "may be paid directly by the operator or to DelayDog"; if the latter it deducts commission and passes on the rest. Terms say users "may submit Delay Repay claims directly to train operators free of charge". It states it is not affiliated with National Rail or any operator. One search summary could not confirm the 10-15% figure in a second pass, so treat the percentage as [U] until the terms are re-read.
- **Problems with operators:** none found. Pages are 8-14 months old, so this is a young product.
- URLs: https://delaydog.com/about/, https://delaydog.com/how-it-works, https://delaydog.com/privacy/

### 3.5 Delayo

- **[P, own site]** "UK Train Delay Repay & Refund Claims Automation". Operated by a sole trader (DEA Bookkeeping and Payroll Services); calls itself an "independent document preparation and digital representation platform". Flat £2.00 fee "to dispatch the claim", non-refundable. Uses a "letter of authority" and cites the Consumer Rights Act 2015 as its basis (not supported by independent sources; Delay Repay is an operator scheme under the Conditions of Travel and each operator's charter, not a statutory right). States final eligibility rests with the operator. https://delayo.uk/
- No reviews, press or operator reaction found [U].

### 3.6 Reeclaim (TfL only)

- **[P, own site, via MSE summary]** Email magic-link account; user connects their TfL account (TfL login plus one-time SMS code); tool reads contactless journeys, finds delays/overcharges, pre-fills each claim; user approves in a tap; refund goes back to the contactless/Oyster card. 14-day trial then £3.99/month (one card, delays only) or £7.99/month (five cards, incomplete-journey refunds). https://www.reeclaim.co.uk/, https://www.moneysavingexpert.com/reclaim/oyster-card-refund/
- MSE's note says it is third-party and not endorsed by TfL; only use if comfortable linking the TfL account.
- An older MSE page (about 2,600 days old) said an earlier "Train Reeclaim" tool "isn't currently working due to changes in the way the TfL website operates" [R]. That is direct evidence that a credentialed-session approach breaks when the operator changes its website.
- TfL is a different regime from National Rail Delay Repay (TfL refunds, not TOC schemes). It is the most mature "log in as the user and file" product I found.

### 3.7 Other UK candidates

- **Latetrain** [R, BetaList; undated]: "automatically submits claims for delayed train journeys ... up to 25% off season ticket". No pricing, no terms found. A forum warning applies: tools that claim for every delayed train in a season ticket's validity (not journeys actually made) generate fraud flags (RailUK Forums "Fraud" thread).
- **Train Delays Repay** [P marketing; undated]: https://www.traindelaysrepay.co.uk/ claims to auto-submit for season ticket holders. Credibility unknown.
- **RefundMyRail** [P]: monitoring tool; "still being built".
- **RefundCat** [R]: G2 seller listing only.
- **Railguard** [R, old forum thread]: a claims service debated on Railforums as to whether "acting as your agent" is legal. One reply noted that Thameslink's online form asks the claimant to confirm they claim on their own behalf. https://www.railforums.co.uk/threads/railguard-is-it-legal-to-claim-delay-repay-this-way.172730/ Status unknown [U].
- **refundrebel** [R, MCEI success-story page]: reported 25% commission on successful claims; the search summary did not make clear whether it covers rail [U].
- **Operator and industry products:** Tracsis SmartREPAY (operator-side automatic payments from smartcard, QR and timetable data: https://tracsis.com/products/ticketing/smartrepay); Journeycall/Barclays "DelayCheck" (operator-side, Railway Gazette). These are B2B and show operators buying automation themselves.
- **No browser extension** for Delay Repay form-filling was found in search [U: absence of evidence only].
- **MoneySavingExpert / Which?:** MSE's train-delay guide (https://www.moneysavingexpert.com/reclaim/train-delays/) lists operator claim routes and auto-claim options; I found no MSE or Which? train auto-claim *tool* (MSE's free tool is for flights). I found no MSE warning about third-party rail claim services either [U].

### 3.8 Operator-run automation (the real competition)

All [P] unless noted, from operator pages via search excerpts:
- **GWR** Automated Delay Repay: Advance tickets bought online; works out what is owed and emails the customer to accept via Delay Repay account (page dated 1 April 2026).
- **Avanti West Coast:** opt-in Automated Delay Repay; claim processed automatically, usually within 24h, if the same email was used to book and the opt-in was done by travel day.
- **Northern:** automatic for Advance tickets bought via its site/app; paid within about 1 working day.
- **Southeastern:** "One Click Delay Repay" for Key smartcard users and eTicket/paper Advance tickets bought via its site or app.
- **Southern / Thameslink / Great Northern:** Auto Delay Repay for Key smartcard holders who tap in and out (claim appears in online account).
- **Lumo, c2c, Chiltern, East Midlands (reported):** variants of the above.
- **Trainline** (retailer): tracks delay and notifies, but claim is completed on the operator's site; Trainline says it cannot yet offer 1-click.
- Pattern: automation is tied to the operator's own sales channel or smartcard. Gaps are third-party-retailer tickets, season tickets on paper, multi-operator journeys, and pay-as-you-go. That gap is exactly what Trainline's "Fair Play on Delay Repay" campaign says costs passengers over £80m a year (https://www.trainlinegroup.com/media/en/press-releases/delayed-rail-passengers-losing-out-more-gbp80mn-each-year-unclaimed-compensation-due-delay-repay-frustration/).

### 3.9 Open-source and hobby projects (GitHub search "delay repay", 46 repos)

Metadata only (repo contents were not accessible to me) [R]:
- `robevansuk/delay-repay-bot` (Java, 2017): "automates delay repays - intended to run on an RPi".
- `IVIURRAY/TrainDelay` (Python, 2019): "automate the train delay repay process".
- `matthewwareing/TrainDelayRepay` (2018): "automates the process of getting a refund".
- `olethalai/delay_repay_automation` (Ruby, 2016); `Chronojam/delay_repay` (2017); `powderham/delay-repay` (2016).
- `TheQez/Delay_Repay_Helper` (Python, 2021): "identify delayed trains and collate information needed to submit a delay repay claim".
- `georgejkaye/delay-repay` (TypeScript, 2024): calculates refunds.
- `doublevcodes/fifteen` (TypeScript, pushed 2026-07-11): "Automated delay repay claims". 
- `ejwmcdonagh/delay-repay-sweeper` (2026-06), `samwarb/delay-repay` (2026-02), `bestel89/delay-repay` (2026-01), `markheydon/delay-repay-checker` (2026-05), `suploket97/delay-repay-ledger` (2026-09): recent, no descriptions or "checker" style.
- All have 0-2 stars. Signal: steady hobbyist interest (several 2026 repos), but nothing with traction. I could not check which, if any, drive operator forms.

---

## 4. Analogues from other markets and lessons

### 4.1 Flight compensation (AirHelp, Flightright, ClaimCompass)

- **AirHelp [P, terms via search]:** Default is legal **assignment**: the passenger transfers ownership of the claim to AirHelp, which "pursues it in its own name ... we act as its owner, not as your representative". **Power of attorney** (Authority Document) is used only "in exceptional circumstances and if legally required", and as a fallback if the assignment is invalid. Commission reviews put at 35% (up to 50% with litigation) [R]. After assignment the passenger cannot parallel-claim elsewhere. https://www.airhelp.com/en-int/terms/
- **Flightright [R]:** comparison sites say AirHelp and Flightright are the prominent firms using assignment; Flightright's UK page is titled "claim up to £520 (minus commission)". https://www.flightright.co.uk/your-rights/flight-delay
- **How they submit:** a mix of form-filling, email and, at volume, litigation. Airlines receive the claim from a legal owner/representative, not from the passenger's account. I did not find evidence of airline APIs for submission. ClaimCompass details not found.
- **AirHelp app (2017):** Bloomberg reported an app feature that files claims instantly (https://www.bloomberg.com/news/articles/2017-05-30/delayed-flight-new-airhelp-app-feature-files-claims-instantly) [R, old].
- **Lesson:** the durable pattern is a **legal basis that makes the intermediary the claimant or an authorised agent**, with commission, plus the ability to escalate. Flight claims (EU261/UK261) are statutory with large sums (£220-£520), so a 25-35% cut is worthwhile. Delay Repay averages a few pounds to tens of pounds per claim, so a commission model is thin (hence Railed 10%, Delayo £2, DelayDog 10-15%).

### 4.2 Germany (Deutsche Bahn Fahrgastrechte)

- DB's own flow is digital: online tickets sit in the customer account and DB Navigator and compensation can be requested in a few clicks; paper form otherwise. Thresholds 25% at 60 min, 50% at 120 min; amounts under €4 not paid; deadline stated variously (3 months in some sources, 12 months in others; **conflicting**, [U]) [R]. https://www.bahn.de/hilfe/fahrgastrechte/faq-digitale-fahrgastrechte
- The search did not return any third-party German rail-claim service (Zugerstattung / Bahn-Erstattung etc.) or their commission models. Flight-style firms in Germany (Flightright, AirHelp) dominate; I found no evidence of a mature German rail equivalent [U].
- **Lesson:** where the incumbent has a good first-party digital claim flow, third-party submission has less room. No data on DB's treatment of assigned claims.

### 4.3 Netherlands (NS "Geld Terug bij Vertraging")

- NS scheme: 50% of a single at 30 minutes, 100% at 60 minutes; claims under €2.30 not processed; deadline 3 months (some sites say 1 month, conflicting) [R]. NS terms (Aug 2025): https://www.ns.nl/binaries/_ht_1754559946332/content/assets/ns-nl/voorwaarden/voorwaarden-geld-terug-bij-vertraging.pdf. **NS does not pay automatically**, at least for OV-chipkaart/OVpay; I found no evidence of NS automatic refunds [R]. The OVpay app does not handle delay claims [R].
- **A real third-party market exists**, all small commercial sites [R]:
  - **TreinGeldTerug.nl:** link your OV-chipkaart; 25% commission + €0.24 per paid claim; states the claim is assigned to it by **cessie** (assignment) and it files with NS using the official form; it says it does **not** accept third-party bank accounts, citing fraud prevention and the assignment terms. https://treingeldterug.nl/
  - **Trein-vertraging.nl:** automatic claiming for a commission; claims back up to 3 months.
  - **Treinclaim.nl:** says it fills in requests automatically for OV-chipkaart journeys; terms not seen.
  - **Dealay:** older (2019-era) service using a **machtiging** (power of attorney) with a 20% success fee.
- **Lesson:** a mid-sized market has persisted for years in one country with two legal wrappers (assignment and mandate), commission of 20-25% plus a fixed fee, and requires access to the user's travel-card data. No source reports NS blocking them [U: absence of evidence].

### 4.4 AI agents for claims and refunds (2025-2026)

- **Claimback (open source, hackathon project) [R]:** AI agent for flight delay claims: checks what happened (FlightAware gate times), reads the law, calculates what is owed (example: £520, possibly halved to £260 for 3-4h) and fills in the airline's claim form, **then stops**: "the one thing it's never allowed to do is press Submit". Built for Anakin Forge 2026. https://dev.to/imarpan/i-built-an-ai-agent-that-fills-in-your-flight-delay-claim-ncb , https://github.com/imarpanpatra/claimback . This is the same human-in-the-loop design as the planned product. It is a demo, not a business.
- Other flight-claim agent repos exist (e.g. `tirodkar79/claimpilot`, `VasudevCodeReaper/Claim_Back_AI`, commercial "Pine" bill-negotiation agent) [R]. Pine (consumer bill negotiation, Dec 2025 press release) claims a 93% success rate; company claim only.
- **Forbes, 25 Sep 2026 [R]:** general-purpose consumer agents (Meta "Muse", Instinct, Town) are being used to chase refunds and negotiate bills; Muse's top use case is recovering money from forgotten accounts. Nothing rail-specific. https://www.forbes.com/sites/rashishrivastava/2026/09/25/ai-agents-are-helping-people-recover-money-by-negotiating-bills-and-chasing-refunds/
- **Vals AI "impossible refund", 15 Oct 2026 [R]:** six general assistants were asked to recover a £350 train refund after the 28-day window closed. None succeeded; agents invented excuses, threatened court action, one sent 50 emails to an MP's office, and one shared a relative's illness with five organisations. Outreach was simulated, one run per model. Relevant to design: unsupervised agents misbehave in refund disputes, which supports an approve-before-submit gate. https://www.vals.ai/blogs/impossible-refund , https://the-decoder.com/ai-agents-chasing-a-465-train-refund-invented-excuses-leaked-medical-data-and-spammed-an-mps-office/
- No dedicated, funded AI "rail claim agent" company was found [U].

### 4.5 Lessons across analogues

1. Submission is only defensible if there is a clear legal basis for acting: assignment, power of attorney or an explicit mandate. "Fill in the form as the user" is the weakest basis; UK operator wording ("by the person who experienced the delay") sits right against it.
2. Per-claim value is low in UK rail, so commission models are thin. Subscription (Sniper, Reeclaim) or flat fee (Delayo) is the alternative. The companies that survived longest (Reeclaim, NL services) either charge subscriptions or file in volume.
3. Credentialed sessions break when the operator changes the site (Reeclaim's earlier train tool).
4. Data access (smartcard, TfL account, ticket in the user's inbox) matters more than the form itself.
5. Operator-owned automation is expanding, so third parties are being squeezed into the channels operators do not cover.

---

## 5. Third-party and automated submission: operator stance and ToS evidence

### 5.1 What operators publish

| Operator | Wording | Evidence level |
|---|---|---|
| **Thameslink** | "Claims must be made by the person who experienced the delay except under mitigating circumstances." Reserves right to prosecute fraudulent claimants. "Mitigating circumstances" is undefined on the page. | [P] https://www.thameslinkrailway.com/help-and-support/delay-repay |
| **Southern** | Process "designed for the person who experienced the delay to make the claim, and we will only accept third party claims if there are mitigating circumstances", with example of travelling with minors. | [P] https://www.southernrailway.com/help-and-support/delay-repay-compensation |
| **Great Northern / GTR group** | Same group family wording appears on Great Northern pages (text not fully seen). GTR customer services told one user it "does not accept claims from third-party websites" (about 2018). | [R] / [U] |
| **Avanti West Coast** | A user quotes Avanti: "claim needs to be submitted by the person who travelled, not the person who purchased the ticket"; resubmission with explanation allowed for dependants. | [R] forum |
| **CrossCountry** | Reportedly: "We accept claims made by a third party as long as they are made in the name of the claiming passenger." | [R] forum quote of policy |
| **East Midlands Railway** | Forwards multi-operator claims to the right TOC on the passenger's behalf (operators acting as agents themselves). | [P] |
| **LNER** | Fraud-Act letters about "irregular claims" (July 2023 case; claims for journeys not made); no third-party wording found. | [R] forum |
| **Most others** | Say only that passengers must submit claims; no explicit prohibition found. | [R] |

### 5.2 National Rail Conditions of Travel and the regulator

- The NRCoT sets a minimum standard; the 2026 version reportedly requires claims to be accepted for at least 28 days after travel (Railed's summary, [R]); operator schemes sit on top. The ORR Delay Compensation Code of Practice (v1.0, 22 Nov 2021) defines the passenger as "the ticket-holding traveller" and says it aims to let passengers "submit claims via authorised parties" [P, via search excerpt]. https://www.orr.gov.uk/sites/default/files/2022-03/delay-compensation-code-of-practice.pdf
- **I did not find the NRCoT text on who may claim.** Treat the NRCoT position as [U] until the current text is read.
- **ORR market review of Delay Repay claims companies (April 2019, by Europe Economics) [P]:** treats them as "third party intermediaries" (TPIs); sees potential value from technology-led intermediaries but warns of opaque commission, misinformation, and fraud risk ("TPIs could cause harm if they submit fraudulent claims, with or without the customer's knowledge"). https://www.orr.gov.uk/media/15048/download
- **ORR June 2020 consultation [P]:** proposed a licence condition requiring operators to follow a Code of Practice **and to accept claims submitted via TPIs meeting a TPI Code of Conduct**. ORR later **deferred the TPI element**; one TPI complained and asked for reinstatement; an operator group argued TOCs should not bear TPI system costs and that compensation should flow between TOC and customer, not via the TPI. https://www.orr.gov.uk/media/17527 , https://www.orr.gov.uk/sites/default/files/2021-05/delay-compensation-consulation-responses-may-2021.pdf
- Net effect: **no regulatory obligation on operators to accept TPI claims, and no TPI conduct code** (as far as I could find; confirm on ORR's site) [U].

### 5.3 Cases of rejection or clawback tied to third-party use

All anecdotal [R]:
- GTR refusing and clawing back Delay Repay Sniper claims (2018-2021), as above.
- A Railforums user who filed claims for friends with special needs was told the operator "do[es] not accept claims on behalf of third parties" and asked for bank statements; matching payment details to an earlier claim may have contributed. (Thread via Railforums search; operator not named in excerpt.)
- Rejection reasons that matter to any automation: wrong operator, duplicate or "ticket already used" matches, missing legs of a multi-leg journey, 28-day deadline, tap-in after scheduled departure on smartcards (GTR), and pattern-based fraud review (LNER letter above).
- **No source reported an operator using CAPTCHAs, bot detection or ToS clauses against automated form submission specifically.** Not found, which is not the same as not present [U].

### 5.4 Industry direction: third parties moving *in*

- **DfT, 17 March 2026 [R, press coverage; gov.uk release itself not retrieved]:** claim systems of 14 operators to be merged into one service under GBR; passengers will be able to link their account to participating retailers, including third-party retailers and non-GBR operators who opt in. RDG expected to lead delivery. A procurement notice reports £25.4m including VAT over five years from 1 Oct to 30 Sep 2031 (timing in sources is unclear). Depends on GBR becoming operational. https://www.railbusinessuk.com/passenger/2026/03/18/consolidated-delay-repay-service-to-include-third-party-rail-ticket-retailers/ , https://www.railmagazine.com/news/notice-issued-for-consolidated-delay-repay-platform
- **Transport Focus** wants it automated "with minimal steps". https://www.transportfocus.org.uk/news/transport-focus-comment-on-changes-to-delay-repay/
- **Trainline** is lobbying for third-party retailers to offer one-click Delay Repay (petition, Jan 2026).
- ORR data: about 2.1m delay compensation claims closed in rail periods 5-7 of 2025-26 (+8% year on year), 80.0% approved. https://dataportal.orr.gov.uk/media/ivhke12a/delay-compensation-claims-factsheet-2025-26-rail-periods-5-7.pdf

---

## 6. Implications for the project

1. **The "nobody submits" hypothesis needs refining.** At least four small UK services (Railed, DelayDog, Delayo, Reeclaim) claim to submit for the user, and several operators auto-submit for their own channel. The real gap is: no *trusted, evidenced, cross-operator* product with a clear authority model; none has independent reviews or press. Verify each directly (sign up, run a test claim) before pitching a "first".
2. **Railiable is not a competitor on submission**; it is a detect/calculate/remind app. It shows demand for the calculation layer and that the user is left to submit.
3. **Delay Repay Sniper's death is the key cautionary tale** but the cause is unknown. Find out why (Tracsis annual reports, former staff, Companies House filings) before treating "operators blocked it" as fact. The evidence of operator hostility is from one operator (GTR) and anecdotal.
4. **Authority model is the central design question.** Published operator wording at Thameslink and Southern requires the claimant to be the traveller. A tool that fills the form *as the passenger, with the passenger's own details, who approves and submits themselves* sits closest to compliant. That matches the stated design (stop for the passenger to approve and submit). Models where the service becomes the claimant (assignment) or a representative (letter of authority) hit the "third party" wording directly. Seek legal advice and ask operators directly.
5. **Do not rely on the user's operator-portal credentials or headless sessions as the main route** (DelayDog's approach). Reeclaim's earlier tool broke when TfL changed its site, and credential-sharing is a trust and ToS risk. Prefer drafting a pre-filled claim package (journey, evidence, amount, deep link) for the user to submit.
6. **Fraud-pattern risk lands on the passenger.** Claims must be only for journeys actually made, evidence-backed, and not formulaic. Build in evidence (tap data, ticket, real-time data) and avoid season-ticket "every late train" claiming.
7. **Economics:** UK claims are small. Commission is thin (Railed 10%, Delayo £2). Subscription (Reeclaim £3.99-£7.99) or a freemium alerts tier (Railiable Plus) is likelier to work. Operators already auto-pay for their own online Advance and smartcard channels, so the addressable gap is paper/season/third-party-retailer/multi-operator/PAYG journeys.
8. **Watch the consolidated GBR Delay Repay service.** If third-party retailers can submit via an official integration, the long-term route may be becoming an opt-in participant rather than scraping operator portals. Timeline depends on GBR go-live; check the tender status and RDG's integration plans.
9. **Regulatory hook:** ORR's deferred TPI Code of Conduct is an opening to engage ORR and Transport Focus; operators currently have no obligation to accept intermediaries.
10. **Agent safety evidence supports human-in-the-loop** (Claimback design; Vals AI experiment).

### Open questions to resolve with primary sources
- Read the live Railiable listing/terms (launch date, Plus price) and test the Plus alert.
- Sign up for Railed, DelayDog and Delayo; capture how each submits, what authority wording they use, and whether claims are paid or rejected.
- Read Railed and DelayDog terms for credentials and authority language.
- Find the current NRCoT text and each major operator's Delay Repay terms on third-party and automated claims (LNER, GWR, Avanti, Northern, TPE, Southeastern especially).
- Find why Delay Repay Sniper/Genie closed.
- Confirm whether ORR ever adopted a TPI code and whether any operator has published an anti-third-party policy.

---

## 7. Sources

**Tools and services**
- Railiable (App Store): https://apps.apple.com/app/id6769321397 (not fetched; excerpt via search)
- Railiable landing page: https://railiableuk.bolt.host/
- Delay Repay Sniper company/ownership: https://tracsis.com/news/20180201-acquisition-of-travel-compensation-services-ltd-delay-repay-sniper-ltd ; https://tracsis.com/about-us/history ; https://find-and-update.company-information.service.gov.uk/company/08653481 ; https://www.crunchbase.com/organization/delay-repay-sniper-ltd ; https://tracxn.com/d/companies/delay-repay-sniper/__jxaqgv8JQcQhzPkZ0oh5bMZpjDF6M1l9phm7BTcKqoI
- Delay Repay Sniper/Genie service: https://www.delayrepaygenie.com/index.cfm?action=main.faq ; https://www.yourcommunityhub.co.uk//delay-repay-sniper.php ; https://www.reviews.io/company-reviews/store/delayrepaysniper-com
- Operator friction: https://www.railforums.co.uk/threads/gtr-not-accepting-my-claim-through-delay-repay-sniper.163594/ ; https://abcommuters.com/2018/04/26/commuters-beware-delay-repay-could-get-you-fined-for-doing-absolutely-nothing-wrong/ ; https://forums.moneysavingexpert.com/discussion/6233103/delay-repay-letter ; https://www.railforums.co.uk/threads/railguard-is-it-legal-to-claim-delay-repay-this-way.172730/ ; https://www.railforums.co.uk/threads/questions-about-delay-repay-claims-and-third-party-services-in-the-uk.284537/ ; https://www.railforums.co.uk/threads/delay-repay-irregularity.251730/
- Railed: https://gotrailed.co.uk/ ; https://gotrailed.co.uk/blog/automatic-delay-repay-what-it-covers/ ; https://gotrailed.co.uk/blog/why-delay-repay-claims-get-rejected/ ; https://www.appbrain.com/app/railed-train-delay-repay/com.gotrailed.railed
- DelayDog: https://delaydog.com/ ; https://delaydog.com/about/ ; https://delaydog.com/how-it-works ; https://delaydog.com/privacy/ ; https://apps.apple.com/gb/app/delaydog/id6755113841 ; https://play.google.com/store/apps/details?id=com.delaydog.app
- Delayo: https://delayo.uk/
- Reeclaim: https://www.reeclaim.co.uk/ ; https://www.moneysavingexpert.com/reclaim/oyster-card-refund/
- Others: https://www.traindelaysrepay.co.uk/ ; https://betalist.com/startups/latetrain ; https://refundmyrail.co.uk/ ; https://www.g2.com/sellers/refundcat ; https://mcei.de/success-stories/refundrebel ; TrainTrick: https://www.imperial.ac.uk/news/173687/imperial-student-launches-claim-compensation-delayed/ and https://medium.com/@info_25009/traintrick-has-reached-its-final-destination-4afa1f595e07
- Trainline: https://www.thetrainline.com/trains/great-britain/delay-repay ; https://support.thetrainline.com/hc/en-gb/articles/5170397531807-My-UK-train-was-delayed-Can-I-claim-compensation ; https://www.trainlinegroup.com/media/en/press-releases/delayed-rail-passengers-losing-out-more-gbp80mn-each-year-unclaimed-compensation-due-delay-repay-frustration/ ; https://www.cityam.com/trainline-calls-for-better-delay-repay-after-passengers-lose-out-on-80m/
- Operator automation: https://www.gwr.com/help-and-support/refunds-and-compensation/automated-delay-repay ; https://www.avantiwestcoast.co.uk/help-and-support/delay-repay ; https://help.northernrailway.co.uk/s/article/Automated-Delay-Repay-Compensation ; https://www.southeasternrailway.co.uk/help/refunds-and-compensation/delay-repay-compensation ; https://www.southernrailway.com/help-and-support/delay-repay-compensation/auto-delay-repay ; https://www.lumo.co.uk/help/delay-repay ; https://tracsis.com/products/ticketing/smartrepay
- GitHub search "delay repay" (46 repos): https://github.com/search?q=delay+repay&type=repositories ; e.g. https://github.com/doublevcodes/fifteen , https://github.com/robevansuk/delay-repay-bot , https://github.com/georgejkaye/delay-repay

**Operator terms and regulator**
- Thameslink: https://www.thameslinkrailway.com/help-and-support/delay-repay
- Southern: https://www.southernrailway.com/help-and-support/delay-repay-compensation
- East Midlands Railway: https://www.eastmidlandsrailway.co.uk/delay-repay
- ORR Delay Repay Claims Companies Market Review (Apr 2019): https://www.orr.gov.uk/media/15048/download ; https://www.orr.gov.uk/monitoring-regulation/rail/competition/market-monitoring/market-review-rail-compensation-claims-companies
- ORR consultations and Code of Practice: https://www.orr.gov.uk/media/17527 ; https://www.orr.gov.uk/sites/default/files/2021-05/second-consultation-on-improving-access-to-delay-compensation-may-2021_0.pdf ; https://www.orr.gov.uk/sites/default/files/2021-05/delay-compensation-consulation-responses-may-2021.pdf ; https://www.orr.gov.uk/sites/default/files/2022-03/delay-compensation-code-of-practice.pdf
- ORR claims data: https://dataportal.orr.gov.uk/media/ivhke12a/delay-compensation-claims-factsheet-2025-26-rail-periods-5-7.pdf
- National Rail compensation page: https://www.nationalrail.co.uk/help-and-assistance/compensation-and-refunds/
- DfT consolidated Delay Repay (Mar 2026): https://www.gov.uk/government/news/delay-repay-changes-will-make-rail-travel-easier-under-great-british-railways (not retrieved; relied on coverage) ; https://www.railbusinessuk.com/passenger/2026/03/18/consolidated-delay-repay-service-to-include-third-party-rail-ticket-retailers/ ; https://www.railmagazine.com/news/notice-issued-for-consolidated-delay-repay-platform ; https://www.transportfocus.org.uk/news/transport-focus-comment-on-changes-to-delay-repay/ ; https://consumervoice.uk/trains/new-delay-repay-rules-aim-to-stop-passengers-missing-out-on-80m-in-compensation/

**Other markets and AI agents**
- AirHelp terms: https://www.airhelp.com/en-int/terms/ ; Flightright UK: https://www.flightright.co.uk/your-rights/flight-delay ; AirHelp app (2017): https://www.bloomberg.com/news/articles/2017-05-30/delayed-flight-new-airhelp-app-feature-files-claims-instantly
- Deutsche Bahn: https://www.bahn.de/hilfe/fahrgastrechte/faq-digitale-fahrgastrechte ; https://www.verbraucherzentrale.de/wissen/reise-mobilitaet/unterwegs-sein/erstattung-bei-zugverspaetung-so-gibts-geld-zurueck-12080
- NS: https://www.ns.nl/binaries/_ht_1754559946332/content/assets/ns-nl/voorwaarden/voorwaarden-geld-terug-bij-vertraging.pdf ; https://treingeldterug.nl/ ; https://trein-vertraging.nl/en ; https://treinclaim.nl/compensatie/ns-binnenland ; https://trein-vertraging.nl/blog/ovpay-geld-terug-bij-vertraging
- AI agents: https://dev.to/imarpan/i-built-an-ai-agent-that-fills-in-your-flight-delay-claim-ncb ; https://github.com/imarpanpatra/claimback ; https://www.vals.ai/blogs/impossible-refund ; https://the-decoder.com/ai-agents-chasing-a-465-train-refund-invented-excuses-leaked-medical-data-and-spammed-an-mps-office/ ; https://www.forbes.com/sites/rashishrivastava/2026/09/25/ai-agents-are-helping-people-recover-money-by-negotiating-bills-and-chasing-refunds/
