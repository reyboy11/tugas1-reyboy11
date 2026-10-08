# Tugas 1: Indonesian News Big Data Analysis

Repository: `tugas1-reyboy11`

## Deskripsi Project

Project ini merupakan implementasi eksplorasi dan profiling awal Big Data menggunakan **Indonesian News Dataset (`idn-news-az`)**. Dataset berisi kumpulan artikel berita berbahasa Indonesia dari berbagai portal berita daring.

Pada Milestone 1, fokus pengerjaan diarahkan pada dokumentasi dataset, pemeriksaan karakteristik awal data, serta pengujian pemrosesan dataset berukuran besar menggunakan **Polars Lazy API**.

Pendekatan lazy digunakan melalui `pl.scan_parquet()` agar Polars tidak langsung memuat seluruh dataset ke memori ketika data pertama kali dibaca. Pendekatan ini sesuai untuk dataset yang terdiri dari ratusan file Parquet dan berukuran lebih dari satu gigabyte.

Project juga telah diuji menggunakan Docker untuk memastikan environment analisis dapat dibangun dan dijalankan kembali secara konsisten.

---

## Status Pengerjaan

**Milestone 1: Selesai**

Cakupan Milestone 1 yang telah dikerjakan:

- Dokumentasi dataset pada `data/README.md`.
- Dataset memenuhi ketentuan lebih dari 500 MB atau lebih dari 1 juta baris.
- Profiling awal menggunakan Polars Lazy API.
- Pemeriksaan jumlah file dan ukuran dataset.
- Pemeriksaan jumlah baris.
- Pemeriksaan schema dataset.
- Pemeriksaan sampel data.
- Pemeriksaan missing values.
- Profiling awal kolom tanggal.
- Pengujian notebook dari awal sampai akhir.
- Pengujian environment menggunakan Docker.

Notebook Milestone 2 dan Milestone 3 masih menggunakan template repository dan akan dikembangkan pada tahap berikutnya.

---

## Dataset

**Nama Dataset:**  
Indonesian News Dataset (`idn-news-az`)

**Sumber:**  
https://huggingface.co/datasets/esteler-ai/idn-news-az

**Lisensi:**  
Creative Commons Attribution 4.0 International atau CC BY 4.0

**Format:**  
Parquet

### Karakteristik Dataset

| Informasi | Hasil |
|---|---|
| Jumlah file | 441 file Parquet |
| Ukuran lokal | ±1.45 GiB atau sekitar 1.56 GB |
| Jumlah baris | 1.149.789 |
| Jumlah kolom | 4 |
| Bahasa | Indonesia |
| Unit analisis | Satu artikel berita |

Dataset memenuhi ketentuan Tugas 1 karena memiliki ukuran lebih dari 500 MB sekaligus jumlah observasi lebih dari 1 juta baris.

### Struktur Kolom

| Kolom | Deskripsi |
|---|---|
| `date` | Tanggal publikasi artikel berita |
| `link` | URL sumber artikel berita |
| `title` | Judul artikel berita |
| `text` | Isi artikel berita |

---

## Tujuan Milestone 1

Milestone 1 bertujuan untuk:

1. Menyiapkan dataset Indonesia berukuran besar sesuai ketentuan tugas.
2. Mendokumentasikan sumber, ukuran, format, struktur, dan cara memperoleh dataset.
3. Menggunakan Polars Lazy API untuk membaca kumpulan file Parquet secara efisien.
4. Melakukan profiling awal terhadap struktur dan kualitas dataset.
5. Menyiapkan dasar analisis untuk tahap data cleaning dan exploratory data analysis berikutnya.
6. Memastikan project dapat dijalankan kembali menggunakan environment yang terdokumentasi.

---

## Teknologi yang Digunakan

| Teknologi | Penggunaan |
|---|---|
| Python | Bahasa pemrograman utama |
| Polars | Profiling dan pemrosesan data besar |
| Parquet | Format penyimpanan dataset |
| PyArrow | Dukungan pemrosesan data berbasis Arrow dan Parquet |
| JupyterLab | Environment notebook |
| Git | Version control |
| GitHub | Repository dan dokumentasi proses pengerjaan |
| Docker | Reproduktivitas environment |

`DuckDB` dan `Plotly` telah tersedia pada dependency project, tetapi implementasi utamanya digunakan pada milestone berikutnya.

---

## Struktur Repository

```text
tugas1-reyboy11/
├── .github/
│   └── workflows/
│       └── lint_check.yml
├── data/
│   └── README.md
├── notebooks/
│   ├── 01_data_profiling.ipynb
│   ├── 02_data_cleaning.ipynb
│   └── 03_eda_and_insights.ipynb
├── output/
│   └── figures/
├── src/
├── .dockerignore
├── .gitignore
├── Dockerfile
├── requirements.txt
└── README.md
```

Dataset mentah disimpan secara lokal pada `data/raw/` dan tidak dimasukkan ke repository GitHub.

---

## Notebook Milestone 1

Notebook utama:

```text
notebooks/01_data_profiling.ipynb
```

Notebook tersebut melakukan beberapa tahap profiling.

### 1. Import Library

Library utama yang digunakan adalah Polars.

### 2. Penentuan Lokasi Dataset

Notebook menentukan lokasi root project dan membaca seluruh file Parquet pada:

```text
data/raw/idn-news/data_files/
```

### 3. Pemeriksaan Jumlah File dan Ukuran Dataset

