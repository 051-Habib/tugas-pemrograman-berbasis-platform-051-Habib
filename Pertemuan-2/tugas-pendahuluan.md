# 1. Bandingkan struktur data pada /posts/1 dan /users/1 di JSONPlaceholder. Jelaskan perbedaan field dan fungsinya.

# /posts/1
Struktur Data: Berisi data konten/postingan.
# Field & Fungsi:
- userId: ID pengguna yang membuat postingan (penghubung ke entitas user).
- id: ID unik untuk setiap postingan.
- title: Judul dari postingan.
- body: Isi utama dari postingan.

# /users/1
Struktur Data: Berisi data profil pengguna.
# Field & Fungsi:
- id: ID unik untuk setiap pengguna.
- name: Nama lengkap pengguna.
- username: Nama akun pengguna.
- email: Alamat email pengguna.
- address (Object): Informasi alamat (jalan, kota, zip-code, geo koordinat).
- phone: Nomor telepon pengguna.
- website: Situs web pengguna.
- company (Object): Informasi perusahaan tempat pengguna bekerja.

---

# 2. Analisa struktur tabel yang ada pada /posts dan /users di JSONPlaceholder. Buat diagram relasi sederhana yang menjelaskan hubungan antar tabel.

- Tabel users: Memiliki Primary Key `id`.
- Tabel posts: Memiliki Primary Key `id` dan Foreign Key `userId`.

Relasi: One-to-Many (1:N) — Satu pengguna dapat memiliki banyak postingan, tetapi satu postingan hanya dimiliki oleh satu pengguna.

```text
+------------------+                  +------------------+
|      users       |                  |      posts       |
+------------------+                  +------------------+
| PK : id          |<-------1:N-------| PK : id          |
|      name        |                  | FK : userId      |
|      username    |                  |      title       |
|      email       |                  |      body        |
+------------------+                  +------------------+

# 3. Analisis hubungan antara URL, method, dan data yang dikembalikan pada contoh /posts di JSONPlaceholder.
- GET /posts : Mengambil seluruh daftar postingan (mengembalikan Array of Objects).
- GET /posts/1 : Mengambil satu postingan spesifik (mengembalikan Object).
- POST /posts : Membuat postingan baru (mengembalikan Object postingan baru + ID dari server).
- PUT /posts/1 : Memperbarui seluruh data postingan ID 1 (mengembalikan Object postingan diperbarui).
- PATCH /posts/1 : Memperbarui sebagian field postingan ID 1 (mengembalikan Object dengan field yang diubah).
- DELETE /posts/1 : Menghapus postingan ID 1 (mengembalikan Object kosong {}).

# 4. Bedakan penggunaan /posts/1 dan ?userId=1 berdasarkan hasil yang dikembalikan JSONPlaceholder.
- /posts/1 (Path Parameter): Mengakses satu resource postingan spesifik berdasarkan ID postingan. Mengembalikan single Object.
- /posts?userId=1 (Query Parameter): Memfilter daftar postingan berdasarkan pemiliknya (userId = 1). Mengembalikan Array of Objects.

# 5. Bandingkan hasil GET, POST, PUT, PATCH, dan DELETE pada JSONPlaceholder. Kaitkan setiap method dengan status code dan perubahan datanya.
- GET    : Status Code 200 OK | Tidak ada perubahan data di server (Read-only).
- POST   : Status Code 201 Created | Menambahkan data baru di server.
- PUT    : Status Code 200 OK | Mengganti/memperbarui seluruh isi data resource.
- PATCH  : Status Code 200 OK | Memperbarui sebagian field dari data resource.
- DELETE : Status Code 200 OK | Menghapus data resource dari server.


  

