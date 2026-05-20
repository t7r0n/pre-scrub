# Operator Brief: Overdrive Health

Overdrive Health gets a local, deterministic pressure test around ambulance, claim, and denials. The useful part is the repeatable evidence path from fixture to failure to operator action.

## Highest-leverage checks

- ambulance evidence replay -> block release until cited evidence is regenerated (ambulance_coverage, evidence ev_0088).
- random operator packet -> accept only if decision claims cite fixture evidence (claim_risk, evidence ev_0011).
- denials regression harness -> open a regression issue with trace and benchmark delta (denials_precision, evidence ev_0022).
- claim boundary probe -> route to reviewer with evidence packet (random_latency, evidence ev_0077).

## What makes this useful

The workflow is intentionally local and deterministic. A reviewer can run the same fixture set, inspect the evidence IDs, open the dashboard, and see exactly why a recommendation passed, went to review, or blocked.
