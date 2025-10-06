# Input — Sistem Input Data Nomor Customer

**Satu-liner:** Aplikasi web sederhana untuk memasukkan dan mencari nomor customer agar proses transaksi di konter Ruang Data Telemedia lebih cepat bagi frontliner.

## Deskripsi

Aplikasi ini dibuat khusus atas permintaan owner konter untuk mempermudah frontliner dalam memasukkan data nomor customer saat transaksi. Aplikasi berbasis file statis (HTML/CSS/asset) dengan antarmuka minimal yang memfokuskan pada input cepat, pencarian, dan penyalinan nomor customer ke sistem transaksi.

## Fitur utama

* Form input nomor customer cepat (single-field).
* Daftar/riwayat singkat nomor yang baru saja dimasukkan (lokal/session).
* Tombol copy untuk menyalin nomor ke clipboard dengan cepat.
* UI ringan dan cepat (dirancang untuk terminal/PC konter).
* Struktur file sederhana: `index.html`, `css/`, `assets/`.

## Tujuan penggunaan

* Mempercepat proses pengambilan nomor customer saat frontliner melayani.
* Mengurangi kesalahan input saat mengetik nomor.
* Menjadi alat bantu frontend tanpa mempengaruhi sistem backend utama (opsional: integrasi API bila diinginkan).

---

## Cara cepat menjalankan (Quickstart)

> Aplikasi ini terlihat berisi file statis; untuk menjalankan lokal cukup buka file `index.html` di browser atau hosting di static web host.

**Langkah lokal (paling cepat):**

1. Clone repo:

   ```bash
   git clone https://github.com/h4nzs/input.git
   cd input
   ```
2. Buka `index.html` di browser (double click) atau jalankan server statis sederhana:

   ```bash
   # dengan Python 3:
   python -m http.server 8000
   # lalu buka http://localhost:8000
   ```
3. Masukkan nomor customer di field yang tersedia, tekan Enter atau tombol submit, gunakan tombol copy bila perlu.

---

## Struktur file (perkiraan berdasarkan isi repo)

```
input/
├─ index.html        # halaman utama UI input customer
├─ css/
│  └─ style.css      # stylesheet
├─ assets/           # gambar/icon/font atau file statis lain
└─ .gitignore
```

> Catatan: mohon cek isi `index.html` dan `css/` untuk detail kelas dan elemen DOM jika ingin menambahkan fungsionalitas.

---

## Rekomendasi penggunaan & integrasi

1. **Integrasi API (opsional)**

   * Jika data harus disimpan ke server (supaya bisa dicari/rekonsiliasi), buat endpoint POST `/api/customers` yang menerima nomor dan metadata (timestamp, user/frontliner). Pertimbangkan autentikasi sederhana (API key) bila bukan jaringan internal.
2. **Penyimpanan sementara**

   * Bila belum ada backend, gunakan `localStorage` atau `sessionStorage` untuk menyimpan riwayat nomor sementara agar frontliner bisa melihat daftar singkat pada sesi.
3. **Validasi input**

   * Terapkan validasi format nomor (regex) dan trimming whitespace. Tampilkan error message jelas bila input salah.
4. **Copy-to-clipboard**

   * Gunakan API Clipboard modern (`navigator.clipboard.writeText`) dengan fallback untuk browser lama.
5. **Responsif & Mobile**

   * Pastikan ukuran tombol/bidang input cukup besar untuk klik cepat di layar sentuh.
6. **Keamanan & Privasi**

   * Jangan menyimpan nomor sensitif tanpa enkripsi bila disimpan di server. Batasi akses data hanya staf yang berwenang.
7. **Logging & Audit**

   * Bila transaksi membutuhkan audit trail, simpan waktu, user id, dan action (input/copy).
8. **Backup & Export**

   * Sediakan opsi ekspor CSV untuk rekonsiliasi manual bila diperlukan.

---

## Perbaikan fungsional (prioritas tinggi)

* Menambahkan validasi format nomor (mencegah input kosong atau karakter non-digit bila bukan diizinkan).
* Tombol undo/hapus terakhir (jika salah input).
* Indikator keberhasilan (toast) saat nomor disalin atau tersimpan.
* Fallback clipboard untuk browser yang tidak mendukung `navigator.clipboard`.
* Dukungan multi-user sederhana (nama frontliner dipilih sebelum input untuk audit).

