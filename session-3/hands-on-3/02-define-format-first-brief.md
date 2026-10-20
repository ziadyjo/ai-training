# Langkah 2: Tentukan format dan brief pertama

Durasi ±8 menit. Brief yang berubah bentuk tiap minggu sulit dibaca. Kamu menetapkan format tetap lebih dulu, lalu minta brief pertama dari backlog.

## Yang dikerjakan

1. Baca [`brief-format.md`](sources/brief-format.md): tiga bagian tetap dan aturan angka.
2. Kirim Prompt di bawah. Claude membaca backlog di Notion dan menulis brief di chat, tanpa menyimpan atau mengirim ke mana pun.
3. Reviewer memeriksa dengan **Cek mutu brief** (6 pemeriksaan di [README](README.md#cek-mutu-brief)). Bandingkan angka brief dengan backlog baris per baris.
4. Driver mencatat di [scorecard](../scorecard.md) baris v1.
5. Jangan memperbaiki dulu. Pilih satu temuan untuk Langkah 4.

## Prompt

Ganti dulu: `[TANGGAL]`.

```
CONTEXT
Tanggal: [TANGGAL]. Sumber data: database "WebTM Backlog" di Notion. Format brief ada di bawah.

TASK
Tulis brief progres proyek dari backlog. Hanya baca, jangan mengubah Notion.

RULES
- Tiga bagian tetap: Progres, Prioritas minggu ini, Hambatan.
- Progres: jumlah story per Status, dan story yang berubah. Sebut Story ID untuk tiap angka.
- Prioritas: maksimal tiga story, masing-masing dengan alasan satu kalimat.
- Hambatan: tiap hambatan dengan alasan, sumber (Story ID), dan tindakan yang diminta dari siapa.
- Yang tidak ada di backlog ditulis "tidak ada data". Jangan menebak tanggal, nama orang, atau persentase.
- Maksimal 200 kata. Awali dengan tanggal data diambil.

OUTPUT FORMAT
Brief dalam bahasa Indonesia dengan tiga judul bagian.
```

## Cek

- Tiga bagian tetap ada dan maksimal 200 kata.
- Setiap angka bisa ditelusuri ke Story ID, dan cocok dengan Notion.
- Tidak ada nama orang, tanggal, atau persentase yang tidak ada di backlog.
- Hambatan punya alasan, sumber, dan tindakan.
- Scorecard v1 terisi.

---

Sebelumnya: [Langkah 1: Siapkan data progres dan MoM](01-prepare-progress-data.md)  
Berikutnya: [Langkah 3: Buat scheduled task dan jalankan](03-create-scheduled-task.md)
