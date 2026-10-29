# **WORKBOOK: LEMBAR KERJA MAHASISWA WS06**

## **Success Metrics (BPI/DMAIC) & Pemetaan Komponen SI Awal**

* **Mata Kuliah**: Konsep Sistem Informasi (KSI)
* **Kerangka Kerja**: Project-Based Learning (PBL) Level 1
* **Fase Learning Spine**: Fase 3 — Define (Minggu 4)
* **Sub-CPMK / SFIA**: S-01.1 (Intermediate - Problem Framing) & S-03.1 (Intermediate - Pemetaan SI) | SFIA BUSA L1, METR L2
* **Keterkaitan Deliverable**: Bahan Utama Deliverable D1 Final (TPL-01) & D2 Draf (TPL-02)

---

### **1. Identifikasi Kelompok & Rotasi Kepemimpinan**

* **Nama Kelompok**:Syncore Team
* **Objek UMKM Mitra**: Temu Tempo Kopi
* **Phase Lead 3 (Define)**: Satria Ariya Prathama (NIM: 2600016023)
* **Anggota Tim**: Ananta Rizqi Fadhlurrohman, Muhammad Rasikh Zakki Aufa, Muhammad Dhiyauddin Nur, Alfin Farrel Gennaro

---

### **2. Landasan Konseptual: Metrik BPI & Pemetaan 5 Pilar SI**

Business Process Improvement (BPI) mengukur keberhasilan perbaikan proses bisnis melalui dua dimensi utama (Rainer et al., 2014):
* **Efisiensi (Efficiency)**: Mengukur penghematan sumber daya (doing things well), seperti efisiensi waktu siklus transaksi atau reduksi biaya operasional.
* **Efektivitas (Effectiveness)**: Mengukur pencapaian kualitas/tujuan (doing the right things), seperti akurasi data stok, penurunan angka selisih kasir, dan kepuasan pelanggan.
* **Model 5 Pilar SI O'Brien**: Solusi sistem informasi dipetakan ke dalam pilar People, Hardware, Software, Data, dan Network (Marakas & O'Brien, 2013).

---

### **3. Workspace A: Matrik Metrik Keberhasilan Bisnis (DMAIC Six Sigma)**

| Dimensi Metrik | Parameter Kinerja | Kondisi Baseline (As-Is) | Target Solusi (To-Be) | Metode Pengukuran |
| --- | --- | --- | --- | --- |
| Efisiensi (Waktu) | Durasi rekapitulasi mingguan pemilik | ± 60 menit (1 jam) setiap hari Minggu saat libur | < 5 menit per minggu (Penghematan waktu > 90%) | Pengujian waktu saat data kasir diimpor ke spreadsheet/sistem |
| Efektivitas (Akurasi) | Frekuensi transaksi terlewat / salah rekap | 1–2 transaksi per minggu saat kedai ramai | 0 transaksi salah rekap (Akurasi data 100%) | Rekonsiliasi silang jumlah nota kasir vs hasil ringkasan sistem |
| Efektivitas (Tata Kelola) | Pemisahan kas usaha dengan uang pribadi (Prive) | Belum ada pos pencatatan (uang kas kedai sering terpakai untuk keperluan pribadi) | 100% penarikan dana pribadi tercatat terpisah pada modul prive | Audit berkala saldo fisik kas di laci terhadap catatan buku kas |
| Efektivitas (Analisis Bisnis) | Kemudahan evaluasi tren penjualan menu | 0 jam / minggu (Excel murni deretan angka mentah tanpa formula grafik) | Grafik visual otomatis (tren omzet mingguan & komparasi penjualan menu) | Uji coba keterbacaan grafik performa kedai bersama pemilik |

---

### **4. Workspace B: Pemetaan Arsitektur 5 Pilar SI Solusi Awal**

```text
┌────────────────────────────────────────────┐
│                      PETA 5 PILAR SISTEM INFORMASI                      │
├────────────────────────────────────────────┤
│ 1. PEOPLE RESOURCES (Pengguna & Spesialis)                              │
│    • Pengguna Akhir: Mas Joy (Pemilik & Pengelola Tunggal Temu Tempo Kopi) │
│    • Pengembang SI: Tim Syncore (Satria, Ananta, Zakki, Dhiyauddin, Alfin) │
├────────────────────────────────────────────┤
│ 2. HARDWARE RESOURCES (Perangkat Mesin & Media)                         │
│    • Perangkat Fisik Input: Smartphone Android (kasir harian) & Laptop/PC │
│    • Perangkat Fisik Output: Layar Monitor Laptop / Layar Smartphone Pemilik │
├────────────────────────────────────────────┤
│ 3. SOFTWARE RESOURCES (Aplikasi & Prosedur Operational)                 │
│    • Aplikasi Sistem: Online Spreadsheet (Google Sheets) & Prototipe Python CLI sederhana untuk pengolahan file transaksi │
│    • Prosedur SOP: Prosedur ekspor berkas kasir, pencatatan prive, dan pemantauan grafik evaluasi penjualan │
├────────────────────────────────────────────┤
│ 4. DATA RESOURCES (Struktur Data & Basis Data)                          │
│    • Data Transaksi: Berkas ekspor transaksi kasir (.csv / spreadsheet) │
│    • Data Finansial: Log pos penarikan prive & riwayat margin mingguan │
├────────────────────────────────────────────┤
│ 5. NETWORK RESOURCES (Jaringan Communication & Media)                   │
│    • Konektivitas: Jaringan Internet / Wi-Fi Kedai (untuk sinkronisasi Cloud Spreadsheet secara online agar bisa diakses fleksibel lewat HP/laptop Mas Joy) │
└────────────────────────────────────────────┘
```

---

### **5. Workspace C: Lembar Persetujuan Formal Mitra (Sign-Off)**

Dengan ini, pemilik / manajer UMKM mitra menyatakan setuju atas rumusan kebutuhan fungsional, target metrik keberhasilan, dan batas cakupan sistem yang dirancang oleh tim mahasiswa.

* **Nama UMKM Mitra**: Temu Tempo Kopi
* **Nama Pemilik / Pengelola**: Mas Joy
* **Tanggal Persetujuan**: ____________________

**Tanda Tangan Persetujuan Mitra:**

```text

(Cap / Tanda Tangan Pemilik UMKM Mitra)
```

---

### **6. Verifikasi Integritas AI (TPL-07) & Pengesahan**

**Penggunaan AI Co-pilot:
Apakah tim menggunakan AI untuk membantu merumuskan metrik BPI / diagram 5 pilar SI? [x] Ya  [ ] Tidak
(Jika Ya, wajib melampirkan formulir TPL-07: AI Usage Disclosure & Verification Note).**

Tanda Tangan Tim & Pengesahan Dosen:

```text
Phase Lead 3: Satria Ariya Prathama - [Lihat Tanda Tangan Digital](../assets/tanda_tangan_team/tanda_tangan_satria.jpg) (Tanggal: 29 Oktober 2026)
```
```text
Dosen Coach: _______________________ (Tanggal: __________)  [ ] Approved
```
