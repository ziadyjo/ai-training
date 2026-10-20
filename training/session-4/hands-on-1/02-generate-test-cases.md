# Langkah 2: Hasilkan test case v1

Durasi ±15 menit. Kamu menjalankan Skill pada beberapa requirement dan memeriksa hasilnya di chat. Belum ada yang dijalankan di browser.

## Yang dikerjakan

1. Di chat baru dalam Project WebTM, pilih **Sonnet 5.5**. Ketik `/qa-test`, pilih Skill dari daftar, lalu tempel prompt di bawah dengan link BRD-mu.
2. Skill membaca BRD lewat connector (kartu izin muncul, pilih **Allow once**). Dia menampilkan tabel test case, coverage matrix, **Cek mutu test case** (N dari 6), dan daftar pertanyaan.
3. Reviewer membaca hasilnya dengan daftar di bagian Cek. Driver tidak memperbaiki apa pun dulu.
4. Simpan tabelnya: kamu memakainya di Langkah 3 sampai 5. Scorecard baris v1 diisi di Langkah 4.

## Prompt

Ganti dulu: `[LINK BRD]`.

```
/qa-test [LINK BRD]

Fokus: alur Create New Role dan Daftar Role di WebTM (admin web, pengguna Super Admin). Pakai requirement RM-001, RM-004, RM-005, dan RM-006. Berhenti setelah test case, coverage matrix, Cek mutu, dan pertanyaan. Jangan menjalankan apa pun.
```

## Cek

- Setiap test case punya ID requirement (atau "tanpa rujukan").
- Langkah bernomor dan satu aksi per langkah.
- Expected result bisa dilihat di layar.
- Isi pesan error yang TBC di BRD tidak dikarang.
- Ada baris coverage untuk keempat requirement, termasuk yang belum punya test case.

---

Sebelumnya: [Langkah 1: Bangun qa-test dari starter](01-build-qa-test.md)  
Berikutnya: [Langkah 3: Prioritas dan coverage matrix](03-priority-coverage.md)
