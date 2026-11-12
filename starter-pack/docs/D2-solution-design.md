# D2 — System & Solution Design

**Project**: Digital Problem Framing Mini Project — Temu Tempo Kopi  
**Tim**: Satria Ariya Prathama, Ananta Rizqi Fadhlurrohman, Muhammad Rasikh Zakki Aufa, Muhammad Dhiyauddin Nur, Alfin Farrel Gennaro | **Tanggal**: 11-11-2026 | **Versi**: v1.0  
**Template**: TPL-02  
**Worksheet terkait**: WS05, WS06, WS07, WS08  

---

## 1. Daftar Kebutuhan (User Story)

| # | User Story (Role - Goal - Benefit) | Prioritas |
|---|---|:---:|
| **US-01** | **Sebagai** Pemilik Temu Tempo Kopi (Mas Joy),<br>**Saya ingin** mengimpor berkas transaksi mingguan dari aplikasi kasir tablet untuk direkapitulasi secara otomatis,<br>**Sehingga** proses rekapitulasi dapat selesai dalam waktu kurang dari 5 menit tanpa rumus manual di Excel dan menghemat waktu libur hari Minggu. | **Tinggi** |
| **US-02** | **Sebagai** Pengelola Keuangan Kedai,<br>**Saya ingin** mencatat pengeluaran operasional bisnis dan penarikan pribadi (prive) secara terpisah,<br>**Sehingga** arus kas usaha tetap transparan dan laba bersih aktual kedai tidak terdistorsi oleh pengeluaran pribadi pemilik. | **Tinggi** |
| **US-03** | **Sebagai** Pengambil Keputusan Usaha,<br>**Saya ingin** melihat dasbor visual grafik mingguan (tren omzet, proporsi kategori menu kopi vs makanan, rasio pembayaran QRIS/Tunai, dan ranking menu),<br>**Sehingga** dapat mengevaluasi performa produk dan menentukan strategi promo bundling secara cepat dan akurat. | **Sedang** |

---

## 2. Kriteria Penerimaan (Acceptance Criteria)

| # | Kriteria Penerimaan (Format Given - When - Then) |
|---|---|
| **AC-01** | **Given** berkas laporan transaksi mingguan format CSV dari tablet Aplikasir telah diunduh,<br>**When** data diproses oleh sistem rekapitulasi,<br>**Then** sistem otomatis menghitung total omzet kotor, total laba kotor (omzet - HPP), dan agregasi penjualan per menu dalam waktu < 5 detik dengan akurasi 100%. |
| **AC-02** | **Given** terdapat transaksi pengeluaran kas kedai untuk kebutuhan pribadi pemilik,<br>**When** nominal dan keterangan diinput dengan memilih opsi pos "Prive",<br>**Then** sistem mencatat transaksi tersebut ke Buku Prive, memotong sisa kas fisik di laci, dan TIDAK mengurangi nilai laba bersih operasional kedai. |
| **AC-03** | **Given** data rekapitulasi penjualan dan pengeluaran kas telah selesai diproses,<br>**When** pemilik membuka lembar dasbor evaluasi,<br>**Then** sistem menyajikan grafik Donut proporsi kategori menu, grafik Pie metode pembayaran, bar chart peringkat menu terlaris vs terendah, serta ringkasan laba bersih mingguan. |

---

## 3. Success Metrics (BPI / DMAIC Six Sigma)

| Dimensi Metrik | Parameter Kinerja | Baseline (As-Is) | Target Solusi (To-Be) | Cara Mengukur |
|---|---|---|---|---|
| **Efisiensi (Waktu)** | Durasi rekapitulasi penjualan mingguan pemilik | ± 60 menit (1 jam) setiap hari Minggu saat libur | < 5 menit per minggu (Penghematan waktu > 90%) | Stopwatch pengujian saat berkas CSV diimpor ke sistem |
| **Efektivitas (Akurasi)** | Frekuensi transaksi terlewat / salah rekap | 1–2 transaksi per minggu saat kedai ramai | 0 transaksi salah rekap (Akurasi 100%) | Rekonsiliasi silang jumlah nota kasir vs hasil ringkasan sistem |
| **Efektivitas (Tata Kelola)** | Pemisahan kas usaha dengan uang pribadi (Prive) | Belum ada pos pencatatan (kas operasional bercampur) | 100% penarikan pribadi tercatat terpisah pada pos Prive | Audit saldo fisik kas di laci terhadap catatan buku kas |
| **Efektivitas (Analisis Bisnis)** | Kemudahan evaluasi tren penjualan menu | 0 jam/minggu (Excel murni deretan angka mentah) | Dasbor grafik visual terbarui otomatis tiap minggu | Uji keterbacaan grafik performa kedai bersama pemilik |

