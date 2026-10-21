# Langkah 6: Konsolidasi dan QA Report

Durasi ±10 menit. Hasil langkah ini adalah **QA Report**: satu halaman yang merangkum hasil uji, defect, bukti, dan usulan. Satu defect bisa berasal dari dua tempat: prototype yang salah, atau requirement yang kurang jelas. Perbaikan prototype kembali ke Claude Code. Requirement yang kurang jelas menjadi usulan change note untuk BRD, yang menunggu persetujuan manusia.

## Yang dikerjakan

1. Kirim prompt di bawah ke chat Project yang sama dengan Langkah 4 dan 5 (berisi execution record dan defect record). Claude menyusun QA Report dengan format Skill `qa-run` dan memisahkan defect menurut asalnya.
2. Baca usulan change note. Tiap butir menyebut ID requirement, bunyi sekarang, usulan, dan test case atau defect yang mendasarinya.
3. Setujui atau tolak tiap butir. Claude tidak menulis ke BRD. Bila kamu menyetujui, kamu atau pemilik BRD menuliskannya sendiri di bagian Changes.
4. Simpan QA Report sebagai `qa-report.md` di folder `webtm-prototype` (salin dari chat), bersama execution record dan defect record. Defect yang berasal dari prototype diperbaiki nanti di tab Code dengan prompt iterasi Sesi 3, lalu test case-nya dijalankan ulang.

## Prompt

```
/qa-run

CONTEXT
Execution record dan defect record di atas, dari test case yang dijalankan di prototype WebTM.

TASK
Susun QA Report dan pisahkan defect menurut asalnya. Jangan menulis ke BRD atau Google Docs.

RULES
- Konsolidasi: jumlah Lulus, Gagal, Terblokir, dan jumlah defect.
- Untuk tiap defect, tulis asalnya: Prototype (perilaku tidak sesuai requirement yang jelas) atau Requirement (requirement kurang jelas atau bertentangan).
- Defect berasal Requirement menjadi usulan change note: ID requirement, bunyi sekarang, usulan, dasar (TC dan defect).
- Hanya butir yang didukung langsung oleh hasil uji. Jangan menambah usulan dari dugaan.
- Akhiri dengan: "Usulan ini menunggu persetujuan manusia."

OUTPUT FORMAT
QA Report satu halaman dengan bagian: Ringkasan (jumlah per hasil dan satu kalimat kesimpulan), Cakupan (test case dan requirement yang diuji, dan yang belum), Hasil per test case, Defect dengan asal dan tingkat, Bukti (label tangkapan layar), Usulan change note, lalu daftar pertanyaan.
```

## Cek

- Jumlah di QA Report cocok dengan execution record.
- Tiap defect punya asal, dan alasannya masuk akal.
- Usulan change note punya dasar test case atau defect, bukan dugaan.
- BRD tidak berubah.

---

Sebelumnya: [Langkah 5: Iterasi, test case kedua atau aturan lebih ketat](05-iterate-second-run.md)  
Selesai. Isi [scorecard](../scorecard.md) dan cek Kriteria lulus di [README](README.md).
