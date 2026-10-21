# Langkah 5: Iterasi, test case kedua atau aturan lebih ketat

Durasi ±15 menit. Hasil AI berbeda tiap kali, jadi iterasi itu normal. Kamu memperbaiki satu temuan dari Cek mutu v1, menjalankan test case kedua (atau mengulang yang pertama), dan membuktikan angkanya naik.

## Yang dikerjakan

1. Ambil satu temuan dari Langkah 4. Contoh: hasil tanpa bukti, expected dan actual hanya ditulis untuk hasil akhir, defect tanpa langkah reproduksi.
2. Pilih satu jalan. Jalan A: kirim prompt iterasi di bawah ke chat Project untuk memperbaiki catatan test case pertama. Jalan B: jalankan test case kedua, sebaiknya negatif (mis. Role Name sama dengan role Inactive, RM-004) di side panel dengan prompt Langkah 3, lalu susun catatannya dengan prompt Langkah 4. Test case negatif paling sering menemukan defect.
3. Jalankan lagi enam pemeriksaan. Isi [scorecard](../scorecard.md) baris v2 dengan apa yang kamu ubah.
4. Hasil tidak membaik? Kembali ke catatan v1 dan perbaiki hanya satu hal.

## Prompt iterasi (Jalan A, kirim ke chat Project)

Ganti dulu: `[TEMUAN]`.

```
CONTEXT
Execution record di chat ini. Temuan dari Cek mutu: [TEMUAN].

TASK
Perbaiki satu hal di execution record sesuai temuan itu.

RULES
- Ubah hanya bagian itu.
- Hasil yang tidak punya label bukti ditulis Terblokir dengan alasan.

OUTPUT FORMAT
Sebutkan baris yang berubah dan pemeriksaan mana yang seharusnya sekarang lolos.
```

## Cek

- Satu temuan, satu perbaikan. Bagian lain tidak berubah.
- Cek mutu v2 lebih tinggi atau sama dengan v1 dan kamu bisa menunjuk penyebabnya.
- Tidak ada hasil baru tanpa bukti.
- Scorecard v2 terisi.

---

Sebelumnya: [Langkah 4: Bandingkan, bukti, dan defect](04-compare-evidence-defects.md)  
Berikutnya: [Langkah 6: Konsolidasi dan QA Report](06-consolidate-qa-report.md)
