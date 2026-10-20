# Langkah 2: Analisis struktur dan konvensi BRD

Durasi ±6 menit. Tujuannya memastikan connector benar-benar membaca template dari link salinanmu (sekaligus menguji koneksi dari Quick Setup), dan kamu mengenal struktur serta konvensi yang nanti diisi Skill. Konvensi dilihat dari Reference BRD di Context Project.

## Yang dikerjakan

1. Buka chat baru di dalam Project, lalu pilih **Opus 5.5** di model picker. Effort biarkan **Medium**.
2. Tempel prompt di bawah, ganti `[LINK SALINAN]` dengan link salinan "BRD WebTM v1.0", lalu baca tabel hasilnya.

## Prompt

```
TASK
Baca template BRD di link di bawah, lewat Google Docs connector, lalu rangkum strukturnya dalam satu tabel. Setelah itu baca Reference BRD di Context Project untuk melihat konvensi penulisannya.

LINK
[LINK SALINAN]

OUTPUT FORMAT
Tabel dengan satu baris per bagian template dan kolom Bagian BRD | Fungsi | Konvensi penulisan | Contoh di Reference BRD. Tulis format ID requirement di kolom Konvensi penulisan pada baris Requirement. Kolom Contoh berisi satu contoh pendek bentuk penulisan dari Reference BRD, tanpa menyalin isi requirement.

RULES
- Baca template sekarang lewat Google Docs connector. Jangan memakai ingatan dari chat lain atau dokumen lampiran.
- Struktur hanya dari template. Jangan menambah bagian yang tidak ada di template. Reference BRD hanya untuk kolom Contoh.
- Kolom Contoh memakai placeholder seperti [X] dan [peran], bukan kutipan isi Reference (tanggal, nama field, butir perubahan). Pola ID boleh ditulis lengkap.
- Isian yang belum pasti, misalnya format tanggal, ditandai TBC di tabel.
- Jangan bertanya dan jangan menyusun BRD. Berhenti setelah tabel.
```

## Cek

Tabel memuat delapan bagian bernomor sesuai template (Document Identity sampai Appendix), dan kolom Contoh terisi bentuk dari Reference BRD (mis. pola ID `[PREFIX]-001`, pemisahan Business Requirement dan Functional Requirement). Baris tambahan untuk Cover, Header, Table of Contents, dan sub-bagian 8.1 sampai 8.3 wajar, karena semuanya ada di template. Bila ada yang kurang atau tidak ada di template, beri feedback spesifik, misalnya: "Bagian X tidak ada di template, perbaiki tabelnya hanya dari template."

Pastikan di riwayat chat ada langkah pemakaian Google Docs connector. Kalau Claude menjawab "sudah terbaca di langkah sebelumnya" tanpa memakainya, kirim ulang: "Baca ulang template lewat Google Docs connector, lalu perbarui tabelnya."

Kalau Claude gagal membaca template, periksa link salinanmu dan koneksi Google Docs connector (Quick Setup), lalu kirim ulang prompt.

Kalau Claude menulis bahwa Reference BRD tidak ada di Context Project dan kolom Contoh berisi TBC, buka Context Project dan pastikan kedua berkas ada dan sudah selesai diproses. Pastikan juga chat dibuka dari dalam Project, lalu kirim ulang prompt.

Kalau Claude menawarkan menyusun BRD atau bertanya, abaikan dulu. BRD disusun lewat Skill di Langkah 5.

---

Sebelumnya: [Langkah 1: Buat Project dan isi Instructions](01-create-project.md)  
Berikutnya: [Langkah 3: Lengkapi starter Skill](03-complete-starter.md)
