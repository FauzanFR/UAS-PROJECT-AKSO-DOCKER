# UASP Docker Project

## Deskripsi
Proyek ini adalah tugas Ujian Akhir Semester Praktik untuk matakuliah **Arsitektur Komputer & Sistem Operasi**. Proyek ini menggunakan Docker Compose untuk menjalankan tiga layanan:
1. **NGINX**: Web server untuk menyajikan halaman HTML sederhana.
2. **MySQL**: Database server untuk menyimpan data.
3. **RabbitMQ**: Aplikasi tambahan dari kategori Message Queues.

Semua layanan diatur menggunakan file `docker-compose.yml` dan saling terhubung melalui jaringan Docker.

---

## File dan Struktur Folder
```
UASP/
│
├── docker-compose.yml  # File konfigurasi Docker Compose
├── index.html          # File HTML untuk halaman NGINX
├── rabbitmq.conf       # File konfigurasi tambahan untuk RabbitMQ
└── README.md           # Dokumentasi proyek ini
```

---

## Langkah Menjalankan Proyek

### 1. Pastikan Docker Terinstal
- Unduh dan instal Docker dari [docker.com](https://www.docker.com/).
- Pastikan Docker Compose sudah tersedia (bawaan Docker Desktop versi terbaru).

### 2. Jalankan Proyek
1. **Buka Terminal atau Command Prompt**
   - Arahkan terminal ke folder tempat file `docker-compose.yml` disimpan.
     ```bash
     cd /path/to/UASP
     ```

2. **Jalankan Docker Compose**
   - Jalankan perintah berikut untuk memulai layanan:
     ```bash
     docker-compose up
     ```

3. **Periksa Layanan**
   - **NGINX**: Buka browser dan akses `http://localhost:8080`.
     - Halaman web sederhana akan muncul dengan tulisan "Halo, ini adalah halaman NGINX!".
   - **RabbitMQ**: Buka browser dan akses `http://localhost:15672`.
     - Login dengan:
       - Username: `admin`
       - Password: `adminpassword`
     - Dashboard RabbitMQ akan terbuka.
   - **MySQL**: Gunakan terminal untuk masuk ke MySQL:
     ```bash
     docker exec -it mysql_db mysql -u root -p
     ```
     - Masukkan password: `rootpassword`.
     - Jalankan perintah berikut untuk melihat database:
       ```sql
       SHOW DATABASES;
       ```

---

## Konfigurasi Utama di `docker-compose.yml`
### 1. NGINX (Layanan Web Server)
- Menampilkan halaman HTML dari file `index.html`.
- Tersedia di port `8080`.

### 2. MySQL (Layanan Database)
- Database default: `ujian`.
- User dan password:
  - Root User: `root` / `rootpassword`
  - User Tambahan: `user` / `password`.
- Data disimpan di volume Docker untuk menjaga persistensi.

### 3. RabbitMQ (Layanan Message Queue)
- Dashboard tersedia di port `15672`.
- Login menggunakan:
  - Username: `admin`
  - Password: `adminpassword`.
- Menggunakan konfigurasi tambahan dari `rabbitmq.conf` untuk pengaturan lebih lanjut.

---

## Troubleshooting
1. **Error saat menjalankan `docker-compose up`:**
   - Pastikan Docker Desktop sedang berjalan.
   - Periksa apakah port `8080` atau `15672` sedang digunakan oleh aplikasi lain.

2. **Halaman NGINX tidak muncul:**
   - Periksa apakah file `index.html` ada di folder yang sama dengan `docker-compose.yml`.

3. **Tidak bisa login ke RabbitMQ:**
   - Pastikan menggunakan username dan password yang benar (`admin` / `adminpassword`).

4. **MySQL tidak berjalan:**
   - Periksa log di terminal untuk melihat pesan kesalahan.
   - Pastikan konfigurasi database di `docker-compose.yml` sudah benar.

---

## Penutup
Proyek ini membuktikan kemampuan untuk:
1. Menjalankan beberapa layanan dalam Docker menggunakan Docker Compose.
2. Menggunakan volume, jaringan, dan konfigurasi tambahan untuk menghubungkan layanan.
3. Menyediakan fitur tambahan di setiap layanan.

Jika ada pertanyaan atau masalah, jangan ragu untuk menghubungi saya!
