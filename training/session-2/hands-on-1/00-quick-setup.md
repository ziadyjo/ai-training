# Quick Setup: Hubungkan Miro ke Claude

Durasi ±8 menit. Connector adalah jalan Claude ke tool lain. Miro dihubungkan sekarang supaya Langkah 3 bisa langsung menggambar. Connector Google Docs dari Sesi 1 tetap dipakai untuk membaca BRD.

## Yang dikerjakan

1. Buka **Customize** di sidebar, lalu **Connectors**. Pastikan **Google Docs** masih berstatus Connected. Kalau tidak, klik **Connect** dan ulangi login Google.
2. Klik tab **Discover**, cari **Miro**, pilih yang berlabel **Connector** (by Miro), lalu klik **Connect**. Login ke akun Miro dan pilih team yang kamu pakai.
3. Buka halaman Miro di Connectors. Lihat daftar **Tool permissions**. Bawaannya **Needs approval**: Claude meminta izinmu sebelum menjalankan tool. Biarkan begitu.
4. Di Miro, buat satu board kosong bernama `Claude AI Training`. Salin link board dari tombol **Share**.
5. Uji koneksi dengan prompt di bawah. Claude boleh meminta izin: pilih **Allow once**.

Miro hanya bisa membuka board yang akunmu boleh akses. Paket Miro Free dibatasi 100 panggilan tool per hari, dan membaca board juga dihitung, jadi uji koneksi cukup sekali (satu uji memakai sekitar 2 panggilan). Kalau board berada di team lain, Claude tidak bisa membacanya.

## Prompt

Ganti dulu: `[LINK BOARD]`.

```
Baca board Miro ini dan sebutkan nama board dan isinya sekarang. Jangan menambah atau mengubah apa pun di board.

[LINK BOARD]
```

## Cek

Claude menyebut nama `Claude AI Training` dan menyatakan board masih kosong, dan kartu izin muncul sebelum tool Miro berjalan. Kalau Claude tidak menemukan board, lihat "Kalau bermasalah" di [README](README.md).

---

Berikutnya: [Langkah 1: Pasang flow-diagram dan siapkan BRD](01-setup-skill.md)
