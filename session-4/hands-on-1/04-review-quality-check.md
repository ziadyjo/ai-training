# Langkah 4: Review coverage dan Cek mutu

Durasi ±8 menit. Kamu tidak menilai test case dari kesan pertama, tetapi dari enam pemeriksaan tetap. Reviewer membaca daftarnya dan mencatat.

## Yang dikerjakan

1. Baca bagian **Cek mutu test case** hasil Claude. Bandingkan dengan pemeriksaanmu sendiri memakai [daftar di README](README.md#cek-mutu-test-case): Claude tidak boleh memberi lulus pada hal yang jelas kurang. Cek silang juga dengan flow Miro: setiap cabang keputusan dan exception punya test case atau tercatat sebagai gap.
2. Isi [scorecard](../scorecard.md) baris v1: Cek mutu, test case tanpa dasar, dan hal yang kurang.
3. Kirim Prompt di bawah bila kamu ingin Claude menunjukkan test case yang melanggar tiap pemeriksaan.
4. Pilih satu temuan paling penting untuk Langkah 5. Temuan yang biasa muncul: requirement dengan aturan belum punya skenario negatif, expected terlalu umum, atau requirement yang belum punya test case.

## Prompt

```
CONTEXT
Tabel test case di chat ini.

TASK
Periksa tabel dengan enam pemeriksaan Cek mutu test case. Jangan mengubah tabel.

RULES
- Untuk tiap pemeriksaan yang gagal, sebut TC atau ID requirement yang melanggar dan satu perbaikan yang diusulkan.

OUTPUT FORMAT
Tabel: pemeriksaan, hasil, TC atau ID yang melanggar, perbaikan.
```

## Cek

- Scorecard v1 terisi dengan angka dari pemeriksaanmu, bukan hanya dari Claude.
- Satu temuan dipilih dan disebut dengan ID-nya.
- Tabel test case belum diubah.

---

Sebelumnya: [Langkah 3: Prioritas dan coverage matrix](03-priority-coverage.md)  
Berikutnya: [Langkah 5: Iterasi, tambah aturan ke Skill](05-iterate-skill.md)
