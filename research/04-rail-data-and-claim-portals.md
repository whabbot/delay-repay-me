# 04 - Rail data sources for delay verification, and operator claim portals

Research date: 2026-10-19. Slice: (A) open data for verifying a past journey's delay, (B) operator Delay Repay claim portals.

## Method and confidence caveat (read first)

- **WebFetch was unusable in this session.** Every fetch failed (DNS, then a 403 from the egress proxy for hosts such as wiki.openraildata.com). All findings come from WebSearch result summaries, not from reading the primary pages in full.
- Labels used throughout:
  - **VERIFIED**: stated on a primary or official page (operator, RDG, National Rail, Network Rail, Realtime Trains, gov.uk, Find a Tender), as quoted in search results.
  - **REPORTED**: press, trade press, blog, forum, third-party library README, or secondary summary.
  - **UNCERTAIN**: not confirmed, or sources conflict.
- No operator Terms of Use were read. Section 4.4 is therefore a list of gaps. Do not treat it as legal clearance.
- Dates matter. The Open Rail Data wiki NRDP page was flagged as roughly 1,200 days old in search metadata, so it is stale on timing.

---

## 1. Summary

- **Recommended verification source for v1: Historical Service Performance (HSP) via the Rail Data Marketplace (RDM).** It is Darwin-derived, free once you register on RDM, and returns scheduled vs actual times per stop plus cancellation/late reason codes for up to about 1 year back. That covers the 28-day claim window easily. Known weaknesses: undocumented/strict rate limits (sustained 429s reported July 2026), some data gaps, and an old SOAP-era-style integration surface that has been moving platforms.
- **Realtime Trains (RTT) Next Generation API (data.rtt.io, launched March 2026)** is a good second source and a cross-check. The legacy api.rtt.io is turned off (shutdown date quoted variously as 30 Sep or 1 Oct 2026). The free tier is **non-commercial only** with small rate limits (10/min, 100/hr, 1,000/day per the revised blog update). Commercial use needs a paid or enterprise plan. Treat RTT as a cross-check, not the legal basis.
- **Network Rail feeds (TRUST/VSTP/SCHEDULE/TD) are the raw layer.** They are stream- or file-oriented and suited to building your own archive. They are the wrong tool for an on-demand "was my train late?" lookup. Fine as a later, self-hosted option.
- **No evidence found that a single white-label vendor runs several TOC portals.** Portal hostnames follow a `delayrepay.<operator-domain>` pattern for GWR, Thameslink, Southern and TPE, which hints at shared software or at least shared conventions, but no vendor was named in anything I could read. The only confirmed consolidation is a **future** one: RDG is procuring a single national Delay Repay platform (tender published 4 June 2026, award reportedly planned for 19 October 2026, contract starting 30 October 2026), and the government says claims will eventually be made through the retailer where the ticket was bought.
- **Biggest project risk is not data, it is the claim side.** There is no public claims API. Portals need ticket evidence and payment details. Automated form-filling may breach portal terms (unverified either way), and the whole claim landscape is about to be reorganised under Great British Railways. The "draft and stop for passenger approval" design is the right posture.

---

## 2. Data source comparison and recommendation

### 2.1 Comparison table

