# 02 - Operator auto-compensation schemes and national policy

Research date: 2026-10-19. Slice: train operators' own automatic or assisted Delay Repay schemes, national policy (DfT / GBR / ORR), and claim-rate data.

## Method caveat (read first)

WebFetch was blocked in this session: every host (gov.uk, orr.gov.uk, operator sites, parliament) failed with DNS/proxy errors, and I did not work around the block. All findings therefore come from WebSearch result summaries, which quote or paraphrase the pages listed, but I did not open the pages themselves. Labels used below:

- **VERIFIED-ish**: a search summary quoted an operator, gov.uk, ORR, Transport Focus or Parliament page directly. Still worth a spot-check by opening the URL.
- **REPORTED**: press, trade press, blogs, forums, or third-party analysts (Untap, MyTrainPal, Trainline marketing).
- **UNCERTAIN**: sources conflict, are old, or I found nothing.

Nothing here has been confirmed by reading a primary page end to end. Before building on any operator-specific rule, re-check the operator URL in the sources list.

---

## 1. Summary

- **Only c2c pays with no passenger action.** c2c's Automatic Delay Repay credits an eVoucher to a linked online account for smartcard users who tap in and out, with a trigger of "more than 2 minutes" late (c2c's own pages). Untap's 2026 audit says c2c is the only operator that is fully automatic. Everywhere else, "automatic" or "one-click" means the operator pre-fills a claim and the passenger still has to accept it, or an opt-in plus direct purchase triggers a payout. (VERIFIED-ish for c2c; REPORTED for the Untap claim.)
- **Nearly every automated scheme is limited to tickets bought direct from the operator** (website or app, usually Advance/e-ticket, or the operator's own smartcard), usually needing an account or opt-in with the same email as the booking. Tickets bought through Trainline, TrainPal and similar retailers are not covered by any operator auto scheme I found. DfT says about 26% of passengers buy through independent retailers (as cited by Trainline).
- **A DfT written answer (Aug 2026) says ten of the fourteen DfT-contracted operators offer automated "one-click" Delay Repay.** DfT does not hold data on what share of journeys actually receive it. (VERIFIED-ish via TheyWorkForYou mirror of Hansard.)
- **Policy is promised, not live.** DfT announced on 17 March 2026 that Delay Repay claim systems will merge into one service under Great British Railways (GBR), and passengers will be able to claim through the retailer where they bought the ticket (e.g. Trainline). Delivery depends on the Railways Bill (in Lords committee as of Oct 2026, Royal Assent targeted end-2026, GBR operating around mid/late 2027) and a procurement for a consolidated platform that RDG is running right now (award decision reported as planned for 19 Oct 2026).
- **The claim rate is about 45% and falling.** The DfT/Transport Focus 2025 survey found 45% of eligible passengers claimed (down from 47% in 2023, the first fall since 2016). Roughly 34% claim at the 15-minute tier and 51% at the 30-minute tier. The opportunity is large, but the claim volume is rising fast (ORR: 3.8m claims closed in periods 1-4 of 2026-27, up 55%).
- **The project's window is real but time-limited.** Direct-booking passengers on many operators are already served; the gaps are third-party-booked tickets, non-automated operators, and manual evidence-heavy claims. A DfT-backed national system that accepts retailer-originated claims could erode that gap from roughly 2027-28 onward.

---

## 2. Per-operator table

Legend: DR15 / DR30 = Delay Repay threshold (minutes). "Auto?" distinguishes **Full auto** (money paid with no passenger action), **Assisted auto** (claim pre-filled or triggered, passenger accepts/clicks), **No** (manual claim only), **UNCERTAIN**. "3rd-party bookings" = whether tickets from Trainline/TrainPal etc. can use the auto scheme. Standard claim window is 28 days of travel unless stated. Ownership column: "DfTO" = DfT Operator Limited (public); status from search summaries, see section 3.

| Operator | Auto? (marketing name) | Conditions | Covers 3rd-party bookings? | DR band | Portal platform | Ownership | Source |
|---|---|---|---|---|---|---|---|
| **Avanti West Coast** | Assisted auto: "Automated Delay Repay" (ADR) | Advance tickets booked direct only; opt in; Delay Repay account with same email as ticket purchase; first opt-in no later than day of travel; claim created within 24h. Non-Advance tickets not covered. | **No.** Seatfrog's help page says claims must go direct to Avanti. | DR15 | Own portal (account required); vendor UNCERTAIN | Not confirmed as DfTO; reported to remain private into 2027 (UNCERTAIN) | [Avanti](https://avantiwestcoast.co.uk/help/delay-repay), [promo page](https://www.avantiwestcoast.co.uk/tickets-and-savings/ways-to-save/promotion), [Seatfrog](https://help.seatfrog.com/hc/en-gb/articles/6188991526415-What-should-I-do-if-my-Superfare-train-was-delayed) |
| **LNER** | Assisted auto: "One-click Delay Repay" | Tickets bought on LNER website/app, opted in; email within ~30 min with a claim link. Manual form otherwise. Forums report problems on split/through journeys (anecdotal). | **No.** LNER says tickets bought elsewhere claim via the original seller (e.g. Trainline). | Search summaries say DR30 (LNER page snippet); third-party lists conflict (UNCERTAIN) | Own portal; vendor UNCERTAIN | DfTO (public) since 2018 | [LNER](https://www.lner.co.uk/help-and-support/delay-repay/), [Rail Forums](https://www.railforums.co.uk/threads/one-click-automatic-delay-repay-systems-are-useless.299127/) |
| **GTR: Thameslink, Great Northern, Southern, Gatwick Express** | Assisted auto: "Auto Delay Repay" | Key Smartcard; enrol in Auto Delay Repay; tap in and out (even with open gates); any ticket type loaded; email alert within 48h, passenger then claims. Not for paper/e-ticket/Advance (UNCERTAIN, pages only discuss smartcard). | N/A (smartcard-based, not retailer-based) | DR15 | Own portal | DfTO since 31 May 2026 (REPORTED via gov.uk headline; see sec. 3) | [Thameslink](https://www.thameslinkrailway.com/help-and-support/delay-repay/auto-delay-repay), [Great Northern](https://www.greatnorthernrail.com/help-and-support/journey-problems/delay-repay-compensation/auto-delay-repay), [Southern](https://www.southernrailway.com/help-and-support/delay-repay-compensation/auto-delay-repay) |
| **c2c** | **Full auto**: "Automatic Delay Repay" | c2c Smartcard with valid ticket; tap in at origin and out at destination; online account with the smartcard linked. Pays as eVoucher into account. Trigger stated as >2 minutes (c2c marketing). | N/A (smartcard only) | Auto from 2 min; manual scheme DR15 | Own system | DfTO since July 2025 | [c2c auto DR](https://www.c2c-online.co.uk/tickets-and-fares/automatic-delay-repay/), [eligibility](https://www.c2c-online.co.uk/help_centre/compensation/when-am-i-eligible-for-automatic-delay-repay/), [Untap](https://untap.money/rail-index) |
| **GWR** | Assisted auto: "Automated Delay Repay" | Opt in (default on for new Delay Repay accounts); same email as GWR account; one of: Advance bought on GWR.com, PAYG on GWR touch smartcard (Bristol), or weekly/monthly/annual/flexi season on a GWR smartcard bought on GWR.com. Notified within 48h with amount and pre-filled claim; passenger reviews/accepts. | **Not stated; implied no** (requires purchase on GWR.com). UNCERTAIN. | DR15 | Own (Delay Repay account) | Private First Group until transfer; reported Dec 2026 (UNCERTAIN) | [GWR automated DR](https://www.gwr.com/help-and-support/refunds-and-compensation/automated-delay-repay) |
| **Southeastern** | Assisted auto: "One Click Delay Repay" | Sign up in Southeastern account; Key smartcard holders, or e-ticket/Advance bought via Southeastern website/app. | **No** (third-party tickets need a ticket copy/eTicket reference; "we cannot use order references from third parties"). | DR15 | Own | DfTO (public since 2021) | [Southeastern FAQ](https://www.southeasternrailway.co.uk/help/support/faqs/refunds/one-click-delay-repay-faqs) |
| **South Western Railway** | Assisted auto: "Automated Delay Repay" | Touch smartcard season holders (tap data) and Advance tickets bought at southwesternrailway.com; create account, opt in. Alerts then accept/decline/amend. Details from forum quote of SWR text and a 2019 gov.uk story. | Implied no. UNCERTAIN (no current SWR page seen). | DR15 | Own | DfTO since May 2025 | [ITSO](https://www.itso.org.uk/news/news/smart-automatic-refunds-on-south-western-railway), [gov.uk 2019](https://www.gov.uk/government/news/half-of-departments-rail-operators-now-delivering-improved-delay-repay-compensation), [forum](https://www.railforums.co.uk/threads/how-does-automatic-delay-repay-work.180814/) |
| **Northern** | Reported as auto for Advance bought direct ("Automatic Delay Repay") but sources are 2017-19; no 2026 confirmation. | Advance ticket bought at northernrailway.co.uk/app; refunded to payment card (reported 1 working day processing). Reported as 30-min trigger. | Implied no | Manual DR15; auto threshold UNCERTAIN | Own | DfTO (public since 2020) | [LEP 2018](https://www.lep.co.uk/business/how-automatically-receive-compensation-if-your-train-delayed-226759), [Northern DR](https://northernrailway.co.uk/delay-repay), [Northern report](https://www.northernrailway.co.uk/delay-repay-performance-and-continuous-improvement-report) |
| **TransPennine Express** | Assisted auto: "Automated Delay Repay" | Advance tickets bought on tpexpress.co.uk or the TPExpress app; My Account email must match Delay Repay account; claim generated for delay of 15+ min on the booked train. (Launch coverage said 30 min; TPE page says 15.) | **No** (direct only) | DR15 | Own | DfTO (public since 2023) | [TPE](https://www.tpexpress.co.uk/help/delay-repay-compensation/automated-delay-repay), [RailAdvent](https://railadvent.co.uk/?p=27465) |
| **CrossCountry** | **No** evidence of auto | Manual form; BACS check warning; smartcard tickets need image and number. | n/a | DR30 (50% for 30-59 single, 100% 60+). Some third-party lists say DR15; CrossCountry's own page says 30. | Own form | Private (Arriva); no transfer date found (UNCERTAIN) | [CrossCountry](https://www.crosscountrytrains.co.uk/delay-repay) |
| **ScotRail** | **No** evidence of auto | Online or post; 28 days. Proposals for automatic payouts (Scottish Labour) are not policy. Page references claims "made before 26 November 2025" (reason unknown). | n/a | DR30: 50% of single / 25% of return for 30-59 min; 100% for 60-119 | Own | Scottish Government owned (since Apr 2022) | [ScotRail](https://www.scotrail.co.uk/about-scotrail/our-delay-repay-guarantee), [Scot LibDems Jan 2026](https://www.scotlibdems.org.uk/news/article/scotrail-disruption-payments-top-pound3-million) |
| **Transport for Wales** | **No** evidence of auto | Online or paper claim; 28 days. | n/a | DR15 (25% single for 15-29) | Own | Welsh Government owned (since Feb 2021) | [TfW](https://tfw.wales/delay-repay), [TfW 2018 announcement](https://news.tfw.wales/news/new-compensation-scheme-set-to-benefit-rail-customers-as-services-are-restored) |
| **Chiltern Railways** | **No** (automated processing back-end only, not passenger-visible auto) | Online compensation page; payouts by bank transfer, cheque, refund, vouchers, charity. 2022 "new automated system" is claim processing. | n/a | DR15 | Own (2022 new system; vendor UNCERTAIN) | Transfer to DfTO set for 20 Sept 2026; completion not confirmed (UNCERTAIN) | [Chiltern 2022](https://press.chilternrailways.co.uk/news/chiltern-railways-launch-delay-repay-15-compensation-scheme), [Rail Magazine](https://www.railmagazine.com/news/dfto-handover-date-announced-for-chiltern-railways) |
| **West Midlands Railway / London Northwestern** | **No** evidence of auto | Online claim; payment by card, BACS, PayPal, vouchers, charity. Season tickets: 12.5% of daily cost at 15-29 min. | n/a | DR15 | Own | DfTO since 1 Feb 2026 | [LNR](https://www.londonnorthwesternrailway.co.uk/delay-repay), [WMR](https://www.westmidlandsrailway.co.uk/delay-repay), [DfT](https://dfto-newsroom.prgloo.com/news/department-for-transport-confirm-date-that-west-midlands-railway-will-transfer-to-public-ownership) |
| **East Midlands Railway** | **No** evidence of auto (account pre-fills details; "Delay Repay function" in app) | App/web claim, ticket photo needed; pay by BACS, card, Amazon voucher, PayPal within 20 working days. ORR: EMR claims closed up 115% (Apr-Jul 2026) - cause not stated. | n/a | DR15 | Own | No transfer date found; reportedly still private into 2027 (UNCERTAIN) | [EMR](https://eastmidlandsrailway.co.uk/help-manage/manage/make-a-delay-repay-claim), [EMR news](https://news.eastmidlandsrailway.co.uk/news/emr-make-claiming-a-refund-after-a-delay-quicker-and-easier) |
| **Greater Anglia** | **No** evidence of auto | Online portal or paper; contactless users need a journey statement. | n/a | DR15 | Own | DfTO since 12 Oct 2025 | [Greater Anglia](https://www.greateranglia.co.uk/delayrepay) |
| **Merseyrail** | **No** | Own scheme (not national DR): journeys wholly on Northern/Wirral lines delayed >30 min; single = full fare, return = 50%; online claim with proof of purchase; 14-20 days. City Line (Northern) uses Northern's rules. | n/a | Own scheme, 30 min | Own online claim form | Merseytravel / operator JV (not DfTO) | [Merseyrail help](https://help.merseyrail.org/hc/en-gb/articles/14723310591132-Single-Return-Ticket-Compensation-Information) |
| **Grand Central** | **No** evidence | Own policy; sources disagree on whether it fully joins national DR. Reported 50% at 60-119, 75% at 120+ (Trainline table). | n/a | Own, starts around 60 min (REPORTED, UNCERTAIN) | UNCERTAIN | Private open access | [Trainline](https://www.thetrainline.com/trains/great-britain/delay-repay) (via search summary) |
| **Hull Trains** | **No** evidence | Online form. Reported 50% for 30-59, 100% for 60+. | n/a | DR30 (REPORTED) | UNCERTAIN | Private open access | [Trip.com guide](https://uk.trip.com/trains/guide/hull-trains-delay-repay) (REPORTED only) |
| **Lumo** | Assisted auto: "Auto Delay Repay" | Advance ticket bought on Lumo website/LumoGo app; register for Auto Delay Repay with same email; claim processed within 24h of journey for 30+ min delay. | **No** (direct only) | DR30 | Own | Private open access (FirstGroup) | [Lumo](https://lumo.co.uk/help/delay-repay) |
| **Elizabeth line (TfL)** | **No** (TfL "Service Delay Refund", not national DR) | Online claim via contactless/Oyster account or phone; delay 30+ min on Elizabeth line/Overground (15+ for Tube/DLR); 28 days; single-fare refund; "within our control" only. | n/a | 30 min | TfL online refund system | TfL | [TfL](https://tfl.gov.uk/fares/refunds-and-replacements/overground-and-tfl-rail-delays) |
| **Heathrow Express** | **No** | Own scheme: >15 min = 50% of HEx portion, >30 min = 100%; online form or post with original ticket; refunded to original payment method. | n/a | Own scheme | Own | Heathrow Airport Holdings | [Heathrow Express](https://www.heathrowexpress.com/help-centre/HelpTopic/how-can-i-claim-compensation-if-my-train-is-delayed/) |
| **Caledonian Sleeper** | Assisted/full auto (unclear): bookings on sleeper.scot or Guest Service Centre processed automatically within 24h for 30+ min delay, with email confirming details | Direct bookings only. Third-party bookings must contact the third party. Manual claims by post with original tickets; 10 working days. | **No.** Third-party bookings go to the retailer | DR30 | Own | Scottish Government owned (via Serco) | [Caledonian Sleeper](https://www.sleeper.scot/?p=848) |

Notes on the table:

- **Portal vendors:** I could not identify a vendor for any operator's claim portal from accessible sources. Every operator appears to run its own branded form/account (GWR and Avanti use account-based "Delay Repay accounts"; GTR's three/four brands share a single "Auto Delay Repay" design). UNCERTAIN whether some share a white-label backend. Recommend a hands-on inspection (DNS, form action URLs, JS bundles) as a follow-up task rather than guessing.
- **Thresholds:** third-party lists disagree on LNER, CrossCountry, ScotRail, Lumo, Caledonian Sleeper (15 vs 30). I have used operator wording where a search summary quoted it. Re-check before coding thresholds.
- **Payment methods seen:** card refund (Northern, Avanti, Southeastern implied), BACS, PayPal, National Rail vouchers, Amazon vouchers (EMR), charity donation, eVoucher (c2c), cheque (Chiltern).
- **Ten of fourteen** DfT-contracted operators offering one-click (DfT, Aug 2026) fits roughly: LNER, Avanti, GTR, GWR, Southeastern, SWR, TPE, Northern, c2c, plus one more (unclear which). DfT did not list them.

---

## 3. National policy and timeline: live vs promised

### Live now

| Item | Status | Source |
|---|---|---|
| Delay Repay (DR15/DR30) as national scheme; operators run their own claims | Live. Claims must go to the operator that ran the delayed train. | [ORR](https://www.orr.gov.uk/media/17407/download) (older) |
| ORR Delay Compensation Licence Condition / Code of Practice: operators must report on awareness steps | Live. ORR publishes yearly operator performance and "continuous improvement actions". | [ORR](https://www.orr.gov.uk/complaints-handling-and-delay-compensation-operator-performance-and-continuous-improvement-actions) |
| Operator-level one-click / auto schemes | Live at about ten DfT operators (Aug 2026 written answer) | [Hansard mirror](https://www.theyworkforyou.com/wrans/?id=2026-07-13.18291.h) |
| Public ownership under DfTO | Live for LNER, Northern, Southeastern, TPE, SWR, c2c, Greater Anglia, WMR/LNR, GTR (31 May 2026). Chiltern scheduled 20 Sept 2026 (completion unconfirmed). GWR reportedly Dec 2026. Avanti, CrossCountry, EMR: no date found. | [DFTO](https://dfto-newsroom.prgloo.com/news/dfto-takes-next-steps-towards-great-british-railways), [Rail Magazine](https://www.railmagazine.com/news/dfto-handover-date-announced-for-chiltern-railways), [GOV.UK GTR](https://www.gov.uk/government/news/gtr-services-transferred-to-public-ownership) |
| Did nationalisation change compensation? | **No evidence it did.** Each DfTO operator still runs its own Delay Repay process. Differences are driven by pre-existing operator schemes. UNCERTAIN (absence of evidence). | various |
| Trainline in-app Delay Repay check | Live (2026): detects eligible delays and links to the operator's form; does not file the claim. | [Trainline support](https://support.thetrainline.com/hc/en-gb/articles/5170397531807-My-UK-train-was-delayed-Can-I-claim-compensation) |

### Promised / in progress

| Item | Detail | Timing | Source |
|---|---|---|---|
| **DfT announcement, 17 Mar 2026** | "Delay Repay changes will make rail travel easier under Great British Railways": compensation claim systems merged into one service under GBR; passengers can claim directly from the retailer they bought from (Trainline etc.); participating retailers include third-party retailers and non-GBR operators that opt in; plus refund-cutoff change from 1 Apr 2026 (~£40m/yr savings) and railcard verification trials later in 2026. | No firm launch date; expected to take effect once GBR is operational (Rail Business UK) | [GOV.UK press release](https://www.gov.uk/government/news/delay-repay-changes-will-make-rail-travel-easier-under-great-british-railways), [Railnews](https://railnews.mobi/news/2026/03/17-delay-repay-system-to-be.html), [Rail Business UK](https://www.railbusinessuk.com/passenger/2026/03/18/consolidated-delay-repay-service-to-include-third-party-rail-ticket-retailers/) |
| **Consolidated Delay Repay procurement (RDG + Network Rail FTR programme)** | Phase 1 tender (Find a Tender 026489-2026, published about 4 Jun 2026): Lot 1 core platform incl. customer website and back-office portal (~£12.75m); Lot 2 electronic ticket validation database (~£0.72m); Lot 3 vouchers, warrants, printing, BACS (~£7.7m). Total about £21.2m ex-VAT. Contracts reported to run 30 Oct 2026 to 30 Sep 2031 (+ possible extension). RDG to operate an "interim national capability prior to GBR go-live". Later procurement to add PAYG scheme integration. Award decision reported as planned 19 Oct 2026 (today); not confirmed. | Contract start Oct 2026; interim service before GBR go-live | [Find a Tender](https://www.find-tender.service.gov.uk/Notice/026489-2026), [Rail Business UK](https://www.railbusinessuk.com/ticketing/2026/06/08/procurement-of-consolidated-train-delay-repay-service-begins/), [Rail Magazine](https://www.railmagazine.com/news/notice-issued-for-consolidated-delay-repay-platform) |
| **Railways Bill 2024-26** | Establishes GBR. Passenger Watchdog can set consumer standards in licence conditions, incl. compensation for disruption ("delay repay") and complaints. Report stage amendments (15 May 2026) proposed a GBR duty to make compensation systems digital by default, reduce passenger burden, and automate payouts "where practicable" - debated 10 Jun 2026; adoption **unconfirmed**. Commons passed June 2026; Lords committee began 8 Sept 2026 (seven sittings, dates through at least 26 Oct). | Royal Assent targeted by end-2026 (Bird & Bird, Aug 2026); GBR operational around summer 2027 (target) to about 12 months after Assent; one source says end-2027 | [Commons Library](https://commonslibrary.parliament.uk/research-briefings/cbp-10386/), [Amendment paper](https://publications.parliament.uk/pa/bills/cbill/59-02/0001/amend/railways_rm_rep_0515.pdf), [Hansard 10 Jun](https://hansard.parliament.uk/commons/2026-06-10/debates/D04D1360-E0F8-4D80-B4B4-E9EF69FA9B39/RailwaysBill), [Bird & Bird](https://www.twobirds.com/en/insights/2026/uk/railways-bill-update---august-2026), [Parallel Parliament](https://www.parallelparliament.co.uk/bills/2024-26/railways) |
| **Williams-Shapps plan (2021)** | Original source of "GBR" and the simplified/consolidated compensation idea. Background only. | n/a | (not searched; background knowledge, UNCERTAIN as a citation) |
| **ORR revenue-protection review recommendations** | DfT said (Mar 2026) the Delay Repay simplification follows ORR revenue protection review recommendations. No published DfT reply found. | UNCERTAIN | [Transport Focus](https://www.transportfocus.org.uk/news/transport-focus-comment-on-changes-to-delay-repay/) |
| **Full automation** | **Not promised.** Transport Focus is publicly pressing for automation once GBR exists ("must go further and make the process automated"). Government language is "one easy-to-use service" and "simplified", not automatic payouts. | None | [Transport User Voice, Mar 2026](https://www.transportfocus.org.uk/cy/news/transport-user-voice-march-2026-delays-and-compensation/) |
| **Rail Ombudsman** | Recommended (ORR casework deep dive) that automatic Delay Repay be investigated further; handles rejected-claim appeals (Caledonian Sleeper and others point passengers to it). No standalone Ombudsman statement on automation found. | n/a | [ORR deep dive](https://www.orr.gov.uk/sites/default/files/2024-07/rail-ombudsman-casework-deep-dive-report-2024.pdf), [Ombudsman handbook](https://media.railombudsman.org/Common_Complaints_Likely_Outcomes_Handbook_Oct25_7f045e72c9.pdf) |

Other points:

- Institute for Rail Research (via Rail Magazine) calls for "parity of access" to Delay Repay across ticket vendors. Trainline's "Fair Play on Delay Repay" campaign (Jan 2026) argued the one-click tools exclude independent retailers and estimated over £80m/yr unclaimed (company estimate, commercial interest). [Trainline press](https://www.trainlinegroup.com/media/en/press-releases/delayed-rail-passengers-losing-out-more-gbp80mn-each-year-unclaimed-compensation-due-delay-repay-frustration/), [Rail Gazette](https://www.railwaygazette.com/uk/trainline-calls-for-third-party-ticket-sellers-to-be-able-to-offer-one-click-delay-repay/70393.article).
- Taxpayer cost of delay payouts in England and Wales: about £169m in 2025-26, up 12% (REPORTED, Telegraph/AOL piece cited via Rail Magazine). [AOL](https://www.aol.co.uk/articles/400m-bill-britain-rail-failures-050000000.html)

---

## 4. Claim-rate data

| Metric | Value | Date | Label | Source |
|---|---|---|---|---|
| Share of passengers who claimed for their most recent eligible delay | **45%** (down 2pp from 47% in 2023; first fall since 2016) | 2025 survey (DfT/Transport Focus) | VERIFIED-ish (quoted from ORR factsheet and Transport Focus) | [Transport Focus](https://www.transportfocus.org.uk/cy/news/transport-user-voice-march-2026-delays-and-compensation/), [ORR factsheet P8-10 2025-26](https://dataportal.orr.gov.uk/media/vbnipogc/delay-compensation-claims-factsheet-2025-26-rail-periods-8-10.pdf) |
| Eligible under DR30 who claimed | 51% (54% in 2023) | 2025 | VERIFIED-ish | ORR factsheet above |
| Eligible under DR15 who claimed | 34% (35% in 2023) | 2025 | VERIFIED-ish | ORR factsheet above |
| London and South East commuters | 43% (down from 47%; DfT calls it significant) | 2025 | REPORTED (third-party analysis of DfT data) | [DfT delays and compensation 2025](https://assets.publishing.service.gov.uk/media/698df9dd492ea446ea7f4358/rail-delays-and-compensation-2025.pdf) |
| Trend | 35% (2016) rising to 47% (2023) then 45% (2025) | 2016-2025 | REPORTED | Untap / DfT survey series |
| Cause per Transport Focus | Manual re-entry of journey details at some operators; satisfaction with the process itself stays high | 2026 | VERIFIED-ish | Transport Focus |
| Claims closed by TOCs 2025-26 (GB) | 9.10m, up 9.5%; 80.5% approved (down 1.1pp); 99% closed within 20 working days | Apr 2025-Mar 2026 | VERIFIED-ish | [ORR annual consumer report 2025-26](https://www.orr.gov.uk/annual-rail-consumer-report-2025-2026) |
| Claims closed Apr-25 Jul 2026 (P1-4) | **3.8m, up 55% year on year**; 83.6% approved; 99.1% closed within 20 working days. Cancelled trains up by a third, stations arrived 15+ min late up 39%. 22 operators up; LNER +125%, EMR +115% (238,897). ORR does not attribute cause. | 2026-27 | VERIFIED-ish (ORR factsheet via search) | [ORR factsheet P1-4 2026-27](https://dataportal.orr.gov.uk/media/52abf1ay/delay-compensation-claims-factsheet-2026-27-rail-periods-01-04.pdf) |
| Share of claims received automatically | 11% (2023) down to 8% (2025) | 2023-2025 | REPORTED (Untap audit, 24 operators, FY2024-25 ORR/DfT data) | [Untap Rail Index](https://untap.money/rail-index) |
| Unclaimed value | about £80-90m/yr (private estimates); Untap says about one third of money owed unpaid in 2024-25 | 2024-26 | REPORTED, commercial interest | [Trainline press](https://www.trainlinegroup.com/media/en/press-releases/delayed-rail-passengers-losing-out-more-gbp80mn-each-year-unclaimed-compensation-due-delay-repay-frustration/), [Untap](https://untap.money/rail-index) |
| Which? | I did not find a current Which? claim-rate survey. Which? has called for automatic compensation (undated). | n/a | UNCERTAIN | [Scotsman (undated)](https://www.scotsman.com/news/scottish-news/scotrail-named-and-shamed-as-one-of-the-worst-companies-for-compensation-claims-547067) |
| Older DfT benchmark | 25% of eligible passengers got compensation owed (DfT 2020 research cited by ORR) | 2020 | REPORTED, old | ORR consultation material |

Caution: survey claim rates (share of eligible passengers) and ORR volumes (claims closed) measure different things and must not be divided into each other. The 55% volume jump in 2026 alongside a 45% survey rate suggests either far more disruption (cancellations +33%) or more claims per claimant, or both. Not attributable to automation on the evidence found.

---

## 5. Implications for the project

**Already (mostly) solved, for direct bookers**
- Passengers who book direct with an operator that offers an opt-in scheme (LNER, Avanti, GWR, Southeastern, TPE, SWR, Lumo, Caledonian Sleeper, Northern if still live) or who use the GTR/c2c/SWR/GWR smartcards get a pre-filled claim or voucher with little effort. c2c is fully solved for smartcard users. The product adds little for these people, except: (a) reminding them to opt in before travel, (b) catching multi-operator journeys the automation misses, (c) checking the amount.

**Where the gap remains**
1. **Third-party bookings (Trainline, TrainPal, other retailers; about 26% of passengers per DfT).** No operator auto scheme covers them as of Oct 2026. Trainline only shows a link to the operator form. This is the strongest wedge: the agent can detect the delay from open data, assemble evidence (booking reference, e-ticket, delay data) and draft the operator form.
2. **Operators with no automation:** CrossCountry, ScotRail, TfW, Chiltern, WMR/LNR, EMR, Greater Anglia, Merseyrail, Hull Trains, Grand Central, Elizabeth line, Heathrow Express (and Avanti/others for non-Advance tickets). Includes high-volume manual flows (EMR was the second-biggest increase).
3. **Non-Advance / walk-up / paper tickets and season tickets** on operators whose auto schemes cover only Advance or e-tickets.
4. **Awareness and opt-in failures.** Most schemes need opt-in before travel; the 45% claim rate and 8% automatic share show people do not.
5. **Multi-leg, multi-operator, and split-ticket journeys**, where auto systems are reported to under-calculate (anecdotal, Rail Forums).
6. **Rejected claims and appeals** (ORR: about 17-20% rejected; Northern's complaints are mostly about claim rejections). An agent could help with the Rail Ombudsman route.

**Could GBR make the project obsolete? And when?**
- **Not before 2027, probably not fully before 2028.** The sequence: Railways Bill Royal Assent (target end-2026, but Lords committee may run into autumn and beyond) then GBR operational (target about mid-2027; one source says end-2027) then retailer-accessible consolidated Delay Repay (stated as taking effect once GBR is operational) then non-GBR operators opting in. RDG's interim national capability may arrive earlier, during 2027, if the Oct 2026 award lands on schedule. That is a plan, not a delivered product.
- **What GBR threatens:** the third-party-booking wedge (claim from Trainline in one place) and the "multiple portals" pain. A single national claim form with retailer access would remove most of the portal-hopping an agent solves. If it also moved to automatic payment from ticket-validation data (the Lot 2 e-ticket validation database hints at this), the value of a passenger-side agent would collapse for covered journeys.
- **What GBR does not obviously threaten:** government language is "simplified" and "one easy-to-use service", not automatic payout. Transport Focus is lobbying for automation, and the Bill amendment on "automate where practicable" was not confirmed as adopted. Open-access operators, TfL and Heathrow Express (Merseyrail too) are outside GBR and opt in only voluntarily. Evidence preparation, delay verification against open data, multi-journey monitoring, and appeals will likely remain useful, but as a thinner layer.
- **Strategic reading:** treat this as a 12-24 month window. Build for the multi-operator, third-party-ticket, and non-automated cases now; design the agent so the "submit" step can later target the consolidated GBR/RDG service (one adapter) instead of N operator portals. Watch: the RDG contract award for Lot 1; whether the platform has a public API or only a web form; any consultation on retailer opt-in; Lords amendments to the compensation clause.

**Follow-ups worth doing (not possible this session)**
- Open each operator's page directly (WebFetch was blocked) and confirm thresholds, auto eligibility and payment methods.
- Identify claim-portal vendors by inspecting the actual forms.
- Confirm Northern's current auto scheme, LNER/CrossCountry/ScotRail thresholds, Chiltern's DfTO transfer, and which operators fall in DfT's "ten of fourteen".
- Check whether the RDG consolidated-platform award was made on 19 Oct 2026 and to whom.

---

## 6. Sources

Primary / near-primary (read via search summary, not opened):
- DfT press release, 17 Mar 2026: https://www.gov.uk/government/news/delay-repay-changes-will-make-rail-travel-easier-under-great-british-railways
- Hansard written answer "Railways: Compensation" (TheyWorkForYou mirror): https://www.theyworkforyou.com/wrans/?id=2026-07-13.18291.h
- Railways Bill report-stage amendments, 15 May 2026: https://publications.parliament.uk/pa/bills/cbill/59-02/0001/amend/railways_rm_rep_0515.pdf
- Hansard, Railways Bill (Commons, 10 Jun 2026): https://hansard.parliament.uk/commons/2026-06-10/debates/D04D1360-E0F8-4D80-B4B4-E9EF69FA9B39/RailwaysBill
- Hansard, Railways Bill (Lords, 16 Sep 2026): https://hansard.parliament.uk/Lords/2026-09-16/debates/40DD2BD5-AFFB-4985-A3E3-EB64F9CF7D6D/RailwaysBill
- Commons Library, Railways Bill 2024-26: https://commonslibrary.parliament.uk/research-briefings/cbp-10386/
- Bill stages: https://bills.parliament.uk/bills/4030/stages
- Find a Tender, Consolidated Delay Repay Service: https://www.find-tender.service.gov.uk/Notice/026489-2026
- ORR delay compensation factsheet P1-4 2026-27: https://dataportal.orr.gov.uk/media/52abf1ay/delay-compensation-claims-factsheet-2026-27-rail-periods-01-04.pdf
- ORR factsheet P8-10 2025-26: https://dataportal.orr.gov.uk/media/vbnipogc/delay-compensation-claims-factsheet-2025-26-rail-periods-8-10.pdf
- ORR factsheet P11-13 2025-26: https://dataportal.orr.gov.uk/media/ittbwvrh/delay-compensation-claims-factsheet-2025-26-rail-periods-11-13.pdf
- ORR annual rail consumer report 2025-26: https://www.orr.gov.uk/annual-rail-consumer-report-2025-2026
- ORR operator performance and improvement actions: https://www.orr.gov.uk/complaints-handling-and-delay-compensation-operator-performance-and-continuous-improvement-actions
- DfT, Rail delays and compensation 2025: https://assets.publishing.service.gov.uk/media/698df9dd492ea446ea7f4358/rail-delays-and-compensation-2025.pdf
- Transport Focus, Transport User Voice March 2026: https://www.transportfocus.org.uk/cy/news/transport-user-voice-march-2026-delays-and-compensation/
- Transport Focus comment: https://www.transportfocus.org.uk/news/transport-focus-comment-on-changes-to-delay-repay/
- DfTO newsroom: https://dfto-newsroom.prgloo.com/news/dfto-takes-next-steps-towards-great-british-railways
- DfTO annual report 2025-26: https://assets.publishing.service.gov.uk/media/6a5e3d7a30f5842e1f5a5eb3/dfto-ara-report-25-26.pdf
- GOV.UK, GTR transferred to public ownership: https://www.gov.uk/government/news/gtr-services-transferred-to-public-ownership
- Rail Ombudsman handbook Oct 2025: https://media.railombudsman.org/Common_Complaints_Likely_Outcomes_Handbook_Oct25_7f045e72c9.pdf
- ORR Rail Ombudsman deep dive 2024: https://www.orr.gov.uk/sites/default/files/2024-07/rail-ombudsman-casework-deep-dive-report-2024.pdf

Operator pages (via search summary):
- Avanti: https://avantiwestcoast.co.uk/help/delay-repay and https://www.avantiwestcoast.co.uk/tickets-and-savings/ways-to-save/promotion
- LNER: https://www.lner.co.uk/help-and-support/delay-repay/
- Thameslink / Great Northern / Southern auto DR: https://www.thameslinkrailway.com/help-and-support/delay-repay/auto-delay-repay ; https://www.greatnorthernrail.com/help-and-support/journey-problems/delay-repay-compensation/auto-delay-repay ; https://www.southernrailway.com/help-and-support/delay-repay-compensation/auto-delay-repay
- c2c: https://www.c2c-online.co.uk/tickets-and-fares/automatic-delay-repay/ ; https://www.c2c-online.co.uk/help_centre/compensation/when-am-i-eligible-for-automatic-delay-repay/
- GWR: https://www.gwr.com/help-and-support/refunds-and-compensation/automated-delay-repay
- Southeastern: https://www.southeasternrailway.co.uk/help/support/faqs/refunds/one-click-delay-repay-faqs
- SWR (indirect): https://www.itso.org.uk/news/news/smart-automatic-refunds-on-south-western-railway ; https://www.gov.uk/government/news/half-of-departments-rail-operators-now-delivering-improved-delay-repay-compensation
- Northern: https://northernrailway.co.uk/delay-repay ; https://www.northernrailway.co.uk/delay-repay-performance-and-continuous-improvement-report
- TPE: https://www.tpexpress.co.uk/help/delay-repay-compensation/automated-delay-repay
- CrossCountry: https://www.crosscountrytrains.co.uk/delay-repay
- ScotRail: https://www.scotrail.co.uk/about-scotrail/our-delay-repay-guarantee
- TfW: https://tfw.wales/delay-repay
- Chiltern: https://press.chilternrailways.co.uk/news/chiltern-railways-launch-delay-repay-15-compensation-scheme
- London Northwestern / West Midlands Railway: https://www.londonnorthwesternrailway.co.uk/delay-repay ; https://www.westmidlandsrailway.co.uk/delay-repay
- EMR: https://eastmidlandsrailway.co.uk/help-manage/manage/make-a-delay-repay-claim
- Greater Anglia: https://www.greateranglia.co.uk/delayrepay
- Merseyrail: https://help.merseyrail.org/hc/en-gb/articles/14723310591132-Single-Return-Ticket-Compensation-Information
- Lumo: https://lumo.co.uk/help/delay-repay
- Caledonian Sleeper: https://www.sleeper.scot/?p=848
- TfL Overground/Elizabeth line: https://tfl.gov.uk/fares/refunds-and-replacements/overground-and-tfl-rail-delays
- Heathrow Express: https://www.heathrowexpress.com/help-centre/HelpTopic/how-can-i-claim-compensation-if-my-train-is-delayed/
- Seatfrog (third-party booking limitation): https://help.seatfrog.com/hc/en-gb/articles/6188991526415-What-should-I-do-if-my-Superfare-train-was-delayed
- Trainline support: https://support.thetrainline.com/hc/en-gb/articles/5170397531807-My-UK-train-was-delayed-Can-I-claim-compensation

Press / trade / third-party (REPORTED):
- Untap Rail Index 2026: https://untap.money/rail-index ; https://untap.money/guides/train-delay-repay/transpennine-express
- Trainline press release (Fair Play on Delay Repay): https://www.trainlinegroup.com/media/en/press-releases/delayed-rail-passengers-losing-out-more-gbp80mn-each-year-unclaimed-compensation-due-delay-repay-frustration/
- Railway Gazette, Trainline call: https://www.railwaygazette.com/uk/trainline-calls-for-third-party-ticket-sellers-to-be-able-to-offer-one-click-delay-repay/70393.article
- Rail Business UK, third-party retailers: https://www.railbusinessuk.com/passenger/2026/03/18/consolidated-delay-repay-service-to-include-third-party-rail-ticket-retailers/
- Rail Business UK, procurement: https://www.railbusinessuk.com/ticketing/2026/06/08/procurement-of-consolidated-train-delay-repay-service-begins/
- Rail Magazine, notice issued: https://www.railmagazine.com/news/notice-issued-for-consolidated-delay-repay-platform
- Rail Magazine, IRR report: https://www.railmagazine.com/news/irr-calls-for-urgent-delay-repay-reform-in-new-report
- Rail Magazine, Chiltern handover: https://www.railmagazine.com/news/dfto-handover-date-announced-for-chiltern-railways
- Railnews: https://railnews.mobi/news/2026/03/17-delay-repay-system-to-be.html
- Rail Technology Magazine: https://www.railtechnologymagazine.com/articles/delay-repay-overhaul-promises-faster-simpler-compensation-rail-passengers
- Bird & Bird, Railways Bill update Aug 2026: https://www.twobirds.com/en/insights/2026/uk/railways-bill-update---august-2026
- Parallel Parliament, Railways Bill: https://www.parallelparliament.co.uk/bills/2024-26/railways
- Rail Forums on LNER one-click: https://www.railforums.co.uk/threads/one-click-automatic-delay-repay-systems-are-useless.299127/
- Scottish Liberal Democrats, ScotRail payments: https://www.scotlibdems.org.uk/news/article/scotrail-disruption-payments-top-pound3-million
- MoneySavingExpert, train delays: https://www.moneysavingexpert.com/reclaim/train-delays/
- MyTrainPal operator guide: https://www.mytrainpal.com/guide/train-companies-delay-repay
- BritBrief on 55% claims rise: https://britbrief.co.uk/business/transport/rail-delay-compensation-payouts-soar-55-across-network.html
- Telegraph/AOL on cost to taxpayers: https://www.aol.co.uk/articles/400m-bill-britain-rail-failures-050000000.html
