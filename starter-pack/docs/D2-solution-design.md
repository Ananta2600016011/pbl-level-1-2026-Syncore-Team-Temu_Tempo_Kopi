# D2 — System & Solution Design

**Project**: Digital Problem Framing Mini Project — Temu Tempo Kopi  
**Tim**: Satria Ariya Prathama, Ananta Rizqi Fadhlurrohman, Muhammad Rasikh Zakki Aufa, Muhammad Dhiyauddin Nur, Alfin Farrel Gennaro | **Tanggal**: 11-11-2026 | **Versi**: v1.0  
**Template**: TPL-02  
**Worksheet terkait**: WS05, WS06, WS07, WS08  

---

## 1. Daftar Kebutuhan (User Story)

| # | User Story (Role - Goal - Benefit) | Prioritas |
|---|---|:---:|
| **US-01** | **Sebagai** Pemilik Temu Tempo Kopi (Mas Joy), **saya ingin** mengimpor berkas transaksi mingguan dari aplikasi kasir tablet untuk direkapitulasi secara otomatis, **sehingga** proses rekapitulasi dapat selesai dalam waktu kurang dari 5 menit tanpa rumus manual di Excel dan menghemat waktu libur hari Minggu. | **Tinggi** |
| **US-02** | **Sebagai** Pengelola Keuangan Kedai, **saya ingin** mencatat pengeluaran operasional bisnis dan penarikan pribadi (prive) secara terpisah, **sehingga** arus kas usaha tetap transparan dan laba bersih aktual kedai tidak terdistorsi oleh pengeluaran pribadi pemilik. | **Tinggi** |
| **US-03** | **Sebagai** Pengambil Keputusan Usaha, **saya ingin** melihat dasbor visual grafik mingguan (tren omzet, proporsi kategori menu kopi vs makanan, rasio pembayaran QRIS/Tunai, dan ranking menu), **sehingga** dapat mengevaluasi performa produk dan menentukan strategi promo bundling secara cepat dan akurat. | **Sedang** |

---

## 2. Kriteria Penerimaan (Acceptance Criteria)

