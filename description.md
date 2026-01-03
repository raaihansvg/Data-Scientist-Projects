# Analisis Kemiskinan di Indonesia — Regresi dan Clustering (Data BPS)

## Gambaran Umum
Project ini bertujuan untuk menganalisis kondisi **kemiskinan di Indonesia** menggunakan pendekatan **analisis data** dan **machine learning** dengan data resmi dari **Badan Pusat Statistik (BPS)**.

Analisis dilakukan pada tingkat **provinsi**, dengan fokus untuk memahami pola kemiskinan, hubungan antar variabel, serta pengelompokan wilayah berdasarkan karakteristik kemiskinan. Project ini tidak hanya berfokus pada performa model, tetapi juga pada **interpretasi sosial dan pemahaman konteks data**.

Ruang lingkup analisis meliputi:
- Data cleaning dan preprocessing  
- Exploratory Data Analysis (EDA)  
- Pemodelan regresi  
- Analisis clustering  
- Visualisasi spasial (peta provinsi)  
- Interpretasi hasil dan keterbatasan analisis  

---

## Struktur Repository

| File / Folder | Deskripsi |
|---------------|----------|
| `Poverty-Analysis-Indonesia.ipynb` | Notebook utama berisi EDA, modeling, clustering, dan visualisasi |
| `README.md` | Dokumentasi project |
| `data/` | Dataset kemiskinan Indonesia (BPS) |

---

## Dataset
Dataset yang digunakan bersumber dari **Badan Pusat Statistik (BPS)** dan berisi data **jumlah serta persentase penduduk miskin** di Indonesia.

Karakteristik dataset:
- Level data: Provinsi  
- Bentuk data: Tabel statistik  
- Periode data: 2015–2024  
- Variabel utama:
  - Jumlah penduduk miskin  
  - Persentase penduduk miskin  
  - Tahun  
  - Provinsi  

Dataset disertakan langsung di folder `data/` untuk menjaga **reproducibility** analisis.

---

## Alur Analisis

### Data Preprocessing
Tahapan preprocessing yang dilakukan antara lain:
- Penggabungan beberapa dataset tahunan  
- Penanganan missing values  
- Penyesuaian tipe data dan standarisasi fitur numerik  
- Pemeriksaan distribusi data dan potensi outlier  

---

### Exploratory Data Analysis (EDA)
EDA dilakukan untuk memahami karakteristik awal data, meliputi:
- Distribusi tingkat kemiskinan antar provinsi  
- Hubungan antar variabel numerik  
- Perbandingan kondisi kemiskinan antar wilayah  

Hasil EDA menunjukkan adanya **ketimpangan regional** dan distribusi data yang tidak simetris.

---

### Pemodelan Regresi
Model regresi digunakan untuk mencoba memprediksi **persentase kemiskinan** di tingkat provinsi.

Pendekatan yang digunakan:
- Model regresi dasar (baseline)  
- Random Forest Regression  

Evaluasi model dilakukan menggunakan:
- R² Score  
- Mean Absolute Error (MAE)  

Hasil regresi menunjukkan performa yang terbatas, yang mengindikasikan bahwa kemiskinan dipengaruhi oleh banyak faktor non-numerik dan struktural yang tidak sepenuhnya tercakup dalam data. Oleh karena itu, regresi digunakan sebagai **analisis pendukung**, bukan sebagai alat prediksi utama.

---

### Analisis Clustering
Clustering digunakan untuk **profiling wilayah**, bukan untuk prediksi.

Pendekatan yang dilakukan:
- Agregasi data per provinsi  
- Feature scaling  
- K-Means Clustering (K = 3)  
- Penentuan jumlah cluster menggunakan Elbow Method  

Interpretasi cluster:
- Cluster 0: Tingkat kemiskinan rendah dan populasi penduduk miskin relatif kecil  
- Cluster 1: Tingkat kemiskinan tinggi dan populasi penduduk miskin sedang  
- Cluster 2: Tingkat kemiskinan sedang dengan populasi penduduk miskin paling besar akibat jumlah penduduk yang tinggi  

---

## Visualisasi Spasial
Hasil clustering divisualisasikan dalam bentuk **peta provinsi Indonesia** menggunakan data GeoJSON.

Visualisasi ini menunjukkan bahwa:
- Kemiskinan tidak tersebar secara acak  
- Wilayah dengan populasi besar memiliki beban kemiskinan absolut yang signifikan  
- Terdapat pola regional yang jelas dalam karakteristik kemiskinan di Indonesia  

---

## Hasil dan Insight
- Model regresi memiliki nilai R² yang relatif rendah  
- Clustering lebih efektif untuk mengungkap pola struktural kemiskinan  
- Visualisasi spasial memperkuat interpretasi hasil clustering  

Pendekatan unsupervised learning terbukti lebih informatif untuk eksplorasi pola dibandingkan prediksi numerik semata.

---

## Kesimpulan
Project ini menunjukkan bahwa permasalahan sosial seperti kemiskinan **tidak dapat sepenuhnya dijelaskan oleh model numerik sederhana**.  

Meskipun performa prediksi terbatas, kombinasi **EDA, clustering, dan pemetaan spasial** mampu memberikan insight yang lebih bermakna dalam memahami kemiskinan di Indonesia secara struktural dan regional.

---

## Keterbatasan
- Faktor sosial, budaya, dan kebijakan tidak sepenuhnya tercermin dalam data  
- Data bersifat agregat (tingkat provinsi), bukan individu  
- Hasil analisis tidak ditujukan sebagai dasar kebijakan langsung  


---

## Penulis
Raihan Lazuardi  
Data Science & Machine Learning Enthusiast
