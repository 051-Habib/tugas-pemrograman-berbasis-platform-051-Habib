# Tugas Mandiri 2 — Memahami HTTP Status Code

Tugas ini melatih Anda menjelaskan makna kode status HTTP dan menghubungkannya dengan hasil pengujian menggunakan endpoint khusus HTTPBin (`/status/:code`).

---

## Tabel Rangkuman Hasil Pengujian HTTP Status Code

| Status Code | Arti | Hasil Pengujian | Kapan Digunakan |
| :--- | :--- | :--- | :--- |
| **200** | OK | Berhasil mengembalikan respons standar (`200 OK`). | Digunakan saat permintaan (*request*) berhasil diproses sepenuhnya oleh server tanpa ada kendala. |
| **201** | Created | Berhasil mengembalikan status bahwa data baru telah dibuat. | Digunakan ketika server sukses membuat sumber daya atau data baru (misalnya setelah method POST). |
| **400** | Bad Request | Mengembalikan status bahwa permintaan tidak valid. | Digunakan saat server tidak dapat memproses permintaan karena kesalahan format dari sisi klien (misalnya sintaks JSON salah). |
| **401** | Unauthorized | Mengembalikan status penolakan karena belum terotentikasi. | Digunakan ketika pengguna mencoba mengakses halaman yang butuh *login*, tetapi belum menyertakan token atau identitas yang sah. |
| **403** | Forbidden | Mengembalikan status bahwa akses dilarang. | Digunakan saat server mengenali identitas pengguna, tetapi pengguna tersebut tidak memiliki hak akses (*permission*) ke halaman tersebut. |
| **404** | Not Found | Mengembalikan status bahwa alamat atau endpoint tidak ditemukan. | Digunakan ketika URL atau sumber daya yang diminta oleh klien tidak tersedia di server. |
| **500** | Internal Server Error | Mengembalikan status adanya kendala di sisi server. | Digunakan saat terjadi kesalahan tak terduga di dalam sistem atau kode server saat memproses permintaan. |

---

## Detail Pengujian HTTP Status Code di Postman

### 1. Status Code: 200 (OK)
* **URL Lengkap:** `https://httpbin.org/status/200`
* **Tujuan Endpoint:** Menguji respons sukses standar dari server.
* **Kode Status HTTP:** `200 OK`
* **Isi Respons (Response Body):**
*(Respons berupa teks kosong atau sukses standar dari HTTPBin)*

---

### 2. Status Code: 404 (Not Found)
* **URL Lengkap:** `https://httpbin.org/status/404`
* **Tujuan Endpoint:** Menguji respons ketika sumber daya atau endpoint tidak ditemukan oleh server.
* **Kode Status HTTP:** `404 Not Found`
* **Isi Respons (Response Body):**
*(Respons menunjukkan data tidak ditemukan)*

---

### 3. Status Code: 500 (Internal Server Error)
* **URL Lengkap:** `https://httpbin.org/status/500`
* **Tujuan Endpoint:** Menguji respons kegagalan sistem di sisi server.
* **Kode Status HTTP:** `500 Internal Server Error`
* **Isi Respons (Response Body):**
*(Respons menunjukkan kendala pada server)*

---

## Pertanyaan Analisis & Evaluasi

### 1. Apa perbedaan makna kode `400` dan `404`? Berikan satu contoh keadaan untuk masing-masing kode.
* **Makna & Perbedaan:** 
  * Kode **400 (Bad Request)** berarti server memahami permintaan yang dikirimkan oleh klien, tetapi permintaan tersebut cacat, tidak valid, atau salah format dari segi struktur data. 
  * Sedangkan kode **404 (Not Found)** berarti server gagal menemukan alamat endpoint atau sumber daya yang diminta karena memang tidak ada di dalam sistem.
* **Contoh Keadaan:**
  * **400:** Mengirimkan *payload* body berformat JSON yang rusak atau tidak lengkap saat melakukan registrasi akun.
  * **404:** Mengakses URL endpoint yang salah atau sudah dihapus, misalnya `/api/v1/produks` padahal yang benar `/api/v1/produk`.

---

### 2. Apa perbedaan makna kode `401` dan `403` dalam pemeriksaan identitas dan hak akses pengguna?
* **Makna & Perbedaan:**
  * Kode **401 (Unauthorized)** berkaitan dengan **identitas/autentikasi**. Artinya, "Siapa Anda? Anda belum *login* atau token Anda tidak dikenal".
  * Kode **403 (Forbidden)** berkaitan dengan **hak akses/otorisasi**. Artinya, "Kami tahu siapa Anda, tetapi Anda tidak memiliki izin untuk membuka halaman ini".
* **Contoh Keadaan:**
  * **401:** Pengguna mencoba mengakses menu profil pribadi tanpa menyertakan token *Bearer* autentikasi di header.
  * **403:** Pengguna biasa (*regular user*) yang sudah *login* mencoba masuk ke halaman khusus admin (`/admin/dashboard`).

---

### 3. Mengapa `500` menunjukkan masalah pada sisi server?
* **Alasan:** Kode status dalam rentang 5xx (termasuk **500 Internal Server Error**) secara khusus dirancang untuk menginformasikan bahwa kesalahan murni berasal dari infrastruktur, database, atau kode program di dalam server itu sendiri, bukan karena kesalahan data yang dikirim oleh klien. Hal ini biasanya terjadi akibat *bug* coding, kegagalan koneksi database, atau kehabisan memori server saat memproses data.

---

### 4. Apakah setiap respons kesalahan HTTP menunjukkan kerusakan pada server? Jelaskan alasan Anda dengan memberikan contoh.
* **Jawaban:** **Tidak.** Respons kesalahan (*error*) tidak selalu berarti server mengalami kerusakan atau *crash*. Sebagian besar kesalahan dikategorikan sebagai kesalahan klien (kategori 4xx), di mana server berfungsi normal dan justru merespons dengan benar untuk memberi tahu klien bahwa ada yang keliru dengan permintaan yang mereka kirim.
* **Contoh:** Ketika klien meminta data produk dengan ID yang tidak ada di database dan server mengembalikan kode **404 Not Found**, server tidak rusak; server berjalan dengan sangat baik dan memang melaporkan bahwa data tersebut tidak ditemukan.

---

## Lampiran Tangkapan Layar Postman
* Screenshot Status 200: `assets/status-200.png`
* Screenshot Status 404: `assets/status-404.png`
* Screenshot Status 500: `assets/status-500.png`