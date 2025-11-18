## Bitcoin × Gold Correlation

This repository investigates the statistical relationship between Bitcoin (BTC) prices and Gold prices over 2020–2025 using monthly data. The workflow is fully reproducible and organized for transparent auditing, cleaning, merging, exploratory analysis, and correlation testing (including robustness checks).

## Project Layout
```
CA1-BTC-Gold-Correlation/
├─ data/
│  ├─ raw/         # Original, immutable datasets (never edit these)
│  ├─ interim/     # Intermediate cleaned/reshaped data
│  └─ processed/   # Final analysis-ready datasets (used in notebooks/figures)
├─ notebooks/      # Jupyter Notebooks in numbered workflow order
├─ reports/
│  ├─ figures/     # Images exported from notebooks
│  ├─ tables/      # CSV/LaTeX tables exported from notebooks
│  └─ files/       # PDF file
├─ references/     # PDFs, notes, and citation files (e.g., .bib)
├─ environment/    # requirements.txt / environment.yml
```

## Expected Raw Inputs
**Place these in data/raw/:**
  - gold_monthly_price.csv
   Columns: Date (YYYY-MM), Price (USD)
  - btc-hourly-price_2015_2025.csv
   Columns: TIME_UNIX (epoch seconds or ms), CLOSE_PRICE (USD)

## Workflow
1. **01_data_audit.ipynb** — Inspect schema, date ranges, missing values, duplicates.
2. **02_clean_gold.ipynb** — Parse & standardize monthly gold prices, set EOM index, filter 2020–2025.
3. **03_clean_btc.ipynb** — Convert BTC hourly → monthly end-of-month close, align time zone, filter 2020–2025.
4. **04_merge_align.ipynb** — Inner-join Gold & BTC on EOM; ensure matched months only.
5. **05_eda_visuals.ipynb** —  Plot levels (often log-scaled) and compute monthly log returns; save basic figures and tables.
6. **06_correlation.ipynb** — Pearson correlation (with 95% CI via Fisher z), rolling 6M/12M correlations; save summary tables and plots.
7. **07_freeze_qc.ipynb** — Freeze final datasets to data/processed/ and print quick QC summaries.
8. **08_exports.ipynb** — Export final publication figures/tables used in the report.
9. **09_robustness.ipynb** — Robustness checks: Spearman (rank), rolling window sensitivity (6/12M), alternative sub-periods, light winsorization (1%), and optional lead–lag test.
10. **10_data_dictionary.ipynb** — Auto-generate a simple data dictionary for all processed files.

## Naming Conventions
- Use ISO dates: `YYYY-MM-DD` in filenames and date columns where applicable.
- Keep **raw** files immutable; create new versions in `interim/` or `processed/`.
- Examples:
  - `data/raw/monthly_gold.csv`
  - `data/interim/gold_monthly_clean_2020_2025.csv`
  - `data/processed/monthly_returns_gold_btc_2020_2025.csv`

## Environment & Setup
- Python version: 3.13.8
- Install dependencies:
  ```bash
  pip install -r environment/requirements.txt
  ```

## Notes
- Document all cleaning rules in the notebooks (cell-by-cell).
- Prefer correlations on **monthly returns** (e.g., log returns) rather than price levels to avoid spurious correlation from trends.
- Keep figures/tables exported to `reports/` for easy inclusion. 

## Data Governance & Ethics (brief)
- Note data sources, licenses, and any transformations (e.g., BTC hourly → EOM monthly close).
- Document decisions affecting interpretation (e.g., inner join removing months with missing series).