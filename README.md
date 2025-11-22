# electricity-price-forecasting

Full Report: [Click here](Bury_Stanowska/report/Bury_Stanowska_Final_Report.pdf)

Datasets: [Click here](Bury_Stanowska/datasets)

Code: [Click here](Bury_Stanowska/code/predictive_analytics_project_final_report.py)

## Project Overview

This project explores **day-ahead electricity price forecasting (EPF)** using various models, with a focus on the **long-term seasonal component** in electricity price series. The study replicates and extends the results of the paper:

*Marcjasz G., Uniejewski B., Weron R. (2019) "On the importance of the long-term seasonal component in day-ahead electricity price forecasting with NARX neural networks", International Journal of Forecasting, 35, 1520–1535.*

The goal is to implement benchmark models and more advanced methods like **SCAR** and **NARX neural networks**, and evaluate their performance.

---

## Datasets

Two datasets are used in this project:

1. **GEFCom2014 dataset**  
   - Source: Global Energy Forecasting Competition 2014  
   - Variables: Locational marginal prices (LMP), day-ahead system load  

2. **Nord Pool dataset**  
   - Source: Nord Pool, European power exchange  
   - Variables: System prices, hourly consumption prognosis for Denmark, Finland, Norway, Sweden  

Missing data was handled by filling blanks with the arithmetic average of neighboring values.

---

## Methods Implemented

1. **Benchmark Models**  
   - Naïve benchmark: Forecasting based on same hour from previous day or week  
   - Expert benchmark: Autoregressive model with exogenous inputs, weekday dummies, and non-linear effects

2. **Seasonal Component Autoregressive (SCAR)**  
   - Decomposes log-prices into long-term seasonal component (LTSC) and stochastic component  
   - Includes ARX modeling and combination with LTSC for forecasting

3. **Artificial Neural Network (ANN)**  
   - NARX (Non-linear Autoregressive with Exogenous inputs) recurrent neural network  
   - One hidden layer with 5 neurons, trained with Levenberg–Marquardt algorithm

4. **Committee Machines**  
   - Ensemble of multiple ANN or SCANN networks to improve forecast accuracy

5. **ARIMA (Further Development)**  
   - Used as an additional benchmark for daily predictions due to computational limitations

---

## Performance Evaluation

- **Metric:** Weekly-weighted mean absolute error (WMAE)  
- **Results:**  
  - ANN benchmarks generally achieve the lowest error  
  - SCAR models improve forecasts over Naïve and Expert benchmarks  
  - Neural network-based models outperform linear models when considering long-term seasonality 
