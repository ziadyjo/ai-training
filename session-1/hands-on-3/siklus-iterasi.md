# Siklus iterasi: ulangi sebanyak perlu

Satu putaran terdiri dari tiga prompt yang sama, hanya link dan nomor versi yang berganti. Pakai ini untuk v1.3, v1.4, dan seterusnya, di dalam atau di luar kelas. Semuanya di chat yang sama dan model yang sama (Opus 5.5).

Alurnya: **review versi sekarang, perbaiki Skill dari dua temuan, salin versi dan perbarui, lalu review ulang.** Putaran berikutnya dimulai dari review ulang tadi.

Skor bisa berbeda antar run. Baca butir Skor mutu yang Gagal, bukan hanya angkanya.

## Langkah A: review versi sekarang

Ganti: `[LINK VERSI SEKARANG]`.

```
/brd-review [LINK VERSI SEKARANG] fokus kelompok fitur Role Management

Pembanding isi: Product Concept di Context Project dan notulen meeting yang terlampir di chat ini. Fokus: requirement tanpa ID atau tanpa sumber, isi yang tidak ada di sumber, dan poin notulen yang belum tercermin di BRD.

Setelah Skor mutu, bandingkan bentuk BRD dengan Reference BRD di Context (kolom tabel Requirement, pola ID, cara menulis kondisi) dan sebut paling banyak tiga selisih bentuk. Selisih isi bukan temuan.
```

Catat baris scorecard di [scorecard](scorecard.md), dan catat butir yang **Gagal**. Kalau ragu, klik tombol ulang satu kali dan baca butir yang Gagal di kedua laporan: butir yang muncul di keduanya yang dipercaya.

## Langkah B: perbaiki Skill dari dua temuan

Tidak ada yang diganti.

```
TASK
Dari laporan review BRD di atas dan laporan review sebelumnya di chat ini (atau gap list Hands-on #2), pilih dua temuan yang berulang (muncul di keduanya), berkaitan dengan butir Skor mutu yang Gagal (butir 1, 4, 5, 6, atau 8), dan bisa diperbaiki lewat aturan penyusunan BRD. Kalau yang berulang kurang dari dua, lengkapi dengan temuan lain yang memenuhi dua syarat terakhir. Utamakan temuan yang jawabannya sudah tertulis di Product Concept atau notulen tetapi BRD menulis TBC atau tidak memuatnya. Usulkan perubahan pada SKILL.md brd-draft, di bagian Aturan generate BRD atau Mode perbarui, supaya kesalahan serupa tidak terulang.

OUTPUT FORMAT
1. Dua temuan yang dipilih (ID gap), butir Skor mutu yang terkait, dan satu kalimat alasan tiap pilihan.
2. Perubahan sebagai baris lama dan baris baru, dengan nama bagian yang diubah.

RULES
- Jangan menerapkan apa pun sebelum aku menyetujui.
- Jangan mengubah bagian yang tidak terkait.
- Abaikan temuan yang penyebabnya batas connector atau pembacaan PDF (header dan footer, tabel 8.1 dari PDF, isi gambar) dan temuan yang menunggu jawaban stakeholder.
```

Balas "setuju", lalu simpan lewat kartu **Update skill** (periksa jumlah baris di **Content**, klik **Update** dan **Update skill**). Tolak bila Claude menawarkan memperbarui BRD sekarang.

## Langkah C: salin versi dan perbarui

Buka versi sekarang, klik **File > Make a copy**, beri nama versi berikutnya (mis. `BRD WebTM v1.3`), lalu ganti: `[LINK VERSI BERIKUTNYA]`, `[NOMOR VERSI]`, `[TANGGAL]`.

```
/brd-draft [LINK VERSI BERIKUTNYA]

TASK
Perbarui BRD ini ke versi [NOMOR VERSI] dengan Mode perbarui. Terapkan hanya aturan yang baru ditambahkan ke Skill di Langkah B, pada bagian BRD yang terkait dengan dua temuan yang tadi dipilih. Tampilkan daftar perubahan di chat dulu.

IDENTITAS
Versi: [NOMOR VERSI]. Tanggal: [TANGGAL].

RULES
- Bagian lain tidak diubah.
- Catat perubahan di 8.3 Changes dan tambahkan satu baris di Document Change Control.
```

Periksa daftar perubahan, balas "Setuju, tulis ke salinan.", setujui kartu izin connector, dan terima semua saran di Docs (**Tools > Review suggested edits > Accept all**). Lalu kembali ke Langkah A dengan link versi baru.

## Kapan berhenti

- Skor mutu 8 dari 8, atau butir yang tersisa hanya yang di luar jangkauan Skill: butir 7 (tabel 8.1 dari PDF, dirapikan di Sesi 3) dan header serta footer.
- Temuan yang tersisa hanya TBC yang menunggu stakeholder.
- Kalau skor turun setelah satu putaran, batalkan perubahan Skill yang tidak terkait dengan dua temuan yang dipilih.
