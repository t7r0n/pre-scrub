# Pre Scrub

An ambulance billing pre submission scrubber: predicts the denial reason from the closed ePCR + dispatch trace, points the medic at the missing field, and proves it would have cleared payer adjudication.

## Why This Exists

Ambulance claim denials are not random. They cluster on a small set of failure modes that are deterministic given the document: missing origin/destination modifiers (RH/SH/QL...), medical necessity narrative that doesn't justify the HCPCS A code chosen (A0427 ALS Emergency vs A0429 BLS Emergency), missing PCS (Physician Certification Statement) for non emergent transports, or a patient signature gap on the ePCR.

## What It Builds

- Replays synthetic `ambulance` and `claim` cases against the project's evidence rules.
- Scores `ambulance_coverage`, `claim_risk`, and `denials_precision` so regressions are visible in CSV and JSON.
- Plants `ambulance drift` and `claim gap` failures as negative controls.
- Writes citation-locked decision claims; unsupported claims fail verification.
- Exports a review dashboard and demo pack for `pre-scrub` without hosted services.

## Local Run

```bash
uv sync
uv run pre-scrub all
uv run pytest -q
uv run ruff check .
```

## Outputs

- `outputs/analysis.json`
- `outputs/scenario_report.csv`
- `outputs/decision_report.md`
- `outputs/evidence_packet.md`
- `outputs/dashboard.html`
- `outputs/demo_pack.zip`

## Sources

- https://www.ycombinator.com/launches/PbA-overdrive-health-ai-powered-rcm-for-ambulance-agencies
- https://www.ycombinator.com/companies/overdrive-health/jobs/THGCs1s-founding-engineer
- https://linkedin.com/in/michael-schroeder-217513bb/
- https://x.com/ycombinator/status/2029315960830611864
- https://www.cms.gov/medicare/coding-billing/healthcare-common-procedure-system
- https://www.imagetrend.com/platform/epcr-software/
- https://www.eso.com/
- https://www.novaoneadvisor.com/report/us-emergency-medical-services-billing-software-market

## Boundary

This repository uses synthetic fixtures only. It has no credentials, no customer data, no outreach data, and no dependency on a hosted API.
