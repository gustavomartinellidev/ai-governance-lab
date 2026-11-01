# 🔎 Third-Party AI Risk Assessment with a Decision Model

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/gustavomartinellidev/ai-governance-lab/blob/main/notebooks/002-third-party-ai-risk-screening/third-party-ai-risk-screening.ipynb)
&nbsp;
[📄 Screening report (PDF)](tprm_screening_report.pdf)
&nbsp;·&nbsp;
[💬 LinkedIn post](⟦link do post⟧)

> **Can a model that cannot write a sentence help screen vendor risk?**
> This notebook sends 30 answers from three fictional AI vendors to a security and AI-governance questionnaire through **Jev** (TypeSafe AI), a decision model that returns typed, calibrated judgments instead of text. A short policy in Python turns those judgments into **PASS / REVIEW / FAIL**, and a human reviews the gray zone. The result is a screening layer with human oversight by design.

<p align="center">
  <img src="cover_linkedin.png" alt="Third-party AI screening with a decision model: 30 vendor answers, 5 need a human" width="760">
</p>

## 🧭 How it works

| Step | Who decides | What happens |
|---|---|---|
| 1. Judge | **The model** | For each answer, Jev returns 4 typed answers: *addresses the control?* (probability), *type of evidence* (none / claimed / referenced), *specificity* (0–2) and *red flag?* (probability) |
| 2. Decide | **The code** | An explicit, versioned policy maps those numbers to PASS / REVIEW / FAIL, with a gray zone (0.30–0.70) that always goes to a human |
| 3. Review | **A person** | The review queue and the findings are read by an assessor; PASS answers are spot-checked by sampling |

## 🗺️ What's inside

| Section | What it does | Governance question |
|---|---|---|
| 1. Setup | SDK, API key from Colab Secrets, pinned model version | *Can the result be reproduced? Is the key handled safely?* |
| 2. The Scenario | 10 controls mapped to ISO/IEC 27001, 42001, 27701, NIST AI RMF, EU AI Act; 30 synthetic vendor answers | *What are we assessing, against which standards?* |
| 3. The Decision Model | What Jev is; Noul, Choice and Score; the 4 questions | *What is the system, and what can it output?* |
| 4. Running the Screening | One call per answer; decision log with model, hash, timestamp, latency, tokens | *Is every judgment traceable?* |
| 5. The Decision Policy | PASS / REVIEW / FAIL thresholds in code; human review queue | *Who decides: the model, the code or a human?* |
| 6. Vendor Risk Tiers | Aggregation per vendor, critical controls, chart, LinkedIn cover | *Can we communicate the result clearly?* |
| 7. Assessment Report | Plain-text and PDF screening report, CSV and JSON logs | *Can a non-technical reviewer understand and file it?* |

## 📊 Reference run

| | |
|---|---|
| Model | `jev-1.13.0` (TypeSafe AI), pinned |
| Scope | 30 answers · 3 fictional vendors · 10 controls |
| Result | **8 PASS · 5 REVIEW · 17 FAIL** |
| Human review queue | 5 of 30 answers (17%) |
| Vendor tiers | Aurora Desk AI: Low · Helix Assist: High · Quill Support: High |
| Marketing-style answers | 0.02–0.09 on *addresses the control*, 10 out of 10 |
| "We train on customer data" | Red-flag probability 0.97 |
| Median latency | 88 ms per answer (p90 124 ms) |
| Cost | 20,551 input tokens ≈ USD 0.0009 |

*Jev is a remote model; its answers may change between versions. The model version, a hash of every input and the full typed responses are logged so a run can be audited and compared later.*

## ▶️ How to run

1. Create a TypeSafe API key at [typesafe.ai](https://typesafe.ai) and add it to Colab **Secrets** (🔑 icon) as `TYPESAFE_API_KEY`.
2. Click **Open in Colab** above and select `Runtime → Run all` (30 API calls, about 1 minute, no GPU, a fraction of a cent).
3. The last cell downloads the outputs to your computer.

The notebook is published **with outputs saved**, so you can read every result without running it. To experiment, change the thresholds in Section 5.1 (`REVIEW_BAND`, `RED_FLAG_FAIL`) or replace the synthetic answers in Section 2.2 with your own **non-confidential** examples.

## 📁 Files

| File | Description |
|---|---|
| [`third-party-ai-risk-screening.ipynb`](third-party-ai-risk-screening.ipynb) | The notebook, with outputs |
| [`tprm_screening_report.pdf`](tprm_screening_report.pdf) | The formatted screening report |
| [`vendor_screening.png`](vendor_screening.png) | Chart: PASS / REVIEW / FAIL per vendor |
| [`cover_linkedin.png`](cover_linkedin.png) | Cover image used in the LinkedIn post |

## 🏛️ Why this matters for AI governance

- **ISO/IEC 42001, Annex A.10:** third-party and customer relationships; **A.6.2.8:** event logging; **A.9.2–A.9.4:** responsible use and human oversight.
- **ISO/IEC 27001, Annex A 5.19–5.22:** supplier relationships and monitoring of supplier services.
- **NIST AI RMF, GOVERN 6 and MAP 4:** policies and risk mapping for third-party AI components.
- **EU AI Act, Art. 13, 14 and 26:** transparency to deployers, human oversight, and deployer obligations.

Typed outputs make every judgment loggable and contestable; keeping the policy in code makes human oversight a mechanism rather than a promise. This is a screening layer that ranks attention, not a compliance verdict.

## ⚠️ Limitations

- **Screening ≠ assessment.** No SOC 2 report, contract or configuration was reviewed; the output is a prioritized reading list for a human assessor.
- **The model can be wrong.** Probabilities are estimates; calibration should be checked on your own data before trusting any threshold.
- **Synthetic vendors.** All three vendors and all 30 answers are fictional. Real questionnaires are longer and messier.
- **Confidentiality.** Real vendor material often cannot be sent to another third-party API; check your contracts first. The screening tool is itself a third party.
- Educational material, **not legal advice**.
---

**Gustavo Martinelli** · AI Engineer & AI Governance Specialist · [LinkedIn](https://www.linkedin.com/in/gustavomartinelli/)

*Part of [AI Governance Lab](../../README.md). Feel free to copy, adapt and share, with attribution.*

## ⭐ Support this project

If these notebooks are useful to you:
- **Star this repository**: it helps more people find it.
- **Follow me** on [GitHub](https://github.com/gustavomartinellidev) and [LinkedIn](https://www.linkedin.com/in/gustavomartinelli/) for new notebooks.
- **Share** a notebook with someone working on AI or AI governance.
