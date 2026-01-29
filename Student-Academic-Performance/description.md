#  End-to-End Student Final GPA Prediction

![Python](https://img.shields.io/badge/Python-3.9+-blue)
![Scikit-learn](https://img.shields.io/badge/Scikit--Learn-ML-orange)
![Status](https://img.shields.io/badge/Project-End--to--End-success)
![Dataset](https://img.shields.io/badge/Dataset-1M%20Rows-green)

##  Overview
This is an **end-to-end machine learning project** that predicts **students' Final GPA** using a large-scale academic dataset with **1 million records**.

Project ini mencakup seluruh pipeline Data Science, mulai dari **Exploratory Data Analysis (EDA)** hingga **model inference**, sehingga mencerminkan workflow dunia nyata.

---

## End-to-End Pipeline
This project covers the full ML lifecycle:

1. Data loading & exploration  
2. Exploratory Data Analysis (EDA)  
3. Feature engineering (domain-driven)  
4. Train–validation split  
5. Data preprocessing (scaling with pipeline)  
6. Model training & evaluation  
7. Model interpretation  
8. Model inference on new student data  

---

##  Objective
- Predict students' Final GPA accurately
- Understand key factors influencing academic performance
- Build a **stable, interpretable, and inference-ready ML pipeline**

---

##  Dataset
- Dataset: `student_academic_performance_1M`
- Rows: **1,000,000**
- Features: **52**
- Target variable: **final_gpa**

The dataset includes academic scores, study habits, LMS activity, health indicators, and socio-economic factors.

---

##  Feature Engineering
To improve model performance and interpretability, several engineered features were created:

- **academic_knowledge**
- **academic_engagement**
- **overall_academic_index**
- **study_efficiency**
- **stress_health_index**

Feature engineering was applied consistently during training and inference using a dedicated preparation function.

---

##  Model
- Algorithm: **Ridge Regression**
- Preprocessing: **StandardScaler**
- Implementation: **Scikit-learn Pipeline**

Ridge Regression was selected to balance **performance and interpretability**, especially on a large dataset.

---

##  Model Performance
Model evaluation results:

| Metric | Value |
|------|------|
| R² | ~0.72 |
| MAE | ~0.27 |
| RMSE | ~0.34 |

The model explains most of the variation in GPA with relatively low prediction error.

---

## Key Insights
The most influential factors affecting Final GPA are:
- **Study efficiency**
- **LMS activity**
- **Digital & computer skills**
- **Attendance rate**
- **Previous GPA**

This indicates that **learning effectiveness and consistency** matter more than raw study duration.

---

##  Inference Example
The trained pipeline supports direct inference on new student data.

```python
Predicted Final GPA: 3.78
```


This result indicates a **high-performing student** based on learned patterns from historical data.

---

## Conclusion
This end-to-end project demonstrates that:
- Domain-driven feature engineering significantly improves prediction quality
- Interpretable models can perform well on large datasets
- A clean ML pipeline ensures reliable training and inference

The final model is **production-ready, explainable, and scalable**.

---

## Tech Stack
- Python
- Pandas, NumPy
- Scikit-learn
- Matplotlib, Seaborn
- Google Colab

---

##  Author
Built as an end-to-end Data Science portfolio project.

