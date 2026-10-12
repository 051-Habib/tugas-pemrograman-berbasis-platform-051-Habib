## Tugas Mandiri 3 — Memahami Request dan Response

Tugas ini melatih Anda mengidentifikasi informasi yang dikirim klien kepada server dan informasi yang dikembalikan server kepada klien menggunakan endpoint /get dan /headers pada HTTPBin.

---

## Detail Pengujian Postman

1. Endpoint: GET Request dengan Query Parameter (/get)

- URL Lengkap: https://httpbin.org/get?nama=Habib&nim=051

- Tujuan Endpoint: Menguji pengiriman data dari klien ke server menggunakan query parameters pada method GET.

- Data yang Dikirim: nama=Habib, nim=051 (melalui URL/Query String)

- Kode Status HTTP: 200 OK

- Isi Respons (Response Body):
```json
{
  "args": {
    "nama": "Habib",
    "nim": "051"
  },
  "headers": {
    "Accept": "*/*",
    "Accept-Encoding": "gzip, deflate, br",
    "Host": "httpbin.org",
    "User-Agent": "PostmanRuntime/7.32.3",
    "X-Amzn-Trace-Id": "Root=1-65000000-..."
  },
  "origin": "114.125.x.x",
  "url": "https://httpbin.org/get?nama=Habib&nim=051"
}
```

## 2. Endpoint: Header Inspection (/headers)

- URL Lengkap: https://httpbin.org/headers

- Tujuan Endpoint: Menguji dan melihat informasi metadata (HTTP headers) yang diterima oleh server dari klien.

- Kode Status HTTP: 200 OK

- Isi Respons (Response Body):
```json
{
  "headers": {
    "Accept": "*/*",
    "Accept-Encoding": "gzip, deflate, br",
    "Host": "httpbin.org",
    "User-Agent": "PostmanRuntime/7.32.3",
    "X-Amzn-Trace-Id": "Root=1-65000001-..."
  }
}
```
## Pertanyaan Analisis & Evaluasi

1. Apa yang dimaksud dengan permintaan (request), dan pihak mana yang mengirimkannya?

- Jawaban: Permintaan (request) adalah sekumpulan data atau pesan yang dikirimkan untuk meminta layanan, pemrosesan data, atau sumber daya dari server. Pihak yang mengirimkannya adalah Client (misalnya aplikasi Postman atau web browser).

2. Apa yang dimaksud dengan respons (response), dan pihak mana yang mengirimkannya?

- Jawaban: Respons (response) adalah balasan yang diberikan setelah server selesai memproses suatu permintaan, yang berisi status kode, header, serta data hasil proses. Pihak yang mengirimkannya adalah Server.

3. Apa fungsi query parameter? Jelaskan menggunakan parameter nama dan nim pada pengujian Anda.

- Jawaban: Query parameter berfungsi untuk mengirimkan data tambahan melalui URL. Berdasarkan hasil pengujian di atas, parameter nama=Habib dan nim=051 dikirimkan lewat URL, lalu server HTTPBin memprosesnya dan mengembalikannya ke dalam objek JSON bagian "args", membuktikan bahwa server sukses menerima parameter tersebut.

4. Apa fungsi HTTP header? Sebutkan satu header yang terlihat pada hasil pengujian dan jelaskan informasi yang dimuatnya.

- Jawaban: HTTP header berfungsi sebagai informasi tambahan atau metadata yang menyertai komunikasi antara klien dan server.

- Contoh Header: Header "Host": "httpbin.org", yang memuat informasi mengenai nama domain atau alamat server tujuan tempat permintaan dikirim.

5. Apa perbedaan penempatan data pada query parameter di URL dan pada body permintaan?

- Jawaban:

- Query Parameter: Data diletakkan langsung di dalam URL (terbuka), biasanya digunakan pada method GET untuk pencarian atau filter data yang tidak bersifat rahasia.

- Body Permintaan: Data disembunyikan di dalam bagian badan (body) paket HTTP, biasanya digunakan pada method POST, PUT, atau PATCH untuk mengirim data berukuran besar atau data sensitif (seperti password).

---

## Lampiran Tangkapan Layar Postman
* Screenshot GET : `assets/request-get.png`
* Screenshot Headers : `assets/request-headers.png`





