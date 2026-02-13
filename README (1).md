
```markdown
# 📋 Sistem Absensi Digital Siswa 12 RPL

![Version](https://img.shields.io/badge/version-2.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-active-success)

Sistem absensi modern berbasis barcode scanner dengan fitur lengkap untuk kelas 12 RPL. Dibangun menggunakan HTML5, CSS3, dan JavaScript dengan database IndexedDB untuk penyimpanan lokal.

---

## 📑 Daftar Isi

- [Fitur Utama](#-fitur-utama)
- [Teknologi](#-teknologi)
- [Instalasi](#-instalasi)
- [Cara Penggunaan](#-cara-penggunaan)
  - [Menu Absensi](#1-menu-absensi)
  - [Menu Generator Barcode](#2-menu-generator-barcode)
  - [Menu Guide](#3-menu-guide)
- [Status Kehadiran](#-status-kehadiran)
- [Export Excel](#-export-excel)
- [Database Siswa](#-database-siswa)
- [Troubleshooting](#-troubleshooting)
- [Pengembang](#-pengembang)

---

## ✨ Fitur Utama

| Fitur | Deskripsi |
|-------|-----------|
| 📷 **Barcode Scanner** | Scan barcode real-time menggunakan kamera device |
| ⌨️ **Input Manual** | Input barcode manual dengan validasi otomatis |
| 🎨 **4 Status Absensi** | Hadir, Bolos, Izin, dan Sakit dengan warna berbeda |
| 📊 **Export Excel** | Export data dengan format terstruktir (Izin/Sakit dipisah di bawah) |
| 🏷️ **Generator Barcode** | Buat dan download barcode untuk setiap siswa |
| 📱 **Responsive Design** | Tampilan optimal di desktop, tablet, dan mobile |
| 💾 **IndexedDB** | Penyimpanan lokal yang persisten dan cepat |
| 🔍 **Guide/Directory** | Daftar lengkap siswa dengan fitur pencarian dan copy kode |

---

## 🛠️ Teknologi

- **Frontend**: HTML5, CSS3 (CSS Variables, Flexbox, Grid), JavaScript (ES6+)
- **Library**:
  - [html5-qrcode](https://github.com/mebjas/html5-qrcode) - Barcode/QR Scanner
  - [SheetJS/xlsx](https://github.com/SheetJS/sheetjs) - Export Excel
  - [JsBarcode](https://github.com/lindell/JsBarcode) - Generator Barcode
  - [Font Awesome](https://fontawesome.com/) - Icon
- **Database**: IndexedDB (Browser Native)
- **Storage**: LocalStorage (untuk data berita jika ada)

---

## 📥 Instalasi

### Prasyarat
- Browser modern (Chrome, Firefox, Edge, Safari) dengan kamera access
- Koneksi internet (untuk load CDN library)
- Web server (opsional, untuk development)

### Langkah Instalasi

1. **Download File**
   ```bash
   git clone https://github.com/username/absensi-12rpl.git
   # atau download ZIP manual

   ```

2. Struktur Folder
   
```
   absensi-12rpl/
   ├── index.html          # File utama
   ├── README.md           # File ini
   └── assets/             # (Opsional) folder tambahan
   ```

3. Menjalankan
   
   Opsi A: Direct Open
   - Buka file `index.html` langsung di browser
   - Catatan: Fitur kamera mungkin terbatas karena security policy

   Opsi B: Local Server (Rekomendasi)
   
```bash
   # Menggunakan Python
   python -m http.server 8000
   
   # Menggunakan Node.js (http-server)
   npx http-server -p 8000
   
   # Menggunakan PHP
   php -S localhost:8000
   ```

   - Buka browser: `http://localhost:8000`

4. Izinkan Kamera
   - Klik "Mulai" pada Scanner Barcode
   - Izinkan akses kamera saat browser meminta
   - Pilih kamera belakang (rear camera) untuk mobile

---

📖 Cara Penggunaan

1. Menu Absensi

A. Scan Barcode
1. Klik tombol "Mulai" pada section Scanner Barcode
2. Arahkan kamera ke barcode siswa
3. Sistem otomatis mendeteksi dan menyimpan data
4. Notifikasi toast muncul jika berhasil

B. Input Manual
1. Masukkan nomor barcode di kolom input (contoh: `RPL1009`)
2. Tekan Enter atau klik tombol Check
3. Jika siswa terdaftar, otomatis tersimpan dengan status Hadir

C. Tambah Status Manual (Izin/Sakit/Bolos)
1. Klik salah satu tombol quick add:
   - 🟢 Hadir - Status hadir normal
   - 🔴 Bolos - Status tidak hadir tanpa keterangan
   - 🟣 Izin - Status izin dengan keterangan
   - 🟠 Sakit - Status sakit dengan keterangan
2. Isi form yang muncul:
   - Barcode: Nomor unik siswa (contoh: RPL1009)
   - Nama: Otomatis terisi jika siswa terdaftar
   - Kelas: XII/XI/X
   - Jurusan: RPL (default)
