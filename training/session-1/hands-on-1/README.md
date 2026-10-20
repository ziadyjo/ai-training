# Hands-on #1: Build Requirement Review & BRD Skill

Kamu melengkapi Skill `brd-draft` dari starter (menulis Description), mengujinya pada Product Concept, lalu memperbaikinya sampai hasilnya konsisten. Contoh BRD jadi (`Reference BRD`) ada di Project sebagai standar bentuk dan mutu, bukan sebagai sumber isi. Ikuti langkah dari 00 sampai 05. Berkas yang dipakai ada di [`sources/`](sources/).

| | |
|---|---|
| Durasi | 50 menit |
| Model | Opus 5.5 untuk menyusun Skill. Sonnet 5.5 bila usage terbatas |
| Hasil | Skill `brd-draft` terpasang dengan Description (tulis sendiri), dan BRD pertama di Google Docs |

## Urutan langkah

| Langkah | Isi | Berkas | Menit |
|---|---|---|---|
| Quick Setup | Hubungkan Google Docs connector dan salin template | [00-quick-setup.md](00-quick-setup.md) | ±5 |
| 1 | Buat Project, unggah Product Concept dan Reference BRD, isi Instructions | [01-create-project.md](01-create-project.md) | ±4 |
| 2 | Baca template lewat connector, rangkum strukturnya, dan catat konvensi dari Reference BRD | [02-analyze-structure.md](02-analyze-structure.md) | ±6 |
| 3 | Lengkapi starter Skill: tulis Description sendiri | [03-complete-starter.md](03-complete-starter.md) | ±5 |
| 4 | Pasang Skill di Claude | [04-setup-skill.md](04-setup-skill.md) | ±6 |
| 5 | Uji dan perbaiki (BRD Role Management v1.0) | [05-test-refine.md](05-test-refine.md) | ±24 |

## Cara menyalin prompt

1. Klik tombol salin di pojok kanan blok kode. Satu blok adalah satu prompt.
2. Ganti teks dalam kurung siku, misalnya `[LINK SALINAN]`, sebelum mengirim.
3. Di kotak chat, tekan Shift+Enter untuk pindah baris. Prompt yang diawali `/` harus berada di baris pertama.

## Tertinggal?

Ambil Skill checkpoint di [`sources/brd-draft-checkpoint/`](sources/brd-draft-checkpoint/), pasang lewat Customize > Skills (lihat Langkah 4), lalu lanjut ke Hands-on #2. Hasilmu akan berbeda dari acuan. Pakai acuan untuk melanjutkan, bukan untuk menyalin.

## Kriteria lulus

- [ ] `name` berupa `brd-draft` dan `description` (maksimal 450 karakter) menyebut kapan Skill dipakai dan kapan tidak.
- [ ] Skill menulis TBC, bukan menebak, saat isi draft kurang, dan mengikuti bagian-bagian template BRD.
- [ ] BRD tampil di chat dan disetujui sebelum ditulis ke Google Docs.
- [ ] Isi requirement berasal dari Product Concept. Fitur yang hanya ada di Reference BRD tidak muncul sebagai isi, dan ditulis TBC bila perlu.

## Kalau bermasalah

| Masalah | Jalan keluar |
|---|---|
| Skill tidak terpanggil | Ketik `/` lalu pilih Skill, atau sebut nama Skill di prompt. Periksa description |
| Skill langsung menulis tanpa menampilkan draft | Tambahkan aturan: jangan menulis ke Google Docs sebelum BRD disetujui di chat |
| Skill menolak menulis penuh | Salinan sudah terisi, itu penjagaan. Untuk memperbaiki BRD yang sudah terisi, minta memperbarui bagian tertentu (Mode perbarui). Untuk BRD baru dari nol, buat salinan baru dari template asli |
| Description terpotong di tab Overview | Batas 500 karakter. Perpendek, lalu simpan versi baru |
| Kuota cepat habis | Turun ke Sonnet 5.5, buka chat baru per tugas |
