# 01 - Booking apps and ticket retailers: what they do about Delay Repay

Research date: 2026-10-19. Slice: third-party ticket retailers and booking apps (plus the National Rail / GBR position).

## Method and evidence caveat (read first)

- WebFetch failed with DNS errors (`getaddrinfo ENOTFOUND`) for every host tried (trainlinegroup.com, gov.uk, thetrainline.com, mytrainpal.com, apps.apple.com, railmagazine.com). I could not open a single page directly. A request to inspect the proxy status was denied by the sandbox and I did not work around it.
- All findings therefore come from WebSearch result summaries, which quote or paraphrase the pages at the cited URLs. No page was read in full.
- Labels used below:
  - **PRIMARY (via search excerpt)**: the URL is the company's or government's own page, but I saw it only through a search excerpt, not by opening it. Re-check before relying on exact wording.
  - **REPORTED**: press, trade media, blogs, forums, or a competitor's marketing.
  - **UNCERTAIN**: could not confirm, or sources conflict.
- Nothing here is "VERIFIED" in the strict sense of me having read the primary page.

## 1. Summary

- **No mainstream booking app submits a Delay Repay claim on the passenger's behalf.** Trainline (the market leader) detects delays and estimates the payout, then sends you to the operator's claim page. Its own campaign says industry rules stop it offering a "1-click" claim. TrainPal, Omio/Uber, Trainsplit, Split My Fare, Raileasy and Seatfrog all say claims go to the operator.
- **One adjacent app does claim to file for you: Railed** (gotrailed.co.uk, Android and web; a 10% fee on successful claims). It is not a ticket retailer, and its description of itself is the only evidence I found (REPORTED/UNCERTAIN). It is the closest existing competitor to the project.
- **Operator auto-pay and one-click schemes are mostly direct-booking only.** GWR, TransPennine Express, Northern, Southeastern and LNER limit them to tickets bought on the operator's own site or app (some also to smartcards). Southeastern explicitly excludes Trainline tickets. About 26% of passengers buy via independent retailers (DfT figure cited by Trainline) and get the manual route.
- **A structural fix is planned but not live.** DfT announced (17 March 2026) a consolidated Delay Repay service under Great British Railways, claimable from wherever you buy, with retailers opting in. Procurement is under way (award decision reported for 19 Oct 2026; contract start given as 1 Oct or 30 Oct 2026 depending on the notice; award not confirmed). The Railways Bill was still in the Lords; GBR is expected around 12 months after Royal Assent. There is no GBR app or retail site yet.
- **Uber's UK train ticketing is resold third-party inventory (Omio partnership, 2022 launch).** I found no Delay Repay feature. "Uber Trains" proper is a planned Channel Tunnel service (about 2029), not UK domestic rail.

## 2. Comparison table

