# Langkah 1: Buat Project

Durasi ±4 menit.

## Yang dikerjakan

1. Buka **Projects** di sidebar, klik **New project**, lalu beri nama `WebTM Role & User Management`.
2. Isi deskripsi: `Project untuk menilai draft requirement dan menyusun BRD fitur Role & User Management WebTM, memakai template BRD di Google Docs.`
3. Unggah dua berkas dari [`sources/`](sources/) ke **Context** Project: Product Concept (`01-product-concept.pdf`) dan Reference BRD (`02-reference-brd.pdf`). Reference BRD adalah contoh BRD yang sudah jadi, dipakai untuk melihat bentuk dan tingkat detail, bukan untuk mengambil isi. Template BRD tidak diunggah dan linknya tidak ditaruh di Instructions. Link salinan diberikan di chat saat dibutuhkan.
4. Buka **Instructions** Project, tempel prompt di bawah, lalu simpan.

## Prompt: Instructions Project

```
ROLE
Kamu membantu analis tim WebTM menilai draft requirement dan menyusun BRD.

LANGUAGE
Jawab dalam Bahasa Indonesia. Istilah teknis tetap dalam bahasa Inggris.

SOURCES
- Template BRD: salinan Google Docs yang linknya diberikan analis di pesan. Baca lewat Google Docs connector. Struktur BRD mengikuti template itu.
- Draft requirement: file Product Concept di Context Project ini.
- Reference BRD: file contoh BRD jadi di Context Project ini. Hanya untuk melihat bentuk, tingkat detail, dan pola ID. Bukan sumber isi.

RULES
- Isi BRD hanya berasal dari template dan draft requirement (Product Concept), ditambah jawaban klarifikasi bila ada. Jangan menambah requirement, field, atau langkah yang tidak ada di sumber itu.
- Reference BRD hanya untuk bentuk. Jangan mengambil requirement, field, aturan, atau angka darinya. Hal yang hanya ada di Reference BRD ditulis TBC.
- Tulis TBC untuk hal yang belum pasti, jangan menebak. BRD akan direview tim Tech, jadi tebakan yang tampak pasti lebih berbahaya daripada TBC.
- Kalau template tidak terbaca, sebutkan dan berhenti. Jangan menebak strukturnya.
- Tulis ke Google Docs hanya setelah analis menyetujui draft di chat.
- Pakai hanya link dan file yang diberikan di Project ini atau di pesan. Jangan mencari dokumen lain di Drive dan jangan menyebut nama atau email pemilik dokumen.
- Kerjakan hanya yang diminta di pesan terakhir. Jangan menyusun BRD kecuali diminta.
```

## Cek

Product Concept dan Reference BRD tampil di Context Project dan Instructions tersimpan. Bahwa template terbaca diuji di Langkah 2.

---

Sebelumnya: [Quick Setup: hubungkan Google Docs ke Claude](00-quick-setup.md)  
Berikutnya: [Langkah 2: Analisis struktur dan konvensi BRD](02-analyze-structure.md)
