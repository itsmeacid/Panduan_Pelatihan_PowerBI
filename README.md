# 📊 Logistics Operations Dashboard — Power BI

Dashboard interaktif untuk memantau pengiriman, ketepatan waktu, dan biaya operasional. Repository ini juga menjadi panduan singkat untuk mengulang praktik pembuatan dashboard menggunakan Power BI.

<p align="center">
  <img src="assets/images/dashboard-preview.png" alt="Preview Logistics Operations Dashboard" width="100%">
</p>

## 🎯 Tujuan

- Memantau jumlah dan status pengiriman.
- Melihat tren pengiriman berdasarkan waktu.
- Membandingkan biaya pengiriman dan penanganan.
- Menyaring informasi berdasarkan tanggal, moda pengiriman, dan jenis layanan.

## 🧰 Tools dan Dataset

- **Tools:** Microsoft Power BI Desktop, Power Query, dan DAX.
- **Dataset:** `dataset_operasional_logistik_bahasa_indonesia.xlsx`
- **Tabel utama:** `Data Logistik`

Letakkan dataset di folder `dataset/` dan gambar dashboard di `assets/images/dashboard-preview.png`. Jika dataset merupakan data latihan sintetis, jangan menyebutnya sebagai data aktual perusahaan.

## 🚀 Langkah Pembuatan Dashboard

### 1. Import dan persiapan data

1. Buka Power BI Desktop, pilih **Get data → Excel workbook**.
2. Pilih file `dataset_operasional_logistik_bahasa_indonesia.xlsx`.
3. Pada Navigator, pilih sheet **Data Logistik**, lalu klik **Transform Data**.
4. Di Power Query Editor, aktifkan **View → Column quality, Column distribution,** dan **Column profile** untuk memeriksa kualitas data.
5. Pastikan tipe data setiap kolom sudah benar. Untuk tanggal berformat `26/12/2025`, gunakan **Change Type → Using Locale**, pilih **Date** dan **Indonesian (Indonesia)** jika diperlukan.
6. Tambahkan kolom biaya melalui **Add Column → Custom Column**:
   - Nama kolom: `Total_Biaya_Rp`
   - Formula: `[Biaya_Pengiriman_Rp] + [Biaya_Penanganan_Rp]`
7. Periksa nilai kosong, error, dan duplikasi sesuai kebutuhan, lalu pilih **Close & Apply**.

### 2. Buat tabel kalender

Di Power BI Desktop, pilih **Modeling → New table**, kemudian masukkan DAX berikut:

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

Tabel ini menyediakan rentang tanggal untuk analisis waktu dan kolom `Tahun Bulan` untuk tren bulanan.

### 3. Hubungkan tabel

Pada **Model view**, hubungkan:

`Kalender[Date]` → `Data Logistik[Tanggal_Pesanan]`

Gunakan pengaturan **One-to-many (1:*)**, **Single** untuk arah filter, dan aktifkan relasi tersebut. Tabel Kalender menjadi sisi **One (1)**, sedangkan Data Logistik menjadi sisi **Many (*)**.

### 4. Buat measure DAX

Pilih tabel **Data Logistik**, lalu gunakan **Modeling → New measure** untuk membuat measure berikut satu per satu:

```dax
Total Pengiriman =
DISTINCTCOUNT('Data Logistik'[ID_Pengiriman])
```

Menghitung jumlah ID pengiriman yang unik.

```dax
Total Paket =
SUM('Data Logistik'[Jumlah_Paket])
```

Menjumlahkan seluruh paket.

```dax
Total Biaya Pengiriman =
SUM('Data Logistik'[Biaya_Pengiriman_Rp])
```

Menjumlahkan biaya pengiriman.

```dax
Total Biaya Penanganan =
SUM('Data Logistik'[Biaya_Penanganan_Rp])
```

Menjumlahkan biaya penanganan.

```dax
Total Biaya Operasional =
[Total Biaya Pengiriman] + [Total Biaya Penanganan]
```

Menjumlahkan biaya pengiriman dan biaya penanganan yang tersedia di dataset. Nilai ini **tidak otomatis mencakup seluruh biaya perusahaan**, seperti gaji, bahan bakar aktual, atau penyimpanan jika variabel tersebut tidak tersedia.

> **Catatan:** Measure `Pengiriman Selesai`, `Persentase Tepat Waktu`, dan `Pengiriman Terlambat` juga diperlukan untuk tiga KPI pada gambar. Rumusnya harus disesuaikan dengan nama dan kategori yang benar pada kolom `Status_Pengiriman`; pastikan definisi status “tepat waktu” sesuai dengan data yang digunakan.

### 5. Susun dashboard

Atur halaman melalui **Report view → Format page → Canvas settings → Type: 16:9**. Susun elemen dashboard seperti berikut:

- **Header:** `LOGISTICS OPERATIONS DASHBOARD`
- **Subjudul:** *Monitoring Pengiriman, Ketepatan Waktu, dan Biaya Operasional*
- **Slicer:** `Kalender[Date]` (gaya **Between**), `Moda_Pengiriman`, dan `Jenis_Layanan`.
- **Kartu KPI:** Total Pengiriman, Pengiriman Selesai, Persentase Tepat Waktu, Pengiriman Terlambat, dan Total Biaya Operasional.
- **Line chart:** X-axis `Kalender[Tahun Bulan]`, Y-axis `[Total Pengiriman]` untuk melihat tren pengiriman bulanan.
- **Donut chart:** Legend `Status_Pengiriman`, Values `[Total Pengiriman]` untuk melihat komposisi status pengiriman.
- **Bar chart biaya:** bandingkan biaya operasional berdasarkan kategori yang tersedia pada dataset.

Gunakan warna status secara konsisten, misalnya **hijau** untuk tepat waktu, **merah** untuk terlambat, **biru** untuk dalam pengiriman, dan **abu-abu** untuk dibatalkan. Pastikan label, satuan, dan format angka mudah dibaca.

## 📁 Struktur Repository

```text
Panduan-Pelatihan-Power-BI/
├── README.md
├── dataset/
│   └── dataset_operasional_logistik_bahasa_indonesia.xlsx
├── dashboard/
│   └── dashboard-logistik.pbix
└── assets/
    └── images/
        └── dashboard-preview.png
```

Sesuaikan nama dan lokasi file dengan isi repository yang benar-benar diunggah.

## 📈 Hasil

Dashboard membantu pengguna memantau volume pengiriman, status pengiriman, tren bulanan, dan biaya berdasarkan filter yang dipilih. Insight yang diperoleh bergantung pada kualitas, kelengkapan, dan definisi variabel dalam dataset.

## ⚠️ Catatan

- Dataset latihan bukan data aktual perusahaan kecuali sumbernya resmi dan terverifikasi.
- Jangan mengunggah data internal atau sensitif.
- Untuk membuka laporan `.pbix` atau dashboard online, pengguna mungkin memerlukan Power BI Desktop, akun Microsoft, atau izin akses.

---

**Learn the data. Understand the insight. Make better decisions.**
