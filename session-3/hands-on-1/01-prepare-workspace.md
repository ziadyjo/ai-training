# Langkah 1: Siapkan workspace dan referensi

Durasi ±10 menit. Claude Code bekerja di satu folder. Semua yang perlu dibaca Claude harus ada di folder itu, jadi kamu menyiapkannya dulu.

## Yang dikerjakan

1. Buat folder `webtm-prototype` di tempat yang mudah kamu temukan (mis. Documents), dengan subfolder `references`.
2. Ekspor desain dari Claude Design (Sesi 2):
   - Buka desain `WebTM Role Management` di **Artifacts**, klik **Share** di kanan atas, lalu pilih tab **Export**.
   - Klik **HTML** (Standalone web page) dan simpan berkasnya ke `references/` dengan nama `claude-design.html`.
   - Klik **PNG** untuk gambar desain, dan simpan sebagai `references/mockup-create-role.png`. Untuk satu screen saja (mis. Daftar Role), pakai ikon unduh di pojok judul screen itu dan simpan sebagai `references/mockup-daftar-role.png`. Claude membaca gambar lebih pasti daripada kode ekspor.
   - Menu ekspor tidak ada di akunmu atau hasilnya kosong? Ambil screenshot dua screen (Daftar Role dan Create New Role). Tidak punya desain? Salin gambar dari [`sources/mockup-acuan/`](sources/mockup-acuan/).
3. Unduh BRD v1.1 dari Google Docs: **File**, **Download**, **PDF Document**, simpan sebagai `references/brd.pdf`. Tertinggal: salin [`sources/brd-v1-1.pdf`](sources/brd-v1-1.pdf).
4. Buka Claude Code di folder itu: di aplikasi Claude, klik **Code** di bagian atas, pilih **Local**, klik **Select folder**, lalu pilih `webtm-prototype`. Bila ditanya apakah folder ini dipercaya, pilih percaya (trust).
5. Lihat di bawah kotak input: mode izin aktif dan model. Pilih model **Sonnet 5.5** dan mode **Manual** dulu.
6. Kirim prompt di bawah. Claude hanya boleh membaca dan menjawab.

## Prompt

```
CONTEXT
Folder ini berisi subfolder references dengan BRD v1.1 dan desain Claude Design (HTML dan screenshot).

TASK
Sebutkan berkas yang ada di folder references dan isi tiap berkas dalam satu kalimat.

RULES
- Untuk BRD, sebutkan ID requirement yang ada.
- Untuk desain, sebutkan screen yang terlihat.
- Jangan membuat atau mengubah berkas apa pun.

OUTPUT FORMAT
Daftar bernomor: nama berkas, ringkasan satu kalimat.
```

## Cek

- Claude menyebut semua berkas, termasuk gambar mockup.
- Untuk BRD, Claude menyebut RM-001 sampai RM-007. Kalau BRD tidak terbaca, unduh ulang sebagai Markdown (**File**, **Download**, **Markdown**) dan simpan sebagai `brd.md`.
- Untuk desain, Claude menyebut minimal Daftar Role dan Create New Role.
- Tidak ada berkas baru di folder (Claude hanya membaca).

---

Berikutnya: [Langkah 2: Buat CLAUDE.md](02-create-claude-md.md)
