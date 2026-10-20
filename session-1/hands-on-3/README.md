# Hands-on #3: Standardized BRD & Skill Refinement

Alurnya satu putaran: **perbarui, review, perbaiki Skill, perbarui lagi, review lagi**. Kamu memperbarui BRD hasil Hands-on #1 dengan notulen meeting (`/brd-draft`, Mode perbarui), mereviewnya (`/brd-review`), memilih dua temuan untuk diperbaiki di Skill, lalu membuktikan bahwa BRD berikutnya lebih baik. BRD tidak dibuat ulang dari nol: tiap versi adalah salinan versi sebelumnya. Berkas yang dipakai ada di [`sources/`](sources/).

**Aturan main:** pakai satu chat dan satu model (Opus 5.5) dari Langkah 1 sampai 5. Semua prompt tinggal disalin; hanya link, nama, dan tanggal yang diganti. Putaran perbaikan bisa diulang sebanyak perlu: prompt siap pakai ada di [`siklus-iterasi.md`](siklus-iterasi.md).

| | |
|---|---|
| Durasi | 50 menit |
| Model | Opus 5.5 untuk semua langkah (Sonnet 5.5 bila usage terbatas) |
| Hasil | BRD v1.1 (hasil pembaruan notulen) dan v1.2 (setelah Skill diperbaiki). Dua temuan yang kamu pilih hilang di v1.2, butir Skor mutu yang terkait Lulus, dan BRD terakhir menjadi dasar Sesi 2. Skor total sebagai bukti pendukung (contoh 4 menjadi 6 atau 7 dari 8). Tabel 8.1 dirapikan di Sesi 3 |

## Sebelum mulai (cek 1 menit)

- [ ] `BRD WebTM v1.0` hasil Hands-on #1 ada di Google Docs.
- [ ] Gap list Hands-on #2 masih bisa disalin (chat Hands-on #2 belum ditutup).
- [ ] Skill `brd-draft` terpasang (versi dari Hands-on #1) dan `brd-review` terpasang.
- [ ] `sources/meeting-notes.pdf` bisa dibuka. Notulen bertanggal 20 Oktober 2026 (10.00–11.00).
- [ ] Pakai Opus 5.5 dan satu chat dari Langkah 1 sampai 5.

## Urutan langkah

| Langkah | Isi | Berkas | Menit |
|---|---|---|---|
| 1 | Siapkan v1.1, notulen, dan gap list (persiapan, belum ada prompt) | [01-add-notes.md](01-add-notes.md) | ±5 |
| 2 | Cocokkan notulen dan perbarui BRD menjadi v1.1 (satu prompt) | [02-generate-brd.md](02-generate-brd.md) | ±11 |
| 3 | Review v1.1 dan catat Skor mutu | [03-review-brd.md](03-review-brd.md) | ±8 |
| 4 | Perbaiki Skill dari dua temuan | [04-improve-skill.md](04-improve-skill.md) | ±11 |
| 5 | Perbarui ke v1.2, review ulang, dan bandingkan | [05-rerun-compare.md](05-rerun-compare.md) | ±15 |

## Kecocokan dengan silabus Sesi 1

| Aktivitas silabus | Langkah |
|---|---|
| Incorporate clarified requirements | 1 dan 2 (notulen dicocokkan lalu dimasukkan ke BRD) |
| Generate BRD using current template | 2 (BRD v1.1 adalah salinan template yang diperbarui lewat `brd-draft`) |
| Review against references and source requirements | 3 (pembanding isi: Product Concept dan notulen; pembanding bentuk: Reference BRD) |
| Identify recurring inconsistencies | 4 (temuan yang muncul di gap list Hands-on #2 dan di review v1.1) |
| Update Skill after review | 4 (kartu Update skill) |
| Re-run and validate consistency | 5 (BRD v1.2, review ulang, lalu uji konsistensi dengan mengulang review) |

## Cara menyalin prompt

1. Klik tombol salin di pojok kanan blok kode. Satu blok adalah satu prompt.
2. Ganti teks dalam kurung siku, misalnya `[LINK SALINAN BARU]`, sebelum mengirim.
3. Di kotak chat, tekan Shift+Enter untuk pindah baris. Prompt yang diawali `/` harus berada di baris pertama.

## Tertinggal?

- **Langkah 2:** salin isi BRD acuan [`sources/brd-v1-1-checkpoint.md`](sources/brd-v1-1-checkpoint.md) ke salinan template baru bernama `BRD WebTM v1.1`, lalu lanjut ke Langkah 3.
- **Langkah 4:** pasang Skill [`sources/brd-draft-v2/SKILL.md`](sources/brd-draft-v2/SKILL.md) lewat **Edit** Skill, lalu lanjut ke Langkah 5.
- **Langkah 1:** gap list Hands-on #2 tidak ada? Pakai [`../hands-on-2/sources/gap-list-checkpoint.md`](../hands-on-2/sources/gap-list-checkpoint.md).

Hasilmu akan berbeda dari acuan. Pakai acuan untuk melanjutkan, bukan untuk menyalin.

## Kriteria lulus

- [ ] Semua requirement punya ID dan sumber.
- [ ] Poin notulen tercermin di BRD, dan yang belum terjawab tetap TBC.
- [ ] Dua temuan yang kamu pilih di Langkah 4 tidak muncul lagi di review v1.2, dan butir Skor mutu yang terkait Lulus.
- [ ] Skor mutu v1.2 lebih tinggi dari v1.1 (pendukung: skor bisa berbeda antar run, jadi baca butirnya, bukan hanya angkanya).
- [ ] [Scorecard](scorecard.md) terisi (baris v1.1 dan v1.2).

## Kalau bermasalah

| Masalah | Jalan keluar |
|---|---|
| Claude mengisi TBC dengan angka | Tambahkan aturan eksplisit di Aturan generate BRD: TBC dipindahkan apa adanya ke BRD |
| Skill menolak menulis atau menyusun ulang dari nol | Pastikan prompt memuat link BRD terisi dan kata "Mode perbarui". Template asli tidak pernah ditulis: salin dulu BRD terakhir lewat File > Make a copy |
| ID tidak konsisten antar bagian | Minta Claude menjelaskan aturan penomoran, lalu tulis ke Skill |
| Perubahan Skill tidak berpengaruh | Periksa bahwa kamu memakai versi terbaru dan chat baru |