Seluruh file Parquet dihitung untuk memastikan dataset memenuhi batas ukuran Tugas 1.

### 4. Lazy Scanning

Dataset dibaca menggunakan:

```python
pl.scan_parquet()
```

Hasilnya berupa `LazyFrame`, sehingga Polars dapat merencanakan operasi terlebih dahulu sebelum melakukan eksekusi.

### 5. Pemeriksaan Schema

Schema digunakan untuk mengetahui nama kolom dan tipe data awal.

### 6. Penghitungan Jumlah Baris

Jumlah observasi aktual dihitung menggunakan `pl.len()`.

### 7. Pemeriksaan Sampel Data

Beberapa baris awal diperiksa untuk memahami bentuk dan isi dataset.

### 8. Pemeriksaan Missing Values

Jumlah nilai null diperiksa pada seluruh kolom.

### 9. Profiling Kolom Tanggal

Kolom `date` diperiksa dengan melakukan konversi sementara dari string menjadi tipe tanggal.

Tahap ini menemukan bahwa tidak seluruh representasi nilai pada kolom `date` dapat langsung diperlakukan sebagai tanggal valid. Temuan tersebut belum dibersihkan pada Milestone 1 dan akan menjadi salah satu fokus validasi data pada Milestone 2.

---

## Hasil Profiling Awal

Profiling menghasilkan beberapa temuan awal:

- Dataset terdiri dari **441 file Parquet**.
- Ukuran file secara lokal sekitar **1.45 GiB**.
- Dataset memiliki **1.149.789 baris**.
- Dataset memiliki empat kolom utama, yaitu `date`, `link`, `title`, dan `text`.
- Pada pemeriksaan null awal, empat kolom utama tidak menunjukkan nilai null.
- Kolom `date` pada data mentah masih disimpan sebagai string.
- Pemeriksaan parsing tanggal menunjukkan adanya nilai yang memerlukan validasi lebih lanjut.
- Dataset dapat dibaca dan diproses menggunakan Polars Lazy API tanpa harus langsung memuat seluruh data ketika `LazyFrame` dibuat.

Hasil tersebut menjadi dasar untuk proses data cleaning pada milestone berikutnya.

---

## Cara Mendapatkan Dataset

Dataset tidak disimpan langsung pada GitHub karena ukurannya besar.

Dataset dapat diperoleh dari:

https://huggingface.co/datasets/esteler-ai/idn-news-az

Dataset juga dapat diunduh menggunakan Hugging Face Hub.

Contoh:

```python
from huggingface_hub import snapshot_download

snapshot_download(
    repo_id="esteler-ai/idn-news-az",
    repo_type="dataset",
    local_dir="data/raw/idn-news",
    allow_patterns="data_files/*.parquet"
)
```

Setelah proses selesai, struktur lokal dataset menjadi:

```text
data/
└── raw/
    └── idn-news/
        └── data_files/
            ├── *.parquet
            └── ...
```

Folder `data/raw/` telah dimasukkan ke `.gitignore` sehingga dataset mentah tidak ikut terunggah ke repository.

---

## Menjalankan Project Secara Lokal

Buat dan aktifkan virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Install dependency:

```bash
pip install -r requirements.txt
```

Jalankan JupyterLab:

```bash
jupyter lab
```

Buka:

```text
http://localhost:8888/lab
```

Kemudian jalankan:

```text
notebooks/01_data_profiling.ipynb
```

---

## Reproduktivitas dengan Docker

Docker digunakan untuk menyediakan environment yang konsisten sehingga project dapat dijalankan kembali tanpa bergantung pada konfigurasi Python lokal.

Build Docker image:

```bash
docker build -t tugas1-bigdata .
```

Jalankan container:

```bash
docker run --rm -p 8888:8888 -v "$(pwd)":/home/jovyan/work tugas1-bigdata
```

Kemudian buka:

```text
http://localhost:8888/lab
```

Pada pengujian Milestone 1:

- Docker image berhasil dibangun.
- Container berhasil dijalankan.
- JupyterLab berhasil diakses melalui browser.
- Repository lokal berhasil di-mount ke container.
- Polars berhasil digunakan di dalam container.
- `01_data_profiling.ipynb` berhasil dijalankan dari awal sampai akhir.

File `.dockerignore` digunakan agar dataset mentah, virtual environment, Git metadata, serta file sementara tidak ikut dikirim sebagai Docker build context.

---

## Penyimpanan Dataset

Dataset mentah tidak disimpan pada GitHub.

Folder berikut diabaikan oleh Git:

```text
data/raw/
data/processed/
```

Pendekatan tersebut menjaga ukuran repository tetap kecil, sementara instruksi memperoleh dataset tetap tersedia melalui dokumentasi.

---

## AI Disclosure Statement

**Alat AI yang digunakan:**  
ChatGPT

**Bagian yang dibantu:**  
AI digunakan untuk membantu memahami instruksi tugas, menjelaskan penggunaan Git dan Docker, membantu debugging, melakukan review struktur repository, serta memberikan masukan terhadap dokumentasi dan kode profiling.

**Verifikasi yang dilakukan:**  
Seluruh kode dijalankan ulang secara mandiri pada environment lokal. Notebook profiling juga diuji melalui JupyterLab yang berjalan di dalam Docker. Output diperiksa kembali dan setiap bagian project dipahami sebelum dilakukan commit dan pengumpulan.

---

## Author

**Nama:** M. Raihan Abdi  
**NIM:** 202310370311474
