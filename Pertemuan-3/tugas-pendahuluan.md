##  Soal 1 — Bandingkan Bootstrap dan Tailwind

## Class utama kartu dan tombol:

- Pada Bootstrap (pendekatan berbasis komponen), class yang sering digunakan untuk kartu adalah card, card-body, sedangkan untuk tombol adalah btn dan btn-primary.

- Pada Tailwind CSS (pendekatan berbasis utility), class yang digunakan berupa kumpulan utilitas mentah seperti bg-white rounded-lg shadow-md p-4 untuk kartu, serta bg-blue-500 text-white px-4 py-2 rounded untuk tombol.

   Pendekatan yang lebih mudah bagi pemula: Menurut saya, Bootstrap lebih mudah digunakan oleh pemula karena menyediakan komponen yang sudah jadi (class="card") tanpa harus merangkai banyak utility class satu per satu dari awal.

Soal 2 — Rancang Satu Kartu Biodata dengan Dua Pendekatan

## Struktur HTML Versi Komponen (Bootstrap):
```html
<div class="card" style="width: 18rem;">
  <img src="foto.jpg" class="card-img-top" alt="Foto Profil">
  <div class="card-body">
    <h5 class="card-title">Habib</h5>
    <p class="card-text">NIM: 051</p>
    <a href="#" class="btn btn-primary">Profil</a>
  </div>
</div>
```

## Struktur HTML Versi Utility (Tailwind):
```html
<div class="max-w-sm rounded overflow-hidden shadow-lg p-4 bg-white">
  <img class="w-full h-auto rounded" src="foto.jpg" alt="Foto Profil">
  <div class="px-6 py-4">
    <div class="font-bold text-xl mb-2">Habib</div>
    <p class="text-gray-700 text-base">NIM: 051</p>
    <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Profil</button>
  </div>
</div>
```
## Jumlah aturan CSS / class:
- Versi komponen memiliki jumlah class yang sedikit karena dibungkus dalam satu nama komponen (sekitar 6 class utama).

- Versi utility memerlukan jumlah class yang jauh lebih banyak langsung di dalam elemen HTML (sekitar 12+ utility class).

   Kemudahan mengubah warna: Versi utility lebih mudah diubah warnanya secara spesifik langsung pada elemen tanpa perlu menimpa file CSS eksternal.

## Soal 3 — Amati Isi Token (JWT)

- Jumlah bagian token: Terdiri dari 3 bagian yang dipisahkan oleh titik (.), yaitu Header, Payload, dan Signature.

- Data pada payload: Berisi informasi klaim seperti data subjek (sub), waktu penerbitan (iat), serta identitas pengguna.

- Alasan password tidak boleh disimpan di payload: Payload JWT hanya di-encode (bukan dienkripsi total menggunakan enkripsi dua arah yang aman dari pembacaan), sehingga siapa pun yang memegang token dapat mendekode base64-nya dan membaca password secara mentah jika disimpan di dalam payload.

## Soal 4 — Analogi Gerbang Kampus

- Authentication vs Authorization: Pemeriksaan kartu identitas atau KTM di gerbang depan kampus sebagai bukti bahwa Anda adalah warga kampus yang sah merupakan contoh authentication. Pemeriksaan khusus di depan pintu masuk ruang server laboratorium untuk memastikan apakah akun Anda memiliki hak akses masuk ke ruangan tersebut merupakan contoh authorization.

- Contoh kondisi: Seseorang berhasil menunjukkan kartu identitas mahasiswa yang valid (lolos authentication), tetapi satpam tetap melarangnya masuk ke ruang server karena mahasiswa tersebut tidak memiliki hak akses atau izin khusus untuk ruangan server tersebut##.

## Soal 5 — Peran di Aplikasi Nyata (Contoh: GitHub)

   Tiga Peran (Role): Owner, Collaborator/Developer, dan Viewer.

   Fitur khusus peran tertentu: Fitur untuk menghapus repositori (Delete Repository) atau mengatur akses kolaborator hanya boleh digunakan oleh peran Owner.

   Respons untuk dua keadaan:

- Pengguna belum login lalu mengakses halaman privat akan menghasilkan respons 401 Unauthorized karena sistem belum mengenali identitas pengguna.

- Pengguna sudah login (dikenali identitasnya) tetapi mencoba mengakses halaman kelola repo yang bukan haknya akan menghasilkan respons 403 Forbidden karena pengguna tidak memiliki izin akses (authorization).

