a#  Fault Type Classification — Rotating Equipment Analysis

## Project Overview

Project ini bertujuan untuk mendeteksi jenis kerusakan pada **rotating equipment** berdasarkan data sensor:

- Vibration (X, Y, Z)
- Acoustic Level
- Temperature

Model mengklasifikasikan kondisi mesin ke dalam **4 kelas**:

- Normal
- Bearing Fault
- Imbalance
- Overheating

Workflow project:

- Exploratory Data Analysis (EDA)
- Data preprocessing & cleaning
- Feature scaling
- Training beberapa model (RF, HGB, MLP)
- Model selection
- Full evaluation
- Submission file generation

---

## Files in This Folder

| File | Deskripsi |
|------|-----------|
| `Fault_Type.ipynb` | Notebook utama (EDA → preprocessing → modeling → evaluation) |
| `models` | Folder tempat model final & file pendukung |
| `data`  | Folder tempat penyimpanan data |
| `submission_predictions.csv` | Prediksi final untuk file submission |
| `description.md` | Dokumentasi project |


---



##  Installation

### 1. Clone repository

```bash
git clone https://github.com/username/Fault-Type-Classification.git
cd Fault-Type-Classification
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

Jika belum punya file, buat `requirements.txt` seperti:

```
pandas
numpy
scikit-learn
matplotlib
seaborn
joblib
```

---

## How to Run

### 1. Buka notebook utama

```bash
jupyter notebook Fault_Type.ipynb
```

### 2. Jalankan pipeline lengkap:
- EDA
- Preprocessing
- Train model
- Evaluation
- Save artifacts

---

##  Modeling Summary

Model yang diuji:

| Model              | Status       | Notes                          |
|-------------------|--------------|--------------------------------|
| Random Forest      | Best Model | Stable & akurasi 100%          |
| HGBClassifier      |  Tested     | Tidak mengalahkan RF           |
| MLPClassifier      |  Tested     | Tuning 18 kombinasi, 100% val  |

---

##  Model Evaluation

| Metric     | Score |
|------------|-------|
| Accuracy   | 1.00  |
| Precision  | 1.00  |
| Recall     | 1.00  |
| F1-score   | 1.00  |

Confusion matrix menunjukkan prediksi **sempurna** pada semua kelas.

---

##  Saved Artifacts

File tersimpan di folder `models/`:

| File                  | Fungsi                                      |
|-----------------------|----------------------------------------------|
| `final_model.pkl`     | Model terbaik untuk inference                |
| `scaler_full.pkl`     | StandardScaler fit pada full dataset         |
| `label_encoder.pkl`   | Encoder label kelas                          |
| `features_list.pkl`   | Daftar fitur yang digunakan                  |
| `training_summary.txt`| Ringkasan training & hasil tuning            |

---

##  Generate Submission

### 1. Jalankan inference pada `solution.csv`

Output file otomatis dibuat:

```
submission_predictions.csv
```



| id | Fault_Type |
|----|------------|
| 0  | Normal     |
| 1  | Normal     |
| ...| ...        |

---






