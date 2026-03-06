# Grant Scanner Report — 2026-03-06

**Scan scope:** Basque Country
**Calls found:** 8 total | **Passed evaluation:** 2 included

---

## High Confidence

### Elkartek 2026 — Collaborative Research Programme
- **Funder:** Basque Government / Dept. of Industry, Energy Transition and Sustainability
- **Source:** SPRI Elkartek
- **Deadline:** 2026-03-13 (7d remaining)
- **Status:** open
- **URL:** https://www.spri.eus/es/ayudas/elkartek/
- **Budget:** €47M total (€23M for 2026, €24M for 2027)
- **Summary:** Funds collaborative fundamental research and high-industrial-potential research by RVCTI entities (Basque Science, Technology and Innovation Network). Projects require 3-8 partner entities, minimum €1M budget for fundamental research. Strategic areas explicitly include artificial intelligence, biotechnology, advanced materials, and digital technologies. AI priorities name "hybrid modeling and learning", "physics-based multimodal models", "explainability", and "new biomarkers and imaging techniques for diagnosis/prognosis."
- **Track:** A+B
- **Module fit:**
  - MOD-FAIR-TRAIN: 1 — Open science is not a core Elkartek topic; data management could be a minor WP but not lead framing
  - MOD-IMG-SERVERS: 1 — Imaging infrastructure could be positioned as enabling technology but not a natural Elkartek scope
  - MOD-AI-PIPELINES: 3 — Strong natural fit. AI is a named strategic area; foundation models, validated pipelines, explainability, AI for health imaging all align directly
  - MOD-THEORY-AI: 3 — Strong natural fit. "Hybrid modeling and learning," "physics-based multimodal models," "neural networks for complex multivariate systems" map directly to theory-infused AI. This is the highest-value module for Elkartek
  - MOD-MULTIMODAL-BIOMARKERS: 2 — Partial fit. "New biomarkers, biosensors, imaging techniques for diagnosis/prognosis" under the biotechnology priority. Requires named PI anchor and defined cohort
- **Confidence:** HIGH — CIC biomaGUNE is an RVCTI entity and directly eligible. The call's AI + biotechnology strategic areas are a natural home for theory-infused AI applied to biomedical imaging. Two modules score 3.
- **Red flags:**
  - **Deadline in 7 days** — extremely tight for a new application unless biomaGUNE is already involved in an Elkartek consortium for 2026
  - Requires a consortium of 3+ RVCTI entities — partner identification and agreement needed
  - Minimum €1M budget for fundamental research projects — no single entity may exceed 70% of costs
  - If no ongoing Elkartek partnerships exist, this deadline is likely unrealistic for this cycle

---

## Medium Confidence

### Ikerbasque Research Fellows 2026
- **Funder:** Ikerbasque — Basque Foundation for Science (co-funded by Basque Government and European Commission)
- **Source:** Ikerbasque Calls
- **Deadline:** 2026-03-10 at 13:00 CET (4d remaining)
- **Status:** open
- **URL:** https://calls.ikerbasque.net/
- **Budget:** 15 positions, €46,195 gross salary/year for 5 years, plus €10,000 start-up and up to €4,000 moving allowance
- **Summary:** 5-year postdoctoral research fellowships for researchers with PhDs completed 2015-2023. Designed as a track toward an independent PI role. Open to all research areas. Requires acceptance letter from host institution (CIC biomaGUNE would serve as host).
- **Track:** B
- **Module fit:**
  - MOD-FAIR-TRAIN: 0 — No fit for a researcher recruitment call
  - MOD-IMG-SERVERS: 0 — Not applicable
  - MOD-AI-PIPELINES: 2 — Could recruit an AI/ML researcher for imaging pipeline development and validation
  - MOD-THEORY-AI: 3 — Strong fit for recruiting a computational biologist, applied mathematician, or physics-informed ML researcher — exactly the core team assembly need identified in Phase I deliverables
  - MOD-MULTIMODAL-BIOMARKERS: 2 — Could recruit a multimodal imaging / biomarker researcher with computational focus
- **Confidence:** MEDIUM — Excellent strategic fit for core team assembly, especially for MOD-THEORY-AI. However, this funds a single researcher rather than program infrastructure. The 5-year duration and PI-track structure are ideal for building theory-infused AI capability. Confidence downgraded because the deadline is 4 days away and the application requires a full research proposal, host institution acceptance letter, and 2 reference letters.
- **Red flags:**
  - **Deadline in 4 days** — almost certainly too late unless an application is already in preparation
  - Funds one researcher, not a program — valuable but narrow scope
  - PhD must be from 2015-2023 — specific eligibility window limits candidate pool
  - Requires host institution acceptance letter already secured

---

## Calls evaluated but excluded

| Call | Status | Reason for exclusion |
|---|---|---|
| **Hazitek 2026** (Enterprise R&D, €119M) | Closed 2026-02-27 | Deadline passed. Company-led call; CIC biomaGUNE could participate as research partner but not lead. MOD-AI-PIPELINES partial fit (2) but confidence is moot. |
| **Azpitek 2026** (Research infrastructure, €9M) | Open until 2026-03-27 | Eligibility restricted to "centros tecnológicos multifocalizados" (multifocal technology centers). CIC biomaGUNE is a CIC (Cooperative Research Center), likely not eligible. Confidence LOW. |
| **INKER 2026** (Scientific equipment, €4M) | Closed 2026-01-22 | Deadline passed. Strong Track A fit for imaging server hardware (OMERO/XNAT) or GPU compute infrastructure (MOD-IMG-SERVERS: 2, MOD-AI-PIPELINES: 2). CICs are eligible. 90% funding for €100K-€1M equipment. **High priority for 2027 cycle** — short window (~1 month), prepare specs + quotes by Nov 2026. |
| **IKERTALDE 2026-2029** (Research group support) | Closed 2025-10-21 | University system groups only; CIC biomaGUNE not eligible. |
| **PIBA 2025-2027** (Basic/applied research) | Closed 2025-01-17 | Deadline passed. Limited to BERCs and university research structures — CICs not listed as eligible. |
| **Predoctoral Programme 2025-2026** | Closed ~2025-10 | University and BERC focused predoctoral fellowships. |
| **BERC/CIC 2026-2029** (€140M direct subsidy) | Not a competitive call | Direct institutional sustainability funding: €80M for CICs, €60M for BERCs over 4 years. CIC biomaGUNE receives baseline funding through this framework. Relevant as co-financing commitment in proposals but not a competitive opportunity. |

---

## Scan metadata
- **Date:** 2026-03-06
- **Sources checked:** SPRI Elkartek, SPRI Hazitek, Euskadi Ayudas/Trámites, PIBA, IKERTALDE, INKER, Azpitek, Ikerbasque Calls, BERC/CIC framework, BOPV, Gobierno Vasco Dept. Ciencia
- **Sources with errors or no results:** Open Data Euskadi (no structured grant call data found), BOPV (used indirectly via search), Plan Estratégico de Subvenciones (not fetched — annual planning doc)
