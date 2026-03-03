# Funding Strategy Report: Theory-Infused AI for Biomedical Imaging

**CIC biomaGUNE — March 2026**
**Prepared by:** Ryan Tasseff, Data Officer

---

## 1. Program vision

CIC biomaGUNE is building a multi-year, multi-funder research program called **"Theory-Infused AI for Biomedical Imaging."** The program's central argument is that biomedical imaging — across microscopy, MRI, PET, SPECT, and CT — is generating data at a scale that outpaces current analytical capacity. We address this not with generic AI tooling, but with a distinctive scientific proposition: **unifying generative AI with mechanistic modeling** so that learned representations are constrained by physics and biology, and mechanistic models are empowered by data-driven representations.

The program is structured as a **portfolio of five complementary modules**, each targeting different funder preferences and call types. This portfolio design reduces dependency on any single call, supports staged delivery, and allows us to pursue institutional infrastructure funding and PI-led scientific funding simultaneously.

---

## 2. Why biomaGUNE is the right place

- **Image-centric and multi-scale.** The institute's research spans microscopy (confocal, fluorescence, expanding to whole-slide and high-resolution dynamic imaging) and biomedical imaging (preclinical MRI, CT, PET, SPECT) through the nationally recognized ReDIB/ICTS multi-node network.

- **Deep integration by design.** Track record at the chemistry-biology-materials interface, with a culture of multi-disciplinary collaboration — exactly what theory-infused AI demands.

- **Mechanistic modeling expertise already in-house.** Ongoing molecular dynamics and first-principles projects (atomistic/quantum simulations of plasmonic nanoparticles, protein-nanomaterial interaction modeling). The operational lead has a PhD in nonlinear dynamics with published ODE/PDE biological models, multiscale simulation platforms, and statistical mechanics-inspired approaches to cell fate decisions.

- **DIPC compute partnership.** The Donostia International Physics Center provides theoretical physics depth and significant compute resources (including large-scale GPUs), located in the same city. This is a strategic asset for the computationally intensive theory-infused AI work.

- **The gap we fill.** BiomaGUNE lacks unified AI/ML infrastructure spanning data management, model training, and deployment. The wider computational biology community lacks a general theoretical framework for theory-infused AI that turns biological imaging data into predictive models. This program delivers both.

---

## 3. The two-track funding strategy

All proposals follow a **two-track pattern** designed for maximum flexibility across funder types:

### Track A — Institutional enablement
- **Focus:** Services, compliance, interoperability, adoption metrics
- **Typical calls:** Open science infrastructure, institutional digital transformation, equipment/infrastructure programs
- **Examples:** FAIR data services, imaging repository deployment, AI pipeline factory as shared infrastructure
- **Funder appeal:** Measurable capability building, sustainability plans, service models

### Track B — PI-anchored scientific projects
- **Focus:** Biological/clinical aims led by PIs; platform work packaged as funded work packages; theory-infused modeling as a research program
- **Typical calls:** Health/biomedical research, translational programs, collaborative R&D, AI/modeling research (AEI), GenAI4EU, EuroHPC
- **Examples:** Multimodal biomarker discovery, digital-twin prototypes, theory-infused AI methodology papers
- **Funder appeal:** Scientific novelty, translational potential, publication and impact metrics

**Key rule:** Every Track A deliverable must be proven through at least one Track B anchor project. Infrastructure is never proposed in isolation — it is always validated through real scientific use.

---

## 4. The five modules

Each module is maintained as a "project fiche" — a self-contained description with scope, deliverables, metrics, dependencies, and guardrails. Proposals are assembled by selecting and combining modules to match a specific call's language and priorities.

### Module 1: FAIR Data Practices Enablement (MOD-FAIR-TRAIN)

**What it is:** Institute-wide training and adoption program that makes FAIR (Findable, Accessible, Interoperable, Reusable) practice operational — repeatable data management plans (DMPs), minimum metadata habits, and publication-linked data packaging.

**Current status:** Operational rollout in progress. DMP templates delivered, OA archiving workflow running, RDM workshops with office-hours follow-up model active. Officialization package (Master RDM SOP + DMP SOP + OA archiving SOP) underway.

