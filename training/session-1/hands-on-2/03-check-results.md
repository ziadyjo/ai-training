# Langkah 3: Periksa dan rapikan hasil

Durasi ±12 menit. Satu prompt memeriksa kutipan, jenis, dan nama bagian BRD sekaligus, jadi hasilnya satu tabel yang konsisten.

## Yang dikerjakan

1. Pilih baris yang kutipannya diperiksa: tiga baris dengan jenis berbeda, misalnya G03, G06, G09, atau tulis `semua`. Kutipan ada di kolom Kutipan sumber, setelah label `BRD:` dan `Sumber:` (label itu bukan teks dokumen).
2. Kirim prompt di bawah di kotak **Reply** pada chat yang sama dengan laporan review, `[BARIS]` diganti. Claude membaca ulang BRD dan Product Concept, sekitar 2 sampai 3 menit.
3. Baca tabel hasilnya, lalu buka satu lokasi dari kolom Lokasi untuk memastikan. Di BRD: tekan Ctrl+F (Cmd+F di Mac) di Google Docs dan cari potongan pendek kutipan, tanpa label dan tanda kutip. Di Product Concept: buka Project, klik **Context**, klik berkasnya, lalu cari bagian yang disebut. Kutipan dari gambar dilihat langsung di gambarnya.
4. Kalau kutipan tidak ada di lokasi itu, kirim `Kutipan [ID] tidak kutemukan di lokasi itu. Cari lagi, atau tulis Tidak ditemukan.`

## Prompt

Ganti dulu: `[BARIS]` dengan nomor baris, misalnya `G03, G06, G09`, atau tulis `semua`.

```
TASK
Periksa tabel review di atas, lalu perbaiki:
1. Kutipan: untuk [BARIS], cari kutipan BRD di dokumen BRD dan kutipan Sumber di Product Concept, termasuk gambar.
2. Jenis: cocokkan dengan definisi di Kriteria review Skill brd-review (Terpenuhi, Hilang, Ambigu, Konflik, Belum lengkap). Pindahkan yang salah jenis. Temuan yang hanya berasal dari teks sumber yang sengaja dihapus atau disamarkan (mis. "[link internal dihapus]") bukan gap: keluarkan dari tabel.
3. Bagian BRD: samakan namanya dengan judul bagian di template (mis. 4 Project Summary, 5 Project Scope, 7 Requirement, 8 Appendix).

OUTPUT FORMAT
1. Satu tabel lengkap dengan kolom ID, Jenis, Bagian BRD, Kutipan sumber, Clarification question, Verifikasi (Ditemukan, Tidak ditemukan, Tidak berlaku bila sumbernya memang tertulis tidak disebut, atau Tidak diperiksa), dan Lokasi (bagian atau ID di BRD, judul bagian atau tabel di Product Concept). Jenis dan Bagian BRD memakai hasil perbaikan.
2. Daftar baris yang diubah atau dikeluarkan: ID, nilai lama, nilai baru (atau "dikeluarkan"), dan satu kalimat alasan. Kalau tidak ada, tulis "Tidak ada perubahan".

RULES
- Jangan menulis Ditemukan kalau kamu tidak bisa menunjuk lokasinya.
- Kutipan sumber harus relevan dengan klaim gap, bukan sekadar ada di dokumen. Bila sumber gap berupa gambar yang tidak bisa kamu buka, tulis Tidak diperiksa.
- Jangan menambah temuan dan jangan menghapus selain yang sesuai poin 2. Jangan mengubah kutipan dan pertanyaan.
```

## Cek

- Kolom Verifikasi terisi untuk baris yang kamu sebut, dengan lokasi. Baris yang sumbernya "tidak disebut" berstatus Tidak berlaku.
- Jenis dan Bagian BRD di tabel akhir sudah sesuai Kriteria review dan template.
- Satu lokasi sudah kamu buka sendiri dan kutipannya ada, dan isinya menjawab klaim gap itu.

---

Sebelumnya: [Langkah 2: Jalankan /brd-review](02-run-review.md)  
Berikutnya: [Langkah 4: Tulis clarification questions](04-write-questions.md)
