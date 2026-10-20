# Decisions

A running log of scope and design decisions. Background is in [`PROJECT_INTENT.md`](PROJECT_INTENT.md) and [`../research/SUMMARY.md`](../research/SUMMARY.md).

## 2026-10-20

### D1. Target journeys: TrainPal bookings on West Midlands Trains and Avanti West Coast

The first use case is tickets bought through **TrainPal** for journeys on:

- **West Midlands Railway (WMR)** and **London Northwestern Railway (LNR)**, both run by West Midlands Trains;
- **Avanti West Coast**.

Why: these are the operators we travel on most, and none of their automated schemes covers third-party bookings. Avanti's scheme is limited to direct Advance bookings. The research didn't settle whether WMR has any automated option (see open questions), but nothing suggests it covers TrainPal tickets. So every claim here is currently manual, which is exactly the gap.

The first operator to build for is still open (see below).

### D2. A personal tool, built in the open

This is a personal tool first, developed in a **public** repository that others could use or extend. That means:

- **No personal data in the repo.** Tickets, booking emails, journey history, evidence packs and bank details stay in a local data directory that git ignores. Test fixtures are synthetic or fully redacted. E-ticket barcodes count as sensitive, because they may be reusable.
- **No secrets in the repo.** API credentials (Rail Data Marketplace, Realtime Trains) come from the environment or a local config file that git ignores.
- **Bring your own credentials, run locally.** Each user registers for their own data access. Nothing runs as a hosted service that holds other people's tickets or logins. This also fits the non-commercial terms of Realtime Trains' free tier.
- **The core works for any operator; operators are pluggable.** Others will travel with different operators.

### D3. Parsing e-ticket emails is core input, not an extra

Booking confirmation emails (starting with TrainPal's) are the main way to get the journey and the proof of ticket. Calendar-based detection stays an extra.

### D4. First operator: West Midlands Trains (WMR + LNR)

Neither of the remaining candidates has a stronger case. One integration covers both WMT brands, and their portal runs on the Tracsis `delayrepaycompensation.com` platform. That same platform also serves Greater Anglia and c2c, so the work carries over. See [`../research/05-portal-spike.md`](../research/05-portal-spike.md).

WMR and LNR do offer "one-click" claims, but only for Advance Singles bought through their own app or website. TrainPal tickets don't qualify, which settles the earlier open question.

### D5. Hand-off: claim pack first, then an agent-driven browser (B2)

The rule we agreed: use B2 (an agent-driven visible browser that stops before Submit) if the portal's final screen shows the values being submitted. Otherwise use B1 (a browser extension). The spike found that both target portals end on a review screen: WMT's "Confirm your claim" and Avanti's "Review claim details". So **B2**. B1 stays a stretch goal.

Because most claims will be made on a phone, and B2 is desktop-only:

- **A: claim pack** (copy and paste, phone-friendly) is the **first deliverable and the everyday route**. It's also the structured output that B2 fills in.
- **B2** follows for when you're at a computer. The agent fills the form and stops at the review screen. The person checks it, ticks the reCAPTCHA and presses Submit.
- **B1** (stretch) is the only automated option that could also work on a phone, via Firefox for Android or Safari on iOS.

### D6. Phone platform: Android

Claims are mostly made on an Android phone. That has two effects:

- The claim pack (A) must work well in a mobile browser on Android.
- The stretch goal B1 (browser extension) could run on the phone via **Firefox for Android**, which supports extensions. That makes it the only automated hand-off that could work on a phone.

### D7. Facts confirmed from past use

Both the WMT portal and the Avanti portal **find TrainPal-bought tickets** in their ticket lookup. This is from past claims we've made, not from the spike.

### D8. Train Badger: optional data source, not a dependency

Train Badger (see [`../research/06-train-badger.md`](../research/06-train-badger.md)) is iOS-only and in beta. It verifies delays from the same data source we chose (HSP) and has an agent API, but it never submits claims. We keep HSP as our own source of truth. Train Badger may become an optional cross-check later.

### D9. Rules for how the tool behaves on claim portals

WM Trains' website terms (WMR and LNR) contain no clause on automation. Their acceptable-use clauses set the rules we follow on every portal (see [`../research/05-portal-spike.md`](../research/05-portal-spike.md), section 2a):

1. **Fill the form, nothing more.** Never get around validation, the reCAPTCHA, or the portal's own checks.
2. **Never change the portal page.** The evidence and the approval view live in our own window, side panel or extension pop-up, never added onto the operator's page. This avoids the clause about altering the site's "look and feel".
3. **One claim at a time, at a person's pace.** No polling, crawling or bulk submission. Don't use the portal's lookup APIs as a data source.
4. **Only your own details, in your own session.** No stored or shared portal passwords.
5. **No operator code or assets in the repo.** Only facts about the form (field names, step order) and short quotes.
6. **A person makes the declaration.** The tool drafts claims only for a real ticket plus checked train data. Pressing Submit, with the Fraud Act warning on screen, is always a person's action.

## Open

- **Walk-through of a real claim:** waiting until there's a delay to claim for. Until then, design from the spike's field list.
- **Check that HSP's RIDs match the portal's train list** for the same journey.
