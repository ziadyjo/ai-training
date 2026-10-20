# Langkah 1: Siapkan data progres dan MoM

Durasi ±6 menit. Brief progres hanya sebaik data di backlog. Kamu mengisi Status story sesuai kondisi fiktif, dan membaca MoM sprint review yang dipakai di Langkah 4.

## Yang dikerjakan

1. Buka [`progress-data.md`](sources/progress-data.md). Tabelnya berisi Status tiap story pada akhir minggu fiktif ini.
2. Perbarui kolom Status di backlog (Notion atau Google Docs) sesuai tabel itu. Cara cepat: kirim Prompt di bawah, lalu periksa hasilnya.
3. Buka [`sprint-review-mom.md`](sources/sprint-review-mom.md) dan baca dua kali. Belum dipakai sampai Langkah 4.
4. Pastikan backlog punya minimal satu story Done, satu In Progress, dan satu Blocked.

Story di backlogmu berbeda dari contoh. Sesuaikan: tandai kira-kira 30 persen Done, 30 persen In Progress, 1 sampai 2 Blocked, sisanya Backlog.

## Prompt

Ganti dulu: `[TEMPEL TABEL STATUS]`.

```
Perbarui kolom Status di database "WebTM Backlog" di Notion sesuai tabel di bawah. Ubah hanya kolom Status dan hanya baris yang disebut. Tambahkan alasan di kolom Dependency untuk story yang Blocked. Jangan mengubah properti lain. Setelah selesai, sebutkan baris yang berubah.

[TEMPEL TABEL STATUS]
```

## Cek

- Backlog punya Status Done, In Progress, Blocked, dan Backlog.
- Story Blocked punya alasan tertulis.
- Hanya kolom Status (dan alasan Blocked) yang berubah.

---

Berikutnya: [Langkah 2: Tentukan format dan brief pertama](02-define-format-first-brief.md)
