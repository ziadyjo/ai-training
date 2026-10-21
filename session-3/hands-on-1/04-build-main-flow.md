# Langkah 4: Bangun alur utama

Durasi ±25 menit. Rencana sudah disetujui. Sekarang Claude membangun satu tahap setiap kali, dan kamu melihat hasilnya di browser sebelum lanjut.

## Yang dikerjakan

1. Ganti model ke **Sonnet 5.5** (dropdown model). Pastikan mode **Manual**, supaya tiap perubahan muncul di diff view dengan pilihan Accept atau Reject.
2. Kirim Prompt A. Claude membuat `index.html` berisi Daftar Role dan Create New Role. Pilih **Accept** setelah membaca ringkasan perubahannya.
3. Buka `index.html` di **Browser pane**: klik nama berkasnya di percakapan, atau tekan Cmd+Shift+B (macOS) atau Ctrl+Shift+B (Windows). Klik alurnya sekali: Create New Role, isi nama, Submit.
4. Kirim Prompt B untuk validasi dan state. Muat ulang Browser pane, lalu coba nama kosong dan nama "Staff".
5. Kirim Prompt C untuk Role Permission.
6. Bila waktu ada, kirim Prompt D (opsional). Bila tidak, lewati.

## Prompt A: Daftar Role dan Create New Role

```
CONTEXT
Ikuti CLAUDE.md dan PLAN.md. Tampilan mengikuti desain Claude Design di references (warna, sidebar, tabel, tombol). Perilaku mengikuti BRD.

TASK
Kerjakan tugas 1 dan 2 di PLAN.md: buat index.html satu berkas dengan sidebar (Access Control > Roles), Daftar Role, dan Create New Role (Role ID, Role Name, Role Status). Setelah Submit, kembali ke Daftar Role dan role baru muncul di tabel.

RULES
- Hanya elemen yang ada di PLAN.md. Komentar HTML dengan ID requirement di tiap blok (mis. <!-- RM-004 -->).
- Data contoh fiktif dari PLAN.md. Role ID dibuat otomatis oleh skrip dan tidak bisa diedit.
- Setiap tombol dan field punya teks label yang terlihat dan atribut id.
- Hal yang belum diputuskan BRD ditulis "TBC" di layar dan dicatat di NOTES.md.
- Jangan menyalin kode ekspor Claude Design. Jangan menambah fitur atau halaman lain.

OUTPUT FORMAT
Tulis index.html dan NOTES.md. Setelah itu jelaskan dalam tiga kalimat apa yang dibuat dan cara membukanya.
```

## Prompt B: validasi dan state

```
CONTEXT
Ikuti CLAUDE.md dan PLAN.md. index.html sudah berisi Daftar Role dan Create New Role.

TASK
Kerjakan tugas validasi dan state di PLAN.md.

RULES
- Role Name kosong: pesan tampil di bawah field dan Submit tidak menyimpan.
- Role Name sama dengan role yang sudah ada, baik Active maupun Inactive (RM-004): pesan tampil, isi pesannya "[Pesan validasi: TBC]".
- State loading sekitar satu detik setelah Submit.
- Jangan mengubah hal lain.
- Tambahkan komentar ID requirement di blok baru dan perbarui NOTES.md bila ada hal TBC baru.

OUTPUT FORMAT
Perbarui index.html dan NOTES.md. Jelaskan dalam tiga kalimat apa yang berubah.
```

## Prompt C: Role Permission

```
CONTEXT
Ikuti CLAUDE.md dan PLAN.md. Daftar Role, Create New Role, dan validasi sudah ada.

TASK
Kerjakan tugas Role Permission di PLAN.md (RM-005).

RULES
- Daftar menu dan submenu dari Appendix 8.1 BRD, termasuk Access Control dengan submenu Master Menu, Roles, Users.
- Tiap menu dan submenu punya dropdown None, View Only, All Access.
- Default value ditulis TBC sesuai BRD.
- Tambahkan tombol untuk membuka dan menutup semua submenu bila ada di desain.
- Jangan mengubah hal lain.

OUTPUT FORMAT
Perbarui index.html. Jelaskan dalam tiga kalimat apa yang berubah.
```

## Prompt D: tahap opsional

```
CONTEXT
Ikuti CLAUDE.md dan PLAN.md. Semua tahap wajib sudah selesai.

TASK
Kerjakan tahap opsional di PLAN.md: Role Members, Edit Role, dan Change Log Role.

RULES
- Role Members: dibuka dari angka Total User, berisi nama dan email fiktif, dengan state kosong bila role tanpa user.
- Edit Role: Role Name, Role Permission, dan Role Status bisa diubah, Role ID tidak.
- Change Log Role: dibuka dari tombol Change Log di Edit Role (entrypoint ditulis TBC). Tiap perubahan di Edit Role menambah satu baris dengan format log RM-003.
- Jangan mengubah screen yang sudah ada.

OUTPUT FORMAT
Perbarui index.html. Jelaskan dalam tiga kalimat apa yang berubah.
```

## Cek

- `index.html` tersimpan di folder proyek dan terbuka di Browser pane.
- Create New Role membuka form, Submit mengembalikan ke tabel dengan role baru.
- Pesan muncul untuk nama kosong dan nama "Staff".
- Role Permission menampilkan menu dan submenu dengan tiga pilihan level akses.
- `NOTES.md` berisi hal yang ditandai TBC.

---

Sebelumnya: [Langkah 3: Susun rencana di plan mode](03-plan-mode.md)  
Berikutnya: [Langkah 5: Jalankan dan verifikasi](05-run-and-verify.md)
