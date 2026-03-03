# MOD-AI-PIPELINES — Cross-Group AI Pipeline Factory (Production Workflows)

```yaml
module_id: MOD-AI-PIPELINES
module_name: Cross-Group AI Pipeline Factory (Foundation-Model-First, Validated, Uncertainty-Aware)
track_type: both
time_horizon: 24_months_initial, 5_years_full
readiness_level: pilot_to_operational
eligible_lead_types: [institution, PI_as_anchor, consortium]
best_fit_geographies: [Basque, Spain, EU]
budget_class: medium
keywords:
  - foundation models, self-supervised learning, vision transformers
  - segmentation, denoising, registration, classification
  - multiple-instance learning (MIL), weak supervision
  - uncertainty quantification, calibration, triage workflows
  - reproducibility, validation, benchmarking, domain-shift testing
  - model registry, QA/QC, containerization, GPU scheduling
  - explainability, attention maps, saliency evaluation
  - FAIR-aligned model lifecycle
core_assets:
  - SegOid pipeline — active production loop with user pull and retraining cycle
  - institutional imaging across microscopy (OMERO-bound) and DICOM modalities (XNAT-bound)
  - ReDIB/ICTS multi-node biomedical imaging network (nationally recognized infrastructure)
  - open-access foundation model ecosystem (UNI, CONCH, 3DINO, MST — see Technical approach)
dependencies:
  - imaging server substrate for data access/versioning (MOD-IMG-SERVERS)
  - reference datasets + annotations for validation (internal + public benchmarks)
  - compute allocation (GPU) and packaging standards
  - PI anchor projects providing labeled cohorts and domain endpoints (MOD-MULTIMODAL-BIOMARKERS)
success_metrics:
  - "# pipelines validated and in production use by multiple groups"
  - "external-shift validation reports per pipeline (domain-shift cohort testing)"
  - "# analyses run, turnaround time, and user-reported satisfaction"
  - reproducibility artifacts (containers, configs, versioning, QA checklists)
  - uncertainty-flagged case rate and downstream resolution pathway documented
  - "publications or preprints with TRIPOD+AI-aligned reporting"
last_updated: 2026-03-03
```

## One-sentence positioning

Establish a pipeline factory that turns research-grade scripts into validated, reproducible, uncertainty-aware analysis services — grounded in open foundation models and stress-tested against real domain shift — usable by multiple groups with full QA and lifecycle management.

## Current state

- **SegOid pipeline** already in a production-ish loop: user-driven pull, retraining requests, packaging update cycle. This is the first portfolio story — a real pipeline with real adoption, not a plan.
- Institutional demand exists across multiple groups for repeatable analysis (segmentation, denoising, registration, classification).
- BiomaGUNE imaging spans microscopy (fluorescence, confocal, electron) and biomedical DICOM modalities (preclinical MRI, CT, PET, SPECT) through ReDIB/ICTS, providing a diverse substrate for pipeline development.
- Execution doctrine: option creation then follow user pull, strict WIP discipline, one execution wedge at a time.

## Technical approach — foundation-model-first pipeline design

The core architectural decision is to start from the strongest available open pretrained encoders rather than training from scratch, following the dominant pattern in both computational pathology and 3D medical imaging (see deep-research evidence base below).

### Pipeline architecture pattern

Each production pipeline follows a three-stage design:

1. **Foundation encoder (frozen or lightly adapted).** Use open-weight self-supervised models as feature extractors. For histology/microscopy: pathology foundation models (UNI, CONCH, CTransPath). For 3D imaging (preclinical MRI, CT, PET, SPECT): 3DINO-ViT or MST-style 2D-to-3D adaptation with DINOv2 backbones.

2. **Task-specific aggregation head.** For whole-slide or large-field-of-view images: attention-based multiple-instance learning (MIL) providing built-in interpretability via tile/instance scoring. For 3D volumes: slice-transformer or volume-level classification heads. For simpler tasks: linear probe or lightweight fine-tuning.

