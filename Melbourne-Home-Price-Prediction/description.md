# Melbourne House Price Prediction

## Project Overview
This project is an **end-to-end machine learning pipeline** for predicting house prices in Melbourne using the Kaggle *Melbourne Housing Dataset*.  
The focus of this project is not only achieving good predictive performance, but also applying **sound machine learning practices**, including leakage-free preprocessing, proper model evaluation, and a real-world inference demo.

> **Evaluation Metric:** Root Mean Squared Error (RMSE)

---

## Dataset
- **Source:** Kaggle – Melbourne Housing Dataset  
- **Target Variable:** `Price`  
- **Description:**  
  The dataset contains information about residential properties in Melbourne, including location, number of rooms, land size, building area, distance to the city center, and other relevant attributes.

---

## Project Workflow

### 1. Exploratory Data Analysis (EDA)
- Analysis of price distribution
- Missing value inspection
- Location-based insights
- Identification of features that could cause data leakage

---

### 2. Data Preprocessing
All preprocessing steps are implemented using **`Pipeline`** and **`ColumnTransformer`** to ensure reproducibility and prevent data leakage.

- Train–test split performed **before** preprocessing
- Numerical features:
  - Median imputation
- Categorical features:
  - Most frequent imputation
  - One-hot encoding
- Preprocessing is **fitted only on training data**

---

### 3. Feature Analysis & Selection
- **Mutual Information** used as an initial signal for feature relevance
- **Model-based feature importance** using Random Forest
- High-cardinality identifier features such as `Address` were **removed** to avoid memorization and improve generalization

---

### 4.Modeling & Cross-Validation
Multiple regression models were evaluated using **5-fold cross-validation**:

| Model | CV RMSE (approx.) |
|------|------------------|
| Linear Regression | ~460k |
| Random Forest (baseline) | ~295k |
| Tuned Random Forest | ~326k |
| Gradient Boosting (sklearn) | ~306k |
| **HistGradientBoostingRegressor** | **~276k (best)** |

The **HistGradientBoostingRegressor** was selected as the final model due to:
- Lowest cross-validated RMSE
- Stable performance
- Strong suitability for tabular housing data

---

### 5.Final Evaluation
- **Test RMSE:** ~**253k AUD**
- No significant overfitting observed
- Performance improvement validated empirically

---

## 6.Model Inference Demo
To simulate real-world usage, the final trained pipeline was:
1. Saved using `joblib`
2. Reloaded
3. Used to predict the price of a **new, unseen house**

Example inference output: Predicted House Price: AUD 1.608.978


This demonstrates that the model is not only evaluated offline, but also **ready to be reused in applications or APIs**.

---

## Tech Stack
- Python
- pandas, NumPy
- scikit-learn
- matplotlib
- joblib

---

## Repository Structure
| File                         | Description                             |
|------------------------------|---------------------------------------------|
| `Melbourne-House-Predict` | Notebook       |
| `description.md`                  | Project Description                       |
| `data`                  | Dataset                        |
| `melbourne_house_price_model.pkl`                  | Saved trained model used to predict Melbourne house prices |



---

## Key Takeaways
- Built a **leakage-free machine learning pipeline**
- Compared multiple models using cross-validation
- Selected the final model based on **empirical performance**
- Included a **clean inference demo** simulating real-world usage
- Project is **reproducible and portfolio-ready**

---

## Future Improvements
- Experiment with LightGBM or XGBoost for further performance gains
- Deploy the model using FastAPI or Streamlit
- Add automated input validation for inference

---

##  Author
**[Raihan Lazuardi]**  
Aspiring Data Scientist / Machine Learning Practitioner




