# Langkah 4: Cari skenario hilang dan perbaiki Skill

Durasi ±17 menit. Flow yang rapi belum tentu lengkap. Kamu mencari skenario yang belum ada, memilih satu pelajaran, lalu menyimpannya ke Skill supaya flow berikutnya tidak mengulang kekurangan yang sama.

## Yang dikerjakan

1. Tempel Prompt A di chat yang sama. Claude menyebut skenario yang hilang beserta ID requirement sumbernya, atau menulisnya sebagai pertanyaan bila BRD tidak menyebutnya.
2. Pilih satu skenario yang paling penting dan nyata ada di BRD. Satu saja.
3. Tempel Prompt B untuk meminta usulan satu aturan Skill. Baca baris lama dan baris baru, setujui hanya yang relevan.
4. Balas "setuju". Claude menampilkan kartu **Update skill**. Buka **Content**, periksa jumlah barisnya, lalu klik **Update** dan **Update skill** di konfirmasi. Kalau kartu tidak muncul, buka Skill, klik **Edit**, terapkan perubahan, lalu **Save version**.
5. Buka chat baru di Project yang sama, jalankan Prompt C, lalu bandingkan Cek mutu dan flow spec dengan Langkah 2. Catat di [scorecard](../scorecard.md) baris v2.

Tertinggal? Minta Skill `flow-diagram` dengan satu aturan tambahan (hak akses) ke instruktur, pasang lewat **Edit** Skill, lalu jalankan Prompt C.

Referensi tambahan: setelah memilih skenario, cek apakah AC-003 dan RM-005 di [Reference BRD Role Management](../reference-brd-role-management.md) menyebut skenario yang kamu lewatkan. Itu pembanding, bukan sumber flow.

Jangan menggambar ulang di Miro pada langkah ini. Perbandingan cukup dari flow spec.

## Prompt A: cari skenario hilang

```
TASK
Cari skenario yang belum ada di flow Create New Role ini. Untuk setiap skenario sebutkan ID requirement di BRD yang mendasarinya.

RULES
- Kalau BRD tidak menyebut skenario itu, tulis sebagai pertanyaan, bukan sebagai langkah.
- Jangan mengubah flow spec atau board Miro sebelum aku setuju.
- Maksimal lima skenario, urutkan dari yang paling berisiko.
```

## Prompt B: simpan pelajaran ke Skill

Ganti dulu: `[SKENARIO YANG DIPILIH]`.

```
TASK
Skenario berikut hilang dari flow dan aku ingin Skill flow-diagram menangkapnya sendiri di flow berikutnya: [SKENARIO YANG DIPILIH]. Usulkan satu aturan baru di bagian Aturan dan validasi SKILL.md flow-diagram.

OUTPUT FORMAT
Tampilkan perubahan sebagai baris lama dan baris baru, dengan nama bagian yang diubah.

RULES
- Jangan menerapkan apa pun sebelum aku menyetujui.
- Aturan harus berlaku untuk flow apa pun, bukan hanya Create New Role.
- Jangan mengubah bagian lain.
```

## Prompt C: jalankan ulang

Ganti dulu: `[LINK BRD]`.

```
/flow-diagram [LINK BRD]

Flow: Create New Role di Role Management. Susun flow spec dari bagian BRD yang relevan saja. Berhenti sebelum menggambar di Miro.
```

## Cek

Skill punya versi baru dengan satu aturan tambahan, flow spec baru memuat skenario yang kamu pilih (sebagai langkah, atau sebagai TBC bila BRD belum menjawab), dan bagian lain flow tidak berubah tanpa alasan.

Skor Cek mutu bisa tetap sama (mis. 6 dari 6) karena aturan baru tidak mengubah enam pemeriksaannya. Yang dibandingkan adalah isi flow spec: cabang atau exception baru muncul dan langkah lain tidak berubah. Jalankan Prompt C di chat baru supaya hasilnya tidak terpengaruh Prompt A dan B.

Kalau Cek mutu turun atau banyak langkah berubah tanpa sebab, batalkan perubahan: aturan yang terlalu luas menggeser bagian lain.

---

Sebelumnya: [Langkah 3: Gambar di Miro](03-draw-in-miro.md)  
Berikutnya: [Langkah 5: Tautkan flow ke BRD](05-link-to-brd.md)
