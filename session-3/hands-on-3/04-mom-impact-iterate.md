# Langkah 4: Dampak MoM sebagai usulan dan iterasi

Durasi ±7 menit. Catatan meeting sering mengubah requirement. Claude boleh menemukan dampaknya, tetapi perubahan BRD tetap keputusan manusia. Hasilnya berupa usulan, bukan penulisan langsung.

## Yang dikerjakan

1. Kirim Prompt usulan dengan isi [`sprint-review-mom.md`](sources/sprint-review-mom.md). Claude membaca BRD lewat connector dan membandingkannya dengan MoM.
2. Periksa usulan: tiap butir menyebut ID requirement, bunyi BRD sekarang, bunyi usulan, dan alasan dari poin MoM. BRD tidak berubah.
3. Setujui atau tolak tiap butir dengan jelas. Perubahan yang kamu setujui diterapkan olehmu atau lewat permintaan terpisah.
4. Pilih satu temuan dari brief (Langkah 2 atau 3), kirim Prompt iterasi, jalankan lagi task sesuai permintaan, lalu isi scorecard v2.
5. Catat apakah dampak MoM terhadap backlog (story yang berubah atau Blocked) perlu masuk ke brief minggu depan.

## Prompt usulan

Ganti dulu: `[LINK BRD]` dan `[TEMPEL MOM]`.

```
CONTEXT
BRD WebTM: [LINK BRD]. MoM sprint review ada di bawah.

TASK
Bandingkan MoM dengan BRD. Daftar requirement yang terdampak sebagai USULAN perubahan. Jangan menulis atau mengubah apa pun di BRD, Notion, atau berkas lain.

RULES
- Tiap butir: ID requirement, bunyi BRD sekarang, bunyi usulan, poin MoM sebagai dasar, dan dampak ke backlog (Story ID).
- Hanya butir yang didukung langsung oleh poin MoM. Jangan menambah usulan dari dugaan.
- Bila MoM bertentangan dengan BRD tanpa penjelasan, tandai sebagai pertanyaan, bukan usulan.
- Akhiri dengan: "Usulan ini menunggu persetujuan manusia."

OUTPUT FORMAT
Tabel: ID requirement, bunyi sekarang, usulan, dasar MoM, dampak backlog. Lalu daftar pertanyaan.

[TEMPEL MOM]
```

## Prompt iterasi

```
Perbaiki satu hal di brief: [TEMUAN]. Ubah hanya bagian itu dan pertahankan format tiga bagian. Sebutkan baris yang berubah dan Story ID sumbernya.
```

## Cek

- BRD tidak berubah (cek riwayat versi Google Docs).
- Tiap usulan punya dasar poin MoM. Tidak ada usulan dari dugaan.
- Pertentangan tanpa penjelasan masuk pertanyaan.
- Cek mutu brief v2 lebih tinggi atau sama dengan v1 dan kamu bisa menunjuk penyebabnya.
- Scorecard v2 terisi.

---

Sebelumnya: [Langkah 3: Buat scheduled task dan jalankan](03-create-scheduled-task.md)
