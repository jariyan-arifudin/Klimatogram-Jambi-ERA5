# Analisis Klimatogram Provinsi Jambi (ERA5-Land)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Research-orange)

## Deskripsi Proyek

Repositori ini berisi alur kerja (*workflow*) lengkap untuk analisis klimatologi di Provinsi Jambi periode 2010-2020. Script ini mengotomatisasi proses dari hulu ke hilir:

1.  **Data Acquisition:** Mengunduh data reanalisis *ERA5-Land Monthly Averaged* secara otomatis menggunakan **CDS API** (Copernicus Climate Change Service).
2.  **Spatial Processing:** Memotong (*clipping*) data global NetCDF sesuai batas administrasi Provinsi Jambi (Shapefile).
3.  **Data Processing:** Menghitung statistik rata-rata bulanan (Klimatologi) untuk parameter Suhu Udara (2m Temperature) dan Total Presipitasi.
4.  **Visualization:** Menghasilkan grafik **Klimatogram** (kombinasi Bar & Line chart) standar akademis.

## Prasyarat

Sebelum menjalankan script, pastikan Anda memiliki:

1.  **Akun Copernicus CDS:**
    Anda harus mendaftar di [Climate Data Store](https://cds.climate.copernicus.eu/) dan menyetujui lisensi penggunaan data ERA5.
2.  **CDS API Key:**
    Setelah mendaftar, salin `url` dan `key` API Anda. Script akan meminta input ini saat dijalankan.
3.  **Google Colab:**
    Script ini dioptimalkan untuk berjalan di Google Colab karena membutuhkan integrasi Google Drive untuk menyimpan/membaca Shapefile.

## Struktur Direktori Google Drive

Agar script berjalan lancar, pastikan struktur folder di Google Drive Anda:

```text
/My Drive/Colab Notebooks/Skripsi/
├── Batas Adm Jambi/
│   └── Adm_Jambi_Prov.shp  (Beserta .shx, .dbf, .prj)

```

## Instalasi & Penggunaan

1. **Clone Repositori (atau Copy Script):**
Salin script utama ke dalam Google Colab.
2. **Instalasi Pustaka:**
Jalankan perintah berikut di sel pertama Colab:
```python
!pip install cdsapi rioxarray geopandas netCDF4

```


3. **Eksekusi Script:**
Jalankan script. Anda akan diminta memasukkan **API Key** secara interaktif.
4. **Output:**
* File Data: `jambi_era5_land_2010_2020.nc` (disimpan sementara).
* Gambar Grafik: `klimatogram_jambi_era5.png`.



## Metodologi Pengolahan

* **Suhu Udara:** Dikonversi dari Kelvin (K) ke Celcius (°C).
* **Curah Hujan:** Dikonversi dari laju rata-rata harian (m/hari) menjadi akumulasi bulanan (mm/bulan) dengan memperhitungkan jumlah hari dalam setiap bulan (kabisat diperhitungkan).
* **Spasial:** Menggunakan `rioxarray` untuk masking area di luar batas Jambi agar statistik yang dihasilkan presisi hanya untuk wilayah daratan provinsi.

## Penulis

**Jariyan Arifudin** Mahasiswa Geografi Lingkungan

Universitas Gadjah Mada (UGM)

## Lisensi & Sitasi

Kode ini didistribusikan di bawah **MIT License**.
Jika Anda menggunakan metode ini untuk penelitian, silakan sitasi repositori ini:

> Arifudin, J. (2026). *Analisis Klimatogram Provinsi Jambi (ERA5-Land)*. GitHub Repository.