**Why it matters for funding:**
- Satisfies open science requirements in virtually all EU and Spanish calls
- Reduces downstream friction for imaging servers and AI pipelines
- Provides measurable adoption metrics (training completion, DMP coverage, reuse events) that funders can audit

**Budget class:** Small to medium
**Readiness:** Operational — can be included in proposals now

---

### Module 2: Imaging Data Infrastructure — OMERO + XNAT (MOD-IMG-SERVERS)

**What it is:** Deploy and operationalize complementary imaging repositories — OMERO for microscopy and XNAT for DICOM biomedical imaging — with standardized ingest, minimal metadata profiles, and governed access so data becomes findable, shareable under controls, and analysis-ready.

**Current status:** Design and pilot phase. Two lighthouse pilots are active:
- **gjesus3 pilot** (microscopy): registry model with raw/project/publication tiers, baseline metadata expectations, spec v1.0 and launch plan
- **Nuke pilot** (DICOM): second imaging-RDM workflow generalizing the ingestion and metadata pattern beyond microscopy
- **XNAT server** identified as Q2 2026 bridge from RDM governance to data infrastructure proof-of-concept

**12-24 month deliverables:**
1. Governance defined: identity/access model, lifecycle management, system-of-record for imaging metadata
2. OMERO lighthouse pilot: acquisition → ingest → minimal metadata → access → export for analysis
3. XNAT lighthouse pilot: DICOM ingest → project conventions → access → viewer/export hooks
4. Cross-cutting: connect server datasets to DMPs and publication-linked archiving

**Longer-term (3-5 years):** Federation/interoperability with APIs and controlled sharing; integration with validated AI pipelines; longitudinal and time-series datasets versioned and accessible for dynamical models.

**Budget class:** Medium to large
**Readiness:** Design and pilot — early proposals possible now, full proposals after lighthouse demonstrations

---

### Module 3: Cross-Group AI Pipeline Factory (MOD-AI-PIPELINES)

**What it is:** A pipeline factory that turns research-grade scripts into validated, reproducible, uncertainty-aware analysis services — grounded in open foundation models and stress-tested against real domain shift — usable by multiple groups with full QA and lifecycle management.

**Current status:** Pilot to operational. **SegOid pipeline** is already in a production loop with user-driven pull, retraining requests, and packaging updates. This is a real pipeline with real adoption, not a plan. Institutional demand exists across multiple groups for repeatable analysis (segmentation, denoising, registration, classification).

**Core technical approach — foundation-model-first:**

Each production pipeline follows a three-stage architecture:

1. **Foundation encoder (frozen or lightly adapted).** Open-weight self-supervised models as feature extractors. For histology/microscopy: pathology foundation models (UNI, CONCH, CTransPath). For 3D imaging (preclinical MRI, CT, PET, SPECT): 3DINO-ViT or MST-style 2D-to-3D adaptation.

2. **Task-specific aggregation head.** Attention-based multiple-instance learning (MIL) for whole-slide images; slice-transformers for 3D volumes; linear probes for simpler tasks.

3. **Uncertainty and triage layer.** Deep ensembles or MC-dropout for calibrated confidence; explicit "uncertain case" flagging with defined downstream actions (expert review, repeat acquisition).

**Why foundation-model-first de-risks the program:**
- **Label efficiency** — strongest gains in low-label regimes, directly relevant to preclinical settings with small annotated cohorts
- **Reduced preprocessing burden** — strong SSL encoders can eliminate stain normalization without degrading performance
- **Faster baselines** — freeze-then-probe provides rapid initial results
- **Open weights available now** — UNI, CONCH, 3DINO, and Models Genesis all provide open code/weights, so prototyping can begin immediately on existing biomaGUNE data

**Validation framework (key differentiator for funders):**
- **Domain-shift validation as default** — every pipeline validated against cohorts reflecting real deployment shift (different batch, operator, genotype, staining protocol)
- **Uncertainty-aware triage** — ensemble disagreement scoring, explicit uncertain-case flagging, documented resolution pathways
- **TRIPOD+AI-aligned reporting** — data provenance, evaluation design, appropriate metrics (AUROC, C-index), subject-level splitting, leakage guards
- **Explainability requirements** — attention maps from MIL, Grad-CAM for 3D, concept-based methods where applicable

