# Langkah 1: Bangun qa-test dari starter

Durasi ±12 menit. `qa-test` belum lengkap: starter hanya punya input, langkah kerja, dan format dasar. Kamu menambahkan dua bagian yang menjaga test case tetap jelas dan terukur, lalu memasangnya.

## Yang dikerjakan

1. Buka **Customize** di sidebar, tab **Skills**, klik **+ Add**, pilih **Create a skill**.
2. Isi **Skill name** dengan `qa-test`.
3. Isi **Description** dengan teks di bagian "Description" di bawah.
4. Buka [`sources/qa-test-starter/SKILL.md`](sources/qa-test-starter/SKILL.md). Salin semua isi setelah baris `---` kedua (mulai dari `# QA Test`) ke editor instruksi.
5. Ganti dua bagian yang masih kosong di editor, "Aturan dan validasi" dan "Cek mutu test case", dengan teks di bagian "Yang kamu tambahkan" di bawah. Klik **Create**.
6. Buka Project **WebTM Role & User Management** dan mulai chat baru. Siapkan link BRD-mu.
7. Siapkan prototype-mu dari Sesi 3 (`index.html`), atau minta prototype acuan ke instruktur. Dibuka di Hands-on #2, belum sekarang.

Tertinggal? Minta Skill `qa-test` lengkap ke instruktur dan pasang dengan cara yang sama.

## Description

```
Dipakai saat BRD dengan ID requirement sudah ada dan analis perlu test case: skenario uji dengan prakondisi, langkah bernomor, expected result, prioritas, dan coverage matrix terhadap requirement. Pakai juga saat analis menulis "buat test case", "susun skenario uji", atau "cek coverage". Tidak menjalankan test case dan tidak menulis ke BRD.
```

## Yang kamu tambahkan

Ganti baris "(Tambahkan di Langkah 1 ...)" di bagian "Aturan dan validasi" dengan:

```
- Setiap test case bertaut ke ID requirement. Kalau tidak ada dasar di requirement, tulis "tanpa rujukan" dan pindahkan ke pertanyaan.
- Satu test case, satu tujuan. Langkah bernomor, satu aksi per langkah.
- Expected result harus bisa diamati di layar: teks yang muncul, elemen yang berubah, data yang tampil. Jangan menulis "berfungsi" atau "benar".
- Isi yang masih TBC di requirement (mis. teks pesan) ditulis sebagai pertanyaan. Expected cukup menyatakan bahwa pesan tampil.
- Jangan menambah test case untuk fitur yang tidak ada di requirement.
- Pakai data fiktif. Jangan memakai data nyata.
- Tidak menulis ke BRD atau Google Docs. Skill ini hanya menyusun test case.
- Bahasa Indonesia; istilah teknis tetap Inggris.
```

Ganti baris "(Tambahkan di Langkah 1 ...)" di bagian "Cek mutu test case" dengan:

```
Enam pemeriksaan tetap, sama di setiap versi:
1. **Rujukan:** setiap test case tertaut ke ID requirement, atau ditandai "tanpa rujukan" dan masuk pertanyaan.
2. **Langkah:** prakondisi tertulis, langkah bernomor dengan satu aksi per langkah, dan orang lain bisa menjalankannya tanpa bertanya.
3. **Expected:** setiap expected result konkret dan bisa diamati, bukan "berfungsi" atau "benar".
4. **Prioritas:** Tinggi, Sedang, atau Rendah terisi dengan alasan satu kalimat.
5. **Skenario:** requirement yang punya aturan punya skenario positif dan negatif.
6. **Tanpa karangan:** tidak ada test case untuk hal di luar requirement, dan yang TBC tercatat sebagai pertanyaan.

Tulis tabel Pemeriksaan, Hasil (lulus atau gagal), dan Alasan satu kalimat. Hasil gagal wajib menyebut TC atau ID requirement yang bermasalah.
```

## Cek

- `qa-test` muncul di daftar Skills dan aktif.
- Tidak ada baris "(Tambahkan di Langkah 1 ...)" tersisa di instruksi.
- Description menjelaskan kapan Skill dipakai.

---

Berikutnya: [Langkah 2: Hasilkan test case v1](02-generate-test-cases.md)
