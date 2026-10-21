# Langkah 3: Buat scheduled task dan jalankan

Durasi ±9 menit. Scheduled task adalah prompt yang dijalankan Claude sesuai jadwal atau sesuai permintaan. Kamu menjadikan prompt brief dari Langkah 2 sebagai task harian, lalu menjalankannya sekali tanpa menunggu jadwal.

Task tidak dipicu oleh MoM baru. Task berjalan per jadwal (di sini setiap hari kerja), dan setiap kali jalan ia membaca MoM bertanggal hari ini atau kemarin. Karena hanya memakai connector, task tetap berjalan walau komputermu mati.

## Yang dikerjakan

1. Buka **Scheduled** di sidebar aplikasi Claude desktop, klik **New task**. Bila muncul pilihan, pilih mengisi manual.
2. Isi:
   - Nama: `Brief Progres WebTM`
   - Prompt: blok di bawah (ganti `[LINK BRD]` dulu)
   - Frekuensi: **Weekdays**, jam 17.00
   - Model: **Sonnet 5.5**
   - Mode persetujuan: pilih yang meminta persetujuan (task ini hanya membaca)
3. Simpan, lalu klik **Run now**.
4. Run pertama biasanya berhenti menunggu izin untuk tool Notion dan Google Docs. Buka sesi run dari halaman task. Untuk tool **baca** (search, fetch), pilih izin tetap (always allow). Tool yang menulis atau membuat apa pun: tolak.
5. Tunggu sampai selesai, lalu buka hasil run dari halaman task. Bandingkan dengan brief Langkah 2: format sama, angka sama, Catatan MoM "tidak ada MoM baru".

## Prompt task

Ganti dulu: `[LINK BRD]`.

```
CONTEXT
Sumber: database "WebTM Backlog" dan "WebTM MoM" di halaman "WebTM" di Notion, dan BRD WebTM v1.1: [LINK BRD].

TASK
Tulis brief progres proyek WebTM dengan empat bagian tetap.

RULES
- Hanya baca: jangan membuat, mengubah, atau menghapus apa pun di Notion, Google Docs, atau tempat lain.
- PROGRES: jumlah story per Status (Done, In Progress, Blocked, Backlog) dengan Story ID untuk tiap angka.
- PRIORITAS MINGGU INI: maksimal tiga story, masing-masing dengan alasan satu kalimat.
- HAMBATAN: alasan, sumber (Story ID, ID requirement, atau MoM), dan tindakan yang diminta dari peran apa.
- CATATAN MOM: hanya halaman di WebTM MoM dengan Tanggal meeting hari ini atau kemarin. Untuk tiap poin yang berdampak: ID requirement dan Story ID terdampak, dan usulan perubahan BRD bila poin itu mengisi TBC atau menambah aturan. Poin yang bertentangan dengan BRD, atau keputusan yang masih sementara atau terbuka, ditulis sebagai pertanyaan, bukan usulan. Tanpa MoM baru tulis "tidak ada MoM baru".
- Yang tidak ada di data ditulis "tidak ada data". Jangan menebak tanggal, nama orang, atau persentase.
- Maksimal 300 kata, bahasa Indonesia. Awali dengan tanggal data diambil.

OUTPUT FORMAT
Brief dengan empat judul bagian. Akhiri dengan "Usulan menunggu persetujuan." 
```

## Cek

- Task muncul di daftar **Scheduled** dengan nama, frekuensi, dan model yang benar.
- Run sesuai permintaan selesai tanpa galat.
- Brief hasil run punya empat bagian, angka cocok dengan Notion, dan Catatan MoM "tidak ada MoM baru".
- Tidak ada yang berubah di Notion atau BRD.

---

Sebelumnya: [Langkah 2: Tentukan format dan brief pertama](02-define-format-first-brief.md)  
Berikutnya: [Langkah 4: MoM baru masuk, jalankan ulang, putuskan usulan](04-mom-impact-iterate.md)
