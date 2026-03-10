# Funding Strategy Timeline — Image Data Infrastructure & AI

**CIC biomaGUNE | March 2026**
**Prepared by:** Ryan Tasseff

---

## Summary

This report maps our program to a phased funding strategy with specific grant targets and deadlines. The program has two phases:

1. **Groundwork (2026-2027):** Relieve the current compliance burden, build imaging data infrastructure, and deploy validated AI analysis pipelines on top of it.
2. **Science program (2027+):** Use the groundwork to pursue theory-infused AI research and multimodal biomarker discovery through larger, longer-term grants.

The groundwork is prerequisite to the science. Without governed imaging repositories and production AI pipelines, the scientific proposals lack a credible platform story.

---

## Phase 1: Groundwork

### 1A. FAIR compliance and data stewardship

**The problem:** Open access archiving, data management plans, and metadata compliance currently consume a disproportionate share of the Data Officer's time. This is necessary work, but it is not scalable and it blocks progress on the higher-value infrastructure and AI work.

**What we need:**
- A dedicated data steward (or equivalent) to own day-to-day FAIR compliance, DMP support, OA archiving, and researcher training
- Formalized SOPs and onboarding materials so compliance work becomes routine rather than bespoke

**Grants that fund this:**

| Grant | Funder | Budget available | Deadline | Key requirements |
|-------|--------|-----------------|----------|-----------------|
| **EOSC FAIR Data Uptake** (INFRAEOSC-2026-01-01) | EU / Horizon Europe | ~40M EUR (1 project) | 2026-06-16 | Large consortium; biomaGUNE as participant, not lead. Could fund a local data steward as part of FAIR adoption work package. Info Day 2026-03-18. |
| **AEI Research Networks** (RED2026) | AEI (Spain) | Small (networking) | 2026-06-10 to 2026-07-01 | Low funding but strategic: build a FAIR imaging data network across Spanish centers. Positions us for larger follow-on calls. |
| **BERC/CIC 2026-2029 Framework** | Basque Government | 80M EUR across all CICs (4 years) | Not competitive (baseline) | Existing institutional funding. Internal argument for a data steward position within the current framework allocation. Most direct path to immediate hiring. |

**Note on personnel funding:** Most infrastructure and research grants (AEI PID, Elkartek, EOSC) allow personnel costs as budget items. A data steward can be embedded as a line item in any of the larger grants listed below. The question is which grant arrives first and whether institutional baseline funding can bridge the gap.

---

### 1B. Imaging data infrastructure (OMERO + XNAT + storage)

**The problem:** After current proof-of-concept pilots are complete (microscopy RDM, DICOM workflows), we need production servers: OMERO for microscopy data and XNAT for biomedical imaging (MRI, PET, CT, SPECT). This means server hardware, storage arrays, and possibly GPU compute nodes.

**What we need:**
- Server hardware and storage for OMERO and XNAT deployments
- Network and backup infrastructure
- Sysadmin time (can be shared with data steward or IT)

**Grants that fund this:**

| Grant | Funder | Budget available | Deadline | Key requirements |
|-------|--------|-----------------|----------|-----------------|
| **Azpitek 2026** | Basque Gov / SPRI | 9M EUR total; avg ~750K/project | **2026-03-27 (18 days)** | Up to 100% funding for non-economic activity. CIC eligibility confirmed. Need vendor quotes and equipment specs. Most immediate opportunity. |
| **AEI Scientific Equipment** (EQC2026) | AEI (Spain) | ~170M EUR | ~2026-09 to 2026-10 | National equipment call. Imaging servers, storage, GPU compute. Need vendor quotes by summer. |
| **INKER 2027** | Basque Gov / Dept. Science | ~4M EUR | ~2027-01 (expect short window) | 90% funding for equipment 100K-1M EUR. CICs eligible. Missed 2026 cycle; prepare specs and quotes by Nov 2026. |
| **EOSC FAIR Data Uptake** (same as above) | EU / Horizon Europe | ~40M EUR | 2026-06-16 | Infrastructure component within a larger FAIR adoption consortium. |

---

### 1C. AI analysis pipelines (segmentation, classification, etc.)

**The problem:** Once imaging data is in governed repositories, we need validated analysis pipelines running on top — segmentation, denoising, registration, classification — as shared services rather than one-off scripts. We already have a working prototype (SegOid) and need to formalize and expand.

**What we need:**
- GPU compute for model training and inference
- Personnel (computational scientist / ML engineer)
- Production infrastructure (model registry, containerization, QA)

