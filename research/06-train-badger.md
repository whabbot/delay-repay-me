# 06 - Train Badger

Date: 2026-10-20. Pages read directly: trainbadger.app home, WMR guide, journey check, beta page, terms, and the agent guide (`/for-agents.md`).

## Summary

- **What it is:** an iPhone app (iOS 17+) for live UK departures, with platform prediction and **Delay Repay tracking**. It's in **private beta on TestFlight**. It's free during the beta, and a "Train Badger Pro" subscription is planned that will include Delay Repay tracking. There's no Android app.
- **What it does for Delay Repay:**
  - You "pin" a train before you travel.
  - It records the actual arrival, works out the delay at your destination and checks eligibility against each operator's scheme. It covers 26 operators, including WMR, LNR and Avanti.
  - Then it **links you to the operator's claim form**. Its own wording: "Train Badger itself never submits a claim".
- **Delay data:** live Darwin data, plus Network Rail's **Historical Service Performance (HSP)** for the public journey check. HSP is the same source we chose. The public journey check covers the last 7 days only, since the previous day's data takes several hours to settle.
- **It publishes an API and MCP server for AI agents** ([`/for-agents.md`](https://trainbadger.app/for-agents.md)). The workflow it describes is register → track → poll → file → mark:
  1. An agent registers a train before departure.
  2. It polls for claimable journeys, each with a verification status and the operator's claim URL.
  3. It **files the claim on the operator's own site**.
  4. It marks the journey as claimed, so it's never filed twice.

  The guide tells the agent to "show the claim to the human before submitting it", and says automated use of an operator's form "must respect that operator's terms".
- **Limits:** you can only register trains from today to 30 days ahead (no registering after the fact). Up to 4 legs and 20 writes a day per account. The public journey check is limited to 10 lookups a minute. API keys are scoped and revocable, and minted in the app or the account portal.
- **Privacy stance:** "No ads. No tracking. No data sold. Zero third-party SDKs."

## What it means for us

1. **It confirms the design and the gap.** A product built specifically for agents still stops at "link to the claim form" and leaves submission to an agent and a person. Its own guide describes the human-approved flow we chose.
2. **It overlaps our detect, verify and calculate stages.** It does much of what we planned around HSP: confirming the delay and working out eligibility.
3. **We could use it as a data source.** Our agent could register trains through its API when a TrainPal booking email arrives (bookings are made before travel, which fits the 30-day register-ahead window). Then it would poll for verified outcomes and claim URLs. Downsides:
   - it's a beta with "no SLA" and no promise the API stays the same;
   - the account and API keys are minted in an iOS app or an "account portal", and it's unclear whether you can sign up without an iPhone;
   - it would add a third-party dependency to an open-source tool.

   **Recommendation:** keep HSP as our own source of truth, and list Train Badger as an optional cross-check or alternative data source. Revisit once it's out of beta.
4. **It's not a competitor for our use case today:** it's iOS-only (we're on Android), it doesn't submit, and it doesn't read ticket emails.
5. **Content quality:** its WMR guide says WMR is "operated by Abellio", but slice 02 found WMR/LNR have been publicly owned since 1 Feb 2026. And its claim link points to a WMR help page, not the Tracsis claim form. Treat its operator data as a guide, not a source.

## Sources

- Home: https://trainbadger.app/
- WMR guide: https://trainbadger.app/delay-repay/west-midlands-railway
- Journey check: https://trainbadger.app/delay-repay/journey-check
- Beta: https://trainbadger.app/beta
- Terms (effective 30 May 2026): https://trainbadger.app/terms
- Agent guide: https://trainbadger.app/for-agents.md (more at `/llms.txt`, `/api-docs`, `/api-docs/openapi.json`)
