# Grant Scanner — Matching and Evaluation Spec

**Date:** 2026-03-03 (updated 2026-03-06)

## Overview

The grant scanner consists of two Claude Code skills — **`/scan-grants`** and **`/check-grant`** — that read actual call text and evaluate contextual fit against the program's five modules and two tracks. This document defines the matching logic. For full tool specification, see `GRANT_SCANNER_CLI_SPEC.md`.

## Evaluation approach: LLM contextual analysis

The scanner does **not** use keyword-matching heuristics. Instead, it:

1. Fetches the actual call text (or abstract/summary if full text is gated)
2. Loads the dossier context (STRATEGY.md, PROJECT_OVERVIEW.md, all five module fiches)
3. Sends both to Claude for contextual evaluation
4. Produces a structured per-call assessment with scores, reasoning, confidence, and red flags

This is the critical differentiator: a call mentioning "data" or "digital" is not automatically a fit. The LLM reads scope, objectives, and eligibility to confirm genuine alignment.

## Evaluation dimensions

### 1. Track fit

Does the call fund:
- **Track A** — institutional enablement / infrastructure / open science?
- **Track B** — PI-anchored scientific projects with platform work packages?
- **A+B** — both?
- **Neither** — scope doesn't align with the two-track pattern?

### 2. Module fit (0-3 per module)

| Score | Meaning |
|---|---|
| 0 | No fit |
| 1 | Superficial keyword overlap but scope doesn't align |
| 2 | Partial fit, would require creative framing |
| 3 | Strong natural fit |

Modules evaluated:
- **MOD-FAIR-TRAIN** — FAIR data practices, training, adoption, open science compliance
- **MOD-IMG-SERVERS** — imaging repositories, OMERO/XNAT, data infrastructure, governed access
- **MOD-AI-PIPELINES** — validated analysis pipelines, foundation models, AI/ML for imaging, QA
- **MOD-THEORY-AI** — theory-infused AI, generative AI + mechanistic modeling, physics-informed ML, nonlinear dynamics
- **MOD-MULTIMODAL-BIOMARKERS** — multimodal science, biomarker discovery, predictive imaging, digital twins

### 3. Confidence

Overall assessment of whether the call is worth pursuing:
- **HIGH** — strong fit, clear eligibility, actionable
- **MEDIUM** — plausible fit, may require creative framing or partner coordination
- **LOW** — weak fit, likely false positive

### 4. Red flags

Any scope mismatches, eligibility issues, or reasons this might be a false positive. Examples:
- "digital health" used in a clinical IT context that doesn't apply
- Consortium requirements that exceed current partner readiness
- Budget scale misaligned with program scope
- Geographic restrictions that exclude biomaGUNE

## Filtering pipeline

Calls pass through three stages before appearing in the report:

1. **Deadline filter** — minimum 90 days lead time; expired calls excluded; pre-announcements included and flagged
2. **Contextual evaluation** — full assessment against dossier context (call text retrieved via WebFetch)
3. **Composite inclusion rule** — at least one module ≥ 2, confidence MEDIUM or HIGH

Calls that fail the composite rule are listed in the "evaluated but excluded" section of the scan report.

## Dossier context files (loaded for evaluation)

- `STRATEGY.md` — two-track pattern and packaging rules
- `PROJECT_OVERVIEW.md` — program scope, non-goals, phased outcomes
- `MODULES/MOD-FAIR-TRAIN.md`
- `MODULES/MOD-IMG-SERVERS.md`
- `MODULES/MOD-AI-PIPELINES.md`
- `MODULES/MOD-THEORY-AI.md`
- `MODULES/MOD-MULTIMODAL-BIOMARKERS.md`

## Output

See `GRANT_SCANNER_CLI_SPEC.md` sections 6-7 for full output format. Summary:

- **`/scan-grants`:** dated Markdown report (`SCANS/grant_scan_YYYY-MM-DD-NN.md`) grouped by confidence level, plus conversational summary
- **`/check-grant`:** conversational evaluation of a single call (not written to file unless requested)
- **CSV on request:** flat CSV suitable for appending to `GRANT_FIT_MATRIX_TEMPLATE.csv`

## What this does NOT do

- Replace human judgment — this is a filter and structured briefing, not a decision maker
- Submit proposals or pre-register for calls
- Send notifications (v1 — may be added later)
- Guarantee completeness — some calls may not appear on monitored portals
