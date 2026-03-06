# Skill: scan-grants

Scan funding portals for open calls and evaluate them against the program's five-module / two-track framework.

## Instructions

You are a grant scanner for CIC biomaGUNE's program: "Image Data Infrastructure & Analysis to Drive Theory-Infused AI." Your job is to find open or upcoming funding calls and evaluate each one against the dossier.

### Step 1: Load dossier context

Read the following files to build your evaluation context:

- `STRATEGY.md`
- `PROJECT_OVERVIEW.md`
- `MODULES/MOD-FAIR-TRAIN.md`
- `MODULES/MOD-IMG-SERVERS.md`
- `MODULES/MOD-AI-PIPELINES.md`
- `MODULES/MOD-THEORY-AI.md`
- `MODULES/MOD-MULTIMODAL-BIOMARKERS.md`
- `REFERENCE/KEYWORDS_TAXONOMY.md`
- `bot/sources.yaml`

### Step 2: Parse arguments

`$ARGUMENTS` determines the scan scope:

| Argument | Behavior |
|---|---|
| *(empty)* | Full scan across all regions (EU, Spain, Basque) |
| `EU`, `Spain`, or `Basque` | Filter to that region only |
| A source name (e.g., `Elkartek`, `AEI`) | Focus on that specific source from sources.yaml |
| A URL | Evaluate that single call (same as `/check-grant`) |

### Step 3: Search for calls

For each region in scope, use **WebSearch** with targeted queries combining funder names, program keywords, and temporal qualifiers (e.g., "2026", "convocatoria abierta", "open call").

**Query strategy by region:**

**EU (English queries):**
- `Horizon Europe 2026 open calls health data AI imaging`
- `EU Funding Tenders portal 2026 calls research infrastructure digital`
- `ERC EIC 2026 open calls biomedical imaging artificial intelligence`

**Spain (Spanish queries):**
- `AEI convocatorias abiertas 2026 investigación infraestructuras datos`
- `ISCIII convocatorias 2026 salud investigación biomédica`
- `CDTI ayudas 2026 I+D colaborativa inteligencia artificial`
- `MICIU convocatorias 2026 ciencia innovación`

**Basque Country (Spanish queries):**
- `Elkartek 2026 convocatoria investigación colaborativa`
- `Hazitek 2026 convocatoria I+D`
- `PIBA Euskadi 2026 investigación básica aplicada`
- `Gobierno Vasco ayudas 2026 investigación ciencia innovación`
- `Ikerbasque 2026 calls research`

Also **WebFetch** the `programme_page`-class source URLs from sources.yaml to check for listed open or upcoming calls.

Adjust queries dynamically based on what you find. If a search reveals a specific call, follow up to get the full call details.

### Step 4: Evaluate each call

For every candidate call found, produce a structured evaluation:

**4a. Track fit:**
- **Track A** — institutional enablement / infrastructure / open science
- **Track B** — PI-anchored scientific projects with platform work packages
- **A+B** — both tracks
- **Neither** — scope doesn't align

**4b. Module fit (0-3 per module):**

| Score | Meaning |
|---|---|
| 0 | No fit |
| 1 | Superficial keyword overlap but scope doesn't align |
| 2 | Partial fit, would require creative framing |
| 3 | Strong natural fit |

Evaluate all five modules:
- **MOD-FAIR-TRAIN** — FAIR data practices, training, adoption, open science compliance
- **MOD-IMG-SERVERS** — imaging repositories, OMERO/XNAT, data infrastructure, governed access
- **MOD-AI-PIPELINES** — validated analysis pipelines, foundation models, AI/ML for imaging, QA
- **MOD-THEORY-AI** — theory-infused AI, generative AI + mechanistic modeling, physics-informed ML, nonlinear dynamics
- **MOD-MULTIMODAL-BIOMARKERS** — multimodal science, biomarker discovery, predictive imaging, digital twins

**4c. Confidence:** HIGH / MEDIUM / LOW with one-sentence justification.

**4d. Red flags:** Scope mismatches, eligibility issues, consortium requirements beyond current readiness, budget scale misalignment, geographic restrictions.

**4e. Composite inclusion rule:** Include in report only if:
- At least one module scores >= 2
- Confidence is MEDIUM or HIGH

Be skeptical. A call mentioning "data" or "digital" is not automatically a fit. Read the actual scope and objectives.

### Step 5: Write report

Write the report to `REPORTS/grant_scan_YYYY-MM-DD.md` using today's date:

```markdown
# Grant Scanner Report — {date}

**Scan scope:** {regions scanned or specific source}
**Calls found:** {N total} | **Passed evaluation:** {N included}

---

## High Confidence

### {Call Title}
- **Funder:** {funder name}
- **Source:** {source name from sources.yaml}
- **Deadline:** {date or TBD} ({days remaining}d)
- **Status:** open | pre-announcement | rolling
- **URL:** {URL}
- **Summary:** {2-3 sentence summary of what the call funds}
- **Track:** A | B | A+B
- **Module fit:**
  - MOD-FAIR-TRAIN: {0-3} — {one-line reasoning}
  - MOD-IMG-SERVERS: {0-3} — {one-line reasoning}
  - MOD-AI-PIPELINES: {0-3} — {one-line reasoning}
  - MOD-THEORY-AI: {0-3} — {one-line reasoning}
  - MOD-MULTIMODAL-BIOMARKERS: {0-3} — {one-line reasoning}
- **Confidence:** HIGH — {justification}
- **Red flags:** {any concerns or "None"}

---

## Medium Confidence

{same format}

---

## Calls evaluated but excluded

{brief list of calls that were found but didn't pass the composite inclusion rule, with one-line reason}

---

## Scan metadata
- Date: {date}
- Sources checked: {list}
- Sources with errors or no results: {list}
```

### Step 6: Present findings

After writing the report, summarize conversationally:
- Highlight the top 2-3 opportunities
- Note any upcoming deadlines requiring action
- Suggest next steps (concept note drafting, partner outreach, deeper review)
- Offer to go deeper on any specific call (`/check-grant`)
- Offer to add high-scoring calls to the Grant-Fit Matrix


## What this does NOT do

- Submit proposals or pre-register for calls
- Send emails or notifications
- Replace human judgment — this is a structured filter and briefing
- Guarantee completeness — some calls may not appear in web search results
