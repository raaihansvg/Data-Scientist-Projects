# COVID-19 in Indonesia: A Data-Driven Provincial Risk Analysis

## Overview

Project ini bertujuan untuk memahami dinamika penyebaran COVID-19 di Indonesia melalui pendekatan data science berbasis provinsi. Analisis dilakukan dalam tiga tahap utama: eksplorasi time-series untuk memahami pola gelombang pandemi, segmentasi provinsi menggunakan unsupervised learning (K-Means clustering), serta pengujian hubungan antara kepadatan penduduk dan tingkat kasus menggunakan linear regression.

Project ini tidak hanya berfokus pada visualisasi data, tetapi juga pada interpretasi analitis untuk menjawab pertanyaan penting:

- Apakah kepadatan penduduk menjadi faktor dominan dalam penyebaran COVID-19?
- Apakah semua provinsi memiliki karakteristik risiko yang sama?
- Bagaimana segmentasi risiko antar wilayah dapat dipetakan menggunakan machine learning?

---

## Key Insights

- Terdapat **tiga gelombang utama pandemi** di Indonesia, dengan lonjakan terbesar terjadi pada periode varian Delta (2021) dan Omicron (awal 2022).
- **DKI Jakarta muncul sebagai outlier yang sangat berbeda dari provinsi lain**, terutama dari sisi kasus per juta dan kepadatan penduduk.
- Provinsi di Pulau Jawa cenderung berada dalam cluster berisiko tinggi.
- Hasil regression menunjukkan bahwa **Population Density hanya menjelaskan sekitar 20% variasi kasus antar provinsi (R² ≈ 0.20)**.
- Faktor non-demografis seperti mobilitas, kebijakan pembatasan sosial, testing rate, dan perilaku masyarakat kemungkinan memiliki pengaruh yang lebih besar.

---

## Workflow Analysis

### 1. Data Preprocessing

Tahap awal mencakup:

- Pembersihan missing values dan duplikasi
- Konversi tipe data ke format numerik
- Pemisahan data nasional dan data provinsi
- Seleksi fitur relevan untuk analisis

Fitur utama yang digunakan dalam analisis lanjutan:

- Total Cases per Million
- Total Deaths per Million
- Case Fatality Rate
- Population Density

---

### 2. Growth Factor Analysis

Growth Factor dihitung untuk mengamati percepatan penyebaran kasus.

Namun, ditemukan adanya outlier ekstrem pada kolom *New Cases* yang menyebabkan grafik growth factor kurang stabil. Karena sudah dilakukan 7-day moving average untuk memperjelas tren, analisis growth factor tidak dijadikan fokus utama dalam interpretasi akhir.

Pendekatan ini menunjukkan selektivitas dalam memilih metode yang relevan secara analitis.

---

### 3. Clustering Provinsi (K-Means)

Untuk memahami segmentasi risiko antar provinsi, digunakan algoritma K-Means dengan fitur:

- Total Cases per Million
- Total Deaths per Million
- Case Fatality Rate
- Population Density

Data dilakukan scaling sebelum clustering untuk menghindari bias skala.

#### Penentuan Jumlah Cluster

Metode Elbow digunakan untuk menentukan nilai k optimal.  
Hasil menunjukkan bahwa **k = 4** memberikan keseimbangan antara kompleksitas model dan penurunan inertia.

Empat cluster tersebut merepresentasikan:

1. High density – high case province (contoh: DKI Jakarta)
2. High transmission – medium density provinces (beberapa wilayah Jawa)
3. Moderate risk provinces
4. Low impact provinces

---

### 4. Dimensionality Reduction with PCA

Karena clustering dilakukan dalam 4 dimensi, PCA digunakan untuk mereduksi dimensi menjadi 2 komponen utama agar dapat divisualisasikan dalam scatter plot.

Hasil PCA menunjukkan:

- DKI Jakarta terpisah jelas sebagai outlier.
- Provinsi di Pulau Jawa membentuk cluster tersendiri.
- Wilayah luar Jawa cenderung terkonsentrasi dalam cluster risiko rendah.

Visualisasi ini memperjelas struktur segmentasi yang tidak terlihat langsung dari tabel data.

---

### 5. Statistical Analysis: Correlation & Linear Regression

Tujuan analisis ini adalah menguji apakah kepadatan penduduk mempengaruhi total kasus COVID-19 per juta penduduk.

Model Linear Regression dibangun dengan:

- X = Population Density  
- y = Total Cases per Million  

Hasil:

- R² ≈ 0.206

Artinya, hanya sekitar 20% variasi kasus antar provinsi yang dapat dijelaskan oleh kepadatan penduduk.

Meskipun terdapat hubungan positif, density bukan faktor dominan dalam menentukan tingkat kasus. Variasi sisanya kemungkinan dipengaruhi oleh faktor lain seperti mobilitas, kebijakan PPKM, testing rate, vaksinasi, dan perilaku masyarakat.

---

## Visualizations

Beberapa visual utama dalam project ini:

- Time Series Plot Total Cases  
- 7-Day Moving Average  
- Elbow Plot (penentuan jumlah cluster)  
- PCA Scatter Plot (visualisasi cluster 2D)  
- Regression Plot (Population Density vs Cases per Million)

Setiap visual diinterpretasikan secara kontekstual untuk mendukung insight yang diperoleh.

---

## Conclusion

Pandemi COVID-19 di Indonesia tidak dapat dijelaskan hanya oleh satu variabel seperti kepadatan penduduk.

Meskipun population density memiliki kontribusi terhadap variasi kasus antar provinsi, pengaruhnya relatif terbatas. Clustering menunjukkan adanya segmentasi risiko yang jelas antar wilayah, terutama perbedaan signifikan antara provinsi dengan urbanisasi tinggi dan wilayah berpopulasi lebih jarang.

Analisis ini menegaskan bahwa dinamika pandemi merupakan fenomena multidimensional yang dipengaruhi oleh kombinasi faktor geografis, kebijakan, dan perilaku sosial.

Project ini merepresentasikan pendekatan analitis yang sistematis dalam menggabungkan time-series analysis, unsupervised learning, dan statistical modeling untuk menghasilkan insight berbasis data.
