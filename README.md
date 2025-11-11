# Big-Data

🧭 Analisis Ulasan Aplikasi Traveloka dari Google Play Store
Proyek ini berfokus pada pengumpulan, pembersihan, dan analisis data ulasan pengguna aplikasi Traveloka dari Google Play Store. Tujuan utamanya adalah untuk memahami perilaku pengguna, pola sentimen, serta menghasilkan model yang dapat digunakan untuk klasifikasi, regresi, dan clustering berdasarkan ulasan pengguna.

🧮 1. Pengambilan Dataset

Data utama diperoleh dari hasil scraping langsung melalui Google Play Store untuk aplikasi Traveloka.
Selain itu, digunakan pula dataset tambahan dari Kaggle sebagai pembanding untuk memperkaya data analisis.

Link dataset pendukung:
Google Play Store Reviews Dataset (Kaggle)

🌐 2. Scraping Ulasan Aplikasi Traveloka

Scraping dilakukan dengan menggunakan pustaka google-play-scraper untuk mengambil seluruh ulasan aplikasi Traveloka dalam bahasa Indonesia.

Proses ini mencakup pengambilan data seperti ID ulasan, nama pengguna, teks ulasan, rating (score), jumlah like, versi aplikasi, waktu unggah, serta respons dari pihak Traveloka.

📂 3. Menggabungkan Data

Tahap berikutnya adalah menggabungkan dua sumber data:
- Dataset hasil scraping terbaru (reviews_traveloka_scraped.csv), dan
- Dataset tambahan (revies_traveloka_googleplaystore.csv) yang berisi data batch sebelumnya.

Kedua dataset digabungkan menjadi satu file gabungan bernama data_traveloka_gabungan.csv yang digunakan untuk tahap preprocessing selanjutnya.

🧹 4. Data Cleaning

Proses pembersihan data dilakukan secara sistematis dengan beberapa tahap:
1. Menghapus baris duplikat dan nilai kosong.
2. Menghapus karakter yang tidak diperlukan seperti emoji dan simbol non-alfabet.
3. Menormalisasi teks menjadi huruf kecil.
4. Menghapus tanda baca serta kata-kata tidak relevan.
5. Melakukan tokenisasi teks untuk memecah kalimat menjadi kata.
6. Menyusun kembali data yang sudah bersih untuk memastikan kolom penting tersedia.

Tahapan ini menghasilkan dataset yang lebih terstruktur dan siap untuk analisis.

📊 5. Exploratory Data Analysis (EDA) dengan Metode SMART

Metode SMART (Specific, Measurable, Actionable, Relevant, Timely) diterapkan untuk memahami data secara menyeluruh. Analisis dilakukan dengan tujuan untuk menemukan insight yang bermakna dari data ulasan.
- Specific: Mengidentifikasi kata-kata yang paling sering digunakan dalam ulasan pengguna.
- Measurable: Mengukur distribusi rating dari 1 hingga 5 bintang untuk melihat kecenderungan sentimen.
- Actionable: Menemukan pola kata negatif yang sering muncul pada ulasan dengan rating rendah.
- Relevant: Menelusuri hubungan antara panjang ulasan, jumlah kata, dan nilai rating yang diberikan.
- Timely: Menganalisis perubahan tren sentimen dari waktu ke waktu berdasarkan tanggal ulasan.

Hasil analisis divisualisasikan menggunakan grafik, diagram batang, dan wordcloud untuk menggambarkan pola data secara visual.

⚙️ 6. Preprocessing

Tahap ini mempersiapkan teks agar dapat digunakan dalam model pembelajaran mesin. Berdasarkan isi notebook preprocessing:
1. Import Library:
   Menggunakan pustaka seperti pandas, NumPy, NLTK, dan Sastrawi untuk memproses teks.
2. Stopword dan Stemmer:
   Dibuat daftar stopwords bahasa Indonesia dan tambahan kata tidak penting seperti “banget”, “aja”, dan “nih”.
   Proses stemming dilakukan menggunakan pustaka Sastrawi untuk mengembalikan kata ke bentuk dasarnya.
3. Pemanggilan Dataset:
   File data_traveloka_gabungan.csv dibaca untuk diproses lebih lanjut.
4. Validasi Kolom:
   Memastikan kolom teks utama (content) tersedia dan siap diproses.
5. Pembuatan Kamus Slang:
   Dibuat kamus berisi ratusan kata gaul atau singkatan populer yang dikonversi ke bentuk baku (misalnya “gk” → “tidak”, “bgt” → “banget”).
6. Pembersihan Teks:
   Melakukan normalisasi, penghapusan simbol, konversi slang, tokenisasi, dan penghapusan stopwords.
7. Hasil Akhir:
   Dataset hasil preprocessing disimpan dengan kolom tambahan seperti clean_text, tokens, n_tokens, dan n_chars.

🤖 7. Modeling (Klasifikasi, Regresi, Clustering)

Setelah preprocessing, data digunakan untuk membuat model pembelajaran mesin berdasarkan notebook Machine_Learning.ipynb.
Tahapan modeling mencakup tiga pendekatan utama:

a. Klasifikasi

Model klasifikasi digunakan untuk mengelompokkan ulasan berdasarkan sentimen (positif, netral, negatif).
Data teks yang telah diolah digunakan untuk membangun model dengan tujuan memprediksi kecenderungan sentimen pengguna.

b. Regresi

Model regresi digunakan untuk memprediksi nilai rating numerik berdasarkan isi ulasan.
Hasil evaluasi mencakup nilai Mean Squared Error (MSE), Root Mean Squared Error (RMSE), dan koefisien determinasi (R²).

c. Clustering

Pendekatan clustering dilakukan untuk mengelompokkan ulasan ke dalam beberapa kelompok berdasarkan kemiripan kata dan konteks kalimat.
Metode seperti K-Means digunakan untuk melihat pola alami dalam data ulasan tanpa label sentimen

📈 8. Hasil dan Visualisasi

Hasil analisis dan modeling menghasilkan beberapa insight utama, antara lain:
- Sebagian besar pengguna memberikan rating tinggi (4–5 bintang).
- Kelompok ulasan negatif memiliki kecenderungan mengandung kata seperti error, refund, dan lemot.
- Ulasan dengan kata yang lebih panjang cenderung memberikan detail pengalaman yang lebih lengkap.
- Model klasifikasi mampu mengenali pola sentimen dengan cukup baik setelah tahap preprocessing dilakukan.
  
Visualisasi hasil meliputi grafik distribusi rating, wordcloud kata populer, serta plot hasil clustering.

🧰 9. Teknologi yang Digunakan

Bahasa: Python

Library utama: pandas, numpy, re, nltk, Sastrawi, matplotlib, seaborn, scikit-learn, google-play-scraper

Lingkungan kerja: Google Colab

✍️ Kontributor

1. Nama: Fayza Zahra Putri Hakim

   Peran: Data Engineer, Data Analyst

2. Nama: Ghefira Diandra Maharani

   Peran: Machine Learning Engineer, Data Analyst

3. Nama: Salma Zanuba

   Peran: Machine Learning Engineer, Data Analyst

📄 Lisensi

Pengguna diperbolehkan untuk menyalin, memodifikasi, dan mendistribusikan proyek ini dengan mencantumkan atribusi yang sesuai
