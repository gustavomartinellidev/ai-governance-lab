# 🧠 Inside a Neural Network: One Decision, Layer by Layer
 
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/gustavomartinellidev/ai-governance-lab/blob/main/notebooks/001-inside-a-neural-network/inside-a-neural-network.ipynb)
&nbsp;
[📄 Explainability report (PDF)](explainability_report.pdf)
&nbsp;·&nbsp;
[💬 LinkedIn post](LINKEDIN_POST_URL)
 
> **Can we explain why an AI made a decision?**
> This notebook trains a small neural network, asks it to make one decision, and opens it up to show *why* it decided that way: layer by layer, neuron by neuron. It then turns that explanation into a plain-language report a non-technical reviewer can read.
 
<p align="center">
  <img src="decision_path.gif" alt="Animated decision path through a neural network" width="760">
</p>

## 🎨 How to read the animation
 
| Element | Meaning |
|---|---|
| 🟠 Orange line | An active signal; thicker means a larger contribution |
| 🔵 Blue line | The **decision path**, the route that pushed hardest toward the answer |
| ⚪ Light gray neuron | An **inactive** neuron for this input (ReLU output = 0) |
| Darker orange fill | A stronger value or activation |
 
## 🗺️ What's inside
 
| Section | What it does | Governance question |
|---|---|---|
| 1. Setup | Libraries and fixed random seeds | *Can the result be reproduced?* |
| 2. The Data | Iris dataset, train/test split, standardization | *What was the model trained on?* |
| 3. The Model | A 4 → 5 → 3 neural network (43 parameters) | *What exactly is the system?* |
| 4. Training | Training, test accuracy, model fingerprint | *How well does it perform? Which version is it?* |
| 5. Opening the Black Box | Forward hooks, decision path, feature influence | *Why did it decide this?* |
| 6. Explainability Report | Plain-language report | *Can a non-technical reviewer understand it?* |
| 7. Visualizing the Decision | Animated GIF and formatted PDF report | *Can we communicate it clearly?* |
 
## 📊 Reference run
 
| | |
|---|---|
| Test accuracy | 93.3% (30 unseen flowers) |
| Case explained | Test sample #1, the least-confident *correct* decision |
| Prediction | **Virginica**, 74.3% confidence (correct) |
| Main reasons | Petal length (48%) and petal width (46%) |
| Decision path | Petal length → H5 → Virginica |
 
*Results are reproducible thanks to fixed seeds. Different hardware or PyTorch versions may produce small differences.*
 
## ▶️ How to run
 
1. Click **Open in Colab** above.
2. Select `Runtime → Run all` (about 1 minute, no GPU needed).
3. The last cell downloads the outputs to your computer.
To explain a different flower, change `SAMPLE_INDEX` in Section 5.1. The notebook also lists the flowers the model got **wrong**, which are interesting cases to explore.
 
## 📁 Files
 
| File | Description |
|---|---|
| [`inside-a-neural-network.ipynb`](inside-a-neural-network.ipynb) | The notebook, with outputs |
| [`decision_path.gif`](decision_path.gif) | The animated decision path |
| [`explainability_report.pdf`](explainability_report.pdf) | The formatted explainability report |
 
## 🏛️ Why this matters for AI governance
 
- **LGPD (Brazil), Art. 20:** the right to review automated decisions and to receive clear information about their criteria and procedures.
- **EU AI Act, Art. 86:** the right to an explanation of individual decisions made with high-risk AI systems.
- **GDPR, Art. 22:** protection against solely automated individual decisions.
A report like this is one practical building block toward those obligations, not a complete compliance solution.
 
## ⚠️ Limitations
 
- The **decision path is a simplification**: every active neuron contributes to the result.
- **Gradient × input** is a local method. Production systems should also use SHAP or Integrated Gradients.
- A model with 43 parameters can be traced neuron by neuron; large models cannot.
- Educational material, **not legal advice**.
---
 
**Gustavo Martinelli** · AI Engineer & AI Governance Specialist · [LinkedIn](https://www.linkedin.com/in/gustavomartinelli/)
 
*Part of [AI Governance Lab](../../README.md). Feel free to copy, adapt and share, with attribution.*

## ⭐ Support this project

If these notebooks are useful to you:
- **Star this repository**: it helps more people find it.
- **Follow me** on [GitHub](https://github.com/gustavomartinellidev) and [LinkedIn](https://www.linkedin.com/in/gustavomartinelli/) for new notebooks.
- **Share** a notebook with someone working on AI or AI governance.
 
