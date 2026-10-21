# Langkah 3: Susun rencana di plan mode

Durasi ±15 menit. Di plan mode Claude hanya membaca dan menulis rencana. Berkas tidak berubah sampai kamu menyetujui. Rencana adalah titik di mana kamu menangkap salah paham, saat biayanya masih murah.

Penting: mode awal Claude Code bisa Auto, yaitu Claude langsung bekerja tanpa meminta persetujuan pada tiap aksi. Karena itu kamu pindah ke plan mode sendiri.

## Yang dikerjakan

1. Pindah ke plan mode: buka selector mode di samping tombol kirim dan pilih **Plan**, atau tekan Cmd+Shift+M (macOS) atau Ctrl+Shift+M (Windows).
2. Ganti model ke **Opus 5.5** lewat dropdown model di samping tombol kirim.
3. Kirim prompt di bawah. Claude membaca referensi, mungkin mengajukan pertanyaan, lalu menyajikan rencana.
4. Baca rencananya dengan daftar di bagian Cek. Driver membaca, reviewer mencentang.
5. Bila ada yang salah, jangan setujui. Balas dengan satu feedback, mis. "Hapus halaman login dari rencana, tidak ada di BRD." Ulangi sampai rencana benar.
6. Setujui rencana. Bila ditanya cara melanjutkan, pilih yang tetap meminta persetujuanmu untuk tiap perubahan (mode **Manual**). Claude menyimpan rencana sebagai `PLAN.md`.

## Prompt

```
CONTEXT
Baca CLAUDE.md, BRD, dan desain Claude Design di folder references. Tujuannya prototype HTML satu berkas untuk Role Management WebTM, dengan alur utama Create New Role.

TASK
Susun rencana implementasi dan simpan sebagai PLAN.md setelah aku setujui. Jangan mengubah berkas lain sebelum aku menyetujui.

RULES
- Screen wajib: Daftar Role (RM-001), Create New Role dengan Role Status dan Role Permission (RM-004, RM-005, RM-006), dan tampilan setelah Submit.
- Screen opsional, ditulis sebagai tahap terakhir: Role Members (RM-002), Edit Role (RM-007), Change Log Role (RM-003).
- Untuk tiap screen: elemen dengan ID requirement, dan sumber tampilannya (desain atau BRD).
- Tulis bagian "Selisih desain dan BRD": hal yang ada di desain tetapi tidak di BRD, atau sebaliknya.
- State yang dibuat: loading saat Submit, error Role Name kosong, error Role Name sama dengan role Active, error Role Name sama dengan role Inactive.
- Data contoh fiktif (tulis nilainya): minimal tiga role Active dan satu role Inactive.
- Hal yang BRD belum putuskan (pesan validasi, default Role Status, tampilan setelah simpan) masuk bagian Pertanyaan. Jangan memutuskannya sendiri.
- Tidak ada login, tidak ada hapus role, tidak ada fitur di luar BRD.
- Urutan pengerjaan sebagai tugas bernomor. Tiap tugas satu tahap yang bisa diperiksa di browser.
- Tulis cara memeriksa: langkah klik yang membuktikan alur berjalan.

OUTPUT FORMAT
Rencana berbagian: Screen, Elemen dan ID, Selisih desain dan BRD, State, Data contoh, Urutan, Pertanyaan, Cara memeriksa.
```

## Cek

- Setiap screen dan elemen punya ID requirement. Yang tidak punya ada di Pertanyaan atau Selisih.
- Tiga error Role Name disebut: kosong, sama dengan role Active, sama dengan role Inactive.
- Data contoh punya minimal satu role Inactive (dipakai untuk menguji aturan RM-004).
- Tidak ada login, hapus role, atau fitur lain di luar BRD.
- Cara memeriksa berisi langkah klik yang konkret.
- Belum ada berkas selain `PLAN.md` yang berubah.

---

Sebelumnya: [Langkah 2: Buat CLAUDE.md](02-create-claude-md.md)  
Berikutnya: [Langkah 4: Bangun alur utama](04-build-main-flow.md)
