# Funding Initiative Artifacts (Project Bootstrap)

**Purpose:** Reusable "funding positioning dossier" for a multi-year program at CIC biomaGUNE:
1. FAIR data practices and adoption
2. Imaging data servers and governed access (OMERO + XNAT)
3. Cross-group AI production pipelines (foundation-model-first)
4. Theory-infused AI framework (generative AI + mechanistic modeling)
5. Multimodal biomarker discovery & predictive imaging (PI-led science layer)

**Created:** 2026-03-03

## What's inside

### Core strategy documents
- `README.md` — quick orientation and repo structure
- `PROJECT_OVERVIEW.md` — 1-2 page narrative for alignment (leadership / PIs / partners)
- `STRATEGY.md` — portfolio + two-track strategy and packaging rules
- `ROADMAP.md` — phases, milestones, and deliverables
- `EVIDENCE_BANK.md` — reusable "why this team / why this institute" proof points
- `TEAM_PROFILES.md` — proposal-ready key personnel bios (linked to CV)

### Opportunity tracking and grant scanning
- `GRANT_FIT_MATRIX_TEMPLATE.md` — opportunity tracker instructions
- `GRANT_FIT_MATRIX_TEMPLATE.csv` — opportunity tracker data (machine-readable)
- `GRANT_SCANNER_CLI_SPEC.md` — grant scanner specification (sources, scanning strategy, evaluation rubric, output format, skill invocation)
- `BOT_MATCHING_SPEC.md` — grant scanner matching and evaluation logic (contextual analysis, module scoring, filtering pipeline)

### Module fiches (`MODULES/`)
- `MOD-FAIR-TRAIN.md` — FAIR Data Practices Enablement (Training + Adoption)
- `MOD-IMG-SERVERS.md` — Imaging Data Infrastructure (OMERO + XNAT)
- `MOD-AI-PIPELINES.md` — Cross-Group AI Pipeline Factory (foundation-model-first, validated, uncertainty-aware)
- `MOD-THEORY-AI.md` — Theory-Infused AI Framework (Generative AI + Mechanistic Modeling)
- `MOD-MULTIMODAL-BIOMARKERS.md` — Multimodal AI for Biomarker Discovery & Predictive Imaging

### Templates (`TEMPLATES/`)
- `PROJECT_FICHE_TEMPLATE.md` — blank module fiche template
- `CONCEPT_NOTE_TEMPLATE.md` — call-specific concept note template

### Reference materials (`REFERENCE/`)
- `GOVERNANCE_RACI.md` — roles, decision rights, and service boundaries
- `KEYWORDS_TAXONOMY.md` — controlled keywords for matching/reporting
- `REFERENCES_INTERNAL.md` — pointers to existing BiomaGUNE RDM artifacts
- `deep-research-report.md` — state-of-the-art review: imaging AI classification, foundation models, validation practices, datasets, IP landscape
- `program_Proposal–Theory-infused_Ai.docx` — program proposal: Image Data Infrastructure & Analysis to Drive Theory-Infused AI (vision, aims, phased roadmap, alignment)

### Grant scanner (`bot/`)
- `bot/README.md` — grant scanner status and invocation guide
- `bot/config.yaml` — configuration notes (evaluation parameters embedded in skill definitions)
- `bot/sources.yaml` — funding source registry (25 sources across EU, Spain, Basque Country)

### Grant scanner commands (`.claude/commands/`)
- `.claude/commands/scan-grants.md` — multi-region scanning skill (`/scan-grants`)
- `.claude/commands/check-grant.md` — single-call evaluation skill (`/check-grant`)

### Deliverable reports (`REPORTS/`)
- `FUNDING_STRATEGY_REPORT.md` — detailed funding strategy report covering program vision, five modules, phased roadmap, funding alignment, and execution doctrine (PI-shareable)
- `program_summary_for_PIs.docx` — PI-facing program summary
- `theory_ai_assessment_summary.docx` — theory-infused AI assessment summary

### Grant scan output (`SCANS/`)
- `grant_scan_2026-03-06.md` — Basque Country grant scan report (first operational scan): Elkartek, Ikerbasque RF, INKER, Hazitek, Azpitek, IKERTALDE, PIBA, BERC/CIC evaluated

### Personnel
- `RyanTasseff_CV.md` — operational lead CV (markdown)
- `RyanTasseff_basic_20250613.docx` — operational lead CV (original)

## Recommended workflow

1. Read `PROJECT_OVERVIEW.md` and `STRATEGY.md` to align on scope and framing.
2. Treat each file in `MODULES/` as "source of truth" for proposal work packages.
3. Track opportunities in the Grant-Fit Matrix and link them to module IDs.
4. Keep `EVIDENCE_BANK.md` and `TEAM_PROFILES.md` current; they prevent rewriting credibility text every time.
5. Share finished deliverable reports from `REPORTS/` with PIs, leadership, or partners.

## Naming conventions

- Umbrella program: "Image Data Infrastructure & Analysis to Drive Theory-Infused AI"
- Module sheets: "Project Fiche"
- Call adaptation: "Concept Note"
