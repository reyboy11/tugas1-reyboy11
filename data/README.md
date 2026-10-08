# Dataset Documentation

## Dataset yang Dipilih

| Item | Isi |
|---|---|
| Nama dataset | Indonesian News Dataset (`idn-news-az`) |
| Sumber | https://huggingface.co/datasets/esteler-ai/idn-news-az |
| Lisensi/ketentuan pakai | CC BY 4.0 |
| Format | Parquet |
| Ukuran lokal | ±1.45 GB |
| Jumlah file | 441 file Parquet |
| Jumlah baris | 1.149.789 baris |
| Bahasa | Indonesia |
| Periode data | Mengikuti nilai pada kolom `date`, rentang tanggal diverifikasi pada tahap profiling |
| Unit analisis | Satu artikel berita |

## Deskripsi Dataset

Dataset `idn-news-az` berisi kumpulan artikel berita berbahasa Indonesia yang berasal dari berbagai portal berita daring.

Dataset dipilih karena memiliki ukuran sekitar 1.45 GB pada penyimpanan lokal dan terdiri dari 1.149.789 baris. Dengan demikian, dataset memenuhi ketentuan Tugas 1 karena berukuran lebih dari 500 MB dan memiliki lebih dari 1 juta baris.

Dataset digunakan untuk eksplorasi, profiling, pembersihan, dan analisis Big Data menggunakan Polars dan DuckDB.

## Struktur Kolom

| Kolom | Deskripsi |
|---|---|
| `date` | Tanggal publikasi berita |
| `link` | URL sumber artikel berita |
| `title` | Judul artikel berita |
| `text` | Isi artikel berita |

## Cara Memperoleh Dataset

Dataset tidak disimpan langsung pada repository GitHub karena memiliki ukuran yang besar.

Dataset dapat diperoleh dari:

https://huggingface.co/datasets/esteler-ai/idn-news-az

Setelah dataset diunduh, file Parquet ditempatkan pada:

data/raw/idn-news/data_files/

Struktur penyimpanan lokal:

data/
└── raw/
    └── idn-news/
        └── data_files/
            ├── *.parquet
            └── ...

Notebook membaca seluruh file Parquet menggunakan pola:

../data/raw/idn-news/data_files/*.parquet

## Pemrosesan Data

Tahap profiling menggunakan Polars Lazy API melalui `pl.scan_parquet()` sehingga dataset dapat diproses secara lazy tanpa langsung memuat seluruh data ke memori.

Pada tahap berikutnya, DuckDB digunakan untuk profiling berbasis SQL dan perintah `SUMMARIZE`.

## Aturan Penyimpanan

- Dataset mentah disimpan pada `data/raw/`.
- Dataset mentah tidak di-commit ke GitHub.
- Data mentah tidak dimodifikasi secara langsung.
- Hasil transformasi dapat disimpan pada `data/processed/`.
- Seluruh proses pengolahan harus dapat dijalankan ulang melalui notebook yang tersedia.
