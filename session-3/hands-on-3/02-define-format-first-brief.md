# Langkah 2: Tentukan format dan brief pertama

Durasi ±7 menit. Brief yang berubah bentuk tiap minggu sulit dibaca. Kamu menetapkan format tetap lebih dulu, mengujinya sekali di chat, baru menjadikannya task di Langkah 3.

## Yang dikerjakan

1. Baca [`brief-format.md`](sources/brief-format.md): empat bagian tetap dan aturan angka.
2. Kirim Prompt di bawah di chat Project WebTM. Claude membaca backlog dan MoM di Notion dan menulis brief di chat, tanpa menyimpan ke mana pun.
3. Reviewer memeriksa dengan **Cek mutu brief** (6 pemeriksaan di [README](README.md#cek-mutu-brief)). Bandingkan angka brief dengan backlog baris per baris.
4. Catatan MoM seharusnya berbunyi "tidak ada MoM baru": dua MoM bertanggal 7 dan 14 Oktober 2026, dan MoM Review BRD belum bertanggal.
5. Driver mencatat di [scorecard](../scorecard.md) baris v1. Pilih satu temuan untuk Langkah 4.

## Prompt

Ganti dulu: `[LINK BRD]`.

```
CONTEXT
Sumber data: database "WebTM Backlog" dan "WebTM MoM" di halaman "WebTM" di Notion. BRD WebTM v1.1: [LINK BRD]. Format brief di bawah.

TASK
Tulis brief progres proyek. Hanya baca: jangan mengubah Notion, BRD, atau apa pun.

RULES
- Empat bagian tetap: Progres, Prioritas minggu ini, Hambatan, Catatan MoM.
- Progres: jumlah story per Status dengan Story ID untuk tiap angka.
- Prioritas: maksimal tiga story, masing-masing dengan alasan satu kalimat.
- Hambatan: alasan, sumber (Story ID, ID requirement, atau MoM), dan tindakan yang diminta dari peran apa.
- Catatan MoM: hanya MoM dengan Tanggal meeting hari ini atau kemarin. Tiap poin yang berdampak: ID requirement dan Story ID terdampak, dan usulan perubahan BRD bila poin itu mengisi TBC atau menambah aturan. Poin yang bertentangan dengan BRD, atau keputusan yang masih sementara atau terbuka, ditulis sebagai pertanyaan. Tanpa MoM baru tulis "tidak ada MoM baru".
- Yang tidak ada di data ditulis "tidak ada data". Jangan menebak tanggal, nama orang, atau persentase.
- Maksimal 300 kata. Awali dengan tanggal data diambil.

OUTPUT FORMAT
Brief dalam bahasa Indonesia dengan empat judul bagian. Akhiri dengan "Usulan menunggu persetujuan."
```

## Cek

- Empat bagian tetap ada dan maksimal 300 kata.
- Setiap angka bisa ditelusuri ke Story ID dan cocok dengan Notion.
- Catatan MoM berbunyi "tidak ada MoM baru" (MoM lama diabaikan).
- Tidak ada nama orang, tanggal, atau persentase yang tidak ada di data.
- Scorecard v1 terisi.

---

Sebelumnya: [Langkah 1: Siapkan data progres](01-prepare-progress-data.md)  
Berikutnya: [Langkah 3: Buat scheduled task dan jalankan](03-create-scheduled-task.md)
