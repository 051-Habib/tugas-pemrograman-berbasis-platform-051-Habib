##  Tugas Mandiri 1 — Mengenal HTTP Method dan Endpoint

### Rangkuman Hasil Pengujian HTTPBin

| No | Method | Endpoint | Data yang dikirim | Status | Hasil |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1** | GET | `/get` | Query parameter (`?nama=Habib&nim=051`) | `200 OK` | Berhasil mengembalikan data parameter pada bagian `args`. |
| **2** | POST | `/post` | JSON/body (`{"nama": "Habib", "role": "Backend"}`) | `200 OK` | Berhasil merekam data yang dikirim pada bagian `json`. |
| **3** | PUT | `/put` | JSON/body (`{"status": "update"}`) | `200 OK` | Berhasil memperbarui seluruh data melalui body request. |
| **4** | PATCH | `/patch` | JSON/body (`{"role": "BE Enthusiast"}`) | `200 OK` | Berhasil memperbarui sebagian data melalui body request. |
| **5** | DELETE | `/delete` | `-` | `200 OK` | Berhasil memproses permintaan penghapusan data. |

### Detail Pengujian, URL Lengkap, dan Isi Respons (Response Body)

### 1. HTTP Method: GET
* **URL Lengkap:** `[https://httpbin.org/get?nama=Habib&nim=051](https://httpbin.org/get?nama=Habib&nim=051)`
* **Tujuan Endpoint:** Menguji request GET untuk mengambil atau membaca data dari server menggunakan tambahan Query Parameter.
* **Data yang Dikirim:** `nama=Habib`, `nim=051` (melalui URL/Query String)
* **Kode Status HTTP:** `200 OK`
* **Isi Respons (Response Body):**
```json
{
  "args": {
    "nama": "Habib",
    "nim": "051"
  },
  "headers": {
    "Accept": "*/*",
    "Host": "httpbin.org",
    "User-Agent": "PostmanRuntime/7.x.x"
  },
  "origin": "xxx.xxx.xxx.xxx",
  "url": "https://httpbin.org/get?nama=Habib&nim=051"
}
```
* **Penjelasan Respons Server:** Server HTTPBin menampilkan kembali parameter yang dikirim melalui URL di dalam objek `args`, lengkap dengan informasi `headers` dan alamat IP asal (`origin`).

---

### 2. HTTP Method: POST
* **URL Lengkap:** `[https://httpbin.org/post](https://httpbin.org/post)`
* **Tujuan Endpoint:** Menguji request POST untuk mengirim data baru ke server melalui Request Body (format JSON).
* **Data yang Dikirim (JSON Body):**
```json
{
  "nama": "Habib",
  "role": "Backend Enthusiast"
}
```
* **Kode Status HTTP:** `200 OK`
* **Isi Respons (Response Body):**
```json
{
  "args": {},
  "data": "{\"nama\": \"Habib\", \"role\": \"Backend Enthusiast\"}",
  "files": {},
  "form": {},
  "json": {
    "nama": "Habib",
    "role": "Backend Enthusiast"
  },
  "headers": {
    "Content-Type": "application/json",
    "Host": "httpbin.org"
  },
  "origin": "xxx.xxx.xxx.xxx",
  "url": "https://httpbin.org/post"
}
```
* **Penjelasan Respons Server:** Server menerima payload berformat JSON dan meresponnya dengan menampilkan kembali data tersebut pada bagian properti `json` serta `data`.

---

### 3. HTTP Method: PUT
* **URL Lengkap:** `[https://httpbin.org/put](https://httpbin.org/put)`
* **Tujuan Endpoint:** Menguji request PUT untuk mengganti atau memperbarui keseluruhan data pada server.
* **Data yang Dikirim (JSON Body):**
```json
{
  "id": 1,
  "status": "updated-full"
}
```
* **Kode Status HTTP:** `200 OK`
* **Isi Respons (Response Body):**
```json
{
  "args": {},
  "data": "{\"id\": 1, \"status\": \"updated-full\"}",
  "files": {},
  "form": {},
  "json": {
    "id": 1,
    "status": "updated-full"
  },
  "headers": {},
  "origin": "xxx.xxx.xxx.xxx",
  "url": "https://httpbin.org/put"
}
```
* **Penjelasan Respons Server:** Server mencatat data pengganti yang dikirimkan melalui body dan mengembalikannya secara utuh di dalam objek `json`.

---

### 4. HTTP Method: PATCH
* **URL Lengkap:** `[https://httpbin.org/patch](https://httpbin.org/patch)`
* **Tujuan Endpoint:** Menguji request PATCH untuk memperbarui sebagian (partial update) data di server.
* **Data yang Dikirim (JSON Body):**
```json
{
  "role": "Updated Backend Developer"
}
```
* **Kode Status HTTP:** `200 OK`
* **Isi Respons (Response Body):**
```json
{
  "args": {},
  "data": "{\"role\": \"Updated Backend Developer\"}",
  "files": {},
  "form": {},
  "json": {
    "role": "Updated Backend Developer"
  },
  "headers": {},
  "origin": "xxx.xxx.xxx.xxx",
  "url": "https://httpbin.org/patch"
}
```
* **Penjelasan Respons Server:** Server mengonfirmasi pembaruan parsial dengan mengembalikan data bagian field yang dikirimkan pada payload.

---

### 5. HTTP Method: DELETE
* **URL Lengkap:** `[https://httpbin.org/delete](https://httpbin.org/delete)`
* **Tujuan Endpoint:** Menguji request DELETE untuk menghapus sumber data tertentu pada server.
* **Data yang Dikirim:** `-` (Tidak memerlukan body data khusus)
* **Kode Status HTTP:** `200 OK`
* **Isi Respons (Response Body):**
```json
{
  "args": {},
  "data": "",
  "files": {},
  "form": {},
  "json": null,
  "headers": {
    "Host": "httpbin.org"
  },
  "origin": "xxx.xxx.xxx.xxx",
  "url": "https://httpbin.org/delete"
}
```
* **Penjelasan Respons Server:** Server memproses perintah hapus dan mengembalikan konfirmasi URL beserta informasi header bahwa permintaan hapus telah diterima.

---

### Lampiran 

- Screenshot GET: `assets/get.png`
- Screenshot POST: `assets/post.png`







