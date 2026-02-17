# Financial Sentiment Analysis using FinBERT

This repository implements a **sentiment analysis model** tailored specifically for financial texts, such as stock market news, earnings reports, and financial tweets. The project leverages the **FinBERT** architecture, a specialized BERT model pre-trained on financial corpora, to better capture the nuances of business language.

---

##  Project Overview

The goal of this project is to classify financial statements into three categories:

* **Positive**
* **Negative**
* **Neutral**

Financial language often differs from general daily language. For example, the word *"lower"* could be **positive** in *"lower inflation"* but **negative** in *"lower revenue"*. Hence, a domain-specific model is necessary.

---

## Technical Workflow

1. **Model Selection**: Using `ProsusAI/finbert` via the Hugging Face Transformers library.
2. **Environment**: Implemented in **Google Colab** using **Python**.
3. **Pipeline**: Utilizes Hugging Face's `pipeline` abstraction for efficient inference.
4. **Custom Prediction**: Includes a `predict(text)` function that returns both **labels** and **confidence scores**.

---

## Dataset & Performance

* **Dataset Size**: ~5,000 entries
* **Condition**: High class imbalance (common in financial data where Neutral often dominates)
* **Metric**: Achieved **F1-Score of 0.76**

> **Why 0.76 is a solid result:**
> On imbalanced datasets, F1-Score is more informative than raw accuracy. A score of 0.76 shows that the model can distinguish sentiment classes effectively despite limited and imbalanced data, maintaining a healthy balance between Precision and Recall.

---

## Usage Example

```python
text = "$BBCA reported Q4 results in line with guidance; dividend announcement expected in March."
result = predict(text)
print(result)
```

**Expected Output Example:**

```python
{'label': 'Neutral', 'score': 0.85}
```



---

##  Conclusion

This project demonstrates that even with a **limited dataset of 5,000 samples and imbalance data**, a domain-specific transformer model like **FinBERT** can achieve a **robust F1-Score of 0.76**.