**12-24 month deliverables:**
1. Production criteria defined (QA, documentation, versioning, uncertainty reporting, domain-shift validation)
2. SegOid fully validated with containerized packaging, held-out benchmarks, uncertainty flagging
3. 1-2 additional pipelines on a second modality (e.g., preclinical MRI classification or histology WSI subtyping)
4. Minimal model registry with model cards and provenance
5. Reference evaluation reports a funder can audit
6. Reusable validation protocol template for PI-anchored projects

**Budget class:** Medium
**Readiness:** Pilot to operational — strong proposal material available now

---

### Module 4: Theory-Infused AI Framework (MOD-THEORY-AI)

**What it is:** The program's core intellectual differentiator. Formalize a framework where generative AI and first-principles biology constrain each other — learned manifolds regularize mechanistic dynamics, and physics/biology constrain learned representations — producing predictive, interpretable models that go beyond descriptive analytics.

**The scientific premise:**

Generative AI has shown that massive, heterogeneous examples can robustly capture reality. Biological mechanistic modeling has struggled with complexity, missing parameters, and limited predictive accuracy. Theory-infused AI bridges these: generative AI informs and constrains mechanistic models, while mechanistic structure regularizes and interprets learned representations. The outcome is models that are **data-powerful yet constrained by physics and biology**.

**Current status:** Concept and early formulation. The operational lead has direct background in the core methods (PhD in nonlinear dynamics, published ODE/PDE biological models, multiscale simulation). Institutional mechanistic modeling expertise exists but is not yet connected to the imaging AI pipeline work. DIPC partnership identified but collaboration scope not yet formalized. Program proposal drafted.

**Three formulation pillars (Phase I groundwork):**

1. **Entropy as a measure of feasible latent occupancy.** Use information-theoretic and statistical mechanical measures to quantify the "feasibility" of latent states learned by generative models. Latent regions with low biological plausibility (high free energy) are penalized — providing principled regularization.

2. **Bounding dynamics to learned manifolds.** Constrain ODE/PDE dynamical models to operate on manifolds learned from imaging data. The manifold captures feasible biological states; the dynamics capture mechanistic trajectories through those states. This prevents mechanistic models from predicting biologically impossible states.

3. **Variable-transformed dynamics in learned latent spaces.** Reformulate mechanistic equations in the coordinate system of the learned latent space. This allows classical nonlinear dynamics tools (bifurcation analysis, stability analysis, sensitivity analysis) to operate directly on data-derived representations.

**How it integrates with other modules:**
- Builds on top of **MOD-AI-PIPELINES** foundation model encoders — the learned latent spaces become the substrate for mechanistic dynamics
- Requires governed, versioned, longitudinal imaging data from **MOD-IMG-SERVERS**
- Produces testable predictions that **MOD-MULTIMODAL-BIOMARKERS** projects validate experimentally

**12-24 month deliverables:**
1. Initial formulations documented (all three pillars) with toy/synthetic demonstrations
2. One pilot latent-dynamics model on a real biomaGUNE dataset with temporal/longitudinal structure
3. Core team requirements defined; joint seminars with imaging platforms initiated
4. DIPC collaboration scope formalized
5. Publication or preprint: initial formulation paper

**3-5 year vision:** Physics-infused generative models on multiple modalities; multimodal fusion via constrained latent dynamics; multi-scale integration (micro- to macro-scale signals); translational testbeds with CIC bioGUNE and clinical partners.

**5-10 year vision:** Unified researcher-facing platform for constrained latent-dynamics modeling; federated expansion with ICTS/ReDIB nodes; high-impact use cases including real-time adaptive imaging and organ-/disease-focused digital twins.

**Budget class:** Medium to large
**Readiness:** Concept to pilot — requires formulations and at least one pilot result before leading large proposals

---

### Module 5: Multimodal AI for Biomarker Discovery & Predictive Imaging (MOD-MULTIMODAL-BIOMARKERS)

**What it is:** The science proof layer. PI-led multimodal projects that use the platform modules and theory framework to generate publishable, validated biomarker insights and predictive imaging applications — from discovery through digital-twin prototypes.

**Current status:** Concept and partnering stage. The DIAP (Data Infrastructure and Analysis Program) defining document is targeted for June 2026. Candidate subprojects are emerging from imaging-RDM pilots and AI pipeline work, but named PI anchors and defined cohorts/datasets are needed before this module leads proposals.

