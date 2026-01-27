# Script Documentation Reviewer

A cross‑language documentation auditor for PowerShell, Python, Bash, and other scripting languages. Designed to ensure your scripts are supportable, maintainable, and handoff‑ready — even years after you wrote them.

This tool evaluates documentation quality, identifies gaps, computes weighted scores, assigns severity levels, and can even generate missing documentation sections on demand.

---

## 📌 Features

- Multi‑language support (PowerShell, Python, Bash, etc.)
- Weighted scoring model for documentation, supportability, and maintainability
- Risk scoring engine modeled after enterprise security tooling
- Markdown or HTML report output
- Documentation diff mode for comparing script versions
- Rewrite mode to generate missing documentation sections
- Strict, deterministic output format
- Governance‑ready structure with versioning and changelog discipline

---

## 🚀 Use Cases

- Preparing scripts for handoff to another engineer  
- Ensuring internal tools meet documentation standards  
- Auditing legacy scripts before refactoring  
- Improving supportability for automation teams  
- Creating consistent documentation across a codebase  
- Integrating into CI/CD or GitHub Actions for automated reviews  

---

## 🧠 How It Works

The Script Documentation Reviewer operates in three modes:

### 1. REVIEW Mode (default)
Analyzes a single script and produces a full report including:
- Documentation completeness score  
- Supportability score  
- Maintainability score  
- Weighted overall score  
- Severity‑based risk score  
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

---

## 📊 Weighted Scoring Model

| Category                   | Weight |
|---------------------------|--------|
| Documentation Completeness | 0.40   |
| Supportability             | 0.35   |
| Maintainability            | 0.25   |

The final score is normalized to a 0–10 scale.

---

## ⚠️ Risk Scoring Engine

Each issue contributes to a cumulative risk score:

| Severity       | Points |
|----------------|--------|
| Critical       | +25    |
| High           | +15    |
| Medium         | +7     |
| Low            | +3     |
| Informational  | +1 (max +5 total) |

Risk bands:
- **0–20:** Low Risk  
- **21–50:** Moderate Risk  
- **51–80:** High Risk  
- **81–100:** Severe Risk  

---

## 🧩 Example Usage

### REVIEW Mode
