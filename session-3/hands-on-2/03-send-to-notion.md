# Langkah 3: Kirim ke Notion

Durasi ±7 menit. Menulis ke Notion mengubah data di luar chat, jadi draf di chat harus sudah kamu periksa lebih dulu. Claude membuat database **WebTM Backlog** di bawah halaman **WebTM** dan mengisi baris dari tabel.

## Yang dikerjakan

1. Kirim Prompt di bawah. Claude menyiapkan database dan baris. Kartu izin muncul: pilih **Allow once**, lalu periksa halaman yang dituju.
2. Buka Notion dan periksa: database **WebTM Backlog** ada di bawah halaman **WebTM**, di samping **WebTM MoM**, jumlah baris sama dengan tabel, properti sesuai skema.
3. Bandingkan dua atau tiga baris dengan tabel di chat. Isi acceptance criteria tidak boleh terpotong.
4. Hanya kamu yang mengubah isi Notion setelah ini kecuali kamu meminta: Claude tidak boleh menghapus atau menimpa baris yang sudah ada tanpa persetujuan.

## Prompt

```
CONTEXT
Tabel backlog di chat ini sudah kuperiksa. Halaman "WebTM" di Notion berisi database "WebTM MoM".

TASK
Kirim tabel backlog tadi ke Notion sebagai database baru "WebTM Backlog" di bawah halaman "WebTM".

RULES
- Properti: Story ID (judul), User Story (teks), Acceptance Criteria (teks), Requirement ID (teks), Priority (select: Must, Should, Could), Size (select: S, M, L), Dependency (teks), Status (select: Backlog, In Progress, Done, Blocked), Sprint (teks).
- Satu baris per story dari tabel.
- Jangan mengubah atau menghapus halaman lain, termasuk database WebTM MoM.

OUTPUT FORMAT
Jumlah baris yang dibuat.
```

## Prompt perbaikan (bila properti kurang)

Ganti dulu: `[NAMA PROPERTI]`.

```
CONTEXT
Database "WebTM Backlog" di Notion belum punya properti [NAMA PROPERTI].

TASK
Tambahkan properti itu dan isi untuk baris yang sudah ada dari tabel di chat.

RULES
- Jangan membuat database baru dan jangan menghapus baris.

OUTPUT FORMAT
Daftar baris yang diisi.
```

## Alternatif: Google Docs

Bila Notion tidak tersambung, minta tabel yang sama ditulis ke Google Docs baru bernama `WebTM Backlog`:

```
CONTEXT
Tabel backlog di chat ini sudah kuperiksa. Notion tidak tersambung.

TASK
Buat dokumen Google Docs baru bernama "WebTM Backlog" berisi tabel backlog tadi.

RULES
- Kolom sama dengan tabel di chat.
- Jangan mengubah dokumen lain.

OUTPUT FORMAT
Link dokumen dan jumlah baris.
```

## Cek

- Database ada dengan properti sesuai skema.
- Jumlah baris di Notion sama dengan jumlah story.
- Dua atau tiga baris cocok dengan tabel di chat, tanpa teks terpotong.
- Tidak ada halaman lain yang berubah.

---

Sebelumnya: [Langkah 2: Draf backlog dan Cek mutu](02-draft-backlog-quality-check.md)  
Berikutnya: [Langkah 4: Review dependency dan iterasi](04-review-dependency-iterate.md)
