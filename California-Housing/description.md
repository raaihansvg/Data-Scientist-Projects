# aCalifornia Housing Price Prediction  
### End-to-End Regression Machine Learning Project

## Project Overview

This project builds an **end-to-end machine learning regression pipeline** to predict the **median house value in California** using socioeconomic and geographic features.

The workflow covers the full data science lifecycle:
- Exploratory Data Analysis (EDA)
- Data preprocessing
- Model benchmarking
- Model evaluation
- Final inference with **real-world currency interpretation**

The final model uses **XGBoost Regressor**, which demonstrated superior performance compared to baseline and alternative tree-based models.

---

##  Problem Statement

The objective is to predict **Median House Value (`MedHouseVal`)** for a given **census block group** using features such as:
- Income level
- Housing characteristics
- Population density
- Geographic location

>  **Important Note**  
Each data point represents an **area-level aggregation**, **not an individual house**.  
Predictions correspond to the **median house price within an area**, not the price of a single property.

---

## Dataset

- **Source**: California Housing Dataset  
- **Target Variable**: `MedHouseVal`
- **Target Unit**:  
  - Expressed in units of **$100,000 USD**

---

##  Features Used

| Feature     | Description |
|------------|-------------|
| MedInc     | Median income in the area |
| HouseAge  | Median house age |
| AveRooms  | Average number of rooms per household |
| AveBedrms | Average number of bedrooms per household |
| Population| Area population |
| AveOccup  | Average occupants per household |
| Latitude  | Geographic latitude |
| Longitude | Geographic longitude |

---

## Modeling Approach

###  Baseline Model
- **Linear Regression**
- Used to validate preprocessing and establish baseline performance

###  Advanced Models Evaluated
- Random Forest Regressor  
- Gradient Boosting Regressor  
- HistGradientBoosting Regressor  
- **XGBoost Regressor (Final Model)**

Model selection was based on:
- Cross-validation RMSE
- Model stability
- Generalization performance

---

## Final Model Performance

| Metric | Value |
|------|------|
| RMSE (Validation) | **0.46** |
| R² Score | **0.84** |

### Interpretation
- The model explains approximately **84% of the variance** in median house values
- Remaining error is mainly due to:
  - Noise
  - Unobserved factors (e.g., neighborhood quality, amenities, crime rate)

---

## Feature Analysis

Feature importance analysis using **Mutual Information** and **XGBoost importance** shows:

- **Median Income (`MedInc`)** is the strongest predictor
- **Geographic features** (Latitude & Longitude) play a significant role
- **Occupancy-related features** capture non-linear effects effectively

---

## Model Inference

### Example Input
```python
new_house = {
    "MedInc": 6.8,
    "HouseAge": 28,
    "AveRooms": 6.2,
    "AveBedrms": 1.05,
    "Population": 950,
    "AveOccup": 2.6,
    "Latitude": 37.85,
    "Longitude": -122.25
}
```
### Prediction Output
```python
Predicted House Value (USD): $335,861
Predicted House Value (IDR): Rp 5,686,469,632
}
```
### The prediction represents the median house value in the given area, converted to USD and IDR purely for interpretability



---
##  Author
**[Raihan Lazuardi]**  
Aspiring Data Scientist / Machine Learning Practitioner
