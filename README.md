<<<<<<< HEAD
# Senior-Data-Scientist-Project
=======
# Part 1: eCommerce Forecasting Model

## Overview
This project builds a simple **30-day revenue forecast** from hypothetical advertising data (Meta & Google).  
We engineered daily revenue from orders × AOV, explored correlations, and produced an interactive Plotly dashboard.

Key outputs:
- **Forecasted revenue** for the next 30 days
- **Interactive dashboard** (Plotly) with:
  - Historical vs forecasted revenue
  - Spend vs orders correlation (split by platform)
- **CSV file** containing the next 30 days of revenue forecasts

---

## Data
### Columns
The dataset includes the following fields:
- `date`: Daily date (YYYY-MM-DD)
- `daily_spend`: Daily ad spend (per platform)
- `daily_clicks`: Number of ad clicks
- `daily_orders`: Orders attributed to ads
- `aov`: Average order value
- `platform`: Meta / Google  
- **Derived**:  
  - `revenue = daily_orders × aov`

### Aggregation
Data is aggregated to daily totals across platforms for forecasting.  
Platform splits are retained for correlation analysis.

---

## Forecasting Method
We chose a **simple linear regression** model using scikit-learn:

- **Features**:
  - Time index (`t`)
  - Day-of-week dummy variables
  - Daily spend (to capture spend → revenue relationship)
- **Target**: `daily revenue`

### Why Linear Regression?
- **Interpretability**: clear link between spend and revenue
- **Flexibility**: can incorporate external regressors (spend, promos, etc.)
- **Speed**: suitable for daily retraining

### Steps
1. Encode day-of-week as dummy variables
2. Fit regression on historical data
3. Generate future features (`t`, day-of-week, assumed spend)
4. Forecast next 30 days of revenue
5. Compute 95% confidence intervals using residual standard error

---

## Findings
- **Spend vs Orders**:  
  Strong positive correlation observed:
  - Meta: higher orders per dollar compared to Google  
  - Google: slightly lower conversion rate but higher AOV
- **Revenue Seasonality**:  
  Weekly pattern visible (weekends dip, weekdays stronger).
- **Forecast**:  
  Next 30 days projected to continue historical trend, with spend driving most variation.

---

## Outputs
1. **Dashboard**  
   - Historical revenue (line)
   - Forecasted revenue with 95% CI band
   - Spend vs orders scatter, split by platform

2. **Forecast CSV**  
   File: `revenue_forecast_30d.csv`  
   Columns:
   - `date`
   - `forecast_revenue`
   - `lower_95`
   - `upper_95`
>>>>>>> 6948c75 (Moved README file)
