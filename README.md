# Taxi Demand Forecasting

## Business Problem
Ride-hailing platforms lose money two ways: too few drivers during demand spikes (surge pricing, lost rides) and too many during quiet hours (idle driver costs). This project forecasts **hourly taxi demand** so driver supply can be matched to expected demand, especially around peak hours.

## Data
Hourly taxi order counts with timestamps, covering multiple weeks of operations. Features engineered from the timestamp: hour of day, day of week, holiday flags.

## Approach
1. **Exploratory analysis** — demand patterns by hour/day, trend and seasonality decomposition
2. **Stationarity checks** — ADF test, differencing where needed
3. **Modeling** — ARIMA family models, tuned via AIC; train/test split on time
4. **Evaluation** — MAE on the hold-out period vs. a naive baseline

## Results
- Model captures the strong **daily and weekly seasonality** in taxi demand
- Forecasts track peak-hour surges (morning/evening rush) that a naive average would miss
- Output is an hourly demand curve operations teams can use for driver scheduling

## Business Takeaways
- Demand is highly predictable from calendar features alone — no exotic data needed
- The biggest wins come from staffing correctly around the **evening peak**, where forecast errors cost the most
- The same pipeline generalizes to any hourly-demand problem (food delivery, support tickets, call centers)

## Tech
Python · pandas · statsmodels (ARIMA) · matplotlib/seaborn

## Run it
```bash
pip install -r requirements.txt
jupyter notebook time_series.ipynb
```
