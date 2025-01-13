# tes-rumah-web

## Link Deploy Aplikasi
https://dion-tes-rumahweb.netlify.app/

Aplikasi frontend sederhana yang menampilkan data pengguna menggunakan API `https://jsonplaceholder.typicode.com/users`. Aplikasi ini dibuat dengan Vue.js dan memiliki fitur daftar pengguna, detail pengguna, dan pencarian pengguna berdasarkan email.

## Fitur
1. Daftar Pengguna: Menampilkan daftar nama, email, dan alamat pengguna.
2. Detail Pengguna: Menampilkan detail lengkap pengguna ketika nama pengguna diklik.
3. Pencarian Pengguna: Fitur pencarian pengguna berdasarkan email.

## Teknologi yang Digunakan
- JavaScript
- Vue.js
- Axios (untuk mengambil data dari API)

## Panduan Instalasi dan Setup
### 1. Menginstal dependensi yang dibutuhkan
Buka terminal atau command prompt di direktori proyek dan jalankan perintah berikut:
```bash
npm install
```
### 2. Compile and Hot-Reload for Development
```sh
npm run dev
```

### 3. Compile and Minify for Production

```sh
npm run build
```

## Penjelasan Struktur Kode
/src
  /assets
  /components
    UserList.vue          # Komponen untuk menampilkan daftar pengguna
    UserDetail.vue        # Komponen untuk menampilkan detail pengguna
    SearchBar.vue         # Komponen untuk fitur pencarian pengguna berdasarkan email
  App.vue                 # Komponen utama aplikasi
  main.js                 # Titik masuk aplikasi

## Langkah untuk menjalankan Aplikasi
1. Ketika aplikasi sudah terbuka, maka akan muncul judul aplikasi User Management App, dalam halaman ini user dapat melihat semua daftar pengguna yang berisi (nama, email, dan alamat pengguna)
2. Ketika nama pengguna di klik, maka di bagian bawah list akan muncul detail lengkap pengguna
3. Ketika diarahkan ke search bar, pengguna dapat melakukan pencarian berdasarkan email dan akan menampilkan data lengkap sesuai dengan emailnya