**Two-layer scope:**

**Layer 1 — Biomarker discovery (near-term, 12-24 months):**
- Multimodal fusion of imaging with clinical, omics, or report-derived features
- Classification, prognostic scoring, cohort stratification
- Built on foundation-model-first pipelines from MOD-AI-PIPELINES
- Validated with domain-shift testing and TRIPOD+AI-aligned reporting

**Layer 2 — Predictive imaging and digital twins (medium-term, 3-5+ years):**
- Digital-twin workflows for adaptive acquisition (models that predict optimal next-scan parameters in real time)
- Individualized predictions in preclinical settings (trajectory forecasting using constrained latent dynamics)
- Decision support in live imaging experiments
- Multimodal fusion via constrained latent dynamics (shared mechanistic latent spaces)

**12-24 month deliverables:**
1. 1-2 anchor questions with defined modalities, cohorts, and PI anchors
2. Platform modules implemented as funded work packages
3. At least one publishable result plus reusable datasets under controlled access
4. Requirements document for Layer 2 digital-twin applications

**Budget class:** Medium to large
**Readiness:** Concept and partnering — requires PI anchors before leading proposals

---

## 5. Phased delivery roadmap

### Phase 0 (now — 3 months): Packaging and alignment — UNDERWAY

What's already done or in progress:
- Two lighthouse pilots active (gjesus3 microscopy, Nuke DICOM)
- Grant-fit matrix and weekly Friday triage routine operational
- DMP kit, OA archiving workflow, officialization package in progress
- SegOid pipeline in user-driven iteration
- Funding positioning dossier bootstrapped
- Program proposal drafted

Remaining:
- Finalize v1.0 of all five module fiches
- Agree governance/RACI and service boundaries (draft exists, needs steering group sign-off)
- DIAP defining document (targeted June 2026)
- Scope DIPC compute partnership

### Phase I (3-24 months): Foundations

- Training curriculum and onboarding paths for labs
- OMERO and XNAT lighthouse workflows demonstrated end-to-end
- SegOid formalized as first production pipeline with full validation
- Foundation-model-first architecture established with open encoders
- Theory-infused AI initial formulations documented; one pilot on real data
- Core team and DIPC collaboration scoped
- 1-2 PI-anchored biomarker questions defined with cohorts

### Phase II (2-5 years): Methods and translational collaborations

- Physics-infused generative models on multiple imaging modalities
- Multimodal fusion via constrained latent dynamics
- Multi-scale integration validated against longitudinal imaging
- 2-3 production AI pipelines with full validation suites
- Digital-twin prototype(s) on preclinical use cases
- Translational testbeds with CIC bioGUNE and clinical partners

### Phase III (5-10 years): Unified platforms and impact at scale

- Researcher-facing platform for constrained latent-dynamics modeling
- Federated expansion with ICTS/ReDIB nodes
- Real-time adaptive imaging, organ-/disease-focused digital twins
- Open tools adopted beyond biomaGUNE
- Follow-on funding driven by scientific results

---

## 6. Key milestones

| # | Milestone | Phase |
|---|---|---|
| M1 | All five module fiches finalized (v1.0) | 0 |
| M2 | OMERO lighthouse end-to-end demonstration | I |
| M3 | XNAT lighthouse end-to-end demonstration | I |
| M4 | First cross-group AI pipeline in production with domain-shift validation and uncertainty-aware triage | I |
| M5 | Adoption metrics reported (labs, datasets, reuse signals) | I |
| M6 | Theory-infused AI initial formulations published; pilot model on real data | I |
| M7 | DIPC collaboration formally scoped and operational | I |
| M8 | First PI-anchored biomarker result published | II |
| M9 | Digital-twin prototype demonstrated on preclinical use case | II |
| M10 | Unified theory-AI platform available to internal users | III |

---

## 7. Funding alignment by geography

### Basque Country (RIS3 / BRTA)

Serves Bio-Health and Advanced Manufacturing/Nanotech priorities with a strong digitalization layer — FAIR imaging data, generative-AI analytics, and translational tools for nanomedicine. Natural fit for **Elkartek** (collaborative R&D) and **Hazitek** (industry-academic consortia). Creates local software/data value chains.

