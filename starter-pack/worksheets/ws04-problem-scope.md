# **WS04: Problem Identification & Scope**

**Mata Kuliah**: Konsep Sistem Informasi (KSI)  
**Kerangka Kerja**: Project-Based Learning (PBL) Level 1  
**Fase Learning Spine**: **Fase 2 - Frame (Problem Discovery & Scope)**  
**Minggu / Alokasi Waktu**: Minggu 2 / 14 Jam Belajar  
**Sub-CPMK / SFIA**: S-01.1 (Introduce - Problem Framing) | SFIA BUSA L1 (_Business Analysis_), IRMG L1  
**Penanggung Jawab Fase**: **Phase Lead 2 (Frame - Mahasiswa B)**  
**Keterkaitan Deliverable**: Sumber Utama Penyusunan **Deliverable D1 (Problem Brief - TPL-01)**

## **1\. Identifikasi Tim & Objek Proyek**

| **Elemen Informasi**          | **Rincian Identitas Kelompok & Mitra**        |
| ----------------------------- | --------------------------------------------- |
| **Nama Kelompok / Kelas**     | [ Syncore Team / Kelas A ]                    |
| **Phase Lead 2 (Frame - M2)** | [ Muhammad Rasikh Zakki Aufa - 2600016028 ]   |
| **Nama UMKM Mitra Lapangan**  | [ Temu Tempo Kopi ]                           |
| **Pemilik / Kontak Mitra**    | [ Mas Joy / +62882008806986 ]                 |

## **2\. Matriks Problem Framing & Analisis Akar Masalah (Root Cause Analysis)**

Gunakan temuan kuantitatif dari WS03 untuk memisahkan antara **Gejala Permukaan (_Symptoms_)** dan **Akar Masalah Utama (_Root Cause_)** operasional bisnis mitra:

| **No** | **Kategori Observasi**      | **Gejala Permukaan (_Symptoms_)**                                                                                                                                                                                                                                                                                                                                                                                                                              | **Akar Masalah Operasional (_Root Cause_)**                                                                                                                                                                                                                                                                                                                                                                                                      | **Bukti Kuantitatif (_Baseline Data_)**                                                                                                                                                                                                                                                               |
| ------ | --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **1**  | **Proses Transaksi Kasir**  | Saat jam ramai (*peak hour*), pelanggan sering datang berombongan sehingga antrean menumpuk dan penyajian pesanan makanan agak terlambat. | Keterlambatan penyajian terjadi karena Mas Joy bekerja sendirian melayani kasir sekaligus meracik pesanan dan memasak di bar. Kondisi di kasir juga rawan terdistraksi saat ramai, ditambah aplikasi kasir di telepon pintar (smartphone) tidak memiliki fitur ubah (edit) transaksi, sehingga apabila terjadi kesalahan klik, data harus dihapus dan diinput ulang dari awal. | Waktu saji minuman di bawah 5 menit, sedangkan makanan berat membutuhkan waktu 10-15 menit pada saat jam ramai (12.00-15.00 WIB dan setelah 20.00 WIB), dengan aplikasi kasir yang tidak punya fitur edit transaksi. |
| **2**  | **Pengelolaan Stok Barang** | Pembelian bahan baku terutama biji kopi belum terjadwal rutin karena baru dibeli saat stok fisik menipis, serta harus diambil sendiri ke pemasok. | Persediaan bahan baku belum menggunakan pencatatan digital khusus (*stock opname*), hanya mengandalkan cek fisik malam hari menjelang tutup kedai lalu dicatat di aplikasi catatan ponsel. Mas Joy mengurus seluruh operasional kedai sendirian sehingga tidak sempat merekap stok secara berkala setiap hari. | Pencatatan stok masih manual lewat catatan di HP setelah cek fisik malam hari. Biji kopi dibeli putus rata-rata 2 kg per minggu langsung ke daerah Bumijo. |
| **3**  | **Rekapitulasi Keuangan**   | Rekapitulasi penjualan tidak dilakukan setiap malam karena fisik sudah lelah setelah 17 jam operasional kedai, melainkan terkumpul dan baru dikerjakan setiap hari Minggu sehingga menyita waktu libur pemilik. Saat kedai ramai, ada transaksi yang terlewat tidak kerekap, serta uang kas kedai sering terpakai untuk kebutuhan pribadi Mas Joy tanpa pencatatan tersendiri. | Format Microsoft Excel yang digunakan saat ini hanya berupa tabel angka mentah tanpa rumus otomatis. Mas Joy harus memindahkan data transaksi kasir dan menghitung margin secara manual sehingga rentan terdapat transaksi yang terlewat atau tidak tercatat. Ditambah lagi, belum ada pencatatan penarikan dana pemilik (prive) yang terpisah, sehingga uang modal kedai bercampur dengan pengeluaran pribadi yang menjadi kendala operasional paling dirasakan pemilik saat ini. | Waktu libur hari Minggu tersita sekitar 1 jam untuk memindahkan data kasir dan menghitung margin manual di Excel. Berdasarkan hasil wawancara, ada 1-2 transaksi per minggu yang tidak kerekap atau salah rekap saat kedai ramai, serta kas kedai masih sering terpakai untuk keperluan pribadi tanpa pos pencatatan prive tersendiri. |
| **4**  | **Analisis & Evaluasi Penjualan Menu & Bisnis** | Penjualan minuman kopi mendominasi makanan berat dengan rasio rata-rata 3:2. Mas Joy belum memiliki dasbor grafik visual untuk memantau performa bisnis (pemasukan vs pengeluaran, tren penjualan, menu terlaris vs terendah) sehingga sulit menentukan strategi promo dan paket penjualan. | Format Excel Mas Joy hanya berupa baris angka mentah tanpa rumus maupun dasbor grafik otomatis. Waktu libur hari Minggu sudah habis untuk rekapitulasi angka manual, sehingga Mas Joy tidak sempat lagi membuat grafik tren penjualan atau perbandingan menu. Akibatnya, Mas Joy kesulitan membaca produk mana yang paling laris (seperti Nasi Goreng) maupun produk yang penjualannya stagnan/lambat untuk pembuatan promo bundling. | Format rekapitulasi di Excel murni tabel angka mentah tanpa grafik visual. Penjualan harian berada di rasio rata-rata 3 kopi berbanding 2 makanan berat, dan alokasi waktu pemilik untuk evaluasi grafik bisnis adalah 0 jam per minggu. |

