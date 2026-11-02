# **WORKBOOK: LEMBAR KERJA MAHASISWA WS05**

## **Formulasi Kebutuhan Fungsional: User Story & Acceptance Criteria**

* **Mata Kuliah**: Konsep Sistem Informasi (KSI)
* **Kerangka Kerja**: Project-Based Learning (PBL) Level 1
* **Fase Learning Spine**: Fase 3 — Define (Minggu 3)
* **Sub-CPMK / SFIA**: S-01.1 (Intermediate - Problem Framing) & S-03.1 (Intermediate - Pemetaan SI) | SFIA BUSA L1, REQM L2
* **Keterkaitan Deliverable**: Bahan Utama Deliverable D2 (System & Solution Design - TPL-02)

---

### **1. Identifikasi Kelompok & Rotasi Kepemimpinan**

* **Nama Kelompok**: Syncore Team
* **Objek UMKM Mitra**: Temu Tempo Kopi
* **Phase Lead 3 (Define)**: Satria Ariya Prathama (Mahasiswa C)
* **Anggota Tim**: 1. Muhammad Rasikh Zakki Aufa, 2. Ananta Rizqi Fadhlurrohman, 3. Muhammad Dhiyauddin Nur, 4. Alfin Farrel Gennaro

---

### **2. Landasan Konseptual: Analisis Sistem "What" vs "How"**

Dalam tahap Systems Analysis, fokus utama tim adalah menentukan APA (What) yang dibutuhkan pengguna bisnis untuk memecahkan masalahnya, BUKAN BAGAIMANA (How) sistem dibangun secara teknis (Marakas & O'Brien, 2013).

User Story merepresentasikan kebutuhan fungsional dari sudut pandang pengguna bisnis dengan pola:
$$\text{"Sebagai [], Saya ingin [], Sehingga []"}$$
Acceptance Criteria (Given-When-Then) mendefinisikan batas kondisi kapan sebuah fitur dinyatakan selesai dan memenuhi syarat penerimaan pengguna (Rainer et al., 2021).

---

### **3. Workspace A: Formulasi User Story Fungsional**

Petakan minimal 3 User Story Utama yang langsung menjawab akar masalah pada D1 / WS04:

#### **User Story 1 (Prioritas Utama / Rekapitulasi Otomatis)**

* **Sebagai (As a)**: Pemilik Temu Tempo Kopi (Mas Joy)
* **Saya ingin (I want to)**: Memindahkan atau mengimpor data transaksi mingguan dari aplikasi kasir ke dalam sistem pengolah data agar direkapitulasi secara otomatis tanpa rumus manual di Excel.
* **Sehingga (So that)**: Proses rekapitulasi dapat diselesaikan lebih cepat (menghemat waktu libur), akurat, dan meminimalkan potensi kesalahan hitung margin maupun transaksi yang terlewat.

#### **User Story 2 (Pemisahan Kas Usaha vs Kas Pribadi)**

* **Sebagai (As a)**: Pemilik Temu Tempo Kopi (Mas Joy)
* **Saya ingin (I want to)**: Fitur pencatatan khusus untuk memisahkan pengeluaran operasional kedai dengan penarikan dana pribadi pemilik (prive).
* **Sehingga (So that)**: Arus kas operasional kedai dan saldo kas fisik di laci dapat dipantau secara akurat tanpa tercampur kebutuhan pribadi.

#### **User Story 3 (Visualisasi Grafik dalam Evaluasi)**

* **Sebagai (As a)**: Pemilik Temu Tempo Kopi (Mas Joy)
* **Saya ingin (I want to)**: Melihat ringkasan performa penjualan kedai dalam bentuk grafik visual yang ringkas dan mudah dipahami.
* **Sehingga (So that)**: Evaluasi bisnis mingguan dapat dilakukan dengan cepat untuk melihat tren omzet serta perbandingan menu yang paling laris vs kurang bergerak tanpa harus membaca tabel angka mentah.

---

### **4. Workspace B: Acceptance Criteria Berbasis Skenario (Given-When-Then)**

Susun kriteria penerimaan terstruktur untuk User Story 1 (mencakup Skenario Sukses dan Skenario Penanganan Eror):

#### **Skenario 1A: Transaksi Penjualan Berhasil (Happy Path)**

* **Diberikan (Given)**: Pemilik memiliki file ekspor data transaksi yang valid dari aplikasi kasir.
* **Ketika (When)**: Pemilik memindahkan (mengunggah/mengimpor) file data transaksi tersebut ke dalam halaman sistem rekapitulasi.
* **Maka (Then)**: Sistem merekap secara otomatis dan menampilkan total omzet, rincian pembayaran (Tunai vs QRIS), margin keuntungan, serta status "Rekapitulasi Berhasil".

#### **Skenario 1B: Penanganan Berkas Rusak / Eror (Exception Path)**

* **Diberikan (Given)**: File data transaksi rusak, salah format (bukan format standar ekspor kasir), atau datanya kosong.
* **Ketika (When)**: Pemilik mencoba memindahkan (mengunggah/mengimpor) file data transaksi tersebut ke dalam sistem.
* **Maka (Then)**: Sistem menolak proses, menampilkan pesan peringatan bahwa format data tidak valid, dan tidak merusak data rekapitulasi yang sudah ada sebelumnya.

---

### **5. Workspace C: Catatan Validasi Kebutuhan dengan Mitra (Field Confirmation)**

* **Tanggal Validasi**: 26 Oktober 2026 (Terjadwal) | Narahubung: Mas Joy (Pemilik)
* **Narahubung Mitra**: Mas Joy (Pemilik)
* **Hasil Konfirmasi User Story**:
  - [x] Seluruh User Story disetujui mitra
    **bukti persetujuan**: [Buka di Google Drive](https://docs.google.com/document/d/1iEeE0Nn09S2G_LeHFvQMmidNzTp6dBkkdoTBe9warUA/edit?usp=sharing)
  - [ ] Terdapat penyesuaian/revisi kebutuhan (Tuliskan revisi jika ada):
    __________________________________________________________________

---

### **6. Verifikasi Integritas AI (TPL-07) & Pengesahan**

**Penggunaan AI Co-pilot:**
Apakah tim menggunakan AI untuk membantu merumuskan skenario Given-When-Then? [ ] Ya [x] Tidak  
*(Jika Ya, wajib melampirkan formulir TPL-07: AI Usage Disclosure & Verification Note).*

Tanda Tangan Tim & Pengesahan Dosen:

```text
Phase Lead 3: Satria Ariya Prathama[Lihat Tanda Tangan Digital](../assets/tanda_tangan_team/tanda_tangan_satria.jpg) (Tanggal: 26 Oktober 2026)
```
```text
Dosen Coach: _______________________ (Tanggal: __________)  [ ] Approved
```