3. Klik Simpan

D. Mengubah Status
1. Klik ikon 🔄 (exchange) pada kolom Aksi di tabel
2. Pilih status baru dari modal yang muncul:
   - Hadir → Bolos/Izin/Sakit
   - Bolos → Hadir/Izin/Sakit
   - Izin → Hadir/Bolos/Sakit
   - Sakit → Hadir/Bolos/Izin
3. Klik Simpan Perubahan

E. Menghapus Data
1. Klik ikon 🗑️ (trash) pada kolom Aksi
2. Konfirmasi penghapusan pada dialog
3. Data akan terhapus permanen

---

2. Menu Generator Barcode

A. Generate Single Barcode
1. Pindah ke tab "Generator Barcode"
2. Isi form:
   - Nomor Barcode: ID unik (contoh: RPL1009)
   - Nama Siswa: Nama lengkap
   - Kelas: Pilih XII/XI/X
   - Jurusan: Default RPL
   - Format: CODE128 (rekomendasi), CODE39, EAN13, UPC
3. Klik Generate Barcode
4. Preview akan muncul di sebelah kanan

B. Download Barcode
- Single: Klik tombol Download pada card preview
- Dari List: Klik ikon ⬇️ pada item di daftar generated
- Semua: Klik Download All (akan download satu per satu)

C. Print Barcode
1. Generate barcode
2. Klik tombol Print
3. Atur ukuran kertas di dialog print
4. Klik Print

D. Generate Massal
1. Klik "Generate Semua Siswa"
2. Sistem akan generate barcode untuk seluruh siswa di database
3. Download satu per satu atau semua sekaligus

---

3. Menu Guide

A. Melihat Daftar Siswa
1. Klik tombol "Guide" di navigasi atas
2. Pilih tab XII RPL 1 atau XII RPL 2
3. Scroll untuk melihat seluruh daftar

B. Mencari Siswa
1. Ketik nama atau kode barcode di kolom Search
2. Hasil filter otomatis muncul
3. Klik ❌ untuk reset pencarian

C. Copy Kode Barcode
1. Cari siswa yang diinginkan
2. Klik ikon 📋 (copy) di sebelah kanan nama
3. Kode tersimpan di clipboard, siap di-paste

---

🏷️ Status Kehadiran

Status	Warna	Icon	Keterangan	Waktu Hadir	
Hadir	🟢 Hijau	✓ Check	Siswa hadir tepat waktu	Tercatat	
Bolos	🔴 Merah	✗ Slash	Tidak hadir tanpa keterangan	Tercatat (awal), waktu bolos tercatat	
Izin	🟣 Ungu	✉️ Envelope	Tidak hadir dengan izin	Dikosongkan	
Sakit	🟠 Oranye	🏥 Medical	Tidak hadir karena sakit	Dikosongkan	

Visual pada Tabel
- Hadir: Baris putih normal
- Bolos: Baris merah muda + teks dicoret
- Izin: Baris ungu muda
- Sakit: Baris oranye muda

---

📊 Export Excel

Format File
- Nama File: `Absensi_12RPL_YYYY-MM-DD.xlsx`
- Sheet: "Absensi"

Struktur Data Excel

Bagian 1: Hadir & Bolos (Atas)

No	Nama_Siswa	Kelas	Jurusan	Tanggal	Waktu_Hadir	Status	Waktu_Bolos	Barcode	
1	Nama Siswa	XII	RPL	2024-01-15	07:30:00	HADIR	-	RPL1009	
2	Nama Siswa	XII	RPL	2024-01-15	07:35:00	BOL	09:00:00	RPL2013	

Bagian 2: Izin & Sakit (Bawah - Longkap 1 Field)

No	Nama_Siswa	Kelas	Jurusan	Tanggal	Waktu_Hadir	Status	Waktu_Bolos	Barcode	
3	Nama Siswa	XII	RPL	2024-01-15	(kosong)	IZIN	-	RPL1001	
4	Nama Siswa	XII	RPL	2024-01-15	(kosong)	SAKIT	-	RPL2001	

> Catatan: Kolom Waktu_Hadir dikosongkan untuk status Izin dan Sakit sesuai permintaan format.

Cara Export
1. Pastikan ada data absensi hari ini
2. Klik tombol "Export Excel" di pojok kanan atas tabel
3. File otomatis terdownload
4. Buka dengan Microsoft Excel, Google Sheets, atau LibreOffice Calc

---

👥 Database Siswa

XII RPL 1 (Kode: RPL1001 - RPL1017)

Kode	Nama	
RPL1001	Ade Pajriah	
RPL1002	Aisah	
RPL1003	Anggun Mega Aini	
RPL1004	Artika Sari Devi	
RPL1005	Atikah	
RPL1006	Azizah Kamizah	
RPL1007	Indri Nuriska	
RPL1008	Kaila Pratiwi	
RPL1009	Kania Putri Dewi	
RPL1010	Nopi Yanti	
RPL1011	Nurul Sa'adah	
RPL1012	Ovi Nurmaniyah	
RPL1013	Putri Damayanti	
RPL1014	Rani Anggraeni	
RPL1015	Selli Repina	
RPL1016	Siti Aminah	
RPL1017	Syafa Aqilah	