## **3\. Perumusan Problem Statement Kontekstual**

Berdasarkan analisis di atas, rumuskan **Problem Statement** utama dalam 1-2 paragraf terstruktur.  
_Petunjuk_: Hindari mendefinisikan masalah sebagai _"Mitra belum memiliki aplikasi Python/komputer"_. Definisikan dari hambatan bisnis nyata mitra!

**Rumusan Problem Statement Kelompok**:  
_"Operasional dan administrasi di **Temu Tempo Kopi** saat ini menemui kendala karena seluruh pekerjaan dijalankan secara mandiri oleh Mas Joy sebagai pemilik tunggal (solo operator) tanpa alat bantu pencatatan yang terintegrasi otomatis. Di bagian pelayanan, waktu penyajian makanan berat memakan waktu **10-15 menit** saat jam ramai (12.00-15.00 WIB dan setelah 20.00 WIB), dengan aplikasi kasir telepon pintar yang tidak memiliki fitur ubah (edit) transaksi jika terjadi salah input. Di bagian stok, pengadaan biji kopi masih manual (beli putus 2 kg/minggu ke Bumijo) berdasarkan cek fisik malam hari tanpa pencatatan digital._

_Di bagian keuangan dan evaluasi bisnis, ketiadaan sistem rekapitulasi otomatis membuat Mas Joy harus memindahkan data transaksi kasir dan menghitung margin secara manual di Microsoft Excel setiap hari Minggu. Proses rutin ini menyita **waktu libur operasional sekitar 1 jam per minggu**, ditambah risiko 1-2 transaksi terlewat atau tidak terekap/tidak tercatat saat kondisi kedai ramai. Masalah ini diperberat oleh belum adanya pos pencatatan penarikan dana pribadi pemilik (prive), sehingga uang kas kedai sering tercampur untuk keperluan pribadi yang menjadi kendala operasional terbesar mitra. Selain itu, lembar kerja Excel pemilik belum memiliki dasbor grafik otomatis untuk memantau arus kas masuk vs keluar, tren penjualan mingguan, menu terlaris/terendah, dan rasio kopi vs makanan (**3 : 2**). Akibatnya, waktu istirahat pemilik tersita untuk rekap manual dan evaluasi perkembangan bisnis kedai menjadi terhambat."_

