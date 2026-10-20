# Langkah 4: Review coverage dan Cek mutu

Durasi ±8 menit. Kamu tidak menilai test case dari kesan pertama, tetapi dari enam pemeriksaan tetap. Reviewer membaca daftarnya dan mencatat.

## Yang dikerjakan

1. Baca bagian **Cek mutu test case** hasil Claude. Bandingkan dengan pemeriksaanmu sendiri memakai [daftar di README](README.md#cek-mutu-test-case): Claude tidak boleh memberi lulus pada hal yang jelas kurang. Cek silang juga expected result tiga test case dengan RM-003 sampai RM-005 di [Reference BRD Role Management](../../session-2/reference-brd-role-management.md); selisih yang valid jadi temuan.
2. Isi [scorecard](../scorecard.md) baris v1: Cek mutu, test case tanpa dasar, dan hal yang kurang.
3. Kirim Prompt di bawah bila kamu ingin Claude menunjukkan test case yang melanggar tiap pemeriksaan.
4. Pilih satu temuan paling penting untuk Langkah 5. Temuan yang biasa muncul: requirement dengan aturan belum punya skenario negatif, expected terlalu umum, atau requirement yang belum punya test case.

## Prompt

```
Periksa tabel test case di atas dengan enam pemeriksaan Cek mutu test case. Untuk tiap pemeriksaan yang gagal, sebut TC atau ID requirement yang melanggar dan satu perbaikan yang diusulkan. Jangan mengubah tabel.
```

## Cek

- Scorecard v1 terisi dengan angka dari pemeriksaanmu, bukan hanya dari Claude.
- Satu temuan dipilih dan disebut dengan ID-nya.
- Tabel test case belum diubah.

---

Sebelumnya: [Langkah 3: Prioritas dan coverage matrix](03-priority-coverage.md)  
Berikutnya: [Langkah 5: Iterasi, tambah aturan ke Skill](05-iterate-skill.md)
