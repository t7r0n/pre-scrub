# Decision Report: Pre Scrub

An ambulance billing pre submission scrubber: predicts the denial reason from the closed ePCR + dispatch trace, points the medic at the missing field, and proves it would have cleared payer adjudication.

## Evidence-Grounded Findings

CLAIM: ambulance evidence replay should `block release until cited evidence is regenerated` because blocks=4 reviews=5 mean_severity=2.611. [EVID: ev_0088]
CLAIM: claim boundary probe should `route to reviewer with evidence packet` because blocks=3 reviews=4 mean_severity=2.528. [EVID: ev_0077]
CLAIM: denials regression harness should `open a regression issue with trace and benchmark delta` because blocks=3 reviews=5 mean_severity=2.528. [EVID: ev_0022]
CLAIM: random operator packet should `accept only if decision claims cite fixture evidence` because blocks=4 reviews=5 mean_severity=2.556. [EVID: ev_0011]
