# Analisis Perbaikan Responsi Infrastruktur Teknologi Informasi

## Identitas Praktikan
- Nama: Alma Maida Wirastuti
- NIM: H1H024021

---

## Permasalahan 1 - Syntax Error pada docker-compose.yml

**Gejala:**
Perintah docker compose up gagal tanpa ada container yang berhasil dijalankan.

**Penyebab:**
Deklarasi services tidak diikuti tanda titik dua sehingga file YAML tidak dapat di-parse.

**Solusi:**
Mengubah services menjadi services:.

---

## Permasalahan 2 - DB_HOST Salah pada web1

**Gejala:**
Service web1 tidak dapat terhubung ke database.

**Penyebab:**
Nilai DB_HOST diisi mysql sedangkan nama service database yang terdefinisi adalah db.

**Solusi:**
Mengubah nilai DB_HOST pada web1 menjadi db.

---

## Permasalahan 3 - Password Database Salah pada web2

**Gejala:**
Service web2 gagal melakukan koneksi ke database karena error autentikasi.

**Penyebab:**
Nilai DB_PASS diisi wrongpassword yang tidak sesuai dengan password yang didefinisikan pada service db.

**Solusi:**
Mengubah nilai DB_PASS pada web2 menjadi student123.

---

## Permasalahan 4 - Build Context web3 Mengarah ke Folder yang Tidak Ada

**Gejala:**
Docker gagal melakukan build pada service web3.

**Penyebab:**
Nilai context mengarah ke ./web33 yang tidak ditemukan di dalam repository.

**Solusi:**
Mengubah nilai context menjadi ./web3.

---

## Permasalahan 5 - Service web3 Tidak Terdaftar di Network Frontend

**Gejala:**
Nginx tidak dapat meneruskan request ke web3 meskipun container sudah berjalan.

**Penyebab:**
Service web3 hanya terhubung ke network backend sehingga tidak dapat dijangkau oleh Nginx.

**Solusi:**
Menambahkan network frontend pada konfigurasi service web3.

---

## Permasalahan 6 - Nama Volume Tidak Konsisten

**Gejala:**
Docker menampilkan error saat mencoba mount volume untuk service database.

**Penyebab:**
Volume yang digunakan pada service db adalah db-data namun dideklarasikan sebagai database-data.

**Solusi:**
Menyeragamkan nama volume menjadi db-data di seluruh bagian docker-compose.yml.

---

## Permasalahan 7 - Nama Upstream web1 Salah pada Konfigurasi Nginx

**Gejala:**
Nginx menampilkan error bad gateway saat request diteruskan ke web1.

**Penyebab:**
Nama server pada upstream Nginx ditulis web11 padahal nama container yang benar adalah web1.

**Solusi:**
Mengubah nama upstream dari web11 menjadi web1:80.

---

## Permasalahan 8 - Port Upstream web3 pada Nginx Tidak Sesuai

**Gejala:**
Request yang diteruskan ke web3 melalui Nginx tidak mendapat respons.

**Penyebab:**
Port upstream web3 didefinisikan sebagai 8080 sedangkan web server berjalan di port 80.

**Solusi:**
Mengubah port upstream web3 menjadi web3:80.

---

## Permasalahan 9 - Label Server web2 Salah pada index.php

**Gejala:**
Halaman web2 menampilkan teks WEB-WEB bukan WEB-2.

**Penyebab:**
Terdapat kesalahan penulisan string identitas server pada file index.php milik web2.

**Solusi:**
Memperbaiki string menjadi WEB-2.

---

## Permasalahan 10 - Label Server web3 Salah pada index.php

**Gejala:**
Halaman web3 menampilkan teks WEB-WOB bukan WEB-3.

**Penyebab:**
Terdapat kesalahan penulisan string identitas server pada file index.php milik web3.

**Solusi:**
Memperbaiki string menjadi WEB-3.

---

## Permasalahan 11 - Identitas Praktikan Belum Diisi

**Gejala:**
Halaman web menampilkan teks placeholder untuk nama dan NIM.

**Penyebab:**
Variabel nama dan NIM pada masing-masing file index.php belum diisi dengan data yang sebenarnya.

**Solusi:**
Mengisi nama lengkap dan NIM pada seluruh file index.php di web1, web2, dan web3.
