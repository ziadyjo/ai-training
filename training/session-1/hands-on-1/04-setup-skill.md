# Langkah 4: Pasang Skill di Claude

Durasi ±6 menit.

## Yang dikerjakan

1. Buka **Customize** di sidebar, tab **Skills**, klik **+ Add**, pilih **Create a skill**.
2. Isi **Skill name** dengan `brd-draft`.
3. Isi **Description** dengan paragraf description dari Langkah 3.
4. Buka [`sources/brd-draft-starter/SKILL.md`](sources/brd-draft-starter/SKILL.md), salin semua isi setelah baris `---` kedua (mulai dari `# BRD Draft`), lalu tempel ke editor instruksi. Kalau hasilmu belum jalan, atau untuk membandingkan, pakai acuan di [`sources/brd-draft-checkpoint/SKILL.md`](sources/brd-draft-checkpoint/SKILL.md).
5. Klik **+ Add file**, ketik nama berkas `references/brd-structure.md` (folder `references` terbentuk otomatis), lalu tempel isi berkas di bawah ke editornya.
6. Klik **Create**. Skill muncul di daftar "Created by you" sebagai v1.

Menambah berkas setelah Skill dibuat: buka Skill, tab **Contents**, klik **Edit**, tambahkan berkas dengan cara yang sama, lalu **Save version**. Ikuti tombol yang tampil di layarmu.

## Isi `references/brd-structure.md`

Berkas yang sama ada di [`sources/brd-draft-starter/references/brd-structure.md`](sources/brd-draft-starter/references/brd-structure.md).

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

Skill tampil di daftar, `references/brd-structure.md` ada di tab Contents, dan Description tampil utuh di tab Overview. Description dipotong di 500 karakter, jadi kalau kalimat terakhirnya terputus, perpendek lalu simpan versi baru.

Uji pemanggilan di Langkah 5: Skill terpanggil untuk permintaan yang jelas dan untuk parafrasenya (mis. "buat BRD", "susun requirement"), dan tidak terpanggil untuk topik lain.

---

Sebelumnya: [Langkah 3: Lengkapi starter Skill](03-complete-starter.md)  
Berikutnya: [Langkah 5: Uji dan perbaiki](05-test-refine.md)
