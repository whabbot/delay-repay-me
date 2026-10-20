# Market research: overall summary

Research date: 2026-10-19. This file brings together four research slices:

| File | Slice |
| --- | --- |
| [`01-booking-apps.md`](01-booking-apps.md) | Trainline, TrainPal, Uber, Omio, split-ticket sites and other retailers |
| [`02-operator-auto-compensation.md`](02-operator-auto-compensation.md) | Operators' own automatic schemes, national policy (DfT / GBR / ORR), claim rates |
| [`03-independent-tools-and-analogues.md`](03-independent-tools-and-analogues.md) | Independent claim tools, Delay Repay Sniper, flight and European analogues, operator stance on third-party claims |
| [`04-rail-data-and-claim-portals.md`](04-rail-data-and-claim-portals.md) | Open rail data for verifying delays, operator claim portals |
| [`05-portal-spike.md`](05-portal-spike.md) | Hands-on look at the West Midlands Trains and Avanti claim portals (added after this summary; it updates section 3 below) |
| [`06-train-badger.md`](06-train-badger.md) | Train Badger: iOS beta app with Delay Repay tracking and an API for AI agents |

> **Evidence caveat.** In every slice, direct page fetches failed in the research environment. All findings come from search-result excerpts of the cited pages, not from reading them in full. Each file labels claims as primary-source excerpt, reported, or uncertain. Re-check anything load-bearing (operator rules, competitor features, tender dates) against the live page before relying on it.

## The headline

**The gap is real but narrower than we first thought, and it has a time limit.**

- No mainstream booking app submits claims. Trainline detects the delay, estimates the payout and links out to the operator, and says publicly that industry rules stop it offering one-click claims.
- Operator "automatic" schemes almost never cover tickets bought through Trainline or TrainPal.
- But "nobody submits claims for you" isn't quite true. A handful of small, new UK services claim to submit for a fee. None has independent reviews, and their standing with operators is unknown.
- The industry is building a national Delay Repay platform that retailers can plug into. That could close much of the gap from around 2027–28.

## What we thought vs. what we found

| What we thought | What we found |
| --- | --- |
| Trainline spots delays and prompts you to claim. | **Confirmed.** Launched 8 Dec 2025. It detects the delay, estimates the amount, and deep-links to the operator's claim page for about 17 operators. Its Jan 2026 "Fair Play on Delay Repay" campaign says industry rules stop it offering one-click claims. |
| Avanti, LNER and GTR pay out automatically, but only for direct bookings. | **Mostly confirmed, with nuance.** Only **c2c** is truly automatic (smartcard tap in and out, eVoucher). Elsewhere "automatic" means the operator pre-fills a claim and you accept it. This applies at Avanti, LNER, GTR, GWR, Southeastern, SWR, TPE, Lumo and Caledonian Sleeper. **None covers Trainline or TrainPal tickets**; Avanti, LNER, TPE, Lumo and Southeastern say outright that their schemes are direct-booking only. A DfT answer says 10 of 14 DfT operators offer one-click. |
| Railiable calculates what you're owed, but you submit yourself. It may be iOS only. | **Confirmed.** It's an iOS app using Network Rail data that detects, calculates and alerts, with a paid "Plus" tier for alerts. You submit on the operator's site yourself. No Android app was found. |
| Submission is the gap in the market. | **Partly.** See the competitor table below. The real gap is a *trustworthy, evidence-backed* tool where the passenger stays the claimant. |

## Who already does what

