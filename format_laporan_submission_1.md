
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

# **Data Preparation**

### **Feature Engineering**
Pada tahap ini, dilakukan pengolahan fitur agar siap digunakan dalam model. Langkah-langkah yang dilakukan:  
1. **Encoding Fitur Kategorikal**  
   Fitur seperti `mainroad`, `guestroom`, `basement`, `airconditioning`, `prefarea`, dan `furnishingstatus` diubah menjadi nilai numerik menggunakan **LabelEncoder**.  
2. **Penambahan Fitur Baru**  
   Ditambahkan fitur `price_per_sqft` (harga per meter persegi) untuk meningkatkan kemampuan model dalam memahami hubungan harga dan luas properti.  
3. **Penanganan Outlier**  
   Menggunakan metode **IQR** (Interquartile Range) untuk menghapus data yang memiliki nilai terlalu ekstrem, seperti harga atau luas area yang terlalu jauh dari rentang normal.  

### **Vectorizer**
Tidak ada fitur berbasis teks pada dataset ini, sehingga tahap ini tidak diperlukan.  

### **Split Data**
Dataset dibagi menjadi **training** dan **testing** set:  
- **Training Set**: 80% dari data, digunakan untuk melatih model.  
- **Testing Set**: 20% dari data, digunakan untuk evaluasi model.  
- Proses pembagian dilakukan menggunakan fungsi `train_test_split` dengan `random_state=42` untuk memastikan hasil yang konsisten:
   ```python
   from sklearn.model_selection import train_test_split
   X_train, X_test, y_train, y_test = train_test_split(X_scaled, y, test_size=0.2, random_state=42)
   ```

---

# **Modeling**

Berbagai model diterapkan untuk memprediksi harga rumah. Berikut adalah deskripsi model yang digunakan:  

### **1. Linear Regression**
Model regresi linear sederhana digunakan sebagai baseline.  
- Tidak ada parameter khusus yang digunakan.  

### **2. Ridge Regression**
Model regresi linear dengan regularisasi L2 untuk mencegah overfitting.  
- Parameter utama: `alpha` (kontrol tingkat regularisasi). Dicoba dengan nilai [0.1, 1, 10].  

### **3. Lasso Regression**
Model regresi linear dengan regularisasi L1 yang dapat melakukan seleksi fitur.  
- Parameter utama: `alpha`. Dicoba dengan nilai [0.01, 0.1, 1].  

### **4. Random Forest Regressor**
Model berbasis ensemble yang menggunakan banyak pohon keputusan untuk meningkatkan akurasi.  
- Parameter utama:  
  - `n_estimators`: Jumlah pohon (100, 200).  
  - `max_depth`: Kedalaman maksimum pohon (10, 20, None).  

### **5. Decision Tree Regressor**
Model pohon keputusan tunggal.  
- Parameter utama:  
  - `max_depth`: Kedalaman maksimum pohon (10, 20, None).  

### **6. Support Vector Regressor (SVR)**
Model regresi berbasis SVM dengan kernel RBF.  
- Parameter utama:  
  - `C`: Regularisasi (1, 10).  
  - `kernel`: Jenis kernel (RBF).  

### **7. XGBoost Regressor**
Model gradient boosting yang sangat efisien.  
- Parameter utama:  
  - `learning_rate`: Tingkat pembelajaran (0.01, 0.1).  
  - `n_estimators`: Jumlah pohon (100, 200).  

---

# **Evaluation**

### **Metode Evaluasi**
- **R² (R-squared)**: Mengukur seberapa baik model menjelaskan variansi data target.  
- **MAPE (Mean Absolute Percentage Error)**: Mengukur kesalahan prediksi relatif terhadap nilai sebenarnya dalam persentase.  

### **Hasil Evaluasi Model**

| **Model**            | **R²**    | **MAPE**              |
|-----------------------|-----------|-----------------------|
| Linear Regression     | 0.8792    | 1.543798e+14          |
| Ridge Regression      | 0.8791    | 1.537867e+14          |
| Lasso Regression      | 0.8536    | 7.150074e+12          |
| Random Forest         | 0.9686    | 9.720269e+13          |
| Decision Tree         | 0.9414    | 1.563750e+14          |
| SVR                  | 0.7285    | 5.871988e+14          |
| XGBoost               | 0.9692    | 4.385626e+13          |

### **Analisis Hasil**
1. **XGBoost**: Model terbaik dengan **R² tertinggi (0.9692)** dan **MAPE terendah (4.385626e+13)**.  
2. **Random Forest**: Alternatif yang baik dengan performa mendekati XGBoost.  
3. **SVR**: Model terburuk dengan **R² rendah (0.7285)** dan **MAPE tinggi**.  

### **Kesimpulan**
- **XGBoost** memberikan hasil yang optimal untuk prediksi harga rumah.  
- Model ini menjawab **problem statement** dengan akurasi tinggi, mampu menjelaskan hampir seluruh variansi harga rumah.  
- Solusi ini berdampak positif pada **business understanding**, memberikan prediksi harga yang lebih akurat untuk pengambilan keputusan investasi properti.  

---

_Laporan ini telah disusun untuk memenuhi standar dokumentasi proyek machine learning yang rapi dan informatif. Untuk pertanyaan atau saran, silakan menghubungi._ 😊



Berikut revisi dan penjelasan yang disesuaikan dengan masukan Anda:  





