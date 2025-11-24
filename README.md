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
├─ references/     # Notes and citation files (e.g., .bib)
├─ environment/    # requirements.txt / environment.yml
```

## Expected Raw Inputs
**Place these in `data/raw/`:**

- **`gold_monthly_price.csv`**  
  Columns:  
  - `Date` (YYYY-MM)  
  - `Price` (USD)

- **`btc-hourly-price_2015_2025.csv`**  
  Columns:  
  - `TIME_UNIX` (epoch seconds or ms)  
  - `CLOSE_PRICE` (USD)

---

## Workflow
1. **01_Audit_Raw.ipynb** — Inspect schema, date ranges, missing values, duplicates.  
2. **02_Clean_Gold.ipynb** — Parse & standardize monthly gold prices, set EOM index, filter 2020–2025.  
3. **03_Clean_Btc.ipynb** — Convert BTC hourly → monthly end-of-month close, align time zone, filter 2020–2025.  
4. **04_Merge_Align.ipynb** — Inner-join Gold & BTC on EOM; ensure matched months only.  
5. **05_EDA.ipynb** — Plot levels (optionally log-scaled) and compute monthly log-returns; save figures/tables.  
6. **06_Correlation.ipynb** — Pearson correlation (with 95% CI via Fisher z), rolling 6M/12M correlations; save summary tables and plots.  
7. **07_Freeze_QC.ipynb** — Freeze final datasets to `data/processed/` and print quick QC summaries.  
8. **08_Exports.ipynb** — Export final publication figures/tables used in the report.  
9. **09_Robustness.ipynb** — Robustness checks: Spearman (rank), rolling-window sensitivity, alternative sub-periods, light winsorization (1%), and optional lead–lag test.  
10. **10_Data_Dictionary.ipynb** — Auto-generate a simple data dictionary for all processed files.

---

## Naming Conventions
- Use ISO dates: `YYYY-MM-DD` in filenames and date columns where applicable.  
- Keep **raw** files immutable; create new versions in `interim/` or `processed/`.  
- Examples:
  - `data/raw/monthly_gold.csv`
  - `data/interim/gold_monthly_clean_2020_2025.csv`
  - `data/processed/monthly_returns_gold_btc_2020_2025.csv`

---

## Environment & Setup
- Python version: 3.13.8 (or compatible 3.10+)
- Install dependencies:
  ```bash
  pip install -r environment/requirements.txt
  ```

## Methods References
- **Pearson correlation & p-value:** `scipy.stats.pearsonr` (SciPy docs)  
- **Spearman correlation:** `scipy.stats.spearmanr` (SciPy docs)  
- **Fisher r→z CI:** standard formula (Fisher, 1921)  
- **Rolling correlation:** `pandas.Series.rolling().corr()`  
- **Bootstrap CI:** non-parametric **paired** resampling of `(X, Y)`  
- **Winsorization:** clip at {1%, 99%} quantiles  
- **Jackknife:** leave-one-out Δr

---

## Reproducibility
1. Create a virtual environment and install dependencies:  
   `pip install -r environment/requirements.txt`
2. Run notebooks **01 → 10** from the repo root.
3. Artifacts are written to:
   - `data/interim`, `data/processed`
   - `reports/figures`, `reports/tables`
4. For identical numbers (e.g., bootstrap), use random seed **42** and the same **end-of-month (EOM)** alignment.

---

## Data Governance & Ethics (brief)
- Note data sources, licenses, and key transformations (e.g., BTC hourly → EOM monthly close).  
- Document decisions affecting interpretation (e.g., inner join removing months with missing series).  
- Keep raw data unmodified; all changes happen in `interim/` or `processed/`.

---

## Citations & Provenance

**Data**
- Gold monthly prices — DataHub “Gold Prices” (PDDL).  
- Bitcoin hourly OHLCV — Mouad Jaouhari “bitcoin-hourly-ohclv-dataset” (MIT).

**APIs / Methods**
- pandas (time series / resampling / rolling correlation)  
- NumPy (log, vectorized operations)  
- SciPy (`pearsonr`, `spearmanr`)  
- Fisher (1921) — r-to-z CI formula

**GenAI disclosure**  
Some wording for comments/captions and code-structuring tips were assisted by ChatGPT (model: **GPT-5 Thinking**). All core code was authored/verified by the author and relies on official pandas/NumPy/SciPy APIs.