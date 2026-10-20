# Langkah 1: Hubungkan Notion dan buat user story

Durasi ±10 menit. Notion adalah tempat backlog tinggal. Claude membacanya lewat connector, dan bisa menulis ke sana atas izinmu. Kamu menghubungkannya dulu, baru meminta Claude menyusun user story dari BRD.

## Yang dikerjakan

1. Di aplikasi Claude buka **Customize**, lalu **Connectors**, cari **Notion**, dan sambungkan. Login ke akun Notion milikmu dan beri izin akses ke halaman yang kamu pilih. Notion tidak bisa tersambung untuk akun tamu.
2. Buat halaman kosong `WebTM Backlog` di Notion dan beri izin akses ke halaman itu.
3. Buka chat baru di Project WebTM dan pilih **Sonnet 5.5**. Cek koneksi dengan Prompt A.
4. Kirim Prompt B untuk menyusun user story dari BRD. Claude membaca BRD lewat connector Google Docs (pilih **Allow once**).
5. Tulis temuanmu: berapa story, mana yang TBC.

## Prompt A: cek koneksi

```
Cari halaman "WebTM Backlog" di Notion dan sebutkan judul serta isinya. Jangan membuat atau mengubah halaman apa pun.
```

## Prompt B: user story

Ganti dulu: `[LINK BRD]`.

```
CONTEXT
BRD WebTM: [LINK BRD]. Fokus pada bagian Role Management dan Access Control. Pengguna: Super Admin.

TASK
Susun user story dari requirement BRD. Target 8 sampai 12 story. Jangan menulis ke Notion dulu.

RULES
- Format: "Sebagai [peran], saya ingin [tujuan], supaya [manfaat]".
- Tiap story: judul, ID requirement sumber (RM-xxx atau AC-xxx), minimal dua acceptance criteria yang bisa dijawab ya atau tidak.
- Satu story satu tujuan. Pecah bila terlalu besar.
- Requirement yang masih TBC (mis. pesan validasi, mapping Change Log) tidak dijadikan story berisi tebakan. Masukkan ke bagian Pertanyaan dengan ID requirement-nya.
- Jangan menambah story di luar BRD.

OUTPUT FORMAT
Daftar story bernomor S-01 dan seterusnya, lalu bagian Pertanyaan.
```

## Cek

- Notion tersambung dan Claude menemukan halaman `WebTM Backlog`.
- Setiap story punya ID requirement dan acceptance criteria yang bisa diperiksa.
- Requirement TBC ada di Pertanyaan, bukan di story.
- Belum ada yang ditulis ke Notion.

---

Berikutnya: [Langkah 2: Draf backlog dan Cek mutu](02-draft-backlog-quality-check.md)
