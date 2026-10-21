# Langkah 2: Draf backlog dan Cek mutu

Durasi ±8 menit. Backlog dibuat sebagai tabel di chat lebih dulu. Kamu memeriksanya, baru di Langkah 3 hasilnya dikirim ke Notion. Notion adalah tempat menyimpan, bukan tempat mengecek.

## Yang dikerjakan

1. Kirim Prompt di bawah. Claude mengubah story dari Langkah 1 menjadi tabel sesuai [skema backlog](sources/backlog-schema.md).
2. Reviewer memeriksa tabel dengan **Cek mutu backlog** (6 pemeriksaan di [README](README.md#cek-mutu-backlog)).
3. Driver mencatat di [scorecard](../scorecard.md) baris v1: Cek mutu, story dikarang, hal yang kurang.
4. Jangan memperbaiki dulu. Pilih satu temuan paling penting untuk Langkah 4.

## Prompt

```
CONTEXT
User story dari langkah sebelumnya di chat ini. Skema backlog: Story ID, Title, User Story, Acceptance Criteria, Requirement ID, Priority, Size, Dependency, Status, Sprint.

TASK
Ubah user story tadi menjadi tabel backlog di chat, lalu nilai tabelnya dengan Cek mutu backlog. Jangan menulis ke Notion.

RULES
- Kolom: Story ID, Title, User Story, Acceptance Criteria, Requirement ID, Priority (Must, Should, Could), Size (S, M, L), Dependency (ID story lain atau "tidak ada"), Status (semua "Backlog"), Sprint (kosong).
- Di bawah tabel, nilai tiap dari 6 pemeriksaan Cek mutu backlog: lolos atau tidak, dengan alasan satu kalimat.

OUTPUT FORMAT
Tabel backlog, lalu tabel Cek mutu dengan jumlah N dari 6.
```

## Cek

- Semua kolom skema ada dan terisi.
- Priority dan Size punya alasan yang masuk akal (story Must adalah yang menjadi inti alur Create New Role).
- Dependency menunjuk ID story yang ada, atau "tidak ada".
- Cek mutu dari Claude kamu bandingkan dengan pemeriksaanmu sendiri: tidak boleh memberi lolos pada hal yang jelas kurang.
- Scorecard v1 terisi.

---

Sebelumnya: [Langkah 1: Hubungkan Notion dan buat user story](01-connect-notion-user-stories.md)  
Berikutnya: [Langkah 3: Kirim ke Notion](03-send-to-notion.md)
