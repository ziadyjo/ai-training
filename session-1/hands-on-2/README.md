# Hands-on #2: Requirement Gap Analysis

Kamu memakai Skill `brd-review` untuk memeriksa BRD hasil Hands-on #1 terhadap Product Concept, menemukan gap, lalu mengubahnya jadi pertanyaan klarifikasi untuk stakeholder. Berkas yang dipakai ada di [`sources/`](sources/).

| | |
|---|---|
| Durasi | 30 menit |
| Model | Opus 5.5 untuk dokumen panjang. Sonnet 5.5 sebagai pembanding opsional |
| Hasil | Gap list dengan kutipan BRD dan sumber, serta clarification questions |

## Urutan langkah

| Langkah | Isi | Berkas | Menit |
|---|---|---|---|
| 1 | Pasang `brd-review` | [01-setup-skill.md](01-setup-skill.md) | ±3 |
| 2 | Jalankan `/brd-review` | [02-run-review.md](02-run-review.md) | ±8 |
| 3 | Periksa dan rapikan hasil | [03-check-results.md](03-check-results.md) | ±12 |
| 4 | Tulis clarification questions | [04-write-questions.md](04-write-questions.md) | ±7 |

## Cara memakai prompt

Klik tombol salin di pojok blok kode, ganti teks dalam kurung siku, lalu kirim. Tekan Shift+Enter untuk pindah baris.

## Tertinggal?

Ambil gap list di [`sources/gap-list-checkpoint.md`](sources/gap-list-checkpoint.md), lalu lanjut ke Hands-on #3. Hasilmu akan berbeda dari acuan. Pakai acuan untuk melanjutkan, bukan untuk menyalin.

## Kriteria lulus

- [ ] Kutipan di baris yang diperiksa ditemukan di BRD dan Product Concept (bukan Reference BRD).
- [ ] Tiap gap punya satu pertanyaan tertutup dan satu peran penjawab (gap gabungan dipecah di Langkah 4).
- [ ] [Scorecard](scorecard.md) terisi (baris v1.0).

## Kalau bermasalah

| Masalah | Jalan keluar |
|---|---|
| Yang terpanggil `brd-draft` | Pastikan baris pertama `/brd-review`, atau pilih `brd-review` dari daftar `/` |
| Skill tidak bisa membaca BRD | Pastikan Google Docs connector Connected. Cadangannya, tempel isi BRD ke chat |
| Hasil berbeda dari temanmu | Normal. Bandingkan kutipannya, bukan jumlah gap |
| Skor mutu butir 1 gagal karena header dan footer | Skill tidak menilai header dan footer (connector tidak membacanya). Gantilah manual di Google Docs |
