# E-Kwitansi Bendahara Medexordia

Aplikasi web sederhana untuk membuat bukti penerimaan pembayaran secara digital bagi Bendahara Angkatan 1 **Medexordia, Fakultas Kedokteran UIN Walisongo Semarang**. Kwitansi dapat disesuaikan, dipratinjau secara langsung, lalu diekspor menjadi gambar PNG atau dokumen PDF.

## Ringkasan

E-Kwitansi membantu bendahara menyiapkan bukti pembayaran untuk iuran kas, pembayaran kegiatan, maupun keperluan lain. Pengguna mengisi detail transaksi melalui formulir, sedangkan tampilan kwitansi diperbarui secara real-time.

Aplikasi ini merupakan **generator dokumen berbasis frontend**, bukan aplikasi akuntansi, sistem pencatatan kas, atau layanan verifikasi pembayaran.

## Fitur

### 1. Identitas pembayar
- Pilihan cepat dari daftar 50 mahasiswa Angkatan 1 Medexordia.
- Pencarian nama dan NIM melalui daftar saran (*autocomplete*).
- Nama dan NIM saling disinkronkan ketika cocok dengan data yang tersedia.
- Nama dan NIM tetap dapat dimasukkan secara manual.

### 2. Detail kwitansi
- Nomor kwitansi yang dapat diedit.
- Tombol **+1 Urutan** untuk menaikkan nomor secara manual.
- Tanggal transaksi.
- Penyesuaian bulan Romawi dan tahun pada nomor kwitansi mengikuti tanggal yang dipilih.
- Nominal pembayaran dalam Rupiah.
- Tombol tambah nominal cepat yang menambahkan Rp10.000, Rp25.000, Rp50.000, atau Rp100.000 ke nominal saat ini.

### 3. Informasi pembayaran
- Metode pembayaran: Cash, QRIS, dan Transfer Bank.
- Jenis pembayaran: iuran kas, pembayaran acara, atau keterangan khusus.
- Konversi nominal menjadi teks terbilang dalam bahasa Indonesia secara otomatis.

### 4. Kustomisasi dokumen
- Pengaturan kota penerbit dan nama bendahara.
- Penggantian logo menggunakan berkas gambar milik pengguna.
- Opsi menampilkan atau menyembunyikan stempel digital.
- Pratinjau kwitansi yang mengikuti perubahan formulir secara langsung.

### 5. Ekspor dan konfirmasi
- Ekspor kwitansi sebagai gambar PNG.
- Ekspor kwitansi sebagai PDF.
- Menyalin ringkasan pembayaran yang siap ditempel ke percakapan WhatsApp.
- Notifikasi untuk memberi tahu pengguna ketika proses berhasil atau gagal.

## Teknologi

| Teknologi / Pustaka | Penggunaan |
|---|---|
| HTML5 | Struktur halaman dan formulir |
| Tailwind CSS (CDN) | Styling dan tata letak responsif |
| JavaScript | Logika formulir, sinkronisasi data, dan pratinjau |
| Lucide Icons | Ikon antarmuka |
| Google Fonts | Tipografi Inter, Poppins, Playfair Display, dan JetBrains Mono |
| html2canvas | Mengubah area kwitansi menjadi gambar |
| jsPDF | Membuat berkas PDF dari hasil render kwitansi |

Aplikasi tidak memerlukan framework JavaScript, proses kompilasi, atau instalasi paket melalui npm.

## Menjalankan secara lokal

1. Clone repository:

   ```bash
   git clone https://github.com/kazadarojat/kwitansikas.git
   cd kwitansikas
   ```

2. Jalankan server lokal sederhana, misalnya menggunakan Python:

   ```bash
   python -m http.server 8000
   ```

3. Buka alamat berikut pada browser:

   ```
   http://localhost:8000
   ```

Alternatifnya, buka `index.html` langsung melalui browser. Koneksi internet tetap diperlukan untuk memuat pustaka dan font yang diambil dari CDN.

## Cara menggunakan

1. Buka aplikasi dan pilih mahasiswa dari daftar, atau masukkan nama serta NIM secara manual.
2. Periksa nomor dan tanggal kwitansi. Gunakan **+1 Urutan** untuk menaikkan nomor apabila diperlukan.
3. Masukkan nominal pembayaran. Teks terbilang akan dibuat secara otomatis.
4. Pilih metode pembayaran dan jenis pembayaran, kemudian lengkapi keterangannya.
5. Sesuaikan kota penerbit, nama bendahara, logo, dan tampilan stempel.
6. Periksa seluruh informasi pada bagian pratinjau.
7. Pilih **Salin WhatsApp**, **Ekspor PNG**, atau **Ekspor PDF** sesuai kebutuhan.

