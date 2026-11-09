# **WORKBOOK: LEMBAR KERJA MAHASISWA (WS07)**

## **Simple Solution Design — IPO, Flowchart & Pseudocode**

---

### **INFORMASI UTAMA**

* **Mata Kuliah**: Konsep Sistem Informasi (KSI)
* **Kerangka Kerja**: Project-Based Learning (PBL) Level 1
* **Learning Moment**: Fase 4: Design (Minggu 5–6)
* **Sub-CPMK / SFIA**: S-03.1 (Intermediate) | SFIA ARCH L2, DESN L2
* **Keterkaitan Deliverable**: Sumber utama pembuatan Deliverable D2 (System & Solution Design - TPL-02)
* **Phase Lead**: Satria Ariya Prathama (Phase Lead 4 — Design)

---

### **RUANG KERJA TIM (WORKSPACE)**

#### **1. IDENTIFIKASI KELOMPOK & SOLUSI**

* **Nama Tim**: Syncore Team
* **Nama UMKM Mitra**: Temu Tempo Kopi
* **Judul Solusi SI**: Sistem Rekapitulasi Penjualan Otomatis, Pemisahan Kas Prive, dan Dasbor Evaluasi Bisnis Temu Tempo Kopi Berbasis Google Sheets & Prototipe Python
* **Phase Lead 4 (Design)**: Satria Ariya Prathama (2600016023)

#### **2. PEMETAAN ARSITEKTUR 4 LAPISAN SI (M05)**

Petakan solusi Anda ke dalam 4 lapisan arsitektur terintegrasi:

| Lapisan Arsitektur | Komponen Solusi Tim | Keterangan & Batasan |
| --- | --- | --- |
| 1. Process Layer (Alur Kerja To-Be) | Pemilik tetap melayani transaksi kasir menggunakan aplikasi kasir smartphone eksisting. Data transaksi disalin/diimpor secara berkala ke Google Sheets untuk direkapitulasi secara otomatis (< 5 menit), penarikan pribadi dicatat pada pos prive, dan grafik evaluasi bisnis terbarui otomatis. | Memangkas waktu rekapitulasi manual di hari Minggu dari ± 60 menit menjadi < 5 menit. Batasan: Tidak membuat aplikasi kasir baru dan tidak membuat cetak struk dari spreadsheet. |
| 2. Data Layer (Struktur Data Logis) | Tabel Data Transaksi (No TRX, Tanggal, Menu, Kategori, Qty, Harga, Total, Metode Bayar), Tabel Keuangan Kas (Pemasukan, Beban Operasional, Pos Prive), dan Tabel Rekapitulasi/Agregasi. | Pos Prive dicatat terpisah dari pengeluaran operasional agar tidak mengaburkan laba bersih usaha. Penyimpanan pada tab Google Sheets dan file CSV lokal. |
| 3. Application Layer (Modul Program) | Modul Rekapitulasi Penjualan Otomatis (formula SUM, SUMIF, COUNTIF), Modul Pencatatan Kas & Pos Prive, Modul Dasbor Visualisasi Grafik, dan Modul Prototipe Python CLI (main.py). | Menjaga formula spreadsheet tetap sederhana dan mudah dipahami pemilik. Prototipe Python CLI dibuat terpisah untuk demonstrasi logika pemrograman. |
| 4. Infrastructure Layer (Perangkat Fisik) | Smartphone Android (kasir eksisting mitra), Laptop/PC (pengolahan spreadsheet & CLI), Browser Google Chrome, Google Drive, dan koneksi internet Wi-Fi kedai. | Memanfaatkan perangkat dan layanan cloud gratis yang sudah dimiliki mitra tanpa biaya server tambahan. |

#### **3. SPESIFIKASI IPO (INPUT - PROCESSING - OUTPUT - STORAGE - CONTROL)**

##### **Fitur Fungsional Utama 1: Rekapitulasi Otomatis Data Penjualan Mingguan**