| Product | Detects | Calculates | Submits | Model | Notes |
| --- | --- | --- | --- | --- | --- |
| Trainline | ✅ | ✅ | ❌ link-out | Free (retailer) | Says it's blocked from offering one-click claims |
| TrainPal, Omio/Uber, Trainsplit, Split My Fare, Raileasy, Seatfrog | ❌ | ❌ | ❌ | – | "Claim with the operator." Uber's UK rail is Omio inventory. |
| Operator schemes (Avanti, LNER, GWR, GTR, etc.) | ✅ | ✅ | Pre-filled, you accept | Free | Direct bookings only |
| c2c | ✅ | ✅ | ✅ fully automatic | Free | Smartcard plus tap in and out only |
| Railiable | ✅ | ✅ | ❌ | Freemium (iOS) | |
| **Railed** | ? | ✅ | ✅ (claimed) | 10% of payout | You forward tickets and it files. The Android app was pulled from Google Play in May 2026. |
| **DelayDog** | ✅ | ✅ | ✅ (claimed), after you approve | 10–15% commission | WhatsApp, app and web. Reportedly uses headless logins (at least for TfL). |
| **Delayo** | ? | ✅ | ✅ (claimed) | £2 per claim | Files under a "letter of authority" |
| **Reeclaim** | ✅ | ✅ | ✅ | £3.99–£7.99 a month | TfL only. Logs into your TfL account. |
| Delay Repay Sniper | ✅ | ✅ | ✅ link-to-submit | ~£9.99 a month | **Dead.** Tracsis bought it in 2018 and the company was dissolved in July 2024. GTR reportedly refused and clawed back claims made through it. |

The best analogues from other markets are AirHelp and Flightright (flights) and TreinGeldTerug (Dutch rail). All scale through **legal assignment or power of attorney plus commission**: the service becomes the claimant. Claimback, an open-source AI agent for flight claims, deliberately never presses Submit, which is the same posture we're proposing.

## Key findings for scoping

### 1. The authority model is the central design question

The question that matters is who the claimant is.

