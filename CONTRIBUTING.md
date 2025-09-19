# Contributing to CognitiMag — AI-Cognitive Coach for ADHD & ASD

🎉 Thanks for your interest in contributing! This document explains how to propose changes, file issues, and submit pull requests (PRs) in a safe, privacy-preserving, and accessible way.

> **Non-medical:** CognitiMag is an assistive/learning research project. It is **not** a medical device and must not provide clinical advice.

---

## Table of Contents
- [Code of Conduct](#code-of-conduct)
- [Before You Start](#before-you-start)
- [Development Setup](#development-setup)
- [Style, Linting, and Tests](#style-linting-and-tests)
- [Commit Messages](#commit-messages)
- [Branching & PR Process](#branching--pr-process)
- [Privacy & Safety Requirements](#privacy--safety-requirements)
- [Data & Model Contributions](#data--model-contributions)
- [Documentation Contributions](#documentation-contributions)
- [Accessibility Guidelines](#accessibility-guidelines)
- [Security Policy](#security-policy)
- [Licensing & DCO](#licensing--dco)
- [Community & Support](#community--support)

---

## Code of Conduct
By participating, you agree to uphold our Code of Conduct.

- See: `CODE_OF_CONDUCT.md` (create one if missing; you can use the Contributor Covenant).
- Be respectful and inclusive; assume good intent.

---

## Before You Start
1. **Check existing issues/PRs** to avoid duplication.
2. **Open a GitHub Issue** for new features/bugs and discuss the approach.
3. Make sure your proposal aligns with project goals:
   - Trustworthy AI (safety, robustness, interpretability).
   - Privacy-by-design (no PHI/PII by default).
   - Cognitive accessibility (WCAG-aligned UX).

---

## Development Setup

### 1) Clone & Environment

    git clone https://github.com/<org>/CognitiMag.git
    cd CognitiMag

    # Python 3.10–3.12
    python -m venv .venv
    # macOS/Linux:
    source .venv/bin/activate
    # Windows (PowerShell):
    # .\.venv\Scripts\Activate.ps1

    pip install -r requirements.txt

### 2) Optional developer tools

We recommend using `pre-commit` and test tooling:

    pip install -U pip wheel
    pip install -U pytest pytest-cov black ruff pre-commit
    pre-commit install

> If you add new dev tools, update `requirements.txt` and this doc.

---

## Style, Linting, and Tests

### Code Style
- **Python:** format with **Black**; lint with **Ruff** (PEP8+ rules).
- Keep functions small and testable. Add docstrings (Google or NumPy style).

### Run checks locally

    # Format & lint
    black .
    ruff check .

    # Unit tests (with coverage)
    pytest -q --cov=src --cov-report=term-missing

### CI
- CI runs on PRs via `.github/workflows/ci.yml`.
- Aim for **≥80%** coverage on changed lines (or justify exceptions in PR).

---

## Commit Messages
Use **Conventional Commits** for clear history and easier tooling:

    <type>(optional-scope): short summary

    [optional body]

    [optional footer(s)]

**Types:** `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`.

**Examples:**

    feat(personalization): add constrained bandit policy with per-user embeddings
    fix(safety): lower TIR by tightening refusal rules on risky prompts
    docs(readme): add quick start and privacy notes

If your change fixes an issue:

    fix(eval): handle OOD split seed mismatch

    Closes #123

---

## Branching & PR Process

### Branching
Create topic branches from `main`:

    feature/<short-name>
    fix/<short-name>
    docs/<short-name>

### PR Checklist
- [ ] Issue linked (e.g., `Closes #NNN`) and clear description.
- [ ] Tests added/updated; `pytest` passes locally.
- [ ] `black .` and `ruff check .` pass.
- [ ] No PHI/PII or secrets in code, tests, or fixtures.
- [ ] Updated docs (`README.md`, `CHANGELOG.md` if applicable).
- [ ] Screenshots or small demo for UX changes (if applicable).

> Keep PRs focused and reasonably small. Large or cross-cutting changes should be split into smaller PRs.

---

## Privacy & Safety Requirements

**Mandatory for all contributions:**
- 🚫 **No PHI/PII** in code, configs, logs, sample data, or tests.
- ✅ Use **synthetic** or **de-identified** examples only.
- 🔒 Default mode must be **on-device/local**; any telemetry must be **opt-in** and aggregated (DP optional).
- 🛡️ Do not weaken safety guardrails. Changes affecting refusal/deflection logic must include updated tests and evaluation results (see `safety/safety_metrics.md`).
- 🧪 If your change touches safety, run the offline red-team suite (when available) and report TIR/APVR deltas in the PR.

Env example for local dev:

    COGNITIMAG_MODE=local
    COGNITIMAG_TELEMETRY=off
    COGNITIMAG_SAFETY_STRICT=on
    COGNITIMAG_DEVICE=cpu

---

## Data & Model Contributions

### Datasets
- Provide a `DATASET_CARD.md` including:
  - **Provenance & license**
  - **Intended use** and limitations
  - **De-identification** and privacy notes
  - **Known biases** and evaluation caveats
- Include a small **toy sample** (synthetic) for tests, or provide a script to generate it.
- Large files: do **not** commit to Git; use a storage bucket or release artifact.

### Models
- Provide a `MODEL_CARD.md` with:
  - **Training data** summary, **intended use**, **limitations**
  - **Safety considerations** (e.g., risk of harmful advice)
  - **Evaluation**: robustness, TIR/APVR, explanation metrics
- Ensure license compatibility and include citation if required.

---

## Documentation Contributions
- Keep `README.md` concise and task-oriented.
- Add module-level docstrings and inline comments for complex logic.
- For notable changes, update `CHANGELOG.md` (if present).

---

## Accessibility Guidelines
If you change UI/UX or user-facing strings:
- Follow the **WCAG** checklist in `accessibility/a11y_checklist.md`.
- Prefer **plain language** and predictable flows.
- Provide labels/ARIA attributes and sufficient contrast.
- Avoid cognitive overload; chunk tasks into steps.

---

## Security Policy
- **Do not** report vulnerabilities via public issues.
- Email **security@<your-domain>** (or use GitHub Security Advisories).
- Include steps to reproduce and environment details.
- We practice coordinated disclosure and will credit reporters where appropriate.

---

## Licensing & DCO
- By contributing, you agree your changes are licensed under:
  - **Code:** Apache-2.0 (see `LICENSE`)
  - **Docs/Assets:** CC BY 4.0 (if applicable)
- Use the **Developer Certificate of Origin (DCO)**. Sign your commits:

    git commit -s -m "feat: add stable explanation generator"

This adds a `Signed-off-by: Your Name <you@example.com>` line.

> If your organization requires a CLA, maintainers will provide details during PR review.

---

## Community & Support
- Issues: GitHub **Issues** for bugs/features.
- Discussions: GitHub **Discussions** (if enabled) or open an issue first.
- Releases & Roadmap: see `README.md` and project boards.

💙 Thanks for helping make CognitiMag safer, more private, and more accessible!
