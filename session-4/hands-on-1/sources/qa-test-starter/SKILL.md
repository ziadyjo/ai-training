---
name: qa-test
description: Dipakai saat BRD dengan ID requirement sudah ada dan analis perlu test case: skenario uji dengan prakondisi, langkah bernomor, expected result, prioritas, dan coverage matrix terhadap requirement. Pakai juga saat analis menulis "buat test case", "susun skenario uji", atau "cek coverage". Tidak menjalankan test case dan tidak menulis ke BRD.
---

# QA Test

Mengubah requirement menjadi test case yang jelas dan bisa dijalankan orang lain. Claude menyusun, analis meninjau dan menyetujui, baru test case dipakai.

## Input
- Requirement dari BRD (link Google Docs lewat connector, atau bagian yang ditempel analis), lengkap dengan ID requirement. Kalau tidak terbaca, minta analis menempel bagian yang dimaksud.
- Opsional: prototype atau mockup sebagai konteks tampilan. Kalau tidak ada, jangan menebak nama tombol dan label.

Kalau tidak ada requirement ber-ID, sebutkan dan berhenti.

## Langkah kerja
1. **Pilih requirement.** Pakai requirement yang disebut analis. Kalau tidak disebut, tanyakan: tiga sampai enam requirement per putaran.
2. **Susun skenario.** Untuk tiap requirement: jalur normal dengan data valid, dan skenario lain yang diminta aturan di requirement.
3. **Tulis test case.** ID berurutan (TC-001), ID requirement, jenis skenario, prakondisi, langkah bernomor, expected result, prioritas dengan alasan.
4. **Prioritas.** Tinggi: jalur utama, kalau gagal fitur tidak bisa dipakai. Sedang: aturan penting yang punya jalan keluar. Rendah: tampilan atau kenyamanan.
5. **Coverage matrix.** Tabel requirement terhadap test case. Tandai requirement yang belum punya test case dan test case yang tidak punya requirement.
6. **Cek mutu test case.** Nilai dengan enam pemeriksaan di bawah, tulis "N dari 6".
7. **Berhenti dan minta persetujuan.** Jangan menjalankan atau mengubah apa pun.

## Aturan dan validasi
(Tambahkan di Langkah 1: aturan yang menjaga test case tetap jelas dan tertaut ke requirement.)

## Cek mutu test case
(Tambahkan di Langkah 1: enam pemeriksaan tetap.)

## Format output
Tabel test case:

| TC | Req | Jenis | Judul | Prakondisi | Langkah | Expected | Prioritas |
|---|---|---|---|---|---|---|---|

Setelah tabel, berurutan: coverage matrix (baris requirement, kolom TC, tanda x), daftar requirement tanpa test case, Cek mutu test case, lalu daftar pertanyaan.
