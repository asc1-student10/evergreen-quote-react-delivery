# Copilot-Assisted Assembly: Critique

**Assembly step:** Asked GitHub Copilot to add two more realistic rows to `public/quotes.json`, matching the existing shape.

**Date:** 2026-09-02
**Author:** Ricky Cotton

## Critique

Copilot got the substance right: unique ids, premiums that scaled sensibly with coverage type and amount, and an exact match to the existing date/key format. What it got wrong is invisible: nothing stopped it from writing bad data, and I proved that by changing a premium to a string and running `npm run type-check` and it passed clean. I'd ship the actual rows as-is after eyeballing them, but I wouldn't trust that eyeballing as a process going forward; the fix isn't a smarter prompt, it's runtime validation on the fetch.

## Test performed

1. Changed one new row's `premium` field from a number to a string (e.g. `"129"`).
2. Ran `npm run type-check`.
3. **Result: passed with zero errors.**
4. Reverted the change before committing.
