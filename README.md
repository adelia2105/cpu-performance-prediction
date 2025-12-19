📘 Judul Proyek
Prediksi Kinerja CPU Berdasarkan Spesifikasi Teknis Menggunakan Metode Regresi Machine Learning

👤 Informasi
Nama: Agnes Adelia Putri
NIM: 233307031
Program Studi: Teknologi Informasi
Dosen Pengampu: Gus Nanang Syalfuddlin, S.Kom., M.Kom.
Repo: https://github.com/adelia2105/cpu-performance-prediction.git
Video Pembahasan: https://drive.google.com/file/d/1q0J_gBQ2NvJSY9nG5OaBU80YFcSdqhpf/view?usp=sharing

1. 🎯 Ringkasan Proyek
Menyelesaikan permasalahan prediksi kinerja CPU berdasarkan spesifikasi teknis
Melakukan EDA, data cleaning, dan preprocessing
Membangun 3 model: Linear Regression (Baseline), Random Forest (Advanced), MLP (Deep Learning)
Melakukan evaluasi menggunakan metrik MSE, RMSE, MAE, dan R²
Menentukan model terbaik berdasarkan performa dan interpretabilitas

2. 📄 Problem & Goals
Problem Statements:
Dataset mengandung fitur kategorikal yang tidak dapat langsung digunakan
Perlu prediksi relative CPU performance (prp) dengan akurasi tinggi
Dataset memiliki skala fitur berbeda sehingga perlu normalisasi
Diperlukan perbandingan antara model tradisional dan deep learning untuk regresi

Goals:
Membangun model regresi dengan R² > 0.80
Mengimplementasikan tiga pendekatan modeling
Menentukan model terbaik berdasarkan RMSE, MAE, dan R²
Membuat sistem prediksi yang reproducible


📁 Struktur Folder
cpu-performance-prediction/
│
├── data/
│   ├── computer_hardware.csv
│   └── data_dictionary.txt
│
├── notebooks/
│   ├── 01_eda.ipynb
│   ├── 02_preprocessing.ipynb
│   ├── 03_modeling.ipynb
│   └── 04_evaluation.ipynb
│
├── src/
│   ├── data_preprocessing.py
│   ├── model_training.py
│   ├── model_evaluation.py
│   └── utils.py
│
├── models/
│   ├── linear_regression.pkl
│   ├── random_forest.pkl
│   └── neural_network.h5
│
├── reports/
│   ├── eda_report.pdf
│   ├── model_comparison.pdf
│   └── final_presentation.pdf
│
├── tests/
│   ├── test_preprocessing.py
│   └── test_models.py
│
├── requirements.txt
├── environment.yml
├── README.md
└── .gitignore

