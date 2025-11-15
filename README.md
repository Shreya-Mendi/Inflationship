# Inflationship
Modeling the Relationship Between Port Traffic and Inflation


## Forecast Window

Both models use the same forecast horizon:
12 months (defined by steps = 12)

For the out-of-sample MAPE calculation, the model:
Trains on all data except the last 12 months
Forecasts the next 12 months
Compares predictions to actual values for those 12 months

## Model Accuracy
Based on the comparison table in the notebook:
Full SARIMAX (CPI + exog variables)
In-sample MAPE: ≈ 0.1 - 1%
Out-of-sample MAPE: ≈ 0.3 - 2%
Interpretation: Extremely accurate
Exog-only SARIMAX
In-sample MAPE: ≈ 2 - 5%
Out-of-sample MAPE: ≈ 4 - 9%
Interpretation: Much worse fit, but still meaningful


## What This Means
The Full SARIMAX is 2-4x more accurate because it:
Uses past CPI values (autoregressive component)
Captures CPI's own momentum and patterns
Models seasonality
PLUS uses the exogenous variables

The Exog-only model sacrifices accuracy for interpretability - it shows you the direct causal effect of port activity and import prices on CPI, without confounding from CPI's own historical patterns.
## Example Performance Difference
If actual CPI is 100:
Full SARIMAX might predict 99.7-101.5 (0.3-1.5% error)
Exog-only might predict 95-105 (5% error)
The exog-only model is still reasonable for understanding relationships, but you wouldn't want to use it for precise inflation forecasting.