# Langkah 5: Tautkan flow ke BRD

Durasi ±10 menit. Flow yang tidak tertaut ke BRD akan hilang dari ingatan tim. Kamu menambahkan tautan board dan gambar diagram ke bagian Proposed Business Process di BRD.

## Yang dikerjakan

1. Di chat Langkah 2 (flow yang sudah digambar), tempel prompt di bawah dengan link BRD-mu. Ini menulis ke salinan BRD milikmu, jadi Claude meminta izin tulis. Pilih **Allow once**.
2. Buka BRD. Di bagian 6, bawah isi **Proposed Business Process**, harus ada dua baris baru: tautan ke board Miro dan petunjuk menempel gambar.
3. Ambil gambar diagram: di Miro pilih frame diagram, lalu **Export image** dan simpan. Di BRD, letakkan kursor di bawah baris petunjuk, lalu **Insert > Image > Upload from computer**. Atur lebar gambar sampai teks di kotak terbaca: gambar portrait cukup sekitar 60 persen lebar sel, sedangkan gambar horizontal yang sangat lebar tidak terbaca berapa pun lebarnya (lihat Langkah 3).
4. Reviewer mengecek bahwa isi BRD selain dua baris itu tidak berubah.

Bila bagian 6 sudah memuat link flow lain, tulis di prompt bahwa baris baru ditaruh di bawah baris link itu, bukan di bawah paragraf terakhir. Penempatan gambar tetap manual. Kalau add-on Miro untuk Google Docs sudah terpasang di akunmu, kamu boleh memakai panel samping Miro untuk menyisipkan gambar.

## Prompt

Ganti dulu: `[LINK BRD]` dan `[LINK BOARD]`.

```
Tautkan flow Create New Role yang sudah digambar ke BRD ini: [LINK BRD]

Tambahkan hanya dua baris di bawah isi bagian 6 (Proposed Business Process): satu baris "Diagram flow: Create New Role" sebagai hyperlink ke [LINK BOARD], dan satu baris petunjuk untuk menempel gambar. Jangan mengubah isi BRD yang lain.
```

## Cek

- Di BRD ada hyperlink ke board Miro dan gambar diagram di bagian 6.
- Gambar terbaca di BRD: zoom 100% dan pastikan teks kotak bisa dibaca. Kalau tidak terbaca, gambar ulang di frame baru dengan format portrait (lihat Langkah 3).
- Tidak ada perubahan lain di BRD: bandingkan lewat **Version history** di Google Docs.
- Tabel Requirement, header, dan footer tidak berubah.

Kalau Claude menulis di tempat lain atau mengubah teks, pilih **Restore this version** di Version history, lalu ulangi dengan prompt yang lebih sempit.

---

Sebelumnya: [Langkah 4: Cari skenario hilang dan perbaiki Skill](04-find-gaps-improve-skill.md)