| App / retailer | Delay detection | Claim feature | Platforms | Fees | Eligible for operator auto-pay? | Evidence |
|---|---|---|---|---|---|---|
| **Trainline** (consumer) | Yes. Tracks journey, push notification, estimate of amount | Deep link to the operator's claim site; may show claim details. Not submitted by Trainline. Pre-fill unclear | iOS, Android, web (notifications via app or email) | None found for the feature | Generally no. Operators match against their own bookings; Southeastern explicitly excludes Trainline tickets | PRIMARY (via excerpt) + REPORTED |
| **Trainline Business** | Same flow described | Link to operator form | Business app / web | n/a | Not confirmed | PRIMARY (via excerpt) |
| **TrainPal** | Not confirmed. Live status in journey planner only | Claim guidance; homepage FAQ mentions "submit and track through TrainPal", but its guides say claims go to the operator | iOS, Android, web | Booking fee model, not researched | Not confirmed | PRIMARY (via excerpt), UNCERTAIN on in-app claim |
| **Uber (UK Travel)** | Not found for trains | None found | iOS, Android | Uber One cashback promo (expired by 31 Mar 2026) | Not confirmed | REPORTED |
| **Omio** | Yes for trip updates (delays, platforms). Not Delay Repay specific | None. Claim with the operator | iOS, Android, web | n/a | Not confirmed | App listing via excerpt, REPORTED |
| **Trainsplit / Raileasy** | None found | None. Says only the operator can pay; blog argues split tickets can claim on whole journey | Web, Android app | Share of saving | Not confirmed | PRIMARY (via excerpt) |
| **Split My Fare** | None found | None. Help says delay at junction between split tickets not claimable | Web | 15% of saving | Not confirmed | PRIMARY (via excerpt) |
| **Seatfrog** | None found | None. Explicitly "cannot claim through Seatfrog"; operator form, attach ticket and upgrade confirmation | iOS, Android | n/a | Not confirmed | PRIMARY (via excerpt) |
| **Rail Europe, Kiwi, Trip.com** | None found | Nothing found | Web/app | n/a | Not confirmed | Gap: nothing found |
| **National Rail (NRE) app** | Live disruption info | No claim feature found; claims via operator | iOS, Android, web | Free | n/a | UNCERTAIN (no official page seen) |
| **GBR app / retail site** | Not launched | Planned: one-stop shop, claim Delay Repay in one place | n/a | n/a | Planned consolidated scheme | PRIMARY (via excerpt), future |
| **Railiable** (adjacent) | Yes, via Network Rail movement data; alerts on paid tier | Calculates amount, copies details, opens operator portal. User submits | iOS (iPad listed); no Android found | Free + "Plus" subscription, price unconfirmed | n/a (works with any ticket) | App Store listing via excerpt |
| **Railed** (adjacent) | Yes. Says it detects ticket purchases and monitors journeys | **Says it files the claim directly with the operator and pays you 90%** | Android (AppBrain listing), web | 10% of successful claims; free if rejected | n/a | REPORTED (self-description only) |

## 3. Per-app detail

### Trainline (consumer app)

