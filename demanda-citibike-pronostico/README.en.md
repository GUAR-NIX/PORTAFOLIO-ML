🇪🇸 [Español (full version)](README.md) · 🇬🇧 **English (summary)**

# 🚲 How many bikes will leave each station tomorrow? Demand forecast by station and hour (Citi Bike + weather)

Citi Bike moves tens of thousands of bikes a day and every night it must **rebalance**: take bikes to the stations that will
run empty at tomorrow's peak hours. That requires knowing, **the night before**, how many **departures** each station will have
in each hour of the next day. A **global LightGBM model** is trained on **44.3 million trips** (2024) and weather data.

## Results (final test: 28 days, 3–31 December 2024; forecast issued at midnight for the next 24 hours)

| Question | Answer |
|---|---|
| Can tomorrow's demand be predicted by station and hour? | **Yes**: WAPE **50.6%** vs. **72.9%** for the seasonal baseline (**−30.6%**) and 62.0% for "same hour yesterday" |
| Is it robust over time? | It beats the seasonal baseline in the 4 weeks of a rolling-origin backtest; mean WAPE **38.4%** vs. 54.4% |
| How much is lost by forecasting a day ahead? | The 1-hour-ahead model reaches **42.3%**, but it is useless for planning the night before |
| Does weather add signal? | **Yes**: without weather WAPE rises to **58.2%** and bias to +22.6% |
| Which variables drive the prediction? | SHAP: demand history 48.5%, **weather 24.6%**, calendar 20.0% |
| How reliable are the intervals? | Actual coverage **75.1%** (nominal 80%): a bit too narrow |
| What does the business gain? | If a missed peak costs more than **3.5** false alarms, it pays to alert with the p90 quantile (recall 58.1%) |

**Data engineering highlights:** DuckDB aggregates 8.7 GB of CSV in streaming; the download is idempotent and resumable; the
main model only uses lags of **24 h or more**, and a test alters the previous 24 h and checks that its variables do not change;
WAPE is used because MAPE explodes with zero demand.

**Documented limitation:** *actual* weather is used as a stand-in for the 24-hour weather forecast, so real-world error would be
higher.

**Architecture, figures, API, app and reproduction commands:** [full README (Spanish)](README.md). Commands are
language-independent.
