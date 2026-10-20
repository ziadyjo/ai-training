# Langkah 4: Bandingkan, bukti, dan defect

Durasi ±15 menit. Hasil eksekusi baru berguna bila ditulis sebagai catatan yang bisa diperiksa orang lain. Kamu menyusun execution record dan defect record, lalu memeriksanya dengan enam pemeriksaan tetap.

## Yang dikerjakan

1. Buka chat baru di Project WebTM (bukan side panel) dan pilih **Sonnet 5.5**. Tempel catatan per langkah dari Langkah 3.
2. Kirim prompt di bawah. `qa-run` membandingkan expected dan actual per langkah, memberi hasil Lulus, Gagal, atau Terblokir, menyusun defect, dan menilai **Cek mutu execution record**.
3. Reviewer memeriksa tiap klaim terhadap tangkapan layar. Hasil yang tidak punya bukti diubah menjadi Terblokir.
4. Bandingkan Cek mutu dari Claude dengan [daftar di README](README.md#cek-mutu-execution-record). Isi [scorecard](../scorecard.md) baris v1.
5. Pilih satu temuan paling penting untuk Langkah 5.

## Prompt (kirim ke chat Project)

Ganti dulu: `[TEMPEL CATATAN LANGKAH]`.

```
/qa-run

CONTEXT
Catatan eksekusi satu test case di prototype WebTM ada di bawah, bersama label tangkapan layar yang kupegang.

TASK
Susun execution record dan defect record dari catatan ini. Jangan menjalankan apa pun dan jangan mengubah test case.

RULES
- Bandingkan expected dan actual per langkah. Hasil per langkah: Lulus, Gagal, atau Terblokir.
- Hasil tanpa label bukti ditulis Terblokir dengan alasan.
- Satu ketidaksesuaian, satu defect. Isi semua field defect.
- Akhiri dengan konsolidasi (jumlah per hasil dan jumlah defect) dan Cek mutu execution record.

OUTPUT FORMAT
Execution record, defect record, konsolidasi, Cek mutu execution record (N dari 6).

[TEMPEL CATATAN LANGKAH]
```

## Cek

- Setiap Lulus atau Gagal menyebut label bukti.
- Expected dan actual ada per langkah.
- Defect (bila ada) punya langkah reproduksi, expected, actual, tingkat, dan bukti.
- Jumlah di konsolidasi cocok dengan tabel.
- Scorecard v1 terisi.

---

Sebelumnya: [Langkah 3: Jalankan test case pertama](03-run-first-test-case.md)  
Berikutnya: [Langkah 5: Iterasi, test case kedua atau aturan lebih ketat](05-iterate-second-run.md)
