# Hands-on #2: Requirement-to-UI Design Exploration

Kamu mengubah BRD dan flow dari Hands-on #1 menjadi brief UI dengan `/ui-brief`, menghubungkan Google Stitch ke Claude lewat MCP, membuat 3 sampai 4 screen inti, membandingkan dua layout, lalu menautkan hasilnya ke BRD. Alternatifnya adalah Claude Design. Berkas yang dipakai ada di [`sources/`](sources/).

| | |
|---|---|
| Durasi | 75 menit |
| Model | Sonnet 5.5 untuk brief UI dan membuat screen. Opus 5.5 hanya bila perlu menganalisis konflik antar requirement |
| Jalur | Dua jalur dengan hasil sama. Utama: Stitch lewat MCP di Claude Code (Langkah 3 sampai 5). Alternatif: Claude Design, langkah lengkap di [claude-design.md](claude-design.md) |
| Hasil | Brief UI dengan Cek mutu brief, 3 sampai 4 screen di Stitch (atau Claude Design), satu layout terpilih dengan alasan, dan tautan serta gambar di BRD |

## Urutan langkah

| Langkah | Isi | Berkas | Menit |
|---|---|---|---|
| 1 | Pasang ui-brief | [01-setup-skill.md](01-setup-skill.md) | ±8 |
| 2 | Jalankan ui-brief | [02-run-ui-brief.md](02-run-ui-brief.md) | ±15 |
| 3 | Hubungkan Stitch lewat MCP | [03-connect-stitch-mcp.md](03-connect-stitch-mcp.md) | ±17 |
| 4 | Hasilkan dan bandingkan screen | [04-generate-compare-screens.md](04-generate-compare-screens.md) | ±25 |
| 5 | Simpan hasil dan tautkan ke BRD | [05-save-link-to-brd.md](05-save-link-to-brd.md) | ±10 |
| Alternatif | Claude Design menggantikan Langkah 3 sampai 5 | [claude-design.md](claude-design.md) | ±45 |

## Cara menyalin prompt

1. Klik tombol salin di pojok kanan blok kode. Satu blok adalah satu prompt.
2. Ganti teks dalam kurung siku, misalnya `[LINK BRD]`, sebelum mengirim.
3. Di kotak chat, tekan Shift+Enter untuk pindah baris. Prompt yang diawali `/` harus berada di baris pertama.
4. Tiap prompt di Langkah 4 bertanda tempat kirimnya: chat Claude atau Claude Code.

## Tertinggal?

Minta berkas acuan ke instruktur. Hasilmu akan berbeda dari acuan: pakai acuan untuk melanjutkan, bukan untuk menyalin.

## Kriteria lulus

- [ ] Server `stitch` terhubung di Claude Code, atau kamu memakai Claude Design dengan alasan yang jelas.
- [ ] Tiap screen punya tujuan dan aksi utama (minimal 2 screen, target 4).
- [ ] Screen penting punya state kosong, loading, atau error.
- [ ] Tidak ada elemen di luar BRD dan flow: yang tidak punya dasar ada di daftar pertanyaan, bukan di desain.
- [ ] Screen tertaut ke ID requirement.
- [ ] Dua layout dibandingkan dengan kriteria tertulis, dan feedback hanya mengubah layout terpilih.
- [ ] Link Stitch (atau Claude Design) dan gambar ada di BRD.
- [ ] [Scorecard](../scorecard.md) v1 dan v2 untuk UI terisi.

## Kalau bermasalah

| Masalah | Jalan keluar |
|---|---|
| `claude` tidak dikenal di terminal | Claude Code belum terpasang atau terminal belum dibuka ulang. Ikuti panduan instalasi resmi di Langkah 3, lalu buka terminal baru |
| Server `stitch` tidak muncul di `/mcp` | Jalankan ulang perintah `claude mcp add`, lalu mulai ulang Claude Code. Pastikan variabel API key diisi di terminal yang sama dengan yang menjalankan `claude` |
| `MCP server stitch already exists in user config` | Server sudah pernah ditambahkan. Jalankan `claude mcp list` untuk melihat statusnya. Kalau tidak terhubung atau key lama sudah tidak berlaku, jalankan `claude mcp remove stitch --scope user`, lalu ulangi perintah `claude mcp add` dengan key terbaru |
| Galat `401`, `AUTH_FAILED`, atau pesan bahwa server menolak header Authorization saat tool dipanggil | API key salah, kosong, atau kedaluwarsa. `/mcp` bisa tetap menampilkan terhubung. Cek variabel terisi tanpa menampilkannya: `echo ${#STITCH_API_KEY}` (angka harus lebih dari 0). Buat key baru di Stitch Settings, jalankan `claude mcp remove stitch --scope user`, lalu ulangi `claude mcp add` di terminal yang sama |
| Galat `403` atau `PERMISSION_DENIED` | Ada pembatasan akun atau project Google. Pakai Claude Design |
| Galat `Incompatible auth server: does not support dynamic client registration` | Claude Code mencoba masuk lewat OAuth dan mengabaikan header key. Ini masalah yang dilaporkan pengguna lain. Jangan menghabiskan waktu: pakai Claude Design |
| Claude menjawab tool Stitch tidak ada di sesi ini | Prompt B, C, dan E harus dikirim di Claude Code (terminal), bukan di chat Claude. Pindah ke jendela terminal tempat `claude` berjalan, pastikan `/mcp` menampilkan `stitch`, lalu kirim ulang |
| Tool Stitch muncul tetapi screen tidak jadi | Minta Claude menyebut screen yang sudah ada sebelum mengulang. Generasi bisa tetap berjalan di server setelah Claude berhenti menunggu, dan mengulang tanpa cek membuat screen ganda |
| Claude memakai ID yang salah (`NOT_FOUND`) | Minta Claude menampilkan daftar screen dan memakai ID persis seperti yang dikembalikan |
| Galat `RATE_LIMITED` | Kuota Stitch tercapai. Kurangi permintaan, atau pakai Claude Design |
| Stitch menambah field atau fitur yang tidak ada di brief | Kirim Prompt E: hapus elemen itu, sebut namanya. Jangan menerima fitur tambahan karena terlihat bagus |
| Jumlah screen berbeda dari yang dipilih | Minta Claude menambah atau menghapus screen satu per satu dengan nama screen dari brief |
| API key tertempel di chat atau berkas | Hapus key itu di Stitch Settings dan buat yang baru. Jangan membagikan layar yang menampilkan key |
| Ekspor Stitch tidak tersedia | Ambil screenshot tiap screen dan namai dengan ID requirement |
