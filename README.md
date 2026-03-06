# Funding Positioning Dossier — Image Data Infrastructure & Analysis to Drive Theory-Infused AI

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

### For internal alignment
Circulate `PROJECT_OVERVIEW.md` to leadership, PIs, and partners.

### For proposal assembly
1. Start from the relevant module fiche(s) in `MODULES/` — these are the source of truth for work packages.
2. Pull credibility text from `EVIDENCE_BANK.md` and `TEAM_PROFILES.md`.
3. Use `TEMPLATES/CONCEPT_NOTE_TEMPLATE.md` to draft a call-specific concept note that maps call language to module IDs.
4. Follow the packaging rules in `STRATEGY.md` (Section 3).

### For funding opportunity tracking
1. **Scan for calls:** run `/scan-grants` (full scan) or `/scan-grants Basque|Spain|EU` (regional). Reports are written to `REPORTS/grant_scan_YYYY-MM-DD.md`.
2. **Evaluate a single call:** run `/check-grant <url>` for a structured assessment (conversational output).
3. **Track opportunities:** add rows to `GRANT_FIT_MATRIX_TEMPLATE.csv`. Each row captures modules, track, readiness level, and next action. See `GRANT_FIT_MATRIX_TEMPLATE.md` for field definitions and workflow.
4. **Plan ahead:** use the `NextAction` column in the CSV to record preparation milestones for future call cycles (e.g., "Oct 2026: begin partner outreach").
5. **Weekly triage (Fridays):** review the matrix, check for deadline changes, update readiness levels.

### For stakeholder sharing
Finished reports in `REPORTS/` are ready to share with PIs, leadership, or external partners:
- `FUNDING_STRATEGY_REPORT.md` — comprehensive strategy overview
- `program_summary_for_PIs.docx` — PI-facing program summary
- `grant_scan_*.md` — scan results with evaluated opportunities

## Key documents

| Document | Purpose |
|---|---|
| `PROJECT_OVERVIEW.md` | 1-2 page narrative for alignment (leadership / PIs / partners) |
| `STRATEGY.md` | Portfolio strategy, two-track pattern, packaging rules, scouting system |
| `ROADMAP.md` | Phased delivery plan with milestones and funding preparation dates |
| `EVIDENCE_BANK.md` | Reusable proof points for proposals |
| `TEAM_PROFILES.md` | Proposal-ready key personnel bios |
| `GRANT_FIT_MATRIX_TEMPLATE.md` + `.csv` | Opportunity tracker — the living list of funding targets |
| `GRANT_SCANNER_CLI_SPEC.md` | Grant scanner architecture and evaluation rubric |
| `BOT_MATCHING_SPEC.md` | Matching and evaluation logic details |
| `ARTIFACT_INDEX.md` | Complete inventory of every file in the dossier |

## Repository structure

```
README.md                       <- You are here
PROJECT_OVERVIEW.md             <- 1-2 page narrative
STRATEGY.md                     <- Portfolio + two-track strategy
ROADMAP.md                      <- Phases, milestones, deliverables
EVIDENCE_BANK.md                <- Reusable proof points
TEAM_PROFILES.md                <- Key personnel bios
GRANT_FIT_MATRIX_TEMPLATE.md    <- Opportunity tracker (instructions + field definitions)
GRANT_FIT_MATRIX_TEMPLATE.csv   <- Opportunity tracker (data — the living matrix)
GRANT_SCANNER_CLI_SPEC.md       <- Grant scanner specification
BOT_MATCHING_SPEC.md            <- Grant scanner matching logic
ARTIFACT_INDEX.md               <- Full file inventory
RyanTasseff_CV.md               <- Operational lead CV (markdown)
RyanTasseff_basic_20250613.docx <- Operational lead CV (original)
MODULES/                        <- Source-of-truth module fiches
  MOD-FAIR-TRAIN.md
  MOD-IMG-SERVERS.md
  MOD-AI-PIPELINES.md
  MOD-THEORY-AI.md
  MOD-MULTIMODAL-BIOMARKERS.md
TEMPLATES/                      <- Reusable templates for proposals
  PROJECT_FICHE_TEMPLATE.md
  CONCEPT_NOTE_TEMPLATE.md
REFERENCE/                      <- Background and reference materials
  GOVERNANCE_RACI.md
  KEYWORDS_TAXONOMY.md
  REFERENCES_INTERNAL.md
  deep-research-report.md                    <- State-of-the-art review (imaging AI, foundation models, validation)
  program_Proposal–Theory-infused_Ai.docx   <- Program proposal document
REPORTS/                        <- Deliverable reports (stakeholder-ready)
  FUNDING_STRATEGY_REPORT.md
  program_summary_for_PIs.docx
  theory_ai_assessment_summary.docx
  grant_scan_2026-03-06.md                   <- Basque Country grant scan (first scan)
bot/                            <- Grant scanner configuration
  README.md                                  <- Scanner invocation guide
  config.yaml                                <- Pointer to command definitions
  sources.yaml                               <- Funding source registry (25 sources, 3 regions)
.claude/commands/               <- Claude Code command definitions
  scan-grants.md                             <- /scan-grants command
  check-grant.md                             <- /check-grant command
```