## **4\. Menetapkan Batasan Sistem (System Boundary / Scope Alignment)**

Untuk mencegah terjadinya pembengkakan fitur (_Scope Creep_) yang membahayakan penyelesaian proyek dalam 1 semester, tentukan secara tegas apa yang **Masuk Cakupan (_In-Scope_)** dan apa yang **Di Luar Cakupan (_Out-of-Scope_)**:

```text
+-----------------------------------------------------------------------------+
|                      SYSTEM BOUNDARY (BATASAN SISTEM)                       |
+-----------------------------------------------------------------------------+
| [ IN-SCOPE: Fitur yang Akan Dibangun ]                                      |
| 1. Otomasi dan penyederhanaan rekapitulasi data transaksi penjualan         |
|    mingguan (< 5 menit).                                                    |
| 2. Modul pencatatan transaksi penarikan pemilik (prive) dari kas usaha.     |
| 3. Dasbor visualisasi evaluasi bisnis otomatis (arus kas in/out, tren       |
|    penjualan, ranking menu terlaris/terendah, dan rasio kopi vs makanan).   |
+-----------------------------------------------------------------------------+
| [ OUT-OF-SCOPE: Di Luar Cakupan Proyek ]                                    |
| 1. Pembuatan atau perombakan aplikasi kasir utama (POS).                    |
| 2. Otomasi pemesanan stok ke supplier luar (auto-order biji kopi).          |
| 3. Integrasi payment gateway / QRIS otomatis langsung ke perbankan.         |
+-----------------------------------------------------------------------------+
```

### **Tabel Penegasan Cakupan Proyek (*Scope Alignment Table*)**

