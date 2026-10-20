# Langkah 4: Tulis clarification questions

Durasi ±7 menit. **Clarification question** adalah pertanyaan tertutup (ya, tidak, pilihan, atau angka) yang jawabannya bisa langsung ditulis ke BRD.

## Yang dikerjakan

1. Kirim prompt di bawah di chat yang sama.
2. Periksa pembagian peran. Pertanyaan bisnis ke product owner, perilaku sistem ke tim Tech, tampilan dan teks ke UI/UX designer, keputusan tentang isi BRD ke analis.
3. Simpan hasilnya untuk Hands-on #3: biarkan chat ini terbuka, dan klik tombol salin (ikon dua kotak di bawah jawaban Claude) untuk menyalin tabel akhir beserta baris scorecard. Tempelkan baris scorecard ke [scorecard](scorecard.md), sesuai urutan kolom di tabel itu.

## Prompt

```
TASK
Dari tabel hasil Langkah 3:
- Pastikan tiap gap punya satu pertanyaan tertutup (ya, tidak, pilihan, atau angka). Tulis ulang yang masih terbuka tanpa menambah angka atau asumsi yang tidak ada di sumber. Pilihan jawaban hanya dari yang tertulis di sumber atau BRD.
- Gap yang menggabungkan banyak butir (mis. satu baris untuk beberapa ID yang TBC) dipecah menjadi gap turunan G10a, G10b, dan seterusnya, satu pertanyaan dan satu peran per turunan.
- Tetapkan satu peran penjawab per gap: bisnis dan prioritas ke product owner, perilaku sistem dan data ke tim Tech, tampilan dan teks ke UI/UX designer, isi BRD ke analis.
- Jangan menulis pertanyaan tentang dokumen yang tidak kamu buka (mis. desain Figma).

OUTPUT FORMAT
1. Satu tabel lengkap (ID, Jenis, Bagian BRD, Kutipan sumber, Clarification question, Peran), dikelompokkan per peran.
2. Satu baris scorecard: Versi BRD, Skor mutu (dari laporan review), Jumlah temuan (sebelum gap gabungan dipecah), Rincian per jenis (setelah perbaikan), Gap dikarang (jumlah baris Tidak ditemukan dari baris yang diperiksa, dalam bentuk N dari M), dan Catatan kosong.

RULES
- Jangan mengubah Jenis, Bagian BRD, dan Kutipan sumber.
- Jangan menambah atau menghapus gap, kecuali memecah gap gabungan seperti di atas.
```

## Cek

Tiap gap punya satu pertanyaan tertutup dan satu peran penjawab, dan gap gabungan sudah dipecah. Pertanyaan tidak memuat pilihan yang tidak ada di sumber: tolak yang menawarkan opsi karangan, misalnya kombinasi akses atau perilaku dropdown yang tidak tertulis di Product Concept. Baris scorecard dicatat di [scorecard](scorecard.md).

| ID | Jenis | Bagian BRD | Clarification question | Peran |
|---|---|---|---|---|
| G06 | Hilang | 7 Requirement (RM-005) | Siapa pemegang akses menu Role Management: tim IT/FA atau manager? | Product owner |
| G10 | Hilang | 8 Appendix (8.2 Rules) | Apakah definisi Main Role dan Additional Role ditambahkan ke 8.2 Rules? | Analis |

Hasilmu akan berbeda. Gap list acuan: [`sources/gap-list-checkpoint.md`](sources/gap-list-checkpoint.md).

---

Sebelumnya: [Langkah 3: Periksa dan rapikan hasil](03-check-results.md)  
Berikutnya: [Hands-on #3](../hands-on-3/)