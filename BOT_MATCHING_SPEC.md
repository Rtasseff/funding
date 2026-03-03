# Bot Matching Spec — Machine-Friendly Fields for Automated Triage

**Date:** 2026-03-03

## Goal

Enable automated scanning of funding opportunities and matching to module fiches with minimal human interpretation.

## How this works

Each module fiche begins with a YAML header with standardized fields. A monitoring workflow can:
1. Extract opportunity text (title, abstract, eligibility, themes, budget, deadlines)
2. Score fit against module keywords and constraints
3. Recommend Track A or Track B configuration
4. Produce a short triage note + suggested next action

## Required module fields (YAML)

- `module_id`
- `module_name`
- `track_type` (A / B / both)
- `time_horizon`
- `readiness_level`
- `eligible_lead_types` (institution / PI_as_anchor / company / consortium)
- `best_fit_geographies`
- `budget_class` (small / medium / large)
- `keywords` (controlled list; see `REFERENCE/KEYWORDS_TAXONOMY.md`)
- `core_assets`
- `dependencies`
- `success_metrics`
- `last_updated`

## Opportunity fields to extract

- name, funder, geography
- themes/keywords
- eligibility and consortium requirements
- budget scale and allowed costs
- windows/deadlines
- evaluation criteria (if available)

## Simple scoring heuristic

- +2 per keyword match (capped)
- +3 if eligibility matches module `eligible_lead_types`
- +2 if allowed costs align with module `budget_class`
- +2 if geography fits
- -3 if consortium requirements exceed current partner readiness

Output: top 1-2 modules + recommended Track + next action

## Data sources (to be configured)

See `bot/config.yaml` for opportunity feed configuration.

## Implementation status

See `bot/README.md` for current development status.
