# Langkah 6: Konsolidasi dan change note

Durasi ±10 menit. Satu defect bisa berasal dari dua tempat: prototype yang salah, atau requirement yang kurang jelas. Perbaikan prototype kembali ke Claude Code. Requirement yang kurang jelas menjadi usulan change note untuk BRD, yang menunggu persetujuan manusia.

## Yang dikerjakan

1. Kirim prompt di bawah ke chat Project. Claude mengonsolidasikan hasil dan memisahkan defect menurut asalnya.
2. Baca usulan change note. Tiap butir menyebut ID requirement, bunyi sekarang, usulan, dan test case atau defect yang mendasarinya.
3. Setujui atau tolak tiap butir. Claude tidak menulis ke BRD. Bila kamu menyetujui, kamu atau pemilik BRD menuliskannya sendiri di bagian Changes.
4. Simpan: execution record, defect record, dan change note di folder atau Project-mu. Defect yang berasal dari prototype dicatat untuk perbaikan di Claude Code.

## Prompt

```
CONTEXT
Execution record dan defect record di atas, dari test case yang dijalankan di prototype WebTM.

TASK
Konsolidasikan hasil dan pisahkan defect menurut asalnya. Jangan menulis ke BRD atau Google Docs.

RULES
- Konsolidasi: jumlah Lulus, Gagal, Terblokir, dan jumlah defect.
- Untuk tiap defect, tulis asalnya: Prototype (perilaku tidak sesuai requirement yang jelas) atau Requirement (requirement kurang jelas atau bertentangan).
- Defect berasal Requirement menjadi usulan change note: ID requirement, bunyi sekarang, usulan, dasar (TC dan defect).
- Hanya butir yang didukung langsung oleh hasil uji. Jangan menambah usulan dari dugaan.
- Akhiri dengan: "Usulan ini menunggu persetujuan manusia."

OUTPUT FORMAT
Konsolidasi, tabel defect dengan asal, tabel usulan change note, lalu daftar pertanyaan.
```

## Cek

- Jumlah di konsolidasi cocok dengan execution record.
- Tiap defect punya asal, dan alasannya masuk akal.
- Usulan change note punya dasar test case atau defect, bukan dugaan.
- BRD tidak berubah.

---

Sebelumnya: [Langkah 5: Iterasi, test case kedua atau aturan lebih ketat](05-iterate-second-run.md)  
Selesai. Isi [scorecard](../scorecard.md) dan cek Kriteria lulus di [README](README.md).
