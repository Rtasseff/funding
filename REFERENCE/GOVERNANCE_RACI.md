# Governance and RACI (Draft)

**Date:** 2026-03-03

## Roles (proposed)

- **Program Operational Lead:** coordinates portfolio, owns templates, runs adoption model
- **IT / Systems Owner:** hosting, backups, uptime, security, account provisioning
- **PI / Scientific Anchor:** defines scientific priorities and validates Track B outputs
- **Data Contact (per lab/project):** ensures minimal metadata and workflow compliance
- **Core Facility / Instrument Lead:** ensures acquisition/export conventions are practical
- **Steering Group (lightweight):** resolves decisions and approves scope changes

## Decision rights (examples)

- Data governance / access rules: Steering Group + IT + Program Lead
- Server architecture and hosting: IT (with Program Lead input)
- Minimal metadata profile: Program Lead + Data Contacts + Core Facility leads
- Pipeline acceptance into "production": PI anchors + Program Lead (QA criteria)
- Theory-infused AI research direction: Program Lead + PI anchors + DIPC partners
- DIPC partnership scope and compute allocation: Program Lead + Steering Group + DIPC

## Service boundaries (avoid scope creep)

**Offered**
- Templates, training, office hours, onboarding playbooks
- Standard ingest guidance and minimal metadata expectations
- Server-backed workflows and reference implementations
- Reproducible pipeline packaging and QA criteria

**Not offered**
- Writing entire DMPs for labs as a default service
- Manual data entry/curation as a default service
- Scientific interpretation in place of PI-led work

## RACI (high-level)

| Activity | Program Lead | IT | PI Anchor | Data Contact | Core Facility |
|---|---|---|---|---|---|
| Define minimal metadata profile | R | C | C | C | C |
| Operate training + adoption model | A/R | C | C | C | C |
| Provision accounts/permissions | C | A/R | C | C | C |
| OMERO/XNAT uptime + backups | C | A/R | I | I | I |
| Lighthouse pilot execution | A/R | C | A/R | R | R |
| Accept pipeline into production | A/R | C | A/R | C | C |
| Proposal assembly (Track A) | A/R | C | C | I | I |
| Proposal assembly (Track B) | C | I | A/R | C | C |
| Theory-AI research direction | A/R | I | C | I | I |
| DIPC partnership coordination | A/R | C | C | I | I |