- Thameslink and Southern publish wording that claims must be made by the person who was delayed, except in mitigating circumstances. Avanti reportedly says the same.
- Services where the service itself becomes the claimant (Delayo's letter of authority, AirHelp-style assignment) run straight into that wording.
- ORR planned in 2020 to make operators accept claims from compliant intermediaries, then deferred it. So operators are under no obligation to accept a third party's claim.

**Draft, then the passenger submits** keeps the passenger as the claimant, using their own details in their own session. That is the most defensible position the research found. It also sets us apart from Railed, DelayDog and Delayo. The research supports the approval step as more than a ToS workaround.

### 2. Verifying the delay is the easy, solid part

- **Primary source: Historical Service Performance (HSP) on the Rail Data Marketplace.** It is free after you register, based on Darwin, and gives scheduled and actual times per stop plus cancellation and delay reason codes. History goes back about a year, which comfortably covers the 28-day claim window. One risk: sustained HTTP 429 (rate-limit) errors were reported in July 2026.
- **Cross-check: the Realtime Trains Next Generation API (data.rtt.io).** The free tier is non-commercial only and capped at 10/min, 100/hr and 1,000/day. That's fine for a personal tool, but a product would need a paid plan. The legacy api.rtt.io is now off.
- Live-board APIs (LDBWS, Huxley) can't prove a past delay. Raw Network Rail feeds (TRUST and others) would need you to keep your own archive.
- Delay is measured at the **final destination on the ticket** against the timetable. Edge cases need passenger input or a flag: missed connections, rerouting, split tickets, and the Advance-ticket "booked train only" rule.

Operators mostly ask for proof of the ticket, not proof of the delay. So the data evidence mainly serves our approval screen and protects the passenger in a dispute. That fits the "agent shows its evidence" theme exactly.

### 3. The claim side is the hard, risky part

> **Updated by the [portal spike](05-portal-spike.md):** shared platforms do exist. Tracsis's `delayrepaycompensation.com` serves WMR, LNR, Greater Anglia and c2c. A `wcr-smart-repay` platform serves Avanti, GWR, TPE, SWR, Hull Trains and Lumo. Both use reCAPTCHA on the final Submit, after a review screen.

- There's no public claims API, and **no shared white-label portal vendor was confirmed**. Portals use `delayrepay.<operator-domain>` hostnames (GWR, Thameslink, Southern, TPE), which hints at shared software, but that's unproven.
- The GTR brands (Southern, Thameslink, Great Northern) are the likeliest case of one form covering several operators.
- No operator ToS clause on automation was found either way, and no CAPTCHA evidence. We need a hands-on spike: load the forms and read the terms.
- Credential sharing and headless logins (DelayDog's approach) are a trust and ToS risk and break when sites change. Reeclaim's earlier tool broke this way. Avoid them.

### 4. The market is about to be re-plumbed

- **17 Mar 2026:** DfT announced that operators' Delay Repay systems will merge into one Great British Railways (GBR) service, and passengers will be able to claim through the retailer they bought from. Retailers opt in.
- **RDG tender** (Find a Tender 053093-2026, about £21m): award reportedly planned for 19 Oct 2026, with the contract starting on 30 Oct (one notice says 1 Oct). It's unconfirmed whether the contract has been awarded.
- **Railways Bill:** in Lords committee, with Royal Assent targeted for end-2026. GBR follows about 12 months later.
- **Consequence:** the window for an independent tool is roughly **12–24 months**. Two things follow:
  - build the core so it doesn't depend on any one operator: verification, entitlement, evidence pack;
  - don't over-invest in per-portal automation.

  If the national platform lets third parties or agents submit for a passenger, submitting through it could replace portal automation entirely.

### 5. Size of the opportunity

- Only **about 45% of eligible passengers claim**: 34% at the 15-minute tier and 51% at the 30-minute tier. That's the first fall since 2016 (DfT and Transport Focus, 2025).
- Claim volume is rising fast: ORR counted 3.8m claims closed in Apr–Jul 2026, up 55%.
- About 26% of passengers buy through independent retailers, so they get the manual route by default.
- The economics are thin for a commercial product: claims are small and competitors charge a 10% commission or £2 a claim. As a personal tool, or a showcase for the evidence-first agent pattern, that doesn't matter.

## What this means for the initial scope ideas

| Initial idea | What the research says |
| --- | --- |
| 1. One operator | **Supported.** Pick it by *the user's main operator and booking channel*. The sweet spot is an operator whose own scheme doesn't cover the user's tickets, e.g. TrainPal or Trainline bookings. GTR (Southern, Thameslink, Great Northern) is a good fallback: one form may cover several brands, and its "claimant must be the traveller" wording suits our approach. |
| 2. Check against real train data | **Strongly supported and feasible.** HSP as the source of truth, with RTT as a cross-check. Cite the source, query and timestamp in the evidence. |
| 3. Draft, then stop for approval | **Strongly supported.** It's the most defensible authority model and it sets us apart from the competition. The open design question is *how* the hand-off works (options below). |
| 4. Extras (calendar or email detection, ticket photos) | **Re-rank.** Parsing **e-ticket confirmation emails** from TrainPal and Trainline is the most natural way to get the journey and the proof of ticket. It's arguably core input rather than an extra. Calendar detection is lower value. |

**Options for the hand-off in idea 3, from safest to most automated:**

1. **Claim pack:** every field, the evidence and a deep link, for the passenger to copy and paste. This is the safest option and works on every portal.
2. **Assisted fill in the passenger's own browser** (extension or user-driven browser): fills the form in the passenger's logged-in session and stops before Submit. Smoother, but still subject to portal ToS and any bot protection.
3. **Headless submission with stored credentials:** not recommended, for the trust, ToS and fragility reasons above.

## Things to verify next (before we commit to scope)

1. **The user's travel pattern:** main operator(s), booking app(s), ticket types (Advance, Anytime, season), and e-ticket vs. paper.
2. **A hands-on spike on the chosen operator's portal:** guest vs. account, fields, upload types, CAPTCHA or Cloudflare, and the terms of use.
3. **Register on the Rail Data Marketplace** and query HSP for a real past delayed journey.
4. **Railed and DelayDog:** how they submit, what authority wording they use, and whether claims get paid.
5. **The RDG national platform:** tender award outcome, and whether third parties will get API access.
6. **The current National Rail Conditions of Travel and operator wording** on third-party and automated claims.
