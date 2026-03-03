# Grant-Fit Matrix (Template)

Maintain one row per opportunity. Map each opportunity to one or more module IDs.

| Opportunity | Geography | Program owner | Module(s) | Track | Eligibility lead | Consortium needs | Scale (EUR) | Duration | Window / deadline | Readiness | Next action | Notes |
|---|---|---|---|---|---|---|---:|---:|---|---|---|---|
| [Name] | [Basque/Spain/EU] | [Funder] | MOD-XXX | A/B | [Institute/PI/Company] | [Partners] |  |  |  |  |  |  |

## Field definitions

- **Module(s):** MOD-FAIR-TRAIN, MOD-IMG-SERVERS, MOD-AI-PIPELINES, MOD-THEORY-AI, MOD-MULTIMODAL-BIOMARKERS
- **Track:** A = institutional enablement; B = PI-anchored science
- **Readiness:** idea / partners / draft / ready
- **Geography:** Basque / Spain / EU / Other

## Workflow

1. When a new opportunity is identified (manually or by the grant scanner), add a row.
2. Score fit using the grant scanner CLI tool (see `GRANT_SCANNER_CLI_SPEC.md` and `BOT_MATCHING_SPEC.md`) or manually evaluate against module fiches.
3. Assign readiness level and next action.
4. When readiness reaches "draft", create a Concept Note using `TEMPLATES/CONCEPT_NOTE_TEMPLATE.md`.
