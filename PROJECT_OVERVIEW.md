# Project Overview — AI-Ready Imaging Data Infrastructure & Reuse

**Date:** 2026-03-03
**Operational lead:** Ryan Tasseff (CIC biomaGUNE)
**Stakeholders:** institute leadership, IT, PIs/group leaders, core facility staff; ReDIB/ICTS stakeholders where relevant.

## Executive intent

BiomaGUNE is producing increasing volumes of complex data (especially imaging). Without systematic capture, standards alignment, and governed repositories, the institute pays recurring "hidden costs": duplicated effort, brittle knowledge transfer, limited internal reuse, and avoidable compliance friction. This program builds durable capability so research outputs are **findable, accessible under appropriate controls, interoperable where it matters, and reusable**—and downstream analysis/AI workflows can operate as shared services rather than one-off scripts.

## Program scope (what funding supports)

Four fundable modules:

1. **FAIR enablement (training + adoption):** practical routines, templates, and training that make compliance and reuse operational.
2. **Imaging servers (OMERO + XNAT):** governed repositories for microscopy and DICOM imaging with standard ingest + minimal metadata.
3. **AI pipeline factory:** validated "production" pipelines (segmentation/denoising/registration), packaging, QA, and lifecycle management.
4. **Multimodal biomarker discovery:** PI-led scientific projects that leverage the platform to produce publishable outcomes.

## Non-goals (scope guardrails)

- Becoming general-purpose IT support for the institute
- Enforcing "perfect metadata" everywhere up front
- Building a full enterprise data lake in the first 24 months
- Owning scientific interpretation that should remain PI-led

## Strategy in one sentence

Build **institutional capability** (Track A) that multiple **PI-anchored projects** (Track B) can attach to, ensuring real usage, measurable outcomes, and repeatable funding opportunities.

## 12-24 month outcomes

**Operational**
- Training curriculum + onboarding path per lab/project role
- Clear service boundaries and RACI
- Basic adoption and usage metrics reporting

**Technical**
- OMERO lighthouse workflow demonstrated end-to-end
- XNAT lighthouse workflow demonstrated end-to-end
- At least one cross-group AI pipeline deployed with QA + reproducibility documentation

**Institutional**
- Reduced time-to-find and time-to-reuse datasets internally
- Improved compliance posture (DMP + publication-linked archiving)
- Increased attractiveness for external collaborations and consortia

## Dependencies

- Governance decisions (identity/access model; "system of record" for metadata)
- IT collaboration for hosting, backups, and reliability
- PI buy-in for adoption (named "data contact" per lab/project)
- Minimal sustainability line item for sysadmin and maintenance

## Primary risks and mitigations

- **Overreach:** mitigate via explicit non-goals and service boundary
- **Low adoption:** mitigate via lighthouse pilots and PI anchors
- **Infrastructure without outcomes:** mitigate via end-to-end demos and success metrics
