# Langkah 3: Susun rencana di plan mode

Durasi ±15 menit. Di plan mode Claude hanya membaca dan menulis rencana. Berkas tidak berubah sampai kamu menyetujui. Rencana adalah titik di mana kamu menangkap salah paham, saat biayanya masih murah.

Penting: di versi terbaru Claude Code, mode awal bisa Auto, yaitu Claude langsung bekerja tanpa meminta persetujuan pada tiap aksi. Karena itu kamu pindah ke plan mode sendiri.

## Yang dikerjakan

1. Pindah ke plan mode. **Tab Code:** buka selector mode di samping tombol kirim dan pilih **Plan**, atau tekan Cmd+Shift+M (macOS) atau Ctrl+Shift+M (Windows). Shift+Tab tidak berpindah mode di tab Code. **Terminal:** tekan **Shift+Tab** sampai tulisan mode di bawah kotak input menunjukkan plan, atau ketik `/plan`, atau jalankan `claude --permission-mode plan`.
2. Ganti model ke **Opus 5.5** untuk rencana: tab Code lewat dropdown model di samping tombol kirim, terminal lewat `/model`.
3. Kirim prompt di bawah. Claude membaca referensi, mungkin mengajukan pertanyaan, lalu menyajikan rencana.
4. Baca rencananya. Pakai daftar di bagian Cek. Di terminal, Ctrl+G membuka rencana di editor teks.
5. Bila ada yang salah, pilih **lanjut merencanakan** dan beri feedback satu per satu. Jangan menyetujui rencana yang berisi fitur di luar BRD.
6. Setujui dengan pilihan yang meminta persetujuan manual atas perubahan berkas (di tab Code: kembali ke mode **Manual**, supaya tiap perubahan muncul di diff view dengan tombol Accept dan Reject). Minta Claude menyimpan rencana sebagai `PLAN.md`.

## Prompt

```
CONTEXT
Baca CLAUDE.md dan semua berkas di folder references. Tujuannya prototype HTML satu berkas untuk alur Create New Role di WebTM.

TASK
Susun rencana implementasi. Jangan mengubah berkas apa pun sebelum aku menyetujui.

RULES
- Rencana mencakup: daftar screen yang dibuat (Daftar Role, Create New Role, tampilan setelah simpan), elemen tiap screen dengan ID requirement-nya, state yang dibuat (normal, kosong, loading, error nama duplikat), data contoh yang dipakai (tulis nilainya, ini data fiktif), dan urutan pengerjaan sebagai daftar tugas bernomor (tiap tugas satu tahap yang bisa diperiksa di browser).
- Screen Role Members dan Change Log hanya dibuat bila sisa waktu ada. Tulis sebagai tahap terakhir yang opsional.
- Hal yang BRD belum putuskan (mis. isi pesan nama duplikat, tampilan setelah simpan) masuk ke bagian Pertanyaan. Jangan memutuskannya sendiri.
- Tidak ada login, tidak ada hapus role, tidak ada fitur di luar BRD.
- Tulis cara memeriksa hasil: langkah klik yang membuktikan alur berjalan.

OUTPUT FORMAT
Rencana berbagian: Screen, Elemen dan ID, State, Data contoh, Urutan, Pertanyaan, Cara memeriksa.
```

## Cek

- Setiap screen dan elemen punya ID requirement. Yang tidak punya ada di Pertanyaan.
- State kosong, loading, dan error nama duplikat disebut.
- Tidak ada login, hapus role, atau fitur lain di luar BRD.
- Bagian Cara memeriksa berisi langkah klik yang konkret.
- Urutan berupa tugas bernomor, bukan satu paragraf.
- Berkas belum ada yang berubah sebelum kamu menyetujui.

---

Sebelumnya: [Langkah 2: Buat CLAUDE.md](02-create-claude-md.md)  
Berikutnya: [Langkah 4: Bangun alur utama](04-build-main-flow.md)
