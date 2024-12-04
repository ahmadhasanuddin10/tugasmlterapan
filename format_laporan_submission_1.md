
# **Prediksi Harga Properti - Ahmad Hasanuddin**

## **Domain Proyek**
Prediksi harga properti adalah aspek penting dalam pasar real estate yang membantu berbagai pihak, termasuk pembeli, penjual, dan investor, dalam pengambilan keputusan yang tepat. Fluktuasi harga yang dipengaruhi oleh berbagai faktor seperti lokasi, fasilitas, dan luas bangunan sering kali sulit diprediksi secara manual. Oleh karena itu, penggunaan model machine learning menjadi solusi untuk menghasilkan prediksi yang akurat dan efisien.

**Referensi:**
1. [DETERMINAN HARGA RUMAH DI INDONESIA](https://jurnal.uns.ac.id/dinamika/article/download/45934/28895)
2. [Survei Harga Properti Residensial BI](https://www.bi.go.id/id/publikasi/laporan/Documents/SHPR_Tw_I_2024.pdf)

---

## **Business Understanding**
### **Problem Statements**
1. Bagaimana memprediksi harga properti berdasarkan fitur seperti luas bangunan, jumlah kamar tidur, fasilitas, dan lokasi?
2. Bagaimana meningkatkan akurasi model prediksi harga properti dengan menggunakan algoritma machine learning yang tepat?

### **Goals**
1. Menghasilkan model machine learning yang mampu memprediksi harga properti dengan akurasi tinggi.
2. Mengoptimalkan kinerja model melalui teknik pemilihan fitur dan hyperparameter tuning.

### **Solution Statements**
- **Model yang Digunakan:** 
  Menggunakan algoritma seperti Random Forest Regressor, XGBoost, dan Linear Regression untuk memodelkan data.
- **Optimalisasi:** 
  Hyperparameter tuning dengan GridSearchCV untuk menemukan konfigurasi parameter terbaik, seperti `n_estimators` dan `max_depth`.

---

## **Data Understanding**
Dataset yang digunakan berisi lebih dari 500 baris data mengenai properti, mencakup harga, luas bangunan, jumlah kamar, dan fasilitas lainnya. Dataset diunduh dari [Housing Price Prediction Dataset - Kaggle](https://www.kaggle.com/datasets/harishkumardatalab/housing-price-prediction).

### **Deskripsi Fitur**
| **Nama Fitur**       | **Deskripsi**                                      |
|-----------------------|----------------------------------------------------|
| `price`              | Harga properti (target variabel).                  |
| `area`               | Luas bangunan dalam sqft.                          |
| `bedrooms`           | Jumlah kamar tidur.                                |
| `bathrooms`          | Jumlah kamar mandi.                                |
| `stories`            | Jumlah lantai.                                     |
| `mainroad`           | Properti di jalan utama (1 = Ya, 0 = Tidak).       |
| `guestroom`          | Properti memiliki ruang tamu (1 = Ya, 0 = Tidak).  |
| `basement`           | Properti memiliki ruang bawah tanah (1 = Ya, 0 = Tidak). |
| `airconditioning`    | Properti memiliki pendingin udara (1 = Ya, 0 = Tidak). |
| `parking`            | Jumlah tempat parkir.                              |
| `prefarea`           | Properti di daerah preferensi (1 = Ya, 0 = Tidak). |
| `furnishingstatus`   | Status furnitur (0 = Tidak Furnitur, 1 = Semi-Furnitur, 2 = Furnitur Lengkap). |

---

## **Data Preparation**
### **Tahapan:**
1. **Encoding Variabel Kategorikal:**
   - Variabel seperti `mainroad`, `guestroom`, dan `prefarea` dikonversi menjadi numerik menggunakan Label Encoding.
2. **Menangani Missing Values:**
   - Nilai yang hilang pada fitur numerik diimputasi dengan rata-rata, sedangkan fitur kategorikal menggunakan modus.
3. **Menghapus Outlier:**
   - Outlier di fitur `price` dan `area` diidentifikasi menggunakan IQR dan dihapus.
4. **Feature Scaling:**
   - Fitur numerik dinormalisasi menggunakan StandardScaler untuk menyamakan skala data.

---

## **Modeling**
### **Algoritma yang Digunakan:**
1. **Linear Regression:**
   - Model dasar untuk memprediksi harga dengan hubungan linier.
2. **Random Forest Regressor:**
   - Model ensemble yang menggabungkan banyak pohon keputusan untuk prediksi yang stabil.
3. **XGBoost:**
   - Model boosting yang menggabungkan prediksi dari model lemah untuk menghasilkan prediksi yang kuat.

### **Hyperparameter Tuning:**
- Menggunakan GridSearchCV untuk:
  - **Random Forest:** Menyetel `n_estimators`, `max_depth`, dan `min_samples_split`.
  - **XGBoost:** Menyetel `learning_rate` dan `max_depth`.

---

## **Evaluation**
### **Metrik Evaluasi:**
1. **R² (Coefficient of Determination):**
   - Mengukur proporsi variansi dalam target yang dapat dijelaskan oleh model.
2. **MAPE (Mean Absolute Percentage Error):**
   - Mengukur kesalahan rata-rata dalam persentase prediksi.

### **Hasil Evaluasi:**
| **Model**             | **R²** | **MAPE** |
|------------------------|--------|----------|
| Random Forest          | 0.731  | 17.13%   |
| XGBoost                | 0.647  | 19.39%   |
| Decision Tree          | 0.441  | 20.45%   |
| SVR                   | -0.029 | 34.56%   |

**Analisis:**
- Model Random Forest menunjukkan kinerja terbaik dengan R² tertinggi dan MAPE terendah.
- SVR tidak memberikan performa yang baik karena data tidak linier.

---

## **Kesimpulan**
Model Random Forest terbukti menjadi solusi terbaik untuk prediksi harga properti. Model ini dapat membantu para pemangku kepentingan di pasar real estate dalam mengambil keputusan dengan lebih percaya diri. Hyperparameter tuning juga berhasil meningkatkan performa model.

Langkah berikutnya:
1. Mengintegrasikan model ke dalam aplikasi untuk prediksi harga properti secara real-time.
2. Mengeksplorasi lebih banyak fitur untuk meningkatkan akurasi model.

---

_Laporan ini telah disusun untuk memenuhi standar dokumentasi proyek machine learning yang rapi dan informatif. Untuk pertanyaan atau saran, silakan menghubungi._ 😊
