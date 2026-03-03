# MOD-MULTIMODAL-BIOMARKERS — Multimodal AI for Biomarker Discovery & Predictive Imaging (Science Layer)

```yaml
module_id: MOD-MULTIMODAL-BIOMARKERS
module_name: Multimodal AI for Biomarker Discovery & Predictive Imaging (Science Layer)
track_type: B
time_horizon: 24_months_initial, 10_years_full
readiness_level: concept_and_partnering
eligible_lead_types: [PI_as_anchor, consortium]
best_fit_geographies: [Basque, Spain, EU]
budget_class: medium_to_large
keywords:
  - biomarker, multimodal, data integration
  - cohort, clinical translation, predictive modeling, validation
  - digital twins, adaptive acquisition, real-time imaging
  - individualized prediction, decision support
  - longitudinal imaging, time-series analysis
  - multimodal fusion (microscopy, PET, MRI, SPECT, CT, optical)
  - preclinical imaging, translational testbeds
core_assets:
  - institute imaging strengths across microscopy and biomedical modalities (ReDIB/ICTS)
  - translational link opportunities (CIC bioGUNE, clinical partners)
  - AI pipeline infrastructure (MOD-AI-PIPELINES) for production-grade analysis
  - theory-infused modeling framework (MOD-THEORY-AI) for predictive applications
  - DIPC compute partnership for large-scale model training
dependencies:
  - PI anchors and access to cohorts/datasets (named anchors required before leading proposals)
  - platform substrate (FAIR practices + servers + pipelines)
  - theory-infused AI framework (MOD-THEORY-AI) for digital-twin and predictive applications
  - longitudinal / time-series imaging datasets for predictive model validation
success_metrics:
  - publications and validated biomarker claims
  - external collaborations and follow-on funding
  - reusable datasets under appropriate controls
  - "# predictive models demonstrating individualized prediction on preclinical endpoints"
  - "digital-twin prototype(s) with quantified prediction accuracy vs. conventional analysis"
  - decision-support demonstrations in live imaging experiments
last_updated: 2026-03-03
```

## One-sentence positioning

PI-led multimodal projects that use the platform modules to generate publishable, validated biomarker insights and predictive imaging applications — from discovery through digital-twin prototypes — converting infrastructure and theory capability into scientific outcomes.

## Current state

- Currently at **concept and partnering** stage — honest assessment.
- DIAP (Data Infrastructure and Analysis Program) is being composed from real subprojects rather than pitched as a top-down initiative. **DIAP defining document targeted for June 2026.**
- Candidate subprojects are emerging from the imaging-RDM pilots and AI pipeline work, but named PI anchors and defined cohorts/datasets are needed before this module leads any proposal.
- Digital-twin and predictive imaging applications are Phase II/III ambitions that depend on the groundwork in MOD-THEORY-AI; this module provides the scientific use cases and validation endpoints.

## Scope: two layers

### Layer 1 — Biomarker discovery (near-term, 12-24 months)

Classical multimodal AI for biomarker identification:
- Multimodal fusion of imaging with clinical, omics, or report-derived features
- Classification, prognostic scoring, and cohort stratification
- Built on foundation-model-first pipelines from MOD-AI-PIPELINES
- Validated with domain-shift testing and TRIPOD+AI-aligned reporting

### Layer 2 — Predictive imaging and digital twins (medium-term, 3-5+ years)

Theory-infused predictive applications leveraging MOD-THEORY-AI:
- **Digital-twin workflows** for adaptive acquisition — models that predict optimal next-scan parameters in real time based on current imaging state
- **Individualized predictions** in preclinical settings — trajectory forecasting for individual animals/samples using constrained latent dynamics
- **Decision support in live imaging experiments** — real-time model inference during acquisition to guide experimental decisions
- **Multimodal fusion via constrained latent dynamics** — microscopy <-> PET/MRI/optical signal integration through shared mechanistic latent spaces

## 12-24 month deliverables

- 1-2 anchor questions with defined modalities and cohorts (Layer 1).
- Platform modules implemented as work packages (data capture, servers, pipelines).
- At least one publishable result plus reusable datasets under controlled access.
- Requirements document for Layer 2 digital-twin applications: identify candidate datasets with longitudinal/temporal structure suitable for predictive modeling.

## Vision (3-10 years)

- Multiple PI-led programs running on the platform substrate, producing publishable multimodal biomarker insights (Layer 1 at scale).
- Reusable cohort datasets under governed access attracting external collaborators.
- Digital-twin prototypes demonstrated on at least one preclinical use case with quantified predictive improvement over conventional analysis (Layer 2).
- Real-time adaptive imaging demonstrations in collaboration with microscopy/imaging platforms.
- Follow-on funding driven by scientific results, not just infrastructure promises.
- Translational testbeds co-developed with CIC bioGUNE, clinical partners, and compute centers.

## Guardrails

- This module is the **science proof layer**. Avoid using it to justify infrastructure without clear scientific anchors.
- **Do not lead with this module in proposals until at least 1-2 PI-anchored candidate datasets/projects and a plausible "first paper" path are identified.**
- **Layer 2 (digital twins) depends on MOD-THEORY-AI groundwork.** Do not promise digital-twin deliverables in 12-24 month proposals; these are 3-5 year outcomes.
- Keep predictive imaging scoped to **preclinical settings first**. Clinical digital-twin claims require regulatory and ethical groundwork beyond current scope.
