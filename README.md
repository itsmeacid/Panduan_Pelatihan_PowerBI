
# 📊 Power BI: Dashboard Operasional Logistik

> Dokumentasi pembelajaran dan implementasi Power BI untuk mengolah data logistik menjadi dashboard interaktif yang informatif, terstruktur, dan mendukung pengambilan keputusan berbasis data.

<p align="center">
  <img src="assets/images/dashboard-preview.png" alt="Preview Dashboard Operasional Logistik" width="100%">
</p>

## 🔎 Tentang Proyek

Repository ini berisi dokumentasi praktikum Power BI yang
dikembangkan sebagai bahan belajar mandiri setelah pelatihan
pembuatan dashboard operasional logistik.

Materi mencakup proses pengolahan data, pembersihan data,
pemodelan data, penggunaan DAX, visualisasi, hingga penyusunan
dashboard interaktif.

Repository ini diharapkan dapat membantu peserta mengulang
materi secara mandiri dan memahami alur pembuatan dashboard
dari data mentah hingga menghasilkan insight.

## 🎯 Tujuan Pembelajaran

Setelah mengikuti panduan ini, pembaca diharapkan mampu:

- Memahami konsep dasar Power BI dan Business Intelligence.
- Mengimpor data dari file CSV atau Excel.
- Membersihkan dan mentransformasi data menggunakan Power Query.
- Memahami tipe data, nilai kosong, error, dan duplikasi.
- Membuat tabel kalender dan relasi antartabel.
- Menggunakan DAX untuk membuat measure dan indikator KPI.
- Membuat grafik, kartu KPI, dan slicer interaktif.
- Menyusun dashboard yang informatif dan mudah dipahami.
- Menarik insight dari hasil visualisasi data.

## 🚀 Lihat Dashboard

Dashboard interaktif dapat diakses melalui Microsoft Fabric:

