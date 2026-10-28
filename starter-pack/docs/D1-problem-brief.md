# D1 - Problem Brief

**Project**: Digital Problem Framing Mini Project - Temu Tempo Kopi
**Tim**: Satria Ariya Prathama, Ananta Rizqi Fadhlurrohman, Muhammad Rasikh Zakki Aufa, Muhammad Dhiyauddin Nur, Alfin Farrel Gennaro | **Tanggal**: 22-10-2026 | **Versi**: v1.0
**Template**: TPL-01

> **Petunjuk**: Hapus teks dalam `[...]` dan huruf miring setelah diisi.
> Worksheet terkait: WS03, WS04

---

## 1. Profil Organisasi / Unit Usaha

- **Nama unit usaha**: Temu Tempo Kopi
- **Jenis usaha / layanan**: Kedai Kopi & Ruang Interaksi Kreatif (Food & Beverage)
- **Lokasi**: Jl. Singoranu No.87, Kragilan, Sorosutan, Kec. Umbulharjo, Kota Yogyakarta, DIY 55162
- **Deskripsi singkat operasional**: Beroperasi setiap hari pukul 08.00-01.00 WIB (17 jam operasional harian). Dikelola mandiri oleh Mas Joy dengan segmen utama mahasiswa dan warga lokal. Melayani transaksi pemesanan luring di kedai serta daring melalui platform ShopeeFood.
- **Narahubung / pemilik**: Mas Joy, Pemilik & Pengelola Tunggal (+62882008806986)

## 2. Deskripsi Masalah Utama

- **Masalah utama**: Terjadinya pemborosan waktu istirahat pemilik di hari libur Minggu akibat proses rekapitulasi data penjualan manual di Microsoft Excel tanpa formula otomatis, diperparah pencatatan keuangan yang masih mencampur kas operasional usaha dengan pengeluaran pribadi sebagai prive serta tidak adanya visualisasi tren penjualan produk.
- **Pihak yang terdampak**: Pemilik usaha (Mas Joy) kehilangan waktu istirahat pada hari libur operasional, kesulitan memantau profit bersih aktual usaha dengan akurat, serta lambat dalam proses evaluasi.
- **Frekuensi / keparahan**: Terjadi rutin setiap hari Minggu saat kedai libur (menyita waktu ± 1 jam istirahat), serta terdapat risiko 1-2 transaksi yang tidak kerekap atau terlewat per minggu saat kondisi kedai ramai.

## 3. Batasan Sistem (Scope)

- **Diselesaikan dalam proyek ini**: Otomatisasi rekapitulasi data transaksi penjualan mingguan dari file csv kasir, Modul pemisahan pencatatan kas operasional bisnis dengan pengeluaran pribadi pemilik sebagai prive, Dasbor evaluasi bisnis otomatis (grafik pemasukan vs pengeluaran, tren penjualan mingguan, dll.) yang otomatis ter-update setelah data transaksi diimpor.
- **Tidak diselesaikan (dan alasan)**: Pembuatan aplikasi kasir (POS) baru: Proses pembuatan yang cukup rumit dan memakan waktu lama, Otomasi pemesanan stok ke supplier: Pasokan biji kopi dibeli putus secara mandiri ke Bumijo saat stok fisik menipis, Integrasi payment gateway / QRIS perbankan otomatis: Memerlukan biaya registrasi perbankan dan izin pihak ketiga yang terlalu rumit untuk proyek mini project semester 1.
- **Asumsi yang dipakai**: Data transaksi dari aplikasi kasir Pemilik dapat diekspor atau dipindahkan ke spreadsheet dalam format file CSV atau teks.

## 4. Data Kuantitatif Pendukung

| Indikator | Nilai/Baseline | Sumber Data | Tanggal |
|---|---|---|---|
| Durasi Rekapitulasi Mingguan | ± 60 menit (1 jam) setiap hari Minggu | Wawancara Pemilik (Mas Joy) | 21-10-2026 |
| Durasi Jam Kerja Harian | 17 jam/hari (08.00-01.00 WIB) | Wawancara Pemilik (Mas Joy) | 21-10-2026 |
| Frekuensi Transaksi Terlewat / Tidak Kerekap | 1-2 transaksi per minggu saat kedai ramai | Wawancara Pemilik (Mas Joy) | 21-10-2026 |

## 5. Pernyataan Kebutuhan Awal (ringkasan ke D2)

- Kebutuhan inti yang akan dijawab prototipe:
1. Modul input dan perhitungan rekapitulasi penjualan otomatis dari file csv kasir tanpa kalkulasi manual di Excel.
2. Modul pencatatan buku kas operasional kedai dengan pencatatan khusus penarikan dana pribadi pemilik (prive).
3. Dasbor grafik visual untuk memantau performa arus kas (masuk vs keluar), tren omzet, dan evaluasi.

## 6. Daftar Rujukan / Bukti

- Observasi Lapangan 1: Senin, 12 Oktober 2026 (Rekaman audio part 1 & part 2, transkrip wawancara, foto).
- Validasi Empiris Lanjutan: Rabu, 21 Oktober 2026 (Rekaman audio observasi 2, transkrip wawancara, foto).
- Diskusi WS dan data validasi: Rabu, 21 Oktober 2026 (foto).
- Aset Fisik: Tersimpan di folder starter-pack/assets/ dan Google Drive tim.

---

**Status**: ☑️ Draf → ⬜ Review Tim → ⬜ Validasi Pemilik → ⬜ Final (Gate 1)
