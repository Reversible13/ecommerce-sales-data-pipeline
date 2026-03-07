# E-Commerce Sales Data Pipeline: Automated ETL & Market Insights

# Project Overview
Proyek ini merupakan bagian dari **Tugas Magang Modul 2 - Data Science**. Fokus utama proyek ini adalah membangun sebuah **Automated Data Pipeline (ETL)** yang mampu menangani puluhan laporan penjualan e-commerce dalam format Excel (.xlsx) yang memiliki struktur kolom tidak konsisten. 

Sistem ini dirancang untuk mengotomatisasi proses penggabungan, pembersihan, dan standardisasi data mentah dari berbagai file bulanan menjadi satu dataset master yang siap dianalisis untuk kebutuhan pengambilan keputusan bisnis.

# Background (Konteks Tugas)
Sebagai bagian dari program magang, tantangan yang diberikan adalah mengolah dataset yang "kotor" dan terfragmentasi. Dataset ini mensimulasikan data transaksi riil yang sering kali memiliki perbedaan penamaan kolom antar periode (misalnya perbedaan format di bulan September vs Desember). Pipeline ini dibuat untuk menggantikan proses manual yang memakan waktu dan rentan kesalahan (*human error*).

# Key Challenges & Solutions
Dalam pengolahan data ini, terdapat beberapa tantangan teknis yang berhasil diatasi:
* **Inconsistent Column Naming**: Menggunakan logika *dynamic mapping* untuk menangani perbedaan nama kolom (contoh: mengubah "Waktu Pengiriman Diatur" menjadi "Waktu Pesanan Dibuat").
* **High Dimensionality**: Menangani file dengan variasi jumlah kolom (hingga 49 kolom) dengan melakukan seleksi kolom otomatis agar memori lebih efisien.
* **Data Cleaning**: 
    * Mengubah data berat (teks "gr") menjadi tipe data numerik (*float*).
    * Konversi format waktu menjadi objek *datetime* untuk analisis tren.
    * Penanganan *missing values* pada kolom alasan pembatalan.

# Pipeline Stages
Proyek ini dibagi menjadi tiga tahap utama (ETL):
1.  **Extract**: Membaca massal file `.xlsx` dari direktori menggunakan `glob` dan `os`.
2.  **Transform**: Standardisasi nama kolom, penghapusan duplikat, dan pembersihan format *string*.
3.  **Load**: Menghasilkan `df_master` dan `df_sukses` yang siap digunakan untuk laporan manajerial.

# Business Insights Generated
Pipeline ini mampu mengekstrak wawasan strategis seperti:
* **Top 10 Product Categories**: Identifikasi produk dengan volume penjualan tertinggi.
* **Golden Hours Analysis**: Menemukan jam sibuk transaksi unik pelanggan.
* **Geographic Distribution**: Pemetaan 5 provinsi dengan jumlah transaksi terbanyak.
* **Payment Preference**: Analisis persentase metode pembayaran (COD vs Non-COD).

# Repository Structure
```text
├── Dataset/                         # Folder data mentah (Excel files)
├── sales_data_pipeline.ipynb        # Main Notebook (Logika ETL & Analisis)
├── README.md                        # Dokumentasi Proyek
└── sales_data_cleaned_final.xlsx    # Output Data Bersih
