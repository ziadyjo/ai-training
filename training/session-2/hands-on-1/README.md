# Hands-on #1: Requirement-to-Process Flow

Kamu mengubah satu bagian BRD hasil Sesi 1 menjadi flow spec dengan `/flow-diagram`, menggambarnya di Miro lewat connector, mencari skenario yang hilang, lalu menautkan hasilnya ke BRD. Berkas yang dipakai ada di [`sources/`](sources/).

| | |
|---|---|
| Durasi | 75 menit |
| Model | Sonnet 5.5 untuk menyusun flow spec dan menggambar. Opus 5.5 hanya bila mencari skenario hilang di BRD yang panjang |
| Hasil | Flow spec Create New Role, diagram swimlane di Miro, dan tautan plus gambar di bagian Proposed Business Process BRD. Flow spec v2 memuat exception atau skenario baru dari aturan Skill (Cek mutu bisa tetap sama) |

## Urutan langkah

| Langkah | Isi | Berkas | Menit |
|---|---|---|---|
| Quick Setup | Hubungkan Miro ke Claude | [00-quick-setup.md](00-quick-setup.md) | ±8 |
| 1 | Pasang flow-diagram dan siapkan BRD | [01-setup-skill.md](01-setup-skill.md) | ±10 |
| 2 | Susun flow spec di chat | [02-draft-flow-spec.md](02-draft-flow-spec.md) | ±15 |
| 3 | Gambar di Miro | [03-draw-in-miro.md](03-draw-in-miro.md) | ±15 |
| 4 | Cari skenario hilang dan perbaiki Skill | [04-find-gaps-improve-skill.md](04-find-gaps-improve-skill.md) | ±17 |
| 5 | Tautkan flow ke BRD | [05-link-to-brd.md](05-link-to-brd.md) | ±10 |

## Cara menyalin prompt

1. Klik tombol salin di pojok kanan blok kode. Satu blok adalah satu prompt.
2. Ganti teks dalam kurung siku, misalnya `[LINK BRD]`, sebelum mengirim.
3. Di kotak chat, tekan Shift+Enter untuk pindah baris. Prompt yang diawali `/` harus berada di baris pertama.

## Tertinggal?

Minta berkas acuan ke instruktur. Hasilmu akan berbeda dari acuan: pakai acuan untuk melanjutkan, bukan untuk menyalin.

## Kriteria lulus

- [ ] Semua aktor di BRD muncul di flow spec.
- [ ] Setiap keputusan punya dua cabang atau lebih, dan ada minimal satu exception.
- [ ] Tidak ada langkah di luar BRD: yang tidak punya dasar ditandai "tanpa rujukan" atau ditulis sebagai pertanyaan.
- [ ] Diagram di Miro sama dengan flow spec yang kamu setujui.
- [ ] Tautan board dan gambar ada di bagian 6 BRD, tanpa perubahan lain.
- [ ] [Scorecard](../scorecard.md) v1 dan v2 terisi.

## Kalau bermasalah

| Masalah | Jalan keluar |
|---|---|
| Miro tidak muncul di Discover atau Connect gagal | Pastikan login Miro aktif di browser yang sama, ulangi Connect. Kalau tetap gagal, lanjut sampai Langkah 2 dan 4, lalu gambar flow spec di Miro secara manual |
| Claude tidak menemukan board | Board harus bisa diakses akunmu. Buka link di browser dulu, dan pastikan team yang dipilih saat Connect sama dengan pemilik board |
| Claude menyebut batas harian Miro tercapai | Miro Free dibatasi 100 panggilan tool per hari (reset 00:00 UTC, yaitu 07:00 WIB). Berhenti memakai tool, lanjutkan flow spec di chat, dan gambar manual di Miro atau tunggu reset. Hemat dengan menggambar sekali, bukan memperbaiki per kotak |
| Kartu izin Miro muncul terus | Pilih Allow once setiap kali. Setiap tool diminta izin per pemakaian, itu normal |
| Claude menggambar tanpa lane atau kotaknya menumpuk | Minta gambar ulang di frame baru dengan "satu lane per aktor". Jangan memperbaiki kotak satu per satu |
| Claude langsung menggambar sebelum kamu setuju | Hentikan dan tulis "Berhenti. Hapus yang baru digambar dan tunggu persetujuanku." Cek bahwa Skill `flow-diagram` terpanggil (tertulis Loaded skill) |
| Flow spec memuat langkah yang tidak ada di BRD | Minta Claude menandai langkah itu "tanpa rujukan", lalu hapus atau jadikan pertanyaan |
| Claude menulis ke bagian BRD yang salah | Pulihkan lewat Version history di Google Docs, lalu ulangi Langkah 5 dengan menyebut bagian 6 secara eksplisit |
| Perubahan Skill tidak berpengaruh | Periksa bahwa kamu memakai versi terbaru dan chat baru |
