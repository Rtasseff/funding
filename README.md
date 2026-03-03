# Funding Positioning Dossier — Theory-Infused AI for Biomedical Imaging

This dossier supports a **portfolio funding strategy** at **CIC biomaGUNE (Donostia-San Sebastian)**. It contains reusable, call-agnostic documents that can be adapted into grant submissions in Spain, the Basque Country, and the EU.

## Program framing

**Umbrella goal:** Build institute capability for **FAIR data capture + governed imaging repositories + validated analysis/AI pipelines + theory-infused modeling**, enabling faster, reproducible discovery, predictive biomedical models, and stronger external collaboration.

This is intentionally modular: each module can be funded and delivered independently while reinforcing the overall program. The distinctive scientific differentiator is a **theory-infused AI** framework that bridges generative AI with mechanistic modeling (statistical mechanics, nonlinear dynamics).

## Two-track proposal pattern

- **Track A — Institutional enablement (infrastructure/open science):** institute capability, services, compliance, interoperability, adoption metrics.
- **Track B — Scientific anchors (PI-led projects):** biological/clinical aims led by PIs, with platform capability as a work package.

## Modules (see `MODULES/`)

1. **MOD-FAIR-TRAIN** — FAIR Data Practices Enablement (Training + Adoption)
2. **MOD-IMG-SERVERS** — Imaging Data Infrastructure (OMERO + XNAT)
3. **MOD-AI-PIPELINES** — Cross-Group AI Pipeline Factory (foundation-model-first, validated, uncertainty-aware)
4. **MOD-THEORY-AI** — Theory-Infused AI Framework (Generative AI + Mechanistic Modeling)
5. **MOD-MULTIMODAL-BIOMARKERS** — Multimodal AI for Biomarker Discovery & Predictive Imaging (science layer)

## What "done" looks like (12-24 months)

- Training/adoption model operating with clear service boundaries
- One microscopy workflow demonstrated end-to-end on an imaging server
- One DICOM workflow demonstrated end-to-end on an imaging server
- At least one validated AI pipeline usable by multiple groups, with domain-shift testing and uncertainty-aware triage
- Theory-infused AI initial formulations documented; pilot model on real data
- DIPC compute partnership scoped
- Metrics: onboarding time, datasets served, adoption rates, reuse signals

## How to use this dossier

- **Internal alignment:** circulate `PROJECT_OVERVIEW.md`
- **Call triage:** populate `GRANT_FIT_MATRIX_TEMPLATE.*`
- **Proposal assembly:** copy/paste from module fiches, then tailor to call language
- **Credibility:** reuse text and numbers from `EVIDENCE_BANK.md` and `TEAM_PROFILES.md`
- **Stakeholder reports:** share finished documents from `REPORTS/` with PIs, leadership, or partners
- **Grant scanning:** see `GRANT_SCANNER_CLI_SPEC.md`, `BOT_MATCHING_SPEC.md`, and `bot/`

## Repository structure

```
README.md                       <- You are here
PROJECT_OVERVIEW.md             <- 1-2 page narrative for leadership/PIs/partners
STRATEGY.md                     <- Portfolio + two-track strategy
ROADMAP.md                      <- Phases, milestones, deliverables
EVIDENCE_BANK.md                <- Reusable proof points for proposals
TEAM_PROFILES.md                <- Proposal-ready key personnel bios
GRANT_FIT_MATRIX_TEMPLATE.md    <- Opportunity tracker (instructions)
GRANT_FIT_MATRIX_TEMPLATE.csv   <- Opportunity tracker (data)
GRANT_SCANNER_CLI_SPEC.md       <- Grant scanner CLI tool specification
BOT_MATCHING_SPEC.md            <- Grant scanner matching and evaluation logic
ARTIFACT_INDEX.md               <- Full index of all artifacts
RyanTasseff_CV.md               <- Operational lead CV (markdown)
RyanTasseff_basic_20250613.docx <- Operational lead CV (original)
MODULES/
  MOD-FAIR-TRAIN.md
  MOD-IMG-SERVERS.md
  MOD-AI-PIPELINES.md
  MOD-THEORY-AI.md
  MOD-MULTIMODAL-BIOMARKERS.md
TEMPLATES/
  PROJECT_FICHE_TEMPLATE.md
  CONCEPT_NOTE_TEMPLATE.md
REFERENCE/
  GOVERNANCE_RACI.md
  KEYWORDS_TAXONOMY.md
  REFERENCES_INTERNAL.md
  deep-research-report.md                    <- State-of-the-art review (imaging AI, foundation models, validation)
  program_Proposal–Theory-infused_Ai.docx   <- Program proposal: Theory-infused AI for Biomedical Imaging
REPORTS/                        <- Deliverable reports for stakeholders
  FUNDING_STRATEGY_REPORT.md                   <- Detailed funding strategy report (PI-shareable)
  theory_ai_assessment_summary.docx            <- Theory-infused AI assessment summary
bot/                            <- Grant scanner CLI tool development
  README.md
  config.yaml
```
