# Data Dictionary (Processed)


## btc_monthly_close_2020_2025.csv

| column   | dtype          | unit          | role           | description                                     |
|:---------|:---------------|:--------------|:---------------|:------------------------------------------------|
| BTC_USD  | float64        | USD           | feature(level) | Monthly Bitcoin price (USD), end-of-month close |
| Date     | datetime64[ns] | YYYY-MM (EOM) | key(time)      | End-of-month timestamp (EOM)                    |

## gold_monthly_clean_2020_2025.csv

| column   | dtype          | unit          | role           | description                                  |
|:---------|:---------------|:--------------|:---------------|:---------------------------------------------|
| Gold_USD | float64        | USD           | feature(level) | Monthly gold price (USD), end-of-month close |
| Date     | datetime64[ns] | YYYY-MM (EOM) | key(time)      | End-of-month timestamp (EOM)                 |

## merged_gold_btc_monthly_2020_2025.csv

| column   | dtype          | unit          | role           | description                  |
|:---------|:---------------|:--------------|:---------------|:-----------------------------|
| BTC_USD  | float64        | USD           | feature(level) | Merged BTC_USD at EOM        |
| Gold_USD | float64        | USD           | feature(level) | Merged Gold_USD at EOM       |
| Date     | datetime64[ns] | YYYY-MM (EOM) | key(time)      | End-of-month timestamp (EOM) |

## monthly_returns_gold_btc_2020_2025.csv

| column   | dtype          | unit                  | role            | description                         |
|:---------|:---------------|:----------------------|:----------------|:------------------------------------|
| BTC_USD  | float64        | USD                   | feature(level)  |                                     |
| Gold_USD | float64        | USD                   | feature(level)  |                                     |
| BTC_ret  | float64        | log return (unitless) | feature(return) | Month-over-month log return of Btc  |
| Gold_ret | float64        | log return (unitless) | feature(return) | Month-over-month log return of Gold |
| Date     | datetime64[ns] | YYYY-MM (EOM)         | key(time)       | End-of-month timestamp (EOM)        |