**Best-fit modules:** MOD-AI-PIPELINES, MOD-IMG-SERVERS, MOD-FAIR-TRAIN (Track A institutional), MOD-MULTIMODAL-BIOMARKERS (Track B with local PI anchors)

### Spain (ICTS / AEI / ISCIII)

Upgrades analysis capability on ICTS-linked imaging infrastructure (ReDIB node), aligning with national goals in AI, personalized medicine, and research modernization.

- **AEI (Agencia Estatal de Investigacion):** Funds AI/modeling research — ideal for MOD-THEORY-AI and MOD-AI-PIPELINES methodology papers
- **ISCIII (Instituto de Salud Carlos III):** Funds biomedical data and translational health — ideal for MOD-MULTIMODAL-BIOMARKERS
- **ICTS calls:** Infrastructure co-funding for MOD-IMG-SERVERS

**Best-fit modules:** MOD-THEORY-AI (AEI), MOD-MULTIMODAL-BIOMARKERS (ISCIII), MOD-IMG-SERVERS (ICTS)

### Europe (Horizon / GenAI4EU / EOSC / EuroHPC)

Maps to Horizon Europe Health & Digital pillars (multimodal data, trustworthy AI, digital twins) and GenAI4EU opportunities. Commits to EOSC-style openness. Can leverage EuroHPC at scale for theory-infused AI computation.

- **Horizon Europe Cluster 1 (Health):** Multimodal biomarkers, digital twins, translational imaging
- **Horizon Europe Digital/AI:** Trustworthy AI, foundation models, physics-informed ML
- **GenAI4EU:** Generative AI applications in health/science
- **EuroHPC:** Compute access for large-scale theory-infused AI training
- **EOSC:** Open science and FAIR data infrastructure

**Best-fit modules:** All five (combined), with MOD-THEORY-AI and MOD-MULTIMODAL-BIOMARKERS as scientific differentiators

---

## 8. How proposals get built (packaging rules)

The program uses a repeatable proposal-building method:

1. **Stable umbrella narrative.** The program brief ("Theory-Infused AI for Biomedical Imaging") remains consistent across all proposals, adapted in emphasis but not reinvented.

2. **Module fiches as source of truth.** Each of the five modules has a maintained project fiche with scope, deliverables, metrics, and guardrails. Proposal work packages map directly to module IDs.

3. **Call-specific concept notes.** For each opportunity, a 1-2 page concept note is written that:
   - Maps the call's language and priorities to specific module IDs
   - States the eligibility lead and partner needs
   - Selects metrics and deliverables appropriate for the call's scale and timeline
   - Specifies Track A, Track B, or a combination

4. **Grant-fit matrix.** A living tracker where each opportunity is scored for fit against the modules, assigned a readiness level (idea → partners → draft → ready), and tracked through to submission.

5. **Sustainability section in every proposal.** Even when modest: service/access policy and support model, maintenance plan and staffing fractions, cost model (internal allocation / recharge / institute commitment).

---

## 9. Metrics that build funder trust

| Category | Metrics |
|---|---|
| **Adoption** | Labs onboarded, training completion rates, DMP coverage |
| **Infrastructure** | Datasets ingested, TB served, onboarding time, uptime |
| **Reuse** | Internal reuse events, # analyses run |
| **AI pipelines** | Validated performance reports, domain-shift test results, uncertain-case rates and resolution, reproducibility artifacts |
| **Theory-AI** | Formulations published, pilot models on real data, predictive improvement over data-only baselines |
| **Science** | Publications, biomarker claims validated, digital-twin demonstrations |
| **Partnerships** | DIPC collaboration scoped, external co-development testbeds, consortium grants awarded |

---

## 10. Execution doctrine

The program operates with a deliberate execution philosophy that funders can audit and PIs can rely on:

- **Option creation, then follow pull.** Build small, demonstrable capabilities; expand only when real users pull for more. This prevents over-investment in unused infrastructure.

- **Strict WIP discipline.** One execution wedge at a time per track. Finish and demonstrate before starting the next increment.

- **Lighthouse-first.** Every capability is proven through a named pilot before being generalized. No institute-wide rollouts without demonstrated adoption.

- **Composition over top-down planning.** The program (especially the science layer) is composed from real subprojects, not pitched as a monolithic initiative.

