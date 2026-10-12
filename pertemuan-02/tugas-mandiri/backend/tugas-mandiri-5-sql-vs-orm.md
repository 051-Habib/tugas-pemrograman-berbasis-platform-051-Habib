# Tugas Mandiri 5 — Membandingkan SQL Mentah dan ORM

**Operasi Database yang Dipilih:** Mengambil satu data berdasarkan ID
**Tabel yang Digunakan:** `jadwal`

---

### A. SQL Mentah

```sql
SELECT *
FROM jadwal
WHERE id = ?;
```
---

### B. ORM
```sql
const jadwal = await prisma.jadwal.findUnique({
  where: {
    id: 1
  }
});
```

## C. Analisis dan Pertanyaan Evaluasi

Bandingkan kedua contoh kode yang Anda tulis, lalu jawab pertanyaan berikut:

1. Apa perbedaan cara penulisan operasi database menggunakan SQL secara langsung dan ORM?

- Jawaban: SQL mentah ditulis menggunakan kueri SQL murni dalam bentuk string teks yang langsung berinteraksi dengan database relasional. Sementara itu, ORM (Object-Relational Mapping) menggunakan pendekatan berbasis objek atau metode bahasa pemrograman (seperti JavaScript/TypeScript) untuk melakukan operasi database tanpa harus menulis sintaks SQL secara manual.

2. Apa kelebihan SQL mentah?

- Jawaban: SQL mentah memberikan kontrol penuh kepada pengembang terhadap performa kueri yang kompleks, lebih mudah dioptimalkan untuk kueri spesifik, dan tidak memerlukan overhead dari pustaka tambahan yang besar.

3. Apa kelebihan ORM?

- Jawaban: ORM mempercepat proses pengembangan (development), membuat kode lebih bersih, mudah dibaca, dan terstruktur berbasis objek. Selain itu, ORM bersifat agnostik terhadap jenis database dan menyediakan keamanan bawaan terhadap risiko injeksi SQL melalui penggunaan parameterisasi otomatis.

4. Apa yang dimaksud dengan SQL injection, dan apa dampaknya terhadap data aplikasi?

- Jawaban: SQL Injection adalah celah keamanan di mana penyerang dapat menyisipkan atau memanipulasi kueri SQL melalui masukan (input) pengguna yang tidak disaring dengan benar. Dampaknya sangat berbahaya, mulai dari kebocoran data sensitif, pencurian informasi, modifikasi data ilegal, hingga penghapusan seluruh isi database aplikasi.

5. Mengapa penggunaan parameter query dapat mengurangi risiko SQL injection?

- Jawaban: Parameter query (seperti menggunakan tanda tanya ? atau placeholder) memisahkan antara struktur perintah SQL dengan data masukan (input). Dengan cara ini, database akan memperlakukan input pengguna murni sebagai data literal, bukan sebagai bagian dari perintah eksekusi SQL, sehingga kode berbahaya tidak akan dieksekusi.

6. Bagaimana ORM membantu pengembang mengakses database? Kaitkan jawaban Anda dengan contoh kode yang telah Anda tulis.

- Jawaban: ORM membantu pengembang dengan menerjemahkan fungsi pemrograman menjadi kueri database secara otomatis. Sebagai contoh, dalam kode prisma.jadwal.findUnique({ where: { id: 1 } }), pengembang tidak perlu menulis sintaks SELECT * FROM jadwal WHERE id = 1 secara manual. ORM mengabstraksi perintah tersebut menjadi objek kode yang aman, intuitif, dan mudah dikelola.



















