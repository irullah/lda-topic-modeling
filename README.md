# 📊 YouTube Comments Topic Modeling (LSA)

Proyek ini adalah tugas mata kuliah **Proyek Sains Data (2022)** yang bertujuan untuk melakukan *scraping* komentar dari sebuah video YouTube, melakukan pra-pemrosesan teks (NLP) untuk Bahasa Indonesia, dan mengelompokkan topik pembicaraan netizen menggunakan metode **Latent Semantic Analysis (LSA)**.

Kode ini telah di-refactor dan dioptimasi agar berjalan lebih cepat dan efisien di lingkungan **Google Colab**.

## ✨ Fitur Utama

1. **YouTube Data Scraping:** Mengekstrak komentar utama dan balasan (*replies*) menggunakan YouTube Data API v3.
2. **Text Preprocessing (Bahasa Indonesia):** 
   - *Cleaning* (menghapus URL, simbol, angka, dan emoji)
   - *Casefolding*
   - *Tokenization* & *Stopword Removal* (menggunakan NLTK)
   - *Stemming* yang dioptimasi (menggunakan Sastrawi dan Dictionary-based approach).
3. **Feature Extraction:** Transformasi teks ke bentuk vektor menggunakan **TF-IDF**.
4. **Topic Modeling:** Mengekstrak topik utama dari ribuan komentar menggunakan **Truncated SVD (LSA)**.

## 🛠️ Teknologi & Library yang Digunakan

- **Bahasa:** Python 3.x
- **Lingkungan Eksekusi:** [Google Colab](https://colab.research.google.com/)
- **Library Utama:** 
  - `pandas`, `numpy` (Manipulasi Data)
  - `google-api-python-client` (Interaksi dengan YouTube API)
  - `nltk`, `Sastrawi` (Natural Language Processing)
  - `swifter` (Paralelisasi proses pandas apply)
  - `scikit-learn` (Machine Learning: TF-IDF & Truncated SVD)

## 🚀 Cara Menjalankan Proyek (di Google Colab)

Karena proyek ini dirancang untuk dijalankan di Google Colab, Anda tidak perlu menginstal library secara manual di komputer Anda. Ikuti langkah-langkah berikut:

### 1. Dapatkan YouTube API Key
1. Kunjungi [Google Cloud Console](https://console.cloud.google.com/).
2. Buat proyek baru dan aktifkan **YouTube Data API v3**.
3. Buat *Credentials* berupa **API Key**. Salin API Key tersebut.

### 2. Atur Lingkungan Google Colab
1. Buka file `.ipynb` di Google Colab.
2. **Sangat Penting:** Jangan menulis API Key Anda langsung di dalam kode!
3. Klik ikon kunci (🔑) **Secrets** di bilah menu sebelah kiri Google Colab.
4. Klik **+ Add new secret**.
5. Masukkan `YOUTUBE_API_KEY` pada kolom **Name**, dan *paste* API Key Anda pada kolom **Value**.
6. Aktifkan *toggle* (sakelar) agar notebook dapat mengakses kunci tersebut.

### 3. Eksekusi Kode
1. Ubah variabel `VIDEO_ID` di dalam kode dengan ID video YouTube yang ingin Anda analisis.
   *(Contoh: dari `https://www.youtube.com/watch?v=KtntKGlmuZw`, ID-nya adalah `KtntKGlmuZw`)*
2. Pada menu atas, klik **Runtime** > **Run all**.
3. Sistem akan otomatis mengunduh *library* tambahan (`Sastrawi`, `swifter`, NLTK resources) dan memproses data hingga output topik ditampilkan.

## 📂 Struktur Proses

1. **Blok 1-2:** Instalasi, import library, dan ekstraksi data dari YouTube. Data disimpan sementara dalam bentuk `.csv`.
2. **Blok 3:** Pra-pemrosesan teks (Pembersihan, Tokenisasi, Stopwords, Stemming). Logika stemming dioptimasi menggunakan *dictionary* agar komputasi jauh lebih cepat.
3. **Blok 4:** Pembuatan matriks TF-IDF dan ekstraksi topik (Topic Modeling) menggunakan Truncated SVD. Menampilkan 5 term/kata kunci teratas untuk setiap topik.

## 🔒 Keamanan
- File `.csv` hasil *scraping* tidak disertakan dalam repositori ini untuk menjaga efisiensi ruang.
- API Key dikelola menggunakan fitur *Environment Secrets* bawaan Google Colab, sehingga dijamin aman dari kebocoran saat di-push ke GitHub.

---
*Dibuat untuk keperluan Proyek Sains Data.*