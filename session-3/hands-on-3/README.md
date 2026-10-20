# Hands-on #3: Scheduled Project Progress Brief

Kamu menyiapkan data progres di backlog, menetapkan format brief tiga bagian, membuat scheduled task yang menyusun brief dari backlog, lalu memakai catatan meeting sprint review untuk mengusulkan perubahan BRD tanpa menulisnya langsung. Berkas yang dipakai ada di [`sources/`](sources/).

| | |
|---|---|
| Durasi | 30 menit |
| Model | Sonnet 5.5 untuk brief dan task. Opus 5.5 hanya untuk menimbang dampak MoM terhadap banyak requirement |
| Jalur | Scheduled task di aplikasi Claude (menu **Scheduled**), membaca backlog dari Notion atau Google Docs |
| Hasil | Scheduled task yang dijalankan sesuai permintaan, brief progres, Cek mutu brief (N dari 6), usulan perubahan BRD dari MoM, scorecard v1 dan v2 |

## Urutan langkah

| Langkah | Isi | Berkas | Menit |
|---|---|---|---|
| 1 | Siapkan data progres dan MoM | [01-prepare-progress-data.md](01-prepare-progress-data.md) | ±6 |
| 2 | Tentukan format dan brief pertama | [02-define-format-first-brief.md](02-define-format-first-brief.md) | ±8 |
| 3 | Buat scheduled task dan jalankan | [03-create-scheduled-task.md](03-create-scheduled-task.md) | ±9 |
| 4 | Dampak MoM sebagai usulan dan iterasi | [04-mom-impact-iterate.md](04-mom-impact-iterate.md) | ±7 |

## Cek mutu brief

Enam pemeriksaan tetap, dipakai di Langkah 2 (v1) dan Langkah 4 (v2). Skor: jumlah yang lolos, dari 6.

| No | Pemeriksaan |
|---|---|
| 1 | Tiga bagian tetap ada: Progres, Prioritas, Hambatan |
| 2 | Setiap angka dan status menyebut Story ID sumbernya dan cocok dengan backlog |
| 3 | Tiap hambatan punya alasan, sumber, dan tindakan yang diminta |
| 4 | Prioritas minggu ini maksimal tiga story, masing-masing dengan alasan |
| 5 | Tidak ada status atau tanggal dikarang: yang tidak ada di data ditulis "tidak ada data" |
| 6 | Muat satu halaman (di bawah 200 kata) dan menyebut tanggal data diambil |

## Cara menyalin prompt

1. Klik tombol salin di pojok kanan blok kode. Satu blok adalah satu prompt.
2. Ganti teks dalam kurung siku, misalnya `[TANGGAL]`, sebelum mengirim.
3. Di kotak chat, tekan Shift+Enter untuk pindah baris.
4. Prompt dikirim di chat Claude di Project WebTM, kecuali Langkah 3 yang dibuat di menu **Scheduled**.

## Tertinggal?

Minta berkas acuan ke instruktur. Hasilmu akan berbeda dari acuan: pakai acuan untuk melanjutkan, bukan untuk menyalin.

## Kriteria lulus

- [ ] Data progres tercatat di backlog (Status berbeda untuk beberapa story).
- [ ] Scheduled task dibuat dengan nama, prompt, frekuensi, dan model yang jelas, lalu dijalankan sesuai permintaan.
- [ ] Brief punya tiga bagian dan semua angkanya cocok dengan backlog.
- [ ] Cek mutu brief v1 dan v2 terisi di [scorecard](../scorecard.md).
- [ ] Dampak MoM berupa usulan perubahan yang menunggu persetujuanmu. BRD tidak berubah.
- [ ] Hal yang tidak ada di MoM atau backlog tidak dikarang.

## Kalau bermasalah

| Masalah | Jalan keluar |
|---|---|
| Menu **Scheduled** tidak ada | Fitur tersedia di paket berbayar. Bila akunmu tidak menampilkannya, jalankan prompt manual di chat |
| Task tidak jalan saat komputer mati | Task yang hanya memakai connector berjalan tanpa komputer menyala. Task yang membaca berkas lokal hanya berjalan saat aplikasi desktop terbuka dan komputer menyala. Task di sini hanya memakai connector |
| Run berhenti dan tidak selesai | Run menunggu izin untuk tool Notion. Buka sesi run-nya di daftar task dan setujui izinnya, lalu pilih izin tetap untuk tool baca. Jalankan ulang dengan **Run now** |
| Task gagal membaca Notion | Periksa connector Notion masih tersambung dan halaman backlog masih diizinkan. Jalankan ulang |
| Brief memuat angka yang tidak ada di backlog | Kirim Prompt iterasi di Langkah 4: sebut angkanya dan minta ditulis "tidak ada data" bila tidak bersumber |
| Brief terlalu panjang | Minta batas 200 kata dan maksimal tiga prioritas |
| Claude menulis perubahan langsung ke BRD | Itu melanggar aturan. Batalkan di Google Docs lewat riwayat versi, lalu kirim Prompt usulan di Langkah 4 yang menegaskan hanya usulan |
| Frekuensi harian tidak berjalan saat kelas | Normal: task dijalankan sesuai permintaan. Jadwal baru berjalan di waktu yang ditentukan |
| Task sulit diubah | Buka halaman task di **Scheduled**, ubah prompt atau frekuensi, lalu jalankan ulang sesuai permintaan |
