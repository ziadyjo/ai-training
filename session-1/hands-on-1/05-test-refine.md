# Langkah 5: Uji dan perbaiki

Durasi ±24 menit. Ini langkah terpanjang: Claude menyusun BRD di chat, menulis ke Google Docs lewat connector (bagian paling lama), lalu kamu memperbaiki Skill dari satu temuan. Cakupan BRD dibatasi ke **Role Management** karena Sesi 2 sampai 4 hanya memakai modul itu, dan supaya penulisan ke Docs selesai dalam beberapa menit, bukan belasan.

## Yang dikerjakan

1. Pakai salinan `BRD WebTM v1.0` dari Quick Setup. Kalau Skill menolak karena salinan sudah terisi, buat salinan baru dari template asli (**File > Make a copy**) dan salin link-nya.
2. Buka chat baru di dalam Project, kirim prompt 1 di bawah. Skill meminta link salinan: tempel link `BRD WebTM v1.0`.
3. Skill meminta requirement dan detail dokumen dalam satu pesan: kirim prompt 2 (ganti isian dalam kurung siku). Kalau Product Concept belum ada di Context, unggah berkasnya lewat **+** di pesan yang sama.
4. Skill menampilkan BRD di chat dulu. Periksa strukturnya, lalu balas "Setuju, tulis ke salinan." Setujui kartu izin connector saat Skill menulis, lalu buka salinanmu di Google Docs (penulisan membutuhkan beberapa menit).
5. Kirim satu feedback memakai prompt 3. Claude menunjukkan baris lama dan baru. Balas "setuju". Claude menampilkan kartu **Update skill**. Buka **Content** dan periksa jumlah barisnya (angka Current dan This draft muncul di konfirmasi; angka bisa sama bila baris diubah di tempat, jadi periksa isi barisnya di Content), lalu klik **Update** dan **Update skill**. Itu menyimpan versi baru; versi lama tetap ada di riwayat. Klik sekali saja: kartu tetap tampil setelah tersimpan, dan klik kedua membuat versi tambahan. Kalau kartu tidak muncul, buka Skill, klik **Edit**, terapkan perubahan, lalu **Save version**.
6. Setelah Skill diperbarui, Claude menanyakan apakah BRD tadi mau diperbaiki. Balas singkat, misalnya "Sudah diperbarui, ya perbaiki." Kalau Claude tidak menawarkan, ketik `/brd-draft [link salinanmu]` dan minta memperbarui hanya bagian yang kamu keluhkan (Mode perbarui). Jangan menyusun ulang dari nol: Skill menolak menulis penuh ke salinan yang sudah terisi. Tambahkan di balasanmu: versi tetap 1.0, jangan tambah baris di Document Change Control dan 8.3 Changes, karena BRD ini belum dirilis sebagai versi berikutnya. Perbaikan itu muncul di Google Docs sebagai **saran** (teks lama dicoret, teks baru disorot). Terima semuanya lewat **Tools > Review suggested edits > Accept all**, lalu periksa: hanya bagian yang kamu keluhkan yang berubah.

## Prompt 1: jalankan Skill

```
/brd-draft
```

## Prompt 2: requirement, cakupan, dan detail dokumen

Ganti dulu: `[Namamu]`, `[Jabatanmu]`, `[Tanggal]`. Tulis tanggal dengan nama bulan bahasa Inggris, misalnya `20 October 2026`.

Skill menampilkan contoh dengan isian `Cakupan: [...]`. Salin dari blok di bawah, yang sudah mengisi cakupannya: untuk hands-on ini BRD fokus ke kelompok fitur Role Management. Nanti, saat BRD dilebarkan ke fitur lain (User Management, Master Menu, dan seterusnya), ganti isian Cakupan dan perbarui BRD lewat Mode perbarui.

```
Requirement: file Product Concept di Context Project ini (bukan Reference BRD).
Cakupan: hanya kelompok fitur Role Management (Daftar Role, Role Members, Change Log Role, Create New Role, Role Permission, dampak Role Status, Edit Role). Fitur lain (User Management dan login) tidak dijabarkan sebagai requirement. Tulis satu butir di Out Of Scope Functionality: "User Management dan login".
Project: WebTM, modul Role Management
Penyusun: [Namamu] - [Jabatanmu]
Penerima: Tim Tech
Tanggal: [Tanggal]
Versi: 1.0
```

## Prompt 3: feedback untuk Skill

Kirim di chat yang sama dengan Langkah 5, jadi Claude sudah tahu BRD mana yang dinilai. Contoh feedback: kolom Business Requirement berisi kalimat turunan Claude sendiri, bukan kalimat dari Product Concept. Cari satu kalimat seperti itu di BRD-mu dan cek di Product Concept sebelum mengirim. Kalau BRD-mu tidak punya masalah ini, pakai masalah lain yang kamu temukan (misalnya butir Out Of Scope yang tidak disebut di draft).