XII RPL 2 (Kode: RPL2001 - RPL2026)

Kode	Nama	
RPL2001	Ade Amelia Rizkiyah	
RPL2002	Badrussalam	
RPL2003	Chelsi Kirani	
...	...	
RPL2013	Padli Nurramadhan	
...	...	
RPL2026	Permana Kusuma	

> Total: 43 siswa terdaftar dalam sistem.

---

🔧 Troubleshooting

❌ Kamera Tidak Bekerja

Masalah: Kamera tidak muncul atau error saat start scanner

Solusi:
1. Pastikan izin kamera diberikan pada browser
2. Gunakan HTTPS atau localhost (bukan file://)
3. Coba browser lain (Chrome rekomendasi)
4. Refresh halaman (F5)
5. Cek apakah kamera sedang digunakan aplikasi lain

❌ Barcode Tidak Terdeteksi

Masalah: Scanner aktif tapi tidak membaca barcode

Solusi:
1. Pastikan pencahayaan cukup terang
2. Jarak optimal: 10-20 cm dari kamera
3. Pastikan barcode tidak blur/berbayang
4. Coba input manual untuk test
5. Gunakan barcode dengan format CODE128

❌ Data Tidak Tersimpan

Masalah: Setelah scan, data tidak muncul di tabel

Solusi:
1. Cek console browser (F12 → Console) untuk error
2. Pastikan IndexedDB tidak disabled
3. Coba hard refresh: `Ctrl + Shift + R`
4. Clear browser cache dan coba lagi

❌ Export Excel Gagal

Masalah: Tombol export tidak berfungsi

Solusi:
1. Pastikan ada data absensi hari ini
2. Cek popup blocker (matikan untuk site ini)
3. Gunakan browser terbaru
4. Coba download ulang setelah beberapa detik

❌ Tampilan Rusak di Mobile

Masalah: Layout tidak rapi di layar kecil

Solusi:
1. Pastikan viewport meta tag aktif
2. Refresh halaman
3. Gunakan mode landscape untuk tabel lebar
4. Update browser ke versi terbaru

---

👨‍💻 Pengembang

Dibuat oleh: Padli Nurramadhan

Profil:
- 🎓 Siswa SMKS Saintek Nurul Muslimin Karawang
- 💻 Jurusan: Rekayasa Perangkat Lunak (RPL)
- 🏫 Kelas: XII RPL 2
- 📱 Kontak: [WhatsApp](https://wa.me/6282249665662)

Sosial Media:
- Instagram: [@dlyy_suka_python](https://instagram.com/dlyy_suka_python)
- Facebook: [Dlyy.fine](https://www.facebook.com/Dlyy.fine)
- GitHub: [padlinurramadan-ui](https://github.com/padlinurramadan-ui)

---

📝 Changelog

v2.0 (2026-02-10)
- ✨ Tambah fitur status Izin dan Sakit
- ✨ Export Excel dengan format terpisah (Izin/Sakit di bawah, longkap 1 field)
- ✨ Modal ubah status dengan visual yang jelas
- ✨ Quick add buttons untuk 4 status
- 🔧 Perbaikan sorting data (Hadir/Bolos di atas, Izin/Sakit di bawah)
- 🎨 Update UI dengan warna status baru

v1.0 (2026-02-08)
- 🚀 Rilis awal
- ✨ Fitur scan barcode dan input manual
- ✨ Status Hadir dan Bolos
- ✨ Generator barcode
- ✨ Export Excel basic

---

📄 Lisensi

Proyek ini dilisensikan di bawah [MIT License](LICENSE).

Hak Cipta © 2026 Padli Nurramadhan

Dibebaskan untuk:
- ✅ Penggunaan pribadi
- ✅ Penggunaan edukasional
- ✅ Modifikasi dan distribusi
- ✅ Kontribusi kode

Dengan ketentuan:
- 📝 Cantumkan kredit pengembang asli
- 📝 Sertakan lisensi MIT dalam distribusi

---

🤝 Kontribusi

Kontribusi sangat diterima! Cara berkontribusi:

1. Fork repository ini
2. Buat branch fitur (`git checkout -b fitur-anda`)
3. Commit perubahan (`git commit -m 'Tambah fitur X'`)
4. Push ke branch (`git push origin fitur-anda`)
5. Buat Pull Request

---

📞 Dukungan

Jika mengalami masalah atau memiliki saran:

1. Buat Issue di GitHub repository
2. Hubungi langsung via WhatsApp: [+62 822-4966-5662](https://wa.me/6282249665662)
3. Email: [padlinurramadan@gmail.com](mailto:padlinurrmadan@gmail.com)
