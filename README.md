# Production Planning

This repository contains the files of my project for the "Production Planning"
course at Amirkabir University of Technology (Tehran Polytechnic) during the
Fall 2023 semester.

## Phase 1: Demand Forecasting

### Description

The dataset contains 6 tables, containing the actual demands for 6 type of
products belonging to 3 groups:

- Group 1 (G1): M1, M3, and M4
- Group 2 (G2): M2 and M5
- Group 3 (G3): M6

This phase focuses on 3 major contributions:

1. Predicting the demands for each group at the next 6 steps in the time series,
   implementing and using various forecasting methods such as Simple Exponential
   Smoothing (SES) and Linear Regression (LR).
2. Conducting error analysis on the resulting predictions from the forecasting
   methods, calculating MFE and MAE for each of them.
3. Calculating the tracking signal for each forecasting method.

### Details

Our demand forecasting section contains 5 methods:

1. Simple Exponential Smoothing (SES) with `alpha=0.3`.
2. Simple Moving Average (SMA) with `n=3`.
3. Weighted Moving Average (WMA) with `weights=[0.2, 0.3, 0.5]`.
4. Linear Regression (LR)
5. Adjusted Linear Regression (ALR) with `cycle_length=12`.

### Results

![SES](./1.%20Demand%20Forecasting/plots/SES.jpg)
![SMA](./1.%20Demand%20Forecasting/plots/SMA.jpg)
![WMA](./1.%20Demand%20Forecasting/plots/WMA.jpg)
![LR](./1.%20Demand%20Forecasting/plots/LR.jpg)
![ALR](./1.%20Demand%20Forecasting/plots/ALR.jpg)

### Error Analysis and Tracking Signal

This section's results can be found at
`./1.%20Demand%20Forecasting/output.xlsx`. However, we can have a glimpse at the
tracking signals:

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>G1</th>
      <th>G2</th>
      <th>G3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>SES</th>
      <td>1.627202</td>
      <td>1.494879</td>
      <td>-5.000000</td>
    </tr>
    <tr>
      <th>SMA</th>
      <td>-1.497890</td>
      <td>-0.543943</td>
      <td>-5.000000</td>
    </tr>
    <tr>
      <th>WMA</th>
      <td>-2.279876</td>
      <td>-1.372624</td>
      <td>-5.000000</td>
    </tr>
    <tr>
      <th>LR</th>
      <td>4.758926</td>
      <td>4.039556</td>
      <td>3.254925</td>
    </tr>
    <tr>
      <th>ALR</th>
      <td>5.000000</td>
      <td>3.809070</td>
      <td>1.948311</td>
    </tr>
  </tbody>
</table>
</div>

## Phase 2: S&OP

### Description

In this phase, we use the forecasts of the first phase in the S&OP of these 3
product groups, modeling an LP problem and conducting sensitivity analysis on
two of its parameters.

The objective function, constraints, parameters, and decision variables can be
found at `./2. S&OP/report.pdf`. Also, the implementation of this problem in
Python's PuLP can be found at `./2. S&OP/notebook.ipynb`. Moreover, the solved
model is exported and saved at `./2. S&OP/model.json`.

### Results

```
total cost: 59338527006666.664
```

