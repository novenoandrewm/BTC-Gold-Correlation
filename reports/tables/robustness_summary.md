# Robustness Summary

**Sample**: N = 66 months (2020-02-29 → 2025-07-31)

**Pearson r** = -0.069 (p = 0.584)  
Fisher 95% CI = [-0.306, 0.176]  
Bootstrap 95% CI = [-0.311, 0.195]

**Spearman ρ** = -0.053 (p = 0.675)

**Winsorize 1%**: r = -0.068 (Δ vs original = +0.001)  
**Jackknife** r_without ∈ [-0.107, -0.020]  
Top-10 influence plot: reports/figures/jackknife_top10.png

**Rolling windows** → reports/tables/robustness_rolling_windows.csv  
**Cross-corr (lags)** → reports/tables/robustness_crosscorr_lags.csv  
Figure: reports/figures/crosscorr_lags.png (★ p<0.05)
