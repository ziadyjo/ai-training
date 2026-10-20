# Langkah 3: Buat scheduled task dan jalankan

Durasi ±9 menit. Scheduled task adalah prompt yang dijalankan Claude sesuai jadwal atau sesuai permintaan. Kamu mengubah prompt brief menjadi task, mengatur frekuensi, lalu menjalankannya satu kali tanpa menunggu jadwal.

## Yang dikerjakan

1. Buka **Scheduled** di sidebar aplikasi Claude, klik **New task**, dan pilih mengisi manual. Cara lain: setelah brief di Langkah 2 memuaskan, minta Claude menjadikannya task lewat tombol **Schedule** di percakapan.
2. Isi: nama `Brief Progres WebTM`, prompt dari bagian di bawah, frekuensi **Weekdays** (jam bebas), model **Sonnet 5.5**, dan mode persetujuan yang paling ketat yang ditawarkan (task ini hanya membaca). Bila diminta memilih folder, pilih folder `webtm-prototype`.
3. Simpan, lalu jalankan sesuai permintaan (**Run now**). Bila run berhenti menunggu izin untuk Notion, buka sesinya dan setujui. Pilih izin tetap (always allow) khusus untuk tool baca Notion supaya run berikutnya tidak berhenti. Tunggu sampai selesai.
4. Buka hasil run dari halaman task. Bandingkan dengan brief di Langkah 2: format sama, isi mengikuti backlog.
5. Jangan memilih frekuensi yang membuat task berjalan saat kelas. Task ini berjalan dari jadwal besok pagi, bukan sekarang.

Task yang hanya memakai connector berjalan tanpa komputer menyala. Task yang membaca berkas di komputermu hanya berjalan saat aplikasi terbuka dan komputer menyala.

## Prompt task

```
Tulis brief progres proyek WebTM dari database "WebTM Backlog" di Notion. Hanya baca, jangan mengubah apa pun. Tiga bagian tetap: Progres (jumlah story per Status dengan Story ID, dan yang berubah), Prioritas minggu ini (maksimal tiga story dengan alasan), Hambatan (alasan, sumber Story ID, tindakan yang diminta). Yang tidak ada di backlog tulis "tidak ada data". Jangan menebak nama, tanggal, atau persentase. Maksimal 200 kata, bahasa Indonesia, dan awali dengan tanggal data diambil.
```

## Cek

- Task muncul di daftar **Scheduled** dengan nama, frekuensi, dan model yang benar.
- Run sesuai permintaan selesai tanpa galat.
- Brief hasil run punya tiga bagian dan angka yang cocok dengan Notion.
- Task hanya membaca: tidak ada baris Notion yang berubah.

---

Sebelumnya: [Langkah 2: Tentukan format dan brief pertama](02-define-format-first-brief.md)  
Berikutnya: [Langkah 4: Dampak MoM sebagai usulan dan iterasi](04-mom-impact-iterate.md)
