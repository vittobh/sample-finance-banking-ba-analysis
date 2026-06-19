# Sample — Finance & Banking Software BA Analysis

Personal research sample. End-to-end BA analysis for a Finance & Banking software platform: problem statement → component breakdown → analysis questions → assumptions → use case → user story → data model.

See [ANALYSIS.md](ANALYSIS.md) for the full pack.

## What this sample shows
- **Problem framing** rooted in market data (SaaS profitability + retention stats)
- **11 core component & feature breakdown** for a modern core-banking platform
- **Open-ended discovery questions** for stakeholder interviews
- **Technical assumptions** (full stack picked: ReactJS / Spring Boot / Oracle / AWS / Salesforce / Guidewire / ERPNext / SignServer)
- **Use case** (Customer Onboarding by Bank Teller, MVP1) with pre/post conditions, normal/alt courses
- **User story + acceptance criteria** in Given/When/Then with password & KYC field specs
- **Data model commentary** (separate table for image blobs, AI/CRM automation hooks)

## Today's lens
A modern take would add: agentic KYC (multi-doc OCR + extraction + sanctions + AML in one orchestration), Y-Score readiness check before launch, eval harness for hallucination / false-positive rate. See [vittobh/AI-assisted-KYC-and-customer-onboarding](https://github.com/vittobh/AI-assisted-KYC-and-customer-onboarding) and [vittobh/pm-os](https://github.com/vittobh/pm-os).

---
Author: **Vittobha Vignesh S** · License: MIT

---

## 🚀 Live Prototype
**[https://vittobh.github.io/sample-finance-banking-ba-analysis/](https://vittobh.github.io/sample-finance-banking-ba-analysis/)**

Working front-end with light + dark mode (toggle in header). Mock backend by default; add an Anthropic/Gemini/Grok key to browser localStorage to attempt live calls.

## 🤖 AI Use Cases (2026)
See **[AI_USE_CASES.md](AI_USE_CASES.md)** — agentic upgrade plan, OSS stack, concrete prompts, evals.

## ⚠️ Limitations
See **[LIMITATIONS.md](LIMITATIONS.md)** — what's mocked vs needs API keys / server proxy.
