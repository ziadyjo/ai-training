# Langkah 2: Susun flow spec di chat

Durasi ±15 menit. Flow spec adalah tabel aktor, langkah, keputusan, dan exception. Kamu memeriksanya dulu di chat. Belum ada yang digambar di Miro.

## Yang dikerjakan

1. Di chat baru dalam Project WebTM, pilih **Sonnet 5.5**. Ketik `/flow-diagram`, pilih Skill dari daftar, lalu tempel prompt di bawah dengan link BRD-mu.
2. Skill membaca BRD lewat connector (kartu izin muncul, pilih **Allow once**). Dia menampilkan flow spec, **Cek mutu flow** (N dari 6), daftar exception, daftar pertanyaan, dan instruksi gambar untuk Miro.
3. Reviewer mengecek hasilnya dengan daftar di bagian Cek. Driver mencatat Cek mutu dan temuan di [scorecard](../scorecard.md) baris v1.
4. Jangan menyetujui dulu. Langkah 3 baru menggambar.

## Prompt

Ganti dulu: `[LINK BRD]`.

```
/flow-diagram [LINK BRD]

Flow: Create New Role di Role Management. Susun flow spec dari bagian BRD yang relevan saja. Berhenti sebelum menggambar di Miro.
```

## Cek

- Semua aktor yang kamu temukan di BRD muncul, dengan nama yang sama.
- Setiap keputusan punya dua cabang atau lebih, masing-masing berlabel.
- Ada minimal satu exception sebagai langkah sendiri.
- Langkah yang tidak ada di BRD ditandai "tanpa rujukan" atau ditulis sebagai pertanyaan.
- Hal yang di BRD masih TBC ditulis TBC, bukan diisi sendiri oleh Claude.
- Link BRD bisa terbaca sebagai lampiran, bukan lewat kartu izin connector. Itu normal selama isinya terbaca.

Setiap langkah punya ID requirement yang bisa kamu buka di BRD. Kalau tidak, itu langkah dikarang: hitung di scorecard.

---

Sebelumnya: [Langkah 1: Pasang flow-diagram dan siapkan BRD](01-setup-skill.md)  
Berikutnya: [Langkah 3: Gambar di Miro](03-draw-in-miro.md)
