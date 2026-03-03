# Grant Scanner CLI Tool

**Status:** Specified / Not yet implemented

## What this is

An LLM-powered CLI tool that scans funding portals weekly and evaluates each call against the program's five-module / two-track framework using contextual analysis (not keyword matching). It produces structured Markdown + CSV reports for the weekly Friday triage.

## How it works

1. **Fetch** — queries configured funding portals for open or upcoming calls
2. **Filter** — deadline (≥90 days), URL validation (HTTP check), pre-announcements flagged
3. **Evaluate** — sends call text + dossier context to Claude for contextual scoring (track fit, module fit 0-3, confidence HIGH/MEDIUM/LOW, red flags)
4. **Report** — outputs dated Markdown report grouped by confidence, plus CSV feeding into `GRANT_FIT_MATRIX_TEMPLATE.csv`

The tool takes **no action beyond reporting**. No submissions, no emails, no side effects.

## Key commands

```bash
grant-scanner scan              # Weekly scan (Tier 1 sources)
grant-scanner scan --all-tiers  # Include Tier 2 sources
grant-scanner check <url>       # Evaluate a single URL manually
grant-scanner healthcheck       # Validate all source URLs
grant-scanner config            # Show current configuration
grant-scanner report --date YYYY-MM-DD  # Retrieve a previous report
```

## Configuration

Runtime config at `~/.grant-scanner/`:
- `config.yaml` — global settings (lead time, output dir, API keys)
- `sources.yaml` — portal definitions (see spec for full list)
- `dossier/` — symlinks or copies of module fiches and strategy docs
- `reports/` — generated reports
- `logs/` — dead_links.log, borderline.log, scan.log

Reference config template in this directory: `config.yaml`

## Data sources

13 portals across 3 geographies:

**Tier 1 (weekly):** EU Funding & Tenders, AEI Convocatorias, AEI Calendario Previsto, BOE Ayudas, BDNS/SNPSAP, Euskadi.eus Ayudas, BOPV, Open Data Euskadi

**Tier 2 (biweekly):** Horizon Europe Work Programmes, CDTI, ISCIII/AES, Basque Ciencia/Universidades, Ikerbasque

See `GRANT_SCANNER_CLI_SPEC.md` section 3 for full URLs and notes.

## Specifications

- **Full spec:** `GRANT_SCANNER_CLI_SPEC.md` (root)
- **Matching logic:** `BOT_MATCHING_SPEC.md` (root)

## Implementation

Not yet started. Dependencies: Python 3.10+ or Node.js, `claude` CLI or Anthropic API, requests/httpx, beautifulsoup4, pyyaml, feedparser.
