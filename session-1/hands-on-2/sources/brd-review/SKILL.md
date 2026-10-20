---
name: brd-review
description: Dipakai untuk memeriksa BRD hasil brd-draft: membandingkan isi BRD dengan template dan sumbernya (Product Concept, jawaban klarifikasi), lalu melaporkan gap (terpenuhi, hilang, ambigu, konflik, belum lengkap) beserta clarification question. Bisa juga untuk draft requirement mentah. Pakai juga saat analis menulis "review BRD", "cek BRD", atau "gap analysis". Hanya melaporkan.
---

# BRD Review

Memeriksa BRD (biasanya hasil `brd-draft`) terhadap template dan sumbernya, lalu melaporkan temuan. Bisa juga memeriksa draft requirement mentah. Claude melaporkan, analis memutuskan perbaikannya.

## Input
- Yang direview: link BRD di Google Docs, dibaca lewat connector. Kalau belum ada BRD, draft requirement (di Context Project, lampiran, atau ditempel).
- Sumber pembanding untuk BRD: draft requirement di Context Project (mis. Product Concept), jawaban klarifikasi, dan tabel sumber dari `brd-draft`, bila ada. Reference BRD (contoh BRD jadi) di Context bukan sumber pembanding isi; pakai hanya untuk membandingkan bentuk dan konvensi bila analis memintanya.
- Template BRD: struktur ada di `references/brd-structure.md`; pakai berkas itu. Jangan meminta link template.

Kalau link BRD tidak terbaca atau tidak ada draft sebagai pembanding, sebutkan dan berhenti. Kalau `references/brd-structure.md` tidak ada, sebutkan dan berhenti.

## Langkah kerja
1. **Tentukan yang direview**, tanpa bertanya bila bisa disimpulkan:
   - Pesan memuat link BRD: itu BRD jadi. Pembandingnya draft requirement di Context; kalau berkasnya lebih dari satu (Reference BRD tidak dihitung), tanya sekali mana yang dimaksud.
   - Pesan menyebut draft requirement (teks, berkas, atau lampiran) tanpa link BRD: review draft itu.
   - Dipanggil tanpa isi: cetak banner Opening display, lalu minta link BRD dengan kalimat di Opening display.
   Pesan boleh menambah fokus (mis. "fokus bagian 7"); ikuti, dan tetap pakai Kriteria review yang sama.
2. **BRD jadi:** baca BRD dan sumber pembandingnya. Untuk setiap bagian BRD, periksa:
   - struktur terhadap template: bagian, urutan, kolom, dan format ID PREFIX-001;
   - isi BRD yang tidak punya dasar di sumber atau bertentangan dengan sumber;
   - informasi di sumber yang belum masuk BRD;
   - TBC yang masih terbuka, kata tanpa ukuran, dan istilah yang berubah-ubah;
   - jawaban klarifikasi yang belum tercermin, bila diberikan.
   Nilai setiap temuan dengan Kriteria review. Tulis satu clarification question per gap.
3. **Draft requirement:** baca seluruh draft dan template. Untuk setiap bagian template, nilai informasi di draft dengan Kriteria review. Tulis satu clarification question per gap.
4. Laporkan dalam Format output. Jangan menulis apa pun ke Google Docs.

## Kriteria review
- **Terpenuhi**: informasi ada, cukup, dan (untuk BRD) tercermin benar di BRD.
- **Hilang**: bagian template butuh informasi, tetapi tidak ada di draft; atau ada di sumber tetapi belum masuk BRD. Contoh: Definition of Success, Out of Scope.
- **Ambigu**: kalimat bisa dibaca lebih dari satu cara, atau memakai kata tanpa ukuran seperti "segera", "berkala", "real-time atau batch".
- **Konflik**: dua bagian saling bertentangan, atau isi BRD tidak punya dasar di sumber atau bertentangan dengan sumber.
- **Belum lengkap**: topik disebut tetapi detailnya kurang, termasuk yang ditandai TBC, "Perlu Konfirmasi", atau tbd. Untuk BRD, TBC yang memang sudah ditandai di BRD digabung menjadi satu temuan per bagian (sebut ID-nya dalam satu baris) dengan satu pertanyaan, kecuali TBC itu bertentangan dengan sumber.

