# tugas1-reyboy11

# Indonesian News Big Data Analysis

## Deskripsi Project

Project ini merupakan implementasi analisis Big Data menggunakan dataset berita berbahasa Indonesia. Dataset yang digunakan adalah Indonesian News Dataset (`idn-news-az`) yang berisi kumpulan berita dari berbagai sumber berita online Indonesia.

Project ini bertujuan untuk melakukan eksplorasi dan profiling awal terhadap dataset berukuran besar menggunakan Python dengan library Polars. Proses pengolahan data menggunakan pendekatan Polars Lazy API agar dapat menangani dataset dalam jumlah besar secara lebih efisien.

Dataset yang digunakan memiliki format Parquet dengan ukuran lebih dari 1 GB sehingga sesuai untuk penerapan konsep Big Data Processing.

---

## Dataset

Nama Dataset:

Indonesian News Dataset (`idn-news-az`)

Sumber Dataset:

https://huggingface.co/datasets/esteler-ai/idn-news-az

Dataset ini berisi kumpulan berita berbahasa Indonesia yang dikumpulkan dari berbagai sumber berita online.

Informasi Dataset:

- Format Data: Parquet
- Jumlah File: 441 file parquet
- Ukuran Dataset: ±1.45 GB
- Jumlah Data: 1.149.789 baris
- Bahasa: Indonesia

Struktur kolom dataset:

| Kolom | Deskripsi |
|---|---|
| date | Tanggal publikasi berita |
| link | URL sumber berita |
| title | Judul berita |
| text | Isi berita |

---

## Tujuan Project

Tujuan dari project ini adalah:

- Melakukan eksplorasi awal terhadap dataset berita berukuran besar.
- Mengetahui struktur dan karakteristik dataset.
- Melakukan profiling data menggunakan pendekatan Big Data.
- Menguji kemampuan Polars dalam menangani dataset berukuran besar.
- Menyiapkan dataset untuk proses analisis lanjutan.

---

## Teknologi yang Digunakan

Teknologi dan tools yang digunakan pada project ini:

- Python
- Polars
- Jupyter Notebook
- GitHub
- Parquet Format

Library utama yang digunakan adalah Polars karena memiliki performa tinggi dalam pemrosesan data besar dengan fitur Lazy API.

---

## Struktur Repository
tugas1-reyboy11-bigdata
│
├── README.md
│
├── data
│   └── README.md
│
├── notebooks
│   ├── README.md
│   └── 01_data_profiling.ipynb
│
└── .gitignore


---

## Notebook

Notebook utama yang digunakan:

`01_data_profiling.ipynb`

Notebook tersebut berisi proses:

- Import library.
- Membaca dataset Parquet menggunakan Polars Lazy API.
- Mengecek ukuran dataset.
- Menghitung jumlah data.
- Melihat schema dataset.
- Melakukan pengecekan missing value.
- Melakukan eksplorasi awal dataset.

---

## Hasil Profiling Dataset

Berdasarkan proses profiling awal diperoleh hasil:

- Dataset terdiri dari 441 file Parquet.
- Ukuran dataset sekitar 1.45 GB.
- Jumlah data sebanyak 1.149.789 baris.
- Dataset memiliki 4 kolom utama yaitu date, link, title, dan text.
- Dataset berhasil diproses menggunakan Polars Lazy API.

---

## Cara Mendapatkan Dataset

Dataset tidak disimpan langsung pada repository GitHub karena memiliki ukuran file yang besar.

Dataset dapat diperoleh melalui sumber berikut:

https://huggingface.co/datasets/esteler-ai/idn-news-az

Setelah dataset berhasil diunduh, file dapat ditempatkan pada struktur folder:

data
└── raw
    └── idn-news
        └── data_files
            ├── *.parquet


---

## Catatan

Repository GitHub hanya menyimpan dokumentasi dataset, notebook analisis, dan struktur project.

File dataset asli tidak dimasukkan ke repository karena ukuran file terlalu besar.

Dataset dapat diunduh kembali melalui sumber dataset yang tersedia dan diproses menggunakan notebook profiling.

---

## AI Disclosure Statement

Alat AI yang digunakan:

ChatGPT

Bagian yang dibantu:

AI digunakan untuk membantu memahami instruksi tugas, membantu proses debugging error, melakukan review dokumentasi project, serta membantu pengecekan struktur repository.

Verifikasi yang dilakukan:

Setiap kode dijalankan ulang secara mandiri. Hasil analisis diperiksa kembali dan setiap bagian project dipahami sebelum dilakukan pengumpulan.

---

## Author

Nama: M. Raihan Abdi

NIM: 202310370311474
