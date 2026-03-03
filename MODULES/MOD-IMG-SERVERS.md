# MOD-IMG-SERVERS — Imaging Data Infrastructure (OMERO + XNAT)

```yaml
module_id: MOD-IMG-SERVERS
module_name: Imaging Data Infrastructure (OMERO + XNAT)
track_type: both
time_horizon: 24_months_initial, 5_years_full
readiness_level: design_and_pilot_phase
eligible_lead_types: [institution, PI_as_anchor, consortium]
best_fit_geographies: [Basque, Spain, EU]
budget_class: medium_to_large
keywords: [imaging repository, OMERO, XNAT, DICOM, OME-TIFF, OME-Zarr, microscopy, metadata, access control, interoperability]
core_assets:
  - standards alignment work (DICOM/OME/REMBI/BIDS awareness)
  - existing RDM governance and templates to connect lifecycle and publication linkage
dependencies:
  - hosting decisions (on-prem vs hybrid) + sysadmin allocation
  - identity/access model and permissions governance
  - minimal metadata profile and ingest conventions
success_metrics:
  - "# projects onboarded + TB ingested/served"
  - median onboarding time (days/weeks)
  - uptime + backup verification
  - "publication linkage coverage (dataset <-> publication)"
last_updated: 2026-03-03
```

## One-sentence positioning

Deploy and operationalize complementary imaging repositories—OMERO for microscopy and XNAT for DICOM biomedical imaging—with standardized ingest, minimal metadata, and governed access so data becomes findable, shareable (under controls), and analysis-ready.

## Current state

- **gjesus3 pilot** active: registry model (raw/project/publication tiers), baseline metadata expectations, spec v1.0 + launch plan targets. This is the microscopy lighthouse.
- **Nuke pilot** active: second imaging-RDM workflow using DICOM reconstructed outputs, generalizing the ingestion + metadata pattern beyond microscopy.
- **XNAT server** identified as Q2 bridge from RDM governance to a data-infrastructure-and-analysis proof-of-concept.
- Standards alignment work underway (DICOM/OME/REMBI/BIDS awareness).
- Key framing: ingestion + registry + metadata governance pilots are already running; servers are the *packaging layer* once workflows stabilize.

## Assumption note

This fiche assumes "Xnet" means **XNAT** (common in biomedical imaging). If "Xnet" refers to a different system, swap the platform name; the governance and deliverables remain the same.

## Next-stage objective (12-24 months)

1. Define governance: identity/access, lifecycle, "system of record" for imaging metadata.
2. OMERO lighthouse pilot: acquisition -> ingest -> minimal metadata -> access -> export for analysis.
3. XNAT lighthouse pilot: DICOM ingest -> project conventions -> access -> viewer/export hooks.
4. Cross-cutting: connect server datasets to DMP "data sources" and publication-linked archiving.

## Longer-term trajectory (3-5 years)

- Federation/interoperability: APIs, controlled sharing, multi-site collaboration.
- Integration with validated AI pipelines and containerized analysis.

## Risks / mitigations

- "Perfect metadata" blocks onboarding: mitigate via minimal profiles + iteration.
- Under-resourced sysadmin: mitigate via explicit budget + service-level targets.
