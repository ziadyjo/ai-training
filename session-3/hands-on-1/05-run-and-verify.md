# Langkah 5: Jalankan dan verifikasi

Durasi ±15 menit. Kamu tidak menilai prototype dari tampilannya, tetapi dari enam pemeriksaan tetap. Driver mengklik, reviewer membaca daftarnya dan mencatat.

## Yang dikerjakan

1. Buka `index.html` di browser biasa (Chrome, Edge, atau Safari). Buka console (F12, tab Console) dan biarkan terbuka.
2. Jalankan langkah klik: Daftar Role, Create New Role, isi nama baru, Simpan, lihat role baru di tabel.
3. Coba jalur gagal: Simpan dengan Role Name kosong, lalu dengan nama yang sudah ada.
4. Baca daftar komentar ID requirement di kode (minta Claude membuat daftarnya bila perlu dengan Prompt di bawah).
5. Isi **Cek mutu prototype** (6 pemeriksaan di [README](README.md#cek-mutu-prototype)) di [scorecard](../scorecard.md) baris v1, lengkap dengan jumlah elemen dikarang dan hal yang kurang.
6. Pilih satu temuan paling penting untuk Langkah 6.

Di tab Code, Browser pane juga bisa membuka berkas HTML statis, tetapi pemeriksaan console tetap dilakukan di browser biasa.

## Prompt

```
Baca index.html. Buat tabel dengan kolom: elemen, ID requirement di komentar, dan statusnya (ada dasar di BRD, ada di mockup, atau tidak ada dasar). Tandai elemen tanpa dasar. Jangan mengubah berkas.
```

## Cek

- Alur utama berjalan dari awal sampai tabel menampilkan role baru.
- Kedua jalur gagal menampilkan pesan.
- Console tidak menampilkan galat merah.
- Elemen tanpa dasar teridentifikasi dari tabel Claude, bukan dari tebakanmu.
- Scorecard v1 terisi.
- Opsional, bila waktu cukup: bandingkan perilaku permission dan konfirmasi Submit dengan RM-004 dan RM-008 di [Reference BRD Role Management](../../session-2/reference-brd-role-management.md). Selisih dicatat sebagai temuan, bukan kewajiban prototype.

---

Sebelumnya: [Langkah 4: Bangun alur utama](04-build-main-flow.md)  
Berikutnya: [Langkah 6: Iterasi dan simpan](06-iterate-and-save.md)
