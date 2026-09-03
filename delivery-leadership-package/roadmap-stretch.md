# Evergreen Quote: Roadmap (Stretch)

## Guiding question
Phase 2 proved a visitor can get a live, believable number with zero commitment. The question for every future round is the same one the vision brief asks about Phase 2: **does this round get a first-time shopper closer to trusting the number and acting on it — or does it add friction back in?** Anything that doesn't clearly answer "closer" gets pushed to a later round.

## Round 3 — Make the number real
**Theme:** replace placeholders with production-grade inputs, without changing what the customer sees.
- Replace the placeholder `BASE_RATES` model with a real rate/rules service call — still returns a monthly number, but sourced from an actual pricing API instead of a hardcoded constant.
- Add an automated test suite (unit tests on the premium calculation, component tests on the form) so "the compiler didn't complain" stops being the only safety net.
- **Why now:** the app's core promise (a *believable* number) is only as strong as its weakest input. This is the highest-risk gap Phase 2 knowingly left open.

## Round 4 — Let the visitor keep their quote
**Theme:** turn a one-time estimate into something the visitor can come back to.
- Lightweight account creation (email or phone, not a full profile) — explicitly deferred in Phase 2's "what's out of scope."
- Persist a visitor's saved quotes across sessions/devices instead of an in-memory context that resets on refresh.
- **Why now:** Phase 2's context provider already models "shared state without prop drilling" — persistence is the natural next step of the same architecture, not a rewrite.

## Round 5 — Let the visitor act on the number
**Theme:** close the loop from "I have a number I trust" to "I'm covered."
- Payment/checkout flow bound to a saved quote.
- Handoff to policy issuance (own system or partner integration) — Phase 2 explicitly ruled this out.
- Basic post-purchase confirmation/receipt experience.
- **Why now:** this is the highest-value, highest-risk round — it's the first time real money and real compliance/regulatory obligations enter the product. It should not start until Round 3 (real rates) and Round 4 (accounts) are stable in production.

## Sequencing rationale
Rounds are ordered by **"what breaks the customer promise if it's wrong"**, not by engineering convenience:
1. A wrong *number* (Round 3) breaks trust immediately — highest priority.
2. Friction *returning* to a saved quote (Round 4) is next, because it's the first ask we make of the customer.
3. Money and compliance (Round 5) come only once the number and the account layer are trustworthy.

## What could reorder this
- The sponsor's real priority
- Resources avaliable
- How individuals respond to the site