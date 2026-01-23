# User Spending Prediction (Behavior-Based Regression)

## Project Overview
This project focuses on predicting **user-level spending** in an e-commerce platform using **pure behavioral features**.  
The main objective is not to maximize model accuracy through transactional leakage, but to build a **realistic, production-ready model** that reflects real-world data constraints.

The project follows an **end-to-end Data Scientist workflow**:
- Data aggregation (transaction → user-level)
- Exploratory Data Analysis (EDA)
- Feature engineering
- Leakage prevention
- Model comparison & evaluation
- Business interpretation

---

## Business Objective
To understand **what behavioral signals are associated with higher user spending**, and assess how far user spending can be predicted **without relying on transaction-derived features** such as price averages.

This mirrors a common real-world constraint where:
- Full transaction details may not be available early
- Models must rely on **limited but reliable behavioral data**

---

##  Dataset
Source: **Olist E-commerce Dataset (Kaggle)**

Original dataset contains multiple tables (orders, order items, customers, products, etc.).  
After joining and aggregation, the data is transformed into a **user-level dataset**.

---

## Feature Engineering Strategy

### 🔹 Features Used (Behavioral Only)
The final model uses the following features:

- `total_items` — total number of items purchased by a user  
- `total_orders` — number of unique orders  
- `active_days` — number of distinct days the user made purchases  
- `user_tenure_days` — time span between first and last purchase  
- `orders_per_active_day` — purchase intensity metric  

Log transformation was applied where appropriate to **compress extreme values** and stabilize learning.

>  **Transaction-derived features such as `avg_item_price` and `avg_order_value` were intentionally excluded to avoid data leakage.**

---

## Data Leakage Prevention
Several features that strongly correlate with the target were explicitly removed:
- `total_spending`
- `avg_item_price`
- `avg_order_value`

These features are direct or near-direct transformations of the target variable and would lead to **inflated but unrealistic performance**.

This decision ensures:
- Honest evaluation
- Production relevance
- Fair model comparison

---

## Feature Relevance (Mutual Information)

| Feature | Mutual Information |
|------|-------------------|
| total_items | 0.22 |
| total_orders | 0.026 |
| active_days | 0.016 |
| log_user_tenure_days | 0.012 |
| user_tenure_days | 0.010 |
| orders_per_active_day | 0.008 |
| log_orders_per_active_day | 0.007 |

**Key Insight:**  
No single feature dominates the prediction. All features provide **weak but consistent signals**, indicating that user spending is inherently difficult to predict with behavioral data alone.

---

##  Modeling & Evaluation

Target variable:
- `log_total_spending` (log-transformed to handle skewness)

Models evaluated:
- Linear Regression
- Random Forest Regressor
- XGBoost Regressor

### Cross-Validated RMSE

| Model | Mean RMSE | Std |
|-----|----------|-----|
| Linear Regression | 0.96 | 0.009 |
| Random Forest | 0.896 | 0.005 |
| XGBoost | 0.896 | 0.005 |

**Observation:**
- Tree-based models outperform linear regression, indicating non-linear relationships.
- Random Forest and XGBoost achieve nearly identical performance.
- Increasing model complexity does not significantly improve results.

This suggests an **information ceiling caused by feature limitations**, not model inefficiency.

---

## Key Findings & Business Insights

- User spending is driven more by **purchase volume and intensity** than by user tenure.
- Being a long-tenured user does not guarantee high spending.
- High-value users can often be identified early based on activity patterns.
- Model performance is constrained by **feature availability**, not algorithm choice.

---

## Limitations
This project intentionally uses a **limited feature set**.

Although the original Kaggle dataset provides richer information (e.g. product categories, payment methods, shipping data), only a subset of features was used to:
- Simulate real-world data constraints
- Prevent data leakage
- Maintain model interpretability

As a result:
- The model is not optimized for maximum accuracy
- Performance reflects realistic business conditions

---

##  Future Improvements
Potential extensions include:
- Product category-level features
- Promotion or discount signals
- Time-windowed behavioral features
- Separate models for one-time vs repeat users
- Spending bucket classification instead of point regression

---

## Conclusion
This project demonstrates that **clean, leakage-free models often produce modest performance**, but offer far greater real-world value.

Rather than chasing inflated metrics, the focus is placed on:
- Honest modeling
- Strong reasoning
- Business-aligned insights

---

## Author Notes
This project is designed to reflect **day-to-day work of a Data Scientist**, emphasizing decision-making, trade-offs, and interpretability over raw model scores.