* **Input**: Data transaksi kasir (nomor transaksi, tanggal, waktu, menu, kategori, kuantitas, harga satuan, metode pembayaran) dan rentang periode rekapitulasi.
* **Processing**: Validasi kelengkapan data, kalkulasi subtotal (kuantitas * harga), penjumlahan total omzet (SUM), rekapitulasi omzet per kategori produk (SUMIF), rekap metode bayar Cash vs QRIS, dan pengurutan menu terlaris vs menu lambat.
* **Output**: Tabel ringkasan rekapitulasi penjualan mingguan (total omzet kotor, total transaksi, proporsi omzet kategori, rincian pembayaran) serta status rekapitulasi berhasil.
* **Storage**: Tab Rekap_Penjualan pada Google Sheets dan/atau file lokal data_penjualan.csv.
* **Control (Error Handling)**: Pengecekan data kosong/non-numerik, penolakan kuantitas <= 0 atau harga negatif, serta proteksi pembatalan proses jika format berkas tidak sesuai kolom standar.

##### **Fitur Fungsional Utama 2: Pencatatan Keuangan Operasional & Pemisahan Pos Prive**

* **Input**: Tanggal transaksi, jenis aliran kas (Pemasukan Bisnis, Pengeluaran Operasional, atau Prive Pemilik), keterangan transaksi, nominal rupiah, dan saldo kas awal.
* **Processing**: Validasi nominal (> 0), pengelompokan akun (Pengeluaran Operasional dicatat sebagai beban usaha; Prive dicatat di pos terpisah dan tidak mengurangi laba usaha melainkan hanya mengurangi saldo kas akhir), kalkulasi laba operasional bersih, dan kalkulasi saldo fisik kas akhir.
* **Output**: Ringkasan laporan arus kas (cash flow), laba operasional bersih kedai, log catatan penarikan prive pemilik, dan informasi saldo kas fisik aktual di laci.
* **Storage**: Tab Keuangan_Kas & Buku_Prive pada Google Sheets dan/atau file lokal data_keuangan.csv.
* **Control (Error Handling)**: Menolak nominal <= 0 dengan notifikasi eror, serta menampilkan peringatan (warning) jika penarikan kas melebihi saldo kas riil kedai.

#### **4. DIAGRAM ALIR (FLOWCHART) LOGIKA PROGRAM**

Petunjuk: Gambarkan diagram alir terstruktur menggunakan simbol standar (Persegi Panjang = Proses, Belah Ketupat = Keputusan IF-ELSE, Jajar Genjang = Input/Output, Oval = Start/End). Lampirkan hasil gambaran digital/foto kertas A3 di bawah ini.

```text
[ TEMPELKAN GAMBAR DIAGRAM FLOWCHART DIGITAL / FOTO DRAF A3 DI SINI ]
```

#### **5. PSEUDOCODE TERSTRUKTUR (INDEPENDEN TEKNOLOGI)**

Tuliskan kode semu terstruktur (pseudocode) untuk modul logika utama solusi Anda:

```text
ALGORITMA Transaksi_Kasir_Teguk
KAMUS DATA:
   kode_produk, nama_produk : STRING
   harga, jumlah, subtotal, total_bayar, uang_tunai, kembalian : REAL
   stok_tersedia : INTEGER

ALUR LOGIKA:
   START
   READ kode_produk, jumlah
   
   IF stok_tersedia >= jumlah THEN
      subtotal = harga * jumlah
      total_bayar = subtotal
      PRINT total_bayar
      
      READ uang_tunai
      IF uang_tunai >= total_bayar THEN
         kembalian = uang_tunai - total_bayar
         stok_tersedia = stok_tersedia - jumlah
         PRINT "Transaksi Sukses", kembalian
         UPDATE Tabel_Stok, Tabel_Transaksi
      ELSE
         PRINT "ERROR: Uang tunai kurang!"
      ENDIF
   ELSE
      PRINT "ERROR: Stok tidak mencukupi!"
   ENDIF
   END
```

---

### **CHECKLIST REFLEKSI & PENGESAHAN WS07**

* [ ] Arsitektur 4 lapisan SI telah terdefinisi konsisten.
* [ ] Tabel IPO mencakup kriteria Storage dan Control (penanganan eror).
* [ ] Flowchart menggambarkan logika percabangan (IF-ELSE) dan perulangan (Loops) tanpa infinite loop.
* [ ] Pseudocode terstruktur dengan rapi dan independen terhadap bahasa pemrograman.
* [ ] Form TPL-07 (AI Usage Disclosure & Verification Note) telah dilampirkan.

```text
Tanggal Pengesahan: ____________________
Tanda Tangan Phase Lead 4 (Design): ____________________
Tanda Tangan Dosen Pembimbing / Coach: ____________________
```
