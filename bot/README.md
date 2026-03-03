# Funding Opportunity Matching Bot

**Status:** Planning / Not yet implemented

## Purpose

Automated scanning and triage of funding opportunities against the module fiches defined in this dossier.

## Planned capabilities

1. **Ingest** opportunity data from configured sources (RSS feeds, scraped portals, API endpoints)
2. **Extract** structured fields: name, funder, geography, themes/keywords, eligibility, budget, deadlines
3. **Score** fit against module YAML headers using the heuristic defined in `BOT_MATCHING_SPEC.md`
4. **Output** triage recommendations: top modules, recommended Track (A/B), suggested next action
5. **Update** the grant-fit matrix (`GRANT_FIT_MATRIX_TEMPLATE.csv`) with new opportunities

## Architecture (planned)

```
[Data Sources] -> [Ingester] -> [Extractor/Parser] -> [Scorer] -> [Output/Notify]
                                                          |
                                              [Module YAML headers]
                                              [Keywords Taxonomy]
```

## Data sources to configure

See `config.yaml` for source definitions. Likely sources:

- Spanish funding portals (CDTI, AEI, ISCIII)
- Basque Government (SPRI / Gobierno Vasco)
- EU portals (Funding & Tenders)
- EUREKA / Eurostar
- Specific program RSS feeds

## Getting started

Bot implementation has not started yet. When ready:

1. Define data sources in `config.yaml`
2. Implement ingester for each source type
3. Implement scorer against module YAML headers
4. Set up notification/output pipeline