🔗 **[Buka Dashboard Operasional Logistik](https://app.fabric.microsoft.com/groups/me/reports/1d061955-9095-487b-8705-465090b486f1?ctid=1241de96-4dbf-4231-aa90-4d48af86085c%26pbi_source=linkShare)**

> Catatan: Akses dashboard bergantung pada izin berbagi
> dan autentikasi akun Microsoft. Jika laporan tidak dapat
> dibuka, pemilik laporan perlu memeriksa pengaturan aksesnya.

## 🗂️ Struktur Repository

```text
Panduan-Pelatihan-Power-BI/
│
├── README.md
│
├── dataset/
│   └── logistics_operations.csv
│
├── dashboard/
│   └── dashboard-logistik.pbix
│
├── panduan/
│   ├── 01-pengenalan-power-bi.md
│   ├── 02-data-preparation.md
│   ├── 03-data-modeling.md
│   ├── 04-dax-measures.md
│   └── 05-dashboard-design.md
│
└── assets/
    └── images/
        ├── dashboard-preview.png
        ├── power-query.png
        ├── data-model.png
        └── dax-measures.png
```

File yang belum tersedia dapat ditambahkan secara bertahap.

## 📁 Dataset

Dataset digunakan sebagai bahan latihan untuk mempraktikkan
proses pengolahan dan analisis data di Power BI.

**Unduh dataset:**

- [Dataset logistik CSV](dataset/logistics_operations.csv)

Dataset latihan ini digunakan untuk mempelajari analisis
operasional seperti volume pengiriman, biaya, status pengiriman,
dan ketepatan waktu.

**Catatan:** Jelaskan sumber dan karakteristik dataset yang
sebenarnya. Jika data dibuat untuk pelatihan, nyatakan bahwa
dataset tersebut merupakan data sintetis, bukan data aktual
perusahaan.

## 📚 Panduan Praktikum

| No. | Materi | Isi Pembelajaran |
|---|---|---|
| 01 | Pengenalan Power BI | Konsep BI, antarmuka, dan alur kerja |
| 02 | Data Preparation | Import, cleaning, tipe data, dan validasi |
| 03 | Data Modeling | Relasi tabel dan tabel kalender |
| 04 | DAX Measures | Perhitungan KPI dan indikator operasional |
| 05 | Dashboard Design | KPI cards, grafik, slicer, dan layout |

### 01. Pengenalan Power BI

Memahami fungsi Power BI dan perannya dalam mengubah data
menjadi informasi yang mudah dianalisis.

📖 [Buka panduan pengenalan](panduan/01-pengenalan-power-bi.md)

### 02. Data Preparation

Mempelajari proses import dataset, transformasi menggunakan
Power Query, pengaturan tipe data, serta pemeriksaan kualitas data.

📖 [Buka panduan data preparation](panduan/02-data-preparation.md)

### 03. Data Modeling

Mempelajari pembuatan relasi data, tabel kalender, dan dasar
pemodelan data untuk analisis berdasarkan waktu.

📖 [Buka panduan data modeling](panduan/03-data-modeling.md)

### 04. DAX Measures

Mempelajari pembuatan measure untuk menghitung indikator
operasional dan KPI dashboard.

📖 [Buka kumpulan kode DAX](panduan/04-dax-measures.md)

### 05. Dashboard Design

Mempelajari pembuatan kartu KPI, grafik tren, grafik
perbandingan, slicer, serta prinsip desain dashboard.

📖 [Buka panduan dashboard design](panduan/05-dashboard-design.md)

## 🧮 Contoh Kode DAX

Berikut contoh sederhana pembuatan tabel kalender untuk
mendukung analisis berdasarkan bulan.

```dax
Kalender =
ADDCOLUMNS(
    CALENDAR(
        MIN('Data Logistik'[Tanggal_Pesanan]),
        MAX('Data Logistik'[Tanggal_Pesanan])
    ),
    "Tahun Bulan", FORMAT([Date], "yyyy-MM")
)
```

Kode tersebut membuat tabel tanggal dan menambahkan kolom
Tahun Bulan, misalnya `2026-01` dan `2026-02`.

Pastikan nama tabel dan kolom disesuaikan dengan dataset
yang digunakan.

📖 Untuk kumpulan measure dan penjelasan setiap kode,
lihat [Panduan DAX Measures](panduan/04-dax-measures.md).

## 🖼️ Dokumentasi Visual

### 1. Hasil Dashboard

![Preview Dashboard](assets/images/dashboard-preview.png)

### 2. Transformasi Data dengan Power Query

![Power Query](assets/images/power-query.png)

### 3. Model Data

![Model Data](assets/images/data-model.png)

### 4. Implementasi DAX

![DAX Measures](assets/images/dax-measures.png)

Setiap gambar menunjukkan tahapan yang dapat diikuti kembali
oleh peserta selama proses praktikum.

## 💡 Hasil yang Diharapkan

Setelah menyelesaikan seluruh praktikum, peserta diharapkan
menghasilkan dashboard Power BI yang mampu:

- Menampilkan KPI utama secara ringkas.
- Memvisualisasikan tren pengiriman berdasarkan waktu.
- Membandingkan status dan performa pengiriman.
- Menyaring data berdasarkan kategori yang tersedia.
- Membantu pengguna menemukan pola dan insight operasional.

## 🛠️ Tools yang Digunakan

- Microsoft Power BI Desktop
- Power Query Editor
- DAX (Data Analysis Expressions)
- Microsoft Excel atau CSV sebagai sumber data
- GitHub untuk dokumentasi dan berbagi materi

## 👨‍💻 Cara Menggunakan Repository

1. Unduh atau clone repository ini.
2. Unduh dataset pada folder `dataset`.
3. Buka Power BI Desktop.
4. Ikuti panduan praktikum secara berurutan.
5. Terapkan kode DAX sesuai nama tabel dan kolom.
6. Bandingkan hasil praktik dengan gambar referensi.
7. Simpan hasil akhir dalam format `.pbix`.

## ⚠️ Catatan

- Dataset latihan tidak boleh dianggap sebagai data aktual
  perusahaan kecuali sumbernya memang resmi dan terverifikasi.
- Jangan mengunggah data internal, rahasia, atau sensitif.
- Akses dashboard Microsoft Fabric dapat memerlukan izin.
- Hasil visualisasi dapat berbeda sesuai versi Power BI,
  dataset, dan pengaturan regional.

## 🙌 Penutup

Panduan ini disusun agar materi pelatihan Power BI dapat
dipelajari kembali secara mandiri, tidak berhenti pada sesi
praktik, dan dapat dikembangkan menjadi proyek portofolio.

Silakan gunakan repository ini sebagai referensi belajar,
eksperimen, dan pengembangan kemampuan Business Intelligence.

**Learn the data. Understand the insight. Make better decisions.**