## Perbaikan teknis & quality-of-life (opsional)

* Tambahkan `README.md` (saat ini tidak ada). (sudah saya buat ini).
* Tambahkan file `LICENSE` (misalnya MIT) bila ingin open-source.
* Tambahkan `CONTRIBUTING.md` jika ada developer lain yang akan kontribusi.
* Tambahkan minifikasi/optimasi asset jika performance diperlukan.
* Tambahkan test unit/integration jika ada logic JS penting.

---

## Troubleshooting umum

* **Halaman kosong / CSS tidak muncul:** Pastikan jalur ke `css/style.css` benar (cek tag `<link>` di `index.html`).
* **Clipboard tidak bekerja:** Browser mungkin butuh HTTPS atau user gesture; coba panggil `writeText` di event click.
* **Input tidak tersimpan antar reload:** Gunakan `localStorage` jika perlu persist antar reload, atau set up backend.

---

## Contoh roadmap pengembangan

1. (MVP) Validasi input, copy, dan riwayat session.
2. (v1) Integrasi backend sederhana (POST/GET), autentikasi dasar.
3. (v2) Dashboard admin untuk melihat statistik nomor/riwayat.
4. (v3) Export CSV, filter, dan pencarian lanjutan.

---

## Template README.md (siap copy-paste)

> Berikut adalah isi file `README.md` siap-tempel. Gunakan ini langsung di repo:

````markdown
# Input — Sistem Input Data Nomor Customer

**Satu-liner:** Aplikasi web sederhana untuk memasukkan dan mencari nomor customer agar proses transaksi di konter Ruang Data Telemedia lebih cepat bagi frontliner.

## Deskripsi
Aplikasi ini dibuat khusus atas permintaan owner konter Ruang Data Telemedia untuk mempermudah frontliner dalam memasukkan data nomor customer saat transaksi. Aplikasi berbasis file statis (HTML/CSS/asset) dengan antarmuka minimal yang memfokuskan pada input cepat, pencarian, dan penyalinan nomor customer ke sistem transaksi.

## Fitur utama
- Form input nomor customer cepat (single-field).
- Daftar/riwayat singkat nomor yang baru saja dimasukkan (lokal/session).
- Tombol copy untuk menyalin nomor ke clipboard dengan cepat.
- UI ringan dan cepat (dirancang untuk terminal/PC konter).

## Cara cepat menjalankan (Quickstart)
1. Clone repo:
   ```bash
   git clone https://github.com/h4nzs/input.git
   cd input
````

2. Buka `index.html` di browser atau jalankan server statis:

   ```bash
   python -m http.server 8000
   # buka http://localhost:8000
   ```
3. Masukkan nomor customer, tekan Enter atau tombol submit, lalu gunakan tombol copy bila perlu.

## Struktur file

```
input/
├─ index.html
├─ css/
│  └─ style.css
├─ assets/
└─ .gitignore
```

## Rekomendasi dan praktik terbaik

* Tambahkan validasi input (regex), trimming, dan pesan error.
* Simpan riwayat sementara di `localStorage` bila belum ada backend.
* Pertimbangkan integrasi backend untuk penyimpanan/rekonsiliasi (endpoint POST/GET).
* Implementasikan clipboard modern (`navigator.clipboard.writeText`) dengan fallback.
* Tambahkan `LICENSE` jika ingin publikasi open-source (contoh: MIT).

## Troubleshooting

* CSS tidak muncul -> cek path `css/style.css`.
* Clipboard gagal -> butuh user gesture atau koneksi HTTPS.
* Offline persistence -> gunakan `localStorage` atau IndexedDB.

## Roadmap singkat

1. Validasi & UX improvements.
2. Integrasi backend dasar (autentikasi bila perlu).
3. Dashboard admin + export CSV.

## Kontak

Untuk perubahan/desain lebih lanjut, hubungi owner konter atau pengembang: *[owner@ruangdatatelemedia.example](mailto:owner@ruangdatatelemedia.example)* (ganti sesuai kontak nyata).


[1]: https://github.com/h4nzs/input "GitHub - h4nzs/input"
