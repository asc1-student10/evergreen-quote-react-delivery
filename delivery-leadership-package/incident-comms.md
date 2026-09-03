# Incident Comms: Day 3 Inject #2 (Stretch Artifact)

**Date / time:** 2026-09-02, ~14:00 (Day 3, Wednesday)
**Author:** Ricky Cotton, Delivery Lead
**Context:** Two possibly-related reports landed together — `main`'s CI red since a rate hotfix push (~40 min prior), and a support ticket for a customer quoted $3,120/month for $180,000 of home coverage, which reproduces.

## The message

> Heads up team — `main`'s CI has been red for ~40 minutes, failing at type-check in `premium.ts` (a string being assigned where a number is expected) right after the "adjust home rate per sponsor note" hotfix push; separately, support just flagged a customer quoted $3,120/month for $180k of home coverage, and they've confirmed it reproduces. I don't know yet whether these are the same problem or two separate ones — **can whoever pushed the hotfix confirm whether that commit touches the same home-rate path support is seeing**, and can support share the exact inputs (coverage amount, age) behind the $3,120 case so we can compare? Whoever owns the hotfix owns the fix; I'm not opening `premium.ts` myself. In the meantime I'm holding my own merges to `main` and parking today's data-feed work — I'll move our next check-in if we need the extra time to get `main` green again.

## Why it's built this way

- **Names what I observed:** the red CI run (with the specific failing step) and the customer report (with the specific reproducing symptom) — stated as two separate facts, not merged into one assumed cause.
- **Names what I'm asking for, from a specific owner:** the hotfix's author confirms whether the commit touches the path support is seeing; support shares the exact reproduction inputs. Neither ask is "can someone look into this."
- **Names who owns the next step:** whoever pushed the hotfix owns the fix — explicitly *not* me. Routing, not fixing, is the job today.
- **Offers air cover:** parking the data-feed work and offering to move the check-in, so the owner doesn't have to fix the incident *and* protect the day's schedule at the same time.