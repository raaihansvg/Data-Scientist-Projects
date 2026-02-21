s# Amazon Sales Revenue Classification

End-to-end Machine Learning project to classify product sales performance using structured Amazon sales data.

This project predicts whether a product generates:

- **0 → Low Revenue**
- **1 → High Revenue**

---

## Problem Statement

Given structured e-commerce sales data, the objective is to build a model that classifies whether a product will generate **high revenue** or **low revenue**.

This is formulated as a **binary classification problem**.

---

## Dataset Overview

The dataset contains product-level sales information such as:

- `price`
- `discount_percent`
- `rating`
- `review_count`
- `product_category`
- `customer_region`
- `quantity_sold`
- `total_revenue`

###  Target Variable

Revenue was transformed into a binary label:

- `0` → Low Revenue  
- `1` → High Revenue  

The split was performed using a median-based threshold.

---

## Feature Engineering

Additional engineered features:

- `price_after_discount`
- `is_discounted`

Careful feature selection was performed to prevent **data leakage** (no direct usage of derived target variables).

---

##  Models Trained

Several classification models were evaluated:

### 1. Logistic Regression
Accuracy: ~0.76  

### 2. Random Forest Classifier
Accuracy: ~0.77  

### 3. XGBoost Classifier (Final Model)
Accuracy: **0.7893**

---

## Best XGBoost Parameters

```python
max_depth = 4
min_child_weight = 1
colsample_bytree = 0.7
subsample = 0.7
n_estimators = 300
learning_rate = 0.05
```
---
## Final Model Performance (XGBoost)

**Accuracy:** 78.93%

### Classification Report

| Class | Precision | Recall | F1-score |
|-------|-----------|--------|----------|
| 0 (Low Revenue)  | 0.88 | 0.68 | 0.77 |
| 1 (High Revenue) | 0.73 | 0.90 | 0.81 |

The model demonstrates strong recall in identifying high-revenue products.

---

##  Model Validation

- Train/Validation split (80/20)
- Cross-validation used during tuning
- Learning curve analysis performed
- No significant overfitting observed

---

## Model Inference

The final trained model can predict new product revenue class.

### Example Output
```python
Prediction : High Sales
Confidence : 74.01%
```
---

### Model Saving

```python
joblib.dump(model, "xgb_model.pkl")
```
---
## Key Insight
- Revenue classification is heavily influenced by pricing features
- XGBoost performs best on structured tabular data
- Preventing data leakage is critical when dealing with revenue-based targets
- Proper feature engineering signinficantly improves classification stability

##  Author
**[Raihan Lazuardi]**  
Aspiring Data Scientist / Machine Learning Practitioner






