# Langkah 4: Perbaiki Skill dari dua temuan

Durasi ±11 menit. Review v1.1 menemukan banyak hal, tetapi tidak semuanya salah Skill. Temuan yang **berulang** (muncul di gap list Hands-on #2 dan di review v1.1) menunjukkan aturan Skill yang kurang. Di langkah ini Claude memilih dua temuan berulang yang bisa diperbaiki lewat aturan `brd-draft` dan menyebabkan butir **Skor mutu** gagal. Kamu cukup memeriksa pilihannya dan menyetujui.

## Yang dikerjakan

1. Di chat yang sama dengan review, tempel prompt di bawah. Tidak ada yang perlu diganti.
2. Periksa dua temuan yang dipilih Claude. Pilihan yang benar **berulang** (ada di gap list Hands-on #2 dan di review v1.1), berkaitan dengan butir Skor mutu yang **Gagal**, dan bisa diperbaiki lewat aturan penyusunan (lihat tabel di bawah). Kalau Claude memilih yang lain, balas "Pilih temuan lain yang berkaitan dengan butir Skor mutu yang Gagal dan ada di tabel panduan".
3. Baca baris lama dan baris baru. Balas "setuju" bila hanya aturan yang terkait dua temuan itu yang berubah.
4. Claude menampilkan kartu **Update skill**. Buka **Content** dan periksa jumlah barisnya (mis. Current 97 baris, This draft 98 baris berarti satu baris ditambah), lalu klik **Update** dan **Update skill**. Versi lama tetap ada di riwayat. Kalau kartu tidak muncul, buka Skill, klik **Edit**, terapkan perubahan, lalu **Save version**.
5. Catat ID dua temuan itu di kolom "Temuan yang diperbaiki" baris v1.2 di [scorecard](scorecard.md).

Abaikan temuan yang penyebabnya instruksi di prompt kamu sendiri (bukan aturan Skill) dan temuan yang menunggu jawaban stakeholder. Kalau Claude menawarkan memperbarui BRD v1.1 sekarang, tolak. Perbaikan diterapkan di Langkah 5 pada salinan v1.2, supaya v1.1 tetap utuh sebagai pembanding.

## Panduan: butir Skor mutu mana yang bisa diperbaiki lewat Skill

| Butir Gagal | Bisa lewat aturan `brd-draft`? | Contoh perbaikan |
|---|---|---|
| 1 Struktur | Ya, untuk butir atau baris kosong sisa penulisan. Header dan footer tidak (batas connector) | Hapus butir kosong setelah menulis |
| 4 Dasar | Ya | Isi hanya dari Product Concept dan notulen |
| 5 Klarifikasi | Ya | Setiap poin notulen dalam cakupan tercermin di BRD |
| 6 Business Requirement | Ya | Alasan dari sumber, TBC hanya bila memang tidak ada |
| 8 TBC | Ya | Link prototype dan Overview yang ada di sumber tidak ditulis TBC |
| 7 Tabel pendukung | Tidak untuk sekarang: pembacaan tabel dari PDF dirapikan di Sesi 3 | – |
| 2, 3 | Biasanya sudah Lulus | – |

## Prompt

```
TASK
Dari laporan review BRD v1.1 di atas dan gap list Hands-on #2 yang terlampir di chat, pilih dua temuan yang berulang (muncul di keduanya), berkaitan dengan butir Skor mutu yang Gagal (butir 1, 4, 5, 6, atau 8), dan bisa diperbaiki lewat aturan penyusunan BRD. Kalau yang berulang kurang dari dua, lengkapi dengan temuan lain yang memenuhi dua syarat terakhir. Utamakan temuan yang jawabannya sudah tertulis di Product Concept atau notulen tetapi BRD menulis TBC atau tidak memuatnya. Usulkan perubahan pada SKILL.md brd-draft, di bagian Aturan generate BRD atau Mode perbarui, supaya kesalahan serupa tidak terulang.

OUTPUT FORMAT
1. Dua temuan yang dipilih (ID gap di review v1.1 dan di gap list Hands-on #2), butir Skor mutu yang terkait, dan satu kalimat alasan tiap pilihan.
2. Perubahan sebagai baris lama dan baris baru, dengan nama bagian yang diubah.

RULES
- Jangan menerapkan apa pun sebelum aku menyetujui.
- Jangan mengubah bagian yang tidak terkait.
- Abaikan temuan yang penyebabnya batas connector atau pembacaan PDF (header dan footer, tabel 8.1 dari PDF, isi gambar) dan temuan yang menunggu jawaban stakeholder.
```

## Cek

- Claude menyebut tepat dua temuan berulang, masing-masing dengan ID di kedua daftar dan butir Skor mutu yang Gagal.
- Skill punya versi baru, dan perubahannya hanya menyentuh aturan yang terkait dua temuan itu.
- Dua ID tercatat di scorecard.

Tertinggal? Pasang [`sources/brd-draft-v2/SKILL.md`](sources/brd-draft-v2/SKILL.md) lewat **Edit** Skill (Skill setelah putaran 1: link prototype, Background, poin notulen tercermin, butir kosong dihapus), lalu lanjut ke Langkah 5.

---

Sebelumnya: [Langkah 3: Review BRD](03-review-brd.md)  
Berikutnya: [Langkah 5: Perbarui, review ulang, dan bandingkan](05-rerun-compare.md)
