# Kalkulator Kurs USD IDR

Kalkulator sederhana untuk mengubah nominal invoice dari dollar (USD) ke rupiah (IDR), dan sebaliknya. Satu file HTML, tanpa build dan tanpa library. Hanya memakai font dari Google Fonts.

## Cara pakai

Buka `index.html` di browser, atau pasang di hosting statis seperti Netlify atau GitHub Pages.

- Isi nominal, hasil langsung muncul. Baris "Terbaca" di bawah kolom nominal menampilkan angka yang dibaca kalkulator, jadi salah titik atau koma langsung kelihatan. Format Indonesia (1.250,50) dan Inggris (1,250.50) sama-sama bisa dibaca.
- Tombol tukar membalik arah konversi dan memindahkan hasil ke kolom nominal.
- "Salin angka" menyalin angka polos untuk spreadsheet, "Salin dengan Rp" menyalin angka berformat.
- "Isi kurs manual" dipakai kalau invoice wajib memakai kurs tertentu, misalnya JISDOR Bank Indonesia atau kurs perusahaan. Kalau kolom kurs manual kosong atau salah, hasil tampil "-" dan tidak diam-diam memakai kurs otomatis.

## Sumber kurs

Kurs otomatis diambil dari API [Frankfurter](https://api.frankfurter.dev/v1/latest?base=USD&symbols=IDR). Isinya kurs referensi harian dari bank sentral Eropa, diperbarui sekali per hari kerja. Ini bukan kurs per detik dan belum tentu sama dengan kurs bank atau JISDOR.

Kalau sumber kurs tidak bisa dihubungi, halaman memakai kurs terakhir yang diketahui (konstanta `SNAP` di `index.html`) dan menandainya "Tidak live". Perbarui konstanta itu sesekali kalau perlu.

Catatan: beberapa tempat yang menampilkan halaman HTML di dalam sandbox (misalnya pratinjau artifact Claude) memblokir permintaan ke internet luar, sehingga kurs live tidak terambil di sana. Di browser biasa atau hosting statis, kurs live terambil.
