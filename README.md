# Pre Scrub

An ambulance billing pre submission scrubber: predicts the denial reason from the closed ePCR + dispatch trace, points the medic at the missing field, and proves it would have cleared payer adjudication.

![Pre Scrub working dashboard](outputs/project_working.svg)

## Why it exists

Ambulance claim denials are not random. They cluster on a small set of failure modes that are deterministic given the document: missing origin/destination modifiers (RH/SH/QL...), medical necessity narrative that doesn't justify the HCPCS A code chosen (A0427 ALS Emergency vs A0429 BLS Emergency), missing PCS (Physician Certification Statement) for non.

The project is intentionally built as a local replay harness instead of a slide. It creates fixtures, plants realistic failure modes, produces citation-locked evidence, and turns the result into a dashboard a reviewer can inspect without credentials or hosted services.

## What is inside

- Deterministic fixture generation for the company-specific risk surface.
- Strategy code in `src/pre_scrub/strategy.py` with project-specific scoring and visual evidence.
- Citation-locked reports where every decision claim points to a generated evidence ID.
- Two regenerated visual artifacts: `outputs/project_working.svg` and `outputs/evidence_map.svg`.
- A portable demo pack with JSON, CSV, Markdown, HTML, SVG, benchmark, and test artifacts.

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

## Boundary

Everything runs locally against synthetic fixtures. There are no credentials, no customer records, no outreach files, and no hosted API dependency.
