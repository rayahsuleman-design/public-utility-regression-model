# public-utility-regression-model
this allows you to edit the readme just like a text cell in colab
use this like a landing page for project
# Hotazel Steam – Forecasting Model Comparison

A simple linear regression project comparing two candidate models for
forecasting monthly revenue for a fictional company, **Hotazel Steam**.

## Overview

The notebook builds and evaluates two single-variable OLS (Ordinary Least
Squares) regression models to predict monthly `revenue`:

- **Model 1:** `revenue ~ production`
- **Model 2:** `revenue ~ coolDD` (cooling degree days)

Each model is trained on historical data and tested on held-out data to see
which feature is the better predictor of revenue.

## Data

- **File:** `AICPA_regressionAnalysisData.csv`
- **Rows:** 48 monthly observations (Jan 2011 – Dec 2014)
- **Columns:**

  | Column | Description |
  |---|---|
  | `type` | `dt4training` (2011–2013, 36 rows) or `dt4testing` (2014, 12 rows) |
  | `date` | Month-end date |
  | `revenue` | Monthly revenue (dependent variable) |
  | `production` | Units produced that month |
  | `coolDD` | Cooling degree days (proxy for warm-weather demand) |
  | `heatDD` | Heating degree days (not used in either model) |

## Notebook Structure

1. **Setup** – imports pandas, numpy, matplotlib; disables scientific notation
2. **Exploring the Data** – loads the CSV, converts `date` to datetime, plots
   revenue over time, and computes correlations between `revenue` and the two
   candidate features
3. **Train/Test Split** – splits the data using the `type` column into
   `dt4training` and `dt4testing`
4. **Model 1** – fits `revenue ~ production` using `statsmodels.OLS` on the
   training data
5. **Model 2** – fits `revenue ~ coolDD` using `statsmodels.OLS` on the
   training data
6. **Test Model 1** – predicts revenue on the testing data and computes
   **MAPE** (Mean Absolute Percentage Error)
7. **Test Model 2** – same testing process for Model 2
8. **Visualization** – plots actual testing revenue against both models'
   predictions for a visual comparison

## Results

| Model | Feature | MAPE (on test data) |
|---|---|---|
| Model 1 | `production` | ~0.254 (25.4%) |
| Model 2 | `coolDD` | ~0.296 (29.6%) |

**Model 1 (production) performs better**, with a lower MAPE than Model 2
(coolDD). This is consistent with the correlation analysis in Section 2,
which shows `production` is much more strongly correlated with `revenue`
(≈0.63) than `coolDD` is (≈-0.17).

## Requirements

- Python 3
- `pandas`
- `numpy`
- `matplotlib`
- `statsmodels`

## Usage

1. Place `AICPA_regressionAnalysisData.csv` in the same directory as the
   notebook (or update the path in the data-loading cell).
2. Run all cells in order from top to bottom.
3. Review the printed MAPE values and the final comparison chart to see
   which model predicts revenue more accurately.
