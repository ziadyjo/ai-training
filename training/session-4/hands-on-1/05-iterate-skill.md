# Langkah 5: Iterasi, tambah aturan ke Skill

Durasi ±15 menit. Hasil AI berbeda tiap kali, jadi iterasi itu normal. Perbaikan yang berulang ditulis ke Skill, bukan diketik ulang di chat. Kamu menambah satu aturan, menjalankan prompt yang sama, dan membandingkan.

## Yang dikerjakan

1. Ambil satu temuan dari Langkah 4. Contoh di bawah memakai aturan skenario negatif.
2. Buka **Customize**, tab **Skills**, buka `qa-test`, lalu tambahkan satu baris aturan di bagian "Aturan dan validasi". Simpan.
3. Mulai chat baru di Project WebTM. Kirim prompt yang sama dengan Langkah 2 (`/qa-test [LINK BRD]` dan fokusnya).
4. Bandingkan v2 dengan v1: Cek mutu, jumlah test case negatif, dan requirement yang masih belum teruji. Isi [scorecard](../scorecard.md) baris v2.
5. Hasil tidak membaik? Kembalikan Skill ke v1 dan coba aturan yang lebih sempit.
6. Pilih 3 sampai 5 test case yang akan dijalankan di Hands-on #2 (ulangi Prompt B di Langkah 3 pada hasil v2). Simpan tabelnya.

## Aturan contoh

```
- Setiap requirement yang punya aturan (unik, wajib, batas, izin) mendapat minimal satu skenario negatif di samping skenario positif. Tulis jenisnya: Positif, Negatif, atau Batas.
```

Aturan lain bila temuanmu berbeda: setiap expected harus menyebut teks atau elemen yang terlihat; requirement tanpa test case harus muncul di daftar gap.

## Cek

- Satu temuan, satu aturan. Bagian lain Skill tidak berubah.
- Aturan tersimpan di Skill (buka lagi `qa-test` untuk memastikan).
- Cek mutu v2 lebih tinggi atau sama dengan v1 dan kamu bisa menunjuk penyebabnya.
- Test case negatif bertambah untuk requirement yang punya aturan.
- Scorecard v2 terisi.

---

Sebelumnya: [Langkah 4: Review coverage dan Cek mutu](04-review-quality-check.md)  
Berikutnya: [Hands-on #2](../hands-on-2/README.md)
