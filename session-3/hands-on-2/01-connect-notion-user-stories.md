# Langkah 1: Hubungkan Notion dan buat user story

Durasi ±10 menit. Notion adalah tempat backlog dan MoM proyek tinggal. Claude membacanya lewat connector, dan menulis ke sana atas izinmu. Kamu menyiapkan halaman **WebTM** di Notion-mu, menghubungkannya ke Claude, lalu meminta Claude menyusun user story dari BRD.

## Yang dikerjakan

1. Siapkan halaman **WebTM** di Notion milikmu (pakai akun Notion pribadi, bukan akun tamu di workspace orang lain):
   - Cara A: buka [template Notion WebTM](https://proximal-tray-c79.notion.site/WebTM-400514a7b02481c38703dda28d8824b0). Halaman WebTM langsung menampilkan daftar MoM. Klik **Duplicate** di kanan atas, pilih workspace-mu. Notion menamai salinannya **WebTM (1)**: klik judulnya dan ganti menjadi `WebTM` (tanpa angka), karena prompt di hands-on memanggil halaman itu dengan nama `WebTM`.
   - Cara B: lewati dulu, Claude membuatnya di poin 4 dengan Prompt C.
   - Isinya dijelaskan di [`sources/notion-webtm/`](sources/notion-webtm/README.md).
2. Di aplikasi Claude buka **Customize**, lalu **Connectors**. Cari **Notion** di tab Discover, klik **Connect**, login ke Notion, dan beri izin ke halaman **WebTM**. Connector ini juga terbaca di tab Code dan di Scheduled.
3. Buka chat baru di Project **WebTM Role & User Management** dan pilih **Sonnet 5.5**. Cek koneksi dengan Prompt A. Kartu izin muncul: pilih **Allow once**.
4. Pakai Cara B? Lampirkan tiga berkas MoM dari [`sources/notion-webtm/`](sources/notion-webtm/README.md) lewat tombol lampiran, kirim Prompt C, lalu ulangi Prompt A.
5. Kirim Prompt B untuk menyusun user story dari BRD. Claude membaca BRD lewat connector Google Docs (pilih **Allow once**).
6. Tulis temuanmu: berapa story, mana yang TBC.

## Prompt A: cek koneksi

```
CONTEXT
Halaman "WebTM" di Notion berisi database "WebTM MoM".

TASK
Cari halaman "WebTM" di Notion dan sebutkan isinya.

RULES
- Hanya baca. Jangan membuat atau mengubah apa pun.

OUTPUT FORMAT
Daftar database di halaman itu, lalu judul halaman di database "WebTM MoM".
```

## Prompt B: user story

Ganti dulu: `[LINK BRD]`.

```
CONTEXT
BRD WebTM v1.1: [LINK BRD]. Fokus pada bagian 7 Requirement (RM-001 sampai RM-007) dan 8.2 Rules. Pengguna: Super Admin.

TASK
Susun user story dari requirement BRD. Target 8 sampai 12 story. Jangan menulis ke Notion dulu.

RULES
- Format: "Sebagai [peran], saya ingin [tujuan], supaya [manfaat]".
- Tiap story: judul, ID requirement sumber (RM-xxx), minimal dua acceptance criteria yang bisa dijawab ya atau tidak.
- Satu story satu tujuan. Pecah bila terlalu besar.
- Requirement yang masih TBC (mis. pesan validasi, mapping Change Log) tidak dijadikan isi story berisi tebakan. Masukkan ke bagian Pertanyaan dengan ID requirement-nya.
- Jangan menambah story di luar BRD.

OUTPUT FORMAT
Daftar story bernomor S-01 dan seterusnya, lalu bagian Pertanyaan.
```

## Prompt C: buat halaman WebTM (hanya Cara B)

Lampirkan dulu: `mom-kickoff.md`, `mom-sprint-planning.md`, dan `mom-review-brd.md`.

```
CONTEXT
Tiga berkas MoM terlampir: mom-kickoff.md, mom-sprint-planning.md, dan mom-review-brd.md.

TASK
Buat halaman "WebTM" di Notion, lalu database "WebTM MoM" di dalamnya, dan isi dengan tiga halaman dari berkas terlampir.

RULES
- Properti database: Name (judul), Tanggal meeting (tanggal), Jenis (select: Kickoff, Sprint Planning, Review BRD).
- Isi halaman persis teks berkasnya.
- "MoM Kickoff Role Management": Tanggal meeting 2026-10-07, Jenis Kickoff.
- "MoM Sprint Planning": Tanggal meeting 2026-10-14, Jenis Sprint Planning.
- "MoM Review BRD WebTM Role Management v1.1": Tanggal meeting dikosongkan, Jenis Review BRD.
- Jangan mengubah halaman lain.

OUTPUT FORMAT
Daftar halaman yang dibuat.
```

## Cek

- Halaman bernama persis **WebTM** (bukan "WebTM (1)"). Notion tersambung dan Claude menemukannya dengan database **WebTM MoM** berisi tiga MoM (MoM Review BRD tanpa tanggal).
- Setiap story punya ID requirement (RM-xxx) dan acceptance criteria yang bisa diperiksa.
- Requirement TBC ada di Pertanyaan, bukan di story.
- Belum ada backlog yang ditulis ke Notion.

---

Berikutnya: [Langkah 2: Draf backlog dan Cek mutu](02-draft-backlog-quality-check.md)