| Source | Covers actual arrival at destination? Cancellations? | History depth | Cost / registration | Licence and limits | Integration difficulty | Status confidence |
|---|---|---|---|---|---|---|
| **HSP (Historical Service Performance)**: JSON API with `serviceMetrics` and `serviceDetails`; on RDM as an open API product | Yes. Per-stop scheduled vs actual times for a given service. Query by origin/destination, date/time window, operator. Includes late/cancellation reason codes (`late_canc_reason`, numeric). | Up to about 1 year (National Rail) | Free; needs RDM account and subscription to the HSP product. | Rate limits not documented in anything I found; a July 2026 post reports sustained 429s after about one route-month of pulls. No CORS support. Licence terms on RDM not read (UNCERTAIN). | Low to medium. Two-step: metrics lists service RIDs, details gives per-stop times. Reason-code lookup table is a known pain point. | REPORTED/VERIFIED: existence, 1-year depth and "free once you sign up to RDM" are stated by National Rail and data.gov.uk (collection updated 24 Mar 2026). |
| **Darwin Push Port** (XML push, near-real-time) | Live predictions and actuals while the train runs; you must capture at the time. | None natively. RDM offers hourly "snapshots" for resync only. A community member reports holding push port data back to 7 Sep 2025 (REPORTED). | Free via RDM registration. | Darwin has historically sat under an NRE licence based on OGL v2.0 with amendments and high-volume thresholds (REPORTED, undated). | High (stream consumer, XML, state management). | Good for live tracking of a journey in progress, not for after-the-fact proof. |
| **LDBWS / OpenLDBWS (Live Departure Boards)**: SOAP, with a REST product on RDM | Current departure/arrival boards only. Board for a station shows trains in a window around "now". Not a historical record. | About 2 hours either side of now, essentially none (UNCERTAIN on exact window). | Free open tier on RDM ("LDBWS - Public"), reportedly instant approval (REPORTED). Historic usage cap about 5,000 requests/hr (2019 reply, old). | Legacy SOAP tokens reportedly don't work with REST clients (REPORTED). | Low. | Not suitable for post-journey proof. Useful for in-journey capture. |
| **Realtime Trains Next Generation API** (https://data.rtt.io, tokens via api-portal.rtt.io; spec at realtimetrains.github.io/api-specification) | Yes: GB-wide services with scheduled/actual/forecast times and cancellations (entitlements can restrict detail). | Free tier history restricted. A paid "Professional" plan reportedly extends to 365 days; Enterprise says "Extended History back to 2012". Free-tier lookback not found (UNCERTAIN). The website's RTT+ "Extended History" is 5 years but personal use only. | Free tier: personal projects/prototypes, **non-commercial only**. Paid plans launched July 2026 (a £4/month hobbyist plan reported, individuals only). Enterprise plan for commercial. | VERIFIED limits were 30/min, 750/hr, 9,000/day, 30,000/week at launch, revised down to 10/min, 100/hr, 1,000/day after the 6-month transition (RTT blog, as quoted). Terms at realtimetrains.co.uk/legal/. Branding/attribution terms not read. | Low. Modern JSON, OpenAPI 3.1 spec, bearer token. | VERIFIED launch/deprecation. Old api.rtt.io is off: dates conflict (30 Sep vs "31 September" vs "disabled since 1 Oct 2026"). Avoid any tutorial that uses api.rtt.io. |
| **Network Rail Open Data: TRUST Train Movements** (ActiveMQ/STOMP topics) | Actual passing/arrival/departure at timing points, cancellation messages. Timing points only (not every station call). | None (live stream only). You must archive it yourself. | Free; account at publicdatafeeds.networkrail.co.uk. | OGL-based licence, brand restrictions (no "official" naming, no Network Rail/TOC logos), no uptime guarantee, user cap (1,000, page undated). Commercial use not explicitly confirmed in what I found. | High (stream plus mapping to schedule). | Still described as current on the Open Rail Data wiki and used by RTT. I could not confirm whether any Network Rail feeds moved to RDM (UNCERTAIN). |
| **Network Rail SCHEDULE (CIF), VSTP, TD, TSR, reference data** | SCHEDULE is the planned timetable. VSTP is late-notice schedule changes. TD is signalling berth steps. | SCHEDULE is daily/weekly full and update files. VSTP and TD are live streams. | Same as TRUST. | Same as TRUST. | High. Needed only if you build your own pipeline. | VERIFIED as listed on the Open Rail Data wiki. |
| **Huxley / Huxley 2** (open-source proxy that wraps LDBWS as JSON) | Same as LDBWS: live boards only. | None. | Self-hosted; you bring your own LDBWS token. | Open source. | Low, but maintenance status in 2026 unconfirmed. | UNCERTAIN: no 2026 status found. |
| **TransportAPI** (commercial) | Rail endpoint exists for real-time and scheduled departures/arrivals. | No historical rail data found. | Paid; free-tier numbers conflict (30/day vs 1,000/day, both undated). | Unclear. | Low. | UNCERTAIN. Not recommended. |
| **Trainline and other consumer APIs** | No public partner API found for delay or claim data. | n/a | n/a | Trainline says it can detect delays and prompts users to claim on the operator site. It says access to "1-click" Delay Repay is denied to independent retailers (campaign claim). | n/a | Not a viable data source. |
| **Third-party aggregators built on HSP** (e.g. recenttraintimes.co.uk) | Historical train times for a station pair. | Unknown | Free website | Unknown | Scraping a third-party site is a poor idea. | Useful only as a manual sanity check. |

### 2.2 Platform context: where Darwin/HSP now live

- National Rail's developer page presents the Rail Data Marketplace as "the new platform for access to both public and private sector rail data" and says Darwin "also drives our Historic Service Performance (HSP) webservice, allowing access to what happened to the train service up to 1 year ago". (VERIFIED, via search summary of https://www.nationalrail.co.uk/developers/ and https://nre.co.uk/developers/)
- The RDM catalogue lists HSP as an open API product and has a "Darwin Real Time Train Information snapshots" product. (VERIFIED/REPORTED: raildata.org.uk catalogue pages seen in search results; I did not open them.)
- The legacy National Rail Data Portal (NRDP) is being retired. The Open Rail Data wiki said "early 2026" (stale). The NRDP sign-in page reportedly says "shutting down later in 2026" with six months' notice, and states that all NRDP users must migrate to RDM. A third-party doc says it was already retired. **Timing is UNCERTAIN, but the direction is clear: build on RDM, not NRDP.**
- A planned Darwin cut-over was reported on openraildata-talk as postponed with no replacement date (REPORTED). Watch this list.

### 2.3 Recommendation

For "after the journey, prove arrival was X minutes late at station Y":

1. **Primary: HSP on RDM.** It was designed for exactly this question (what did the train actually do, up to a year ago), it is derived from the same Darwin data the industry uses, and it returns actual arrival at the destination plus cancellation status. It is free. Cache aggressively (one lookup per journey leg per claim), queue requests and back off on 429s. Store the raw JSON response, the request parameters and a timestamp as the evidence record.
2. **Secondary: RTT Next Generation API** as an independent cross-check and for friendlier service lookup (finding the right service by time and station). Free tier is non-commercial only, so a commercial product needs a paid/enterprise plan. Confirm terms before shipping.
3. **Later, if HSP limits or gaps bite:** run your own TRUST/Darwin archive. Only worth it at scale, and it is significant engineering.
4. **Do not use** LDBWS or Huxley for post-journey proof. Do use Darwin/LDBWS only if you add a live "journey in progress" capture feature.
5. **Cross-check policy:** if HSP and RTT disagree by 1 minute or more near a compensation band boundary (14/15, 29/30, 59/60, 119/120 minutes), show both values to the passenger and flag the claim as borderline rather than asserting a band.

Open items to resolve with a real RDM account (I could not read the docs): HSP's actual rate limits and reset window; whether the HSP licence permits commercial use and requires attribution; the `late_canc_reason` code lookup; HSP coverage gaps (a forum thread about HSP gaps exists, details not read).

---

## 3. How Delay Repay delay is measured, and pitfalls

### 3.1 Rules found

| Rule | Detail | Source and confidence |
|---|---|---|
| Delay is measured at the passenger's **final destination on the ticket**, as arrival time vs scheduled arrival | Avanti: delay is measured by arrival at your destination vs scheduled arrival, not delay at departure. For journeys with connections the whole journey on the ticket is considered. TfW: scale based on the time you should have arrived at your final destination station, not delay to any particular train. | Avanti help page and Passenger Charter 2026; TfW page. VERIFIED (operator pages, via search summaries). |
| Standard threshold is **15 minutes** at most operators | Typical bands: 15-29 min = 25% of a single fare; 30-59 = 50%; 60-119 = 100% (Avanti single; returns 12.5/25/50% for the same bands); TfW 120+ = 100% of single. | Avanti, TfW. VERIFIED. Avanti charter says compensation applies "no matter what caused it". |
| Some operators differ | ScotRail's page said 30 minutes (page referenced claims before 26 Nov 2025, so possibly changed since). | REPORTED/UNCERTAIN. Must be a per-operator config, kept current. |
| **28-day claim window** from the date of the delayed journey | Southeastern, SWR, GWR (date GWR *receives* the claim), Avanti (citing its Passenger's Charter and the National Rail Conditions of Travel), Stansted Express, others. | Operator pages, VERIFIED. No evidence found of a change to 3 months. |
| Multi-operator journeys on one ticket | Southeastern: claim via the operator that caused the *first* delay to the whole journey. | Southeastern page, VERIFIED. |
| Separate tickets / missed connections | Forum evidence of claims bounced between operators and unpaid. | Forum anecdotes only. REPORTED. Treat as high-risk, hand to the human. |
| The delay must be to a service run by that operator | A trainsplit summary says the journey must have been on the claimed operator's train. | REPORTED. |
| Compensation basis is the **timetable at the time of travel** | Roomex (non-official) says delay is compared with the regular timetable or an advance-notice modified timetable (e.g. engineering works). | REPORTED. UNCERTAIN how each operator treats pre-notified timetable changes. Needs the operator's charter. |

### 3.2 Pitfalls for automation

1. **Cancellation vs delay.** A cancelled train is compensated by the delay to the passenger's *actual* arrival on the replacement service (or, if they did not travel, refund rules apply). The agent needs the passenger's actual onward train, not just the cancelled one. HSP shows the cancelled service and reason, but not which train the passenger actually took.
2. **Rerouting / diversions.** Arrival at destination via a diverted service should still be measured at the ticket destination. HSP/RTT `scheduled` for a diverted service may differ from the original plan. Prefer comparing to the original booked service's scheduled arrival where known.
3. **Connections.** Which train did the passenger actually board at each leg? Passenger testimony is needed for *which* train they took, though the delay itself must come from open data. Design: the passenger selects the service from a list of candidates, and the agent verifies it.
4. **"Nominated train" for Advance tickets.** Advance tickets are valid only on the booked train. I could not find an official statement of the exact Delay Repay rule (UNCERTAIN). Operators including Avanti say claims on Advance tickets bought direct can be automatic, so presumably measured against the booked train's scheduled arrival. If the passenger took a different train, expect operator-specific rules. Flag for review rather than auto-compute.
5. **Delay measured at "arrival" means arrival at the platform, not doors open or exit.** Data gives timing at the station. Edge cases (terminating at a different station, e.g. London termini vs "London Terminals" groupings) need station-group mapping.
6. **Boundary rounding.** Darwin/HSP times are to the minute. Operators decide on the minute displayed. Keep the raw time and the minute value. Show both.
7. **Time zones and cross-midnight services.** Use UK local time with service-date (RSID/RID) semantics, not calendar date.
8. **Data gaps.** HSP is derived from Darwin, which can lack actuals if a train was not tracked. A missing record is not evidence of on-time running. Fall back to RTT or tell the passenger honestly that verification failed.
9. **28-day clock.** Compute and surface a "claim by" date per operator, and treat anything after day ~21 as urgent.
10. **Operator causation.** The claim goes to the operator whose train is late or cancelled (or caused the first delay). Per-operator rules differ.

### 3.3 National Rail Conditions of Travel, and the Consumer Rights Act

- Avanti says the 28-day limit comes from "our Passenger's Charter and the National Rail Conditions of Travel". (VERIFIED as a statement by Avanti; I did not read the NRCoT text itself. The Delay Repay specifics are really in each operator's Passenger's Charter. UNCERTAIN how much is in the NRCoT proper.)
- Who can claim: ticket holders who actually travelled and arrived late; holders of Advance/Anytime/off-peak/season tickets, with season tickets assessed through season-ticket Delay Repay rules. (REPORTED/general; not verified per-operator.)
- Evidence required (Southeastern, VERIFIED): travel date, scheduled departure time, origin, interchange stations and destination; plus a ticket reference. For Oyster/contactless: a journey statement or season record. Third-party retailer order references are not accepted. Contactless card statements must show time of travel.
- **Consumer Rights Act 2015** (REPORTED via Which? and Resolver): where Delay Repay does not apply or is insufficient, a passenger may claim consequential financial loss because the operator did not provide the service with "reasonable care and skill". Does not apply to delays caused by factors outside the operator's control. ScotRail also says extra costs may be claimable under the Act on a case-by-case basis. This is a fallback and a differentiator, but out of scope for automated claims.
- **Policy change, March 2026:** government announced refunds for unused tickets restricted to before 23:59 on the day before travel (from 1 April 2026), separate from Delay Repay. Relevant if the agent ever advises "don't travel, refund the ticket". (REPORTED: Railnews, thinkmoney, GOV.UK press release.)

---

## 4. Claim portal landscape

### 4.1 Shared platforms and vendors

I could not identify a vendor for any operator portal. What I did find:

| Finding | Evidence | Confidence |
|---|---|---|
| Portal hostnames follow `delayrepay.<operator domain>`: delayrepay.gwr.com, delayrepay.thameslinkrailway.com, delayrepay.southernrailway.com (online form at `/customer-details`), delayrepay.tpexpress.co.uk | Search result pages | VERIFIED that these hosts exist. UNCERTAIN whether they share software. |
| GTR family (Southern, Thameslink, and probably Gatwick Express/Great Northern) share a Derby postal address and similar registration/login flows | Southern page: postal form goes to a GTR address in Derby; account stores season ticket and repayment preferences | REPORTED/likely, vendor unknown. |
| Celaton "inSTREAM Delay Repay" product page exists | celaton.com/solutions/function/delay-repay (page about 2,400 days old) | UNCERTAIN: no link to any named operator. |
| LNER published a 2023 Prior Information Notice for "Delay Repay Platform development, support & management" | Find a Tender 008368-2023 (via bidstats) | VERIFIED that the PIN exists. Outcome unknown. |
| Arriva UK Trains (CrossCountry, Grand Central) tendered outsourced Delay Repay software in 2023, about £1.1m | Find a Tender 013749-2023 (via search summary) | VERIFIED that the notice exists. Winner unknown. |
| TPE page references old-system access for claims submitted before 18 October 2026 | Search summary of delayrepay.tpexpress.co.uk | UNCERTAIN: hints at a platform migration on or around 18 Oct 2026. I could not corroborate it. |
| **RDG is procuring a single "Consolidated/Centralised Delay Repay Service"** | Find a Tender notice 053093-2026 (published 4 Jun 2026, buyer Rail Settlement Plan Ltd). Est. total about £21.2m ex VAT, term 30 Oct 2026 to 30 Sep 2031 (extension to 2036). Lots: core platform and systems integrator (customer website plus back-office portal), eTVD ticket validation, print/postal. Award reportedly planned 19 Oct 2026. Earlier notice 026489-2026. | VERIFIED notice; award outcome UNCERTAIN (none found as of today). |
| Government plan: merge Delay Repay systems into one under Great British Railways; claims via the retailer used (including third-party apps); trials of a "simple verification process" later in 2026; depends on GBR being established | GOV.UK press release (17 Mar 2026), Railnews, Railway Gazette, Rail Magazine | VERIFIED announcement (GOV.UK, via search). Timeline UNCERTAIN. |
| Many operators run **Automated Delay Repay (ADR)** for their own Advance tickets or smartcards (GWR, SWR, Avanti, TPE, West Midlands Railway "one-click") | Operator pages | VERIFIED. Passenger still reviews and accepts. Limited to tickets bought direct. |

**Implication:** today there is no confirmed single white-label platform covering several operators that you could target with one integration. The practical strategy is a per-operator adapter. In 6 to 18 months the national platform may replace most of them, and its retailer-facing APIs (mentioned in the tender: "retailer-facing APIs", eTVD) are the likely sanctioned integration route.

### 4.2 Typical claim form fields

Consolidated from Southeastern (VERIFIED), plus Trainline, Avanti, Southern and Thameslink pages (VERIFIED/REPORTED):

- Journey: date, scheduled departure time, origin, interchange(s), destination; sometimes actual arrival time or delay length (ask passenger, but we supply verified data).
- Ticket type and proof: paper ticket copy/scan or photo; eTicket or sTicket reference (and barcode screenshot); Key smartcard number; season ticket copy/number; retailer reference when bought from a third party (some operators accept a copy only; third-party order numbers not accepted by Southeastern); Oyster/contactless journey statement. Price paid.
- Passenger: name, address, email; optional account.
- Payment/refund method: bank transfer, cheque, rail vouchers, or card refund (some operators). Southeastern's official page did not list bank details (UNCERTAIN). Forum posts say bank details are entered online.
- Declarations: truthfulness and fraud warnings (Southern states it reserves the right to prosecute fraudulent claimants).
- Response times: Southern says 20 working days.

### 4.3 Bot protection, accounts, public APIs

- **Bot protection:** I could not confirm CAPTCHA/reCAPTCHA/hCaptcha/Cloudflare on any portal. The search results did not describe it, and I could not load the pages. **UNCERTAIN.** Must be tested with a real browser session on each target portal, as part of the integration spike.
- **Accounts:** optional on Southeastern (guest or registered), Southern/Thameslink (account stores details; online form also available). Avanti requires registration on its Delay Repay portal if the ticket was bought elsewhere. TPE ADR requires sign-up with matching email. Mixed picture: assume per-operator.
- **Public APIs for claims:** none found. Trainline states the technology for "1-click" Delay Repay exists but that independent retailers are denied access (campaign claim by Trainline, not independently verified). The consolidated service tender mentions "retailer-facing APIs", which suggests this will open up (see 4.1).
- **Partner integrations:** none found for third-party agents. East Midlands Railway reports fraud-detection controls with referral to an agent for review, which means automated submissions may be scrutinised.

### 4.4 Terms-of-use clauses on automated access

**Not verified.** I was unable to read the terms of any operator portal. A search for GWR's website terms returned Guinness World Records' terms by mistake and nothing on the railway. Action required before any portal automation:

- Read the website terms, the Delay Repay conditions, and robots.txt for each portal (GWR, GTR/Southern/Thameslink, Avanti, Southeastern, LNER, TPE, Northern).
- Look for clauses on "automated means", "robots", "scraping", "agents", and whether claims may be submitted by a third party on the passenger's behalf.
- Note that many UK TOC site terms contain a general ban on automated access (common practice), but I have no evidence for any specific one. Do not assume either way.

---

## 5. Implications for the project

### 5.1 Feasibility

- **Verification: feasible and cheap.** HSP on RDM plus RTT cross-check gives defensible, source-cited evidence of arrival delay for any journey in the last 28 days.
- **Entitlement calculation: feasible but operator-specific.** Needs a per-operator rules table (threshold, bands, single vs return, season ticket handling, claim window). Keep it as versioned config with a "last verified" date and source link. Some operators differ from the 15-minute norm.
- **Evidence assembly: feasible.** Package the HSP/RTT JSON, request parameters, timestamps, and a human-readable summary. Operators mainly want ticket proof, not delay proof, so the data evidence mostly protects the passenger in a dispute and supports the agent's own approval screen.
- **Portal drafting: feasible but fragile, and legally unclear.** No API, probable per-operator form differences, possible bot protection, unverified ToS. A human-in-the-loop design ("draft, attach evidence, stop for passenger to approve and submit") reduces risk and is consistent with passenger-controlled filing. It may still run into ToS limits if a bot fills the form.

### 5.2 Key risks

| Risk | Severity | Mitigation |
|---|---|---|
| Portal ToS or bot protection blocks automated drafting | High | Read ToS per operator; test with a real browser; consider generating a pre-filled summary the passenger pastes, or a browser extension that fills the form within the passenger's own session. Ask operators/RDG about a sanctioned route. |
| National consolidated Delay Repay platform replaces operator portals (reportedly from 30 Oct 2026 for the supplier contract, with GBR go-live later) | High (strategic) | Do not over-invest in per-operator scraping. Track the tender outcome and RDG retailer APIs. Build the core as operator-agnostic: verification + entitlement + evidence pack. |
| HSP rate limits or gaps | Medium | Cache; queue; RTT fallback; own TRUST/Darwin archive if it becomes a problem. |
| RTT free tier is non-commercial; terms/limits changing quickly (rate limits cut since launch; paid plans July 2026) | Medium | Budget for a paid plan if used commercially; keep RTT as optional cross-check. |
| NRDP retirement and Darwin cut-over timing | Medium | Register on RDM now; avoid NRDP/SOAP-only endpoints; subscribe to openraildata-talk. |
| Edge-case journeys (separate tickets, missed connections, Advance ticket on a different train) produce wrong entitlement | Medium | Detect and escalate to the passenger with a clear warning; do not auto-assert. |
| Ticket evidence is sensitive (barcodes, bank details, addresses) | Medium | Minimise storage; passenger supplies payment details in their own session. Do not store bank details. |
| Misstating compensation | Medium | Show the data source, the rule used and its date; require passenger approval. |

### 5.3 Suggested first integration

1. **Data layer:** HSP via RDM (primary) with RTT Next Gen API (cross-check), wrapped in a single `verifyArrival(service, destinationCRS, date)` interface that returns scheduled arrival, actual arrival, delay minutes, cancellation flag and reason code, plus raw payloads and sources.
2. **Operator rules table** for 3 to 5 big operators (suggest GTR family: Southern/Thameslink, GWR, Avanti, Southeastern, LNER), with source links per rule.
3. **First portal target:** one that offers a logged-in account and a plain web form, in a manual-assist mode (agent prepares fields and evidence; passenger pastes or confirms). Candidate: the GTR family (Southern + Thameslink, probably shared flow), since it covers multiple brands and appears to use a consistent form. UNCERTAIN until a spike confirms shared software and bot protection. Also consider GWR (large passenger base, ADR exists, `delayrepay.gwr.com`).
4. **Spike checklist (1-2 days):** register on RDM and test HSP queries with a real past journey; capture rate-limit headers; read the three portals' terms; load each form in a browser and record CAPTCHA/Turnstile behaviour; confirm how each handles guest vs account; confirm what evidence upload types are accepted.
5. **Watch list:** award notice for Find a Tender 053093-2026; RDG announcements on the national platform and retailer APIs; NRDP shutdown notice; RTT terms page; the Darwin cut-over thread.

---

## 6. Sources

Note: all were reached via WebSearch summaries. WebFetch was blocked, so none were read in full unless stated. "V" = official/primary, "R" = reported/secondary.

**Part A: data sources**
- [V] National Rail developers (Darwin, HSP up to 1 year, RDM as new platform): https://www.nationalrail.co.uk/developers/ and https://nre.co.uk/developers/ and https://www.nationalrail.co.uk/developers/darwin-data-feeds/
- [V] data.gov.uk "real time and historic train information" (HSP free after RDM sign-up; updated 24 Mar 2026): https://www.data.gov.uk/collections/transport/real-time-and-historic-train-information
- [V] Rail Data Marketplace product catalogue: https://raildata.org.uk/dataProducts?tagName=Performance+or+delays and Darwin snapshots product: https://raildata.org.uk/dataProduct/P-8b01d5cf-2dd4-48b4-bb98-dc6d3520baf9/discussion
- [R] Open Rail Data wiki, HSP: https://wiki.openraildata.com/index.php?title=HSP
- [R] Open Rail Data wiki, RDM feeds: https://wiki.openraildata.com/index.php/Rail_Data_Marketplace/Feeds
- [R] Open Rail Data wiki, NRDP (retirement "early 2026", stale): https://wiki.openraildata.com/index.php?title=National_Rail_Data_Portal
- [R] Open Rail Data wiki, National Rail feeds: https://wiki.openraildata.com/index.php/About_the_NRE_Feeds and https://wiki.openraildata.com/index.php/AtocIndustryData
- [R] Open Rail Data wiki, Darwin Push Port: https://wiki.openraildata.com/index.php/Darwin:Push_Port
- [R] Official NRDP site (shutdown "later in 2026"): https://opendata.nationalrail.co.uk/
- [R] openraildata-talk, HSP rate limit thread (July 2026): https://groups.google.com/g/openraildata-talk/c/WKdjosrpimo
- [R] openraildata-talk, LDBWS limits (2019): https://groups.google.com/d/msgid/openraildata-talk/8f9bfb89-236c-4537-8592-345777e98013%40googlegroups.com
- [R] openraildata-talk, Darwin historic data: https://groups.google.com/g/openraildata-talk/c/yMWGdj3rG2M/m/VTnVIm9OAQAJ
- [R] openraildata-talk, NRDP update: https://groups.google.com/g/openraildata-talk/c/Z8wOISB3u8g/m/x_OQm5jLBwAJ
- [R] Darwin NRE licence summary (OGL v2.0 with amendments, undated): https://www.slideshare.net/slideshow/nre-developer-terms-conditions/35306536
- [V] Network Rail feeds licence: https://www.networkrail.co.uk/who-we-are/transparency-and-ethics/transparency/open-data-feeds/network-rail-infrastructure-limited-data-feeds-licence and https://www.networkrail.co.uk/who-we-are/transparency-and-ethics/transparency/open-data-feeds/
- [R] Open Rail Data wiki, Network Rail feeds and Train Movements: https://wiki.openraildata.com/index.php/About_the_feeds and https://wiki.openraildata.com/index.php/Train_Movements
- [V] Realtime Trains Next Generation API launch (27 Mar 2026): https://blog.realtimetrains.com/2026/03/next-generation-api-now-available/
- [V] Realtime Trains paid API plans (Jul 2026): https://blog.realtimetrains.com/2026/07/paid-api-plans-are-now-available/
- [V] Realtime Trains developer/data products page: https://www.realtimetrains.co.uk/about/developer/
- [V] Realtime Trains API spec: https://github.com/realtimetrains/api-specification and https://realtimetrains.github.io/api-specification/ ; portal https://api-portal.rtt.io/ ; legacy api.rtt.io https://api.rtt.io/ ; terms https://www.realtimetrains.co.uk/legal/
- [V] Realtime Trains data sources page: https://realtimetrains.co.uk/about/sources
- [V] RTT Extended History (website subscription, personal use): https://blog.realtimetrains.com/2026/01/rtt-extended-history-now-available and https://blog.realtimetrains.com/2025/10/rtt-extended-history-update
- [R] ParkSquare.RealTimeTrains README (old API end date, personal-use note): https://www.nuget.org/packages/ParkSquare.RealTimeTrains
- [R] Huxley: https://github.com/nickjupp/Huxley ; LDBWS REST on RDM (PHP client README): https://root.packagist.org/packages/harmonicdigital/ldbws
- [R] TransportAPI: https://apis.io/providers/transportapi/ and G-Cloud pricing doc https://assets.applytosupply.digitalmarketplace.service.gov.uk/g-cloud-15/documents/700359/142124778636881-pricing-document-2026-01-30-1405.pdf
- [R] recenttraintimes.co.uk: https://recenttraintimes.co.uk/Home/About

**Part B: portals, rules, consolidation**
- [V] Southeastern Delay Repay: https://www.southeasternrailway.co.uk/help/support/faqs/refunds/delay-repay
- [V] Avanti Delay Repay: https://www.avantiwestcoast.co.uk/help-and-support/delay-repay ; Passenger Charter 2026: https://www.avantiwestcoast.co.uk/-/media/avanti-pdfs/avanti-policies/passenger-charter-2026.pdf ; tables https://www.avantiwestcoast.co.uk/-/media/avanti-pdfs/help-and-support-pdfs/delay-repay-tables/delay-repay-01-april-2025--31-march-2026.pdf
- [V] Southern Delay Repay: https://www.southernrailway.com/help-and-support/delay-repay-compensation and https://www.southernrailway.com/your-journey/customer-services/delay-repay/delay-repay-form
- [V] Thameslink Delay Repay: https://delayrepay.thameslinkrailway.com/ and https://www.thameslinkrailway.com/help-and-support/delay-repay
- [V] GWR: https://delayrepay.gwr.com/ and https://www.gwr.com/help-and-support/refunds-and-compensation/automated-delay-repay
- [V] TPE: https://delayrepay.tpexpress.co.uk/ and https://www.tpexpress.co.uk/help/delay-repay-compensation/automated-delay-repay
- [V] SWR: https://www.southwesternrailway.com/contact-and-help/delay-repay
- [V] TfW: https://tfw.wales/delay-repay ; ScotRail: https://www.scotrail.co.uk/delay-repay ; West Midlands Railway: https://www.westmidlandsrailway.co.uk/delay-repay ; Northern: https://northernrailway.co.uk/delay-repay ; Stansted Express: https://www.stanstedexpress.com/help/delay-repay
- [V] Find a Tender, Centralised Delay Repay Service (RSP Ltd, 4 Jun 2026): https://www.find-tender.service.gov.uk/Notice/053093-2026 ; earlier https://www.find-tender.service.gov.uk/Notice/026489-2026
- [R] Rail Business UK on the procurement: https://www.railbusinessuk.com/ticketing/2026/06/08/procurement-of-consolidated-train-delay-repay-service-begins/ ; Rail Magazine: https://www.railmagazine.com/news/notice-issued-for-consolidated-delay-repay-platform
- [V] GOV.UK press release on Delay Repay changes: https://www.gov.uk/government/news/delay-repay-changes-will-make-rail-travel-easier-under-great-british-railways
- [R] Railnews (17 Mar 2026): https://www.railnews.co.uk/news/2026/03/17-delay-repay-system-to-be.html ; Railway Gazette: https://railwaygazette.com/uk/consolidated-delay-repay-service-to-include-third-party-rail-ticket-retailers/70612.article ; Rail Magazine: https://www.railmagazine.com/news/ticket-retailers-welcome-delay-repay-changes
- [V] Find a Tender, LNER Delay Repay platform PIN (2023): https://www.find-tender.service.gov.uk/Notice/008368-2023/PDF
- [V] Find a Tender, Arriva Delay Repay software notice (2023): https://www.find-tender.service.gov.uk/Notice/013749-2023
- [R] Celaton Delay Repay product: https://celaton.com/solutions/function/delay-repay
- [R] Trainline Delay Repay: https://www.thetrainline.com/trains/great-britain/delay-repay ; Railway Gazette on Trainline campaign: https://www.railwaygazette.com/uk/trainline-calls-for-third-party-ticket-sellers-to-be-able-to-offer-one-click-delay-repay/70393.article
- [R] Which? on trains / Consumer Rights Act: https://legalservice.which.co.uk/holidays-travel/trains ; Resolver: https://www.resolver.co.uk/rights-guide/train-delays-cancellations
- [R] thinkmoney on 2026 Delay Repay changes: https://www.thinkmoney.co.uk/blog/delay-repay-changes-what-commuters-need-to-know-about-the-new-rail-rules-in-2026/
- [V] ORR delay compensation factsheets: https://dataportal.orr.gov.uk/media/ittbwvrh/delay-compensation-claims-factsheet-2025-26-rail-periods-11-13.pdf
- [R] RailUK Forums (anecdotes only): https://www.railforums.co.uk/threads/delay-repay.195161/
