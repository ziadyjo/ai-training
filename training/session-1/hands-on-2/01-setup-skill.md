# Langkah 1: Pasang brd-review

Durasi ±3 menit. `brd-review` sudah jadi, jadi kamu menyalinnya, bukan membangunnya. Skill ini hanya melaporkan temuan dan tidak menulis ke Google Docs.

## Yang dikerjakan

1. Buka **Customize** di sidebar, tab **Skills**, klik **+ Add**, pilih **Create a skill**.
2. Isi **Skill name** dengan `brd-review`.
3. Isi **Description** dengan teks di bagian "Description" di bawah.
4. Tempel teks di bagian "Instruksi Skill" ke editor instruksi.
5. Klik **+ Add file**, ketik nama berkas `references/brd-structure.md`, tempel isinya dari bagian terakhir di bawah, lalu klik **Create**.
6. Buka Project "WebTM Role & User Management" dan cek **Context**. Kalau Product Concept belum ada, unggah dari [`../hands-on-1/sources/`](../hands-on-1/sources/).

## Description

```
Dipakai untuk memeriksa BRD hasil brd-draft: membandingkan isi BRD dengan template dan sumbernya (Product Concept, jawaban klarifikasi), lalu melaporkan gap (terpenuhi, hilang, ambigu, konflik, belum lengkap) beserta clarification question. Bisa juga untuk draft requirement mentah. Pakai juga saat analis menulis "review BRD", "cek BRD", atau "gap analysis". Hanya melaporkan.
```

## Instruksi Skill

````
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
````

## Isi `references/brd-structure.md`

Berkas yang sama dengan di Hands-on #1: [`../hands-on-1/sources/brd-draft-starter/references/brd-structure.md`](../hands-on-1/sources/brd-draft-starter/references/brd-structure.md).

````
# Struktur template BRD

Sumber utama adalah template Google Docs (mode Pageless). Berkas ini cadangan struktur bila Docs tidak terbaca, dan merangkum konvensi penulisan dari Reference BRD. Konvensi hanya untuk bentuk. Urutan bagian, kolom tabel, dan gaya tidak diubah. Yang diisi hanya konten, dan konten hanya dari sumber yang disebut analis.

Header: "Business Requirement Document" dan "[Project] Version [x.y]". Footer: "[Nama Project]", nomor halaman, dan "v[x.y]". Keduanya tidak diubah oleh connector, jadi diganti manual.

| # | Bagian | Isi |
|---|---|---|
| Cover | Judul | "Requirement Document", lalu "[Nama Project] - [Nama Modul]", tanggal, "Version [x.y]" |
| 1 | Document Identity | Prepared By, Prepared For, Creation Date, Version |
| 2 | Document Change Control | Tabel Version, Date, Summary of Change |
| 3 | Approval | Tabel Name, Date, Sign |
| 4 | Project Summary | Background/Problem Statement, Objective, Definition of Success |
| 5 | Project Scope | In Scope Functionality, Out Of Scope Functionality |
| 6 | Business Process Overview (Optional) | Current Business Process (As-Is), Proposed Business Process |
| 7 | Requirement | Baris Design & Prototype, lalu tabel Section, Business Requirement, Functional Requirement, User Interface |
| 8 | Appendix | Tiga sub-bagian tetap ada: 8.1 Mapping Adjustment untuk Access Level "View Only" (tabel Menu, Submenu, Adjustment View Only), 8.2 Rules (daftar bernomor), 8.3 Changes (tabel No, Description, Note) |

## Konvensi per bagian
- Tanggal ditulis "D Bulan YYYY" dengan nama bulan bahasa Inggris (mis. 8 September 2026).
- Prepared By: "[Nama] - [Jabatan]". Prepared For boleh kosong. Creation Date dan Version sama dengan cover.
- Document Change Control: satu baris per versi, versi naik per revisi (1.0, 1.1, 1.2). Baris pertama "First draft". Summary berupa satu kalimat yang menyebut pemicu revisi, misalnya diskusi atau meeting.
- Approval: tabel Name, Date, Sign dengan beberapa baris kosong untuk diisi saat persetujuan.
- Project Summary: Background berupa prosa dengan urutan kondisi saat ini, alasan perubahan, lalu konsekuensinya. Objective dan Definition of Success berupa butir "-". Objective diawali kata kerja. Definition of Success terukur (angka atau kondisi yang bisa dicek).
- Project Scope: butir "-". In Scope: "[Modul]: [halaman atau fitur], [halaman atau fitur]". Out Of Scope: hal yang tidak dikerjakan, alasannya, dan workaround bila ada.
- Business Process Overview: As-Is satu atau dua kalimat ("Saat ini belum ..." bila belum ada proses). Proposed berupa gambar user flow atau flowchart, tanpa teks.

