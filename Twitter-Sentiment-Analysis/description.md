# Twitter Sentiment Analysis – Twitter Dataset


Multi-class sentiment classification on noisy Twitter data, built using **classical NLP + Linear SVM**.

This project is not just about modeling —  
it is about **surviving messy, duplicated, spam-filled, sarcastic Twitter data** and turning it into a **reliable sentiment classifier**.

---

## Problem Statement

Twitter data is:
- noisy
- repetitive
- full of URLs, shortlinks, mentions
- full of sarcasm
- inconsistent in grammar
- often duplicated or near duplicated

The objective of this project is to **predict sentiment** accurately while:
- avoiding **data leakage**
- handling **negation & sarcasm**
- removing **spam & irrelevant content**
- keeping the pipeline **production-ready**

### Target Classes
- **Negative**
- **Positive**
- **Neutral**
- **Irrelevant**

---

## Dataset Summary

| Description | Count |
|------------|-------|
| Raw tweets | 74681 |
| After cleaning & filtering | ~64,990 |
| Classes | 4 |

Key columns:
- `Text` → raw tweet
- `Sentiment` → label
- `Clean_Text` → cleaned tweet (final feature)
- `Label` → encoded sentiment

---

##  Files in this folder

| File                         | Deskripsi                                 |
|------------------------------|---------------------------------------------|
| `Twitter_Sentiment_Analysis.ipynb` | Notebook utama      |
| `description.md`                  | Dokumentasi/Penjelasan project                        |
| `Data`                  | Dataset                       |
| `Model`                  | Model Project                       |


### Final Performance

| Class      | Precision | Recall | F1    |
| ---------- | --------- | ------ | ----- |
| Negative   | ~0.92     | ~0.94  | ~0.93 |
| Positive   | ~0.91     | ~0.91  | ~0.91 |
| Neutral    | ~0.91     | ~0.90  | ~0.90 |
| Irrelevant | ~0.90     | ~0.88  | ~0.89 |

Accuracy: ~91%
--- 

## Demo Prediction

Gunakan fungsi berikut di notebook:

```python
predict_text("Not bad I think")
#contoh Output
{'prediction': 'neutral'}

predict_text("Nvidia delivers excellent performance with the new GPU")
#contoh Output
{'prediction': 'positive'}

predict_text("I regret buying this GPU, worst purchase ever")
#contoh Output
{'prediction': 'negative'}

predict_text("Amazing update, now my PC crashes twice as fast")
#contoh Output
{'prediction': 'negative'}

#contoh Output
{'prediction': 'negative'}

```

---











