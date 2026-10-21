# Langkah 4: MoM baru masuk, jalankan ulang, putuskan usulan

Durasi ±8 menit. Ini demo case-nya: meeting review BRD v1.1 baru selesai dan MoM-nya masuk ke Notion. Task yang sama dijalankan ulang dan menangkap keputusan meeting serta dampaknya terhadap backlog dan BRD. Claude boleh menemukan dampaknya, tetapi perubahan BRD tetap keputusan manusia.

## Yang dikerjakan

1. Buka Notion, database **WebTM MoM**, halaman **MoM Review BRD WebTM Role Management v1.1**. Isi **Tanggal meeting** dengan tanggal hari ini. Sekarang MoM ini terhitung MoM baru.
2. Buka task `Brief Progres WebTM` di **Scheduled**, klik **Run now**.
3. Baca bagian Catatan MoM di hasil run bersama reviewer:
   - MoM Kickoff dan Sprint Planning tidak muncul (lebih lama dari kemarin).
   - Keputusan yang mengisi TBC jadi usulan dengan ID requirement dan Story ID: default Role Status Active dan field mandatory (RM-004), default permission None (RM-005), Admin View Only di Role Management (8.2), permission berlaku saat login berikutnya (RM-007).
   - Keputusan sementara atau terbuka jadi pertanyaan, bukan usulan: format Role ID "ROL-" (menunggu Backend), pesan validasi (menunggu PO), entrypoint Change Log lewat Role Details (perlu konfirmasi PO, Role Details tidak ada di BRD).
   - Action item yang menghambat story masuk Hambatan, mis. mapping Change Log (S-08 tetap Blocked).
4. Putuskan tiap usulan: tulis "setuju" atau "tolak" dengan alasan satu kalimat di catatanmu. Task tidak mengubah BRD. Usulan yang kamu setujui diterapkan olehmu sendiri, di luar hands-on ini.
5. Iterasi: ambil satu temuan dari Cek mutu (Langkah 2 atau run ini). Buka task, klik **Edit**, tambahkan satu kalimat aturan ke prompt, simpan, lalu **Run now** lagi.
6. Isi Cek mutu brief di scorecard baris v2.

## Contoh aturan iterasi (tambahkan ke prompt task)

- "Untuk tiap usulan, tulis juga bunyi BRD sekarang dan bunyi usulan."
- "Keputusan berstatus sementara atau terbuka ditulis sebagai pertanyaan, bukan usulan."
- "Diskusi improvement BRD yang masih berstatus Diskusi tidak dijadikan usulan."
- "Batasi Catatan MoM maksimal tujuh butir, urut dari yang berdampak ke story Must."

## Cek

- Run kedua memuat Catatan MoM dari MoM Review BRD saja.
- Format Role ID dan pesan validasi ditulis sebagai pertanyaan, bukan usulan.
- Tiap usulan punya dasar keputusan atau hasil pembahasan di MoM. Tidak ada usulan dari dugaan.
- BRD dan Notion tidak berubah oleh task (cek Version history Google Docs bila ragu).
- Satu aturan, satu perubahan di prompt task. Cek mutu brief v2 lebih tinggi atau sama dengan v1 dan kamu bisa menunjuk penyebabnya.

---

Sebelumnya: [Langkah 3: Buat scheduled task dan jalankan](03-create-scheduled-task.md)  
Selesai. Isi [scorecard](../scorecard.md) dan cek Kriteria lulus di [README](README.md).
