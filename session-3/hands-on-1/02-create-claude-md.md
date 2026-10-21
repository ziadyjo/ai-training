# Langkah 2: Buat CLAUDE.md

Durasi ±10 menit. `CLAUDE.md` dibaca Claude Code di awal setiap sesi. Isinya aturan proyek yang tidak mau kamu ulang tiap kali, mirip template BRD untuk Skill di Sesi 1. Ini panduan, bukan penegak: aturan yang pendek dan jelas lebih sering dipatuhi.

## Yang dikerjakan

1. Kirim prompt di bawah. Claude membaca `references/` lalu membuat `CLAUDE.md`.
2. Di mode Manual, kartu persetujuan muncul sebelum berkas dibuat. Baca isinya di diff view, lalu pilih **Accept** (setujui).
3. Bandingkan hasilnya dengan [`template`](sources/claude-md-template.md). Bila ada bagian yang kurang, minta Claude menambahkannya satu per satu. Targetnya satu layar.
4. Kirim `/context` dan pastikan `CLAUDE.md` muncul sebagai bagian konteks.

Alternatif: perintah `/init` membuat `CLAUDE.md` awal dari isi folder. Hasilnya generik, jadi tetap perlu disesuaikan dengan template.

## Prompt

```
CONTEXT
Folder ini untuk prototype HTML Role Management WebTM (admin web, pengguna Super Admin). Referensi ada di folder references: BRD v1.1 dan desain Claude Design (HTML dan screenshot).

TASK
Buat berkas CLAUDE.md di folder ini. Isinya aturan kerja untuk semua sesi berikutnya di proyek ini.

RULES
- Maksimal 25 baris, bahasa Indonesia, istilah teknis tetap Inggris.
- Isi: tujuan prototype, struktur berkas (satu index.html tanpa framework dan tanpa server, PLAN.md untuk rencana, NOTES.md untuk hal TBC), sumber kebenaran (BRD untuk perilaku, desain untuk tampilan, BRD menang bila bertentangan), cara menandai ID requirement (komentar RM-xxx di kode), cara menandai hal yang belum diputuskan (tulis TBC di layar dan catat di NOTES.md), dan larangan.
- Larangan: jangan menambah fitur di luar BRD, jangan membuat halaman login atau hapus role, jangan memakai logo atau nama orang asli dari desain, jangan menyalin kode ekspor Claude Design.
- Aturan untuk pengujian di Sesi 4: setiap tombol dan field punya teks label yang terlihat dan atribut id yang jelas.
- Aturan kerja: tampilkan rencana dan tunggu persetujuan sebelum mengubah berkas, lalu jelaskan perubahan dalam tiga kalimat.
- Jangan menyalin isi BRD ke CLAUDE.md. Cukup tunjuk lokasinya.

OUTPUT FORMAT
Tulis CLAUDE.md, lalu tampilkan isinya.
```

## Cek

- Tujuan, sumber kebenaran, penandaan ID, penandaan TBC, larangan, dan aturan label untuk pengujian semuanya ada.
- Panjang tidak lebih dari satu layar.
- `/context` menunjukkan `CLAUDE.md` terbaca.
- Tidak ada isi BRD yang disalin penuh (itu membuat konteks cepat penuh).

---

Sebelumnya: [Langkah 1: Siapkan workspace dan referensi](01-prepare-workspace.md)  
Berikutnya: [Langkah 3: Susun rencana di plan mode](03-plan-mode.md)
