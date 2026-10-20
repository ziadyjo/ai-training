# Hands-on #1: Test Case Skill & Test Case Development

Kamu membangun Skill `qa-test` dari starter, memakainya untuk menyusun test case dari requirement BRD, memeriksa prioritas dan coverage, lalu memperbaiki Skill-nya dengan satu aturan dan membuktikan hasilnya naik. Berkas yang dipakai ada di [`sources/`](sources/).

| | |
|---|---|
| Durasi | 60 menit |
| Model | Sonnet 5.5 untuk menyusun test case. Opus 5.5 hanya bila perlu menimbang coverage atas banyak requirement |
| Jalur | Chat Claude di Project WebTM, membaca BRD lewat connector Google Docs |
| Hasil | Skill `qa-test` v2, 8 sampai 12 test case berprioritas dengan coverage matrix, Cek mutu test case (N dari 6), scorecard v1 dan v2 |

## Urutan langkah

| Langkah | Isi | Berkas | Menit |
|---|---|---|---|
| 1 | Bangun qa-test dari starter | [01-build-qa-test.md](01-build-qa-test.md) | ±12 |
| 2 | Hasilkan test case v1 | [02-generate-test-cases.md](02-generate-test-cases.md) | ±15 |
| 3 | Prioritas dan coverage matrix | [03-priority-coverage.md](03-priority-coverage.md) | ±10 |
| 4 | Review coverage dan Cek mutu | [04-review-quality-check.md](04-review-quality-check.md) | ±8 |
| 5 | Iterasi: tambah aturan ke Skill | [05-iterate-skill.md](05-iterate-skill.md) | ±15 |

## Cek mutu test case

Enam pemeriksaan tetap. Dipakai di Langkah 4 (v1) dan Langkah 5 (v2). Skor: jumlah yang lolos, dari 6.

| No | Pemeriksaan |
|---|---|
| 1 | Setiap test case tertaut ke ID requirement, atau ditandai "tanpa rujukan" dan masuk pertanyaan |
| 2 | Prakondisi tertulis, langkah bernomor dengan satu aksi per langkah, dan orang lain bisa menjalankannya tanpa bertanya |
| 3 | Expected result konkret dan bisa diamati di layar, bukan "berfungsi" atau "benar" |
| 4 | Prioritas (Tinggi, Sedang, Rendah) terisi dengan alasan satu kalimat |
| 5 | Requirement yang punya aturan punya skenario positif dan negatif |
| 6 | Tidak ada test case untuk hal di luar requirement, dan yang masih TBC tercatat sebagai pertanyaan |

## Cara menyalin prompt

1. Klik tombol salin di pojok kanan blok kode. Satu blok adalah satu prompt.
2. Ganti teks dalam kurung siku, misalnya `[LINK BRD]`, sebelum mengirim.
3. Di kotak chat, tekan Shift+Enter untuk pindah baris. Prompt yang diawali `/` harus berada di baris pertama.

## Tertinggal?

Minta berkas acuan ke instruktur. Hasilmu akan berbeda dari acuan: pakai acuan untuk melanjutkan, bukan untuk menyalin.

## Kriteria lulus

- [ ] Skill `qa-test` terpasang dan terpanggil di chat baru.
- [ ] 8 sampai 12 test case, semua bertaut ke ID requirement atau ditandai "tanpa rujukan".
- [ ] Coverage matrix menunjukkan requirement yang belum punya test case.
- [ ] Prioritas masuk akal dan kamu memilih 3 sampai 5 test case yang akan dijalankan di Hands-on #2.
- [ ] [Scorecard](../scorecard.md) v1 dan v2 terisi, dan v2 lebih tinggi atau sama dengan v1 dengan penyebab yang bisa ditunjuk.
- [ ] Aturan baru tersimpan di Skill, bukan hanya diketik di chat.

## Kalau bermasalah

| Masalah | Jalan keluar |
|---|---|
| Skill tidak muncul saat mengetik `/qa` | Periksa di **Customize**, tab **Skills**, bahwa `qa-test` aktif. Mulai chat baru di Project WebTM. Bila tetap tidak terpanggil, tulis "Gunakan Skill qa-test" di prompt |
| Claude tidak bisa membaca BRD | Pastikan connector Google Docs masih Connected, atau lampirkan BRD acuan dan sebut "BRD terlampir" |
| Test case terlalu banyak atau tentang fitur yang tidak ada | Batasi ke 3 sampai 6 requirement dan sebut ID-nya. Hapus test case tanpa dasar, jangan dipertahankan karena terlihat bagus |
| Expected result berbunyi "berfungsi dengan baik" | Minta Claude menulis ulang expected sebagai teks, elemen, atau data yang tampak di layar |
| Claude mengarang isi pesan error | Pesan yang masih TBC di BRD cukup ditulis "pesan tampil". Isinya masuk daftar pertanyaan |
| Prioritas semua Tinggi | Minta alasan satu kalimat per test case, lalu turunkan yang dampaknya hanya tampilan |
| Hasil v2 tidak lebih baik dari v1 | Cek apakah aturan baru menimpa aturan lain. Kembalikan Skill ke v1 dari `sources/` dan tambahkan hanya satu baris aturan |
| Batas pemakaian tercapai | Tunggu reset atau kurangi jumlah requirement per putaran |
