---
name: brd-draft
description: Dipakai saat analis punya permintaan fitur atau draft requirement mentah (pesan atasan, product concept, catatan rapat) dan perlu menyusun BRD sesuai template. Menilai informasi di draft, menampilkan BRD di chat untuk disetujui, lalu mengisi salinan template di Google Docs dengan sumber tercatat dan TBC untuk yang belum siap. Pakai juga saat analis menulis "buat BRD" atau "susun requirement". Tidak untuk mereview BRD jadi.
---

# BRD Draft

Draft masuk, BRD terisi. Claude menilai setiap informasi di draft dan lampirannya, menyusun BRD sesuai template, menampilkannya di chat untuk disetujui, lalu menulisnya ke salinan template Google Docs milik analis. Yang belum siap ditandai TBC; analis melengkapinya sendiri. Skill mengisi bagian 1, 2, 4, 5, 6 (opsional), 7, dan 8 (bila ada). Bagian 3 (Approval) dibiarkan seperti template.

## Input
- Link salinan template BRD (File > Make a copy dari [Template BRD](https://docs.google.com/document/d/1mQB_06ReQ9WnhM4of3NWRyncfTr00yO1io7RMf4wp_8/edit?usp=sharing)). Cadangan struktur: `references/brd-structure.md`.
- Draft atau permintaan requirement: ditulis, ditempel, dilampirkan (dokumen atau screenshot), atau sudah ada di Context Project.
- Jawaban klarifikasi, bila ada.
- Reference BRD (opsional): contoh BRD jadi di Project. Hanya untuk bentuk, tingkat detail, dan pola ID; bukan sumber isi.
- Identitas dokumen: project, modul, penyusun, penerima, tanggal, versi.

Pakai hanya dokumen yang disebut analis atau ada di Project. Jangan mencari di Drive dan jangan menyebut nama atau email pemilik dokumen. Kalau template tidak terbaca dan `references/brd-structure.md` tidak ada, sebutkan dan berhenti.

## Langkah kerja
1. **Kumpulkan input dalam dua giliran.** Kalau dipanggil tanpa isi, cetak Opening display, lalu minta (a) link salinan, lalu (b) requirement beserta detail dokumen dalam satu pesan. Requirement harus disebut analis: ditulis, ditempel sebagai catatan, dilampirkan sebagai berkas, atau nama berkas di Project. Jangan memilih sendiri dokumen dari Project. Link dan requirement wajib ada; detail dokumen yang kosong menjadi TBC.
2. **Nilai setiap informasi dengan Kriteria review**, tanpa bertanya. Baca draft, jawaban klarifikasi, dan lampiran sebelum menulis.
3. **Susun BRD di chat**, bagian demi bagian mengikuti template:
   - 1 Document Identity dan 2 Document Change Control: dari identitas dokumen. Entri pertama: versi, tanggal, "First draft".
   - 4 Project Summary: masalah, tujuan, ukuran keberhasilan.
   - 5 Project Scope: fungsi yang masuk dan yang tidak dikerjakan.
   - 6 Business Process (opsional): proses sekarang dan usulan.
   - 7 Requirement: dari draft dan jawaban klarifikasi.
   - 8 Appendix: pertahankan tiga sub-bagian template. 8.1 tabel pendukung berisi tabel dari draft yang terkait requirement dalam cakupan, termasuk tabel mapping hak akses (mis. Mapping Adjustment untuk Access Level "View Only") bila ada, dengan judul dan kolom yang sama seperti sumber, 8.2 Rules berisi aturan umum dari draft sebagai daftar bernomor, 8.3 Changes berisi perubahan yang sudah disepakati (tulis "Belum ada" di baris tabelnya bila tidak ada).
   Akhiri dengan satu pertanyaan: "Tulis BRD ini ke salinan Google Docs?"
4. **Tulis ke salinan lewat Google Docs connector** hanya setelah analis menyetujui. Kalau analis memberi koreksi, perbaiki di chat dulu. Kalau connector tidak tersedia atau gagal, biarkan hasil di chat untuk disalin analis.
5. **Tutup** dengan Format output.

## Mode perbarui
Dipakai bila pesan memuat link BRD yang sudah terisi dan analis meminta memperbarui: memasukkan notulen atau jawaban klarifikasi, atau memperbaiki bagian tertentu. Jangan menyusun ulang dari nol.
1. Baca BRD terisi dan sumber barunya (notulen, jawaban klarifikasi) atau daftar perbaikan dari analis.
2. Tampilkan di chat daftar perubahan: bagian atau ID, isi lama, isi baru, dan dasarnya (nomor poin sumber). Jangan menampilkan ulang seluruh BRD.
3. Tulis ke dokumen hanya setelah analis menyetujui, dan hanya pada bagian di daftar. Bagian, struktur, dan ID yang tidak disebut tidak diubah.
4. Tambahkan satu baris di Document Change Control (versi baru, tanggal, ringkasan) dan catat tiap perubahan di 8.3 Changes dengan nomor poin sumbernya.
5. Fitur yang gugur dihapus beserta turunannya. ID yang sudah ada tidak berganti makna.
6. Setiap poin sumber yang menyentuh bagian BRD dalam cakupan harus tercermin di daftar perubahan. Poin yang sengaja tidak dimasukkan ditulis di akhir daftar beserta alasannya (mis. di luar cakupan).
7. Setelah menulis, baca ulang sel yang diubah dan hapus butir atau baris kosong yang tersisa. Kalau connector tidak bisa menghapusnya, sebut sel dan bagiannya di akhir jawaban.
Template asli tidak pernah ditulis.

## Kriteria review
Sebelum menulis, nilai setiap informasi yang dibutuhkan tiap bagian template:
- **Terpenuhi**: ada di draft dan cukup jelas untuk ditulis tanpa tebakan. Tulis ke BRD.
- **Hilang**: bagian template butuh informasi, draft tidak menyebutnya. Tulis TBC.
- **Ambigu**: kalimat bisa dibaca lebih dari satu cara, atau memakai kata tanpa ukuran ("segera", "berkala"). Tulis TBC dengan kutipan aslinya.
- **Konflik**: dua bagian draft saling bertentangan. Tulis TBC dan sebut kedua kalimatnya.
- **Belum lengkap**: topik disebut tetapi detailnya kurang, termasuk yang di draft ditandai TBC, "Perlu Konfirmasi", atau tbd. Tulis yang ada, sisanya TBC.
Setiap TBC masuk ke daftar TBC sebagai satu pertanyaan tertutup.

## Aturan generate BRD
- Jangan menebak atau menambah requirement, field, atau aturan di luar draft dan jawaban klarifikasi. Yang tidak ada menjadi TBC, termasuk nama dan jabatan penyusun. Di dokumen tulis cukup "TBC" tanpa alasan; alasan dan kutipan draft masuk ke daftar TBC di chat.
- Reference BRD (bila ada di Project) hanya untuk bentuk, tingkat detail, dan pola ID. Jangan mengambil requirement, field, aturan, angka, atau nama fitur dari Reference. Hal yang hanya ada di Reference, bukan di draft atau jawaban klarifikasi, ditulis TBC.
- Hanya bagian 6 (opsional) yang boleh seluruhnya ditulis "Belum ada". Pada bagian lain, judul, sub-bagian, dan tabel template tetap ada. Isian yang tidak ada diganti "Belum ada" atau TBC di tempatnya, bukan dengan menghapus sub-bagian. Ganti semua placeholder dalam kurung siku.
- Struktur mengikuti template: jangan menambah, menghapus, atau mengubah urutan bagian dan kolom.
- Satu halaman atau fitur, satu ID (bukan satu ID per field atau per aturan); field, kondisi, dan pengecualian jadi butir di bawah ID yang sama. Format ID: PREFIX-001 (nomor tiga digit, mulai dari 001 di tiap kelompok fitur). PREFIX adalah singkatan 2–3 huruf dari nama kelompok fitur (mis. ROLE MANAGEMENT menjadi RM) yang kamu buat sendiri. PREFIX bukan isi draft, jadi tidak ditulis TBC dan tidak masuk daftar TBC; arti tiap PREFIX dicatat di tabel sumber. Kondisi dan pengecualian jadi butir di bawah ID yang sama. Satu baris tabel Requirement untuk satu sub-bagian sumber (mis. satu Section atau Page di Product Concept). Jangan menggabungkan beberapa sub-bagian ke satu baris atau satu sel Functional Requirement.
- Business Requirement menjawab "mengapa", Functional Requirement "apa yang dilakukan sistem". Isi Business Requirement satu atau dua kalimat per baris sub-bagian, hanya dari kalimat draft atau jawaban klarifikasi yang menyatakan alasan atau kebutuhan. Jangan menulis ID requirement atau daftar TBC di dalam sel itu. Bila tidak ada kalimat alasan, tulis "TBC" saja dan tambahkan satu pertanyaan tertutup per sub-bagian di daftar TBC. Merujuk ke Objective bagian 4 hanya bila analis atau jawaban klarifikasi menyetujuinya; jangan menyimpulkan alasan sendiri.
- Appendix 8.1: salin tabel pendukung dengan pengelompokan menu induk dan submenu persis seperti di sumber. Satu baris per submenu, nama menu induk hanya di baris pertama grupnya, ejaan sama dengan sumber. Jangan memindahkan submenu ke menu induk lain, menggabungkan menu, atau menjadikan submenu sebagai menu sendiri. Di Google Docs, gabungkan sel Menu secara vertikal per grup (merge cells) bila connector bisa; bila tidak bisa, biarkan sel di bawahnya kosong dan sebut di akhir bahwa sel Menu perlu digabung manual. Jangan menulis TBC di kolom yang nilainya terbaca. Bila pengelompokan tidak jelas, tulis nilai yang terbaca apa adanya dan tanyakan sisanya di daftar TBC.
- Background/Problem Statement memuat seluruh Overview sumber, termasuk konsekuensi seperti migrasi data user. Masuk atau tidaknya hal itu ke scope ditanyakan di daftar TBC.
- Kolom User Interface, flow, dan prototype: "Belum ada" sampai tersedia. Tautan yang ada di draft (mis. Figma, prototype) boleh ditulis apa adanya. Tautan prototype yang tidak menyebut platform ditulis satu kali sebagai "Prototype: <tautan>": jangan memilih Desktop atau Mobile sendiri, dan tanyakan platformnya di daftar TBC. Jangan membuat gambar atau tautan sendiri.
- Screenshot dibaca sebagai sumber: sebutkan yang terlihat, jangan menafsirkan di luar itu.
- Penulisan penuh dari nol hanya ke salinan yang masih berisi placeholder. Kalau salinan sudah terisi dan analis tidak meminta memperbarui, atau itu template asli, berhenti dan minta link salinan baru (lihat Mode perbarui).
- Jangan menulis ke Google Docs sebelum analis menyetujui BRD di chat.
- Jangan menyebut nama orang dari draft di BRD kecuali analis memintanya.
- Nama project dan modul yang tidak disebut analis diambil dari judul dan isi dokumen sumber, bukan ditebak; kalau dokumen tidak menyebutnya, tulis TBC. Cakupan yang tidak disebut berarti seluruh isi dokumen sumber. Cakupan yang dibatasi analis tidak boleh dilebarkan sendiri; hal di luar cakupan cukup satu butir di Out Of Scope Functionality bila analis memintanya.
- Jangan memakai tanda pisah panjang atau sedang (em dash dan en dash) di dokumen. Butir ditulis dengan "- " di awal baris, bukan simbol titik bulat atau tanda pisah lain. Kalimat pendek dan lugas, tanpa hiperbola atau alasan buatan sendiri.
- Bahasa Indonesia; istilah teknis tetap Inggris.

## Format output
Setelah BRD tertulis di Google Docs, tampilkan dua catatan kerja di chat. Keduanya tidak ditulis ke dokumen BRD.
1. Tabel sumber: ID | Requirement | Sumber (nama bagian di Product Concept, atau nomor jawaban klarifikasi).
2. Daftar TBC sebagai clarification question: nomor | pertanyaan | ditujukan ke peran.

Tutup dengan satu baris: header dan footer dokumen (nama project dan versi) diubah manual di Google Docs karena connector tidak mengubahnya, lengkapi TBC, lalu review BRD ini.

## Opening display
Cetak banner ini persis, di dalam blok kode:

~~~
╭────────────────────────────────────────╮
│  BRD DRAFTER                           │
│  Turn a draft into a review-ready BRD  │
╰────────────────────────────────────────╯
~~~

Lalu minta input dalam dua giliran, dengan kalimat ini persis, tanpa kalimat pembuka atau penutup. Tulis sebagai teks biasa (bukan blok kode) agar link tampil sebagai hyperlink.

Giliran pertama:

> Tempel link salinan template BRD. Belum punya? Buka [Template BRD](https://docs.google.com/document/d/1mQB_06ReQ9WnhM4of3NWRyncfTr00yO1io7RMf4wp_8/edit?usp=sharing), klik File > Make a copy, lalu tempel link salinannya ke sini.

Giliran kedua, setelah link diterima:

> Berikan requirement atau konsep-nya: tulis, tempel catatan, atau unggah berkas (PDF, dokumen, screenshot). Kalau berkasnya sudah ada di Project, sebutkan namanya. Sertakan detail dokumen dalam pesan yang sama, contohnya:

Lalu tampilkan contoh ini sebagai blok kode, satu isian per baris, persis seperti ini:

~~~
Requirement: [berkas di Project, link, atau catatan yang ditempel]
Cakupan: [isi sesuai kebutuhanmu: fitur atau kelompok fitur yang dimasukkan, atau "seluruh dokumen"]
Project: [nama project dan modul]
Penyusun: [Namamu] - [Jabatanmu]
Penerima: [tim atau peran penerima]
Tanggal: [Tanggal]
Versi: 1.0
~~~

## Contoh singkat
Draft: "Tambahkan ekspor laporan bulanan ke PDF."
Project Summary: Background dari draft; Objective: menambah ekspor laporan bulanan ke PDF; Definition of Success: TBC (hilang).
Project Scope: In Scope: ekspor laporan bulanan ke PDF; Out of Scope: TBC (hilang).
Business Process: Belum ada.
Daftar TBC: (1) Apa ukuran keberhasilan pemisahan ini? (2) Apa yang sengaja tidak dikerjakan? Ditujukan ke: product owner.

## Self-check sebelum menjawab
- Setiap isi BRD berasal dari draft atau jawaban klarifikasi, dan yang tidak siap ditulis TBC atau "Belum ada"?
- Struktur dan urutan bagian sama dengan template?
- Setiap requirement punya ID dan baris di tabel sumber?
- BRD sudah disetujui di chat sebelum ditulis, dan penulisan penuh hanya ke salinan placeholder (atau perbarui terarah di BRD terisi)?
- Tidak ada em dash, en dash, atau simbol titik bulat di dokumen?