**Grants that fund this:**

| Grant | Funder | Budget available | Deadline | Key requirements |
|-------|--------|-----------------|----------|-----------------|
| **AEI AI Research Projects** (AIA2026) | AEI (Spain) | ~31M EUR | ~2026-05 (expected) | Dedicated AI call. **Requires multi-institution consortium** — begin assembly with DIPC, UPV/EHU, Tecnalia now. |
| **AEI Generacion de Conocimiento** (PID2026) | AEI (Spain) | ~700M EUR | 2026-11-03 to 2026-11-24 | Spain's flagship research call. AI pipeline methodology + validation as a fundable project. Can include personnel and equipment. |
| **Elkartek 2027** | Basque Gov / SPRI | ~47M EUR | ~2027-03 | Collaborative research for RVCTI entities. AI + biotech are named strategic areas. **Requires 3+ partners, min 1M EUR.** Begin partner outreach Oct 2026. |
| **EuroHPC Development Access** | EuroHPC JU | Free compute | Rolling (monthly) | No funding, but free GPU/HPC access for code development. Low barrier — apply anytime. |
| **Azpitek 2026** (same as above) | Basque Gov / SPRI | 9M EUR | **2026-03-27** | Can fund GPU compute hardware alongside imaging servers. |
| **AEI Scientific Equipment** (same as above) | AEI (Spain) | ~170M EUR | ~2026-09 | GPU compute nodes as scientific equipment. |

---

### Groundwork timeline summary

```
Mar 2026  ██ Azpitek 2026 — submit equipment application (servers + GPU)
          ██ EOSC Info Day (Mar 18) — identify consortium to join
Apr 2026     Internal: make case for data steward via BERC/CIC baseline
May 2026     ██ AEI AIA2026 — submit AI consortium proposal (if call opens)
Jun 2026     ██ EOSC FAIR Data Uptake — submit as consortium participant
          ██ AEI Research Networks — submit FAIR imaging network proposal
Jul 2026     Collect vendor quotes for AEI EQC and INKER 2027
Sep 2026     ██ AEI Scientific Equipment (EQC2026) — submit
Nov 2026     ██ AEI PID2026 — submit AI pipeline methodology project
          Begin Elkartek 2027 partner outreach
Jan 2027     ██ INKER 2027 — submit equipment application
Mar 2027     ██ Elkartek 2027 — submit collaborative AI + imaging project
```

---

## Phase 2: Science Program (2027+)

Once groundwork infrastructure is in place — FAIR practices operational, imaging repositories deployed, AI pipelines validated — we pursue the longer-term scientific ambitions: theory-infused AI (bridging generative AI with mechanistic modeling) and multimodal biomarker discovery.

### 2A. Theory-infused AI and key personnel

**What this is:** Physics-informed ML, neural ODEs, latent-dynamics models constrained by biology — the program's intellectual differentiator. Requires a core team (computational biologists, mathematicians) and compute partnership with DIPC.

**Grants that fund this:**

| Grant | Funder | Budget available | Deadline | Key requirements |
|-------|--------|-----------------|----------|-----------------|
| **MSCA Postdoctoral Fellowships 2026** | EU / MSCA | ~180K EUR (2 years, individual) | 2026-09-09 | Recruit a theory-AI postdoc. biomaGUNE as host. Requires identifying a candidate by summer 2026. |
| **AEI ATRAE 2026** | AEI (Spain) | Competitive salary package | 2026-04-23 to 2026-06-04 | Attract a senior international researcher. Begin candidate search now. |
| **AEI Ramon y Cajal 2026** | AEI (Spain) | 240M EUR total (doubled budget) | Opens 2026-11-10 | 5-year senior researcher with stabilization track. CICs eligible. |
| **Ikerbasque Research Fellows 2027** | Ikerbasque | ~46K EUR/year, 5 years | ~2027-03 | 5-year postdoc with PI track. Missed 2026 cycle — prepare host letter and candidate profile by Dec 2026. |
| **ERC Advanced Grant 2026** | ERC | Up to 2.5M EUR (5 years) | 2026-08-27 | Frontier research. **Requires exceptional senior PI profile.** Best if a PI with strong publication record leads. |
| **GenAI4EU Booster** | EU / Horizon Europe CL4 | ~30M EUR | 2026-04-15 | Generative AI for health. Strong fit but **37 days to deadline** — only viable if a consortium is already forming. |
| **RAISE AI in Science** | EU / Horizon Europe CL4 | ~15M EUR | 2026-04-15 | Physics-informed ML, neural ODEs. Same tight deadline constraint. |
| **AEI PID2026** (also listed above) | AEI (Spain) | ~700M EUR | 2026-11 | Theory-infused AI methodology as a fundable research project. |
| **Elkartek 2027** (also listed above) | Basque Gov / SPRI | ~47M EUR | ~2027-03 | "Hybrid modeling and learning" and "physics-based multimodal models" are explicitly named priorities. |

