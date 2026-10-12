## Tugas Mandiri 4 — Pengujian API dengan Postman dan curl

### Uji API menggunakan kedua alat berikut, lalu bandingkan cara masing-masing alat menampilkan hasil pengujian:

- Postman

- curl

---

### A. Menggunakan Postman

1. Permintaan GET melalui Postman

- URL Lengkap: https://httpbin.org/get

- Tujuan Endpoint: Menguji permintaan GET standar untuk mengambil atau membaca data dari server.

- Metode: GET

- Kode Status HTTP: 200 OK

- Isi Respons (Response Body):
```json
{
  "args": {},
  "headers": {
    "Accept": "*/*",
    "Host": "httpbin.org"
  },
  "origin": "114.125.x.x",
  "url": "https://httpbin.org/get"
}
```
---

### 2. Permintaan POST melalui Postman

- URL Lengkap: https://httpbin.org/post

- Tujuan Endpoint: Menguji pengiriman data ke server menggunakan metode POST dengan menyertakan body berformat JSON.

- Metode: POST

- Data JSON yang Dikirim:
```json
{
  "nama": "Habib",
  "kelas": "Informatika"
}
```

- Kode Status HTTP: 200 OK

- Isi Respons (Response Body):
```json
{
  "args": {},
  "data": "{\n \"nama\": \"Habib\",\n \"kelas\": \"Informatika\"\n}",
  "json": {
    "kelas": "Informatika",
    "nama": "Habib"
  },
  "origin": "114.125.x.x",
  "url": "https://httpbin.org/post"
}
```
---

### B. Menggunakan curl

1. Perintah curl -i https://httpbin.org/get

- Tujuan: Menjalankan permintaan HTTP GET melalui terminal sekaligus menyertakan informasi header respons HTTP lengkap.

- Hasil Pengeluaran (Output): Menampilkan baris status HTTP, metadata header respons, diikuti dengan isi data JSON respons di bagian bawah.

2. Perintah curl -i https://httpbin.org/status/404

- Tujuan: Menguji pengembalian status kode kesalahan tertentu dari server (dalam hal ini 404 Not Found).

- Hasil Pengeluaran (Output): Menampilkan status HTTP/1.1 404 NOT FOUND beserta header respons terkait.

---

### C. Membandingkan curl -s dan curl -i

- Susun penjelasan dalam 3–5 kalimat yang mencakup jawaban atas pertanyaan berikut:

1. Apa perbedaan hasil kedua perintah tersebut?

2. Apa fungsi opsi -s?

3. Apa fungsi opsi -i?

4. Kapan Anda menggunakan masing-masing opsi?

- Jawaban Analisis:
- Perintah curl -s (silent) hanya menghasilkan keluaran berupa isi data respons (body) secara bersih tanpa menampilkan progress bar atau header. Sebaliknya, perintah curl -i (include) menyertakan informasi header respons HTTP lengkap di bagian atas sebelum isi respons. Opsi -s digunakan saat kita hanya memerlukan data mentah tanpa gangguan teks tambahan, sedangkan opsi -i digunakan saat proses debugging untuk memeriksa kode status dan header dari server.

---

### Lampiran Tangkapan Layar Pengujian
* Permintaan GET melalui Postman: `assets/postman-get`.

* Permintaan POST melalui Postman: `assets/postman-post`.

* Perintah curl -i: `assets/curl-i.png`.

* Perintah curl -s: `assets/curl-s.png`.




