# Early Detection of Severe Influenza Seasons Using Routine Surveillance Indicators

This repository contains a fully reproducible Python pipeline (Google Colab–ready) that downloads U.S. influenza surveillance data (CDC FluView via the Delphi EpiData API), applies a transparent baseline-referenced methodology, and automatically generates publication-quality plots and tables. All outputs are saved to a timestamped folder and packaged into a ZIP for easy sharing.

---

## 1) What this project does

Given weekly influenza-like illness (ILI) data, the code:

1. **Downloads** national-level FluView ILI data (weekly).
2. **Constructs week-specific historical baselines** using the same calendar week from previous seasons.
3. Computes:
   - Baseline mean and SD: **μₜ**, **σₜ**
   - Standardized deviation score: **Zₜ = (Yₜ − μₜ) / σₜ**
   - Threshold exceedance: **Iₜ = 𝟙{Zₜ ≥ τ}**
   - Persistence score (rolling): **Pₜ = Σⱼ Iₜ₋ⱼ** over a window **L**
4. Produces:
   - Multiple **plots** (PNG) and **tables** (CSV + HTML + Markdown)
5. **Zips** the entire output folder.

> If hospitalization data are available via the Delphi endpoint in your environment, the pipeline also standardizes hospitalizations and produces an alignment plot. If not available, the pipeline proceeds with ILI-only analysis.

---

## 2) Data source

- **CDC FluView** influenza surveillance reports (public)
- Accessed programmatically through the **Delphi Epidemiological Data API (EpiData)**

├─ analysis_colab.ipynb # (optional) Notebook version of the pipeline
├─ fluview_aim_pipeline.py # (optional) Script version of the pipeline
├─ references/ # (optional) manuscript-related references
└─ README.md


You may keep the pipeline as a notebook, a `.py` script, or both.

---

## 4) Quick start (Google Colab)

1. Open a new Colab notebook.
2. Copy–paste the pipeline code into a cell (or upload `analysis_colab.ipynb`).
3. Run all cells.

At the end, Colab will prompt you to download a ZIP file like:

`FLUVIEW_AIM_RUN_YYYYMMDD_HHMMSS.zip`

---

## 5) Quick start (local machine)

### Install dependencies

```bash
pip install delphi-epidata pandas numpy matplotlib scipy tabulate

---

## 3) Repository contents (suggested)

