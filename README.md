# Production Planning

This repository contains the files of my project for the "Production Planning"
course at Amirkabir University of Technology (Tehran Polytechnic) during the
Fall 2023 semester.

## Phase 1: Demand Forecasting

### Description

The dataset contains 6 tables, containing the actual demands for 6 type of
products. These variants belong to 3 groups:

- Group 1 (G1): M1, M3, and M4
- Group 2 (G2): M2 and M5
- Group 3 (G3): M6

This phase focuses on 3 major contributions:

1. Predicting the demands for each group for the next 6 months, implementing and
   using various forecasting methods such as Simple Exponential Smoothing (SES)
   and Linear Regression (LR).
2. Performing error analysis on the resulting predictions from the forecasting
   models, calculating MFE and MAE for each of them.
3. Calculating the tracking signal of each forecasting model's predictions.

### Details

Our demand forecasting section contains 5 models:

1. Simple Exponential Smoothing (SES) with `alpha=0.3`.
2. Simple Moving Average (SMA) with `n=3`.
3. Weighted Moving Average (WMA) with `weights=[0.2, 0.3, 0.5]`.
4. Linear Regression (LR)
5. Adjusted Linear Regression (ALR) with `cycle_length=12`.

### Results

![SES](./phase_1/forecast_plots/SES.jpg)
![SMA](./phase_1/forecast_plots/SMA.jpg)
![WMA](./phase_1/forecast_plots/WMA.jpg) ![LR](./phase_1/forecast_plots/LR.jpg)
![ALR](./phase_1/forecast_plots/ALR.jpg)

### Error Analysis and Tracking Signal

The results for these sections can be found at `output.xlsx`.

## Phase 2: Production Planning

_WIP_