Aturan clarification question:
- Satu gap, satu pertanyaan.
- Pertanyaan tertutup: jawabannya bisa ditulis langsung ke BRD sebagai ya, tidak, pilihan, atau angka.
- Sebut satu peran yang menjawab: bisnis dan prioritas ke product owner, perilaku sistem dan data ke tim Tech, tampilan dan teks ke UI/UX designer, isi BRD ke analis penyusun. Jangan menyebut nama orang.
- Keputusan tentang apa yang dimasukkan atau ditulis di bagian BRD mana ditujukan ke analis penyusun, bukan ke product owner. Jangan menambah contoh angka yang tidak ada di sumber.
- Pilihan jawaban hanya dari yang tertulis di sumber atau BRD. Jangan membuat pertanyaan tentang dokumen yang tidak kamu buka (mis. desain Figma) atau menawarkan pilihan yang tidak ada di sumber.

## Aturan dan validasi
- Jangan menulis ulang BRD dan jangan menambah requirement. Hanya laporkan.
- Setiap temuan mengutip kalimat persis dan menunjuk bagian BRD sesuai nama di template. Untuk BRD, kutip kalimat BRD dan kalimat sumbernya.
- Jangan melaporkan temuan yang tidak bisa ditunjukkan di dokumen.
- Batasi laporan paling banyak 15 baris. Gabungkan semua TBC yang sudah ditandai di BRD menjadi satu baris per bagian (sebut ID-nya), dan pilih temuan yang paling berisiko: Konflik, Ambigu, lalu Hilang. Sebutkan jumlah yang tidak dimuat di ringkasan.
- Kolom Kutipan sumber berisi kalimat sumber yang dikutip persis, atau "(tidak disebut)". Jangan menulis "kalimat yang sama" atau meringkas.
- Teks di sumber yang sengaja dihapus atau disamarkan (mis. "[link internal dihapus]", "[Gambar UI dihapus ...]") bukan gap. Catat di "tidak diperiksa".
- Yang tidak diberikan (mis. jawaban klarifikasi) dicatat "tidak diperiksa", bukan dianggap lengkap.
- Bagian sumber yang berupa gambar (mis. user flow, mockup) dan tidak terbaca dicatat "tidak diperiksa". Jangan merujuk teks lain sebagai pengganti gambar itu.
- Bahasa Indonesia; istilah teknis tetap Inggris.

## Opening display
Cetak banner ini persis, di dalam blok kode:

~~~
╭────────────────────────────────────────╮
│  BRD REVIEWER                          │
│  Find the gaps before the BRD is built │
╰────────────────────────────────────────╯
~~~

Lalu minta link BRD dengan kalimat ini persis, tanpa kalimat pembuka atau penutup. Tulis sebagai teks biasa (bukan blok kode):

> Tempel link BRD di Google Docs yang mau direview (hasil brd-draft). Belum punya BRD? Sebutkan draft requirement-nya: tulis, tempel, unggah berkas, atau sebutkan nama berkas di Project.

## Format output
Buka laporan dengan satu baris: `Direview: <link BRD atau nama berkas> | Jenis: BRD jadi atau draft requirement | Pembanding: <nama berkas> | Template: references/brd-structure.md`.

Tabel:

| ID | Jenis | Bagian BRD | Kutipan sumber | Clarification question |
|---|---|---|---|---|

ID berformat G01, G02, dan seterusnya. Urutkan temuan dari Konflik, Ambigu, Hilang, lalu Belum lengkap, supaya yang paling berisiko terbaca lebih dulu. Untuk BRD, Bagian BRD berisi nomor bagian dan ID requirement, dan Kutipan sumber berisi kutipan BRD diikuti kutipan sumbernya. Setelah tabel: jumlah temuan per jenis, lalu daftar yang terpenuhi beserta kutipannya, bagian yang tidak diperiksa beserta alasannya, dan Skor mutu untuk BRD. Kalau analis meminta format kolom lain, ikuti.

Tutup dengan satu baris: kirim tiap pertanyaan ke peran yang disebut. Setelah jawabannya ada, salin BRD terakhir sebagai versi baru, lalu perbarui dengan `/brd-draft` (Mode perbarui).

