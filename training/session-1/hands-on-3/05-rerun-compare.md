# Langkah 5: Perbarui ke v1.2, review ulang, dan bandingkan

Durasi ±15 menit. BRD tidak dibuat ulang dari nol. v1.1 disalin menjadi v1.2, Claude menerapkan hanya aturan yang baru kamu simpan di Skill, lalu `brd-review` dijalankan lagi. Yang berbeda antara v1.1 dan v1.2 hanya perbaikan itu, jadi selisihnya bisa dibaca langsung.

## Yang dikerjakan

1. Buka `BRD WebTM v1.1`, klik **File > Make a copy**, beri nama `BRD WebTM v1.2`, lalu salin link-nya.
2. Di chat yang sama, tempel **Prompt 1** di bawah dengan link v1.2. Baris pertama harus `/brd-draft`. Kalau Claude tidak memakai aturan baru, buka chat baru dan sebut dua ID gap dari Langkah 4 di bagian TASK.
3. Periksa daftar perubahan di chat. Isinya hanya bagian yang terkait dua temuan itu, ditambah 8.3 Changes dan Document Change Control. Balas "Setuju, tulis ke salinan.", lalu setujui kartu izin connector. Terima semua saran di Docs (**Tools > Review suggested edits > Accept all**).
4. Di chat yang sama, tempel **Prompt 2** dengan link v1.2. Salin baris scorecard di akhir laporan ke [scorecard](scorecard.md) (baris v1.2).
5. Uji konsistensi: klik tombol ulang (ikon panah melingkar di bawah jawaban review) satu kali, lalu bandingkan butir Skor mutu yang Gagal di kedua laporan. Butir yang sama berarti hasilnya konsisten. Kalau berbeda, catat butir mana, dan percayai butir yang muncul di keduanya.
6. Bandingkan v1.1 dan v1.2 di scorecard: dua temuan dari Langkah 4 sudah tidak muncul di tabel gap dan butir terkaitnya Lulus. Skor total biasanya ikut naik, tetapi bisa berbeda antar run. Butir 7 (tabel 8.1 dari PDF) kemungkinan masih Gagal; itu dirapikan di Sesi 3.

## Prompt 1: perbarui ke v1.2

Ganti dulu: `[LINK SALINAN V1.2]`, `[Tanggal]`.

```
/brd-draft [LINK SALINAN V1.2]

TASK
Perbarui BRD ini ke versi 1.2 dengan Mode perbarui. Terapkan hanya aturan yang baru ditambahkan ke Skill di Langkah 4, pada bagian BRD yang terkait dengan dua temuan yang tadi dipilih. Tampilkan daftar perubahan di chat dulu.

IDENTITAS
Versi: 1.2. Tanggal: [Tanggal].

RULES
- Bagian lain tidak diubah.
- Catat perubahan di 8.3 Changes dan tambahkan satu baris di Document Change Control.
```

## Prompt 2: review ulang

Ganti dulu: `[LINK SALINAN V1.2]`.

```
/brd-review [LINK SALINAN V1.2] fokus kelompok fitur Role Management

Pembanding isi: Product Concept di Context Project dan notulen meeting yang terlampir di chat ini. Reference BRD hanya untuk membandingkan bentuk. Fokus: requirement tanpa ID atau tanpa sumber, isi yang tidak ada di sumber, dan poin notulen yang belum tercermin di BRD.
```

## Cek

- Dua temuan dari Langkah 4 tidak muncul lagi di tabel gap v1.2.
- Butir Skor mutu yang terkait dua temuan itu sekarang Lulus. Itu bukti utamanya.
- Skor mutu v1.2 lebih tinggi dari v1.1 (contoh: 4 menjadi 6 atau 7 dari 8). Ini bukti pendukung: skor bisa berbeda antar run, jadi baca butirnya. Kalau skor turun, batalkan perubahan Skill yang tidak terkait dengan dua temuan itu.
- Bagian BRD di luar dua temuan itu tidak berubah. Kalau banyak bagian lain ikut berubah, aturan Skill terlalu luas.
- Review v1.2 bisa memunculkan temuan baru akibat perbaikan, dan itu wajar. Contoh: kalimat pembuka 8.3 ("sudah melalui diskusi antara FA dengan tim Tech") tidak cocok dengan perubahan hasil review, atau dua label Prototype Desktop dan Prototype Mobile berubah menjadi satu label Prototype. Catat sebagai bahan putaran berikutnya.
- Angka peserta akan berbeda. Yang dicek adalah arahnya dan aturan Skill mana yang menyebabkan perubahan.

## Hasil yang diharapkan

- Semua requirement punya ID dan sumber.
- Poin notulen tercermin di BRD, dan yang belum terjawab tetap TBC.
- Dua temuan yang dipilih hilang di v1.2, dan butir Skor mutu yang terkait Lulus.

## Tambahan (opsional, bukan bagian 50 menit)

- **Selisih bentuk dengan Reference BRD.** Review di Langkah 3 sudah menyebut paling banyak tiga selisih bentuk. Selisih bentuk yang berulang adalah bahan putaran berikutnya; selisih isi (mis. Managed Roles) bukan kekurangan BRD-mu bila tidak ada di Product Concept dan notulen.
- **Putaran berikutnya (v1.3, v1.4, ...).** Pakai [`siklus-iterasi.md`](siklus-iterasi.md): tiga prompt siap salin yang diulang sebanyak perlu. Berhenti bila Skor mutu 8 dari 8 dan sisanya hanya TBC yang menunggu stakeholder.
- **Demo instruktur v1.3.** Instruktur memasang Skill `brd-draft` terlengkap (ditambah fitur gugur dihapus beserta turunannya, dan satu pertanyaan TBC per sub-bagian), salin v1.2 menjadi v1.3, tempel jawaban klarifikasi fiktif yang disiapkan instruktur, lalu perbarui lewat Mode perbarui. Skor yang diharapkan tetap sekitar 7 dari 8; 8 dari 8 tercapai setelah tabel 8.1 dirapikan di Sesi 3.

---

Sebelumnya: [Langkah 4: Perbaiki Skill dari dua temuan](04-improve-skill.md)
