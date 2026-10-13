# Taxi Demand Forecasting

## Business Problem

Ride-hailing platforms lose money two ways: too few drivers during demand spikes (surge pricing, lost rides) and too many during quiet hours (idle driver costs). This project forecasts **hourly taxi demand** so driver supply can be matched to expected demand, especially around peak hours.

## Data

26,500 ten-minute-interval taxi order records with timestamps, resampled to **hourly demand** (~4,400 hourly rows covering multiple weeks of operations).

Features engineered from the timestamp: lag features, rolling means, and calendar flags (hour of day, day of week, holidays).

## Approach

1. **Exploratory analysis** — demand patterns by hour/day, trend and seasonality decomposition
2. **Resampling** — raw 10-minute intervals aggregated to hourly demand
3. **Feature engineering** — lag, rolling-mean, and calendar features
4. **Evaluation** — RMSE on a time-based hold-out, benchmarked against a moving-average baseline

## Results

- Final **RMSE of 53.35** on the hold-out period, benchmarked against a moving-average baseline
- The pipeline captures the strong **daily and weekly seasonality** in taxi demand
- Output is an hourly demand curve operations teams can use for driver scheduling

## Business Takeaways

- Demand is highly predictable from calendar features alone — no exotic data needed
- The biggest wins come from staffing correctly around the **evening peak**, where forecast errors cost the most
- The same pipeline generalizes to any hourly-demand problem (food delivery, support tickets, call centers)

## Tech

Python · pandas · scikit-learn · matplotlib/seaborn

## Run it

```
pip install -r requirements.txt
jupyter notebook time_series.ipynb
```
