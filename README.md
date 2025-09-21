# CognitiMag — AI-Cognitive Coach for ADHD & ASD

> ⚠️ **Disclaimer:** This is a research prototype of an assistive/learning tool. It is **not** a medical device and **does not** provide clinical advice.

[![License](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](./LICENSE)
![Python](https://img.shields.io/badge/python-3.10–3.12-informational)

---

## Table of Contents
1. [About](#about)
2. [Key Features](#key-features)
3. [Architecture (at a glance)](#architecture-at-a-glance)
4. [Quick Start](#quick-start)
5. [Repository Structure](#repository-structure)
6. [Configuration](#configuration)
7. [Metrics & Evaluation](#metrics--evaluation)
8. [Safety & Advice Policy](#safety--advice-policy)
9. [Privacy & Data](#privacy--data)
10. [Accessibility](#accessibility)
11. [Roadmap](#roadmap)
12. [Contributing](#contributing)
13. [License](#license)
14. [Links & Citation](#links--citation)
15. [FAQ](#faq)

---

## About
**CognitiMag** is a trustworthy conversational AI coach that helps neurodiverse users (ADHD/ASD) with planning, focus, and daily routines. Technical highlights:
- **On-device personalization** with privacy-preserving updates.
- **Stable explanations** (user-facing rationales) with measurable interpretability.
- **Safety pipeline** (offline red-teaming, refusal/deflection rules, human-in-the-loop review) tracked by explicit metrics.

> Scope is assistive/learning support. No clinical claims, no diagnosis, no treatment.

---

## Key Features
- 🧭 **Personalized prompts & routines** tuned to user preferences.
- 🔒 **Privacy-by-design:** defaults avoid PHI/PII; telemetry is opt-in only.
- 🛡️ **Trust & Safety:** measurable TIR/APVR; guardrails for sensitive topics.
- ♿ **Accessibility-aware UX:** WCAG-aligned patterns to reduce cognitive load.

---

## Architecture (at a glance)
- **Personalization:** constrained contextual bandits with per-user preference embeddings.
- **Explanations:** rationale generator with stability constraints (consistency under paraphrase/perturbation).
- **Safety:** two-stage shields (classifier + rules for refusal/deflection), offline red-team suite.
- **Runtime:** on-device/local by default; optional TEE/federated learning.
  
_Add an optional diagram at `docs/architecture.png`._

---

## Quick Start

### 1) Prerequisites
- **OS:** Linux / macOS / Windows  
- **Python:** 3.10–3.12  
- **Optional:** CUDA 12.x for acceleration

### 2) Clone & setup
git clone https://github.com/<org>/CognitiMag.git
cd CognitiMag
python -m venv .venv; .\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python -m src.demo