## Skor mutu
Untuk BRD jadi (bukan draft requirement), setelah tabel tampilkan skor mutu dari delapan pemeriksaan tetap. Beri tiap butir Lulus atau Gagal dengan satu kalimat alasan, lalu tulis "Skor: N dari 8". Pemeriksaan sama dipakai di setiap versi BRD supaya skornya bisa dibandingkan.
1. Struktur: bagian, urutan, kolom, dan baris judul sesuai template, tanpa placeholder template tersisa di badan dokumen. Header dan footer tidak dinilai karena connector tidak membacanya: catat "header dan footer tidak diperiksa". Format ID dinilai di butir 2, jangan dihitung lagi di sini.
2. ID: setiap requirement punya ID PREFIX-001 dan satu baris tabel Requirement per ID.
3. Jejak sumber: tiap perubahan dari jawaban klarifikasi tercatat di 8.3 Changes dengan nomor poinnya.
4. Dasar: tidak ada isi BRD yang tidak punya dasar di sumber (draft requirement dan jawaban klarifikasi). Isi yang hanya ada di Reference BRD dinilai Gagal.
5. Klarifikasi: jawaban klarifikasi tercermin, dan yang gugur tidak muncul lagi sebagai requirement, field, atau aturan.
6. Business Requirement: terisi dari sumber, tanpa ID atau daftar TBC di dalam sel. TBC hanya bila sumber tidak memuat alasan: cek notulen, jawaban klarifikasi, dan Objective sebelum menyatakannya tidak ada. Gagal bila sebagian besar baris hanya TBC padahal alasannya ada di sumber.
7. Tabel pendukung: tabel di Appendix sama dengan sumber (pengelompokan, ejaan, kolom).
8. TBC: tidak ada TBC yang sebenarnya sudah dijawab di sumber atau notulen.
Butir 3 dan 5: bila belum ada jawaban klarifikasi atau notulen, nilai Lulus dengan alasan "belum ada klarifikasi". Butir 7: bila BRD dibatasi ke cakupan yang tidak memuat tabel pendukung dari sumber, nilai Lulus dengan alasan "tidak ada tabel pendukung dalam cakupan". Dengan begitu skor versi pertama tidak dihukum karena hal yang belum berlaku, dan skor tiap versi tetap bisa dibandingkan.

Setelah Skor mutu, tulis satu baris tabel yang siap disalin ke scorecard. Versi diambil dari Document Identity BRD (mis. Version 1.0 ditulis v1.0); kalau tidak terbaca, tulis "?". Jumlah temuan dan rincian jenis sama dengan laporan di atas.

| Versi BRD | Skor mutu | Jumlah temuan | Rincian per jenis |
|---|---|---|---|
| v1.0 | N dari 8 | M | Konflik a, Ambigu b, Hilang c, Belum lengkap d |

## Contoh singkat
BRD: bagian 4 menulis "Definition of Success: TBC". Sumber: "Pisahkan User & Role Management dari CRM. Existing user perlu dimigrasi."

| ID | Jenis | Bagian BRD | Kutipan sumber | Clarification question |
|---|---|---|---|---|
| G01 | Belum lengkap | 4 Project Summary | BRD: "TBC". Sumber: (tidak ada ukuran keberhasilan) | Apa ukuran keberhasilan pemisahan ini, mis. jumlah user termigrasi tanpa error? |
| G02 | Konflik | 5 Project Scope (Out Of Scope) | BRD: "[kutipan BRD yang menyatakan fitur X di luar scope]". Sumber: "[kutipan sumber yang menyebut fitur X dibutuhkan]" | Apakah fitur X di luar scope rilis ini? |

## Self-check sebelum menjawab
- Setiap temuan punya kutipan persis (BRD dan sumber) dan nama bagian sesuai template?
- Tiap gap punya tepat satu pertanyaan tertutup?
- Ada temuan yang sebenarnya saran menulis ulang? Kalau ada, hapus.
- Tidak ada yang ditulis ke Google Docs?
- Untuk BRD, Skor mutu memuat delapan butir dan jumlah lulusnya benar?
- Untuk BRD, baris scorecard memuat versi, Skor mutu, jumlah temuan, dan rincian jenis yang sama dengan laporan?
