# Format brief progres

Empat bagian tetap, urutan tetap. Maksimal 300 kata.

```
Data diambil: [tanggal]

PROGRES
- Done: [jumlah] ([Story ID])
- In Progress: [jumlah] ([Story ID])
- Blocked: [jumlah] ([Story ID])
- Backlog: [jumlah]

PRIORITAS MINGGU INI (maksimal 3)
1. [Story ID] [judul]: [alasan satu kalimat]

HAMBATAN
- [Story ID]: [alasan]. Sumber: [Story ID, ID requirement, atau MoM]. Tindakan: [peran yang melakukan apa]

CATATAN MOM (MoM dengan Tanggal meeting hari ini atau kemarin)
- [Judul MoM], poin [nomor]: [isi singkat]. Dampak: [ID requirement dan Story ID], atau "tidak berdampak"
- Usulan perubahan BRD: [ID requirement]: [bunyi usulan]. Menunggu persetujuan.
- Tanpa MoM baru: tulis "tidak ada MoM baru"
```

Aturan:
- Angka selalu disertai Story ID sumbernya.
- Yang tidak ada di data ditulis "tidak ada data". Tanggal, nama orang, dan persentase tidak ditebak.
- Hambatan tanpa alasan atau tindakan tidak ditulis.
- Poin MoM yang bertentangan dengan BRD, atau keputusan yang masih sementara atau terbuka, ditulis sebagai pertanyaan, bukan usulan.
- Brief hanya membaca. Tidak ada yang ditulis ke Notion atau BRD.
