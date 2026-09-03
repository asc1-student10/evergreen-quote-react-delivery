# Delivery Review: Evergreen Quote (Phase 2)

---

## Slide 1: Delivery Goal & Whether We Hit It

**Goal:** By Friday, ship a working Evergreen Quote app — a visitor gets a live premium estimate for auto, home, or life and can save it to a shared recent-quotes list — merged to `main` behind a green CI build.

**Status:** Hit: assembled, typed, data-feed live, hook/context wired, `main` green, merged via reviewed PR
- Live estimate for auto/home/life: ✅
- Recent quotes loading from the data feed with visible loading state: ✅
- `npm run type-check` / `npm run build` green: ✅
- Merged to `main` via reviewed PR with green CI: ✅

---

## Slide 2: What Shipped

- Three components (`QuoteForm`, `PremiumDisplay`, `RecentQuotes`) assembled into `App.tsx`
- Sponsor's title and rate decision configured; QA-flagged type error fixed
- Recent quotes switched from sample data to the live `public/quotes.json` feed
- Custom hook (`useQuoteEstimate`) + context provider (`QuotesContext`) wired in — "Save this quote" works
- CI enabled and producing a result on every push; production build passing

---

## Slide 3: Two Key Decisions

**1. Held Marketing's ZIP-code field request (Day 2 inject).**
Marketing asked for a ZIP-code field by Thursday for a regional-pricing A/B test. Because the contracts are typed, we could see precisely that "just add a box" actually touches five layers — the form, the hook, the rate calculation, the data feed, and the display list — real scope on top of an already-committed week. Held it, logged it as the first Round 3 roadmap candidate instead of shipping a cosmetic field.

**2. Go-with-conditions on the Day 3 merge, not a flat go or no-go.**
`main` went red from a rate hotfix at the same time support reported an anomalous $3,120/month quote. Rather than assuming the two were the same bug (or fixing it myself), I routed the question to the hotfix's owner and support, and made the merge decision conditional on `main` returning to green — protecting the delivery goal without freezing all progress.

---

## Slide 4: Risks & How I Handled the Injects

- **Known risks tracked from Day 1** (risk register): dev-server/compiler drift, unbelievable placeholder rates, silent loading/error states, pinned toolchain — each had a named mitigation and trigger, not just a description.
- **Inject #1 (Day 2):** ZIP-code field ask + a moderate-severity, dev-time-only dependency flag. Handled both as explicit decisions (memo + risk register row), not silent scope creep or a reflex dependency bump.
- **Inject #2 (Day 3):** `main` red from a hotfix, coinciding with a customer-reported bad premium. Routed rather than fixed — named the observation, asked specific owners specific questions, offered air cover, and made the merge decision conditional on the evidence, not on assumption.
- **Copilot critique:** proved empirically that our typed contracts protect source code but never reach the JSON data feed — `npm run type-check` passed even with a corrupted premium value in `quotes.json`. Logged as a real gap, not a hypothetical one.

---

## Slide 5: What I'd Do Differently Next Round

- **Enable CI on Day 1, not Day 3** — the go/no-go call this week would have had a full week of signal behind it instead of one day.
- **Add runtime validation on the data feed** before Round 3's real API swap — the Copilot exercise proved the type system's guarantee stops at the JSON boundary; that gap should close before it's loaded from a real service.
- **Time-box optional stretch work explicitly** (e.g., 15 minutes after required issues are verified green) rather than deciding in the moment whether to attempt it.
- **Get sponsor sign-off on scope boundaries earlier** — Marketing's ZIP-code ask landed as a surprise; a one-line scope note in the kickoff brief might have headed it off before Tuesday.
