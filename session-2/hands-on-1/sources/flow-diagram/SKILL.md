---
name: flow-diagram
description: Dipakai saat analis punya BRD (link Google Docs) dan ingin menyusun flow dari satu bagian atau satu fitur: aktor, langkah, keputusan, exception. Menghasilkan flow spec di chat, skor Cek mutu flow, dan instruksi gambar untuk Miro. Pakai juga saat analis menulis "buat flow", "user flow", "flowchart", atau "swimlane". Tidak dipakai untuk menyusun BRD atau mockup.
---

# Flow Diagram

Mengubah requirement di BRD menjadi flow spec yang bisa diperiksa, lalu menjadi instruksi gambar untuk Miro. Claude menyusun, analis menyetujui, baru digambar.

## Input
- Link BRD di Google Docs, dibaca lewat connector. Kalau link tidak terbaca, minta analis menempel bagian BRD yang dimaksud.
- Satu flow: nama flow atau bagian BRD yang dimaksud (mis. "Login"). Bukan seluruh BRD. Kalau analis belum menyebut, tanya sekali dan sarankan dua kandidat dari BRD.

Kalau bagian BRD tidak memuat alur atau kondisi gagal, sebutkan celahnya sebagai pertanyaan. Jangan melengkapinya sendiri.

## Langkah kerja
1. **Minta masukan.** Kalau dipanggil tanpa isi, minta link BRD, lalu nama flow, satu per satu.
2. **Aktor.** Daftar pihak yang bertindak, dengan nama persis seperti di BRD.
3. **Aktivitas.** Urutkan langkah dari pemicu sampai hasil akhir. Ambil hanya dari requirement bagian itu.
4. **Keputusan dan cabang.** Tiap keputusan punya dua cabang atau lebih, masing-masing berlabel.
5. **Exception.** Ambil dari requirement kondisi gagal: input salah, akses ditolak, data kosong, status tidak aktif.
6. **Flow spec.** Tulis sebagai tabel (format di bawah).
7. **Cek mutu flow.** Nilai flow spec dengan enam pemeriksaan di bawah, tulis hasilnya sebagai "N dari 6".
8. **Instruksi gambar** untuk Miro: jenis diagram (flowchart atau swimlane), satu lane per aktor, bentuk per jenis langkah, label cabang, urutan. Format portrait (alur dari atas ke bawah), lebar frame maksimal 1500 unit, font kotak minimal 24, supaya terbaca saat diekspor ke BRD selebar halaman. Bila flow tidak muat, pecah jadi dua frame.
9. **Berhenti dan minta persetujuan.** Tidak ada yang dibuat di Miro sebelum analis menyetujui flow spec.
10. **Setelah disetujui:** gambar di Miro lewat connector, di board yang disebut analis. Kalau analis belum menyebut board, minta nama board. Jangan memakai board lain.
11. **Tautkan ke BRD** (hanya bila diminta analis). Di salinan BRD milik analis, tambahkan dua baris di bawah isi bagian 6 (Proposed Business Process), tanpa mengubah isi lain:
    Diagram flow: [Judul flow](link board Miro)
    Tempel gambar diagram di bawah baris ini (Insert > Image).
    Tulis link sebagai hyperlink.

## Cek mutu flow
Enam pemeriksaan tetap, sama di setiap versi:
1. **Aktor:** semua aktor yang disebut bagian BRD muncul, dengan nama persis.
2. **Titik awal dan akhir:** ada satu Mulai dan minimal satu Akhir, tidak ada langkah buntu.
3. **Cabang:** tiap Keputusan punya dua cabang atau lebih, masing-masing berlabel.
4. **Exception:** kondisi gagal yang disebut BRD punya langkah sendiri.
5. **Rujukan:** setiap langkah menyebut ID requirement atau ditandai "tanpa rujukan", dan tidak ada ID requirement yang relevan dengan flow terlewat.
6. **TBC:** hal yang di BRD masih TBC ditulis sebagai TBC, bukan diisi cabang karangan.

Tulis tabel Pemeriksaan, Hasil (lulus atau gagal), dan Alasan satu kalimat. Hasil gagal wajib menyebut langkah atau ID yang bermasalah.

## Aturan dan validasi
- Draft di chat dulu. Gambar dibuat di Miro hanya setelah analis menyetujui flow spec.
- Jangan menambah langkah, keputusan, atau aktor yang tidak ada di BRD. Kalau perlu, tulis sebagai pertanyaan.
- Satu flow, satu tujuan. Kalau ada dua tujuan, pecah jadi dua flow.
- Tiap keputusan punya cabang untuk semua kondisi yang disebut BRD. Kondisi yang tidak disebut ditulis TBC.
- Menulis ke Google Docs hanya setelah persetujuan, hanya ke salinan milik analis, dan hanya menambah dua baris di langkah 11.
- Bahasa Indonesia; istilah teknis tetap Inggris.

## Format output
Flow spec:

| No | Aktor | Langkah | Jenis | Lanjut ke | Rujukan ID |
|---|---|---|---|---|---|

Jenis: Mulai, Proses, Keputusan, Akhir. Kolom "Lanjut ke" berisi nomor langkah, dan untuk Keputusan berisi label cabang dan nomor tujuannya.

Setelah tabel, berurutan: Cek mutu flow, daftar exception, daftar pertanyaan atau TBC, lalu instruksi gambar untuk Miro.

## Contoh singkat
Input: bagian BRD tentang reset password.

| No | Aktor | Langkah | Jenis | Lanjut ke | Rujukan ID |
|---|---|---|---|---|---|
| 1 | User | Memilih "Lupa password" | Mulai | 2 | RP-001 |
| 2 | Sistem | Memeriksa apakah akun terdaftar | Keputusan | Ya: 3, Tidak: 5 | RP-001 |
| 3 | Sistem | Mengirim link reset | Proses | 4 | RP-002 |
| 4 | User | Membuka link dan mengisi password baru | Akhir | - | RP-003 |
| 5 | Sistem | Menampilkan pesan generik tanpa membocorkan status akun | Akhir | - | tanpa rujukan |

Pertanyaan: langkah 5 tanpa rujukan. Tanyakan apakah perilaku ini memang diminta.

## Self-check sebelum menjawab
- Semua langkah dan keputusan berasal dari BRD atau ditandai pertanyaan?
- Setiap ID requirement yang relevan dengan flow muncul di tabel?
- Setiap keputusan punya cabang berlabel?
- Cek mutu flow ditulis dengan alasan, bukan hanya angka?
- Analis sudah menyetujui spec sebelum apa pun dikirim ke Miro?
