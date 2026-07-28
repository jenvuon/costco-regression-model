# Costco Quarterly Revenue Forecasting

A regression-based forecasting project that predicts **Costco's quarterly revenue** using historical financial data and seasonal dummy variables.

## Project Overview

This project analyzes Costco's quarterly revenue from **2011 Q4 to 2025 Q4** and builds multiple linear regression models to determine how seasonality affects revenue.

The project compares four forecasting models using **Mean Absolute Percentage Error (MAPE)** and selects the most accurate model for prediction.

## Dataset

The dataset contains:

* Fiscal Year
* Fiscal Quarter
* Quarter End Date
* Quarterly Revenue (USD millions)

Time is converted into a numerical trend variable for regression analysis.

## Features Engineered

### Time Trend

A sequential time variable was created to capture long-term revenue growth.

### Holiday Season Dummy

Costco's fiscal **Q1 (September–November)** was treated as the holiday season due to increased customer traffic surrounding events such as:

* Halloween
* Thanksgiving
* Early holiday shopping

An interaction term (`holiday_dv × time`) was also created to allow the holiday effect to change over time.

### Summer Dummy

Costco's fiscal **Q4** consistently experiences higher revenue.

A summer dummy variable and interaction term (`summer_dv × time`) were included to capture this seasonal pattern.

## Models Compared

### Model 1

Trend only

Revenue = β₀ + β₁(Time)

---

### Model 2

Trend + Holiday Dummy

Revenue = β₀ + β₁(Time) + β₂(Holiday Dummy) + β₃(Time × Holiday)

---

### Model 3

Trend + Summer Dummy

Revenue = β₀ + β₁(Time) + β₂(Summer Dummy) + β₃(Time × Summer)

---

### Model 4

Trend + Holiday Dummy + Summer Dummy

Includes both seasonal effects and their interaction terms.

## Model Evaluation

The dataset was split into:

* **75% Training**
* **25% Testing**

Model performance was evaluated using **Mean Absolute Percentage Error (MAPE).**

| Model       | MAPE        |
| ----------- | ----------- |
| Model 1     | 17.1%       |
| **Model 2** | **16.8%** ✅ |
| Model 3     | 18.0%       |
| Model 4     | 18.6%       |

Model 2 achieved the lowest forecasting error and was selected as the final model. 

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Statsmodels
* Google Colab

## Repository Structure

```
├── Costco_Revenue_Forecasting.ipynb
├── costco_quarterly_revenue_2010_2025.csv
├── README.md
```

## Example Workflow

1. Load quarterly revenue dataset
2. Visualize historical revenue trends
3. Create time variable
4. Engineer seasonal dummy variables
5. Split data into training and testing sets
6. Fit four OLS regression models
7. Compare models using MAPE
8. Select the best-performing model
9. Generate revenue predictions with confidence intervals

## Key Takeaways

* Costco exhibits a strong upward long-term revenue trend.
* Seasonal effects significantly influence quarterly performance.
* Incorporating a holiday seasonal dummy improved forecasting accuracy.
* The simplest seasonal model (Model 2) outperformed more complex alternatives, demonstrating that additional variables do not necessarily improve predictive performance.

## Authors

* Tanner Vo Tran
* Jenny Vuong
