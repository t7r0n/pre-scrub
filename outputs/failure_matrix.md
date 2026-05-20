# Failure Matrix: Pre Scrub

| Scenario | Failure mode | Metric | Gate | Evidence |
| --- | --- | --- | --- | --- |
| ambulance evidence replay | ambulance_drift | ambulance_coverage | block release until cited evidence is regenerated | ev_0000 |
| random operator packet | random_blindspot | random_latency | accept only if decision claims cite fixture evidence | ev_0007 |
| random operator packet | random_blindspot | random_latency | accept only if decision claims cite fixture evidence | ev_0011 |
| denials regression harness | denials_misroute | denials_precision | open a regression issue with trace and benchmark delta | ev_0014 |
| claim boundary probe | claim_gap | claim_risk | route to reviewer with evidence packet | ev_0021 |
| denials regression harness | denials_misroute | denials_precision | open a regression issue with trace and benchmark delta | ev_0022 |
| ambulance evidence replay | ambulance_drift | ambulance_coverage | block release until cited evidence is regenerated | ev_0028 |
