# Analisis Iklim & Klimatogram Provinsi Jambi (ERA5-Land)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Research-orange)

## Deskripsi Proyek

Repositori ini memuat *pipeline* komputasi menggunakan Python untuk melakukan analisis klimatologi di Provinsi Jambi pada periode 2010-2020. Script ini dirancang untuk mengotomatisasi seluruh alur kerja mulai dari pengunduhan data hingga pelaporan statistik.

Data iklim yang digunakan adalah **ERA5-Land Monthly Averaged Data** dari Copernicus Climate Change Service (C3S), yang menyediakan data reanalisis resolusi tinggi (~9 km) untuk suhu udara (2m) dan curah hujan.

## Fitur Utama (Alur Kerja)

1.  **Automated Data Retrieval:** Mengunduh data NetCDF secara langsung menggunakan *Climate Data Store (CDS) API*.
2.  **Spatial Clipping:** Memotong (*masking*) data iklim global menggunakan batas administrasi Provinsi Jambi dengan bantuan pustaka `rioxarray`.
3.  **Unit Conversion:** * Mengonversi laju curah hujan ($m/hari$) menjadi akumulasi bulanan ($mm/bulan$).
    * Mengonversi suhu udara (Kelvin) menjadi derajat Celcius (°C).
4.  **Climograph Visualization:** Menghasilkan grafik klimatogram dual-axis berstandar akademis.
5.  **Statistical Export:** Mengekspor agregasi data (bulanan, tahunan, deskriptif, dan identifikasi bulan basah/kering) ke dalam format **Excel (.xlsx)**.

## Prasyarat Kredensial (CDS API)

Script ini membutuhkan otentikasi API dari Copernicus.
1. Buat akun di [Climate Data Store](https://cds.climate.copernicus.eu/).
2. Masuk ke halaman profil (*User Profile*) untuk mendapatkan `URL` dan `API Key` (Personal Access Token).
3. Saat script dijalankan di Google Colab, Anda akan diminta memasukkan API Key tersebut pada *prompt* interaktif.

## Struktur Direktori Data

Script dirancang untuk eksekusi di **Google Colab** dan membutuhkan Shapefile batas administrasi di Google Drive:

```text
/My Drive/Colab Notebooks/Skripsi/
├── Batas Adm Jambi/
│   └── Adm_Jambi_Prov.shp      <-- Shapefile Batas Provinsi
└── (Output file akan otomatis tersimpan di folder *working directory* Colab)

```

## Instalasi Pustaka

```bash
pip install cdsapi rioxarray xarray geopandas netCDF4 openpyxl

```

## Hasil Analisis (Output)

Menjalankan script ini akan menghasilkan beberapa *output*:

1. **Visualisasi Klimatogram (`.png`):**
Grafik perbandingan rata-rata curah hujan (diagram batang) dan suhu udara (diagram garis) selama 12 bulan.
2. **Laporan Statistik Excel (`.xlsx`):**
Buku kerja (*workbook*) Excel yang berisi 4 *sheet*:
* `Data_Bulanan`: Data mentah hasil ekstraksi spasial per bulan.
* `Data_Tahunan`: Agregasi curah hujan total dan rata-rata suhu per tahun.
* `Pola_Musiman`: Rata-rata klimatologis per bulan (Jan-Des).
* `Statistik_Deskriptif`: Ringkasan min, max, rata-rata, dan standar deviasi data.

## Penulis

**Jariyan Arifudin** Mahasiswa Geografi Lingkungan

Universitas Gadjah Mada (UGM)

## Lisensi & Sitasi

Kode ini didistribusikan di bawah **MIT License**.
Jika Anda menggunakan metode ini untuk penelitian, silakan sitasi repositori ini:

> Arifudin, J. (2026). *Analisis Iklim & Klimatogram Provinsi Jambi (ERA5-Land)*. GitHub Repository.
