# Evergreen Quote: Vision Brief

## Product
**Name:** Evergreen Insurance Quote (Phase 2 React rebuild)
**Delivery week:** 2
**Delivery Lead:** Ricky Cotton
**Engineering team (represented by):** [evergreen-quote-react-delivery](https://github.com/asc1-student10/evergreen-quote-react-delivery)
**GitHub Project board:** [Project Board](https://github.com/users/asc1-student10/projects/3/views/1)

## Who is the customer?
A first-time insurance shopper. Often a new renter or new homeowner who was just told they "need insurance". Pulling this up on their phone with no intention of committing to anything yet. They want a believable number in under a minute, without creating an account or handing over an email address. Today their alternative is a competitor's twelve-field quote form that asks for personal information before showing a single price, or simply closing the tab and moving on.

## What pain does Evergreen Quote remove?
Phase 1 made this visitor click a button and wait for a number. That pause, however small, is a moment where an impatient, non-loyal shopper can bounce. The Phase 2 rebuild removes the wait entirely: the estimate updates live as they type their coverage type, age, and coverage amount, and they can see what other customers are paying and save their own quote to that list, all with zero commitment. The pain we remove is friction between "I'm curious what this costs" and "I have a number I trust."

## What does "good" look like at end of the week?
- The estimate visibly updates as a stakeholder types into the form — no button press, no page reload.
- Recent quotes load and "Save this quote" puts a new entry at the top instantly.
- The work lives on `main` via a reviewed pull request with a green CI run — not just on someone's laptop.
- Auto, home, and life all produce believable monthly numbers under the sponsor's current rate decision.

## What are we explicitly NOT doing this week?
- No real rate engine or actuarial pricing — the rate model is a deliberate placeholder.
- No customer accounts, persistent saved quotes, or email capture.
- No payment, checkout, or policy purchase flow.
- No back-end service — `quotes.json` stands in for the quotes API.
- No routing, automated test suite, or production deployment; we stop at a green build.

## How will we know if it worked?
- CI is green on `main` (`npm ci`, type-check, build) at every push, with zero unresolved TypeScript errors.
- In Thursday's demo, a stakeholder can get a quote and see it saved to the top of the Recent Quotes list in under 3 interactions.
- Zero critical defects (broken estimate, missing loading state, failed build) surface during the Friday review.

