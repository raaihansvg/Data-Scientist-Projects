# IMDB Movie Reviews — Sentiment Analysis
<p align="center"> <img src="https://upload.wikimedia.org/wikipedia/commons/6/69/IMDB_Logo_2016.svg" width="200"> </p>

##  Project Overview
Project ini bertujuan untuk mengklasifikasikan review film dari IMDB menjadi **positive** atau **negative** menggunakan metode **Natural Language Processing (NLP)**.

Dataset berisi **50.000 review teks**, masing-masing sudah memiliki label sentimen.

Project ini mencakup:

- Data cleaning & text preprocessing  
- TF-IDF Vectorization  
- Pembangunan model Logistic Regression  
- Evaluasi model  
- Demo prediksi (inference)

---

##  Files in this folder

| File                         | Deskripsi                                 |
|------------------------------|---------------------------------------------|
| `Sentiment_Analysis_clean.ipynb` | Notebook utama      |
| `description.md`                  | Dokumentasi/Penjelasan project                        |




---

## 📊 Dataset
Dataset **tidak disertakan** karena ukurannya melebihi batas upload GitHub.

Dataset bisa diunduh dari:  
https://www.kaggle.com/datasets/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews

Setelah di download , simpan di:
data/IMDB Dataset.csv


---

##  NLP Pipeline

###  Preprocessing
- lowercase  
- menghapus HTML tags  
- menghapus URL  
- menghapus karakter non huruf  
- menghapus stopwords  
- **MENYIMPAN kata negasi** (not, no, never, nor)  
- menyimpan hasil ke kolom `clean`  

---

###  Feature Extraction — TF-IDF
Konfigurasi TF-IDF:
- max_features = 40000
- ngram_range = (1, 2)
- mengubah teks menjadi numerik

---

###  Modeling
Model utama: **Logistic Regression(solver='saga', max_iter=1000)**

**Alasan pemilihan model:**

- stabil  
- cepat  
- performa bagus untuk text classification  

---

###  Model Evaluation

| Metric     | Score |
|------------|--------|
| Accuracy   | 0.90 |
| Precision  | 0.90 |
| Recall     | 0.90 |
| F1-score   | 0.90 |

Model memiliki performa konsisten di kedua kelas.

---

## Demo Prediction

Gunakan fungsi berikut di notebook:

```python
predict_text("this movie was absolutely amazing!")
#contoh Output
Text: this movie was absolutely amazing!
Cleaned: movie absolutely amazing
Prediction: positive | Confidence: 0.98
```

---

### Kesimpulan
Project ini nunjukin bahwa dengan teknik NLP dasar seperti TF-IDF dan Logistic Regression, kita sudah bisa bikin model yang stabil dan akurat buat nentuin sentimen review film. Setelah data dibersihin dan diolah dengan benar, modelnya bisa ngerti mana review yang positif dan mana yang negatif dengan akurasi sekitar 90%.

Intinya: prosesnya simpel, hasilnya kuat, dan model ini sudah cukup buat banyak kebutuhan real-world seperti analisis review atau monitoring opini. Project ini juga bisa jadi dasar buat ngembangin model NLP yang lebih advanced nantinya.

## Limitations
Model dasar TF-IDF + Regresi Logistik mengalami kesulitan dengan kata yang berbasis negasi tertentu seperti "not bad" dan sebagai nya, dimana kombinasi linier fitur masih didominasi dengan prediksi negatif.


