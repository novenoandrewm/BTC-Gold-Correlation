# CA1 — Bitcoin × Gold Correlation (ATU Data Science)

This repository contains all files for the CA1 assignment investigating the statistical relationship between Bitcoin (BTC) prices and Gold prices.

## Project Layout
```
CA1-BTC-Gold-Correlation/
├─ data/
│  ├─ raw/         # Original, immutable datasets (never edit these)
│  ├─ interim/     # Intermediate cleaned/reshaped data
│  └─ processed/   # Final analysis-ready datasets (used in notebooks/figures)
├─ notebooks/      # Jupyter Notebooks in numbered workflow order
├─ src/            # Reusable Python modules for data loading/cleaning/plots 
├─ reports/
│  ├─ figures/     # Images exported from notebooks
│  ├─ tables/      # CSV/LaTeX tables exported from notebooks
│  └─ slides/      # PowerPoint/Slides for presentation
├─ references/     # PDFs, notes, and citation files (e.g., .bib)
├─ environment/    # requirements.txt / environment.yml
└─ logs/           # Any logs from scripts or runs
```

## Workflow
1. **01_data_audit.ipynb** — Inspect data structure, date ranges, missing values.
2. **02_clean_gold.ipynb** — Clean & standardize monthly gold prices.
3. **03_clean_btc.ipynb** — Resample BTC prices to monthly, align with gold.
4. **04_merge_resample.ipynb** — Merge Gold & BTC, ensure matching months.
5. **05_eda_visuals.ipynb** — Visualize levels & returns.
6. **06_correlation.ipynb** — Compute correlations (Pearson/Spearman) on monthly returns; rolling windows and crisis sub-periods.

## Naming Conventions
- Use ISO dates: `YYYY-MM-DD` in filenames and columns.
- Keep **raw** files immutable; create new versions in `interim/` or `processed/`.
- Examples:
  - `data/raw/monthly_gold.csv`
  - `data/processed/gold_monthly_2020_2025.csv`
  - `data/processed/btc_monthly_2020_2025.csv`

## Reproducibility
- Python version: 3.10+
- Install dependencies:
  ```bash
  pip install -r environment/requirements.txt
  ```

## Notes
- Document all cleaning rules in the notebooks (cell-by-cell).
- Prefer correlations on **monthly returns** (pct-change or log returns) rather than price levels.
- Keep figures/tables exported to `reports/` for easy inclusion in the CA1 report.
