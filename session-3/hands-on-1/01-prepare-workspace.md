# Langkah 1: Siapkan workspace dan referensi

Durasi ±10 menit. Claude Code bekerja di satu folder. Semua yang perlu dibaca Claude harus ada di folder itu, jadi kamu menyiapkannya dulu.

## Yang dikerjakan

1. Buat folder `webtm-prototype` di tempat yang mudah kamu temukan, dengan subfolder `references`.
2. Masukkan ke `references/`: mockup dari Sesi 2 (screenshot PNG atau JPG, atau PDF atau HTML hasil ekspor), dan BRD dalam bentuk berkas. Di Google Docs: **File**, **Download**, **Markdown** (atau PDF), lalu simpan sebagai `brd.md`.
3. Salin juga brief UI dari Sesi 2 ke `references/ui-brief.md`.
4. Buka Claude Code di folder itu. **Tab Code:** buka aplikasi Claude, klik **Code** di bagian atas, pilih **Local**, klik **Select folder** dan pilih `webtm-prototype`. **Terminal:** masuk ke folder itu dan jalankan `claude`.
5. Cek pertama: kirim prompt di bawah. Claude hanya boleh membaca dan menjawab.

Tidak ada mockup? Minta brief UI acuan ke instruktur dan pakai sebagai satu-satunya referensi.

## Perintah terminal (hanya bila memakai terminal)

macOS atau Linux:

```
mkdir -p webtm-prototype/references
cd webtm-prototype
claude
```

Windows PowerShell:

```
mkdir webtm-prototype\references
cd webtm-prototype
claude
```

## Prompt

```
Sebutkan berkas yang ada di folder references dan isi tiap berkas dalam satu kalimat. Jangan membuat atau mengubah berkas apa pun.
```

## Cek

- Claude menyebut semua berkas yang kamu taruh, termasuk gambar mockup.
- Ringkasan tiap berkas benar. Kalau BRD tidak terbaca, ulangi unduhan.
- Tidak ada berkas baru di folder (Claude hanya membaca).

---

Berikutnya: [Langkah 2: Buat CLAUDE.md](02-create-claude-md.md)
