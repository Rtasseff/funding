# MOD-AI-PIPELINES — Cross-Group AI Pipeline Factory (Production Workflows)

```yaml
module_id: MOD-AI-PIPELINES
module_name: Cross-Group AI Pipeline Factory (Production Workflows)
track_type: both
time_horizon: 24_months_initial, 5_years_full
readiness_level: pilot_to_operational
eligible_lead_types: [institution, PI_as_anchor, consortium]
best_fit_geographies: [Basque, Spain, EU]
budget_class: medium
keywords: [segmentation, denoising, registration, reproducibility, validation, benchmarking, model registry, QA/QC, containerization, GPU scheduling]
core_assets:
  - existing pilot pipelines (to be referenced in Evidence Bank)
  - institutional demand across groups for repeatable analysis
dependencies:
  - imaging server substrate for data access/versioning (preferred)
  - reference datasets + annotations for validation
  - compute allocation (GPU) and packaging standards
success_metrics:
  - "# pipelines in production use by multiple groups"
  - validated performance reports + failure-mode documentation
  - "# analyses run and turnaround time"
  - reproducibility artifacts (containers, configs, versioning)
last_updated: 2026-03-03
```

## One-sentence positioning

Establish a "pipeline factory" that turns research-grade scripts into validated, reproducible analysis services usable by multiple groups, with QA and lifecycle management.

## Current state

- **SegOid pipeline** already in a production-ish loop: user-driven pull, retraining requests, packaging update cycle. This is the first "portfolio story" — a real pipeline with real adoption, not a plan.
- Institutional demand exists across multiple groups for repeatable analysis (segmentation, denoising, registration).
- Execution doctrine: option creation then follow user pull, strict WIP discipline, one execution wedge at a time.

## 12-24 month deliverables

- Acceptance criteria for "production" pipelines (QA, docs, versioning).
- Minimal model registry/versioning approach.
- 1-2 pipelines delivered end-to-end with benchmarks and a stable run path.
- Reference datasets/evaluation reports that a funder can audit.

## Guardrail

Keep this module scoped to *validated service delivery*, not open-ended AI research.