- **Detection: yes.** The Delay Repay page says Trainline tracks your journey and tells you through the app when you may be owed compensation. PRIMARY (via excerpt): https://www.thetrainline.com/trains/great-britain/delay-repay
- **Launch.** Trainline's press release of 8 December 2025 introduces "Delay Repay notifications", described as an industry first, with real-time estimates of what you may be owed. It says summer beta tests helped process about £1 million in claims. PRIMARY (via excerpt): https://www.trainlinegroup.com/media/en/press-releases/trainline-keeps-train-travellers-track-through-seasonal-disruption-new-features/ ; trade coverage REPORTED: https://railway-news.com/trainline-rolls-out-suite-of-new-features-in-largest-update-yet/
- **Claim feature: deep link, not submission.** Help text: after the trip Trainline sends a push notification or email with a link to the operator's website where you submit the claim. Another excerpt says you can "check all the details and click straight through to the operator's website". PRIMARY (via excerpt): https://support.thetrainline.com/en/support/solutions/articles/78000000555-my-uk-train-was-delayed-can-i-claim-compensation- and the Delay Repay page above.
- **Pre-fill: UNCERTAIN.** One summary of the press release says the app "fills in the information needed"; the help page says you "usually need to fill in a claim form on the train company's website" and that Trainline shows the details. I'd assume "shows claim details to copy", not a pre-filled operator form.
- **Trainline says it cannot do more.** Its campaign "Fair Play on Delay Repay" (launched late January 2026) states that current industry rules mean Trainline is "not yet able to offer a full 1-click Delay Repay experience", and that the technology exists but retailers are denied access. It cites a DfT figure that about 26% of passengers buy via independent apps and websites, and YouGov research (29% said they failed to claim in 2025; Trainline's own commissioned data). PRIMARY (via excerpt): https://www.trainlinegroup.com/media/news/delayed-rail-passengers-losing-out-on-more-than-80mn-each-year-in-unclaimed-compensation-due-to-delay-repay-frustration ; REPORTED: https://www.railwaygazette.com/uk/trainline-calls-for-third-party-ticket-sellers-to-be-able-to-offer-one-click-delay-repay/70393.article , https://railway-news.com/trainline-calls-for-delay-repay-reform-in-new-campaign/
- **Ticket eligibility (conflicting).** The help page excerpt says Delay Repay is available for Flexible or Advance tickets on single-leg trips and not through the app for open returns or season tickets. A news summary says the feature alerts holders of Advance tickets. UNCERTAIN which is current.
- **Operators covered.** The page lists about 17 operators (including Northern, ScotRail, Southeastern, Southern, SWR, Greater Anglia, GWR, TPE, TfW, WMR, Thameslink, Hull Trains, Lumo, Merseyrail, LNWR, Stansted Express, Great Northern). Avanti, LNER, CrossCountry, EMR, Chiltern and others were not in the excerpt, so coverage is UNCERTAIN.
- **Platforms:** iOS, Android; email notifications. **Fees:** none found for the feature.
- **Operator auto-pay.** Tickets bought through Trainline are generally outside operators' direct-booking schemes (see section "Operator auto-pay" below).
- **Trainline Business** (separate help centre) describes the same tracking-plus-link flow. PRIMARY (via excerpt): https://support.businesstravel.thetrainline.com/hc/en-gb/articles/5271362167199-My-UK-train-was-delayed-Can-I-claim-compensation . I found nothing on Trainline Platform / partner-white-label arrangements or on admins claiming on behalf of employees. UNCERTAIN.

### TrainPal

- **Detection: not confirmed.** The FAQ mentions live status and strike warnings in the journey planner; I found no evidence of automatic delay push notifications or Delay Repay estimates. https://www.mytrainpal.com/faq/delays-and-disruptions
- **Claim: guidance, with ambiguous in-app wording.** The homepage FAQ reportedly says Delay Repay claims can be "submitted and tracked through TrainPal", while its FAQ and guides say compensation claims must go to the operator you travelled with, regardless of where you bought, within 28 days. Terms say claim directly from the operator for delays over 30 minutes. I found no description of an in-app filing flow, so treat the in-app claim as UNCERTAIN. Sources: https://www.mytrainpal.com/ , https://www.mytrainpal.com/guide/delay-repay-explained , https://www.mytrainpal.com/guide/delay-repay-time-limit , https://www.mytrainpal.com/web-pages/booking-terms-and-conditions.html
- **Refund vs Delay Repay.** The in-app Refund button is for refunds; the guide says to select "Delay Repay" only if you travelled.
- **Auto-pay eligibility: not stated.** TrainPal's guides mention that operators such as Southeastern, LNER and Avanti offer automated Delay Repay but do not say TrainPal bookings qualify. https://www.mytrainpal.com/guide/train-companies-delay-repay
- Trustpilot (Nov 2025) has a complaint about an inaccurate delay email and vouchers; one anecdote, REPORTED.

### Uber (UK)

- UK users can buy National Rail, Heathrow Express and Eurostar tickets in the Uber app (REPORTED: https://www.uber.com/gb/en/ride/travel/trains ). The Omio partnership launched Aug 2022 (REPORTED: https://www.timeout.com/news/youll-soon-be-able-to-book-eurostar-tickets-on-uber-080422 ; https://www.phocuswire.com/Omio-provides-tech-and-inventory-to-Uber-app ). I could not confirm whether the same inventory partner is used in 2026.
- **No Delay Repay detection or claim feature found.**
- "Uber Trains" in the branding sense is the Gemini Trains partnership for a Channel Tunnel high-speed service (target about 2029, financing and permits outstanding). Not relevant to domestic Delay Repay. REPORTED: https://www.connexionfrance.com/a/741411 , https://www.travelmole.com/news/uber-gemini-high-speed-train-service/

### Omio

- App listing says real-time updates on delays and platform changes (App Store via excerpt: https://apps.apple.com/gb/app/omio-train-bus-and-flight/id885372509 ). I found no Omio Delay Repay page. A RailUK Forums moderator says to claim from the operator (REPORTED, undated: https://www.railforums.co.uk/threads/delay-repay-omio-app.200099/ ).

### Trainsplit, Split My Fare, Raileasy

- All sold by Raileasy-family brands. They say only the operator can pay; Trainsplit says it cannot issue compensation and publishes a blog arguing a delay on a split journey can be claimed against the whole journey (the blog is old, about 2020-21). Split My Fare help says if the delay happened at the junction between two split tickets you cannot claim. Raileasy says claim from the operator that caused the delay.
- No detection or claim tooling found. Sources: https://trainsplit.com/blog/split-ticketing-delay-repay , https://trainsplit.com/help , https://www.splitmyfare.co.uk/help/ , https://raileasy.co.uk/delay-repay
- Fees: Split My Fare takes 15% of the saving (REPORTED); Trainsplit a share of the saving.

### Seatfrog

- Help centre: you cannot claim compensation through Seatfrog; use the operator's Delay Repay form and attach the original ticket plus the Seatfrog upgrade confirmation. Upgrades are not refunded for delays; refund requests are only for cancelled/unused ones. Thresholds as per operator. One page has a placeholder "[refund link]" (stale). Source: https://help.seatfrog.com/hc/en-gb/articles/4408441101583 , https://help.seatfrog.com/hc/en-gb/articles/360001122176-Delay-Repay-my-train-was-delayed-can-I-get-a-refund-on-my-upgrade

### Rail Europe, Kiwi, Trip.com

- Nothing found about Delay Repay features. Trip.com publishes SEO guides on Delay Repay (https://uk.trip.com/trains/guide/uk-delay-repay/) but I saw no product feature. UNCERTAIN / gap.

### National Rail Enquiries and Great British Railways

- **NRE app:** I found no official page showing a Delay Repay feature. One blog describes it as a hub that links to operators. UNCERTAIN.
- **GBR app / retail site: announced, not launched.** DfT press release (17 March 2026): Delay Repay changes under GBR - one consolidated service replacing 14 operators' schemes; passengers can claim from wherever they buy, including third-party retailers such as Trainline; retailers and non-GBR operators opt in; passengers link accounts to participating retailers. PRIMARY (via excerpt): https://www.gov.uk/government/news/delay-repay-changes-will-make-rail-travel-easier-under-great-british-railways ; REPORTED: https://www.railwaygazette.com/uk/consolidated-delay-repay-service-to-include-third-party-rail-ticket-retailers/70612.article , https://www.railmagazine.com/news/ticket-retailers-welcome-delay-repay-changes
- **Timing.** Procurement: RDG/Network Rail's Fares, Ticketing and Retailing programme is buying a "consolidated/centralised Delay Repay service" with retailer-facing APIs via the RDG gateway and an electronic ticket validation lot; the tender notices give differing values and dates (£12.8m+VAT / £25.4m incl. VAT; award decision reported for 19 Oct 2026; contract from 30 Oct 2026 or 1 Oct per notice; to 30 Sep 2031). Sources: https://www.find-tender.service.gov.uk/Notice/026489-2026 , https://www.find-tender.service.gov.uk/Notice/053093-2026 , https://www.railbusinessuk.com/ticketing/2026/06/08/procurement-of-consolidated-train-delay-repay-service-begins/ , https://www.railmagazine.com/news/notice-issued-for-consolidated-delay-repay-platform . I found no confirmation that a contract has been awarded.
- **Legislative timing:** the Railways Bill passed the Commons in June 2026 and was in the Lords; GBR operational about 12 months after Royal Assent (REPORTED, secondary: https://www.gov.uk/guidance/great-british-railways via search, https://www.nsar.co.uk/2026/05/member-update-kings-speech-2026/ ). So retailer-claim integration is unlikely before late 2027. UNCERTAIN.
- A Rail Magazine comment piece argues GBR "must get its ticketing app right" (https://www.railmagazine.com/comment-landing-page/great-british-railways-must-get-its-ticketing-app-right), confirming the app is planned, not live.
- **Independent retailers' lobby.** Independent Rail Retailers (IRR) report (Feb 2026) says its members sell over £5bn of tickets a year and cannot handle Delay Repay for customers; proposes retailers file claims for authorised customers, and "parity of access" in law. https://independentrailretailers.co.uk/delay-repay-reform/ , https://independentrailretailers.co.uk/wp-content/uploads/2026/02/Making-Delay-Repay-work-for-passengers.pdf . A Commons Railways Bill memo (Jan 2026) says the same: https://publications.parliament.uk/pa/cm5901/cmpublic/Railways/memo/RB13.htm

### Adjacent apps with notable Delay Repay functionality

- **Railed** (https://gotrailed.co.uk/ ; Android: https://www.appbrain.com/app/railed-train-delay-repay/com.gotrailed.railed). Self-description: detects ticket purchases, monitors journeys, and when a delay qualifies "fills in the claim form and submits it directly to your operator"; you receive 90% of successful claims, nothing if rejected; claims the whole National Rail network. The operator still decides. **This is the only product I found that claims to file on the user's behalf.** All evidence is the vendor's own marketing. I found no independent review, no operator statement on accepting agent-filed claims, and no evidence of how it submits (portal automation vs. API). UNCERTAIN, and a regulatory/operator-terms risk to examine.
- **Railiable** (iOS App Store, https://apps.apple.com/app/id6769321397 , identification of this listing as Railiable is from search excerpts): live Network Rail data, compensation calculator, alerts on a paid tier, hands off to the operator portal with copy-details. Any ticket source. Free plus in-app purchases. Not a submitter.
- **Other claim helpers seen in results (not investigated):** delayrepay.uk, myrailbuddy.com, Delay Repay Sniper (a third-party admin tool; REPORTED that GTR demanded repayment from users who mentioned using it - an enforcement risk signal, source: abcommuters.com, 2018, old).

### Operator auto-pay and one-click schemes: direct bookings only

This is central to the project hypothesis. Evidence that these apply to direct/own-channel tickets:

- **GWR automated Delay Repay:** notifies within 48 hours and fills in the claim; covers Advance tickets bought on GWR.com and some smartcard travel; opt-in. PRIMARY (via excerpt): https://www.gwr.com/help-and-support/refunds-and-compensation/automatic-delay-repay
- **Southeastern One Click:** for Key smartcard customers and eTicket or paper Advance tickets bought via its website/app; sTicket holders must sign up. Another source says it does not cover Trainline tickets; Southeastern says third-party order references are not enough on their own (via Railed's page, REPORTED). The app auto-generates a claim for 15+ minute delays, and the claim is pre-filled and confirmed by the user. PRIMARY (via excerpt): https://www.southeasternrailway.co.uk/help/refunds-and-compensation/delay-repay-compensation ; Play listing: https://play.google.com/store/apps/details?id=southeastern.travelcompanion.prod
- **LNER:** One-click Delay Repay for customers who book through LNER and opt in; those who booked elsewhere claim by form within 28 days. PRIMARY (via excerpt): https://www.lner.co.uk/support/delay-repay/
- **Avanti West Coast:** pre-populated claim form sent within about 30 minutes for Advance tickets booked directly (app or website); third-party buyers claim manually via the portal. PRIMARY (via excerpt): https://www.avantiwestcoast.co.uk/help-and-support/delay-repay
- **TransPennine Express, Lumo, Northern:** automated scheme limited to Advance tickets bought via the operator's own site/app, opt-in (Railed's operator pages, REPORTED: https://gotrailed.co.uk/train-operators/transpennine-express-delay-repay/ , https://gotrailed.co.uk/train-operators/lumo-delay-repay/ ; Lumo help: https://www.lumo.co.uk/help/delay-repay).
- **Great Northern app:** reported to generate claims automatically (search summary, via Play listing); not confirmed with the operator's page.
- **Blog summary:** auto schemes "usually don't cover tickets bought through sites like Trainline" because the operator has no record of the booking (REPORTED: https://smartsmssolutions.com/resources/blog/uk/automatic-delay-repay-which-operators-auto-compensate , https://gotrailed.co.uk/blog/automatic-delay-repay-what-it-covers/).
- Quality warning from Resolver: automatic systems can miss split-ticket legs or knock-on delays (REPORTED: https://news.resolver.co.uk/train-delays-how-to-use-delay-repay-to-maximise-your-claim/).

Also relevant: ORR/DfT data show Delay Repay claims are growing quickly (3.8m closed in periods 1-4 of 2026-27, up 55% year-on-year, per a forum repost of ORR figures; ORR factsheet 1.9m closed Jan-Mar 2026) but Transport Focus says only about 45% of eligible passengers claim. https://dataportal.orr.gov.uk/media/ittbwvrh/delay-compensation-claims-factsheet-2025-26-rail-periods-11-13.pdf , https://www.transportfocus.org.uk/?p=38714

## 4. Implications for the project

**Where the gap is:**
- The hypothesis largely holds for the incumbent retailers. Trainline, the largest, stops at detect, estimate and link-out, and publicly says it is blocked from going further. TrainPal, Omio, Uber, Seatfrog and the split-ticket sites do not appear to offer even detection.
- Tickets bought outside the operator's own channel (Trainline, TrainPal, split tickets, Seatfrog upgrades, season tickets, contactless/PAYG in some cases) fall outside operator auto-pay and must be claimed manually. That is the clearest gap for an agent that drafts the claim with evidence attached and stops for approval.
- Split-ticket journeys and connection-based claims are explicitly awkward (Split My Fare says junction delays are not claimable; Resolver warns auto-claims miss legs), so computing the correct entitlement is something an agent can add value on.
- The "stop for passenger approval" design is also a reasonable answer to the structural issue below.

**Where the gap is not (risks):**
- **Railed** already claims end-to-end filing for a 10% fee. I could not verify its quality, scale or operator acceptance, but any differentiation must be argued against it (approval step, evidence quality, transparency, no success fee, etc.). Investigate it further (colleagues' slice on claim-management services should cover this).
- **Operators already pre-fill for direct bookers** (Avanti, Southeastern, GWR, LNER, Great Northern). Value there is small; the project's addressable set is non-direct bookings and non-participating operators.
- **The market is about to be re-plumbed.** The consolidated Delay Repay service with retailer APIs, plus account linking, means Trainline and other opting-in retailers could offer true one-click claims once built. On the sources I found, that is probably late 2027 or later (GBR needs Royal Assent first, then about 12 months), but the contract award around this week could move the dates. The window for a retailer-independent agent is real but time-limited; an agent that sits on top of the new service API (if third-party/agent access is permitted) would be a different, possibly better, position than portal automation.
- **Portal automation risk.** I found no operator terms on agent-filed claims. One 2018 consumer-group report suggests GTR challenged users of a third-party tool. The project's "draft and stop for approval" stance reduces this but does not remove it; check each operator's terms and bot protections.
- **Trainline's existing flow** produces the same hand-off the project would draft; the project's edge is the evidence bundle and the actual form fill, not detection.

**Open questions to resolve next:**
1. Exactly what Trainline's claim assistance does (screenshot and click-through test on a real device).
2. Whether TrainPal's "submit and track" wording means anything beyond a link.
3. How Railed actually submits, and whether any operator has blocked or rejected its claims.
4. Whether the consolidated service will allow agent/third-party-on-behalf submissions, and who gets API access.
5. Whether the Rail Delivery Group contract was awarded on 19 Oct 2026.

## 5. Sources

Company and government pages (read only via search excerpts; see caveat):
- https://www.thetrainline.com/trains/great-britain/delay-repay
- https://support.thetrainline.com/en/support/solutions/articles/78000000555-my-uk-train-was-delayed-can-i-claim-compensation-
- https://support.businesstravel.thetrainline.com/hc/en-gb/articles/5271362167199-My-UK-train-was-delayed-Can-I-claim-compensation
- https://www.trainlinegroup.com/media/en/press-releases/trainline-keeps-train-travellers-track-through-seasonal-disruption-new-features/ (8 Dec 2025)
- https://www.trainlinegroup.com/media/news/delayed-rail-passengers-losing-out-on-more-than-80mn-each-year-in-unclaimed-compensation-due-to-delay-repay-frustration (Jan 2026)
- https://www.mytrainpal.com/ ; /faq/delays-and-disruptions ; /guide/delay-repay-explained ; /guide/delay-repay-time-limit ; /guide/train-companies-delay-repay ; /web-pages/booking-terms-and-conditions.html
- https://www.uber.com/gb/en/ride/travel/trains
- https://apps.apple.com/gb/app/omio-train-bus-and-flight/id885372509
- https://trainsplit.com/blog/split-ticketing-delay-repay ; https://trainsplit.com/help ; https://www.splitmyfare.co.uk/help/ ; https://raileasy.co.uk/delay-repay
- https://help.seatfrog.com/hc/en-gb/articles/4408441101583 ; https://help.seatfrog.com/hc/en-gb/articles/360001122176-Delay-Repay-my-train-was-delayed-can-I-get-a-refund-on-my-upgrade
- https://www.gov.uk/government/news/delay-repay-changes-will-make-rail-travel-easier-under-great-british-railways (17 Mar 2026)
- https://www.find-tender.service.gov.uk/Notice/026489-2026 ; https://www.find-tender.service.gov.uk/Notice/053093-2026
- https://www.gwr.com/help-and-support/refunds-and-compensation/automatic-delay-repay
- https://www.southeasternrailway.co.uk/help/refunds-and-compensation/delay-repay-compensation
- https://www.lner.co.uk/support/delay-repay/
- https://www.avantiwestcoast.co.uk/help-and-support/delay-repay
- https://www.lumo.co.uk/help/delay-repay
- https://independentrailretailers.co.uk/delay-repay-reform/ ; https://independentrailretailers.co.uk/wp-content/uploads/2026/02/Making-Delay-Repay-work-for-passengers.pdf
- https://publications.parliament.uk/pa/cm5901/cmpublic/Railways/memo/RB13.htm
- https://dataportal.orr.gov.uk/media/ittbwvrh/delay-compensation-claims-factsheet-2025-26-rail-periods-11-13.pdf
- https://www.transportfocus.org.uk/?p=38714
- https://www.gov.uk/guidance/great-british-railways

Press, trade and third-party (REPORTED):
- https://railway-news.com/trainline-rolls-out-suite-of-new-features-in-largest-update-yet/
- https://railway-news.com/trainline-calls-for-delay-repay-reform-in-new-campaign/
- https://www.railwaygazette.com/uk/trainline-calls-for-third-party-ticket-sellers-to-be-able-to-offer-one-click-delay-repay/70393.article
- https://www.railwaygazette.com/uk/consolidated-delay-repay-service-to-include-third-party-rail-ticket-retailers/70612.article
- https://www.railmagazine.com/news/ticket-retailers-welcome-delay-repay-changes
- https://www.railmagazine.com/news/notice-issued-for-consolidated-delay-repay-platform
- https://www.railmagazine.com/news/irr-calls-for-urgent-delay-repay-reform-in-new-report
- https://www.railbusinessuk.com/ticketing/2026/06/08/procurement-of-consolidated-train-delay-repay-service-begins/
- https://www.railmagazine.com/comment-landing-page/great-british-railways-must-get-its-ticketing-app-right
- https://www.nsar.co.uk/2026/05/member-update-kings-speech-2026/
- https://www.railforums.co.uk/threads/does-trainline-now-let-you-claim-delay-repay.302594/ ; https://www.railforums.co.uk/threads/delay-repay-omio-app.200099/
- https://www.timeout.com/news/youll-soon-be-able-to-book-eurostar-tickets-on-uber-080422 ; https://www.phocuswire.com/Omio-provides-tech-and-inventory-to-Uber-app ; https://www.connexionfrance.com/a/741411 ; https://www.travelmole.com/news/uber-gemini-high-speed-train-service/
- https://news.resolver.co.uk/train-delays-how-to-use-delay-repay-to-maximise-your-claim/
- https://smartsmssolutions.com/resources/blog/uk/automatic-delay-repay-which-operators-auto-compensate
- https://uk.trip.com/trains/guide/uk-delay-repay/

Competitor and vendor self-description (weakest; UNCERTAIN):
- https://gotrailed.co.uk/ ; https://gotrailed.co.uk/blog/automatic-delay-repay-what-it-covers/ ; https://gotrailed.co.uk/blog/trainline-delay-repay-who-to-claim-from/ ; https://gotrailed.co.uk/train-operators/transpennine-express-delay-repay/ ; https://gotrailed.co.uk/train-operators/lumo-delay-repay/ ; https://gotrailed.co.uk/train-operators/southeastern-delay-repay/ ; https://www.appbrain.com/app/railed-train-delay-repay/com.gotrailed.railed
- https://apps.apple.com/app/id6769321397 (Railiable listing as surfaced by search)
- https://delayrepay.uk/ ; https://myrailbuddy.com/guides/how-to-claim-delay-repay
