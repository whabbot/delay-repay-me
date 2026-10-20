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

## Open

- **The hand-off: how the drafted claim reaches the operator's portal.** Under discussion.
- **First operator:** West Midlands Trains (WMR + LNR) or Avanti.
- **WMR's automation:** the research conflicts on whether WMR offers "one-click" claims. Either way, it is unlikely to cover TrainPal tickets.