---

## 4. Desain Solusi

### 4.1 Konsep Solusi (Ringkasan)
Solusi yang dibangun adalah sistem pengolahan data pasca-penjualan berbasis Google Sheets yang didukung prototipe program Python CLI. Sistem ini memanfaatkan berkas ekspor CSV dari aplikasi kasir eksisting mitra (*Aplikasir* pada tablet) tanpa mengganti aplikasi kasir yang sudah nyaman digunakan. Sistem mengotomatiskan kalkulasi omzet, HPP, dan laba kotor (Function 1), memisahkan pencatatan beban usaha dengan pos prive pemilik (Function 2), serta menyajikan grafik visual performa bisnis mingguan (Function 3) untuk memangkas waktu kerja administrasi Mas Joy di hari libur.

### 4.2 Peta Komponen (IPO & 4 Lapisan Arsitektur)

```text
[ INPUT ]                       [ PEMROSESAN LOGIKA ]                   [ OUTPUT ]
• Berkas CSV Aplikasir    ───►  • Function 1: Rekap Penjualan CSV  ───► • Tabel Rekap Mingguan
  (Nomor, Menu, QTY,            • Function 2: Cashflow & Prive          • Laporan Laba Bersih
   Harga Jual, HPP, Bayar)      • Function 3: Evaluasi & Grafik         • Saldo Sisa Kas Fisik
• Input Kasir/Prive             (Validasi Data, SUMIF, Kalkulasi)       • Dasbor Visual Grafik
         │                                                                     │
         └───────────────────► [ PENYIMPANAN DATA ] ◄──────────────────────────┘
                               • Google Sheets (Tab Rekap & Kas)
                               • Berkas Lokal data_penjualan.csv
```

- **Process Layer**: Transaksi kasir tetap dilayani di tablet kasir; berkas CSV diekspor mingguan dan diolah sistem dalam waktu < 5 menit.
- **Data Layer**: Tabel Transaksi Kasir, Tabel Pengeluaran Operasional, Tabel Pos Prive, dan Tabel Agregasi Menu.
- **Application Layer**: Modul Rekapitulasi Penjualan, Modul Buku Kas & Prive, Modul Dasbor Visualisasi, dan Prototipe Python CLI.
- **Infrastructure Layer**: Tablet kasir kedai, laptop pengolah data, Google Drive/Sheets, dan koneksi Wi-Fi kedai.

### 4.3 Flowchart & Pseudocode

- **Arsip Diagram Flowchart & BPMN**: Seluruh diagram alur keputusan (Flowchart Function 1–3) dan diagram swimlane proses bisnis (BPM) diarsipkan pada Google Drive:  
  [Folder Bukti: BPMN dan Flowchart](https://drive.google.com/drive/folders/1wN8l2Wl4Sm-SjztREuGyHkVe6icVcpk6) serta file gambar lokal di folder repositori.
- **Rancangan Pseudocode Modular**: Disusun terstruktur dan independen bahasa pemrograman (Function 1: `Rekapitulasi_Penjualan_CSV`, Function 2: `Input_Cashflow_dan_Prive`, Function 3: `Evaluasi_Bisnis_dan_Dashboard`) sebagaimana tertuang lengkap pada dokumen WS07.

---

## 5. Hasil Validasi Pemilik Usaha

- **Tanggal validasi**: 21 Oktober 2026 (Observasi 2) & 11 November 2026 (Validasi User Story)
- **Feedback pemilik**: Mas Joy sangat menyambut baik solusi alat bantu rekapitulasi ini karena tidak mengharuskannya mengganti aplikasi kasir utama di tablet. Mas Joy juga menyetujui opsi ekspor berkas berformat `CSV Coma` dari Aplikasir dan membenarkan bahwa pemisahan pos prive adalah solusi yang paling dibutuhkan untuk mengatasi selisih kas.
- **Perubahan setelah validasi**:
  1. Menegaskan batasan sistem: membatalkan rencana awal pembuatan POS kasir baru agar operasional harian kedai tidak terganggu.
  2. Menyesuaikan spesifikasi perangkat: input data mengacu pada tablet kasir eksisting kedai.
  3. Memasukkan modul grafik visual mingguan untuk menggantikan tabel angka mentah Excel pemilik.

---

**Status**: ⬜ Draf → ⬜ Review Tim → ⬜ Validasi Pemilik → ☑️ Final (GATE 1)
