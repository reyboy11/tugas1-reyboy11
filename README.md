# tugas1-reyboy11

**Nama:** M. Raihan Abdi  
**NIM:** 202310370311474  

# Analisis Big Data Perilaku Pengguna E-Commerce

## Deskripsi Proyek

Tugas ini merupakan implementasi Analisis Big Data dengan melakukan eksplorasi dan analisis terhadap dataset e-commerce berukuran besar.

Tujuan dari proyek ini adalah memahami pola aktivitas pengguna pada platform e-commerce berdasarkan data interaksi pengguna. Dataset diproses menggunakan pendekatan Big Data Processing agar mampu menangani jumlah data yang besar secara efisien.

Pada tahap awal dilakukan proses data profiling untuk mengetahui karakteristik dataset, struktur data, jumlah baris, tipe data, serta kondisi kualitas data.

## Teknologi yang Digunakan

Teknologi yang digunakan dalam pengerjaan proyek ini:

- Python
- Polars
- DuckDB
- Plotly
- Jupyter Notebook


# Dataset

## Informasi Dataset

**Nama Dataset**

eCommerce Behavior Data from Multi-Category Store


**Sumber Dataset**

Kaggle - eCommerce Behavior Data from Multi-Category Store


**Dataset yang Digunakan**

2019-Nov.csv


**Ukuran Dataset**

±8.39 GB


**Jumlah Data**

67.501.979 baris


## Deskripsi Dataset

Dataset yang digunakan berisi aktivitas pengguna pada platform e-commerce.

Setiap baris data merepresentasikan aktivitas pengguna seperti melihat produk, memasukkan produk ke keranjang, melakukan pembelian, dan menghapus produk dari keranjang.

Dataset memiliki beberapa informasi utama:

| Kolom | Keterangan |
|---|---|
| event_time | waktu aktivitas pengguna |
| event_type | jenis aktivitas pengguna |
| product_id | identitas produk |
| category_id | identitas kategori |
| category_code | kategori produk |
| brand | merek produk |
| price | harga produk |
| user_id | identitas pengguna |
| user_session | sesi aktivitas pengguna |


# Struktur Repository

```text
tugas1-reyboy11
│
├── README.md
│
├── data
│   ├── README.md
│   └── raw
│       └── .gitkeep
│
├── notebooks
│   ├── README.md
│   └── 01_data_profiling.ipynb
│
├── output
│
├── src
│
├── Dockerfile
│
└── requirements.txt
```


# Tahapan Pengerjaan

## Milestone 1 - Data Profiling

Status: Selesai ✅

Tahapan yang sudah dilakukan:

- Menentukan dataset berukuran besar
- Mendokumentasikan sumber dataset
- Mengecek ukuran dataset
- Membaca dataset menggunakan Polars Lazy API
- Melakukan pengecekan struktur kolom
- Menghitung jumlah data
- Melihat contoh data
- Melakukan pengecekan missing value


## Milestone 2 - Data Cleaning

Status: Belum dikerjakan

Rencana pengerjaan:

- Melakukan pembersihan data menggunakan Polars
- Menangani missing value
- Mengecek data duplikat
- Melakukan validasi kualitas data
- Melakukan profiling menggunakan DuckDB


## Milestone 3 - Exploratory Data Analysis

Status: Belum dikerjakan

Rencana pengerjaan:

- Analisis pola aktivitas pengguna berdasarkan waktu
- Analisis kategori dan produk
- Membuat visualisasi interaktif menggunakan Plotly
- Menemukan insight berdasarkan hasil analisis


## Final Project

Status: Belum dikerjakan

Target akhir:

- Menghasilkan insight dari hasil analisis
- Dokumentasi project lengkap
- Menambahkan Docker untuk reproducibility
- Menyediakan environment yang dapat dijalankan ulang


# Notebook

## 01_data_profiling.ipynb

Notebook ini digunakan untuk melakukan eksplorasi awal dataset.

Tahapan yang dilakukan:

- Import library
- Membaca dataset menggunakan Polars Lazy API
- Mengecek ukuran dataset
- Melihat schema dataset
- Menghitung jumlah baris
- Melihat sample data
- Mengecek missing value


# Catatan Dataset

Karena ukuran dataset mencapai beberapa GB, file dataset tidak disimpan langsung pada repository GitHub.

Dataset disimpan secara lokal pada folder:

```text
data/raw/
```

Repository hanya menyimpan dokumentasi, notebook, dan kode analisis.
