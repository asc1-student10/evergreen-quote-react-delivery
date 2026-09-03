# Delivery Goal: Evergreen Quote

## Goal

> By Friday, ship a working Evergreen Quote app — a visitor gets a live premium estimate for auto, home, or life and can save it to a shared recent-quotes list — merged to `main` behind a green CI build.

## "Done" looks like

- The estimate updates live as a visitor types, for auto / home / life.
- Recent quotes load from the data feed with a visible loading state.
- `npm run type-check` passes; the contracts hold.
- `npm run build` succeeds and the CI run on the merge commit is **green**.
- A reviewed PR is merged, branch deleted.
- `delivery-leadership-package/` is complete and committed.

## Out of scope (this week)

- No real rate engine or actuarial pricing — the rate model is a placeholder.
- No customer accounts, persistent saved-quote storage, or email capture.
- No payment, checkout, or policy purchase flow.
- No back-end service — the JSON data feed stands in for the quotes API.
- No routing, automated test suite, or production deployment beyond the green build.