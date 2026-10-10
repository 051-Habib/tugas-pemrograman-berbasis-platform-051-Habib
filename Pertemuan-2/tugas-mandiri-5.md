# Tugas Mandiri 5 — Membandingkan SQL Mentah dan ORM

**Operasi Database:** Mengambil satu data berdasarkan ID  
**Nama Tabel:** `jadwal`

---

## A. SQL Mentah

Penulisan query menggunakan sintaks SQL secara langsung (menggunakan *prepared statement* untuk keamanan):

```sql
SELECT * 
FROM jadwal 
WHERE id = ?;
```
Contoh implementasi pada Node.js (dengan library mysql2):

const [rows] = await db.execute('SELECT * FROM jadwal WHERE id = ?', [1]);

## B. ORM (Object-Relational Mapping)
Penulisan operasi database menggunakan ORM Prisma berbasis method/objek JavaScript:

const jadwal = await prisma.jadwal.findUnique({
  where: {
    id: 1
  }
});

## C. Jawaban Pertanyaan
1. Apa perbedaan cara penulisan operasi database menggunakan SQL secara langsung dan ORM?
- SQL Mentah: Ditulis menggunakan bahasa deklaratif SQL (Structured Query Language) dalam   bentuk string perintah database (SELECT, INSERT, UPDATE, DELETE).

- ORM: Ditulis menggunakan sintaks atau metode objek dari bahasa pemrograman yang digunakan (misalnya pemanggilan metode JavaScript/TypeScript seperti findUnique()), sehingga pengembang tidak perlu menulis query SQL secara manual.

2. Apa kelebihan SQL mentah?
- Performa Tinggi: Perintah dikirim dan dieksekusi langsung oleh database engine tanpa overhead atau abstraction layer tambahan.

- Kontrol Penuh & Fleksibel: Memudahkan pembuatan query kompleks seperti joins bersarang, agregasi berat, dan optimasi query khusus.

- Tidak Terikat Framework/Library: Kompatibel secara universal selama sintaks SQL didukung oleh Relational Database Management System (RDBMS) yang digunakan.

3. Apa kelebihan ORM?
- Pengembangan Lebih Cepat & Produktif: Penulisan kode lebih ringkas, bersih, dan konsisten dengan bahasa pemrograman utama.

- Type Safety & Auto-completion: Mencegah kesalahan pengetikan nama kolom/tabel berkat fitur auto-complete pada editor/IDE (seperti VS Code).

- Fitur Keamanan Bawaan: Secara otomatis menggunakan parameterized queries yang melindungi aplikasi dari ancaman SQL Injection.

- Abstraksi Database (Database Agnostic): Memudahkan migrasi antar RDBMS (misalnya dari PostgreSQL ke MySQL) tanpa harus merombak seluruh query.

4. Apa yang dimaksud dengan SQL injection, dan apa dampaknya terhadap data aplikasi?

- SQL Injection (SQLi) adalah teknik serangan di mana peretas menyisipkan kode SQL berbahaya melalui input pengguna (seperti form atau URL parameter) yang tidak divalidasi.

- Dampak: Peretas dapat membaca data sensitif, mengubah atau menghapus data di database, bypass proses autentikasi (login), hingga mengambil alih hak akses server database secara penuh.

5. Mengapa penggunaan parameter query dapat mengurangi risiko SQL injection?

-  Penggunaan parameter query (prepared statement dengan placeholder ?) memisahkan antara struktur perintah SQL dan nilai data input. Database akan memperlakukan input pengguna secara ketat sebagai literal string/data, bukan sebagai bagian dari instruksi atau perintah SQL yang dapat dieksekusi, sehingga manipulasi kode SQL menjadi tidak memungkinkan.

6. Bagaimana ORM membantu pengembang mengakses database? Kaitkan jawaban Anda dengan contoh kode yang telah Anda tulis.

     ORM menjembatani struktur tabel relasional database dengan objek pemrograman. Pengembang dapat mengelola data seolah-olah berinteraksi dengan objek JavaScript biasa.

- Kaitan dengan contoh kode: Pada contoh prisma.jadwal.findUnique({ where: { id: 1 } }), pengembang tidak perlu menghafal klausa SELECT * FROM jadwal WHERE id = 1 atau mengurus connection pool secara manual. ORM mentransformasikan panggilan fungsi tersebut menjadi query SQL yang aman, mengeksekusinya ke database, lalu mengembalikan hasilnya langsung dalam bentuk objek JavaScript siap pakai.
