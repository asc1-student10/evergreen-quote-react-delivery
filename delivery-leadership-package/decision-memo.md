# Decision Memo: Optional Stretch Work vs. Protecting Required Work

**Date:** 2026-09-01
**Author:** Ricky Cotton
**Decision area:** Scope tradeoff — optional "add a prop" stretch work vs. the three required assembly issues

## Context

This morning has three required issues: assembling the components into `App.tsx`, setting config values, and fixing the known type error. There's also an optional, clearly-marked stretch challenge (adding a prop to a component) available. The component assembly took longer than planned to reconcile with the marker locations, putting the required work at risk of running into the afternoon check-in with nothing shippable yet.

## Options considered

1. **Do the stretch challenge now, alongside the required issues.** Keeps the team hands-on and engaged early, but risks the required issues slipping past the check-in with no green type-check or running app to show.
2. **Skip the stretch challenge entirely.** Guarantees full focus on the required work, but gives up a low-cost opportunity to practice the TypeScript/React mechanics while the components are already open.
3. **Timebox the stretch challenge to after the required issues are verified done.** Required work is protected first; the stretch challenge only happens if time remains before the check-in.

## Recommendation

Option 3: finish and verify all three required issues first (dev server running, type-check green), then spend any remaining time before the check-in on the stretch challenge.

## Why

The check-in and the sponsor only care about what's actually running and green — an unfinished stretch challenge costs nothing, but an unfinished required issue looks like the day fell behind.

## What would change my mind

If the required issues are verified done well before the check-in with real time to spare, I'd move the stretch challenge earlier in the day tomorrow instead of treating it as leftover time.