# Hands-on #1: Design-to-Code Development

Kamu mengubah mockup dan BRD dari Sesi 1 dan 2 menjadi prototype HTML yang bisa diklik, memakai Claude Code. Urutannya: siapkan folder dan referensi, tulis `CLAUDE.md`, minta rencana di plan mode, setujui, bangun, lalu periksa dan perbaiki. Berkas yang dipakai ada di [`sources/`](sources/).

| | |
|---|---|
| Durasi | 90 menit |
| Model | Opus 5.5 untuk rencana di plan mode. Sonnet 5.5 untuk membangun dan memperbaiki. |
| Jalur | Utama: tab **Code** di aplikasi Claude desktop (pilih Chat atau Code di bagian atas). Alternatif: Claude Code di terminal. Cadangan: Artifacts di chat. Langkah sama, tombol dan perintahnya berbeda: keduanya ditulis di tiap langkah |
| Hasil | Folder `webtm-prototype/` dengan `index.html` yang menjalankan alur Create New Role, Cek mutu prototype (N dari 6), dan scorecard v1 dan v2 |

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
| 1 | Setiap elemen punya dasar: ID requirement (RM-xxx) di komentar kode atau di rencana, atau ada di mockup |
| 2 | Alur utama bisa diklik: Daftar Role, Create New Role, simpan, hasil terlihat di Daftar Role |
| 3 | Validasi jalan: Role Name kosong dan Role Name yang sudah dipakai menampilkan pesan |
| 4 | State penting tampil: kosong, loading, dan error pada screen yang diminta rencana |
| 5 | Tidak ada fitur di luar BRD (login, hapus role, dll). Yang belum diputuskan BRD ditandai TBC di layar dan di daftar pertanyaan |
| 6 | Terbuka dengan klik dua kali `index.html`, tanpa instal apa pun dan tanpa galat merah di console browser |

## Cara menyalin prompt

1. Klik tombol salin di pojok kanan blok kode. Satu blok adalah satu prompt.
2. Ganti teks dalam kurung siku, misalnya `[NAMA FOLDER]`, sebelum mengirim.
3. Pindah baris: tab Code memakai Shift+Enter. Terminal memakai Shift+Enter (atau `\` lalu Enter). Perintah yang diawali `/` harus berada di baris pertama.

## Tertinggal?

Minta berkas acuan ke instruktur. Hasilmu akan berbeda dari acuan: pakai acuan untuk melanjutkan, bukan untuk menyalin.

## Kriteria lulus

- [ ] `CLAUDE.md` ada di folder proyek dan terbaca (muncul di `/context`).
- [ ] Rencana dibuat di plan mode dan kamu menyetujuinya sebelum ada berkas yang berubah.
- [ ] `index.html` terbuka di browser dan alur Create New Role bisa diklik.
- [ ] Cek mutu prototype v1 dan v2 terisi di [scorecard](../scorecard.md), dan v2 lebih tinggi atau sama dengan v1 dengan alasan yang bisa ditunjuk.
- [ ] Elemen tanpa dasar BRD sudah dihapus atau masuk daftar pertanyaan.
- [ ] Prototype dan `CLAUDE.md` tersimpan di folder proyek.

## Kalau bermasalah

| Masalah | Jalan keluar |
|---|---|
| Tab Code tidak ada atau meminta upgrade | Claude Code butuh paket berbayar (Pro atau lebih tinggi). Perbarui aplikasi Claude desktop ke versi terbaru dan masuk dengan akun yang benar |
| `claude` tidak dikenal di terminal | Claude Code CLI belum terpasang atau terminal belum dibuka ulang. Pakai tab Code di aplikasi Claude, atau pasang CLI dengan panduan resmi dan buka terminal baru |
| Claude langsung mengubah berkas tanpa bertanya | Mode awal bisa Auto (versi terbaru). Tab Code: buka selector mode di samping tombol kirim dan pilih **Plan** (atau Cmd+Shift+M di macOS, Ctrl+Shift+M di Windows). Terminal: Shift+Tab sampai mode **plan** tampil, atau mulai dengan `claude --permission-mode plan`. |
| Shift+Tab tidak berpindah mode | Di tab Code Shift+Tab memang tidak berpindah mode: pakai selector mode. Di terminal ketik `/plan`, atau mulai ulang dengan `claude --permission-mode plan` |
| Claude tidak mengikuti aturan di `CLAUDE.md` | Jalankan `/context` (tab Code dan terminal) dan periksa berkasnya terbaca. Pastikan berkas bernama persis `CLAUDE.md` dan ada di folder proyek yang kamu pilih. Persingkat aturannya: berkas panjang diabaikan sebagian |
| Claude tidak bisa membaca gambar mockup | Taruh gambar (PNG atau JPG) di `references/` dan sebut nama berkasnya (di tab Code ketik `@` lalu nama berkas, atau lampirkan lewat tombol lampiran). Bila tetap gagal, pakai tabel screen di brief UI sebagai pengganti |
| Halaman kosong di browser | Buka console browser (F12). Tempel pesan galat ke Claude Code dan minta perbaikan satu hal itu |
| Tombol tidak bereaksi | Minta Claude memeriksa penanganan klik di `index.html` dan melaporkan penyebabnya sebelum memperbaiki |
| Claude menambah halaman login, hapus role, atau fitur lain | Kirim prompt iterasi di Langkah 6: sebut elemennya dan minta dihapus. Jangan menerima karena terlihat bagus |
| Konteks terasa penuh dan jawaban menurun | Mulai sesi baru di antara tugas yang tidak berhubungan (tab Code: Cmd+N atau Ctrl+N, terminal: `/clear`). `CLAUDE.md` tetap terbaca ulang |
| Hasil memburuk setelah perubahan | `/rewind` (tab Code dan terminal) kembali ke pesan sebelumnya. Di tab Code bisa juga menolak perubahan di diff view, di terminal juga `Esc` dua kali |
| Claude Code bermasalah sama sekali | Cadangan: di chat Claude minta satu berkas HTML lewat Artifacts, salin ke `index.html`. |
