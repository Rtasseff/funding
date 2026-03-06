# Skill: check-grant

Evaluate a single funding call against the program's five-module / two-track framework.

## Instructions

You are evaluating whether a specific funding call is a genuine fit for CIC biomaGUNE's program: "Image Data Infrastructure & Analysis to Drive Theory-Infused AI."

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

### Step 2: Get call information

`$ARGUMENTS` should be one of:
- A **URL** — use WebFetch to retrieve the call text
- A **text description** — evaluate directly from the provided text
- A **call name** — use WebSearch to find the call, then WebFetch the result

If the URL is behind a login wall or the content is too sparse, note this and ask the user to paste the call text directly.

### Step 3: Evaluate

Produce a structured assessment:

**Track fit:**
- **Track A** — institutional enablement / infrastructure / open science
- **Track B** — PI-anchored scientific projects with platform work packages
- **A+B** — both tracks
- **Neither** — scope doesn't align

**Module fit (0-3 per module):**

| Score | Meaning |
|---|---|
| 0 | No fit |
| 1 | Superficial keyword overlap but scope doesn't align |
| 2 | Partial fit, would require creative framing |
| 3 | Strong natural fit |

Evaluate all five modules with one-line reasoning each:
- **MOD-FAIR-TRAIN** — FAIR data practices, training, adoption, open science compliance
- **MOD-IMG-SERVERS** — imaging repositories, OMERO/XNAT, data infrastructure, governed access
- **MOD-AI-PIPELINES** — validated analysis pipelines, foundation models, AI/ML for imaging, QA
- **MOD-THEORY-AI** — theory-infused AI, generative AI + mechanistic modeling, physics-informed ML, nonlinear dynamics
- **MOD-MULTIMODAL-BIOMARKERS** — multimodal science, biomarker discovery, predictive imaging, digital twins

**Confidence:** HIGH / MEDIUM / LOW with one-sentence justification.

**Red flags:** Scope mismatches, eligibility issues, consortium requirements, budget scale, geographic restrictions.

Be skeptical. A call mentioning "data" or "digital" is not automatically a fit. Read the actual scope and objectives.

### Step 4: Present findings

Output the evaluation conversationally (not written to file unless the user asks). Format:

```
## {Call Title} — Evaluation

**Funder:** ...
**Deadline:** ... ({days remaining}d)
**URL:** ...
**Summary:** {2-3 sentences on what the call funds}

**Track:** A | B | A+B | Neither
**Module fit:**
- MOD-FAIR-TRAIN: {0-3} — {reasoning}
- MOD-IMG-SERVERS: {0-3} — {reasoning}
- MOD-AI-PIPELINES: {0-3} — {reasoning}
- MOD-THEORY-AI: {0-3} — {reasoning}
- MOD-MULTIMODAL-BIOMARKERS: {0-3} — {reasoning}

**Confidence:** {level} — {justification}
**Red flags:** {concerns or "None"}

**Verdict:** {one-sentence recommendation}
```

### Step 5: Offer follow-ups

After the evaluation, offer:
- Write a concept note using `TEMPLATES/CONCEPT_NOTE_TEMPLATE.md`
- Add this opportunity to the Grant-Fit Matrix (`GRANT_FIT_MATRIX_TEMPLATE.csv`)
- Compare against other opportunities already in the matrix
- Run a broader scan (`/scan-grants`) to find similar calls
- Save the evaluation to `REPORTS/` if the user wants a record
