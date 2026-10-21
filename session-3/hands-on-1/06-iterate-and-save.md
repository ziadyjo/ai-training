# Langkah 6: Iterasi dan simpan

Durasi ±15 menit. Hasil AI berbeda tiap kali, jadi iterasi itu normal. Kamu memperbaiki satu hal spesifik, lalu membuktikan bahwa angkanya naik.

## Yang dikerjakan

1. Ambil satu temuan dari Langkah 5 (mis. elemen tanpa dasar, validasi tidak jalan, atau state loading hilang).
2. Kirim Prompt iterasi. Ganti `[TEMUAN]` dengan temuanmu, sebut nama elemen atau pemeriksaan yang gagal.
3. Baca perubahan di diff view, pilih **Accept**, lalu muat ulang Browser pane.
4. Jalankan lagi enam pemeriksaan, jangan menilai dari ingatan. Isi scorecard baris v2: Cek mutu, dikarang, kurang, dan apa yang kamu ubah.
5. Hasil tidak membaik? Kirim `/rewind` untuk kembali ke pesan sebelumnya, atau tolak perubahan di diff view. Lalu coba feedback yang lebih sempit.
6. Simpan: pastikan `index.html`, `CLAUDE.md`, `PLAN.md`, dan `NOTES.md` ada di folder `webtm-prototype`. Folder ini dipakai lagi di Sesi 4, jangan dipindah.
7. Mulai sesi baru (Cmd+N atau Ctrl+N) sebelum pindah ke Hands-on #2, supaya konteks prototype tidak ikut.

## Prompt iterasi

```
CONTEXT
Ikuti CLAUDE.md dan PLAN.md. Temuan dari Cek mutu prototype: [TEMUAN].

TASK
Perbaiki satu hal saja di index.html sesuai temuan itu.

RULES
- Jangan mengubah bagian lain.

OUTPUT FORMAT
Sebutkan blok yang berubah dan pemeriksaan Cek mutu mana yang seharusnya sekarang lolos.
```

## Contoh temuan

- Role Name yang sama dengan role Inactive tetap diterima: perbaiki sesuai RM-004 (Active maupun Inactive).
- Logo atau nama orang dari desain ikut tampil: ganti dengan teks netral.
- Tidak ada state loading saat Submit: tambahkan.
- Elemen "Hapus Role" muncul tanpa dasar di BRD: hapus elemen itu.

## Cek

- Satu feedback, satu perubahan. Bagian lain tidak berubah.
- Cek mutu v2 lebih tinggi atau sama dengan v1 dan kamu bisa menunjuk penyebabnya.
- Elemen dikarang berkurang atau tetap nol.
- Folder berisi `index.html`, `CLAUDE.md`, `PLAN.md`, dan `NOTES.md`.

---

Sebelumnya: [Langkah 5: Jalankan dan verifikasi](05-run-and-verify.md)  
Berikutnya: [Hands-on #2](../hands-on-2/README.md)
