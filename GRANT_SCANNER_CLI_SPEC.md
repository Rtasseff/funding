# Grant Scanner CLI Tool — Specification

**Date:** 2026-03-03
**Author:** Ryan Tasseff / Claude
**Purpose:** Automated weekly scan of funding portals, validated against the five-module / two-track framework, with structured reporting.

---

## 1) What the tool does

A CLI script (designed to be run via `claude` CLI or cron) that:

1. Queries a defined set of funding portals for open or upcoming calls
2. Filters by minimum lead time (≥ 90 days to deadline)
3. Validates that each URL resolves (HTTP 200, no redirect to generic error page)
4. Reads the actual call text and scores language fit against the five modules and two tracks — not just keyword matching, but contextual confirmation that the call's scope genuinely aligns
5. Outputs a structured report (Markdown + optional CSV)

**The tool takes no action beyond reporting.** No submissions, no emails, no side effects.

---

## 2) Input: the dossier context

The tool needs access to the following files from the funding positioning dossier (provided as local paths or bundled into the tool's config directory):

- `STRATEGY.md` — two-track pattern and packaging rules
- `PROJECT_OVERVIEW.md` — program scope and non-goals
- Module fiches:
  - `MOD-FAIR-TRAIN.md`
  - `MOD-IMG-SERVERS.md`
  - `MOD-AI-PIPELINES.md`
  - `MOD-THEORY-AI.md`
  - `MOD-MULTIMODAL-BIOMARKERS.md`
- `GRANT_FIT_MATRIX_TEMPLATE.md` — scoring criteria

These are loaded as system context for the LLM evaluation step.

---

## 3) Sources to scan

### Tier 1 — Primary (scan every week)

| Source | URL | Type | Notes |
|---|---|---|---|
| EU Funding & Tenders Portal | https://ec.europa.eu/info/funding-tenders/opportunities/portal/screen/opportunities/calls-for-proposals | Web/API | Central EU call database incl. Horizon Europe |
| AEI Convocatorias | https://www.aei.gob.es/convocatorias | Web | Main Spanish research call portal |
| AEI Calendario Previsto | https://www.aei.gob.es/convocatorias/calendario-previsto-convocatorias-agencia-estatal-investigacion | Web | Upcoming calls not yet open — early warning |
| BOE Ayudas | https://www.boe.es/buscar/ayudas.php | Web | Official state bulletin, newly published grants |
| BDNS / SNPSAP | https://www.pap.hacienda.gob.es/bdnstrans/ | Web | National grants database; supports alert subscriptions |
| Euskadi.eus Ayudas | https://www.euskadi.eus/gobierno-vasco/tramites-servicios/ | Web | Main Basque Government aid portal |
| BOPV | https://www.euskadi.eus/web01-bopv/es/ | Web | Official Basque gazette |
| Open Data Euskadi | https://opendata.euskadi.eus/ | API/RSS/XLSX | Machine-readable — priority for automation |

### Tier 2 — Secondary (scan biweekly or on-demand)

| Source | URL | Type | Notes |
|---|---|---|---|
| Horizon Europe Work Programmes | https://research-and-innovation.ec.europa.eu/funding/funding-opportunities/funding-programmes-and-open-calls/horizon-europe/horizon-europe-work-programmes_en | Web | Programme docs; calls link back to Tier 1 EU portal |
| CDTI Convocatorias | https://www.cdti.es/convocatorias | Web | Translational / infrastructure / collaborative R&D |
| ISCIII / AES | https://www.isciii.es/ | Web | Biomedical and health research calls |
| Basque Ciencia/Universidades | https://www.euskadi.eus/informacion/ayudas-al-personal-investigador-programa-predoctoral/web01-a3predoc/es/ | Web | IKERTALDE, PIBA, Programa CIC, pre/postdoc |
| Ikerbasque Calls | https://calls.ikerbasque.net/ | Web | Science funding/recruitment |

### Source configuration

Sources are defined in a YAML config file (`sources.yaml`) so they can be added, removed, or re-tiered without changing code:

```yaml
sources:
  - name: "EU Funding & Tenders Portal"
    url: "https://ec.europa.eu/info/funding-tenders/opportunities/portal/screen/opportunities/calls-for-proposals"
    tier: 1
    type: web
    language: en
    scan_frequency: weekly

  - name: "Open Data Euskadi"
    url: "https://opendata.euskadi.eus/"
    tier: 1
    type: api
    language: es
    scan_frequency: weekly
    notes: "Machine-readable, supports RSS and API"

  # ... etc
```

---

## 4) Filtering rules

### 4a. Deadline filter
- **Minimum lead time: 90 days** from scan date
- Calls with no published deadline: include but flag as `deadline: TBD`
- Calls already past deadline: exclude entirely
- Upcoming/pre-announcement calls (no open date yet): include and flag as `status: pre-announcement`

### 4b. URL validation
- HTTP HEAD or GET request to the call-specific URL
- Accept: HTTP 200 (or 301/302 that resolves to a valid page)
- Reject: 404, 410, 5xx, redirect to generic portal homepage, timeout > 10s
- If URL fails validation: exclude from report but log to `dead_links.log` with source and date

### 4c. Language / scope validation (LLM step)
This is the critical differentiator from dumb keyword search. For each candidate call that passes 4a and 4b:

1. Fetch the call text (or abstract/summary if full text is gated)
2. Send to Claude with the dossier context and the following evaluation prompt:

```
You are evaluating whether a funding call is a genuine fit for the
program described in the attached dossier documents.

For each call, assess:

1. TRACK FIT: Does this call fund Track A (institutional enablement /
   infrastructure / open science) or Track B (PI-anchored scientific
   projects with platform work packages)? Or neither?

2. MODULE FIT: Which of the five modules does this call genuinely
   support? Score each 0-3:
   - 0 = no fit
   - 1 = superficial keyword overlap but scope doesn't align
   - 2 = partial fit, would require creative framing
   - 3 = strong natural fit

   Modules:
   - MOD-FAIR-TRAIN (FAIR data practices, training, adoption)
   - MOD-IMG-SERVERS (imaging repositories, OMERO/XNAT)
   - MOD-AI-PIPELINES (validated analysis pipelines, AI/ML for imaging)
   - MOD-THEORY-AI (theory-infused AI, generative AI + mechanistic modeling, physics-informed ML)
   - MOD-MULTIMODAL-BIOMARKERS (multimodal science, biomarker discovery, predictive imaging, digital twins)

3. CONFIDENCE: Overall confidence that this call is worth pursuing
   (HIGH / MEDIUM / LOW) with one-sentence justification.

4. RED FLAGS: Note any scope mismatches, eligibility issues, or
   reasons this might be a false positive (e.g., "digital health"
   used in a clinical IT context that doesn't apply to us).

Be skeptical. A call mentioning "data" or "digital" is not
automatically a fit. Read the actual scope and objectives.
```

### 4d. Composite inclusion rule
Include in the final report only if:
- At least one module scores ≥ 2
- Confidence is MEDIUM or HIGH
- URL validated
- Deadline ≥ 90 days out (or TBD/pre-announcement)

Calls scoring all 1s or with LOW confidence go to a separate `borderline.log` for optional manual review.

---

## 5) Output format

### Primary report: `grant_scan_YYYY-MM-DD.md`

```markdown
# Grant Scanner Report — {date}

**Scan parameters:** {sources scanned}, {date range}, {min lead time}
**Calls evaluated:** {N total} → {N passed filters} → {N in report}

---

## High Confidence

### {Call Title}
- **Funder:** {funder name}
- **Portal:** {source name}
- **Deadline:** {date} ({days remaining}d)
- **Status:** open | pre-announcement | rolling
- **URL:** {verified URL}
- **Summary:** {2-3 sentence summary of what the call actually funds}
- **Track:** A | B | A+B
- **Module fit:**
  - MOD-FAIR-TRAIN: {0-3} — {one-line reasoning}
  - MOD-IMG-SERVERS: {0-3} — {one-line reasoning}
  - MOD-AI-PIPELINES: {0-3} — {one-line reasoning}
  - MOD-THEORY-AI: {0-3} — {one-line reasoning}
  - MOD-MULTIMODAL-BIOMARKERS: {0-3} — {one-line reasoning}
- **Confidence:** HIGH — {justification}
- **Red flags:** {any concerns or none}

---

## Medium Confidence

{same format}

---

## Scan metadata
- Sources with errors: {list}
- Dead links found: {count, see dead_links.log}
- Borderline calls: {count, see borderline.log}
```

### Secondary output: `grant_scan_YYYY-MM-DD.csv`

Flat CSV with columns: `call_title, funder, portal, deadline, days_remaining, status, url, track, mod_fair, mod_img, mod_ai, mod_theory, mod_multi, confidence, red_flags, summary`

This feeds directly into the `GRANT_FIT_MATRIX_TEMPLATE.csv`.

---

## 6) CLI interface

```bash
# Full weekly scan (Tier 1 sources)
grant-scanner scan

# Full scan including Tier 2
grant-scanner scan --all-tiers

# Scan specific source only
grant-scanner scan --source "AEI Convocatorias"

# Check a single URL manually
grant-scanner check <url>

# Validate all configured source URLs are reachable
grant-scanner healthcheck

# Show current configuration
grant-scanner config

# Output previous report
grant-scanner report --date 2026-02-24
```

### Configuration
- `~/.grant-scanner/config.yaml` — global settings (lead time, output dir, API keys)
- `~/.grant-scanner/sources.yaml` — portal definitions
- `~/.grant-scanner/dossier/` — symlinks or copies of module fiches and strategy docs
- `~/.grant-scanner/reports/` — generated reports
- `~/.grant-scanner/logs/` — dead_links.log, borderline.log, scan.log

### Cron setup (example)
```bash
# Run every Friday at 08:00 (before weekly triage)
0 8 * * 5 /usr/local/bin/grant-scanner scan >> ~/.grant-scanner/logs/cron.log 2>&1
```

---

## 7) Technical approach

### Scraping / data retrieval
- **Open Data Euskadi:** Use their API or RSS feed directly — this is the cleanest source
- **EU Funding & Tenders Portal:** Has a structured search; may have an undocumented API or can be scraped from the search results page
- **Spanish portals (AEI, BOE, BDNS):** Mostly web scraping; BDNS supports alert subscriptions which could be leveraged
- **Basque portals (Euskadi.eus, BOPV):** Web scraping

### Language handling
- Spanish-language calls: the LLM evaluation step handles multilingual input natively
- Call text should be fetched in the original language; no pre-translation needed

### Rate limiting and politeness
- Maximum 1 request per second per domain
- Respect `robots.txt` where present
- Cache fetched pages for 24 hours to avoid redundant requests on reruns

### Dependencies
- Python 3.10+ or Node.js (implementer's choice)
- `claude` CLI for the LLM evaluation step (or direct API calls to Anthropic)
- `requests` / `httpx` or equivalent for HTTP
- `beautifulsoup4` or equivalent for HTML parsing
- `pyyaml` for config
- `feedparser` for RSS (Open Data Euskadi)

---

## 8) What this tool does NOT do

- Submit proposals or pre-register
- Send emails or notifications (add later if wanted)
- Store historical trend data (add later if wanted)
- Replace human judgment — this is a filter, not a decision maker
- Guarantee completeness — some calls may not appear on monitored portals

---

## 9) Future extensions (not in v1)

- Email or Slack notification when HIGH confidence calls appear
- Historical tracking: trend of calls per module over time
- Auto-populate GRANT_FIT_MATRIX_TEMPLATE.csv
- Portal-specific API integrations as they become available
- Multi-institute mode (for ReDIB network scanning)
