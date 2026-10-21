# Langkah 4: Review dependency dan iterasi

Durasi ±5 menit. Dependency yang salah membuat sprint salah urut. Kamu minta Claude memeriksa urutan, lalu memperbaiki satu temuan dan membuktikan angkanya naik.

## Yang dikerjakan

1. Kirim Prompt review. Claude membaca backlog dari Notion dan mencari story yang bergantung pada story lain tetapi tidak menuliskannya, atau urutan prioritas yang tidak masuk akal.
2. Pilih satu temuan. Kirim Prompt iterasi dengan temuan itu.
3. Buka Notion dan pastikan hanya baris yang dimaksud yang berubah.
4. Jalankan lagi **Cek mutu backlog**, catat di [scorecard](../scorecard.md) baris v2.
5. Simpan: backlog sudah di Notion. Tambahkan tautan Notion di bagian lampiran BRD bila kamu memakainya.

## Prompt review

```
CONTEXT
Database "WebTM Backlog" di Notion berisi backlog yang baru dikirim.

TASK
Periksa dependency di database itu. Jangan mengubah apa pun.

RULES
- Sebutkan story yang membutuhkan story lain tetapi kolom Dependency-nya "tidak ada".
- Sebutkan story Must yang bergantung pada story Could.

OUTPUT FORMAT
Tabel: Story ID, masalah, saran perbaikan.
```

## Prompt iterasi

Ganti dulu: `[TEMUAN]`.

```
CONTEXT
Database "WebTM Backlog" di Notion. Temuan dari review dependency: [TEMUAN].

TASK
Perbaiki satu hal di database itu sesuai temuan.

RULES
- Ubah hanya baris yang disebut.

OUTPUT FORMAT
Baris yang berubah, dengan nilai sebelum dan sesudah.
```

## Cek

- Satu feedback, satu perubahan. Baris lain tidak berubah.
- Dependency yang diperbaiki menunjuk ID story yang ada.
- Cek mutu v2 lebih tinggi atau sama dengan v1 dan kamu bisa menunjuk penyebabnya.
- Scorecard v2 terisi.

---

Sebelumnya: [Langkah 3: Kirim ke Notion](03-send-to-notion.md)  
Berikutnya: [Hands-on #3](../hands-on-3/README.md)
