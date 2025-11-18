# Data Dictionary (Processed)


## btc_monthly_close_2020_2025.csv

| column   | dtype          | unit          | role           | description                                 |
|:---------|:---------------|:--------------|:---------------|:--------------------------------------------|
| Date     | datetime64[ns] | YYYY-MM (EOM) | key(time)      | End-of-month timestamp (EOM)                |
| BTC_USD  | float64        | USD           | feature(level) | Monthly BTC price (USD), end-of-month close |

## gold_monthly_clean_2020_2025.csv

| column   | dtype          | unit          | role           | description                                  |
|:---------|:---------------|:--------------|:---------------|:---------------------------------------------|
| Date     | datetime64[ns] | YYYY-MM (EOM) | key(time)      | End-of-month timestamp (EOM)                 |
| Gold_USD | float64        | USD           | feature(level) | Monthly gold price (USD), end-of-month close |

## merged_gold_btc_monthly_2020_2025.csv

| column   | dtype          | unit          | role           | description                  |
|:---------|:---------------|:--------------|:---------------|:-----------------------------|
| Date     | datetime64[ns] | YYYY-MM (EOM) | key(time)      | End-of-month timestamp (EOM) |
| Gold_USD | float64        | USD           | feature(level) | Merged Gold_USD at EOM       |
| BTC_USD  | float64        | USD           | feature(level) | Merged BTC_USD at EOM        |

## monthly_returns_gold_btc_2020_2025.csv

| column   | dtype          | unit                  | role            | description                           |
|:---------|:---------------|:----------------------|:----------------|:--------------------------------------|
| Date     | datetime64[ns] | YYYY-MM (EOM)         | key(time)       | End-of-month timestamp (EOM)          |
| Gold_USD | float64        | USD                   | feature(level)  |                                       |
| BTC_USD  | float64        | USD                   | feature(level)  |                                       |
| Gold_ret | float64        | log return (unitless) | feature(return) | Log return of Gold (month-over-month) |
| BTC_ret  | float64        | log return (unitless) | feature(return) | Log return of Btc (month-over-month)  |