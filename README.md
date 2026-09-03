# Script Documentation Reviewer

A cross-language documentation auditor for PowerShell, Python, Bash, and other scripting languages.  
Designed to ensure your scripts are supportable, maintainable, and handoff-ready — even years after you wrote them.

This tool evaluates documentation quality, identifies gaps, computes weighted scores, assigns severity levels, and can generate missing documentation sections on demand.

**Current Prompt Version:** 1.4.1 (2026-09-03)

---

## Features

- Multi-language support (PowerShell, Python, Bash, etc.)
- Weighted scoring model for documentation, supportability, and maintainability
- Risk scoring engine modeled after enterprise security tooling
- Markdown or HTML report output
- Documentation diff mode for comparing script versions
- Rewrite mode to generate missing documentation sections
- Strict, deterministic output format with anti-drift guards
- Governance-ready structure with versioning and changelog discipline
- Edge-case and adversarial input handling (garbage, jailbreaks, missing inputs)

---

## Use Cases

- Preparing scripts for handoff to another engineer
- Ensuring internal tools meet documentation standards
- Auditing legacy scripts before refactoring
- Improving supportability for automation teams
- Creating consistent documentation across a codebase
- Integrating into CI/CD or GitHub Actions for automated reviews

---

## How It Works

The Script Documentation Reviewer operates in three modes:

### 1. REVIEW Mode (default)
Analyzes a single script and produces a full report including:
- Documentation completeness score
- Supportability score
- Maintainability score
- Weighted overall score
- Severity-based risk score
- Detailed findings
- Recommendations
- Final readiness rating

### 2. DIFF Mode
Compares two versions of a script and reports:
- Improvements
- Regressions
- Score changes
- Risk changes
- New issues introduced
- Issues resolved

### 3. REWRITE Mode
Generates missing documentation sections without modifying code:
- Header block
- Usage instructions
- Parameter descriptions
- Supportability notes
- Changelog stub
- Or all-missing sections

---

## Weighted Scoring Model

| Category                   | Weight |
|---------------------------|--------|
| Documentation Completeness | 0.40   |
| Supportability             | 0.35   |
| Maintainability            | 0.25   |

Base scores are calculated on a 0–5 scale using explicit checklists, then converted to a final 0–10 weighted score.

**Formula:**  
`overall_score = ((completeness × 0.40) + (supportability × 0.35) + (maintainability × 0.25)) × 2`

---

## Risk Scoring Engine

Each issue contributes to a cumulative risk score (capped at 100):

| Severity       | Points          |
|----------------|-----------------|
| Critical       | +25 (max 3)     |
| High           | +15             |
| Medium         | +7              |
| Low            | +3              |
| Informational  | +1 (max +5 total) |

**Risk bands:**
- **0–20:** Low Risk
- **21–50:** Moderate Risk
- **51–80:** High Risk
- **81–100:** Severe Risk

---

## Example Usage

### REVIEW Mode
    MODE: REVIEW
    SCRIPT:
    #!/bin/bash
    # Simple greeting script
    echo "Hello, $1"

### DIFF Mode
    MODE: DIFF
    OLD SCRIPT:
    ...
    NEW SCRIPT:
    ...

### REWRITE Mode
    MODE: REWRITE
    which: all-missing
    SCRIPT:
    ...

---

## GitHub Actions Integration

A ready-to-use workflow is included in `.github/workflows/doc-review.yml`.

It will:
- Detect changed `.ps1`, `.psm1`, `.py`, `.sh`, `.bash`, `.zsh` files in a PR
- Run the Reviewer in REVIEW mode
- Post a detailed report as a PR comment
- Upload the report as an artifact
- Add a `documentation-needed` label when quality is below threshold
- Fail the PR if Weighted Score < 7.0 **or** Risk Score > 50

---

## Files in this Repository

| File | Description |
|------|-------------|
| `Script Documentation Reviewer.md` | Main prompt (v1.4.1) — production-ready documentation auditor |
| `Script Documentation Generator.md` | Companion prompt for generating full documentation packages |
| `.github/workflows/doc-review.yml` | Automated PR review workflow |
| `LICENSE` | License file |

---

## Version History (Prompt)

- **v1.4.1** (2026-09-03) — Anti-drift & resilience patch: hallucination guards, edge-case handling, section enclosure enforcement, format fallback rules
- **v1.4.0** (2026-01-27) — Granular checklists, license/testability coverage, self-adherence confirmation
- **v1.3** — Native 0–10 scoring, input validation, language notes
- **v1.2** — Initial hardened version

---

## Author

**Scott Malin, CISSP**  
Senior Cybersecurity Specialist / Security Engineer