Ganti dulu: `[KALIMAT CONTOH DARI BRD-MU]`.

```
FEEDBACK
Kolom Business Requirement berisi kalimat turunanmu sendiri, bukan kalimat dari Product Concept, misalnya: [KALIMAT CONTOH DARI BRD-MU]. Itu kesimpulanmu, bukan isi draft.

TASK
Usulkan perubahan pada Aturan generate BRD di SKILL.md brd-draft supaya Business Requirement hanya berisi alasan yang tertulis di draft atau jawaban klarifikasi, dan selebihnya ditulis TBC. Jangan mengubah bagian lain.

OUTPUT FORMAT
Tunjukkan perubahan sebagai baris lama dan baris baru. Jangan menerapkannya sebelum aku setujui. Setelah itu, tanyakan apakah BRD tadi mau diperbaiki dengan aturan baru.
```

## Prompt 3 alternatif: Business Requirement tidak menjawab "mengapa"

Pakai ini bila di BRD-mu Business Requirement hanya mengulang fungsi (contoh: "Super admin dapat melihat seluruh role beserta jumlah user dan statusnya") dan tidak menyebut alasan. Ganti `[KALIMAT CONTOH DARI BRD-MU]`.

```
FEEDBACK
Kolom Business Requirement di BRD tadi hanya mengulang fungsi, bukan menjawab "mengapa". Contoh: [KALIMAT CONTOH DARI BRD-MU]. Kalimat itu menjelaskan apa yang dilakukan, bukan alasan bisnisnya. Product Concept tidak menyebut alasan per halaman, jadi kolom ini seharusnya tidak berisi kesimpulanmu.

TASK
Usulkan perubahan pada Aturan generate BRD di SKILL.md brd-draft supaya Business Requirement ditulis dengan pola "[Peran] dapat [aksi] supaya [alasan]" hanya bila alasannya tertulis di draft atau jawaban klarifikasi. Bila tidak ada alasan tertulis, tulis pola "[Peran] dapat [aksi]. Alasan bisnis: TBC". Jangan mengubah bagian lain.

OUTPUT FORMAT
Tunjukkan perubahan sebagai baris lama dan baris baru. Jangan menerapkannya sebelum aku setujui. Setelah itu, tanyakan apakah BRD tadi mau diperbaiki dengan aturan baru.
```

Periksa Baris baru sebelum menyetujui: tolak bila Claude menambah aturan lain di luar yang diminta.

## Cek

- Isi requirement berasal dari Product Concept. Kalau BRD memuat fitur yang tidak ada di Product Concept tetapi ada di Reference BRD (mis. Managed Roles atau field Business Unit di Add New User), itu salinan dari Reference. Beri feedback dan minta ditulis TBC.
- Skill benar-benar terpanggil (terlihat langkah "Loading skill"), BRD tampil di chat sebelum ditulis, dan Skill menulis ke salinan, bukan ke template asli.
- BRD hanya memuat kelompok fitur Role Management, dan ID requirement berprefix (mis. RM-001), bukan `TBC`. Kalau ID masih TBC, itu temuan untuk iterasi Skill.
- Header dan footer dokumen ("[Project]", "[Nama Project]", "v1.0") tidak diubah oleh connector. Ganti manual di Google Docs.
- Gambar mockup dan User Flow dari Product Concept tidak masuk otomatis. Tempel manual atau biarkan; Bagian 6 Proposed Business Process berisi teks ringkas.
- Indentasi butir bisa tidak seragam antar baris (sebagian menggantung, sebagian rapat). Rapikan manual atau abaikan.
- Periksa hasil di Google Docs, jangan hanya percaya laporan di chat. Connector bisa menyimpang pada tabel: dua baris tergabung jadi satu, teks satu tabel tercetak tebal semua, atau muncul bullet "-" yang tidak ada di draft. Claude biasanya melaporkan penyimpangan ini di akhir. Catat sebagai temuan dan perbaiki manual; jangan minta Claude menulis ulang seluruh dokumen.
- Kalau Skill tidak terpanggil, ketik ulang `/brd-draft` dan pilih Skill dari daftar.

## Hasil yang diharapkan

- Skill punya description yang menyebut kapan dipakai.
- BRD tampil di chat dan disetujui sebelum ditulis ke Google Docs.
- Skill menulis TBC, bukan menebak, dan mengikuti template.
- Skill diperbarui dari satu temuan nyata, dan hanya bagian yang dikeluhkan yang berubah di BRD.

Hasil tiap peserta akan berbeda. Yang dicek adalah tiga kriteria di atas, bukan kesamaan teks.

Simpan BRD ini sebagai versi 1.0. Hands-on #3 menyalinnya menjadi v1.1 dan memperbaruinya dengan notulen meeting, bukan menyusun BRD dari nol lagi.

---

Sebelumnya: [Langkah 4: Pasang Skill di Claude](04-setup-skill.md)  
Berikutnya: [Hands-on #2](../hands-on-2/)
