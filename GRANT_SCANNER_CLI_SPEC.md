# Grant Scanner — Specification

**Date:** 2026-03-03 (updated 2026-03-06)
**Author:** Ryan Tasseff / Claude
**Purpose:** Scan funding portals for open calls and evaluate each against the five-module / two-track framework, with structured reporting.

---

## 1) What the tool does

Two Claude Code skills that use WebSearch, WebFetch, and full dossier context to find and evaluate funding calls:

- **`/scan-grants`** — multi-region scan across all configured sources, producing a dated report in `REPORTS/`
- **`/check-grant`** — quick evaluation of a single call (URL or description), with conversational output

Claude Code reads the actual call text and scores fit contextually — not keyword matching, but genuine scope evaluation against the program's modules and tracks.

**The tool takes no action beyond reporting.** No submissions, no emails, no side effects.

---

## 2) Input: the dossier context

Both skills read the following files at invocation to build evaluation context:

- `STRATEGY.md` — two-track pattern and packaging rules
- `PROJECT_OVERVIEW.md` — program scope and non-goals
- Module fiches:
  - `MODULES/MOD-FAIR-TRAIN.md`
  - `MODULES/MOD-IMG-SERVERS.md`
  - `MODULES/MOD-AI-PIPELINES.md`
  - `MODULES/MOD-THEORY-AI.md`
  - `MODULES/MOD-MULTIMODAL-BIOMARKERS.md`
- `REFERENCE/KEYWORDS_TAXONOMY.md` — controlled keywords for query construction
- `bot/sources.yaml` — funding source registry (URLs, regions, classes)

Total dossier context is ~58 KB / ~15K tokens — fits comfortably in a single invocation.

---

## 3) Sources to scan

### Source classification

Sources are classified into six functional classes that determine scanning behavior:

| Class | What it is | Scanner behavior |
|---|---|---|
| `call_portal` | Active call listings | WebSearch + WebFetch for open calls |
| `early_warning` | Calendars, pre-announcements | WebSearch for upcoming calls; WebFetch programme pages |
| `legal_gazette` | Official publication backstops (BOE, BOPV, BDNS) | WebSearch with research/innovation keywords |
| `data_feed` | Machine-readable API/RSS sources | WebSearch (structured API integration deferred to v2) |
| `programme_page` | Specific scheme or programme pages | WebFetch directly to check for open/upcoming calls |
| `reference` | Scope/context pages (not scannable) | Not scanned — human triage only |

### EU (4 sources)

