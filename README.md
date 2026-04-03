# MECH 309 Project – Weather and Air Quality Prediction

## Overview
This project focuses on multi-horizon temperature prediction using historical weather data from Montreal.  
We build a ridge regression model to forecast future temperature at different time horizons (1h to 48h) and evaluate its performance across different seasons.

The project also includes a parameter redundancy analysis to assess the importance of different feature groups.

---

## Project Structure
- `notebooks/Part_1_Project.ipynb` : main notebook containing data processing, modeling, and analysis
- `results_table.csv` : summary of model performance metrics
- `redundancy_results.csv` : results of feature ablation study
- `figures/` : generated plots (optional)
- `README.md` : project description and instructions

---

## Methods

### Data Collection
- Weather data is obtained using the Open-Meteo API
- Variables include:
  - Temperature (T)
  - Wind speed (W)
  - Humidity (RH)
  - Pressure (P)
  - Cloud cover

### Feature Engineering
- Lagged variables (1h, 3h, 6h, 12h, 24h, etc.)
- Cyclical time features:
  - Daily cycle (sin/cos)
  - Seasonal cycle (sin/cos)

### Model
- Ridge regression (least squares with regularization)
- Features are standardized before training
- Predictions are made for multiple horizons:
  - 1h, 3h, 6h, 12h, 24h, 48h

### Validation
- Seasonal split:
  - Winter (January)
  - Summer (July)
- Performance metrics:
  - RMSE (Root Mean Square Error)
  - MAE (Mean Absolute Error)

---

## Results

- The model consistently outperforms the persistence baseline.
- Best improvements are observed in summer, reaching up to ~60% improvement.
- Performance decreases with longer prediction horizons, as expected.

Example:
- 1h prediction (Winter): RMSE ≈ 0.64°C
- 12h prediction (Summer): RMSE ≈ 2.29°C with ~60% improvement

---

## Parameter Redundancy Analysis
We evaluate the importance of feature groups by removing them and retraining the model.

Key findings:
- Wind and cloud features have limited impact in some cases
- Temperature lags are the most important predictors
- Removing certain features can slightly improve performance due to reduced noise

---

## How to Run

1. Open the notebook in Jupyter Notebook or Google Colab  
2. Install required libraries:
   - numpy
   - pandas
   - matplotlib
   - requests
3. Run all cells sequentially  

The notebook will:
- Download data
- Train models
- Generate results and plots

---

## Output
- Tables of RMSE and MAE across horizons and seasons
- Prediction plots (model vs actual vs baseline)
- Redundancy analysis summary

---

## Team Contributions
- Sarah Hanna: model design, regression implementation, analysis  
- Sim Virk: data processing, feature engineering, visualization  

---

## Versioning
Final submission is tagged as `v1.0`.
