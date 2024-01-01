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

The results from this phase can be found at `./phase_1/output.xlsx`.

## Phase 2: Production Planning

In this phase, we use the forecasts from the first phase to plan the production
of these 3 product groups. Thus, we model an integer linear programming problem
for this case.

The objective function, constraints, parameters, and decision variables can be
found at `./phase_2/report.pdf`. Also, the implementation of this problem in
Python's PuLP can be found at `./phase_2/notebook.ipynb`. Moreover, the solved
model is exported and saved at `./phase_2/model.json`.

### Results

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }

</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>T20</th>
      <th>T21</th>
      <th>T22</th>
      <th>T23</th>
      <th>T24</th>
      <th>T25</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>RP</th>
      <td>(437, 166, 7)</td>
      <td>(435, 159, 6)</td>
      <td>(433, 154, 6)</td>
      <td>(435, 148, 5)</td>
      <td>(435, 145, 5)</td>
      <td>(435, 144, 5)</td>
    </tr>
    <tr>
      <th>OP</th>
      <td>(3, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
    </tr>
    <tr>
      <th>PI</th>
      <td>(437, 166, 7)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(2, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
    </tr>
    <tr>
      <th>PD</th>
      <td>(0, 0, 0)</td>
      <td>(2, 7, 1)</td>
      <td>(2, 5, 0)</td>
      <td>(0, 6, 1)</td>
      <td>(0, 3, 0)</td>
      <td>(0, 1, 0)</td>
    </tr>
    <tr>
      <th>IL</th>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 13, 0)</td>
      <td>(0, 0, 0)</td>
    </tr>
    <tr>
      <th>IS</th>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 13, 0)</td>
      <td>(0, 0, 0)</td>
    </tr>
    <tr>
      <th>IG</th>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
    </tr>
    <tr>
      <th>TW</th>
      <td>251</td>
      <td>247</td>
      <td>244</td>
      <td>242</td>
      <td>241</td>
      <td>241</td>
    </tr>
    <tr>
      <th>OW</th>
      <td>5</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>HW</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>FW</th>
      <td>19749</td>
      <td>4</td>
      <td>3</td>
      <td>2</td>
      <td>1</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>
