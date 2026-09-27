# Dataset Documentation

## Nama Dataset

Indonesian News Dataset (`idn-news-az`)

## Deskripsi Dataset

Dataset ini berisi kumpulan berita berbahasa Indonesia yang dikumpulkan dari berbagai sumber berita online Indonesia.

Dataset digunakan untuk melakukan eksplorasi dan analisis Big Data menggunakan pendekatan pemrosesan data skala besar dengan Polars dan DuckDB.

## Sumber Dataset

Dataset diperoleh dari Hugging Face:

https://huggingface.co/datasets/esteler-ai/idn-news-az

## Format Dataset

Dataset tersedia dalam format:

- Parquet

Dataset terdiri dari beberapa file parquet yang diproses menggunakan Polars Lazy API.

## Ukuran Dataset

Ukuran dataset:

±1.45 GB

Jumlah file:

441 file parquet

## Jumlah Data

Jumlah baris:

1.149.789 baris

## Struktur Kolom

| Kolom | Deskripsi |
|---|---|
| date | Tanggal publikasi berita |
| link | URL sumber berita |
| title | Judul berita |
| text | Isi berita |

## Lokasi Penyimpanan

Dataset disimpan pada:
data/raw/idn-news/


Struktur:

data
└── raw
    └── idn-news
        └── data_files
            ├── *.parquet


## Catatan

File dataset berukuran besar sehingga tidak disimpan langsung pada repository GitHub.

Dataset dapat diunduh kembali melalui sumber dataset yang tersedia dan diproses menggunakan notebook profiling.
a