<div>
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
      <td>(434092, 147043, 5215)</td>
      <td>(434092, 147043, 5215)</td>
      <td>(434092, 147043, 5215)</td>
      <td>(434148, 147033, 4644)</td>
      <td>(434148, 147033, 4644)</td>
      <td>(434148, 147033, 4644)</td>
    </tr>
    <tr>
      <th>OP</th>
      <td>(5788, 18832, 1413)</td>
      <td>(1, 11920, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
    </tr>
    <tr>
      <th>PI</th>
      <td>(434092, 147043, 5215)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(56, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
    </tr>
    <tr>
      <th>PD</th>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 10, 571)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
    </tr>
    <tr>
      <th>IL</th>
      <td>(0, 0, 0)</td>
      <td>(-599, -2, -300)</td>
      <td>(655, -6002, -91)</td>
      <td>(0, -6089, 0)</td>
      <td>(-44, 8985, 273)</td>
      <td>(0, 0, 0)</td>
    </tr>
    <tr>
      <th>IS</th>
      <td>(0, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(655, 0, 0)</td>
      <td>(0, 0, 0)</td>
      <td>(0, 8985, 273)</td>
      <td>(0, 0, 0)</td>
    </tr>
    <tr>
      <th>IG</th>
      <td>(0, 0, 0)</td>
      <td>(599, 2, 300)</td>
      <td>(0, 6002, 91)</td>
      <td>(0, 6089, 0)</td>
      <td>(44, 0, 0)</td>
      <td>(0, 0, 0)</td>
    </tr>
    <tr>
      <th>TW</th>
      <td>187632</td>
      <td>187632</td>
      <td>187632</td>
      <td>187464</td>
      <td>187464</td>
      <td>187464</td>
    </tr>
    <tr>
      <th>OW</th>
      <td>29157</td>
      <td>13352</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>HW</th>
      <td>167632</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>FW</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>168</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>

### Sensitivity Analysis

As said, sensitivity analysis is conducted on two following parameters:

#### Regular Salary

```
rs = 12000000,	total cost: 55962663006666.664
rs = 13000000,	total cost: 57087951006666.664
rs = 14000000,	total cost: 58213239006666.664
rs = 15000000,	total cost: 59338527006666.664
rs = 16000000,	total cost: 60463815006666.664
rs = 17000000,	total cost: 61589103006666.664
rs = 18000000,	total cost: 62714391006666.664
```

#### Hiring Cost

```
hc = 1200000,	total cost: 59137368606666.664
hc = 1600000,	total cost: 59204421406666.664
hc = 2000000,	total cost: 59271474206666.664
hc = 2400000,	total cost: 59338527006666.664
hc = 2800000,	total cost: 59405579806666.664
hc = 3200000,	total cost: 59472632606666.664
hc = 3600000,	total cost: 59539685406666.664
```

## Phase 3: MPS and MRP

In the final phase, MPS is developed and MRP is conducted for each product
group. More details can be found at `./3. MPS and MRP/notebook.ipynb` and
`./3. MPS and MRP/report.pdf`.

### MPS

#### Group 1

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
      <th>8</th>
      <th>9</th>
      <th>...</th>
      <th>15</th>
      <th>16</th>
      <th>17</th>
      <th>18</th>
      <th>19</th>
      <th>20</th>
      <th>21</th>
      <th>22</th>
      <th>23</th>
      <th>24</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Forecast</th>
      <td>0.0</td>
      <td>109970.0</td>
      <td>109970.0</td>
      <td>109970.0</td>
      <td>109970.0</td>
      <td>108673.0</td>
      <td>108673.0</td>
      <td>108673.0</td>
      <td>108673.0</td>
      <td>108210.0</td>
      <td>...</td>
      <td>108701.0</td>
      <td>108701.0</td>
      <td>108548.0</td>
      <td>108548.0</td>
      <td>108548.0</td>
      <td>108548.0</td>
      <td>108526.0</td>
      <td>108526.0</td>
      <td>108526.0</td>
      <td>108526.0</td>
    </tr>
    <tr>
      <th>Order</th>
      <td>0.0</td>
      <td>101008.0</td>
      <td>107570.0</td>
      <td>82990.0</td>
      <td>92990.0</td>
      <td>81660.0</td>
      <td>69276.0</td>
      <td>62743.0</td>
      <td>59740.0</td>
      <td>75777.0</td>
      <td>...</td>
      <td>70151.0</td>
      <td>58829.0</td>
      <td>61655.0</td>
      <td>53822.0</td>
      <td>56719.0</td>
      <td>59315.0</td>
      <td>60527.0</td>
      <td>54358.0</td>
      <td>53500.0</td>
      <td>62392.0</td>
    </tr>
    <tr>
      <th>Demand</th>
      <td>0.0</td>
      <td>101008.0</td>
      <td>107570.0</td>
      <td>82990.0</td>
      <td>92990.0</td>
      <td>81660.0</td>
      <td>69276.0</td>
      <td>108673.0</td>
      <td>108673.0</td>
      <td>108210.0</td>
      <td>...</td>
      <td>108701.0</td>
      <td>108701.0</td>
      <td>108548.0</td>
      <td>108548.0</td>
      <td>108548.0</td>
      <td>108548.0</td>
      <td>108526.0</td>
      <td>108526.0</td>
      <td>108526.0</td>
      <td>108526.0</td>
    </tr>
    <tr>
      <th>PoH</th>
      <td>4740.0</td>
      <td>119950.0</td>
      <td>12380.0</td>
      <td>145608.0</td>
      <td>52618.0</td>
      <td>187176.0</td>
      <td>117900.0</td>
      <td>9227.0</td>
      <td>116772.0</td>
      <td>8562.0</td>
      <td>...</td>
      <td>6483.0</td>
      <td>114000.0</td>
      <td>5452.0</td>
      <td>113122.0</td>
      <td>220792.0</td>
      <td>112244.0</td>
      <td>219936.0</td>
      <td>111410.0</td>
      <td>219102.0</td>
      <td>110576.0</td>
    </tr>
    <tr>
      <th>ATP</th>
      <td>0.0</td>
      <td>7640.0</td>
      <td>0.0</td>
      <td>40238.0</td>
      <td>0.0</td>
      <td>2539.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>80701.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>95734.0</td>
      <td>0.0</td>
      <td>162396.0</td>
      <td>100184.0</td>
      <td>0.0</td>
      <td>101333.0</td>
      <td>0.0</td>
      <td>100326.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>MPS</th>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>6 rows × 25 columns</p>
</div>

#### Group 2

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
      <th>8</th>
      <th>9</th>
      <th>...</th>
      <th>15</th>
      <th>16</th>
      <th>17</th>
      <th>18</th>
      <th>19</th>
      <th>20</th>
      <th>21</th>
      <th>22</th>
      <th>23</th>
      <th>24</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Forecast</th>
      <td>0.0</td>
      <td>41469.0</td>
      <td>41469.0</td>
      <td>41469.0</td>
      <td>41469.0</td>
      <td>39742.0</td>
      <td>39742.0</td>
      <td>39742.0</td>
      <td>39742.0</td>
      <td>38261.0</td>
      <td>...</td>
      <td>36780.0</td>
      <td>36780.0</td>
      <td>32990.0</td>
      <td>32990.0</td>
      <td>32990.0</td>
      <td>32990.0</td>
      <td>39005.0</td>
      <td>39005.0</td>
      <td>39005.0</td>
      <td>39005.0</td>
    </tr>
    <tr>
      <th>Order</th>
      <td>0.0</td>
      <td>37048.0</td>
      <td>38661.0</td>
      <td>32388.0</td>
      <td>30016.0</td>
      <td>28078.0</td>
      <td>29133.0</td>
      <td>33582.0</td>
      <td>27698.0</td>
      <td>28652.0</td>
      <td>...</td>
      <td>22506.0</td>
      <td>19947.0</td>
      <td>23133.0</td>
      <td>26109.0</td>
      <td>20192.0</td>
      <td>22460.0</td>
      <td>19769.0</td>
      <td>18557.0</td>
      <td>18004.0</td>
      <td>18910.0</td>
    </tr>
    <tr>
      <th>Demand</th>
      <td>0.0</td>
      <td>37048.0</td>
      <td>38661.0</td>
      <td>32388.0</td>
      <td>30016.0</td>
      <td>28078.0</td>
      <td>29133.0</td>
      <td>39742.0</td>
      <td>39742.0</td>
      <td>38261.0</td>
      <td>...</td>
      <td>36780.0</td>
      <td>36780.0</td>
      <td>32990.0</td>
      <td>32990.0</td>
      <td>32990.0</td>
      <td>32990.0</td>
      <td>39005.0</td>
      <td>39005.0</td>
      <td>39005.0</td>
      <td>39005.0</td>
    </tr>
    <tr>
      <th>PoH</th>
      <td>3160.0</td>
      <td>110257.0</td>
      <td>71596.0</td>
      <td>39208.0</td>
      <td>9192.0</td>
      <td>125259.0</td>
      <td>96126.0</td>
      <td>56384.0</td>
      <td>16642.0</td>
      <td>122526.0</td>
      <td>...</td>
      <td>41548.0</td>
      <td>4768.0</td>
      <td>115923.0</td>
      <td>82933.0</td>
      <td>49943.0</td>
      <td>16953.0</td>
      <td>122093.0</td>
      <td>83088.0</td>
      <td>44083.0</td>
      <td>5078.0</td>
    </tr>
    <tr>
      <th>ATP</th>
      <td>0.0</td>
      <td>6032.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>25654.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>41413.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>52251.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>68905.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>MPS</th>
      <td>0.0</td>
      <td>144145.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>6 rows × 25 columns</p>
</div>

#### Group 3

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
      <th>8</th>
      <th>9</th>
      <th>...</th>
      <th>15</th>
      <th>16</th>
      <th>17</th>
      <th>18</th>
      <th>19</th>
      <th>20</th>
      <th>21</th>
      <th>22</th>
      <th>23</th>
      <th>24</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Forecast</th>
      <td>0.0</td>
      <td>1657.0</td>
      <td>1657.0</td>
      <td>1657.0</td>
      <td>1657.0</td>
      <td>1379.0</td>
      <td>1379.0</td>
      <td>1379.0</td>
      <td>1379.0</td>
      <td>1252.0</td>
      <td>...</td>
      <td>1139.0</td>
      <td>1139.0</td>
      <td>1093.0</td>
      <td>1093.0</td>
      <td>1093.0</td>
      <td>1093.0</td>
      <td>1230.0</td>
      <td>1230.0</td>
      <td>1230.0</td>
      <td>1230.0</td>
    </tr>
    <tr>
      <th>Order</th>
      <td>0.0</td>
      <td>1497.0</td>
      <td>1195.0</td>
      <td>1558.0</td>
      <td>1280.0</td>
      <td>1426.0</td>
      <td>1342.0</td>
      <td>1074.0</td>
      <td>1041.0</td>
      <td>1133.0</td>
      <td>...</td>
      <td>821.0</td>
      <td>1122.0</td>
      <td>1122.0</td>
      <td>856.0</td>
      <td>1019.0</td>
      <td>842.0</td>
      <td>1074.0</td>
      <td>815.0</td>
      <td>947.0</td>
      <td>855.0</td>
    </tr>
    <tr>
      <th>Demand</th>
      <td>0.0</td>
      <td>1497.0</td>
      <td>1195.0</td>
      <td>1558.0</td>
      <td>1280.0</td>
      <td>1426.0</td>
      <td>1342.0</td>
      <td>1379.0</td>
      <td>1379.0</td>
      <td>1252.0</td>
      <td>...</td>
      <td>1139.0</td>
      <td>1139.0</td>
      <td>1122.0</td>
      <td>1093.0</td>
      <td>1093.0</td>
      <td>1093.0</td>
      <td>1230.0</td>
      <td>1230.0</td>
      <td>1230.0</td>
      <td>1230.0</td>
    </tr>
    <tr>
      <th>PoH</th>
      <td>1975.0</td>
      <td>90570.0</td>
      <td>89375.0</td>
      <td>87817.0</td>
      <td>86537.0</td>
      <td>85111.0</td>
      <td>83769.0</td>
      <td>82390.0</td>
      <td>81011.0</td>
      <td>79759.0</td>
      <td>...</td>
      <td>72586.0</td>
      <td>71447.0</td>
      <td>70325.0</td>
      <td>69232.0</td>
      <td>68139.0</td>
      <td>67046.0</td>
      <td>65816.0</td>
      <td>64586.0</td>
      <td>63356.0</td>
      <td>62126.0</td>
    </tr>
    <tr>
      <th>ATP</th>
      <td>0.0</td>
      <td>63994.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>MPS</th>
      <td>0.0</td>
      <td>90092.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>6 rows × 25 columns</p>
</div>

### MRP

#### Group 1

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
      <th>8</th>
      <th>9</th>
      <th>...</th>
      <th>15</th>
      <th>16</th>
      <th>17</th>
      <th>18</th>
      <th>19</th>
      <th>20</th>
      <th>21</th>
      <th>22</th>
      <th>23</th>
      <th>24</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Gross Requirements</th>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>Scheduled Receipts</th>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>PoH</th>
      <td>4740.0</td>
      <td>4740.0</td>
      <td>4740.0</td>
      <td>4740.0</td>
      <td>4740.0</td>
      <td>4740.0</td>
      <td>4740.0</td>
      <td>4740.0</td>
      <td>4740.0</td>
      <td>4740.0</td>
      <td>...</td>
      <td>4740.0</td>
      <td>4740.0</td>
      <td>4740.0</td>
      <td>4740.0</td>
      <td>4740.0</td>
      <td>4740.0</td>
      <td>4740.0</td>
      <td>4740.0</td>
      <td>4740.0</td>
      <td>4740.0</td>
    </tr>
    <tr>
      <th>Net Requirements</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>Planned Order Receipt</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>Planned Order Release</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>...</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>216218.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>6 rows × 25 columns</p>
</div>

#### Group 2

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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
      <th>8</th>
      <th>9</th>
      <th>...</th>
      <th>15</th>
      <th>16</th>
      <th>17</th>
      <th>18</th>
      <th>19</th>
      <th>20</th>
      <th>21</th>
      <th>22</th>
      <th>23</th>
      <th>24</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Gross Requirements</th>
      <td>0.0</td>
      <td>144145.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>Scheduled Receipts</th>
      <td>0.0</td>
      <td>144145.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>PoH</th>
      <td>3160.0</td>
      <td>3160.0</td>
      <td>3160.0</td>
      <td>3160.0</td>
      <td>3160.0</td>
      <td>3160.0</td>
      <td>3160.0</td>
      <td>3160.0</td>
      <td>3160.0</td>
      <td>3160.0</td>
      <td>...</td>
      <td>3160.0</td>
      <td>3160.0</td>
      <td>3160.0</td>
      <td>3160.0</td>
      <td>3160.0</td>
      <td>3160.0</td>
      <td>3160.0</td>
      <td>3160.0</td>
      <td>3160.0</td>
      <td>3160.0</td>
    </tr>
    <tr>
      <th>Net Requirements</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>Planned Order Receipt</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>Planned Order Release</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144145.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>6 rows × 25 columns</p>
</div>

#### Group 3

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
      <th>8</th>
      <th>9</th>
      <th>...</th>
      <th>15</th>
      <th>16</th>
      <th>17</th>
      <th>18</th>
      <th>19</th>
      <th>20</th>
      <th>21</th>
      <th>22</th>
      <th>23</th>
      <th>24</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Gross Requirements</th>
      <td>0.0</td>
      <td>90092.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>Scheduled Receipts</th>
      <td>0.0</td>
      <td>90092.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>PoH</th>
      <td>1975.0</td>
      <td>1975.0</td>
      <td>1975.0</td>
      <td>1975.0</td>
      <td>1975.0</td>
      <td>1975.0</td>
      <td>1975.0</td>
      <td>1975.0</td>
      <td>1975.0</td>
      <td>1975.0</td>
      <td>...</td>
      <td>1975.0</td>
      <td>1975.0</td>
      <td>1975.0</td>
      <td>1975.0</td>
      <td>1975.0</td>
      <td>1975.0</td>
      <td>1975.0</td>
      <td>1975.0</td>
      <td>1975.0</td>
      <td>1975.0</td>
    </tr>
    <tr>
      <th>Net Requirements</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>Planned Order Receipt</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>Planned Order Release</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>6 rows × 25 columns</p>
</div>