3. **Uncertainty and triage layer.** Rather than forcing single-label decisions, implement uncertainty-aware outputs: deep ensembles or MC-dropout for calibrated confidence; high-sensitivity vs. high-specificity ensemble disagreement for explicit "uncertain case" flagging; downstream routing of uncertain samples to expert review, additional assay, or repeat acquisition.

### Why foundation-model-first de-risks the program

- **Label efficiency:** SSL-pretrained encoders show strongest gains in low-label regimes, directly relevant to preclinical settings where annotated cohorts are small.
- **Reduced preprocessing burden:** Evidence shows that strong SSL feature extractors can eliminate the need for stain normalization and some augmentations without degrading slide-level performance, reducing compute and instability.
- **Faster baselines:** Freeze-then-probe provides rapid initial results; end-to-end fine-tuning is only pursued when sufficient labeled data and robust external validation are in place.
- **Open weights available now:** UNI, CONCH, TITAN, CTransPath, 3DINO, and Models Genesis all provide open code/weights, meaning pipeline prototyping can begin immediately on existing BiomaGUNE data.

### Applicable open foundation models and datasets

| Model / resource | Domain | Typical use in our pipelines |
|---|---|---|
| UNI | Histopathology (SSL ViT) | Frozen encoder for microscopy tile features |
| CONCH | Histopathology + text (vision-language) | Zero/few-shot classification; retrieval |
| CTransPath | Histopathology (hybrid CNN-Transformer) | Alternative patch encoder for MIL |
| 3DINO-ViT | 3D medical imaging (CT/MRI) | Frozen or fine-tuned encoder for preclinical 3D tasks |
| MST | 3D imaging via 2D slices | Slice-transformer for MRI/CT classification |
| Models Genesis | 3D CT (restoration-based SSL) | Initialization for low-label 3D CNN tasks |
| RadImageNet | Radiology (CNN backbones) | Transfer learning alternative to ImageNet |

Public benchmark datasets (CAMELYON16, TCGA/TCIA collections, LIDC-IDRI, BraTS, preclinical mouse µCT databases) serve as validation and benchmarking references during development.

## Validation and QA framework

Validation design is the primary differentiator between a fundable AI pipeline program and generic method development. This module adopts a structured validation hierarchy aligned with translational best practices.

### Domain-shift validation as default

Every pipeline must be validated against cohorts that reflect the real deployment shift. In preclinical work, the analog of "external hospital" is a different experimental batch:
- Different animal cohort, day, operator, or genotype
- Different tracer batch or scanner calibration period
- Different staining protocol or microscopy acquisition settings

Template: emulate the murine CHD µCT study's "prospective" and "divergent" cohort stress tests — train on one batch, evaluate on held-out batches, explicitly quantify and report performance degradation.

### Uncertainty-aware triage design

Pipelines supporting screening or classification endpoints implement:
- Ensemble disagreement or MC-dropout confidence scoring
- Explicit "uncertain" flag with defined downstream action (expert review, repeat scan, additional stain)
- Reporting of uncertain-case rate and resolution outcomes as a production metric

### Reporting standards

All pipeline validation reports align with TRIPOD+AI guidance:
- Document data provenance, participant/sample flow, and evaluation design
- Report AUROC, sensitivity/specificity for diagnostic endpoints
- Report C-index and time-dependent AUC for prognostic/survival endpoints
- Split at the subject/animal level for longitudinal data (all timepoints per subject stay together)
- Guard against leakage via site-stratified or batch-stratified splits

### Preprocessing as hypothesis

Preprocessing choices (stain normalization, augmentation, intensity windowing, voxel resampling) are treated as testable hypotheses, not rituals:
- Benchmark "with vs. without" stain normalization under the chosen foundation encoder
- Use robustness-oriented augmentation (e.g., strong blur/noise for SPECT) only with explicit external-shift evaluation
- Prefer data-driven or domain-grounded augmentations when augmentation is needed

