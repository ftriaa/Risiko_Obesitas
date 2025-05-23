# 📊 Klasifikasi Risiko Obesitas Berdasarkan Hasil Klastering

Proyek ini bertujuan untuk mengelompokkan individu berdasarkan tingkat risiko obesitas menggunakan algoritma *clustering* dan melakukan prediksi klasifikasi menggunakan model *machine learning*. Data diperoleh dari [Kaggle](https://www.kaggle.com/datasets/aravindpcoder/obesity-or-cvd-risk-classifyregressorcluster), terdiri dari lebih dari 20.000 entri dengan informasi gaya hidup, kebiasaan makan, dan aktivitas fisik.

## Tujuan Proyek

1. Mengelompokkan individu ke dalam kategori risiko obesitas menggunakan **KMeans Clustering**.
2. Melatih model **Random Forest** dan **K-Nearest Neighbor** untuk memprediksi kategori risiko obesitas.
3. Mengevaluasi performa model dan memberikan rekomendasi kesehatan berdasarkan hasil analisis.

## Dataset

Dataset terdiri dari 20.758 entri dan 17 kolom, berisi informasi demografis, kebiasaan makan, dan gaya hidup responden

| No. | Kolom                            | Jumlah Data | Tipe Data | Keterangan                                 |
| --- | -------------------------------- | ----------- | --------- | ------------------------------------------ |
| 1   | `id`                             | 20758       | int64     | ID unik setiap individu                    |
| 2   | `Gender`                         | 20758       | object    | Jenis kelamin (Male/Female)                |
| 3   | `Age`                            | 20758       | float64   | Usia responden                             |
| 4   | `Height`                         | 20758       | float64   | Tinggi badan (meter)                       |
| 5   | `Weight`                         | 20758       | float64   | Berat badan (kg)                           |
| 6   | `family_history_with_overweight` | 20758       | object    | Riwayat keluarga obesitas (yes/no)         |
| 7   | `FAVC`                           | 20758       | object    | Konsumsi makanan berkalori tinggi (yes/no) |
| 8   | `FCVC`                           | 20758       | float64   | Konsumsi sayur (skala 0–3)                 |
| 9   | `NCP`                            | 20758       | float64   | Frekuensi makan utama per hari             |
| 10  | `CAEC`                           | 20758       | object    | Kebiasaan ngemil                           |
| 11  | `SMOKE`                          | 20758       | object    | Merokok (yes/no)                           |
| 12  | `CH2O`                           | 20758       | float64   | Konsumsi air putih (liter per hari)        |
| 13  | `SCC`                            | 20758       | object    | Memantau kalori (yes/no)                   |
| 14  | `FAF`                            | 20758       | float64   | Aktivitas fisik per minggu (jam)           |
| 15  | `TUE`                            | 20758       | float64   | Waktu layar harian (jam)                   |
| 16  | `CALC`                           | 20758       | object    | Konsumsi alkohol                           |
| 17  | `MTRANS`                         | 20758       | object    | Moda transportasi utama                    |


## Metode & Tahapan

### 1. **Clustering (KMeans)**

* **Tujuan**: Menentukan kategori risiko obesitas (`High - Passive`, `Medium - Semi Active`, `Low - Active`).
* **Fitur yang digunakan**: BMI, rasio berat dan aktivitas, skor gaya hidup, dll.
* **Hasil Cluster**:

| Kategori             | BMI   | Weight/FAF | Lifestyle Score | Obesity Score |
| -------------------- | ----- | ---------- | --------------- | ------------- |
| High - Passive       | 39.11 | 104.96     | 0.38            | 20.15         |
| Medium - Semi Active | 35.50 | 56.08      | 0.76            | 18.32         |
| Low - Active         | 23.80 | 27.88      | 0.98            | 12.36         |

### 2. **Klasifikasi**

* Setelah label cluster dibuat, dilakukan pelatihan model klasifikasi untuk memprediksi kategori risiko:

  * Model: **Random Forest** & **K-Nearest Neighbors (KNN)**
  * Teknik tuning hyperparameter: Grid Search

### 3. **Evaluasi**

* **Random Forest**:

  * Akurasi: **99.92%**
  * Precision & Recall: **1.00** untuk semua kelas

* **KNN**:

  * Akurasi meningkat setelah tuning
  * Precision dan recall lebih rendah di beberapa kelas (terutama cluster 2)
  * Cenderung overfitting

## Kesimpulan

* **Random Forest** menjadi model terbaik untuk klasifikasi risiko obesitas.
* Model machine learning yang telah dilatih bisa memprediksi siapa saja yang berisiko tinggi terkena obesitas (misalnya berdasarkan pola makan, aktivitas fisik, usia, berat badan, dll).
* Rekomendasi: eksplorasi model lain (XGBoost, LightGBM), dan validasi menggunakan data baru.