3. 📊 Dataset
Sumber: UCI Machine Learning Repository - Computer Hardware Dataset (https://archive.ics.uci.edu/dataset/29/computer+hardware)
Jumlah Data: 209 sampel, 10 fitur
Tipe: Tabular (numerik dan kategorikal)

Deskripsi fitur utama:
vendor: Nama vendor/pembuat CPU (kategorikal)
model: Model spesifik CPU (kategorikal)
myct: Machine cycle time dalam nanodetik (numerik)
mmin: Minimum main memory dalam KB (numerik)
mmax: Maximum main memory dalam KB (numerik)
cach: Cache memory dalam KB (numerik)
chmin: Minimum channels (numerik)
chmax: Maximum channels (numerik)
prp: Relative CPU performance - target yang diprediksi (numerik)
erp: Estimated relative CPU performance (numerik)

4. 🔧 Data Preparation
Data cleaning: Tidak ditemukan missing values atau data duplikat dalam dataset.

Transformasi data:
Fitur kategorikal (vendor dan model) dihapus karena tidak relevan untuk prediksi numerik dan dapat menyebabkan overfitting
Normalisasi dilakukan menggunakan StandardScaler untuk menyamakan skala semua fitur numerik
Fitur 'erp' dipertahankan meskipun memiliki korelasi tinggi dengan target

Pembagian data:
Data dibagi dengan proporsi 80% training dan 20% testing
Menggunakan random_state=42 untuk memastikan reproducibility
Data diacak sebelum pembagian untuk menghindari bias urutan

5. 🤖 Modeling
Model 1 – Baseline: Linear Regression
Model linear sederhana yang berfungsi sebagai baseline untuk perbandingan. Dipilih karena kesederhanaannya dan kemudahan interpretasi.

Model 2 – Advanced ML: Random Forest Regressor
Model ensemble yang membangun banyak decision tree. Dipilih karena kemampuannya menangani hubungan non-linear dan robust terhadap outliers.

Model 3 – Deep Learning: Multilayer Perceptron (MLP)
Jaringan saraf tiruan dengan 2 hidden layer. Arsitektur: 64 neuron (layer 1) → 32 neuron (layer 2) → output layer. Menggunakan dropout untuk regularisasi.

6. 🧪 Evaluation
Metrik evaluasi yang digunakan:
MSE (Mean Squared Error): Mengukur rata-rata kuadrat error
RMSE (Root Mean Squared Error): Akar dari MSE, dalam skala yang sama dengan target
MAE (Mean Absolute Error): Rata-rata absolute error, mudah diinterpretasi
R² Score: Koefisien determinasi, menunjukkan proporsi variasi yang dijelaskan model

Hasil evaluasi ketiga model:

Linear Regression (Baseline):
MSE: 2370.10
RMSE: 48.68
MAE: 31.41
R²: 0.9534

Random Forest (Advanced):
MSE: 5071.38
RMSE: 71.21
MAE: 30.15
R²: 0.9004

Neural Network (MLP):
MSE: 8327.75
RMSE: 91.26
MAE: 46.21
R²: 0.8364

7. 🏁 Kesimpulan
Model terbaik: Linear Regression

Alasan pemilihan:
Performansi superior: R² mencapai 0.9534, menjelaskan 95.34% variasi data
Efisiensi waktu: Training time hanya 0.5 detik, jauh lebih cepat dari model lain
Interpretabilitas tinggi: Koefisien model dapat diinterpretasikan secara langsung
Stabilitas: Tidak menunjukkan tanda-tanda overfitting atau underfitting
Kesederhanaan: Menerapkan prinsip Occam's Razor - model sederhana dengan hasil optimal

Insight penting dari proyek:
Hubungan antara spesifikasi CPU dan performanya bersifat linear kuat
Memory maksimum (mmax) adalah faktor paling penting untuk performa CPU
Cache memory (cach) memberikan pengaruh signifikan kedua
Model kompleks tidak selalu memberikan hasil terbaik, terutama untuk data dengan pola linear
Dataset yang relatif kecil (209 sampel) membatasi kemampuan model kompleks untuk belajar pattern yang lebih dalam

8. 🔮 Future Work
Perbaikan data:
Mengumpulkan lebih banyak data dengan CPU dari vendor dan generasi lebih baru
Menambahkan fitur teknis tambahan seperti jumlah core, kecepatan clock, dan teknologi manufaktur

Pengembangan model:
Mencoba arsitektur deep learning yang lebih kompleks
Hyperparameter tuning lebih ekstensif untuk Random Forest dan MLP
Eksperimen dengan ensemble methods seperti stacking atau blending model

Deployment:
Membuat API menggunakan Flask atau FastAPI
Mengembangkan web application dengan Streamlit atau Gradio
Containerization dengan Docker untuk portabilitas
Deployment ke platform cloud seperti Heroku, GCP, atau AWS

Optimisasi:
Model compression melalui pruning dan quantization
Meningkatkan kecepatan inference
Mengurangi ukuran model untuk deployment di environment terbatas

9. 🔁 Reproducibility
Environment yang digunakan:
Python 3.9.0
Semua dependensi tercantum dalam requirements.txt dan environment.yml

Langkah reproduksi:
Clone repository dari GitHub
Buat virtual environment Python
Install semua dependensi yang diperlukan
Jalankan script preprocessing, training, dan evaluasi
Atau buka notebook Jupyter untuk analisis interaktif

Reproducibility notes:
Semua random state diset ke 42 untuk hasil yang konsisten
Dataset termasuk dalam repository untuk memastikan versioning
Model disimpan dalam format serialized (pickle/h5)
Dokumentasi lengkap tersedia di README.md dengan instruksi step-by-step