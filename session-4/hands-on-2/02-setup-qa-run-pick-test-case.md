# Langkah 2: Pasang qa-run dan pilih test case

Durasi ±10 menit. `qa-run` sudah jadi, jadi kamu menyalinnya, bukan membangunnya. Skill ini mengatur cara eksekusi dan menyusun catatan hasil. Ia tidak menyusun test case baru dan tidak menulis ke BRD.

## Yang dikerjakan

1. Buka **Customize** di sidebar aplikasi Claude, tab **Skills**, klik **+ Add**, pilih **Create a skill**.
2. Isi **Skill name** dengan `qa-run`. Isi **Description** dengan teks di bagian "Description" di bawah.
3. Buka [`sources/qa-run/SKILL.md`](sources/qa-run/SKILL.md). Salin semua isi mulai dari `# QA Run` ke editor instruksi, lalu klik **Create**.
4. Dari test case terpilih di Hands-on #1, ambil satu yang paling sederhana dan berprioritas Tinggi (mis. TC-001, membuat role baru dengan data valid). Salin barisnya lengkap: prakondisi, langkah, expected. Siapkan juga satu test case negatif (mis. Role Name sama dengan role Inactive) untuk Langkah 5.
5. Cek apakah Skill terbaca di side panel Chrome. Kirim prompt di bawah ke side panel. Bila Claude tidak mengenal `qa-run`, tempel isi [`sources/execution-rules-paste.md`](sources/execution-rules-paste.md) di awal prompt eksekusi pada Langkah 3.

Tertinggal? Minta test case acuan ke instruktur.

## Description

```
Dipakai saat test case sudah ada dan analis akan menjalankannya di prototype, lewat Claude in Chrome atau dengan catatan manual, lalu perlu hasilnya dicatat. Mengatur cara eksekusi (satu test case per giliran, batas aksi, bukti per langkah), membandingkan expected dan actual, dan menyusun execution record, defect record, Cek mutu, serta QA Report. Tidak dipakai untuk menyusun test case baru.
```

## Prompt cek Skill (kirim ke side panel)

```
CONTEXT
Tab aktif adalah prototype WebTM. Skill qa-run terpasang di akunku.

TASK
Katakan apakah kamu bisa membaca Skill qa-run. Bila bisa, ringkas tiga aturannya.

RULES
- Satu kalimat per aturan. Bila tidak bisa, katakan tidak bisa.
- Jangan melakukan apa pun di halaman.

OUTPUT FORMAT
Jawaban "bisa" atau "tidak bisa", diikuti tiga aturan bila bisa.
```

## Cek

- `qa-run` muncul di daftar Skills dan aktif.
- Kamu tahu apakah side panel membaca Skill atau kamu perlu menempel aturan.
- Satu test case terpilih, lengkap dengan prakondisi dan expected.
- Prakondisi test case terpenuhi di prototype (mis. nama yang akan dipakai belum ada).

---

Sebelumnya: [Langkah 1: Siapkan Claude in Chrome, izin, dan prototype](01-setup-claude-in-chrome.md)  
Berikutnya: [Langkah 3: Jalankan test case pertama](03-run-first-test-case.md)
