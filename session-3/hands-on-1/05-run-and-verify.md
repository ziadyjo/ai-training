# Langkah 5: Jalankan dan verifikasi

Durasi ±15 menit. Kamu tidak menilai prototype dari tampilannya, tetapi dari enam pemeriksaan tetap. Driver mengklik, reviewer membaca daftarnya dan mencatat.

## Yang dikerjakan

1. Buka `index.html` di Browser pane tab Code, atau klik dua kali berkasnya di folder untuk membuka di Chrome.
2. Jalankan alur utama: Daftar Role, Create New Role, isi "QA Reviewer", Submit, lihat role baru di tabel.
3. Coba tiga jalur gagal: Submit dengan Role Name kosong, dengan nama role Active yang ada (mis. "Staff"), dan dengan nama role Inactive yang ada (mis. "Auditor").
4. Kirim Prompt pertama. Claude membuat tabel elemen dan dasarnya.
5. Kirim Prompt kedua bila halaman kosong atau ada yang tidak berfungsi.
6. Isi **Cek mutu prototype** (6 pemeriksaan di [README](README.md#cek-mutu-prototype)) di [scorecard](../scorecard.md) baris v1, lengkap dengan jumlah elemen dikarang dan hal yang kurang.
7. Pilih satu temuan paling penting untuk Langkah 6.

## Prompt: elemen dan dasarnya

```
CONTEXT
index.html di folder ini adalah prototype WebTM Role Management.

TASK
Baca index.html dan buat tabel elemen beserta dasarnya.

RULES
- Kolom: elemen, ID requirement di komentar, sumber tampilan (desain atau tidak ada), dan status (ada dasar di BRD, hanya di desain, atau tidak ada dasar).
- Tandai elemen tanpa dasar.
- Jangan mengubah berkas.

OUTPUT FORMAT
Satu tabel, lalu daftar elemen tanpa dasar.
```

## Prompt: periksa galat

```
CONTEXT
index.html di folder ini adalah prototype WebTM Role Management.

TASK
Buka index.html di Browser pane dan periksa apakah ada galat saat halaman dibuka dan saat Submit diklik.

RULES
- Laporkan galat dan penyebabnya.
- Jangan mengubah berkas.

OUTPUT FORMAT
Daftar galat: kejadian dan penyebab. Bila tidak ada, tulis "tidak ada galat".
```

## Cek

- Alur utama berjalan dari awal sampai tabel menampilkan role baru.
- Ketiga jalur gagal menampilkan pesan dan role tidak bertambah. Bila nama role Inactive tetap diterima, itu temuan (RM-004 menyebut Active maupun Inactive).
- Claude tidak melaporkan galat di halaman.
- Elemen tanpa dasar teridentifikasi dari tabel Claude, bukan dari tebakanmu.
- Scorecard v1 terisi.

---

Sebelumnya: [Langkah 4: Bangun alur utama](04-build-main-flow.md)  
Berikutnya: [Langkah 6: Iterasi dan simpan](06-iterate-and-save.md)
