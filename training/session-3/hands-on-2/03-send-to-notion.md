# Langkah 3: Kirim ke Notion

Durasi ±7 menit. Menulis ke Notion mengubah data di luar chat, jadi draf di chat harus sudah kamu periksa lebih dulu. Claude membuat database di bawah halaman `WebTM Backlog` dan mengisi baris dari tabel.

## Yang dikerjakan

1. Kirim Prompt di bawah. Claude menyiapkan database dan baris. Kartu izin muncul: pilih **Allow once**, lalu periksa halaman yang dituju.
2. Buka Notion dan periksa: database ada di bawah `WebTM Backlog`, jumlah baris sama dengan tabel, properti sesuai skema.
3. Bandingkan dua atau tiga baris dengan tabel di chat. Isi acceptance criteria tidak boleh terpotong.
4. Hanya kamu yang mengubah isi Notion setelah ini kecuali kamu meminta: Claude tidak boleh menghapus atau menimpa baris yang sudah ada tanpa persetujuan.

## Prompt

```
Kirim tabel backlog tadi ke Notion. Buat database baru bernama "WebTM Backlog" di bawah halaman "WebTM Backlog" dengan properti: Story ID (judul), User Story (teks), Acceptance Criteria (teks), Requirement ID (teks), Priority (select: Must, Should, Could), Size (select: S, M, L), Dependency (teks), Status (select: Backlog, In Progress, Done, Blocked), Sprint (teks). Isi satu baris per story dari tabel. Jangan mengubah atau menghapus halaman lain. Setelah selesai, sebutkan jumlah baris yang dibuat.
```

## Prompt perbaikan (bila properti kurang)

Ganti dulu: `[NAMA PROPERTI]`.

```
Database belum punya properti [NAMA PROPERTI]. Tambahkan properti itu dan isi untuk baris yang sudah ada dari tabel di chat. Jangan membuat database baru dan jangan menghapus baris.
```

## Alternatif: Google Docs

Bila Notion tidak tersambung, minta tabel yang sama ditulis ke Google Docs baru bernama `WebTM Backlog`:

```
Buat dokumen Google Docs baru bernama "WebTM Backlog" berisi tabel backlog tadi dengan kolom yang sama. Jangan mengubah dokumen lain.
```

## Cek

- Database ada dengan properti sesuai skema.
- Jumlah baris di Notion sama dengan jumlah story.
- Dua atau tiga baris cocok dengan tabel di chat, tanpa teks terpotong.
- Tidak ada halaman lain yang berubah.

---

Sebelumnya: [Langkah 2: Draf backlog dan Cek mutu](02-draft-backlog-quality-check.md)  
Berikutnya: [Langkah 4: Review dependency dan iterasi](04-review-dependency-iterate.md)
