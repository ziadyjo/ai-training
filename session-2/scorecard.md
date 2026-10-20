# Scorecard iterasi Sesi 2

Dipakai di kedua hands-on untuk membandingkan hasil dari satu versi ke versi berikutnya. Isi dari hasil nyata, bukan perkiraan. Satu orang mengetik (driver), satu orang menilai (reviewer).

## Cara mengisi

| Kolom | Artinya |
|---|---|
| Cek mutu | Angka "N dari 6" dari bagian Cek mutu di hasil Skill (`flow-diagram` atau `ui-brief`). Enam pemeriksaan sama di tiap versi. Skor flow bisa tetap sama (mis. 6 dari 6) karena aturan baru tidak mengubah pemeriksaannya; bandingkan juga isi |
| Langkah atau elemen dikarang | Langkah flow atau elemen UI yang tidak punya dasar di BRD dan tidak ditandai pertanyaan atau TBC |
| Aktor atau ID hilang | Aktor di BRD yang tidak muncul di flow, atau ID requirement relevan yang terlewat |
| State hilang | State kosong, loading, atau error yang dibutuhkan screen tetapi tidak ada |
| Catatan | Apa yang diubah dari versi sebelumnya |

## Hands-on #1: flow

| Versi | Cek mutu | Jumlah exception | Langkah dikarang | Aktor atau ID hilang | Catatan |
|---|---|---|---|---|---|
| v1 |  |  |  |  |  |
| v2 |  |  |  |  |  |

v1 dari Skill awal (Langkah 2). v2 dari Skill setelah satu aturan ditambah (Langkah 4, Prompt C). Sebutkan aturan yang ditambah di Catatan.

## Hands-on #2: UI

| Versi | Cek mutu | Elemen dikarang | State hilang | Catatan |
|---|---|---|---|---|
| v1 |  |  |  |  |
| v2 |  |  |  |  |

v1: Cek mutu brief dari Langkah 2, elemen dikarang dan state hilang dari layar pertama di Stitch (Langkah 3). v2: layar terpilih setelah feedback (Langkah 4). Cek mutu brief tidak berubah di v2 kecuali kamu menjalankan ulang `/ui-brief`.

## Pola yang diharapkan

Flow: jumlah exception bertambah dan langkah 1 memuat syarat akses karena skenario yang hilang masuk sebagai exception, langkah, atau pertanyaan; Cek mutu bisa tetap 6 dari 6. UI: elemen dikarang turun setelah Prompt C dan D. Angka peserta akan berbeda. Yang penting adalah kamu bisa menunjuk aturan atau prompt yang menyebabkan perubahannya. Kalau skor turun, batalkan perubahan yang tidak terkait.
