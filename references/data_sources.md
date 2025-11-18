# Data Sources

## Bitcoin hourly OHLCV (raw)
- **File used**: `data/raw/btc-hourly-price_2015_2025.csv`
- **Provider**: Mouad Jaouhari (GitHub repository “bitcoin-hourly-ohclv-dataset”).
- **Description**: Comprehensive Bitcoin hourly price dataset (2015–present) with OHLCV, intended for ML/research. MIT licensed. :contentReference[oaicite:0]{index=0}
- **Original frequency**: Hourly (epoch timestamps).
- **License**: MIT License. :contentReference[oaicite:1]{index=1}
- **Transformations applied in this project**:
  - Parsed `TIME_UNIX` to UTC datetimes (auto-detect ms vs s).
  - Deduplicated timestamps (keep last).
  - Resampled to **end-of-month close** (EOM).
  - Restricted to **2020-01 to 2025-12**.
  - Exported monthly series to `data/processed/btc_monthly_close_2020_2025.csv`.

## Gold monthly prices (raw)
- **Files used**: `data/raw/gold_monthly_price.csv`, `data/raw/gold_annual_price.csv`
- **Provider**: DataHub “core/gold-prices”. Data compiled from historical sources (Timothy Green / World Gold Council) and World Bank; updated monthly. :contentReference[oaicite:2]{index=2}
- **Original frequency**: Monthly and annual (CSV).
- **License**: **Public Domain Dedication and License (PDDL)**. :contentReference[oaicite:3]{index=3}
- **Transformations applied in this project**:
  - Parsed `Date` (YYYY-MM) and numeric `Price`.
  - Normalized to **EOM index**; dropped duplicates/NA.
  - Restricted to **2020-01 to 2025-12**.
  - Exported monthly series to `data/processed/gold_monthly_clean_2020_2025.csv`.

### Provenance Checklist
- Record SHA-256 checksums for the raw files:
  - Windows PowerShell:
    ```
    Get-FileHash data\raw\btc-hourly-price_2015_2025.csv -Algorithm SHA256
    Get-FileHash data\raw\gold_monthly_price.csv -Algorithm SHA256
    ```
