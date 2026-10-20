# Hands-on #2: Project Planning & Backlog Development

Kamu menyusun user story dari requirement BRD, memeriksa mutunya, menyimpannya sebagai backlog di Notion lewat connector, lalu memperbaiki dependency-nya. Berkas yang dipakai ada di [`sources/`](sources/).

| | |
|---|---|
| Durasi | 30 menit |
| Model | Sonnet 5.5. Opus 5.5 hanya bila dependency antar story rumit |
| Jalur | Utama: Notion lewat connector di chat Claude. Alternatif: Google Docs (tabel di dokumen) |
| Hasil | Backlog 8 sampai 12 story di Notion (atau Google Docs), Cek mutu backlog (N dari 6), scorecard v1 dan v2 |

## Urutan langkah

| Langkah | Isi | Berkas | Menit |
|---|---|---|---|
| 1 | Hubungkan Notion dan buat user story | [01-connect-notion-user-stories.md](01-connect-notion-user-stories.md) | ±10 |
| 2 | Draf backlog dan Cek mutu | [02-draft-backlog-quality-check.md](02-draft-backlog-quality-check.md) | ±8 |
| 3 | Kirim ke Notion | [03-send-to-notion.md](03-send-to-notion.md) | ±7 |
| 4 | Review dependency dan iterasi | [04-review-dependency-iterate.md](04-review-dependency-iterate.md) | ±5 |

## Cek mutu backlog

Enam pemeriksaan tetap, dipakai di Langkah 2 (v1) dan Langkah 4 (v2). Skor: jumlah yang lolos, dari 6.

| No | Pemeriksaan |
|---|---|
| 1 | Setiap story punya ID requirement sumber (RM-xxx atau AC-xxx) |
| 2 | Format "Sebagai [peran], saya ingin [tujuan], supaya [manfaat]" lengkap |
| 3 | Minimal dua acceptance criteria per story, tiap butir bisa dijawab ya atau tidak |
| 4 | Priority (Must, Should, Could) dan Size (S, M, L) terisi |
| 5 | Dependency ditulis eksplisit: ID story lain atau "tidak ada" |
| 6 | Tidak ada story tanpa dasar BRD. Yang masih TBC ada di daftar pertanyaan, bukan jadi story berisi tebakan |

## Cara menyalin prompt

1. Klik tombol salin di pojok kanan blok kode. Satu blok adalah satu prompt.
2. Ganti teks dalam kurung siku, misalnya `[LINK BRD]`, sebelum mengirim.
3. Di kotak chat, tekan Shift+Enter untuk pindah baris.
4. Semua prompt di hands-on ini dikirim di chat Claude di dalam Project WebTM, bukan di Claude Code.

## Tertinggal?

Minta berkas acuan ke instruktur. Hasilmu akan berbeda dari acuan: pakai acuan untuk melanjutkan, bukan untuk menyalin.

## Kriteria lulus

- [ ] Notion tersambung ke Claude, atau kamu memakai Google Docs dengan alasan yang jelas.
- [ ] 8 sampai 12 story, semua bersumber dari requirement BRD.
- [ ] Cek mutu backlog v1 dan v2 terisi di [scorecard](../scorecard.md).
- [ ] Backlog ada di Notion (atau Google Docs) dengan semua properti terisi.
- [ ] Dependency diperiksa dan diperbaiki dengan satu feedback.
- [ ] Hal yang TBC ada di daftar pertanyaan, bukan di story.

## Kalau bermasalah

| Masalah | Jalan keluar |
|---|---|
| Notion tidak ada di daftar connector | Cek Customize lalu Connectors. Bila paket Notion-mu tidak mengizinkan, pakai Google Docs |
| Halaman izin Notion menolak | Connector bekerja dengan izin akunmu sendiri. Pakai akun Notion pribadi (bukan akun tamu di workspace orang lain) dan pilih halaman yang boleh diakses |
| Claude tidak menemukan halaman Notion | Pilih halaman induk saat memberi izin, atau buat halaman kosong bernama `WebTM Backlog` lebih dulu |
| Database terbuat, tetapi properti kurang | Kirim Prompt perbaikan di Langkah 3: sebut properti yang kurang |
| Story terlalu banyak atau terlalu besar | Minta Claude memecah story yang Size-nya L, atau memangkas ke 12 teratas berdasarkan Priority |
| Claude menulis story berisi tebakan untuk requirement TBC | Hapus story itu dan pindahkan ke Pertanyaan. Kirim Prompt iterasi di Langkah 4 |
| Batas pemakaian tercapai | Tunggu reset atau kurangi jumlah story. Panggilan connector ikut dihitung |
| Claude ingin mengubah banyak halaman Notion | Pilih **Allow once** dan periksa halamannya. Jangan memberi izin tetap sebelum yakin |
