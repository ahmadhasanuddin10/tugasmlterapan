# Prediksi Rumah - Ahmad Hasanuddin

## Domain Proyek

Pada proyek ini, kami fokus pada prediksi harga properti. Prediksi harga rumah sangat penting dalam pasar real estate karena membantu calon pembeli, penjual, dan investor dalam mengambil keputusan yang tepat. Dengan menggunakan model machine learning, kita dapat memperkirakan harga properti berdasarkan berbagai faktor yang mempengaruhi pasar real estate, seperti luas bangunan, jumlah kamar tidur, fasilitas, dan lokasi.

referensi : https://www.bi.go.id/id/publikasi/laporan/Documents/SHPR_Tw_I_2024.pdf

**Rubrik/Kriteria Tambahan (Opsional)**:

Masalah ini perlu diselesaikan karena harga properti sangat fluktuatif dan dapat dipengaruhi oleh banyak faktor yang sulit diprediksi dengan cara konvensional. Oleh karena itu, metode otomatis seperti machine learning dapat memberikan prediksi yang lebih akurat dan efisien.
  
  Format Referensi: [DETERMINAN HARGA RUMAH DI INDONESIA](https://jurnal.uns.ac.id/dinamika/article/download/45934/28895)

## Business Understanding

### Problem Statements

1. Bagaimana cara memprediksi harga properti berdasarkan berbagai fitur seperti luas bangunan, jumlah kamar tidur, fasilitas, dan lokasi?
2. Bagaimana meningkatkan akurasi model prediksi harga properti dengan menggunakan algoritma machine learning yang tepat?

### Goals

1. Membangun model yang dapat memprediksi harga properti dengan akurasi yang tinggi.

2. Meningkatkan akurasi model melalui teknik pemilihan fitur dan tuning hyperparameter.


**Rubrik/Kriteria Tambahan (Opsional)**:
- Kami akan menggunakan algoritma machine learning untuk mempelajari hubungan antara fitur-fitur properti dan harga properti.
- Kami akan menggunakan berbagai algoritma seperti Random Forest, Ridge, dan XGBoost, serta mengoptimalkan hyperparameter untuk meningkatkan kinerja model.

    ### Solution statements
    - Menggunakan algoritma Random Forest Regressor untuk memprediksi harga properti. Random Forest adalah model ensemble yang dapat menangani data yang kompleks dan memberikan hasil yang lebih baik dibandingkan dengan model linier sederhana.
    - Melakukan hyperparameter tuning untuk meningkatkan akurasi model. Dengan menggunakan GridSearchCV, kami akan mengoptimalkan parameter seperti jumlah pohon, kedalaman pohon, dan ukuran maksimum fitur yang digunakan untuk pelatihan.
## Data Understanding
Dataset yang digunakan dalam proyek ini adalah dataset yang berisi informasi mengenai properti, termasuk harga, ukuran, jumlah kamar, dan fasilitas lainnya. Dataset ini diambil dari berbagai sumber di pasar real estate dan berisi lebih dari seribu baris data. Contoh: [Housing Price Prediction](https://www.kaggle.com/datasets/harishkumardatalab/housing-price-prediction).

Selanjutnya uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

### Variabel-variabel pada dataset adalah sebagai berikut:
Variabel-variabel dalam dataset ini adalah sebagai berikut:
price: Harga properti (target variable).
area: Luas bangunan (dalam kaki persegi).
bedrooms: Jumlah kamar tidur.
bathrooms: Jumlah kamar mandi.
stories: Jumlah lantai pada rumah.
mainroad: Apakah properti terletak di jalan utama (1 = Ya, 0 = Tidak).
guestroom: Apakah properti memiliki ruang tamu (1 = Ya, 0 = Tidak).
basement: Apakah properti memiliki ruang bawah tanah (1 = Ya, 0 = Tidak).
hotwaterheating: Apakah properti memiliki pemanas air (1 = Ya, 0 = Tidak).
airconditioning: Apakah properti dilengkapi dengan pendingin udara (1 = Ya, 0 = Tidak).
parking: Jumlah tempat parkir.
prefarea: Apakah properti terletak di daerah preferensi (1 = Ya, 0 = Tidak).
furnishingstatus: Status furnitur properti (0 = Tidak Furnitur, 1 = Semi-Furnitur, 2 = Furnitur Lengkap).

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data atau exploratory data analysis.

## Data Preparation
Pada tahap data preparation, kami melakukan beberapa tahapan berikut:

Mengonversi variabel kategorikal menjadi numerik menggunakan teknik Label Encoding pada kolom seperti mainroad, guestroom, basement, hotwaterheating, airconditioning, dan prefarea.
Menangani nilai yang hilang dengan cara menghapus atau mengimputasi nilai yang hilang.
Menghapus outlier pada kolom price, area, dan price_per_sqft untuk memastikan bahwa model tidak terganggu oleh data yang tidak representatif.
Fitur normalisasi: Menggunakan StandardScaler untuk menormalkan fitur numerik agar semua fitur berada pada skala yang sama.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Pada tahap ini, kami mencoba beberapa model machine learning untuk menyelesaikan masalah prediksi harga properti:

Algoritma yang Digunakan:
Linear Regression:
Model sederhana yang memprediksi harga properti berdasarkan hubungan linier antara fitur-fitur input dan harga.
Ridge Regression:
Menggunakan regularisasi L2 untuk menghindari overfitting pada model.
Lasso Regression:
Menggunakan regularisasi L1 untuk mengurangi kompleksitas model dengan mengurangi bobot fitur yang kurang relevan.
Random Forest Regressor:
Model ensemble yang menggunakan banyak pohon keputusan untuk memberikan prediksi yang lebih stabil.
Decision Tree Regressor:
Model yang membagi data berdasarkan aturan if-else untuk memprediksi harga.
SVR (Support Vector Regressor):
Menggunakan prinsip margin dan kernel untuk memprediksi harga dengan menangani data yang tidak linier.
XGBoost:
Algoritma boosting yang menggabungkan beberapa model lemah untuk membuat prediksi yang lebih kuat dan akurat.
Hyperparameter Tuning:
Untuk model Random Forest, kami melakukan tuning hyperparameter menggunakan GridSearchCV untuk menemukan parameter terbaik seperti max_depth, min_samples_split, dan n_estimators.
Parameter lainnya juga dioptimalkan untuk model lain menggunakan GridSearchCV.


**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

## Evaluation
Evaluation
Metrik yang Digunakan:
R² (Coefficient of Determination): Mengukur sejauh mana model dapat menjelaskan variabilitas data target.
MAPE (Mean Absolute Percentage Error): Mengukur rata-rata persentase kesalahan prediksi model.
Hasil Evaluasi:
Random Forest: R² = 0.731, MAPE = 17.13%
XGBoost: R² = 0.647, MAPE = 19.39%
Decision Tree: R² = 0.441, MAPE = 20.45%
SVR: R² = -0.029, MAPE = 34.56%
Dari hasil ini, model Random Forest memberikan performa terbaik dengan R² tertinggi dan MAPE terendah dibandingkan dengan model lainnya

##
Conclusion
Proyek ini berhasil membangun model prediksi harga properti dengan akurasi yang cukup baik menggunakan algoritma Random Forest. Dengan melakukan hyperparameter tuning, kami dapat meningkatkan performa model dan mengurangi kesalahan prediksi. Selanjutnya, model ini dapat diterapkan untuk membantu dalam pengambilan keputusan di pasar properti.
**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.

