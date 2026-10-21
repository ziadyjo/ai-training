# Hands-on #1: Design-to-Code Development

Kamu mengubah desain Claude Design dan BRD dari Sesi 1 dan 2 menjadi prototype HTML yang bisa diklik, memakai Claude Code di tab **Code** aplikasi Claude desktop. Urutannya: siapkan folder dan referensi, tulis `CLAUDE.md`, minta rencana di plan mode, setujui, bangun, lalu periksa dan perbaiki. Berkas yang dipakai ada di [`sources/`](sources/).

Claude Design di Sesi 2 sudah menghasilkan tampilan dan prototype. Bedanya: Claude Design mengurus tampilan, Claude Code membangun berkas `index.html` milikmu sendiri yang perilakunya mengikuti BRD (validasi, state, alur sampai role tersimpan), menautkan tiap elemen ke ID requirement, dan siap diuji di Sesi 4. Kamu tidak menulis kode: kamu menilai rencana, perubahan, dan hasil di browser.

| | |
|---|---|
| Durasi | 90 menit |
| Model | Opus 5.5 untuk rencana di plan mode. Sonnet 5.5 untuk membangun dan memperbaiki |
| Jalur | Tab **Code** di aplikasi Claude desktop (pilih Chat atau Code di bagian atas). Terminal tidak dipakai |
| Input | Ekspor desain Claude Design (HTML atau screenshot), BRD v1.1 (PDF atau Markdown) |
| Hasil | Folder `webtm-prototype/` berisi `CLAUDE.md`, `PLAN.md`, `NOTES.md`, dan `index.html` yang menjalankan alur Create New Role. Cek mutu prototype v1 dan v2 di scorecard |

## Urutan langkah

| Langkah | Isi | Berkas | Menit |
|---|---|---|---|
| 1 | Siapkan workspace dan referensi | [01-prepare-workspace.md](01-prepare-workspace.md) | ±10 |
| 2 | Buat CLAUDE.md | [02-create-claude-md.md](02-create-claude-md.md) | ±10 |
| 3 | Susun rencana di plan mode | [03-plan-mode.md](03-plan-mode.md) | ±15 |
| 4 | Bangun alur utama | [04-build-main-flow.md](04-build-main-flow.md) | ±25 |
| 5 | Jalankan dan verifikasi | [05-run-and-verify.md](05-run-and-verify.md) | ±15 |
| 6 | Iterasi dan simpan | [06-iterate-and-save.md](06-iterate-and-save.md) | ±15 |

## Cek mutu prototype

Enam pemeriksaan tetap. Dipakai di Langkah 5 (v1) dan Langkah 6 (v2). Skor: jumlah yang lolos, dari 6.

| No | Pemeriksaan |
|---|---|
| 1 | Setiap elemen punya dasar: ID requirement (RM-xxx) di rencana dan di komentar kode, atau ada di desain |
| 2 | Alur utama bisa diklik: Daftar Role, Create New Role, Submit, role baru terlihat di Daftar Role |
| 3 | Validasi jalan: Role Name kosong, sama dengan role Active, dan sama dengan role Inactive menampilkan pesan |
| 4 | State penting tampil: loading saat Submit, dan pesan error di bawah Role Name dengan form tetap terbuka |
| 5 | Tidak ada fitur di luar BRD (login, hapus role, logo atau nama asli). Yang belum diputuskan BRD ditandai TBC di layar dan di `NOTES.md` |
| 6 | Terbuka dengan klik dua kali `index.html`, tanpa instal apa pun dan tanpa galat |

## Cara menyalin prompt

1. Klik tombol salin di pojok kanan blok kode. Satu blok adalah satu prompt.
2. Ganti teks dalam kurung siku, misalnya `[TEMUAN]`, sebelum mengirim.
3. Pindah baris: tekan Shift+Enter. Perintah yang diawali `/` harus berada di baris pertama.
4. Semua prompt di hands-on ini dikirim di tab **Code**, bukan di chat biasa.
5. Prompt memakai label huruf besar: CONTEXT, TASK, RULES, OUTPUT FORMAT. Pertahankan labelnya saat kamu mengganti teks di dalamnya.

## Tertinggal?

