# E3 - AI Usage Disclosure & Verification Note

**Project**: Digital Problem Framing Mini Project - Temu Tempo Kopi  
**Tim**: Syncore Team | **Periode**: Minggu 1-16 | **Template**: TPL-07  
**Worksheet terkait**: WS15 (dan pendukung Gate 1 & 2: WS03-WS07, D1, D2)  

> **⚠️ CATATAN PENTING**: Isi dokumen ini **secara berkala**, jangan menunggu minggu 16! Anggap ini update mingguan. Dokumen ini adalah *living document*.

---

## 1. AI Usage Disclosure

| Artefak | Tool AI | Bagian yang Dibantu | Modifikasi yang Dilakukan |
|---|---|---|---|
| **D1** (didukung WS03 & WS04, serta tinjauan E4 & E5) | Google Gemini ([Riwayat Chat Sesi Gemini](https://drive.google.com/file/d/1T9Y57ohpgDMDvpHf_d8pXTtMdHuZs2N1/view?usp=sharing)) | 1. Memeriksa kesesuaian draf laporan tim dengan format template dosen dan bukti transkrip wawancara.<br>2. Mengecek kesinambungan masalah agar tidak ada data yang bertentangan antar-file.<br>3. Merapikan kalimat laporan agar lebih baku dan formal. | 1. Memberi batasan tegas ke AI agar hanya merapikan bahasa dan dilarang menambah data fiktif di luar hasil observasi.<br>2. Memeriksa ulang teks dari AI dan memastikan semua angka hasil wawancara (rekap 1 jam, rasio 3:2, dll.) tetap sesuai fakta lapangan. |
| **D2** (didukung WS05, WS06, & WS07) | Google Gemini ([Folder Bukti: Sesi Chat Perancangan & Ekspor Kasir](https://drive.google.com/drive/folders/1GWHJMwAJZlvyukXHwQyh4MM3DOQbYKFL?usp=drive_link)) | 1. Diskusi rumus keuangan: pemisahan Laba Kotor (memotong HPP), Laba Bersih, dan Sisa Kas Fisik agar pos Prive tidak mengacaukan laba usaha.<br>2. Mengecek alur logika perulangan (loop) dan kondisi selesai pada Flowchart Function 1, 2, dan 3.<br>3. Memberikan referensi struktur pseudocode dan contoh skrip Python sederhana untuk membuat grafik di spreadsheet. | 1. Tim aktif mengoreksi masukan AI (misalnya memastikan alur panah perulangan di flowchart sudah benar dan tidak terputus).<br>2. Menyesuaikan atribut data masukan dengan format file CSV asli dari tablet Aplikasir milik mitra.<br>3. Menyederhanakan rancangan logika agar tetap realistis dan sesuai kapasitas proyek semester 1. |
| **D3** | - | *Belum menggunakan AI (Fase Prototipe & Uji)* | - |
| **D4** | - | *Belum menggunakan AI (Fase Portofolio & Refleksi)* | - |
| **E1-E7** | - | *Belum menggunakan AI (Fase Pelaporan/Final)* | - |

---

## 2. Verification Note

| Artefak | Yang Dicek Ulang Manual | Cara Verifikasi |
|---|---|---|
| **D1** (didukung WS03 & WS04) | 1. Angka hasil observasi (waktu rekap 1 jam hari Minggu, rasio 3:2, waktu tunggu makanan, risiko transaksi terlewat).<br>2. Memastikan masalah pencatatan Prive, format Excel tanpa grafik, dan batasan sistem (tidak membuat POS baru) murni dari kebutuhan Mas Joy. | 1. Mencocokkan data laporan dengan 4 file rekaman audio dan transkrip wawancara di folder `assets/`.<br>2. Menanyakan langsung ke Mas Joy saat kunjungan ke kedai.<br>3. Meminta AI mengecek ulang teksnya sendiri di akhir sesi untuk menjamin tidak ada data baru (anti-halusinasi). |
| **D2** (didukung WS05, WS06, & WS07) | 1. Ketepatan rumus: Laba Bersih = Laba Kotor - Beban Operasional, dan Sisa Kas = Total Omzet - Beban - Prive.<br>2. Kesesuaian kolom CSV ekspor Aplikasir dengan input Function 1.<br>3. Hubungan alur data antar-flowchart (Function 1 ke 2, lalu ke 3) agar tidak ada variabel gantung. | 1. Melakukan penelusuran logika manual (desk check) langkah demi langkah pada diagram alir (flowchart).<br>2. Mempraktikkan langsung ekspor CSV di tablet kasir Temu Tempo Kopi. |
| **D3** | *[Akan diverifikasi saat fase build: logika sintaks, algoritma, dan eksekusi program]* | *[Uji coba running kode di mesin lokal dengan test case nyata]* |
| **D4** | *[Akan diverifikasi saat fase penutupan: kesesuaian portofolio, refleksi, dan bukti pendukung]* | *[Pemeriksaan manual seluruh berkas artefak dan rekam jejak kontribusi]* |

---

## 3. Pernyataan Kejujuran

Kami menyatakan daftar di atas lengkap dan jujur. Seluruh output AI telah dianalisis, dimodifikasi, dan diverifikasi secara manual oleh tim.

Tanda tangan seluruh anggota:  
- Satria Ariya Prathama: [Lihat Tanda Tangan Digital](../../assets/tanda_tangan_team/tanda_tangan_satria.jpg)  
- Ananta Rizqi Fadhlurrohman: [Lihat Tanda Tangan Digital](../../assets/tanda_tangan_team/tanda_tangan_ananta.jpg)  
- Muhammad Rasikh Zakki Aufa: [Lihat Tanda Tangan Digital](../../assets/tanda_tangan_team/tanda_tangan_zakki.jpg)  
- Muhammad Dhiyauddin Nur: [Lihat Tanda Tangan Digital](../../assets/tanda_tangan_team/tanda_tangan_yaud.jpg)  
- Alfin Farrel Gennaro: [Lihat Tanda Tangan Digital](../../assets/tanda_tangan_team/tanda_tangan_alfin.jpg)  

---

**Status**: ⬜ Mulai diisi (Minggu 1) → ☑️ Update berkala (Minggu 3-6 / Gate 1 & 2) → ⬜ Final (Demo Day)