### Explainability requirements

- Attention-MIL pipelines produce tile-level attention maps as native interpretability
- 3D pipelines include saliency map generation (Grad-CAM or equivalent) with qualitative expert review as an evaluation endpoint
- Concept-based methods (TCAV) considered for hypothesis-driven validation where human-defined concepts are available

## 12-24 month deliverables

1. **Pipeline production criteria defined:** acceptance criteria for "production" status covering QA, documentation, versioning, uncertainty reporting, and domain-shift validation.
2. **SegOid pipeline fully validated:** formalized with containerized packaging, performance benchmarks on held-out batches, uncertainty flagging, and reproducibility artifacts. Published as the reusable "pipeline factory" template.
3. **1-2 additional pipelines delivered end-to-end:** leveraging foundation-model-first architecture on a second imaging modality (e.g., preclinical MRI classification or histology WSI subtyping), with freeze-probe baselines and domain-shift validation reports.
4. **Minimal model registry / versioning:** model cards, version tracking, and provenance documentation for all deployed models.
5. **Reference evaluation reports:** benchmark results on internal + public datasets that a funder can audit, following TRIPOD+AI-aligned reporting.
6. **Validation protocol template:** reusable template for domain-shift validation applicable to future pipelines and PI-anchored projects.

## Key personnel credibility

**Ryan Tasseff (operational lead)** brings direct, demonstrated experience across the module's core demands:

- **AI-driven image analysis:** Developed AI-driven image-based strategies for molecule screening and applied ML to biomedical imaging at P&G, including high-throughput cellular imaging and organotypic tissue models.
- **Computational biology and multiscale modeling:** 30+ publications including integrated multiscale multicellular skin modeling (bioRxiv 2019), hair cycle dynamics (PLoS Comp Biol 2014), and cancer cell fate modeling (PLoS One 2010). Published mathematical models of biological systems at ISB and Cornell.
- **Production pipeline management:** Managed $1M+ annual budgets and cross-disciplinary teams at P&G; current operational management of ReDIB/ICTS multi-node imaging network at biomaGUNE.
- **Validation and clinical translation:** Led preclinical and clinical trials including human POC clinical studies (patented oral care compositions); experience with clinical genomics on 2000+ genomes (preterm birth, PNAS 2019).
- **Reproducibility and open science:** Published computational tools (PyCoTools, Biocellion), experience with simulation platforms, and current institutional role focused on FAIR data infrastructure.

PhD Chemical & Biomolecular Engineering (Cornell, NSF IGERT Fellow); BS Chemical Engineering (University of Florida, Magna Cum Laude).

## IP and freedom-to-operate awareness

The patent landscape in computational pathology and medical imaging AI is active and industry-driven (6,284 patents identified in a recent systematic evaluation). Common architectural components — including attention-based MIL for whole-slide images and biomarker inference methods — are actively claimed by industry players.

**Guardrail for this module:**
- All pipeline development uses open-weight, open-code foundation models with documented licenses.
- Before any translational or commercial deployment, conduct a freedom-to-operate review for the specific pipeline architecture and intended use.
- Internal research use at biomaGUNE carries lower IP risk but consortium and industry-collaboration proposals must include an explicit IP awareness section.
- Maintain awareness of the open-source vs. proprietary split: open weights do not guarantee freedom to operate.

## Module guardrails

- Keep scoped to **validated service delivery**, not open-ended AI research. Scientific discovery belongs in MOD-MULTIMODAL-BIOMARKERS; theory-infused modeling belongs in MOD-THEORY-AI; this module provides the production machinery that both build upon.
- Foundation models are tools, not goals. Avoid "foundation model for its own sake" framing; every model choice must map to a concrete pipeline need and user demand.
- No institute-wide rollout without demonstrated adoption through lighthouse pilots.
- Uncertainty and validation are not optional add-ons; they are core deliverables.
