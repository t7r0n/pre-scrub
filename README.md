# Pre Scrub

An ambulance billing pre submission scrubber: predicts the denial reason from the closed ePCR + dispatch trace, points the medic at the missing field, and proves it would have cleared payer adjudication.

![Pre Scrub working dashboard](outputs/project_working.svg)

## Why it exists

Ambulance claim denials are not random.

Most internal demos stop at a pretty chart. This repository is built around the harder part: a repeatable path from fixture, to failure, to evidence, to the operator action a serious team would actually trust.

## What is inside

- A deterministic replay harness tuned around ambulance, claim, and denials.
- Company-specific strategy code in `src/pre_scrub/strategy.py`, not just README-level customization.
- Citation-locked reports where every decision claim has to point back to a generated evidence ID.
- Two visual artifacts generated from the latest run: `outputs/project_working.svg` and `outputs/evidence_map.svg`.
- A portable demo pack with JSON, CSV, Markdown, HTML, SVG, and benchmark artifacts.

![Pre Scrub evidence map](outputs/evidence_map.svg)

## Signals it measures

- `ambulance coverage`
- `claim risk`
- `denials precision`
- `random latency`

## Failure modes it plants

- ambulance drift
- claim gap
- denials misroute
- random blindspot

## Run it locally

```bash
uv sync
uv run pre-scrub all
uv run pytest -q
uv run ruff check .
```

## Outputs worth opening

- `outputs/dashboard.html`
- `outputs/project_working.svg`
- `outputs/evidence_map.svg`
- `outputs/operator_brief.md`
- `outputs/decision_report.md`
- `outputs/strategy_model.json`
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

Everything runs locally against synthetic fixtures. There are no credentials, no customer records, no outreach files, and no hosted API dependency.
