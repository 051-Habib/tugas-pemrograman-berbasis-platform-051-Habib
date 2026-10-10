# Laporan Analisis Perbandingan CSS: Komponen vs Utility-First

Laporan ini membandingkan dua pendekatan penataan tampilan kartu biodata menggunakan pendekatan berbasis komponen (CSS kustom) dan berbasis utility-first (Tailwind CSS).

---

## 📊 Hasil Pengamatan & Data Kuantitatif

* **Jumlah Baris CSS (Versi Komponen):** Terdapat **53 baris kode CSS** di dalam tag `<style>` untuk mendefinisikan aturan `.card`, `.card-img`, `.card-title`, `.card-text`, dan `.btn`.
* **Jumlah Class Utility (Versi Utility-First):** Terdapat **28 class utility Tailwind** yang digunakan secara langsung pada elemen HTML.

---

## ⏱️ Analisis Pengerjaan & Kemudaan

1. **Waktu Pengerjaan:**
   * **Utility-First (Tailwind):** Lebih cepat dikerjakan karena tidak perlu bolak-balik berfikir menentukan nama class baru (seperti `.card-title`) dan berpindah antar file/tag CSS.
   * **Komponen:** Membutuhkan waktu lebih lama untuk menulis selektor dan sintaks CSS lengkap dari awal.

2. **Kemudahan Perubahan Tema (Warna):**
   * **Versi Komponen:** Lebih mudah dan terpusat saat ingin mengubah warna seluruh kartu yang ada di proyek. Mengubah properti `background-color` pada aturan `.card` akan otomatis mengubah semua kartu yang menggunakan class tersebut secara sekaligus.
   * **Versi Utility-First:** Sangat cepat untuk mengubah warna satu elemen tertentu secara spesifik langsung di HTML, namun jika ada banyak kartu, harus mengganti class warna pada setiap elemen satu per satu (kecuali jika dimanfaatkannya komponen abstraksi).

3. **Pilihan Pendekatan untuk Proyek Akhir:**
   * Saya memilih **pendekatan Utility-First (Tailwind CSS)** untuk pembuatan halaman antarmuka utama (seperti Dashboard dan Landing Page) karena mempercepat proses pembuatan tata letak dan konsistensi sistem desain (*spacing*, *typography*, dan *color palette*).
   * Namun untuk elemen dasar yang sangat sering diulang (seperti Tombol Utama atau Kartu Produk), saya akan menggabungkannya dengan **pendekatan berbasis komponen** agar pemeliharaan kode (*maintenance*) tetap efisien.

---

## 📸 Tangkapan Layar (Screenshot)

*(Sertakan screenshot pengujian di sini)*
- `[Screenshot Tampilan Laptop - Versi Komponen]`
- `[Screenshot Tampilan Mobile 360px - Versi Komponen]`
- `[Screenshot Tampilan Laptop - Versi Utility]`
- `[Screenshot Tampilan Mobile 360px - Versi Utility]`