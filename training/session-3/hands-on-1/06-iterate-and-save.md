# Langkah 6: Iterasi dan simpan

Durasi ±15 menit. Hasil AI berbeda tiap kali, jadi iterasi itu normal. Kamu memperbaiki satu hal spesifik, lalu membuktikan bahwa angkanya naik.

## Yang dikerjakan

1. Ambil satu temuan dari Langkah 5 (mis. elemen tanpa dasar, validasi tidak jalan, atau state kosong hilang).
2. Kirim Prompt iterasi. Ganti `[TEMUAN]` dengan temuanmu, sebut nama elemen atau pemeriksaan yang gagal.
3. Muat ulang browser dan ulangi pemeriksaan yang terkait. Jangan menilai ulang semuanya dari ingatan: jalankan lagi enam pemeriksaannya.
4. Isi scorecard baris v2: Cek mutu, dikarang, kurang, dan apa yang kamu ubah.
5. Hasil tidak membaik? Kirim `/rewind` untuk kembali ke pesan sebelumnya (tab Code dan terminal sama). Di tab Code kamu juga bisa menolak perubahan di diff view, di terminal bisa `Esc` dua kali. Lalu coba feedback yang lebih sempit.
6. Simpan: pastikan `index.html`, `CLAUDE.md`, dan `NOTES.md` ada di folder. Bila proyek ini kamu tautkan ke BRD, tambahkan lokasi folder dan tanggal di bagian User Interface BRD.
7. Mulai sesi baru sebelum pindah ke hands-on berikutnya (tab Code: Cmd+N atau Ctrl+N, terminal: `/clear`), supaya konteks prototype tidak ikut.

## Prompt iterasi

```
Perbaiki satu hal saja di index.html: [TEMUAN]. Jangan mengubah bagian lain. Setelah selesai, sebutkan baris atau blok yang berubah dan pemeriksaan mana yang seharusnya sekarang lolos.
```

## Contoh temuan

- Elemen "Hapus Role" muncul di tabel tanpa dasar di BRD: hapus elemen itu.
- Role Name duplikat tidak ditolak untuk role yang berstatus Inactive: perbaiki sesuai RM-004.
- Tidak ada state kosong di Daftar Role: tambahkan.

## Cek

- Satu feedback, satu perubahan. Bagian lain tidak berubah.
- Cek mutu v2 lebih tinggi atau sama dengan v1 dan kamu bisa menunjuk penyebabnya.
- Elemen dikarang berkurang atau tetap nol.
- Folder berisi `index.html`, `CLAUDE.md`, dan `NOTES.md`.

---

Sebelumnya: [Langkah 5: Jalankan dan verifikasi](05-run-and-verify.md)  
Berikutnya: [Hands-on #2](../hands-on-2/README.md)