This doctrine is already operational: the current workflow separates institutional enablement from PI-anchored pilots, limits work-in-progress, and sequences delivery around demonstrated demand.

---

## 11. Key personnel

**Ryan Tasseff, Ph.D. — Program Operational Lead**

Current Data Officer at CIC biomaGUNE. PhD in Chemical and Biomolecular Engineering from Cornell University (NSF IGERT Fellow in Nonlinear Dynamics). 30+ publications (PNAS, PLoS Comp Bio, Sci Rep), US patent.

Career spans:
- **Academic research:** Systems biology, computational modeling, clinical genomics (2000+ genomes, PNAS 2019), ODE/PDE biological modeling (hair cycling, cancer signaling, cell differentiation), multiscale simulation (Biocellion platform, integrated skin model)
- **Industry leadership:** P&G Group Head ($1M+ budget), AI-driven image analysis, virtual tissue modeling, patented oral care technologies
- **Executive roles:** CSO at Biocellion SPC, entrepreneurial track record (3 ventures)
- **Current role:** ReDIB/ICTS imaging network management, institutional FAIR data strategy, AI-driven image analysis program, operational funding scouting system

Uniquely positioned at the intersection of mechanistic modeling (the core competency for theory-infused AI), production AI pipeline management, and institutional data strategy.

**Additional personnel:** To be added as the team grows. Module fiches specify the skills needed (computational biologists, mathematicians, computer scientists).

---

## 12. Dependencies and risks

### Dependencies
- Governance decisions (identity/access model; system of record for metadata)
- IT collaboration for hosting, backups, and reliability
- PI buy-in for adoption (named data contact per lab/project)
- Minimal sustainability line item for sysadmin and maintenance
- DIPC partnership formalization (compute access, joint supervision)
- Core team assembly (computational biologists, mathematicians, computer scientists)

### Primary risks and mitigations

| Risk | Mitigation |
|---|---|
| **Overreach** (trying to build everything at once) | Explicit non-goals, phased delivery, service boundaries, strict WIP discipline |
| **Low adoption** (infrastructure nobody uses) | Lighthouse pilots and PI anchors before scaling; follow pull, not push |
| **Infrastructure without outcomes** | End-to-end demonstrations with metrics; Track B anchors prove Track A value |
| **Theory-AI too abstract** (unfundable whitepaper) | Pilot-on-real-data requirement in Phase I; no proposals without working formulations |
| **DIPC dependency** | Scoped collaboration terms before committing in proposals; maintain institutional compute baseline |
| **Digital twin overpromise** | Preclinical only in Phase II; no clinical claims without regulatory/ethical groundwork |

### Guardrails (what we will NOT do)
- Avoid "infinite platform" framing — fund the next implementable increment
- Prefer measurable deliverables to aspirational language
- Do not promise clinical digital twins before preclinical validation
- Theory-infused AI proposals must include working formulations and real-data pilots
- No institute-wide enforcement until lighthouse pilots demonstrate adoption
- Do not lead MOD-MULTIMODAL-BIOMARKERS proposals until PI anchors are named

---

## 13. What we need from PIs

This program is designed to **serve and amplify PI-led science**, not to compete with it. The platform (FAIR data, imaging servers, AI pipelines, theory-infused models) becomes infrastructure that PIs access through their own projects. What we need from interested PIs:

1. **Named anchor projects.** A concrete scientific question with defined imaging modalities, cohorts, and endpoints. This is what makes Track B proposals credible.

2. **Data access.** Willingness to onboard imaging data into the governed platform (OMERO/XNAT) and work with standardized metadata and access controls.

3. **Domain expertise for validation.** AI pipeline validation requires expert-annotated ground truth and domain knowledge to define what "correct" looks like. This cannot come from the platform team alone.

4. **Co-authorship on methodology.** When the platform produces validated pipelines or theory-infused models relevant to a PI's domain, joint publications strengthen both the scientific and the funding case.

5. **Feedback on what to build next.** The execution doctrine follows user pull. PI demand is the signal that determines which capabilities get expanded.

---

*This report is based on the funding positioning dossier maintained at CIC biomaGUNE. Module fiches, evidence bank, team profiles, and the grant-fit matrix are available on request for detailed proposal development.*