| # | Name | Class | Priority | Notes |
|---|---|---|---|---|
| 1 | [EU Funding & Tenders Portal](https://ec.europa.eu/info/funding-tenders/opportunities/portal/screen/opportunities/calls-for-proposals) | call_portal | weekly | Central EU call database |
| 2 | [Horizon Europe Work Programmes](https://research-and-innovation.ec.europa.eu/funding/funding-opportunities/funding-programmes-and-open-calls/horizon-europe/horizon-europe-work-programmes_en) | early_warning | weekly | Scope anchor; calls route to #1 |
| 3 | [Horizon Europe Cluster 1 Health](https://research-and-innovation.ec.europa.eu/research-area/health/cluster-1-health_en) | reference | — | Scope page for health topics; not scannable |
| 4 | [EIC Funding Opportunities](https://eic.ec.europa.eu/eic-funding-opportunities_en) | programme_page | quarterly | Only if translational partnership emerges |

### Spain (10 sources)

| # | Name | Class | Priority | Notes |
|---|---|---|---|---|
| 5 | [AEI Convocatorias](https://www.aei.gob.es/convocatorias) | call_portal | weekly | Main Spanish research calls |
| 6 | [AEI Buscador de Convocatorias](https://www.aei.gob.es/convocatorias/buscador-convocatorias) | call_portal | weekly | Searchable catalog (separate from landing page) |
| 7 | [AEI Calendario Previsto](https://www.aei.gob.es/convocatorias/calendario-previsto-convocatorias-agencia-estatal-investigacion) | early_warning | weekly | Pre-announcements |
| 8 | [MICIU Convocatorias](https://www.ciencia.gob.es/Convocatorias.html) | call_portal | weekly | Ministry calls beyond AEI |
| 9 | [ISCIII / AES](https://www.isciii.es/QueHacemos/Financiacion/Paginas/default.aspx) | call_portal | weekly | Biomedical/health research |
| 10 | [CDTI Ayudas y Servicios](https://www.cdti.es/ayudas) | call_portal | weekly | Collaborative R&D, translational |
| 11 | [CDTI Calendario](https://www.cdti.es/ayudas/calendario-de-convocatorias) | early_warning | weekly | Expected call windows |
| 12 | [BOE Ayudas](https://www.boe.es/buscar/ayudas.php) | legal_gazette | weekly | Official state bulletin backstop |
| 13 | [BDNS / SNPSAP](https://www.pap.hacienda.gob.es/bdnstrans/) | legal_gazette | weekly | National grants DB |
| 14 | [FECYT Convocatorias](https://www.fecyt.es/es/convocatorias) | call_portal | biweekly | Open science / science communication |

### Basque Country (11 sources)

| # | Name | Class | Priority | Notes |
|---|---|---|---|---|
| 15 | [Euskadi Ayudas / Trámites](https://www.euskadi.eus/gobierno-vasco/tramites-servicios/) | call_portal | weekly | Main Basque aid portal |
| 16 | [Open Data Euskadi](https://opendata.euskadi.eus/) | data_feed | weekly | Machine-readable (API/RSS/JSON) |
| 17 | [BOPV](https://www.euskadi.eus/web01-bopv/es/) | legal_gazette | weekly | Official Basque gazette backstop |
| 18 | [Dept. Ciencia, Universidades e Innovación](https://www.euskadi.eus/gobierno-vasco/departamento-ciencia-universidades-innovacion/) | reference | — | Departmental landing; not scannable |
| 19 | [Plan Estratégico de Subvenciones](https://www.euskadi.eus/gobierno-vasco/-/plan-estrategico-subvenciones/) | early_warning | annual | Annual subsidy inventory (~68 lines in 2026) |
| 20 | [PIBA](https://www.euskadi.eus/gobierno-vasco/-/ayuda-subvencion/programa-de-ayudas-para-la-financiacion-de-proyectos-de-investigacion-basica-y-aplicada-piba/) | programme_page | weekly | Basic/applied research projects |
| 21 | [IKERTALDE](https://www.euskadi.eus/gobierno-vasco/-/ayuda-subvencion/programa-de-apoyo-a-los-grupos-de-investigacion-del-sistema-universitario-vasco-ikertalde/) | programme_page | weekly | Research group support |
| 22 | [INKER](https://www.euskadi.eus/gobierno-vasco/-/ayuda-subvencion/programa-de-infraestructuras-de-investigacion-inker/) | programme_page | weekly | Scientific equipment |
| 23 | [SPRI Hazitek](https://www.spri.eus/es/ayudas/hazitek/) | programme_page | weekly | Industry-academic R&D consortia |
| 24 | [SPRI Elkartek](https://www.spri.eus/es/ayudas/elkartek/) | programme_page | weekly | Collaborative research (RVCTI actors) |
| 25 | [Ikerbasque Calls](https://calls.ikerbasque.net/) | programme_page | biweekly | Talent/programme opportunities |

### Source configuration

Sources are defined in `bot/sources.yaml` so they can be added, removed, or reclassified without changing the skill definitions. See that file for the full registry with URLs, classes, priorities, languages, and notes.

---

## 4) Scanning strategy

The scanner uses **theme-based WebSearch** combined with **targeted WebFetch** of programme pages. This replaces the old scraper pipeline approach (HTTP fetching, HTML parsing, rate limiting) with Claude Code's native capabilities.

### WebSearch queries

For each region in scope, the scanner constructs 3-5 search queries combining:
- Funder names (from sources.yaml)
- Program keywords (from KEYWORDS_TAXONOMY.md)
- Temporal qualifiers (current year, "convocatoria abierta", "open call")

**EU queries** are in English. **Spain and Basque** queries are in Spanish. The scanner dynamically adjusts queries based on initial results.

### WebFetch of programme pages

For `programme_page`-class sources (e.g., Elkartek, PIBA, Hazitek), the scanner fetches the page directly to check for open or upcoming call listings.

### Advantages over scraper approach

- **No parser to maintain** — handles portal redesigns gracefully
- **Finds calls beyond monitored portals** — WebSearch surfaces opportunities from any source
- **Multilingual natively** — no translation or language detection pipeline needed
- **Immediate availability** — no dependencies, no deployment, no cron infrastructure

---

## 5) Evaluation rubric

For each candidate call, the scanner produces a structured evaluation:

### Track fit

- **Track A** — institutional enablement / infrastructure / open science
- **Track B** — PI-anchored scientific projects with platform work packages
- **A+B** — both tracks
- **Neither** — scope doesn't align with the two-track pattern

### Module fit (0-3 per module)

| Score | Meaning |
|---|---|
| 0 | No fit |
| 1 | Superficial keyword overlap but scope doesn't align |
| 2 | Partial fit, would require creative framing |
| 3 | Strong natural fit |

Modules:
- **MOD-FAIR-TRAIN** — FAIR data practices, training, adoption, open science compliance
- **MOD-IMG-SERVERS** — imaging repositories, OMERO/XNAT, data infrastructure, governed access
- **MOD-AI-PIPELINES** — validated analysis pipelines, foundation models, AI/ML for imaging, QA
- **MOD-THEORY-AI** — theory-infused AI, generative AI + mechanistic modeling, physics-informed ML, nonlinear dynamics
- **MOD-MULTIMODAL-BIOMARKERS** — multimodal science, biomarker discovery, predictive imaging, digital twins

### Confidence

- **HIGH** — strong fit, clear eligibility, actionable
- **MEDIUM** — plausible fit, may require creative framing or partner coordination
- **LOW** — weak fit, likely false positive

### Red flags

Scope mismatches, eligibility issues, consortium requirements beyond current readiness, budget scale misalignment, geographic restrictions.

### Composite inclusion rule

Include in the final report only if:
- At least one module scores >= 2
- Confidence is MEDIUM or HIGH

Calls failing this rule are listed in the "evaluated but excluded" section of the report.

---

## 6) Output format

### `/scan-grants` report: `REPORTS/grant_scan_YYYY-MM-DD.md`

```markdown
# Grant Scanner Report — {date}

**Scan scope:** {regions or source}
**Calls found:** {N total} | **Passed evaluation:** {N included}

---

## High Confidence

### {Call Title}
- **Funder:** {funder name}
- **Source:** {source name}
- **Deadline:** {date or TBD} ({days remaining}d)
- **Status:** open | pre-announcement | rolling
- **URL:** {URL}
- **Summary:** {2-3 sentence summary}
- **Track:** A | B | A+B
- **Module fit:**
  - MOD-FAIR-TRAIN: {0-3} — {one-line reasoning}
  - MOD-IMG-SERVERS: {0-3} — {one-line reasoning}
  - MOD-AI-PIPELINES: {0-3} — {one-line reasoning}
  - MOD-THEORY-AI: {0-3} — {one-line reasoning}
  - MOD-MULTIMODAL-BIOMARKERS: {0-3} — {one-line reasoning}
- **Confidence:** HIGH — {justification}
- **Red flags:** {concerns or "None"}

---

## Medium Confidence
{same format}

---

## Calls evaluated but excluded
{brief list with one-line reason each}

---

## Scan metadata
- Date: {date}
- Sources checked: {list}
- Sources with errors or no results: {list}
```

### `/check-grant` output

Conversational — same evaluation structure but presented inline, not written to file (unless requested). See skill definition for format.

### CSV on request

If the user asks, the scanner can produce a flat CSV with columns: `call_title, funder, source, deadline, days_remaining, status, url, track, mod_fair, mod_img, mod_ai, mod_theory, mod_multi, confidence, red_flags, summary` — suitable for appending to `GRANT_FIT_MATRIX_TEMPLATE.csv`.

---

## 7) Invocation

### `/scan-grants`

```
/scan-grants              # Full scan — all regions
/scan-grants EU           # EU sources only
/scan-grants Spain        # Spanish sources only
/scan-grants Basque       # Basque sources only
/scan-grants Elkartek     # Single source focus
/scan-grants <url>        # Evaluate a specific URL (same as /check-grant)
```

### `/check-grant`

```
/check-grant <url>                    # Evaluate a call by URL
/check-grant <call name or funder>    # Search for and evaluate a call
/check-grant <pasted text>            # Evaluate from description text
```

---

## 8) What this does NOT do

- Submit proposals or pre-register
- Send emails or notifications (future extension)
- Store historical trend data (future extension)
- Replace human judgment — this is a filter, not a decision maker
- Guarantee completeness — some calls may not appear in web search results or on monitored portals

---

## 9) Future extensions

- **Scheduled scanning** — wrapper script or API integration to trigger `/scan-grants` on a schedule
- **Notifications** — email or Slack alerts when HIGH confidence calls appear
- **Historical tracking** — trend of calls per module over time
- **Auto-populate Grant-Fit Matrix** — append rows to `GRANT_FIT_MATRIX_TEMPLATE.csv` automatically
- **Portal-specific API integrations** — structured access to BDNS, Open Data Euskadi as they become available
- **Multi-institute mode** — ReDIB network scanning