## Tabel Requirement
- Baris atas tabel: "Design & Prototype: Figma | Prototype Desktop | Prototype Mobile". Tautan diisi dari sumber bila ada, selain itu TBC.
- Satu baris judul huruf kapital per kelompok fitur (bar berwarna).
- Di bawahnya, satu baris per sub-bagian: nama sub-bagian, kebutuhan bisnis, requirement ber-ID, kolom UI.
- Business Requirement: satu atau dua kalimat dari sudut pengguna, diawali peran ("[Peran] dapat [aksi] [tujuan]").
- Format ID: PREFIX-001 diikuti judul, dicetak tebal. PREFIX 2 huruf kapital per kelompok fitur, nomor 3 digit dan mulai dari 001 lagi di tiap PREFIX. Satu ID untuk satu halaman atau fitur; perilaku dan field ditulis sebagai butir di bawah ID, bukan ID terpisah per field.
- Functional Requirement: butir "-" untuk perilaku yang bisa diuji, aturan atau kondisi, dan pesan atau validasi. Rincian ditulis sebagai sub-butir, contoh diawali "Contoh:". Nama field, tombol, dan status ditulis dalam tanda kutip. Kata kunci kondisi boleh dicetak tebal. Rujukan antar requirement ditulis [PREFIX-001].
- Kolom User Interface: mockup dengan keterangan "[ID] [judul]". Variasi tampilan diberi akhiran huruf (PREFIX-001A, PREFIX-001B). Sebelum mockup ada tulis "Belum ada".

## Appendix
- 8.1: judul 8.1 Mapping Adjustment untuk Access Level "View Only", kolom Menu, Submenu, Adjustment View Only, isinya disalin dari tabel mapping di sumber persis seperti sumber (pengelompokan menu dan ejaan sama). Baris tanpa perubahan ditulis "Tidak ada perubahan". Tabel pendukung lain dari sumber yang terkait cakupan boleh ditambahkan sebagai 8.1 berikutnya. Bila sumber tidak punya tabel mapping hak akses, tulis satu baris "Belum ada" tanpa judul kolom placeholder.
- 8.2 Rules: daftar bernomor, satu aturan per butir, kalimat deklaratif, kata kunci boleh dicetak tebal. Boleh ditutup baris "NOTE:" tentang siapa yang sudah meninjau aturan.
- 8.2 dan 8.3 yang belum ada isinya ditulis "Belum ada" pada baris tabel atau butirnya.
- 8.3 Changes: kalimat pembuka tetap "Perubahan dibawah ini sudah melalui diskusi antara FA dengan tim Tech", lalu tabel No, Description, Note. Description berisi perubahan konkret sebagai butir "-". Note berisi alasan atau dampak, boleh kosong. Hanya diisi setelah ada diskusi dengan Tech.

## Pola dari Reference BRD
Reference BRD adalah standar bentuk dokumen ini. Pola di bawah dipakai hanya bila ada di sumber dan termasuk cakupan BRD yang diminta analis. Isinya tetap hanya dari sumber, dan yang belum ada di sumber ditulis TBC.
- Kelompok fitur dan PREFIX: AUTENTIKASI & ACCESS CONTROL (AC), MASTER MENU (MM), ROLE MANAGEMENT (RM), USER MANAGEMENT (UM), BREADCRUMBS (BC). Nomor mulai 001 di tiap PREFIX.
- AUTENTIKASI & ACCESS CONTROL: sub-bagian Login & Autentikasi, Use Case Scenario (satu requirement "Skenario", satu butir bercetak tebal per kasus), dan Entrypoint Admin (menu dan submenu di sidebar, serta siapa yang melihatnya).
- Pola sub-bagian per modul, satu requirement per halaman:
  - Halaman Daftar [X]: entrypoint tombol, filter (rincian tiap filter), kolom tabel, tombol aksi per baris.
  - Halaman Change Log [X]: isi log, periode data default beserta filter tanggal, dan tautan dokumen "Mapping Change Log".
  - Add New [X] atau Create New [X]: satu ID untuk halaman, dengan satu butir per field berisi sumber atau cara isi, apakah bisa diedit, mandatory atau tidak, dan nilai dropdown.
  - Edit [X]: data yang dapat diedit dan kalimat "Perubahan tercatat pada Change Log [X]".
  - Modal konfirmasi submit dan tampilan error muncul hanya di kolom UI dengan ID sendiri.
- Business Process Overview, Proposed: satu gambar flow per modul dengan judul bernomor (mis. "1. [Modul] Flow").
- 8.2 Rules: istilah level akses (None, View Only, All Access) dicetak tebal. Butir terakhir boleh berupa tautan dokumen pendukung. Ditutup "NOTE:" tentang siapa yang sudah meninjau.
- 8.3 Changes: Description berisi butir "-", boleh disertai gambar. Note berisi alasan, dan boleh kosong.

## Di luar dokumen BRD
Dua catatan kerja dihasilkan Skill di chat, tidak ditulis ke dokumen BRD:
- Tabel sumber: ID, Requirement, Sumber.
- Daftar TBC dan pertanyaan terbuka.
````

## Cek

`brd-review` tampil di daftar Skill dan Product Concept ada di Context Project. Salinan cadangan Skill ada di [`sources/brd-review/`](sources/brd-review/).

---

Berikutnya: [Langkah 2: Jalankan /brd-review](02-run-review.md)