### 2B. Multimodal biomarker discovery and predictive imaging

**What this is:** PI-led projects that combine imaging modalities (microscopy + MRI/PET/CT) with clinical or omics data to discover and validate biomarkers. Longer-term: digital-twin prototypes for adaptive imaging.

**Grants that fund this:**

| Grant | Funder | Budget available | Deadline | Key requirements |
|-------|--------|-----------------|----------|-----------------|
| **Horizon 2027 — AI Biomarkers** (HLTH-2027-02-TOOL-01) | EU / Horizon Europe CL1 | Typical 6-10M EUR | Stage 1: 2027-04-13 | AI-driven predictive biomarkers with multimodal data. Two-stage. **Requires consortium with clinical partners and independent validation cohorts.** Begin planning in 2026. |
| **AEI Public-Private Collaboration** (CPP2026) | AEI (Spain) | Competitive | 2027-01-12 to 2027-02-02 | Collaborative R&D. **Requires industry partner as co-lead.** |
| **CDTI Misiones 2026** | CDTI (Spain) | 60M EUR | 2026-05-29 to 2026-07-01 | Strategic R&D missions. **Company must lead; biomaGUNE as research partner only.** |
| **ISCIII PI Salud (AES 2027)** | ISCIII (Spain) | ~150M+ EUR | ~2027-03 | Health research projects. **Requires clinical PI or collaborator.** Missed 2026 deadline. |
| **Hazitek 2026 (2nd call)** | Basque Gov / SPRI | 26M EUR (transformative) | ~2026-06 to 2026-07 | Large industry-led R&D. **Company must lead; min. 20M EUR.** CIC as research partner. |

---

### Science program timeline summary

```
Apr 2026  ██ AEI ATRAE — identify and contact senior theory-AI candidate
          (GenAI4EU / RAISE deadlines — only if consortium already forming)
Aug 2026     ██ ERC Advanced Grant — submit if senior PI available
Sep 2026     ██ MSCA Postdoctoral Fellowship — submit theory-AI postdoc application
Nov 2026     ██ AEI PID2026 — submit theory-AI methodology project
          ██ AEI Ramon y Cajal — submit senior researcher recruitment
          Prepare Ikerbasque RF 2027 candidate profile + host letter
2027-Q1      ██ Elkartek 2027 — submit with theory-AI + imaging consortium
          ██ Ikerbasque RF 2027 — submit
2027-Q2      ██ Horizon AI Biomarkers — submit Stage 1 with clinical consortium
          ██ ISCIII AES 2027 — submit with clinical collaborator
```

---

## Key dependencies and risks

- **Data steward hiring is the bottleneck.** Until compliance work is off the Data Officer's plate, bandwidth for infrastructure and AI work remains constrained. The BERC/CIC baseline is the fastest path; grant-funded positions take 6-12 months.
- **Azpitek 2026 deadline is 18 days away.** This is the most immediate actionable opportunity for imaging infrastructure. Needs vendor quotes and equipment specs now.
- **Consortium formation takes time.** AEI AIA2026, Elkartek 2027, and Horizon 2027 AI Biomarkers all require multi-partner proposals. Partner outreach should start months before deadlines.
- **Theory-AI team assembly is critical path for Phase 2.** Without hiring computational researchers (via MSCA, ATRAE, Ramon y Cajal, or Ikerbasque RF), the theory-infused AI work cannot progress beyond early formulations.

---

## Baseline funding context

CIC biomaGUNE receives institutional funding through the **BERC/CIC 2026-2029 framework** (80M EUR across all CICs over 4 years, approved Nov 2025). This provides baseline operations and can be cited as co-financing in grant proposals. It does not, by itself, fund new infrastructure or dedicated personnel for this program.

---

*Based on grant scans completed 2026-03-06 (Basque) and 2026-03-09 (full: EU, Spain, Basque). Detailed call evaluations in `SCANS/`. Module descriptions and program details available in the project dossier.*