| # | Kriteria Penerimaan (Format Given - When - Then) |
|---|---|
| **AC-01** | **Given** berkas laporan transaksi mingguan format CSV dari tablet Aplikasir telah diunduh, **when** data diproses oleh sistem rekapitulasi, **then** sistem otomatis menghitung total omzet kotor, total laba kotor (omzet - HPP), dan agregasi penjualan per menu dalam waktu < 5 detik dengan akurasi 100%. |
| **AC-02** | **Given** terdapat transaksi pengeluaran kas kedai untuk kebutuhan pribadi pemilik, **when** nominal dan keterangan diinput dengan memilih opsi pos "Prive", **then** sistem mencatat transaksi tersebut ke Buku Prive, memotong sisa kas fisik di laci, dan TIDAK mengurangi nilai laba bersih operasional kedai. |
| **AC-03** | **Given** data rekapitulasi penjualan dan pengeluaran kas telah selesai diproses, **when** pemilik membuka lembar dasbor evaluasi, **then** sistem menyajikan grafik Donut proporsi kategori menu, grafik Pie metode pembayaran, bar chart peringkat menu terlaris vs terendah, serta ringkasan laba bersih mingguan. |

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
  [Folder Bukti: BPMN dan Flowchart](https://drive.google.com/drive/folders/1wN8l2Wl4Sm-SjztREuGyHkVe6icVcpk6) serta file gambar lokal di folder repositori (`starter-pack/assets/bpmn_dan_flowchart/`).
- **Rancangan Pseudocode Terstruktur**: Disusun terstruktur dan independen terhadap bahasa pemrograman:

```text
// ==============================================================================
// FUNCTION 1: REKAPITULASI PENJUALAN KASIR DARI BERKAS CSV
// ==============================================================================
ALGORITMA Rekapitulasi_Penjualan_CSV
KAMUS DATA:
   file_csv : FILE_POINTER
   nomor_transaksi, nama_menu, kategori, metode_bayar, no_tx_sebelumnya : STRING
   qty : INTEGER
   harga_jual, harga_pokok, subtotal, laba_kotor_per_item : REAL
   Total_Omzet, Laba_Kotor, Total_Transaksi_Valid : REAL
   tabel_kategori, tabel_pembayaran, tabel_menu : DICTIONARY

ALUR LOGIKA:
   START
   Total_Omzet = 0
   Laba_Kotor = 0
   Total_Transaksi_Valid = 0
   no_tx_sebelumnya = NULL
   Inisialisasi tabel_kategori, tabel_pembayaran, tabel_menu
   
   OPEN file_csv
   WHILE NOT EOF(file_csv) DO
      READ baris dari file_csv
      nomor_transaksi = baris.nomor
      nama_menu = baris.nama_menu
      qty = baris.qty
      harga_jual = baris.harga_jual
      harga_pokok = baris.harga_pokok
      metode_bayar = baris.metode_bayar
      kategori = baris.kategori
      
      subtotal = qty * harga_jual
      Total_Omzet = Total_Omzet + subtotal
      
      laba_kotor_per_item = harga_jual - harga_pokok
      Laba_Kotor = Laba_Kotor + (laba_kotor_per_item * qty)
      
      tabel_menu[nama_menu] = tabel_menu[nama_menu] + qty
      tabel_kategori[kategori] = tabel_kategori[kategori] + subtotal
      tabel_pembayaran[metode_bayar] = tabel_pembayaran[metode_bayar] + subtotal
      
      IF nomor_transaksi != no_tx_sebelumnya THEN
         Total_Transaksi_Valid = Total_Transaksi_Valid + 1
         no_tx_sebelumnya = nomor_transaksi
      ENDIF
   ENDWHILE
   CLOSE file_csv
   
   RETURN Total_Omzet, Laba_Kotor, Total_Transaksi_Valid, tabel_menu, tabel_kategori, tabel_pembayaran
   END

// ==============================================================================
// FUNCTION 2: CASHFLOW & PENCATATAN POS PRIVE INTERAKTIF
// ==============================================================================
ALGORITMA Input_Cashflow_dan_Prive
KAMUS DATA:
   Total_Omzet, Laba_Kotor, Total_Pengeluaran_Bisnis, Total_Prive : REAL
   Laba_Bersih, Sisa_Kas, nominal : REAL
   pilihan_jenis, lanjut_input : STRING
   keterangan : STRING

ALUR LOGIKA:
   START
   RECEIVE Total_Omzet, Laba_Kotor FROM Function 1
   Total_Pengeluaran_Bisnis = 0
   Total_Prive = 0
   lanjut_input = "YA"
   
   WHILE lanjut_input == "YA" DO
      PRINT "Pilih Kategori: 1. Pengeluaran Bisnis / 2. Prive Pemilik"
      READ pilihan_jenis
      READ keterangan, nominal
      
      IF pilihan_jenis == "1" THEN
         Total_Pengeluaran_Bisnis = Total_Pengeluaran_Bisnis + nominal
         Simpan_Ke_Buku_Kas("BISNIS", keterangan, nominal)
      ELSE IF pilihan_jenis == "2" THEN
         Total_Prive = Total_Prive + nominal
         Simpan_Ke_Buku_Prive("PRIVE", keterangan, nominal)
      ENDIF
      
      PRINT "Apakah ingin input pengeluaran lagi? (YA/TIDAK)"
      READ lanjut_input
   ENDWHILE
   
   // Laba Bersih memotong Laba Kotor (bukan Total Omzet karena HPP sudah terpotong di F1)
   Laba_Bersih = Laba_Kotor - Total_Pengeluaran_Bisnis
   
   // Prive hanya memotong Sisa Kas Fisik dan tidak memotong Laba Usaha
   Sisa_Kas = Total_Omzet - Total_Pengeluaran_Bisnis - Total_Prive
   
   RETURN Total_Pengeluaran_Bisnis, Total_Prive, Laba_Bersih, Sisa_Kas
   END

// ==============================================================================
// FUNCTION 3: EVALUASI BISNIS & PERINTAH GRAFIK SPREADSHEET
// ==============================================================================
ALGORITMA Evaluasi_Bisnis_dan_Dashboard
KAMUS DATA:
   Total_Omzet, Laba_Kotor, Laba_Bersih, Sisa_Kas : REAL
   tabel_menu, tabel_kategori, tabel_pembayaran : DICTIONARY
   persen_kategori : DICTIONARY
   menu_terlaris, menu_kurang_diminati : STRING

ALUR LOGIKA:
   START
   RECEIVE data FROM Function 1 & Function 2
   
   // Safety check pembagian nol
   IF Total_Omzet > 0 THEN
      FOR EACH kat IN tabel_kategori DO
         persen_kategori[kat] = (tabel_kategori[kat] / Total_Omzet) * 100
      ENDFOR
      menu_terlaris = MAX_KEY(tabel_menu)
      menu_kurang_diminati = MIN_KEY(tabel_menu)
   ELSE
      SET persen_kategori = 0
      menu_terlaris = "N/A"
      menu_kurang_diminati = "N/A"
   ENDIF
   
   PRINT_EXECUTIVE_SUMMARY(Total_Omzet, Laba_Kotor, Laba_Bersih, Sisa_Kas, menu_terlaris)
   GENERATE_SPREADSHEET_CHART("DonutChart", tabel_kategori, "Proporsi Omzet Kategori")
   GENERATE_SPREADSHEET_CHART("PieChart", tabel_pembayaran, "Metode Pembayaran")
   GENERATE_SPREADSHEET_CHART("BarChart", tabel_menu, "Performa Kuantitas Menu")
   END
```

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
