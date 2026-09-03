# Decision Memo: Marketing's ZIP-Code Field Request

**Date:** 2026-09-01
**Author:** Ricky Cotton
**Decision area:** Marketing's ZIP-code field request for Thursday's regional-pricing A/B test

## Context

Marketing asked for a ZIP-code field on the quote form by Thursday to support a regional-pricing A/B test, saying their pricing table is ready on their side. This lands in the middle of a week where Wednesday through Friday are already committed to the data feed, the hook/context refactor, CI, and the production build — the deliverables the delivery goal is actually measured against.

## Options considered

1. **Option A: Add the field and wire it to marketing's regional pricing this week.** Gives marketing exactly what they asked for by Thursday, but touches every typed layer we have — the `Quote`/`CoverageType` contracts, the `useQuoteEstimate` hook's inputs, the `premium.ts` calculation, the `quotes.json` feed shape, and how `RecentQuotes` renders each entry — on top of Wednesday's already-scheduled work.
2. **Option B: Add only the input box, not the pricing logic.** Visually satisfies "just add the box" with a much smaller footprint, but a customer typing a ZIP code that visibly does nothing to the price is worse than not asking for it at all.
3. **Option C: Hold the feature this week; log it as a Round 3 roadmap candidate.** Protects the already-committed Wednesday–Friday work with zero new risk, at the cost of marketing's Thursday timeline.

## Recommendation

Option C: hold this week, land it as the first item in Round 3.

## Why

Because our contracts are typed, we can already tell "just add a box" isn't small — it touches the form, the hook, the rate calculation, the data feed, and the display list, in the same week we've committed to the data feed and hook/context refactor. That's the typed chain doing its job: it lets us say precisely, today, how big this really is, instead of finding out on Thursday.

## What would change my mind

If marketing only needs a visual mockup of the field for a stakeholder demo — no real pricing behind it — and is comfortable presenting it that way, I'd revisit a narrower version (Option B) without touching Wednesday's plan.
