# Langkah 2: Buat CLAUDE.md

Durasi ±10 menit. `CLAUDE.md` dibaca Claude Code di awal setiap sesi. Isinya aturan proyek yang tidak mau kamu ulang tiap kali. Ini panduan, bukan penegak: aturan yang pendek dan jelas lebih sering dipatuhi.

## Yang dikerjakan

1. Di Claude Code, kirim prompt di bawah. Claude membaca `references/` lalu membuat `CLAUDE.md`.
2. Buka `CLAUDE.md` yang dihasilkan. Ganti atau tambah dengan [`template`](sources/claude-md-template.md) bila ada yang kurang. Targetnya satu layar, bukan berhalaman-halaman.
3. Kirim `/context` (tab Code dan terminal sama) dan pastikan `CLAUDE.md` muncul sebagai bagian konteks.
4. Alternatif: perintah `/init` (tab Code dan terminal sama) membuat `CLAUDE.md` awal dari isi folder. Hasilnya generik, jadi tetap edit.

## Prompt

```
CONTEXT
Folder ini untuk prototype HTML alur Create New Role di WebTM (admin web, pengguna Super Admin). Referensi ada di folder references: BRD, brief UI, dan mockup.

TASK
Buat berkas CLAUDE.md di folder ini. Isinya aturan kerja untuk semua sesi berikutnya di proyek ini.

RULES
- Maksimal 25 baris, bahasa Indonesia, istilah teknis tetap Inggris.
- Isi: tujuan prototype, struktur berkas (satu index.html, tanpa framework, tanpa server), sumber kebenaran (BRD lebih tinggi dari mockup), cara menandai ID requirement (komentar RM-xxx di kode), cara menandai hal yang belum diputuskan (tulis TBC di layar dan catat di NOTES.md), dan larangan (jangan menambah fitur di luar BRD, jangan membuat halaman login).
- Aturan kerja: tampilkan rencana dan tunggu persetujuan sebelum mengubah berkas, lalu jelaskan perubahan dalam tiga kalimat.
- Jangan menyalin isi BRD ke CLAUDE.md. Cukup tunjuk lokasinya.

OUTPUT FORMAT
Tulis CLAUDE.md, lalu tampilkan isinya.
```

## Cek

- Tujuan, sumber kebenaran, penandaan ID, penandaan TBC, dan larangan fitur tambahan semuanya ada.
- Panjang tidak lebih dari satu layar.
- `/context` menunjukkan `CLAUDE.md` terbaca.
- Tidak ada isi BRD yang disalin penuh (itu membuat konteks cepat penuh).

---

Sebelumnya: [Langkah 1: Siapkan workspace dan referensi](01-prepare-workspace.md)  
Berikutnya: [Langkah 3: Susun rencana di plan mode](03-plan-mode.md)
