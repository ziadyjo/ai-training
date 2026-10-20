# Langkah 1: Pasang ui-brief dan siapkan referensi

Durasi ±8 menit. `ui-brief` sudah jadi, jadi kamu menyalinnya, bukan membangunnya. Skill ini menyusun brief UI dan prompt desain, dan tidak menulis ke Google Docs.

## Yang dikerjakan

1. Buka **Customize** di sidebar, tab **Skills**, klik **+ Add**, pilih **Create a skill**.
2. Isi **Skill name** dengan `ui-brief`.
3. Isi **Description** dengan teks di bagian "Description" di bawah.
4. Tempel teks di bagian "Instruksi Skill" ke editor instruksi, lalu klik **Create**. Skill ini tidak butuh berkas referensi.
5. Buka Project **WebTM Role & User Management** dan mulai chat baru.
6. Siapkan dua referensi: link BRD-mu dan flow spec Create New Role dari Hands-on #1 (salin tabelnya dari chat Langkah 4, atau minta flow spec acuan ke instruktur).
7. Cek dua hal untuk Langkah 3: Claude Code sudah terpasang (`claude --version` di terminal) dan kamu bisa login ke [Google Stitch](https://stitch.withgoogle.com) dengan akun Google.

Tertinggal? BRD acuan ada di [`../../session-1/hands-on-3/sources/brd-v1-1-checkpoint.md`](../../session-1/hands-on-3/sources/brd-v1-1-checkpoint.md). Lampirkan ke chat dan sebut "BRD terlampir" setiap prompt meminta link BRD.

## Description

```
Dipakai saat BRD dan flow sudah ada dan analis perlu brief UI: daftar screen, tujuan dan aksi tiap screen, komponen, serta state (kosong, loading, error, sukses) sebelum membuat mockup di Google Stitch, Claude Design, atau Figma. Menghasilkan brief, skor Cek mutu brief, dan prompt siap tempel. Pakai juga saat analis menulis "buat brief UI", "rancang screen", atau "siapkan mockup".
```

## Instruksi Skill

````
# UI Brief

Mengubah requirement dan flow menjadi brief yang jelas untuk alat desain. Claude menyusun brief, analis menyetujui, baru mockup dibuat.

## Input
- Link BRD di Google Docs, dibaca lewat connector, terutama bagian Requirement. Kalau link tidak terbaca, minta analis menempel bagian yang dimaksud.
- Flow: flow spec dari `flow-diagram` di percakapan atau Project, atau link board Miro. Kalau flow tidak ada, sebutkan dan minta. Jangan menebak urutan screen.
- Opsional: design system atau panduan UI (berkas, link, atau screenshot halaman yang sudah ada).

## Langkah kerja
1. **Minta masukan.** Kalau dipanggil tanpa isi, minta link BRD, lalu flow yang dipakai, satu per satu.
2. **Tanya referensi gaya.** Tanyakan satu hal: "Ada design system atau panduan UI? Lampirkan, tempel link, atau jawab tidak ada." Kalau ada, baca hanya yang disebut analis dan catat sebagai sumber gaya. Kalau tidak ada, tulis gaya sebagai "ikuti gaya produk yang sudah ada" dan jangan mengarang warna, font, atau komponen. Lewati pertanyaan ini bila referensi sudah diberikan.
3. **Screen.** Dari flow, daftar setiap langkah yang punya antarmuka. Satu langkah, satu screen. Tambahkan screen dari requirement yang terhubung langsung ke flow (mis. halaman yang dibuka dari daftar) dan tandai "di luar flow".
4. **Tujuan dan aksi.** Tiap screen: apa yang ingin dicapai pengguna dan aksi yang tersedia.
5. **Komponen dan data.** Field, tombol, pesan, dan data yang tampil, ditarik dari requirement.
6. **State.** Normal, kosong, loading, error, sukses, dan akses ditolak bila relevan.
7. **Rujukan.** Hubungkan tiap screen ke ID requirement. Screen tanpa ID ditandai.
8. **Pilih 3 sampai 4 screen inti** untuk mockup pertama. Sisanya disebut sebagai lanjutan.
9. **Cek mutu brief.** Nilai brief dengan enam pemeriksaan di bawah, tulis hasilnya sebagai "N dari 6".
10. **Prompt desain** untuk alat yang dipilih analis (format di bawah).
11. **Berhenti dan minta persetujuan** sebelum prompt dipakai.

## Cek mutu brief
Enam pemeriksaan tetap, sama di setiap versi:
1. **Asal screen:** setiap screen berasal dari satu langkah di flow, atau ditandai "di luar flow" dengan ID requirement yang mendasarinya.
2. **Tujuan dan aksi:** setiap screen punya tujuan dan minimal satu aksi.
3. **State:** screen yang butuh state kosong, loading, atau error menyebutnya.
4. **Rujukan:** setiap screen tertaut ke ID requirement, dan screen tanpa ID ditandai.
5. **Tanpa karangan:** tidak ada field, komponen, atau aksi di luar requirement. Yang belum pasti ditulis sebagai pertanyaan.
6. **Prompt:** prompt desain menyebut platform dan gaya, dan melarang fitur tambahan.

Tulis tabel Pemeriksaan, Hasil (lulus atau gagal), dan Alasan satu kalimat. Hasil gagal wajib menyebut screen atau ID yang bermasalah.

## Aturan dan validasi
- Jangan menambah field, komponen, atau aksi yang tidak ada di requirement. Kalau perlu, tulis sebagai pertanyaan.
- Teks antarmuka memakai bahasa produk, bukan bahasa dokumen ini.
- Jangan menyebut kemampuan alat desain yang belum dipastikan analis. Prompt ditulis netral dan bisa ditempel ke alat apa pun.
- Sebut platform (desktop, mobile, atau keduanya) dan konteks pengguna di setiap prompt.
- Referensi gaya hanya dari yang diberikan analis. Screenshot dibaca sebagai sumber: sebutkan yang terlihat, jangan menafsirkan di luar itu.
- Tidak menulis ke Google Docs. Skill ini hanya menyusun brief.
- Bahasa Indonesia; istilah teknis tetap Inggris.

## Format output
Tabel screen:

| No | Screen | Tujuan | Aksi | Komponen dan data | State | Rujukan ID |
|---|---|---|---|---|---|---|

Setelah tabel, berurutan: Cek mutu brief, daftar pertanyaan, lalu prompt desain, satu blok per alat:

    Rancang [jumlah] screen untuk [platform], untuk [pengguna].
    Konteks: [satu kalimat]
    Screen: [daftar nama screen dan tujuan]
    Komponen dan state per screen: [ringkas dari tabel]
    Gaya: [referensi, atau "ikuti gaya produk yang sudah ada"]
    Jangan menambah fitur di luar daftar ini.

## Contoh singkat
Input: flow reset password, lima langkah.

| No | Screen | Tujuan | Aksi | Komponen dan data | State | Rujukan ID |
|---|---|---|---|---|---|---|
| 1 | Minta reset | User meminta link reset | Kirim | Field email, tombol Kirim | Normal, error format email | RP-001 |
| 2 | Link terkirim | User tahu langkah berikutnya | Kembali ke login | Pesan konfirmasi | Normal | RP-002 |
| 3 | Password baru | User mengisi password baru | Simpan | Dua field password, aturan password | Normal, error aturan, loading | RP-003 |
| 4 | Link tidak berlaku | User tahu link kedaluwarsa | Minta link baru | Pesan, tombol | Error | RP-004 |

## Self-check sebelum menjawab
- Setiap screen berasal dari langkah di flow, atau ditandai "di luar flow" dengan ID requirement?
- Ada field atau aksi yang tidak punya requirement? Kalau ada, hapus atau jadikan pertanyaan.
- State error dan kosong disebut untuk screen yang membutuhkannya?
- Prompt menyebut platform dan melarang fitur tambahan?
- Gaya berasal dari referensi analis, atau ditulis "ikuti gaya produk yang sudah ada"?
- Cek mutu brief ditulis dengan alasan, bukan hanya angka?
````

## Cek

Skill `ui-brief` muncul di daftar Skill dan saat mengetik `/ui` di chat. Kamu punya link BRD (atau BRD terlampir), flow spec, Claude Code yang terpasang, dan akun Stitch yang bisa login.

---

Berikutnya: [Langkah 2: Jalankan ui-brief](02-run-ui-brief.md)
