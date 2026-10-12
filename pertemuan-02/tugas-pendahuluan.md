## 1. Perbandingan Struktur Data /posts/1 dan /users/1

### a. Endpoint /posts/1

### a. Endpoint /posts/1

Struktur JSON:

```json
{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere...",
  "body": "quia et suscipit..."
}


### Penjelasan Field & Fungsinya:

- userId: Identitas unik milik pengguna (penulis) yang membuat postingan tersebut.
- id: Identitas unik (primary key) dari postingan itu sendiri.
- title: Judul artikel atau postingan.
- body: Konten atau isi teks dari postingan.

### b. Endpoint /users/1

Struktur JSON:

```json
{
  "id": 1,
  "name": "Habibullah sukron",
  "username": "051-Habib",
  "email": "sihabeb16@gmail.com",
  "address": {
    "street": "Jl.Darma No. 5",
    "suite": "Apt. 4B",
    "city": "Pamekasan",
    "zipcode": "12345"
  },
  "phone": "0812-3456-7890",
  "website": "[github.com/051-Habib](https://github.com/051-Habib)",
  "company": {
    "name": "Teknik Informatika UNIRA",
    "catchPhrase": "Backend Enthusiast",
    "bs": "Web Development"
  }
}
```

### Penjelasan Detail Field address & company:

### address (Objek Bersarang / nested object):

- street : Nama jalan atau lokasi tempat tinggal pengguna.

- suite : Detail tambahan alamat seperti nomor apartemen, gedung, atau blok.

- city : Nama kota tempat tinggal pengguna.

- zipcode : Kode pos wilayah atau daerah pengguna.

### company (Objek Bersarang / nested object): 

- name : Nama perusahaan, institusi, atau instansi tempat pengguna bekerja/belajar (misal: Teknik Informatika UNIRA).

- catchPhrase : Slogan atau moto utama perusahaan/individu (misal: Backend Enthusiast).

- bs : Bidang bisnis atau fokus keahlian komersial (misal: Web Development). 

## 2. Analisis Tabel & Diagram Relasi

### Analisis Relasi:

- users berperan sebagai entitas utama (parent table). 

- posts berperan sebagai entitas turunan (child table).

- Hubungan (relationship) antara keduanya adalah One-to-Many (1 : N): Satu user dapat membuat banyak post, namun satu post hanya dimiliki oleh satu user melalui kolom userId (Foreign Key).

### Diagram Relasi (ERD Sederhana):

```text
 +-------------------+         1 : N         +-------------------+
 |       USERS       |-----------------------<       POSTS       |
 +-------------------+                       +-------------------+
 | PK : id           |                       | PK : id           |
 |      name         |                       | FK : userId       |
 |      username     |                       |      title        |
 |      email        |                       |      body         |
 +-------------------+                       +-------------------+
```

### 3. Analisis Hubungan URL, Method, dan Data (/posts)

Pada arsitektur REST API, kombinasi URL dan HTTP Method menentukan operasi/aksi yang dilakukan terhadap data:

1. GET /posts:

- Fungsi: Mengambil seluruh daftar postingan.   
- Data Kembalian: Array JSON berisi 100 objek post.  

2. GET /posts/1:

- Fungsi: Mengambil data spesifik post dengan ID 1.   
- Data Kembalian: 1 Objek JSON post.  

3. POST /posts: 

- Fungsi: Membuat data postingan baru.   
- Data Kembalian: Objek baru yang telah dibuat (disertai id baru dari server). 

### 4. Perbedaan /posts/1 dan ?userId=1

### /posts/1 (Path Parameter):

- Tujuan: Menuju entitas spesifik berdasarkan Primary Key postingan.

- Hasil: Mengembalikan 1 objek tunggal JSON (post yang ID-nya 1). 

### /posts?userId=1 (Query Parameter):

- Tujuan: Memfilter/menyaring koleksi postingan berdasarkan kriteria tertentu (userId = 1).

- Hasil: Mengembalikan Array berisi daftar semua objek post yang ditulis oleh pengguna dengan ID 1 (misalnya ada 10 posts).

### 5. Perbandingan HTTP Method pada JSONPlaceholder

| HTTP Method | Fungsi Utama | Status Code (Respon) | Perubahan Data di Server |
| :--- | :--- | :--- | :--- |
| **GET** | Membaca / mengambil data | `200 OK` | Tidak ada perubahan (*Read-only*) |
| **POST** | Menambahkan data baru | `201 Created` | Data baru ditambahkan (ditandai ID baru) |
| **PUT** | Mengganti/memperbarui seluruh isi data | `200 OK` | Seluruh objek ditimpa dengan data baru |
| **PATCH** | Memperbarui sebagian isi field data | `200 OK` | Hanya field yang dikirim yang diperbarui |
| **DELETE** | Menghapus data | `200 OK` | Data dengan ID terkait dihapus |





