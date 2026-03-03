# MOD-THEORY-AI — Theory-Infused AI Framework (Generative AI + Mechanistic Modeling)

```yaml
module_id: MOD-THEORY-AI
module_name: Theory-Infused AI Framework (Generative AI + Mechanistic Modeling)
track_type: both
time_horizon: 24_months_groundwork, 10_years_full
readiness_level: concept_to_pilot
eligible_lead_types: [PI_as_anchor, consortium, institution]
best_fit_geographies: [Basque, Spain, EU]
budget_class: medium_to_large
keywords:
  - theory-infused AI, physics-informed neural networks
  - generative AI, latent variable models, variational autoencoders
  - statistical mechanics, nonlinear dynamics, bifurcation analysis
  - latent ODE/PDE, neural ODE, manifold-constrained dynamics
  - entropy-based regularization, probability-based constraints
  - multi-scale modeling, agent-based modeling
  - mechanistic modeling, first-principles biology
  - digital twins, predictive modeling
  - interpretability by construction, uncertainty quantification
core_assets:
  - operational lead with PhD in nonlinear dynamics (NSF IGERT Fellow) and career in mechanistic biological modeling
  - institutional molecular dynamics and first-principles simulation expertise (atomistic/quantum, plasmonic nanoparticles, protein-nanomaterial interactions)
  - DIPC compute partnership (theoretical physics depth + large-scale GPU access)
  - imaging substrate across microscopy and biomedical modalities (ReDIB/ICTS)
  - AI pipeline infrastructure (MOD-AI-PIPELINES) providing production-grade foundation model encoders
dependencies:
  - FAIR data infrastructure (MOD-FAIR-TRAIN + MOD-IMG-SERVERS) for governed, versioned datasets
  - production AI pipelines (MOD-AI-PIPELINES) providing pretrained encoders and validated baseline workflows
  - PI anchors with mechanistic modeling questions and longitudinal imaging datasets
  - compute allocation (GPU/HPC) — DIPC partnership and institutional resources
  - core team assembly: computational biologists, mathematicians, computer scientists
success_metrics:
  - "initial formulations published (entropy-based latent occupancy, manifold-constrained dynamics, variable-transformed latent dynamics)"
  - "# pilot models demonstrating predictive improvement from theory-infused constraints vs. data-only baselines"
  - "validated on real imaging datasets with quantified uncertainty and interpretability"
  - "adoption by internal PI groups for mechanistic questions"
  - "publications in computational biology / physics-informed ML venues"
  - "external collaborations (DIPC, clinical partners, compute centers)"
last_updated: 2026-03-03
```

## One-sentence positioning

Formalize a framework where generative AI and first-principles biology constrain each other — learned manifolds regularize mechanistic dynamics, and physics/biology constrain learned representations — producing predictive, interpretable models for biomedical imaging that go beyond descriptive analytics.

## Core premise

Generative AI (foundational simulators, large language models, image/video systems) has shown that massive, heterogeneous examples can robustly capture reality. Biological mechanistic modeling has struggled with complexity, missing parameters, and limited predictive accuracy. The theory-infused approach bridges these: generative AI informs and constrains mechanistic models, while mechanistic structure regularizes and interprets learned representations. The outcome is models that are data-powerful yet constrained by physics and biology.

## Why biomaGUNE

- **Deep integration by design.** Track record at the interface of chemistry, biology, and materials science with a culture of multi-disciplinary collaboration.
- **Image-centric and multi-scale.** Imaging across scales — microscopy (confocal, fluorescence, expanding to whole-slide and high-resolution dynamic imaging) and biomedical imaging (MRI, PET, SPECT, CT) via ReDIB/ICTS.
- **Mechanistic modeling expertise.** Ongoing molecular dynamics and first-principles projects (atomistic/quantum simulations of plasmonic nanoparticles, protein-nanomaterial interaction modeling).
- **DIPC compute partnership.** Theoretical physics depth and significant compute (including large-scale GPUs) for AI development, located in Donostia-San Sebastian.

## Current state

- Currently at **concept and early formulation** stage.
- Operational lead (Tasseff) has direct background in the core methods: PhD in nonlinear dynamics with statistical mechanics-inspired approaches to cell fate decisions, published work on ODE/PDE models of biological systems (hair cycling, cancer proliferation, HL-60 differentiation), and multiscale multicellular simulation (Biocellion).
- Institutional mechanistic modeling expertise exists but is not yet connected to the imaging AI pipeline work.
- DIPC partnership identified but formal collaboration scope for this module not yet defined.
- Program proposal document drafted (see `REFERENCE/program_Proposal–Theory-infused_Ai.docx`).

## Technical approach

### Three formulation pillars (Phase I groundwork)

1. **Entropy as a measure of feasible latent occupancy.** Use information-theoretic and statistical mechanical measures to quantify the "feasibility" of latent states learned by generative models. This provides principled regularization: latent regions with low biological plausibility (high free energy) are penalized.

