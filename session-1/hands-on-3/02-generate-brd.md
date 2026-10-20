# Langkah 2: Cocokkan notulen dan perbarui BRD menjadi v1.1

Durasi ±11 menit. Satu prompt melakukan dua hal: mencocokkan notulen dengan gap list, lalu memperbarui BRD v1.1 dengan `brd-draft` dalam Mode perbarui. Claude menampilkan pencocokan dan daftar perubahan di chat, dan hanya bagian di daftar itu yang ditulis ke dokumen.

## Yang dikerjakan

1. Di chat Langkah 1 (notulen dan gap list sudah terlampir), tempel prompt di bawah di baris pertama dengan `/brd-draft`, ganti isian dalam kurung siku, lalu kirim bersama gap list.
2. Claude menampilkan dua hal: tabel pencocokan (tiap gap berstatus Terjawab, Gugur, atau TBC, dengan nomor poin notulen) dan daftar perubahan BRD (bagian atau ID, isi lama, isi baru, nomor poin). Periksa keduanya.
3. Balas "Setuju, tulis ke salinan." dan setujui kartu izin connector saat Claude menulis.
4. Buka `BRD WebTM v1.1` di Google Docs. Kalau perubahan tampil sebagai saran (teks dicoret dan disorot), terima semuanya lewat **Tools > Review suggested edits > Accept all**. Periksa bagian yang ada di daftar dan pastikan bagian lain tidak berubah.

## Prompt

Ganti dulu: `[LINK SALINAN V1.1]`, `[Namamu]`, `[Jabatanmu]`, `[Tanggal]`.

```
/brd-draft [LINK SALINAN V1.1]

CONTEXT
BRD ini hasil Hands-on #1 (v1.0, disalin menjadi v1.1). Terlampir notulen meeting klarifikasi dan gap list Hands-on #2.

TASK
1. Cocokkan setiap poin notulen dengan gap yang dijawabnya. Tampilkan tabel ringkas: gap, status, dan nomor poin notulen. Poin notulen yang tidak menjawab gap mana pun dicantumkan di daftar terpisah.
2. Perbarui BRD ini ke versi 1.1 dengan Mode perbarui. Tampilkan daftar perubahan di chat dulu. Jangan menulis apa pun ke dokumen sebelum aku setuju.

IDENTITAS
Versi: 1.1. Penyusun: [Namamu] - [Jabatanmu]. Tanggal: [Tanggal].

RULES
- Status hanya Terjawab, Gugur, atau TBC. Jawaban sebagian ditulis TBC dengan catatan.
- Gap yang sudah terjawab ditulis dari notulen. Yang belum terjawab tetap TBC.
- Fitur yang gugur dihapus beserta turunannya.
- Catat tiap perubahan di 8.3 Changes dengan nomor poin notulen, dan tambahkan satu baris di Document Change Control.
- Jangan menambah jawaban yang tidak ada di lampiran. Jangan mengubah bagian yang tidak terkait dengan notulen.
```

## Cek

- Tabel pencocokan muncul: tiap gap berstatus Terjawab, Gugur, atau TBC dengan nomor poin notulen. Poin notulen yang tidak menjawab gap mana pun (mis. Business Unit, Managed Roles, Master Menu) ada di daftar terpisah, dan dua hal yang belum terjawab (login saat Taconnect tidak bisa diakses, tanggal go-live) boleh ditulis sebagai di luar cakupan Role Management atau sebagai TBC.
- Daftar perubahan muncul di chat sebelum ada yang ditulis, dan tiap perubahan menyebut nomor poin notulen.
- Di Docs, Document Change Control punya baris 1.1, 8.3 Changes memuat perubahannya, dan bagian yang tidak ada di daftar tidak berubah.
- `BRD WebTM v1.0` Hands-on #1 tidak berubah. Kalau tabel Requirement berantakan, catat sebagai temuan untuk iterasi Skill dan jangan diperbaiki manual dulu.
- Kalau connector gagal menulis, salin hasil dari chat ke salinanmu secara manual.

Tertinggal atau BRD Hands-on #1 tidak ada? Salin isi [`sources/brd-v1-1-checkpoint.md`](sources/brd-v1-1-checkpoint.md) ke salinan template baru bernama `BRD WebTM v1.1`, lalu lanjut ke Langkah 3.

---

Sebelumnya: [Langkah 1: Siapkan v1.1, notulen, dan gap list](01-add-notes.md)  
Berikutnya: [Langkah 3: Review BRD](03-review-brd.md)
