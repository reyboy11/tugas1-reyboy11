# Dokumentasi Dataset Tugas 1

## Dataset yang Dipilih

| Item | Informasi |
|---|---|
| Nama dataset | Indonesian News Dataset (`idn-news-az`) |
| Sumber | https://huggingface.co/datasets/esteler-ai/idn-news-az |
| DOI | 10.57967/hf/1474 |
| Lisensi | CC BY 4.0 |
| Format | Parquet |
| Bahasa | Indonesia |
| Jumlah file lokal | 441 file Parquet |
| Ukuran lokal | ±1.45 GiB atau sekitar 1.56 GB |
| Jumlah baris | 1.149.789 |
| Jumlah kolom | 4 |
| Unit analisis | Satu artikel berita |

Dataset memenuhi syarat Tugas 1 karena memiliki ukuran lebih dari 500 MB dan jumlah observasi lebih dari 1 juta baris.

---

## Deskripsi Dataset

`idn-news-az` merupakan dataset teks yang berisi kumpulan artikel berita berbahasa Indonesia dari berbagai portal berita daring.

Setiap baris merepresentasikan satu artikel berita dan menyimpan informasi tanggal publikasi, tautan sumber, judul, serta isi artikel.

Dataset dipilih karena memiliki skala yang cukup besar untuk menerapkan teknik pemrosesan Big Data menggunakan Polars dengan pendekatan lazy evaluation.

---

## Struktur Kolom

| Kolom | Deskripsi | Tipe Awal |
|---|---|---|
| `date` | Tanggal publikasi artikel | String |
| `link` | URL sumber artikel | String |
| `title` | Judul artikel | String |
| `text` | Isi artikel | String |

Tipe data tersebut merupakan schema awal yang ditemukan pada tahap profiling. Validasi serta kemungkinan perubahan tipe dilakukan pada tahap data cleaning.

---

## Hasil Verifikasi Dataset

Dataset telah diverifikasi secara lokal melalui notebook:

```text
notebooks/01_data_profiling.ipynb
```

Hasil verifikasi awal:

- Jumlah file Parquet: **441 file**.
- Ukuran dataset lokal: **±1.45 GiB**.
- Jumlah observasi aktual: **1.149.789 baris**.
- Jumlah kolom: **4 kolom**.
- Kolom utama: `date`, `link`, `title`, dan `text`.
- Pemeriksaan null awal tidak menemukan nilai null pada empat kolom.
- Kolom `date` masih bertipe string dan memerlukan validasi format lebih lanjut.

Perbedaan penulisan sekitar 1.45 GiB dan 1.56 GB berasal dari perbedaan satuan pengukuran. Notebook menghitung ukuran menggunakan pembagi `1024^3`, sehingga hasilnya secara teknis menggunakan GiB.

---

## Sumber Dataset

Dataset diperoleh melalui Hugging Face:

https://huggingface.co/datasets/esteler-ai/idn-news-az

Halaman dataset menyediakan dokumentasi, metadata, serta file data yang diperlukan untuk memperoleh kembali dataset tanpa menyimpannya pada repository GitHub.

---

## Cara Memperoleh Dataset

### Metode Hugging Face Hub

Install library jika belum tersedia:

```bash
pip install huggingface_hub
```

Dari root repository, jalankan Python dengan kode berikut:

```python
from huggingface_hub import snapshot_download

snapshot_download(
    repo_id="esteler-ai/idn-news-az",
    repo_type="dataset",
    local_dir="data/raw/idn-news",
    allow_patterns="data_files/*.parquet"
)
```

Perintah tersebut mengunduh file Parquet yang digunakan dalam project.

Setelah selesai, struktur lokal menjadi:

```text
data/
├── README.md
└── raw/
    └── idn-news/
        └── data_files/
            ├── *.parquet
            └── ...
```

---

## Path yang Digunakan Notebook

Notebook profiling membaca dataset melalui pola:

```text
data/raw/idn-news/data_files/*.parquet
```

Ketika notebook dijalankan dari folder `notebooks/`, root project ditentukan terlebih dahulu sehingga path dataset tetap dapat ditemukan secara konsisten.

---

## Metode Pembacaan Data

Dataset tidak dibaca menggunakan `pl.read_parquet()` untuk langsung memuat keseluruhan data.

Profiling menggunakan:

```python
pl.scan_parquet()
```

Metode tersebut menghasilkan Polars `LazyFrame`. Operasi kemudian direncanakan dan baru dieksekusi ketika `.collect()` dipanggil.

Pendekatan ini digunakan agar pemrosesan terhadap ratusan file Parquet lebih efisien.

---

## Aturan Penyimpanan

Dataset mentah tidak di-commit ke GitHub.

Folder:

```text
data/raw/
```

digunakan khusus untuk data sumber yang diperoleh dari penyedia dataset.

Dataset mentah tidak dimodifikasi secara langsung.

Data hasil transformasi pada tahap berikutnya dapat ditempatkan pada:

```text
data/processed/
```

selama proses pembentukannya tetap dapat direproduksi melalui notebook atau kode project.

---

## Git dan Docker

Folder data mentah telah dikecualikan melalui `.gitignore`.

Dataset juga dikecualikan dari Docker build context melalui `.dockerignore`.

Dengan demikian, file data berukuran sekitar 1.5 GB tidak dimasukkan ke GitHub dan tidak disalin ke dalam Docker image pada proses build.

Ketika container dijalankan menggunakan:

```bash
docker run --rm -p 8888:8888 -v "$(pwd)":/home/jovyan/work tugas1-bigdata
```

folder project lokal di-mount ke container sehingga dataset tetap dapat digunakan oleh notebook tanpa dimasukkan secara permanen ke Docker image.

---

## Catatan Kualitas Data Awal

Pada Milestone 1 belum dilakukan pembersihan atau penghapusan observasi.

Profiling awal hanya digunakan untuk mengenali kondisi dataset.

Salah satu temuan awal berada pada kolom `date`. Meskipun tidak ditemukan nilai null secara langsung, tidak seluruh nilai dapat langsung dikonversi menjadi tipe tanggal menggunakan satu aturan parsing.

Temuan tersebut dipertahankan sebagai bagian dari hasil profiling dan akan dianalisis lebih lanjut pada tahap data cleaning.

---

## Reproduktivitas

Dataset mentah tidak disertakan dalam repository karena ukurannya besar. Agar analisis dapat direproduksi, repository menyediakan:

- Identitas dan sumber dataset.
- Lisensi dataset.
- Instruksi pengunduhan.
- Struktur direktori yang digunakan.
- Path dataset pada notebook.
- Dependency melalui `requirements.txt`.
- Environment Docker melalui `Dockerfile`.
- Notebook profiling yang dapat dijalankan ulang.

Dengan struktur tersebut, dataset dapat diperoleh kembali dan proses profiling dapat direplikasi dari awal.
