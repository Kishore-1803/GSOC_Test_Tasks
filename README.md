<div align="center">
  <h1>🌌 DeepLense GSoC 2026 Evaluation Tests</h1>
  
  <p>
    <strong>A collection of deep learning and agentic AI solutions for strong gravitational lensing simulations.</strong>
  </p>

  <!-- Badges -->
  <img src="https://img.shields.io/badge/Python-3.9+-blue.svg" alt="Python Version" />
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?logo=pytorch&logoColor=white" alt="PyTorch" />
  <img src="https://img.shields.io/badge/Pydantic-E92063?logo=pydantic&logoColor=white" alt="Pydantic" />
  <img src="https://img.shields.io/badge/Jupyter-F37626.svg?&logo=Jupyter&logoColor=white" alt="Jupyter" />

</div>

<br />

## 📑 Table of Contents

- [Overview](#-overview)
- [Repository Structure](#-repository-structure)
- [Test I: Multi-Class Classification](#-test-i-multi-class-classification)
- [Test II: Agentic AI](#-test-ii-agentic-ai)
- [Getting Started](#%EF%B8%8F-getting-started)
- [License](#-license)

---

## 🔭 Overview

This repository contains implementations for the **DeepLense Google Summer of Code (GSoC) 2026** qualification tests. It encompasses both deep learning models for classifying dark matter substructures in gravitational lenses, as well as an agentic AI workflow orchestrating complex physics simulations through natural language.

---

## 📂 Repository Structure

```text
├── Test I/                      # Multi-Class Classification solution
│   └── deeplense_test1.ipynb    # Classification training and evaluation notebook
├── Test II/                     # Agentic AI Workflow solution
│   ├── deeplense_test2.ipynb    # Agent workflow and interaction notebook
│   └── DeepLenseSim/            # Simulation pipeline submodule
└── README.md                    # Project documentation
```

---

## 🧠 Test I: Multi-Class Classification

**Goal:** Accurately classify strong lensing images based on dark matter substructure into three distinct categories: `no` (no substructure), `sphere` (subhalo), and `vort` (vortex).

### 🚀 Methodology & Approach
We leverage a **Transfer Learning** architecture fine-tuning the **EfficientNet-B3** backbone. EfficientNet provides an unparalleled balance of parameter efficiency and feature extraction, which is ideal for scientific visual data.

*   **Data Pipeline:** Custom `PyTorch Dataset` with built-in min-max preprocessing and tensor structuring.
*   **Augmentation Strategy:** Applies random flips, 45° rotations, and color jittering to enhance generalization.
*   **Optimization:** Configured with `AdamW`, weight decay ($10^{-4}$), and **Cosine Annealing with Warm Restarts** for robust convergence.
*   **Regularization:** Employs **Label Smoothing ($0.1$)** alongside cross-entropy loss to prevent overconfidence and over-fitting on ambiguous lensing patterns.

### 📊 Evaluation Metrics
Performance is measured via:
- **ROC Curve** (Receiver Operating Characteristic) plotted *One-vs-Rest* for granular per-class tracking.
- **AUC Score** (Area Under the ROC Curve) assessing separability per substructure feature.

---

## 🤖 Test II: Agentic AI

**Goal:** Build an intelligent conversational agent using **Pydantic AI** / Orchestral AI that wraps the [DeepLenseSim](https://github.com/mwt5345/DeepLenseSim) pipeline. Allow users to trigger complex strong gravitational lensing simulations entirely via text prompts.

### 🚀 Methodology & Approach
This implementation abstracts the complexity of physics engines into a conversational interface with structured guardrails.

1.  **Semantic Parsing:** Comprehends simulation requests (e.g., *“Generate 5 vortex lenses with a resolution of 150...”*).
2.  **Schema Validation (Pydantic):** Strictly enforces typed models for simulation configurations, catching logical errors before computation.
3.  **Human-in-the-Loop (HitL):** Before triggering expensive simulations, the agent reviews parameter completeness. It automatically pauses execution to ask the user clarifying questions if required fields (like redshift variables) are omitted.
4.  **Tool Orchestration:** Programmatically configures and invokes various physics models (`Model_I`, `Model_II`, etc.) and manages file I/O for the simulated arrays.

### 💯 Success Criteria
- High-fidelity natural language comprehension and entity extraction.
- Failsafe schema validation via Pydantic output parsers.
- Seamless generation, fetching, and display of simulated lensing images.

---

## ⚙️ Getting Started

### Prerequisites

Ensure you have **Python 3.9+** and a package manager like `pip` installed. A dedicated virtual environment is highly recommended.

### Installation

1. **Clone the repository** (and grab submodules if applicable):
   ```bash
   git clone <repository-url>
   cd <repository-dir>
   ```

2. **Create and activate a virtual environment:**
   ```bash
   # Windows
   python -m venv venv
   venv\Scripts\activate

   # macOS / Linux
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install Dependencies:**
   ```bash
   pip install torch torchvision timm scikit-learn numpy matplotlib seaborn pydantic jupyter
   ```

4. **Verify Datasets:**
   Ensure the lensing simulated datasets are extracted and placed within the root `dataset/` directory before running Test I.

### Running the Notebooks

Launch Jupyter Notebook or use standard VS Code integrated notebooks:
```bash
jupyter notebook
```
Navigate to `Test I/deeplense_test1.ipynb` or `Test II/deeplense_test2.ipynb` to execute the steps interactively.

---

## 📜 License

This project is licensed under the [MIT License](LICENSE) - see the LICENSE file for details.
