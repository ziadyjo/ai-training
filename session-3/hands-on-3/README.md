# Hands-on #3: Scheduled Project Progress Brief

Kamu membuat scheduled task yang setiap hari kerja membaca backlog dan MoM di Notion, lalu menyusun brief progres dan usulan perubahan BRD dari MoM baru. Demo case-nya: MoM Review BRD v1.1 masuk ke Notion (tanggalnya diisi hari ini), task dijalankan lagi, dan brief menangkap keputusan dan dampaknya ke backlog dan BRD. BRD tidak pernah diubah oleh task. Berkas yang dipakai ada di [`sources/`](sources/).

| | |
|---|---|
| Durasi | 30 menit |
| Model | Sonnet 5.5 untuk brief dan task. Opus 5.5 hanya bila menimbang dampak MoM terhadap banyak requirement |
| Jalur | Chat di Project WebTM (Langkah 1 dan 2), lalu **Scheduled** di sidebar aplikasi Claude desktop (Langkah 3 dan 4) |
| Input | Halaman WebTM di Notion (WebTM Backlog dan WebTM MoM berisi MoM Review BRD), BRD v1.1 |
| Hasil | Scheduled task `Brief Progres WebTM`, dua brief (sebelum dan sesudah MoM baru), keputusan setujui atau tolak tiap usulan, Cek mutu brief v1 dan v2 |

## Urutan langkah

| Langkah | Isi | Berkas | Menit |
|---|---|---|---|
| 1 | Siapkan data progres | [01-prepare-progress-data.md](01-prepare-progress-data.md) | ±6 |
| 2 | Tentukan format dan brief pertama | [02-define-format-first-brief.md](02-define-format-first-brief.md) | ±7 |
| 3 | Buat scheduled task dan jalankan | [03-create-scheduled-task.md](03-create-scheduled-task.md) | ±9 |
| 4 | MoM baru masuk, jalankan ulang, putuskan usulan | [04-mom-impact-iterate.md](04-mom-impact-iterate.md) | ±8 |

## Cek mutu brief

Enam pemeriksaan tetap, dipakai di Langkah 2 (v1) dan Langkah 4 (v2). Skor: jumlah yang lolos, dari 6.

| No | Pemeriksaan |
|---|---|
| 1 | Empat bagian tetap ada: Progres, Prioritas, Hambatan, Catatan MoM |
| 2 | Setiap angka dan status menyebut Story ID sumbernya dan cocok dengan backlog |
| 3 | Tiap hambatan punya alasan, sumber, dan tindakan yang diminta |
| 4 | Catatan MoM hanya memuat MoM bertanggal hari ini atau kemarin, tiap poin menyebut dampaknya (ID requirement dan Story ID) |
| 5 | Tidak ada status, tanggal, atau usulan dikarang. Poin MoM yang bertentangan dengan BRD, atau masih sementara atau terbuka, ditulis sebagai pertanyaan |
| 6 | Maksimal 300 kata dan menyebut tanggal data diambil |

## Cara menyalin prompt

1. Klik tombol salin di pojok kanan blok kode. Satu blok adalah satu prompt.
2. Ganti teks dalam kurung siku, misalnya `[LINK BRD]`, sebelum mengirim.
3. Di kotak chat, tekan Shift+Enter untuk pindah baris.
4. Langkah 1 dan 2 dikirim di chat Project WebTM. Langkah 3 dan 4 memakai menu **Scheduled**.
5. Prompt memakai label huruf besar: CONTEXT, TASK, RULES, OUTPUT FORMAT. Pertahankan labelnya saat kamu mengganti teks di dalamnya.

## Tertinggal?

- Backlog belum ada di Notion: minta backlog acuan ke instruktur, lalu kirim ke Notion dengan Prompt di Langkah 3 Hands-on #2.
- Halaman WebTM belum ada: ikuti Langkah 1 Hands-on #2 (Cara A atau Cara B).
- Hasilmu akan berbeda dari acuan: pakai acuan untuk melanjutkan, bukan untuk menyalin.

## Kriteria lulus

- [ ] Backlog punya Status Done, In Progress, Blocked, dan Backlog.
- [ ] Scheduled task dibuat dengan nama, prompt, frekuensi, dan model yang jelas, lalu dijalankan dengan **Run now**.
- [ ] Run pertama menulis "tidak ada MoM baru". Run kedua (setelah tanggal MoM Review BRD diisi hari ini) memuat Catatan MoM dan mengabaikan MoM lama.
- [ ] Keputusan yang masih sementara atau terbuka di MoM (mis. format Role ID "ROL-", pesan validasi) ditulis sebagai pertanyaan, bukan usulan.
- [ ] Kamu memutuskan setujui atau tolak untuk tiap usulan. BRD tidak berubah.
- [ ] Cek mutu brief v1 dan v2 terisi di [scorecard](../scorecard.md).

## Kalau bermasalah

| Masalah | Jalan keluar |
|---|---|
| Menu **Scheduled** tidak ada | Perbarui aplikasi Claude desktop. Fitur ini ada di paket berbayar. Bila tetap tidak ada, jalankan prompt task secara manual di chat dan lanjutkan langkahnya |
| Run berhenti dan tidak selesai | Run menunggu izin tool Notion atau Google Docs. Buka sesi run dari halaman task, setujui izinnya, dan pilih izin tetap (always allow) hanya untuk tool baca. Jalankan ulang dengan **Run now** |
| Task gagal membaca Notion | Periksa connector Notion masih Connected dan halaman WebTM masih diizinkan. Jalankan ulang |
| Run kedua tidak menemukan MoM baru | Periksa nama database persis **WebTM MoM**, kolom **Tanggal meeting** pada MoM Review BRD terisi tanggal hari ini, dan halaman MoM ada di dalam database (bukan halaman terpisah) |
| Run memuat MoM lama | Kirim feedback lewat **Edit** task: "Hanya MoM dengan Tanggal meeting hari ini atau kemarin." Jalankan ulang |
| Task tidak jalan saat komputer mati | Task yang hanya memakai connector berjalan tanpa komputer menyala. Task yang membaca berkas di komputermu hanya berjalan saat aplikasi terbuka dan komputer menyala. Task ini hanya memakai connector |
| Brief memuat angka atau usulan yang tidak ada di data | Itu temuan untuk Langkah 4. Perbaiki prompt task, jangan menerima hasilnya |
| Claude menulis perubahan langsung ke BRD atau Notion | Itu melanggar aturan task. Pulihkan lewat Version history di Google Docs atau Notion, lalu tambahkan "Hanya membaca" di awal prompt task |
| Jadwal harian tidak berjalan saat kelas | Normal. Di kelas task dijalankan dengan **Run now**. Jadwal berjalan di waktu yang ditentukan |
