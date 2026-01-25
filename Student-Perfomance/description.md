# Student Performance Prediction using Linear Regression

## Project Overview
This project aims to predict a student's **Performance Index** based on several academic and lifestyle-related factors using **Linear Regression**.  
The model is built with a strong focus on:
- Proper data preprocessing
- Model interpretability
- Robust evaluation
- Clean and reusable inference pipeline

The final model achieves **excellent performance** while remaining simple and explainable.

---

##  Dataset Description
The dataset contains information about students and their academic habits.

###  Features
| Feature | Description | Type |
|------|------------|------|
| Hours Studied | Number of hours spent studying | Numerical |
| Previous Scores | Student's previous exam scores | Numerical |
| Sleep Hours | Average hours of sleep | Numerical |
| Extracurricular Activities | Participation in extracurricular activities (Yes/No) | Categorical |
| Sample Question Papers Practiced | Number of practice papers solved | Numerical |

###  Target
- **Performance Index** (numerical score representing overall student performance)

---

##  Data Preprocessing
To ensure consistency between training and inference, preprocessing is handled using a **scikit-learn Pipeline**:

- **Numerical Features**
  - Standardized using `StandardScaler`
- **Categorical Features**
  - Binary feature (`Yes` / `No`) encoded using `OrdinalEncoder`
  - Explicit category ordering: `No → 0`, `Yes → 1`

This approach prevents data leakage and guarantees consistent transformations during prediction.

---

##  Model Selection
Several models were evaluated, including:
- Linear Regression
- Ridge Regression
- Random Forest Regression

###  Final Choice: **Linear Regression**
Linear Regression was selected because:
- It achieved the **lowest RMSE**
- It showed **high stability** across cross-validation
- Residual analysis confirmed that linear assumptions were satisfied
- It provides strong **interpretability**

---

##  Model Performance
The final model achieved the following metrics:

- **R²:** ~0.989  
- **RMSE:** ~2.05  
- **MAE:** ~1.61  

### Interpretation
- The model explains approximately **98.9%** of the variance in the target variable
- Prediction errors are small relative to the target scale (0–100)
- Performance is stable, indicating no overfitting

---

## Feature Importance (Linear Interpretation)
Since this is a linear model, feature importance is interpreted through **model coefficients** (after standardization):

1. **Previous Scores** – strongest predictor  
2. **Hours Studied** – strong positive influence  
3. Sleep Hours  
4. Extracurricular Activities  
5. Sample Question Papers Practiced  

These results align well with domain knowledge in education.

---

## Residual Analysis
Residual diagnostics show:
- Residuals are centered around zero
- No visible non-linear patterns
- Approximately constant variance across predictions

This confirms that the key assumptions of Linear Regression are reasonably satisfied.

---

##  Model Inference (Usage Example)

The trained pipeline can be used directly for prediction with dictionary-based input.
```python
new_student = {
    "Hours Studied": 9,
    "Previous Scores": 60,
    "Sleep Hours": 6,
    "Extracurricular Activities": "Yes",
    "Sample Question Papers Practiced": 10
}

predicted_score = model.predict(pd.DataFrame([new_student]))[0]
print(f"Predicted Performance Index: {predicted_score:.2f}")
```
## Prediction Output
```python


Predicted Performance Index: 96.96

```
## Project Structure
```
├── data/
│   └── Student_Performance.csv
├── notebooks/
│   └── analysis.ipynb
├── model/
│   └── student_performance_model.pkl
└── README.md
```
---

##  Author
**[Raihan Lazuardi]**  
Aspiring Data Scientist / Machine Learning Practitioner






