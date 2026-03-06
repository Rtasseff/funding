# Strategy — Portfolio Funding Using a Two-Track Pattern

**Date:** 2026-03-03

## 1) Why portfolio funding

"FAIR + imaging servers + production AI + theory-infused modeling + multimodal science" spans distinct funder preferences:
- institutional capability / infrastructure
- open science and interoperability
- method/tool development (AI pipelines, physics-informed ML)
- fundamental research (generative AI + mechanistic modeling)
- scientific discovery and translational impact (biomarkers, digital twins)

A portfolio approach reduces dependency on any single call and supports staged delivery. The addition of theory-infused AI (MOD-THEORY-AI) opens funding lanes in fundamental AI/modeling research (AEI, Horizon Digital/AI) that pure infrastructure proposals cannot access.

## 2) Two-track proposal pattern

### Track A — Institutional enablement
Focus: services, compliance, interoperability, adoption metrics.
Typical calls: open science, institutional digital infrastructure, equipment/infrastructure.

### Track B — PI-anchored scientific projects
Focus: biological/clinical aims led by PIs; platform work as funded WPs; theory-infused modeling as a research program.
Typical calls: health/biomedical research, translational programs, collaborative R&D, AI/modeling research (AEI), GenAI4EU, EuroHPC.

**Rule:** Every Track A deliverable should be proven through at least one Track B anchor.

## 3) Packaging rules (repeatable proposal building)

- Keep a stable umbrella narrative (Program Brief).
- Maintain five module fiches as the source of truth.
- For each call, write a 1-2 page Concept Note that:
  - maps call language to module IDs
  - states eligibility lead and partner needs
  - selects metrics and deliverables appropriate for the call

## 4) Minimal metrics that build funder trust

- **Adoption:** labs onboarded, training completion, DMP coverage
- **Infrastructure:** datasets ingested, TB served, onboarding time, uptime
- **Reuse:** internal reuse events, # analyses run
- **Science:** validated performance reports, publications (Track B)
- **Theory-AI:** formulations published, pilot models on real data, predictive improvement over data-only baselines
- **Partnerships:** DIPC collaboration scoped, external co-development testbeds

## 5) Sustainability pattern (include every time)

Even when modest:
- service/access policy and support model
- maintenance plan and staffing fractions
- cost model (internal allocation / recharge / institute commitment)

## 6) Execution doctrine (how we work — include in workplan narratives)

The program operates with a deliberate execution philosophy that funders can audit:

- **Option creation, then follow pull.** Build small, demonstrable capabilities; expand only when real users pull for more. This prevents over-investment in unused infrastructure.
- **Strict WIP discipline.** One execution wedge at a time per track. Finish and demonstrate before starting the next increment.
- **Lighthouse-first.** Every capability is proven through a named pilot before being generalized. No institute-wide rollouts without demonstrated adoption.
- **Composition over top-down planning.** The program (especially the science layer) is composed from real subprojects, not pitched as a monolithic initiative.

This doctrine is already operational: the current Kanban separates institutional enablement from PI-anchored pilots, limits work-in-progress, and sequences delivery around demonstrated demand.

## 7) Funding scouting system (operational)

- Weekly triage (1 hour/Friday): scan opportunities, score fit, update matrix
- Combined 1-pager (RDM + image analysis) as the standing input to scouting
- Grant-fit matrix as the living tracker (see `GRANT_FIT_MATRIX_TEMPLATE.*`) — populated with 9 opportunities including 3 future-cycle targets (Elkartek 2027, Ikerbasque RF 2027, INKER 2027) with preparation milestones
- Grant scanner commands operational: `/scan-grants` (multi-region) and `/check-grant` (single call) — see `GRANT_SCANNER_CLI_SPEC.md`
- First scan completed 2026-03-06 (Basque): report in `SCANS/grant_scan_2026-03-06.md`
- Scan reports feed the matrix; matrix tracks readiness and next actions per opportunity

## 8) Alignment with regional, national, and European priorities

- **Basque (RIS3 / BRTA):** Serves Bio-Health and Advanced Manufacturing/Nanotech with a strong digitalization layer — FAIR imaging data, generative-AI analytics, and translational tools for nanomedicine. Natural fit for Elkartek/Hazitek consortia; creates local software/data value chains.
- **Spain (ICTS / AEI / ISCIII):** Upgrades analysis on ICTS-linked imaging infrastructure (ReDIB node), aligning with national goals in AI, personalized medicine, and research modernization. Fundable via AEI (AI/modeling) and ISCIII (biomedical data) programs.
- **Europe (Horizon / GenAI4EU / EOSC):** Maps to Horizon Europe Health & Digital (multimodal data, trustworthy AI, digital twins) and GenAI4EU opportunities; commits to EOSC-style openness; can leverage EuroHPC at scale.

## 9) Deliverable reports

Finished reports live in `REPORTS/`. These are stakeholder-ready documents assembled from the dossier's source-of-truth files (module fiches, evidence bank, strategy, roadmap). Keep source files current; regenerate reports as needed.

## 10) Guardrails

- Avoid "infinite platform" framing; fund the next implementable increment.
- Prefer measurable deliverables to aspirational language.
- Avoid institute-wide enforcement commitments until lighthouse pilots demonstrate adoption.
- Theory-infused AI proposals must include working formulations and real-data pilots, not aspirational whitepapers.
- Do not promise clinical digital twins before preclinical validation is demonstrated.
