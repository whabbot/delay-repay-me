# Project intent

## The problem

When a UK train is delayed or cancelled, passengers are usually owed Delay Repay compensation. The apps people book through (Trainline, TrainPal, and similar) don't submit that claim for them. At best they notice the delay and prompt you to claim. You still have to go to the train operator's own portal, log in, type in the journey details, upload the ticket, sometimes get past a CAPTCHA, and submit.

So claims get skipped because each one is a small amount of money for a tedious bit of admin. That's money the passenger is owed and doesn't collect.

## What we know so far (before research)

- **Trainline** spots delays and prompts you to claim. It doesn't submit the claim.
- **Some operators pay out automatically** to registered users. Avanti, LNER and GTR are named in one round-up. The conditions vary: Avanti, for example, only does it if you booked directly with them. That probably doesn't cover tickets bought through a third party like TrainPal.
- **Railiable** (iOS app, 2026) uses Network Rail data to work out how late your train was and how much you're owed. You still copy the details across and submit the claim yourself. It may be iOS-only, with no Android or web version.

## The gap we think exists

Actually **submitting** the claim. That's the interesting part, and also the hard part:

- Every operator has its own claim portal, with its own login, form, and ticket upload.
- Some portals use CAPTCHAs.
- Fully automated submission may breach some portals' terms of service.

## The idea

A Delay Repay agent that:

1. Knows about a journey (from a ticket, a booking, or the user telling it).
2. **Checks the delay against real train data**: open rail data, not the user's say-so. That check is what makes a claim correct rather than a good guess.
3. Works out eligibility and the amount owed under the operator's rules.
4. **Drafts the full claim and stops for approval**: it fills in the claim and shows what it's about to send, with the evidence attached. The user clicks submit.

The approval step does two jobs. It sidesteps the terms-of-service question, because a person submits the claim. It also fits a theme the user has already written about: an agent that shows the evidence for its own output, so a person can check it before anything happens.

## Initial scope ideas (to be discussed, not decided)

1. **One operator**: the one the user travels with most. Do it properly before thinking about others.
2. **Verify the delay against open rail data.**
3. **Draft everything, then stop for approval.** Human-in-the-loop submission with the evidence shown.
4. **Extras later**: detecting journeys or delays from calendar or email, reading ticket photos, more operators.

## Principles

- **Evidence over assertion.** Every claim the agent drafts carries the data that justifies it: scheduled vs. actual times, the data source, and the compensation rule applied.
- **A person stays in control.** Nothing is submitted without explicit approval.
- **Respect the portals.** Work within operators' terms. Prefer official or sanctioned routes where they exist.
- **Narrow and correct before broad.** One operator done well beats ten done badly.

## Open questions

- Which operator first, and which booking channel (direct vs. third-party app)?
- Which rail data source is the best fit for after-the-fact delay checks?
- How does "draft then approve" work in practice: a pre-filled browser session, a copy-paste pack, or something else?
- What does each candidate operator's portal need: login, ticket image, ticket reference, bank details?
- Where do the terms-of-service lines fall for assisted (rather than fully automated) submission?

Market research to inform these is in [`research/`](../research/).
