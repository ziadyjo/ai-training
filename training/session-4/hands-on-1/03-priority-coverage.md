# Langkah 3: Prioritas dan coverage matrix

Durasi ±10 menit. Claude mengusulkan prioritas, kamu yang memutuskan. Lalu kamu memilih test case yang akan dijalankan di Hands-on #2.

## Yang dikerjakan

1. Baca kolom Prioritas dan alasannya. Prioritas Tinggi hanya untuk jalur utama dan aturan yang bila gagal membuat fitur tidak bisa dipakai.
2. Kirim Prompt A di chat yang sama. Claude menilai ulang prioritas dengan alasan dan menampilkan coverage matrix.
3. Ubah prioritas yang tidak masuk akal. Sebut ID test case dan alasannya.
4. Kirim Prompt B untuk memilih 3 sampai 5 test case yang akan dijalankan di Hands-on #2.
5. Catat nomor test case terpilih dan requirement yang belum teruji.

## Prompt A: prioritas dan coverage

```
CONTEXT
Test case di atas, dari requirement RM-001, RM-004, RM-005, dan RM-006.

TASK
Tinjau prioritas dan coverage. Jangan mengubah isi test case.

RULES
- Tiap prioritas punya alasan satu kalimat berdasarkan dampak bila gagal.
- Coverage matrix: baris requirement, kolom TC, tanda x.
- Sebut requirement yang belum punya test case dan test case yang tidak punya requirement.
- Jangan menambah test case baru. Usulan penambahan ditulis terpisah sebagai daftar.

OUTPUT FORMAT
Tabel prioritas (TC, prioritas, alasan), coverage matrix, daftar gap, daftar usulan tambahan.
```

## Prompt B: pilih untuk dijalankan

```
Dari test case di atas, pilih 3 sampai 5 yang paling cocok dijalankan di prototype lewat browser. Syaratnya: prioritas Tinggi atau Sedang, langkahnya hanya klik dan ketik, dan expected-nya terlihat di layar. Urutkan dari yang paling sederhana. Beri alasan satu kalimat per pilihan. Jangan menjalankan apa pun.
```

## Cek

- Tidak semua test case berprioritas Tinggi.
- Coverage matrix menyebut gap dengan jelas.
- Test case terpilih bisa dijalankan tanpa login dan tanpa data nyata.
- Daftar usulan tambahan terpisah dari tabel test case.

---

Sebelumnya: [Langkah 2: Hasilkan test case v1](02-generate-test-cases.md)  
Berikutnya: [Langkah 4: Review coverage dan Cek mutu](04-review-quality-check.md)