2. **Bounding dynamics to learned manifolds.** Constrain ODE/PDE dynamical models to operate on manifolds learned from imaging data. The manifold captures feasible biological states; the dynamics capture mechanistic trajectories through those states. This prevents mechanistic models from predicting biologically impossible states.

3. **Variable-transformed dynamics in learned latent spaces.** Reformulate mechanistic equations in the coordinate system of the learned latent space. This allows classical nonlinear dynamics tools (bifurcation analysis, stability analysis, sensitivity analysis) to operate directly on data-derived representations.

### Integration with existing modules

- **MOD-AI-PIPELINES** provides the foundation model encoders and validated feature extraction. Theory-infused models build *on top of* these representations — the learned latent spaces from foundation models become the substrate for mechanistic dynamics.
- **MOD-IMG-SERVERS** provides governed, versioned, FAIR imaging data. Longitudinal datasets (time-series imaging, repeated acquisitions) are essential for fitting dynamical models.
- **MOD-MULTIMODAL-BIOMARKERS** provides the scientific use cases and PI-anchored validation endpoints. Theory-infused models should produce testable predictions that biomarker projects can validate experimentally.

## 12-24 month deliverables (Phase I)

1. **Initial formulations documented and shared** — mathematical frameworks for all three pillars, with toy/synthetic demonstrations.
2. **One pilot latent-dynamics model on a real dataset** — select a BiomaGUNE imaging dataset with temporal or longitudinal structure; demonstrate that theory-infused constraints improve prediction vs. data-only baselines.
3. **Core team and skills plan** — requirements defined for computational biologists, mathematicians, and computer scientists; joint seminars with microscopy/imaging platforms initiated.
4. **DIPC collaboration scope defined** — formal agreement on compute access and joint supervision/mentoring for theory-infused AI work.
5. **Publication or preprint** — initial formulation paper targeting computational biology or physics-informed ML venue.

## 3-5 year vision (Phase II)

- **Physics-infused generative models** operational on multiple imaging modalities.
- **Multimodal fusion** (microscopy <-> PET/MRI/optical) via constrained latent dynamics.
- **Uncertainty and interpretability by design** — theory-infused models inherently provide mechanistic interpretability and uncertainty from the dynamical structure.
- **Multi-scale integration** — link micro- to meso-/macro-scale imaging signals via constrained latent dynamics; validate against longitudinal imaging data.
- **Translational testbeds** co-developed with internal platforms, CIC bioGUNE, clinical partners, and compute centers.

## 5-10 year vision (Phase III)

- **Unified researcher-facing platform** for constrained latent-dynamics modeling with push-button reproducibility.
- **Federated expansion** interoperating with national ICTS/ReDIB nodes under open-science principles.
- **High-impact use cases** — real-time adaptive imaging, organ- or disease-focused digital twins, open tools adopted beyond biomaGUNE.

## Key personnel credibility

**Ryan Tasseff (operational lead)** — uniquely positioned at the intersection of this module's core demands:

- **Nonlinear dynamics and statistical mechanics:** PhD from Cornell with NSF IGERT Fellowship in Nonlinear Dynamics; dissertation applied statistical mechanics-inspired methods to mammalian cell fate decisions (prostate cancer, leukemia differentiation).
- **ODE/PDE biological modeling:** Published dynamical models of hair cycling (PLoS Comp Biol 2014), HL-60 differentiation (Sci Rep 2017, Integr Biol 2011), prostate cancer signaling (PLoS One 2010), and mathematical models in biotechnology (Elsevier 2011, 2017).
- **Multiscale simulation:** Co-developed Biocellion (accelerated multicellular biological simulation platform); published integrated multiscale multicellular skin model (bioRxiv 2019).
- **AI and imaging:** AI-driven image-based screening and virtual tissue modeling at P&G; current role focused on AI-driven image analysis at biomaGUNE.
- **Clinical genomics:** 2000+ genome analysis for preterm birth (PNAS 2019); experience bridging computational methods to clinical endpoints.

## Guardrails

- **Theory-infused AI is the differentiator, not generic AI.** This module exists because of the mechanistic modeling angle. If a project is pure data-driven ML, it belongs in MOD-AI-PIPELINES. If it's pure biomarker discovery, it belongs in MOD-MULTIMODAL-BIOMARKERS.
- **Start with real formulations and real data, not aspirational whitepapers.** Phase I deliverables require working math and at least one pilot on real imaging data.
- **DIPC partnership must be scoped concretely** — compute access, joint supervision, and collaboration terms before committing in proposals.
- **Do not overcommit on digital twins in Phase I.** Digital-twin applications are Phase II/III; Phase I delivers the theoretical groundwork and one pilot.
- **Maintain composition-over-planning doctrine.** This module composes with real subprojects, not a monolithic AI research program.
