# Project Overview — Image Data Infrastructure & Analysis to Drive Theory-Infused AI

**Date:** 2026-03-03
**Operational lead:** Ryan Tasseff (CIC biomaGUNE)
**Stakeholders:** institute leadership, IT, PIs/group leaders, core facility staff; ReDIB/ICTS stakeholders; DIPC (compute partnership).

## Executive intent

BiomaGUNE is producing increasing volumes of complex data (especially imaging). Without systematic capture, standards alignment, and governed repositories, the institute pays recurring "hidden costs": duplicated effort, brittle knowledge transfer, limited internal reuse, and avoidable compliance friction. This program builds durable capability so research outputs are **findable, accessible under appropriate controls, interoperable where it matters, and reusable** — and downstream analysis/AI workflows can operate as shared services rather than one-off scripts.

Beyond infrastructure, CIC biomaGUNE can lead a new field of computational biology that integrates nonlinear dynamics, statistical mechanics, and imaging-focused generative AI. The program's longer-term ambition is to unify generative AI and multi-scale biology into a practical paradigm of **theory-infused AI** — models that are data-powerful yet constrained by physics and biology — producing predictive models for biomedicine comparable in reliability to those long established in chemistry and engineering.

## Why biomaGUNE

- **Deep integration by design.** Track record at the interface of chemistry, biology, and materials science; a culture of multi-disciplinary collaboration.
- **Image-centric and multi-scale.** Imaging across scales — microscopy (confocal, fluorescence, expanding to whole-slide and high-resolution dynamic imaging) and biomedical imaging (MRI, PET, SPECT, CT) via ReDIB/ICTS.
- **Mechanistic modeling expertise.** Ongoing molecular dynamics and first-principles projects (atomistic/quantum simulations of plasmonic nanoparticles, protein-nanomaterial interaction modeling).
- **DIPC compute partnership.** Theoretical physics depth and significant compute (including large-scale GPUs) in Donostia-San Sebastian.
- **The gap we fill.** What biomaGUNE lacks is unified AI/ML infrastructure spanning data management, model training, and deployment. What the wider community lacks is a general theoretical framework for theory-infused AI that turns biological data into predictive models. This program delivers both.

## Program scope (what funding supports)

Five fundable modules:

1. **FAIR enablement (training + adoption):** practical routines, templates, and training that make compliance and reuse operational.
2. **Imaging servers (OMERO + XNAT):** governed repositories for microscopy and DICOM imaging with standard ingest + minimal metadata.
3. **AI pipeline factory:** validated, uncertainty-aware production pipelines (segmentation, classification, denoising, registration) built on open foundation models, with domain-shift testing, QA, packaging, and lifecycle management.
4. **Theory-infused AI framework:** formalize the bridge between generative AI and mechanistic modeling (statistical mechanics, nonlinear dynamics, latent ODE/PDE) — the core intellectual differentiator.
5. **Multimodal biomarker discovery & predictive imaging:** PI-led scientific projects that leverage the platform and theory framework to produce publishable outcomes, from biomarker identification through digital-twin prototypes.

## Non-goals (scope guardrails)

- Becoming general-purpose IT support for the institute
- Enforcing "perfect metadata" everywhere up front
- Building a full enterprise data lake in the first 24 months
- Owning scientific interpretation that should remain PI-led
- Promising clinical digital twins before preclinical validation

## Strategy in one sentence

Build **institutional capability** (Track A) that multiple **PI-anchored projects** (Track B) can attach to, with a distinctive **theory-infused AI** framework as the scientific differentiator, ensuring real usage, measurable outcomes, and repeatable funding opportunities.

## Phased outcomes

**Phase I (0-24 months): Foundations**
- Training curriculum + onboarding path per lab/project role
- Clear service boundaries and RACI
- OMERO and XNAT lighthouse workflows demonstrated end-to-end
- At least one cross-group AI pipeline deployed with QA, domain-shift validation, uncertainty-aware triage, and reproducibility documentation
- Theory-infused AI initial formulations documented; one pilot latent-dynamics model on real data
- Core team and skills requirements defined; DIPC collaboration scoped
- Basic adoption and usage metrics reporting

**Phase II (2-5 years): Methods and translational collaborations**
- Physics-infused generative models on multiple imaging modalities
- Multimodal fusion via constrained latent dynamics
- Multi-scale integration validated against longitudinal imaging
- Translational testbeds co-developed with internal platforms, CIC bioGUNE, clinical partners
- 2-3 production AI pipelines with full validation suites

**Phase III (5-10 years): Unified platforms and impact at scale**
- Researcher-facing platform for constrained latent-dynamics modeling with push-button reproducibility
- Federated expansion interoperating with national ICTS/ReDIB nodes under open-science principles
- High-impact use cases: real-time adaptive imaging, organ-/disease-focused digital twins, open tools adopted beyond biomaGUNE

## Dependencies

- Governance decisions (identity/access model; "system of record" for metadata)
- IT collaboration for hosting, backups, and reliability
- PI buy-in for adoption (named "data contact" per lab/project)
- Minimal sustainability line item for sysadmin and maintenance
- DIPC partnership formalization (compute access, joint supervision)
- Core team assembly (computational biologists, mathematicians, computer scientists)

## Primary risks and mitigations

- **Overreach:** mitigate via explicit non-goals, service boundaries, and phased delivery
- **Low adoption:** mitigate via lighthouse pilots and PI anchors
- **Infrastructure without outcomes:** mitigate via end-to-end demos and success metrics
- **Theory-AI too abstract:** mitigate via pilot-on-real-data requirement in Phase I; no proposals without working formulations
- **DIPC dependency:** mitigate via scoped collaboration terms before committing in proposals; maintain institutional compute baseline
