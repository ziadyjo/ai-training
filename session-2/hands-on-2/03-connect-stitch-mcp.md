# Langkah 3: Hubungkan Stitch lewat MCP

Durasi ±17 menit. MCP adalah cara standar sebuah tool memberi Claude "pintu" untuk membaca dan menulis. Di langkah ini kamu memasang pintu Google Stitch ke Claude Code, lalu memastikan Claude bisa melihat tool Stitch. Stitch dihubungkan lewat Claude Code, bukan lewat chat Claude.

Alternatif: Claude Design, yang boleh dipilih dari awal atau dipakai kalau koneksi tidak jadi dalam 10 menit. Langkah lengkapnya ada di [claude-design.md](claude-design.md).

## Yang dikerjakan

1. Pastikan Claude Code terpasang. Di terminal, jalankan `claude --version`. Kalau belum ada, ikuti [panduan instalasi resmi](https://code.claude.com/docs/en/setup), lalu masuk dengan akun Claude-mu.
2. Buka [Google Stitch](https://stitch.withgoogle.com), login dengan akun Google, lalu buka **Settings** dan buat API key di bagian API Keys. Salin key itu ke tempat yang aman. Jangan menempelnya di chat, BRD, atau repo.
3. Simpan key di variabel lingkungan pada terminal yang sama dengan yang menjalankan Claude Code (perintahnya di bagian "Perintah").
4. Jalankan perintah penambahan server. Server ini milik Google, alamatnya `https://stitch.googleapis.com/mcp`, dan key dikirim lewat header `X-Goog-Api-Key`.
5. Jalankan `claude`, ketik `/mcp`, dan pastikan server `stitch` muncul dengan status terhubung.
6. Kirim prompt verifikasi di bawah. Claude hanya menyebut tool, tidak membuat apa pun.

## Perintah

macOS atau Linux:

```
export STITCH_API_KEY='[API KEY STITCH]'
claude mcp add --transport http --scope user stitch https://stitch.googleapis.com/mcp --header "X-Goog-Api-Key: $STITCH_API_KEY"
```

Windows PowerShell:

```
$env:STITCH_API_KEY = '[API KEY STITCH]'
claude mcp add --transport http --scope user stitch https://stitch.googleapis.com/mcp --header "X-Goog-Api-Key: $env:STITCH_API_KEY"
```

Ganti dulu: `[API KEY STITCH]`.

Pakai header `X-Goog-Api-Key` seperti di atas. Contoh lain di internet memakai `Authorization: Bearer` dan `X-Goog-User-Project`: itu jalur OAuth yang butuh token berumur pendek dan Google Cloud project ID, bukan jalur yang dipakai di latihan ini. Kalau key atau token pernah tertempel di chat, dokumen, atau screenshot, cabut dan buat yang baru. Jangan menjalankan `claude mcp get stitch` di layar yang dibagikan: perintah itu menampilkan nilai header, termasuk key, apa adanya. Untuk memeriksa status pakai `claude mcp list`.

Perintah `claude mcp add` menyimpan key di berkas konfigurasi Claude Code di laptopmu. Pakai laptop pribadi atau akun yang tidak dipakai bersama, dan hapus server (`claude mcp remove stitch --scope user`) serta key di Stitch Settings setelah training bila tidak dipakai lagi.

## Prompt verifikasi (kirim di Claude Code)

```
Sebutkan tool Stitch yang tersedia di sesi ini dan fungsi tiap tool dalam satu kalimat. Lalu panggil tool daftar project (list_projects) dan sebutkan jumlah project yang ada. Jangan membuat atau mengubah apa pun di Stitch.
```

## Cek

- `/mcp` menampilkan server `stitch` terhubung, atau pesan "Reconnected to stitch".
- Kalau bar bawah Claude Code menulis "auto mode on", Claude bisa menjalankan tool tanpa kartu izin. Tekan Shift+Tab untuk mengganti mode bila kamu ingin menyetujui tiap aksi.
- Claude menyebut tool untuk melihat project dan screen, membuat screen dari teks, mengedit screen, dan membuat variasi. Nama tool bisa berbeda per versi; yang penting fungsinya ada. Daftar bisa memuat tool penghapusan project (mis. `delete_project`) dan tool design system; jangan memintanya di latihan ini.
- Panggilan daftar project berhasil (boleh nol project). Status terhubung di `/mcp` belum membuktikan key valid: key yang salah baru ditolak saat tool dipanggil.
- API key tidak muncul di chat, riwayat terminal yang dibagikan, atau berkas apa pun di repo.

## Alternatif: Claude Design

Pakai ini kalau server `stitch` tidak terhubung, atau muncul pesan galat yang tidak bisa diselesaikan dalam 10 menit.

1. Di sidebar aplikasi Claude buka **Artifacts**, lalu buat desain baru di **Claude Design**.
2. Lanjutkan dengan [claude-design.md](claude-design.md), yang menggantikan Langkah 3 sampai 5. Tidak perlu API key atau Claude Code.

---

Sebelumnya: [Langkah 2: Jalankan ui-brief](02-run-ui-brief.md)  
Berikutnya: [Langkah 4: Hasilkan dan bandingkan screen](04-generate-compare-screens.md)