- Tidak punya ekspor Claude Design: pakai gambar di [`sources/mockup-acuan/`](sources/mockup-acuan/).
- Tidak punya BRD v1.1: pakai [`sources/brd-v1-1.pdf`](sources/brd-v1-1.pdf) atau [`sources/brd-v1-1.md`](sources/brd-v1-1.md).
- Prototype tidak jadi sampai akhir: minta prototype acuan ke instruktur. Hasilmu akan berbeda dari acuan: pakai acuan untuk melanjutkan, bukan untuk menyalin.

## Kriteria lulus

- [ ] `CLAUDE.md` ada di folder proyek dan terbaca (muncul di `/context`).
- [ ] Rencana dibuat di plan mode, tersimpan di `PLAN.md`, dan kamu menyetujuinya sebelum ada berkas lain yang berubah.
- [ ] `index.html` terbuka di browser dan alur Create New Role bisa diklik sampai role baru tampil.
- [ ] Cek mutu prototype v1 dan v2 terisi di [scorecard](../scorecard.md), dan v2 lebih tinggi atau sama dengan v1 dengan alasan yang bisa ditunjuk.
- [ ] Elemen tanpa dasar BRD atau desain sudah dihapus atau masuk `NOTES.md`.
- [ ] Folder berisi `index.html`, `CLAUDE.md`, `PLAN.md`, dan `NOTES.md`. Prototype ini dipakai lagi di Sesi 4.

## Kalau bermasalah

| Masalah | Jalan keluar |
|---|---|
| Tab Code tidak ada atau meminta upgrade | Claude Code butuh paket berbayar (Pro atau lebih tinggi). Perbarui aplikasi Claude desktop ke versi terbaru dan masuk dengan akun yang benar |
| Menu ekspor HTML tidak ada di Claude Design | Ambil screenshot screen Daftar Role dan Create New Role (PNG), simpan di `references/`. Bila desain tertinggal, pakai `sources/mockup-acuan/` |
| Claude langsung mengubah berkas tanpa bertanya | Mode awal bisa Auto. Buka selector mode di samping tombol kirim dan pilih **Plan** (atau Cmd+Shift+M di macOS, Ctrl+Shift+M di Windows) |
| Shift+Tab tidak berpindah mode | Di tab Code Shift+Tab memang tidak berpindah mode: pakai selector mode |
| Claude tidak mengikuti aturan di `CLAUDE.md` | Kirim `/context` dan periksa berkasnya terbaca. Nama berkas harus persis `CLAUDE.md` dan ada di folder yang kamu pilih. Persingkat aturannya: berkas panjang diabaikan sebagian |
| Claude tidak bisa membaca BRD atau desain | Sebut nama berkasnya dengan `@` (mis. `@references/brd.pdf`). BRD PDF tidak terbaca: unduh ulang Google Docs sebagai Markdown. Gambar: pakai PNG atau JPG |
| Claude menyalin seluruh kode ekspor Claude Design | Tolak di diff view. Kirim: "Jangan menyalin kode ekspor. Pakai hanya sebagai acuan tampilan, tulis index.html sendiri sesuai PLAN.md." |
| Halaman kosong di browser | Kirim: "Halaman kosong saat index.html dibuka. Periksa penyebabnya, sebutkan, lalu perbaiki satu hal itu saja." |
| Tombol tidak bereaksi | Kirim: "Tombol [NAMA TOMBOL] tidak bereaksi. Laporkan penyebabnya sebelum memperbaiki." |
| Claude menambah halaman login, hapus role, logo, atau fitur lain | Kirim prompt iterasi di Langkah 6: sebut elemennya dan minta dihapus. Jangan menerima karena terlihat bagus |
| Konteks terasa penuh dan jawaban menurun | Mulai sesi baru (Cmd+N atau Ctrl+N) di folder yang sama. `CLAUDE.md` dan `PLAN.md` tetap terbaca |
| Hasil memburuk setelah perubahan | Kirim `/rewind` untuk kembali ke pesan sebelumnya, atau tolak perubahan di diff view |
| Claude Code bermasalah sama sekali | Cadangan: di chat Claude, lampirkan BRD dan mockup, minta satu berkas HTML lewat Artifacts, lalu simpan sebagai `index.html` di folder |
