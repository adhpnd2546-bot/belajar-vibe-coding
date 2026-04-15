# Panduan Pengembangan Backend Aplikasi

Dokumen ini ditujukan untuk programmer junior sebagai panduan implementasi aplikasi tingkat tinggi.

## Stack Teknologi
- **Runtime & Package Manager**: Bun
- **Framework**: ElysiaJS
- **ORM**: Drizzle ORM
- **Database**: MySQL

---

## Instruksi Implementasi (High-level)

### 1. Persiapan Environment & Konfigurasi
- **Konfigurasi Database**: Buat database baru di MySQL server lokal atau remote.
- **Variabel Lingkungan**: Buat file `.env` di root project. Tambahkan variabel `DATABASE_URL` yang berisi connection string MySQL (`mysql://user:password@host:port/dbname`).

### 2. Setup Drizzle ORM
- **Skema (_Schema_)**: Buat file khusus untuk mendefinisikan skema database menggunakan Drizzle (misalnya `src/db/schema.ts`). Buat setidaknya satu tabel sederhana sebagai percobaan (contoh: tabel `users`).
- **Koneksi Database**: Buat file koneksi database menggunakan driver `mysql2` melalui Drizzle (misalnya `src/db/index.ts`).
- **Migrasi**: Buat file konfigurasi `drizzle.config.ts` untuk keperluan `drizzle-kit`. Kemudian lakukan push/migrasi skema ke database MySQL.

### 3. Implementasi Routing dengan ElysiaJS
- **Inisialisasi Server**: Pada file `src/index.ts`, inisialisasi aplikasi menggunakan `Elysia`.
- **Pembuatan Endpoint (CRUD)**:
  - Buat router/endpoint untuk `GET /` untuk memastikan server berjalan dengan baik (Health Chek).
  - Buat endpoint `GET /users` yang terintegrasi dengan database (Drizzle) untuk mengambil data.
  - Buat endpoint `POST /users` untuk memasukkan data baru ke dalam tabel yang telah kita buat.

### 4. Menjalankan Aplikasi
- Tambahkan script pada `package.json` (misalnya `"dev": "bun --watch src/index.ts"`).
- Pandu cara melakukan uji coba API (contohnya bisa dites menggunakan Postman, cURL, atau Insomnia).
