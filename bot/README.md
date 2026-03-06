# Grant Scanner

**Status:** Operational (Claude Code skills)

## What this is

Two Claude Code skills that scan funding portals and evaluate calls against the program's five-module / two-track framework using contextual analysis (not keyword matching).

## How to use

### `/scan-grants` — multi-region scan

```
/scan-grants              # Full scan — all regions
/scan-grants EU           # EU sources only
/scan-grants Spain        # Spanish sources only
/scan-grants Basque       # Basque sources only
/scan-grants Elkartek     # Focus on a single source
```

Produces a dated report in `REPORTS/grant_scan_YYYY-MM-DD.md` plus a conversational summary with recommended next steps.

### `/check-grant` — single call evaluation

```
/check-grant <url>              # Evaluate a call by URL
/check-grant <call name>        # Search for and evaluate a call
/check-grant <pasted text>      # Evaluate from description
```

Produces a conversational evaluation (track fit, module scores, confidence, red flags). Not written to file unless asked.

## Files in this directory

- `sources.yaml` — funding source registry (25 sources across EU, Spain, Basque Country)

## Specifications

- **Full spec:** `GRANT_SCANNER_CLI_SPEC.md` (root)
- **Matching logic:** `BOT_MATCHING_SPEC.md` (root)
- **Command definitions:** `.claude/commands/scan-grants.md` and `.claude/commands/check-grant.md`
