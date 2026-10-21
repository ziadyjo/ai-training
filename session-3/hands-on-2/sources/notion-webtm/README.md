# Template Notion WebTM

Isi halaman **WebTM** di Notion-mu: satu link yang menjadi single source of truth catatan meeting proyek. Halaman ini langsung menampilkan daftar MoM, dan tiap MoM dibuka untuk melihat detailnya (info meeting, pembahasan, keputusan, action item). Dipakai di Hands-on #2 (backlog) dan Hands-on #3 (scheduled task membaca MoM).

```
WebTM                      (halaman induk, beri izin ke Claude)
├── WebTM MoM              (database inline, tampil langsung: Name, Tanggal meeting, Jenis)
│   ├── MoM Kickoff Role Management                 7 Oktober 2026
│   ├── MoM Sprint Planning                         14 Oktober 2026
│   └── MoM Review BRD WebTM Role Management v1.1   Tanggal meeting kosong, diisi di Hands-on #3
└── WebTM Backlog          (database, dibuat Claude di Hands-on #2 Langkah 3)
```

MoM Review BRD sengaja tanpa tanggal. Di Hands-on #3 kamu mengisi tanggalnya dengan hari ini: itu tanda MoM baru masuk, dan scheduled task akan membacanya.

Dua cara mendapatkannya:

| Cara | Langkah |
|---|---|
| A. Duplikat template (disarankan) | Buka [template Notion WebTM](https://proximal-tray-c79.notion.site/WebTM-400514a7b02481c38703dda28d8824b0), klik **Duplicate** di kanan atas, pilih workspace milikmu. Halaman **WebTM** muncul di sidebar Notion-mu |
| B. Dibuat Claude lewat connector | Ikuti Prompt C di [Langkah 1 Hands-on #2](../../01-connect-notion-user-stories.md) dengan tiga berkas MoM di folder ini sebagai lampiran |

| Berkas | Isi |
|---|---|
| [`mom-kickoff.md`](mom-kickoff.md) | MoM lama, 7 Oktober 2026 |
| [`mom-sprint-planning.md`](mom-sprint-planning.md) | MoM lama, 14 Oktober 2026 |
| [`mom-review-brd.md`](mom-review-brd.md) | MoM Review BRD v1.1, demo case Hands-on #3 |

Semua isi fiktif.