| **No** | **Modul / Fitur Sistem**                                                          | **Status Cakupan (_In-Scope / Out-of-Scope_)** | **Alasan Pertimbangan Kelayakan (O'Brien)**                                                                                                                                                                                                    |
| ------ | --------------------------------------------------------------------------------- | ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **1**  | Otomasi Rekapitulasi Data Transaksi Penjualan                          | **IN-SCOPE**                                   | Membantu pemilik mengolah file ekspor kasir secara otomatis sehingga tidak perlu menghitung manual selama 1 jam di hari libur Minggu.                                                                     |
| **2**  | Modul Pencatatan Transaksi Penarikan Pemilik (Prive)                  | **IN-SCOPE**                                   | Menyediakan pos pencatatan khusus saat pemilik mengambil uang kas kedai untuk kebutuhan pribadi, sehingga arus kas operasional usaha tetap jelas dan tidak bocor.                                               |
| **3**  | Dasbor Visualisasi Evaluasi Bisnis Otomatis                          | **IN-SCOPE**                                   | Menyajikan grafik otomatis saat data rekap diimpor: perbandingan pemasukan vs pengeluaran, tren penjualan, ranking menu terlaris/terendah, dan rasio menu kopi vs makanan (3:2) untuk evaluasi bisnis.      |
| **4**  | Pembuatan Aplikasi Kasir (POS) Baru                                   | **OUT-OF-SCOPE**                               | Mas Joy sudah sangat terbiasa dengan aplikasi kasir di smartphone saat ini. Mengganti aplikasi kasir berisiko mengganggu operasional harian 17 jam kedai.                                                      |
| **5**  | Integrasi Payment Gateway & Otomasi Pemesanan Supplier                | **OUT-OF-SCOPE**                               | Pembelian biji kopi dilakukan mandiri ke Bumijo saat stok habis. Integrasi perbankan/QRIS otomatis juga butuh izin dan biaya pihak ketiga yang terlalu rumit untuk proyek semester 1.                          |

## **5\. Target Metrik Keberhasilan Solusi (To-Be Targets)**

Tentukan target kuantitatif perbaikan yang ingin dicapai melalui solusi sistem informasi To-Be:

| **Indikator Kinerja**                                             | **Kondisi As-Is (Baseline)**                                                                                                                                                                                         | **Target To-Be (Expected)**                                                                           | **Estimasi Persentase Peningkatan**                                                                                                                                                                |
| ----------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Durasi Rekapitulasi Penjualan**                      | **± 60 menit / minggu** _(File kasir dipindahkan dan dihitung marginnya secara manual di Excel; menyita waktu libur hari Minggu)_                                                                                                                 | **< 5 menit / minggu** _(Data transaksi diolah dan dihitung otomatis oleh formula sistem)_ | **Penghematan Waktu > 90%** _(Mengembalikan waktu istirahat pemilik di hari Minggu karena rekap selesai dalam hitungan menit)._                        |
| **Kejelasan Kas & Pencatatan Prive Pemilik**     | **Belum ada pos penarikan prive** _(Uang kas kedai sering terpakai untuk keperluan pribadi pemilik tanpa pencatatan khusus)_                                                                                                 | **Pencatatan Prive Terstruktur** _(Penarikan pribadi tercatat rapi dan terpisah dari kas operasional usaha)_         | Arus kas usaha menjadi jelas dan terpantau tanpa tercampur pengeluaran pribadi pemilik.                                                                                                               |
| **Kemudahan Evaluasi Tren Penjualan & Bisnis** | **Manual & Belum Ada Grafik di Excel** _(Format Excel pemilik saat ini murni baris angka mentah tanpa grafik visual untuk melihat arus kas, tren omzet, maupun ranking menu)_ | **Dasbor Grafik Otomatis** _(Grafik pemasukan vs pengeluaran, tren penjualan, ranking menu terlaris/terendah, dan rasio kopi vs makanan langsung muncul otomatis)_ | Pemilik bisa langsung membaca performa kedai secara visual tanpa perlu mengolah grafik manual tiap minggu, sehingga evaluasi bisnis jadi lebih cepat. |
| **Risiko Salah Hitung Keuangan (Human Error)** | **Cukup tinggi** _(Rawan terjadi kesalahan saat menjumlahkan angka nota transaksi secara manual berulang-ulang)_                                                                                                   | **Perhitungan Otomatis** _(Kalkulasi total omzet, biaya modal, dan margin dikerjakan otomatis oleh sistem)_                    | Penurunan risiko salah hitung margin dan salah rekap manual.                                                                                                                                        |

## **6\. Refleksi & Lembar Pengesahan Phase Lead**

### **A. Pertanyaan Refleksi Tim**

1. _Bagaimana tim memastikan bahwa batasan proyek yang ditetapkan realistis untuk diselesaikan dalam 16 minggu?_
   - **Jawab**: Tim kami membatasi ruang lingkup pada kendala yang paling mendesak bagi Mas Joy, yaitu otomatisasi rekapitulasi penjualan mingguan, modul pencatatan penarikan prive, dan dasbor visualisasi evaluasi bisnis. Fitur yang terlalu rumit -- seperti membuat aplikasi kasir dari awal, integrasi payment gateway, atau pemesanan otomatis ke supplier -- secara tegas kami keluarkan dari cakupan proyek agar tidak terjadi pembengkakan fitur (*scope creep*). Dengan memfokuskan solusi pada pengolahan data transaksi pasca-kasir menggunakan spreadsheet atau program sederhana, alokasi waktu 16 minggu sangat realistis untuk diselesaikan hingga tahap uji coba bersama mitra.
2. _Apakah pemilik usaha mitra telah menyetujui batasan sistem yang diusulkan oleh kelompok?_
   - **Jawab**: Ya, Mas Joy sudah menyetujui batasan sistem ini saat sesi wawancara dan observasi. Beliau sangat setuju jika ada alat bantu yang bisa memangkas waktu rekapitulasi di hari libur Minggu dan mencatat penarikan dana pribadi (prive) secara rapi, tanpa harus mengganti aplikasi kasir di smartphone yang saat ini sudah nyaman beliau gunakan.

### **B. Tanda Tangan Pengesahan Phase Lead 2**

Disusun oleh Phase Lead 2 (Frame): Muhammad Rasikh Zakki Aufa - 2600016028

```
Tanggal Penyusunan: 14 Oktober 2026
Tanda Tangan Phase Lead 2: [Lihat Tanda Tangan Digital](../assets/tanda_tangan_team/tanda_tangan_zakki.jpg)
Diverifikasi oleh Dosen Pengampu / Coach:
Tanggal: [ Tanggal ] | Status Checkpoint: [ APPROVED / REVISION NEEDED ]
Catatan Dosen: __________________________________________________
```
