# delay-repay-me

A Delay Repay agent for UK rail. When your train is delayed or cancelled, it checks the delay against open rail data, works out what you're owed, and drafts the claim for your operator's portal with the evidence attached. Then it stops so you can review the claim and submit it yourself.

> Status: **research and scoping.** No code yet.

## Why

Booking apps like Trainline and TrainPal will tell you a train was late, but they won't file the Delay Repay claim. Every operator has its own portal, login, and ticket upload, so small claims often go unclaimed. This project aims to close that gap without taking control away from the passenger.

## Approach (draft)

1. **Verify:** confirm the delay from real train-running data, not from what the passenger remembers.
2. **Calculate:** apply the operator's Delay Repay rules to get eligibility and the amount.
3. **Draft:** fill in the claim and show exactly what will be sent, with the evidence.
4. **Approve:** the passenger checks it and submits. Nothing goes out automatically.

## Repository layout

| Path | Contents |
| --- | --- |
| [`docs/PROJECT_INTENT.md`](docs/PROJECT_INTENT.md) | The problem, the idea, initial scope ideas and open questions |
| [`docs/DECISIONS.md`](docs/DECISIONS.md) | Log of scope and design decisions |
| [`research/`](research/) | Market and landscape research |
| [`research/SUMMARY.md`](research/SUMMARY.md) | Overall summary of the research |

## Next steps

- Agree scope (first operator, data source, approval flow).
- Write a high-level outline and architecture.
