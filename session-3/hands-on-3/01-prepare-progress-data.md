# Langkah 1: Siapkan data progres

Durasi ±6 menit. Brief progres hanya sebaik data di backlog. Kamu mengisi Status story sesuai kondisi fiktif akhir minggu ke-2 sprint, supaya brief punya sesuatu untuk dilaporkan.

## Yang dikerjakan

1. Buka [`progress-data.md`](sources/progress-data.md). Tabelnya berisi Status tiap story.
2. Story di backlogmu berbeda dari contoh? Cocokkan lewat judul atau Requirement ID. Polanya: sekitar 30 persen Done, 20 persen In Progress, satu Blocked, sisanya Backlog.
3. Di chat Project WebTM, kirim Prompt di bawah dengan tabel yang sudah kamu sesuaikan. Kartu izin muncul: pilih **Allow once**.
4. Buka Notion dan periksa hasilnya.

## Prompt

Ganti dulu: `[TEMPEL TABEL STATUS]`.

```
CONTEXT
Database "WebTM Backlog" di halaman "WebTM" di Notion. Tabel status baru ada di bagian TABEL STATUS di bawah.

TASK
Perbarui kolom Status di database itu sesuai tabel.

RULES
- Ubah hanya kolom Status dan hanya baris yang disebut.
- Untuk story yang Blocked, tulis alasannya di akhir kolom Dependency dengan awalan "Blocked:".
- Jangan mengubah properti lain dan jangan menyentuh database WebTM MoM.

OUTPUT FORMAT
Daftar baris yang berubah.

TABEL STATUS
[TEMPEL TABEL STATUS]
```

## Cek

- Backlog punya Status Done, In Progress, Blocked, dan Backlog.
- Story Blocked punya alasan tertulis.
- Hanya kolom Status (dan alasan Blocked) yang berubah.
- Database WebTM MoM masih berisi tiga MoM tanpa perubahan (MoM Review BRD tetap tanpa tanggal).

---

Berikutnya: [Langkah 2: Tentukan format dan brief pertama](02-define-format-first-brief.md)
