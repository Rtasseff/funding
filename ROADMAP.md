# Roadmap — Phased Delivery Plan

**Date:** 2026-03-03

## Phase 0 (0-3 months): Package + alignment — UNDERWAY

**Done or in progress:**
- Two lighthouse pilots identified and active: gjesus3 (microscopy) and Nuke (DICOM)
- Grant-fit matrix stood up; weekly Friday triage routine operational
- DMP kit, OA archiving workflow, and officialization package in progress
- SegOid pipeline already in user-driven iteration
- Funding positioning dossier bootstrapped (this repository)
- Program proposal drafted ("Theory-infused AI for Biomedical Imaging")

**Remaining:**
- Finalize v1.0 of the five module fiches
- Agree governance/RACI and service boundaries (draft exists, needs steering group sign-off)
- DIAP defining document (targeted June 2026)
- Scope DIPC compute partnership (formal collaboration terms)

## Phase I (3-24 months): Foundations

**FAIR enablement**
- Training curriculum v1 + onboarding path for labs/projects
- Minimum compliance assets fully operational (checklists, templates, SOPs formalized)
- DMP-to-Group protocol rolled out to first adopter groups

**Imaging servers**
- OMERO pilot (building on gjesus3 registry work) demonstrated end-to-end for one lab workflow
- XNAT pilot (building on Nuke DICOM work) demonstrated end-to-end for one lab workflow
- Permissions model + backups verified

**AI pipeline factory**
- SegOid formalized as first "production" pipeline with QA criteria, containerized packaging, and domain-shift validation report
- Foundation-model-first architecture established: open pretrained encoders (UNI/CONCH for microscopy, 3DINO/MST for 3D imaging) evaluated as frozen feature extractors with freeze-then-probe baselines
- Basic model registry/versioning with model cards and provenance documentation
- At least one additional pipeline candidate identified from user demand, with uncertainty-aware triage layer designed
- Reusable validation protocol template published for PI-anchored projects

**Theory-infused AI (groundwork)**
- Initial formulations documented and shared: entropy-based latent occupancy, manifold-constrained dynamics, variable-transformed latent dynamics
- One pilot latent-dynamics model on a real BiomaGUNE imaging dataset with temporal/longitudinal structure
- Core team and skills requirements defined (computational biologists, mathematicians, computer scientists)
- Joint seminars with microscopy/imaging platforms initiated
- DIPC collaboration scope formalized (compute access, joint supervision)
- Publication or preprint: initial formulation paper targeting computational biology or physics-informed ML venue

**Multimodal biomarkers (Layer 1 setup)**
- 1-2 anchor questions identified with defined modalities, cohorts, and PI anchors
- Requirements document for Layer 2 digital-twin applications: candidate datasets with longitudinal structure
- Platform modules implemented as work packages (data capture, servers, pipelines)

## Phase II (2-5 years): Methods and translational collaborations

**Infrastructure at scale**
- Expand adoption to additional labs/projects
- Formalize intake/triage and office hours support model
- Add QA/benchmark datasets and failure-mode reporting with TRIPOD+AI-aligned validation reports
- Expand to 2-3 production pipelines, each with domain-shift validation, uncertainty flagging, and explainability outputs
- IP/freedom-to-operate review completed for any pipeline approaching translational use

**Theory-infused AI (advanced methods)**
- Physics-infused generative models operational on multiple imaging modalities
- Multimodal fusion (microscopy <-> PET/MRI/optical) via constrained latent dynamics
- Multi-scale integration: link micro- to meso-/macro-scale imaging signals via constrained latent dynamics; validate against longitudinal imaging
- Uncertainty and interpretability by design from the dynamical structure
- Demonstrate predictive improvements from theory-infused constraints on existing datasets

**Multimodal biomarkers and predictive imaging**
- At least one publishable result plus reusable datasets under controlled access (Layer 1)
- Digital-twin prototype(s) on preclinical use cases with quantified predictive improvement
- Translational testbeds co-developed with internal platforms, CIC bioGUNE, clinical partners, and compute centers

## Phase III (5-10 years): Unified platforms and impact at scale

**Federated infrastructure**
- Interoperability beyond the institute (consortia/EOSC-aligned where appropriate)
- Multi-site datasets and governed sharing models
- Federated expansion interoperating with national ICTS/ReDIB nodes under open-science principles

**Unified theory-AI platform**
- Researcher-facing suite for constrained latent-dynamics modeling with push-button reproducibility
- Uncertainty/interpretability and model lifecycle management integrated

**High-impact science**
- Multiple PI-led programs producing publishable multimodal biomarker insights at scale
- Real-time adaptive imaging demonstrations in live experiments
- Organ- or disease-focused digital twins in preclinical settings
- Open tools adopted beyond biomaGUNE
- Follow-on funding driven by scientific results, not just infrastructure promises

## Milestones

- **M1:** Module fiches v1.0 complete (all five)
- **M2:** OMERO lighthouse end-to-end demonstration
- **M3:** XNAT lighthouse end-to-end demonstration
- **M4:** First cross-group AI pipeline in production use with domain-shift validation and uncertainty-aware triage
- **M5:** Adoption metrics reported (labs, datasets, reuse signals)
- **M6:** Theory-infused AI initial formulations published; pilot model on real data demonstrated
- **M7:** DIPC collaboration formally scoped and operational
- **M8:** First PI-anchored biomarker result published
- **M9:** Digital-twin prototype demonstrated on preclinical use case
- **M10:** Unified theory-AI platform available to internal users
