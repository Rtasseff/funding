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
- `GRANT_SCANNER_CLI_SPEC.md` — grant scanner CLI tool specification (full spec: sources, filtering, LLM evaluation, output format, CLI interface)
- `BOT_MATCHING_SPEC.md` — grant scanner matching and evaluation logic (LLM contextual analysis, module scoring, filtering pipeline)

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
- `program_Proposal–Theory-infused_Ai.docx` — program proposal: Theory-infused AI for Biomedical Imaging (vision, aims, phased roadmap, alignment)

### Grant scanner CLI development (`bot/`)
- `bot/README.md` — grant scanner CLI tool status, commands, and setup
- `bot/config.yaml` — reference configuration template (runtime config at `~/.grant-scanner/`)

### Personnel
- `RyanTasseff_CV.md` — operational lead CV (markdown)
- `RyanTasseff_basic_20250613.docx` — operational lead CV (original)

## Recommended workflow

1. Read `PROJECT_OVERVIEW.md` and `STRATEGY.md` to align on scope and framing.
2. Treat each file in `MODULES/` as "source of truth" for proposal work packages.
3. Track opportunities in the Grant-Fit Matrix and link them to module IDs.
4. Keep `EVIDENCE_BANK.md` and `TEAM_PROFILES.md` current; they prevent rewriting credibility text every time.

## Naming conventions

- Umbrella program: "Theory-Infused AI for Biomedical Imaging"
- Module sheets: "Project Fiche"
- Call adaptation: "Concept Note"