Pastikan nama, NIM, nominal, tanggal, nomor kwitansi, dan keterangan telah diperiksa sebelum dokumen dibagikan.

## Deployment dengan GitHub Pages

Repository ini menyediakan `index.html` pada direktori utama sehingga dapat digunakan sebagai entry point GitHub Pages.

1. Buka **Settings** pada repository GitHub.
2. Pilih menu **Pages**.
3. Pada bagian *Build and deployment*, pilih **Deploy from a branch**.
4. Pilih branch `main` dan folder `/(root)`.
5. Simpan pengaturan dan tunggu proses deployment selesai.
6. Buka URL yang ditampilkan pada halaman pengaturan GitHub Pages.

Setiap perubahan pada branch dan folder sumber yang dipilih akan diproses kembali oleh GitHub Pages.

## Struktur repository

```text
kwitansikas/
├── index.html
├── aplikasi_kwitansi_medoxordia_fk_uin_walisongo.html
└── README.md
```

- `index.html`: halaman utama aplikasi dan entry point GitHub Pages.
- `aplikasi_kwitansi_medoxordia_fk_uin_walisongo.html`: salinan halaman aplikasi dengan nama deskriptif.
- `README.md`: dokumentasi repository.

Kedua berkas HTML saat ini memiliki isi yang sama. Jika kode aplikasi diperbarui, pastikan keduanya tetap sinkron atau tetapkan satu berkas sebagai sumber utama.

## Arsitektur, data, dan privasi

- Seluruh logika pembuatan kwitansi berjalan di browser pengguna.
- Saat ini tidak terdapat backend, database, autentikasi, maupun integrasi API pembayaran.
- Data formulir dan logo kustom tidak disimpan ke server atau penyimpanan permanen oleh aplikasi. Muat ulang halaman akan mengembalikan formulir ke nilai awal.
- Daftar nama dan NIM mahasiswa ditulis langsung di dalam kode JavaScript. Karena repository ini bersifat publik, data tersebut dapat dilihat melalui source code maupun oleh pengunjung yang mengakses aplikasi. Pastikan publikasi data telah memperoleh persetujuan yang sesuai. Untuk penggunaan yang lebih aman, pertimbangkan menghapus data identitas dari source code publik atau memindahkannya ke layanan backend dengan kontrol akses.
- Tailwind CSS, ikon, font, html2canvas, dan jsPDF dimuat melalui layanan CDN pihak ketiga. Browser memerlukan koneksi internet untuk mengambil aset tersebut.

## Batasan dan catatan penggunaan

**Stempel digital bukan verifikasi pembayaran.** Tulisan “LUNAS / VERIFIED” merupakan elemen visual pada template yang dapat ditampilkan atau disembunyikan. Aplikasi tidak memeriksa mutasi rekening, status QRIS, maupun konfirmasi dari penyedia pembayaran. Bendahara harus memverifikasi pembayaran melalui kanal resmi sebelum menerbitkan kwitansi sebagai tanda pembayaran yang telah diterima.

**Tanggal awal perlu diperiksa pada pagi hari.** Nilai tanggal awal saat ini dibentuk menggunakan tanggal UTC. Pada zona waktu Indonesia (UTC+7 hingga UTC+9), aplikasi berpotensi menampilkan tanggal satu hari sebelumnya pada jam-jam awal sebelum pergantian tanggal UTC. Periksa tanggal pada formulir sebelum menerbitkan kwitansi.

**Nomor kwitansi tidak dikelola secara terpusat.** Tombol kenaikan nomor hanya mengubah nilai pada formulir saat itu. Tidak ada penyimpanan nomor terakhir, penguncian nomor, maupun pemeriksaan duplikasi antarperangkat atau pengguna.

**Tidak ada riwayat transaksi.** Aplikasi tidak menyimpan daftar pembayaran, membuat rekap kas, menghitung saldo, atau menyinkronkan data antarperangkat. Simpan berkas hasil ekspor secara terpisah sebagai arsip.

## Lisensi

Repository ini belum menyertakan berkas lisensi. Ketentuan penggunaan ulang dan distribusi kode belum ditetapkan secara eksplisit.
