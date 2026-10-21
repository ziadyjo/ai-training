# Langkah 2: Hasilkan test case v1

Durasi ±15 menit. Kamu menjalankan Skill pada beberapa requirement dan memeriksa hasilnya di chat. Belum ada yang dijalankan di browser.

## Yang dikerjakan

1. Di chat baru dalam Project WebTM, pilih **Sonnet 5.5**. Ketik `/qa-test`, pilih Skill dari daftar, lalu tempel prompt di bawah dengan link BRD dan link board Miro-mu.
2. Lampirkan screenshot mockup Claude Design (Daftar Role dan Create New Role) lewat tombol lampiran. Tidak ada mockup? Pakai gambar di `session-3/hands-on-1/sources/mockup-acuan/`.
3. Skill membaca BRD dan board lewat connector (kartu izin muncul, pilih **Allow once**). Dia menampilkan tabel test case, coverage matrix, **Cek mutu test case** (N dari 6), dan daftar pertanyaan.
4. Reviewer membaca hasilnya dengan daftar di bagian Cek. Driver tidak memperbaiki apa pun dulu.
5. Simpan tabelnya: kamu memakainya di Langkah 3 sampai 5. Scorecard baris v1 diisi di Langkah 4.

## Prompt

Ganti dulu: `[LINK BRD]` dan `[LINK BOARD MIRO]`.

```
/qa-test [LINK BRD]

CONTEXT
Alur Create New Role dan Daftar Role di WebTM (admin web, pengguna Super Admin). Flow: frame Flow Create New Role di board Miro ini, hanya dibaca: [LINK BOARD MIRO]. Mockup: screenshot Claude Design terlampir.

TASK
Susun test case untuk requirement RM-001, RM-004, dan RM-005. Jangan menjalankan apa pun.

RULES
- Setiap cabang keputusan di flow punya minimal satu test case.
- Expected result tampilan (letak tombol, label, kolom) mengikuti mockup. Aturan, validasi, dan pesan mengikuti BRD.
- Bila BRD, flow, dan mockup berbeda, tulis sebagai pertanyaan, jangan memilih sendiri.
- Jangan mengubah board.

OUTPUT FORMAT
Tabel test case, coverage matrix, Cek mutu test case, dan daftar pertanyaan. Berhenti setelah itu.
```

## Cek

- Setiap test case punya ID requirement (atau "tanpa rujukan").
- Langkah bernomor dan satu aksi per langkah.
- Expected result bisa dilihat di layar, dan yang menyangkut tampilan merujuk ke mockup.
- Isi pesan error yang TBC di BRD tidak dikarang.
- Cabang Ya dan Tidak pada keputusan flow (Role Name sama dengan role existing) masing-masing punya test case.
- Ada baris coverage untuk ketiga requirement, termasuk bagian yang belum punya test case.

---

Sebelumnya: [Langkah 1: Bangun qa-test dari starter](01-build-qa-test.md)  
Berikutnya: [Langkah 3: Prioritas dan coverage matrix](03-priority-coverage.md)
