# Langkah 4: Bangun alur utama

Durasi ±25 menit. Rencana sudah disetujui. Sekarang Claude membangun satu tahap setiap kali, dan kamu melihat hasilnya sebelum lanjut.

## Yang dikerjakan

1. Ganti model ke **Sonnet 5.5** (tab Code: dropdown model, terminal: `/model`). Pilih mode **Manual** (tab Code) atau mode yang meminta persetujuan atas perubahan berkas (terminal) supaya kamu melihat apa yang ditulis.
2. Kirim Prompt A. Claude membuat `index.html` dengan Daftar Role dan Create New Role.
3. Buka `index.html`: klik dua kali di file manager, atau di tab Code klik nama berkasnya di chat untuk membukanya di **Browser pane** (Cmd+Shift+B atau Ctrl+Shift+B membuka panelnya). Klik alurnya sekali sebelum lanjut.
4. Kirim Prompt B untuk validasi dan state. Muat ulang halamannya.
5. Bila waktu ada, kirim Prompt C untuk Role Members dan Change Log. Bila tidak, lewati.
6. Ke Langkah 5 untuk menilai hasilnya dengan Cek mutu.

## Prompt A: dua screen utama

```
CONTEXT
Rencana yang disetujui ada di PLAN.md (atau di percakapan ini). Ikuti CLAUDE.md.

TASK
Buat index.html satu berkas (HTML, CSS, dan JavaScript di dalamnya, tanpa framework dan tanpa server). Bangun dua screen dan navigasi di antaranya: Daftar Role dan Create New Role. Setelah Simpan, kembali ke Daftar Role dan role baru muncul di tabel.

RULES
- Hanya elemen yang ada di rencana. Beri komentar HTML dengan ID requirement di tiap blok (mis. <!-- RM-004 -->).
- Gunakan data contoh dari rencana (fiktif). Role ID dibuat otomatis oleh skrip dan tidak bisa diedit.
- Hal yang belum diputuskan BRD ditulis "TBC" di layar dan dicatat di NOTES.md.
- Jangan menambah fitur atau halaman lain.

OUTPUT FORMAT
Tulis index.html. Setelah itu jelaskan dalam tiga kalimat apa yang dibuat dan cara membukanya.
```

## Prompt B: validasi dan state

```
Tambahkan ke index.html: (1) Role Name kosong menampilkan pesan di bawah field dan Simpan tidak berjalan, (2) Role Name yang sudah ada di tabel (Active maupun Inactive) menampilkan pesan nama sudah dipakai, isi pesannya "TBC" sesuai BRD, (3) state kosong di Daftar Role saat tabel tidak berisi role, (4) state loading singkat saat Simpan (tampilkan indikator sekitar satu detik). Jangan mengubah hal lain. Tambahkan komentar ID requirement di blok yang baru.
```

## Prompt C: tahap opsional

```
Tambahkan screen Role Members (dibuka dari angka Total User di Daftar Role, berisi nama dan email fiktif, dan state kosong bila Total User 0) dan Change Log Role (dibuka dari tautan Log, daftar log fiktif, filter tanggal dengan rentang maksimal 3 bulan). Format baris log ditulis TBC bila BRD belum menentukan. Jangan mengubah dua screen yang sudah ada.
```

## Cek

- `index.html` tersimpan di folder proyek dan terbuka di browser.
- Tombol Create New Role membuka form, Simpan mengembalikan ke tabel dengan role baru.
- Komentar ID requirement ada di blok-blok utama.
- `NOTES.md` berisi hal yang ditandai TBC.

---

Sebelumnya: [Langkah 3: Susun rencana di plan mode](03-plan-mode.md)  
Berikutnya: [Langkah 5: Jalankan dan verifikasi](05-run-and-verify.md)
