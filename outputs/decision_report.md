# Decision Report: Pre Scrub

An ambulance billing pre submission scrubber: predicts the denial reason from the closed ePCR + dispatch trace, points the medic at the missing field, and proves it would have cleared payer adjudication.

## Evidence-Grounded Findings

CLAIM: ambulance drift should `block release until replay is understood` because blocks=2 reviews=3 mean_severity=2.5. [EVID: ev_0088]
CLAIM: ambulance evidence recall should `block release until replay is understood` because blocks=3 reviews=3 mean_severity=1.875. [EVID: ev_0000]
CLAIM: claim gap should `block release until replay is understood` because blocks=3 reviews=2 mean_severity=3.333. [EVID: ev_0011]
CLAIM: claim reviewer handoff should `block release until replay is understood` because blocks=2 reviews=4 mean_severity=2.583. [EVID: ev_0055]
CLAIM: denials failure replay should `block release until replay is understood` because blocks=2 reviews=4 mean_severity=3.333. [EVID: ev_0110]
CLAIM: random policy boundary should `block release until replay is understood` because blocks=2 reviews=3 mean_severity=1.708. [EVID: ev_0033]
