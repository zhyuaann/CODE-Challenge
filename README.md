# Smart Society Starter - AI Mobility Prediction

Proyek ini dibuat sebagai bagian dari kompetisi **Smart Society Starter - Tahap Penyisihan**, yang menantang peserta untuk membangun model kecerdasan buatan guna memprediksi **jumlah perjalanan harian (`trips_thousands`)** berdasarkan data multi-sumber: demografi, aktivitas urban, cuaca, dan infrastruktur transportasi.

## Deskripsi Proyek

Mobilitas perkotaan merupakan salah satu pilar utama kota cerdas (*smart city*). Proyek ini bertujuan untuk:

- Memprediksi jumlah perjalanan harian per zona dan tanggal.
- Menggunakan data historis serta fitur-fitur yang mencerminkan aspek kehidupan kota (cuaca, kepadatan penduduk, fasilitas transportasi, dll).
- Memberikan hasil prediksi dalam format `.csv` sesuai ketentuan kompetisi Kaggle.

---

## Metodologi

Model dibangun dengan pendekatan:

1. **Data Preprocessing**
   - Imputasi nilai numerik menggunakan median.
   - Imputasi nilai kategorikal menggunakan modus.
   - Encoding variabel kategorikal (manual + one-hot encoding).
   - Clipping untuk outlier pada fitur `precipitation`.
   - Normalisasi menggunakan `StandardScaler`.

2. **Feature Engineering: Broad Learning System (BLS)**
   - **Polynomial Features (degree=2)** untuk interaksi non-linear.
   - **Feature Mapping Node (FMN)** dan **Enhancement Node (ENH)** menggunakan random projection + aktivasi `tanh`.
   - Penggabungan semua fitur: awal, polinomial, FMN, dan ENH.

3. **Model Building**
   - Regressor: `KNeighborsRegressor`
   - Baseline parameter: `n_neighbors=5`, `weights='uniform'`
   - Evaluasi menggunakan RMSE (Root Mean Squared Error)

4. **Hyperparameter Tuning (Opsional)**
   - Tuning dilakukan dengan `GridSearchCV` (tapi tidak dipakai untuk submission karena overfitting).

---

## Hasil

- **RMSE Baseline Model (KNN + BLS):** `13.1322`
- **Model hasil tuning** menunjukkan overfitting, sehingga **baseline model digunakan untuk submission final**.
- Submission format sesuai `sample_submission.csv`.

---

## Tools dan Library

- Python 3.10+
- Pandas, NumPy, Matplotlib, Seaborn
- Scikit-Learn
- Jupyter Notebook
