# Langkah 3: Review BRD

Durasi ±8 menit. Struktur template dibaca Skill dari `references/brd-structure.md`. Product Concept dan notulen meeting adalah pembanding isi. Reference BRD adalah pembanding bentuk: di akhir laporan, Claude menyebut selisih bentuk BRD-mu dengan Reference BRD.

## Yang dikerjakan

1. Di chat yang sama, tempel prompt di bawah dengan link BRD v1.1. Baris pertama harus `/brd-review`.
2. Skill menampilkan tabel gap seperti di Hands-on #2, dan di akhir **Skor mutu** (N dari 8) beserta satu baris scorecard.
3. Salin baris scorecard itu ke [scorecard](scorecard.md) (baris v1.1). Itu satu-satunya yang perlu dicatat di langkah ini.

## Prompt

Ganti dulu: `[LINK SALINAN V1.1]`.

```
/brd-review [LINK SALINAN V1.1] fokus kelompok fitur Role Management

Pembanding isi: Product Concept di Context Project dan notulen meeting yang terlampir di chat ini. Fokus: requirement tanpa ID atau tanpa sumber, isi yang tidak ada di sumber, dan poin notulen yang belum tercermin di BRD.

Setelah Skor mutu, bandingkan bentuk BRD dengan Reference BRD di Context (kolom tabel Requirement, pola ID, cara menulis kondisi) dan sebut paling banyak tiga selisih bentuk. Selisih isi bukan temuan.
```

## Cek

- Laporan dibuka dengan baris "Direview: ... | Pembanding: ..." dan memuat Skor mutu, baris scorecard, dan paling banyak tiga selisih bentuk dengan Reference BRD.
- Tiap temuan menunjuk bagian dan ID di BRD, mengutip kalimat BRD dan sumbernya.
- Skor bisa berbeda antar run, bahkan untuk BRD yang sama. Kalau ragu, jalankan review sekali lagi dan baca butir yang Gagal, bukan hanya angkanya.
- Catat butir Skor mutu yang **Gagal**. Itu bahan memilih dua temuan di Langkah 4.
- Skor v1.1 bisa lebih rendah dari v1.0. Itu wajar: butir 3 (jejak sumber) dan butir 5 (klarifikasi) otomatis Lulus di v1.0 karena belum ada klarifikasi, dan baru dinilai sungguhan di v1.1. Yang dibandingkan nanti adalah v1.1 dan v1.2.
- Header dan footer tidak dinilai (connector tidak membacanya). Ganti manual di Google Docs bila perlu.

---

Sebelumnya: [Langkah 2: Cocokkan notulen dan perbarui BRD menjadi v1.1](02-generate-brd.md)  
Berikutnya: [Langkah 4: Perbaiki Skill dari dua temuan](04-improve-skill.md)
