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
| 1. Process Layer (Alur Kerja To-Be) | Pemilik tetap melayani transaksi kasir menggunakan aplikasi kasir dengan tablet. Data transaksi disalin/diimpor secara berkala ke Google Sheets untuk direkapitulasi secara otomatis (< 5 menit), penarikan pribadi dicatat pada pos prive, dan grafik evaluasi bisnis terbarui otomatis. | Memangkas waktu rekapitulasi manual di hari Minggu dari ± 60 menit menjadi < 5 menit. Batasan: Tidak membuat aplikasi kasir baru dan tidak membuat cetak struk dari spreadsheet. |
| 2. Data Layer (Struktur Data Logis) | Tabel Data Transaksi (No TRX, Tanggal, Menu, Kategori, Qty, Harga, Total, Metode Bayar), Tabel Keuangan Kas (Pemasukan, Beban Operasional, Pos Prive), dan Tabel Rekapitulasi/Agregasi. | Pos Prive dicatat terpisah dari pengeluaran operasional agar tidak tercampur laba bersih usaha. Penyimpanan pada tab Google Sheets dan file CSV lokal. |
| 3. Application Layer (Modul Program) | Modul Rekapitulasi Penjualan Otomatis (formula SUM, SUMIF, COUNTIF), Modul Pencatatan Kas & Pos Prive, Modul Dasbor Visualisasi Grafik, dan Modul Prototipe Python CLI (main.py). | Menjaga formula spreadsheet tetap sederhana dan mudah dipahami pemilik. Prototipe Python CLI dibuat terpisah untuk demonstrasi logika pemrograman. |
| 4. Infrastructure Layer (Perangkat Fisik) | Tablet (kasir eksisting mitra), Laptop/Tablet (pengolahan spreadsheet & CLI), Browser Google Chrome, Google Drive, dan koneksi internet Wi-Fi kedai. | Memanfaatkan perangkat dan layanan cloud gratis yang sudah dimiliki mitra tanpa biaya server tambahan. |

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

Rancangan logika sistem Temu Tempo Kopi dibagi menjadi diagram proses bisnis (BPM) dan 3 fungsi modular:
1. **Business Process Model (BPM Swimlane)**: Memetakan interaksi nyata antara Customer, Kasir (Tablet Aplikasir), Pemilik Kedai (Mas Joy), dan Sistem (Google Sheets/Python).
2. **Flowchart Function 1 (Rekapitulasi Penjualan CSV)**: Membaca berkas .csv kasir per baris transaksi (1-loop) untuk menghitung Total Omzet, Laba Kotor (memotong HPP bahan baku per menu), akumulasi omzet per kategori menu, metode pembayaran (Cash vs QRIS), dan wadah kuantitas menu terjual.
3. **Flowchart Function 2 (Cashflow & Pos Prive Interaktif)**: Menerima return omzet dan laba kotor dari Function 1, memproses live-input pengeluaran (Beban Operasional vs Prive Pemilik), serta menghitung Laba Bersih Usaha (Laba_Kotor - Beban) dan Sisa Kas Fisik (Total_Omzet - Beban - Prive).
4. **Flowchart Function 3 (Dashboard Evaluasi Bisnis & Grafik)**: Menerima seluruh variabel return dari Function 1 dan 2, menghitung proporsi persentase (dengan safety check total_omzet > 0), menentukan menu terlaris/kurang diminati, dan memberi instruksi pembuatan grafik visual di spreadsheet.

- **Tautan Berkas Digital (Google Drive)**: [Buka Folder Diagram BPMN & Flowchart](https://drive.google.com/drive/folders/1wN8l2Wl4Sm-SjztREuGyHkVe6icVcpk6)
- **Arsip Berkas Gambar Lokal**: Tersedia di direktori proyek (BPM_TemuTempoKopi.jpg.jpeg, Flowchart_Function1_Rekap.jpg.jpeg, Flowchart_Function2_Cashflow.jpg.jpeg, Flowchart_Function3_Grafik.png, dan system_utama.jpg).

#### **5. PSEUDOCODE TERSTRUKTUR (INDEPENDEN TEKNOLOGI)**

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

### **CHECKLIST REFLEKSI & PENGESAHAN WS07**

* [x] Arsitektur 4 lapisan SI telah terdefinisi konsisten.
* [x] Tabel IPO mencakup kriteria Storage dan Control (penanganan eror).
* [x] Flowchart menggambarkan logika percabangan (IF-ELSE) dan perulangan (Loops) tanpa infinite loop.
* [x] Pseudocode terstruktur dengan rapi dan independen terhadap bahasa pemrograman.
* [x] Form TPL-07 (AI Usage Disclosure & Verification Note) telah dilampirkan.

Tanggal Pengesahan: 11 November 2026  
Tanda Tangan Phase Lead 4 (Design): [Lihat Tanda Tangan Digital](../../assets/tanda_tangan/tanda_tangan_satria.jpg)  
Tanda Tangan Dosen Pembimbing / Coach: ____________________
