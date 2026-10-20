# Langkah 3: Gambar di Miro

Durasi ±15 menit. Setelah kamu menyetujui flow spec, Claude menggambarnya di board lewat connector Miro. Gambar mengikuti spec, bukan sebaliknya.

## Yang dikerjakan

1. Di chat yang sama, periksa sekali lagi flow spec dari Langkah 2. Perbaiki lewat chat bila ada baris yang salah. Satu perubahan per pesan.
2. Tempel prompt di bawah dengan link board dari Quick Setup.
3. Claude meminta izin tool Miro. Pilih **Allow once** (tombol abu-abu) setiap kali. Tombol terang adalah Always allow, jangan dipilih. Kartu bisa muncul beberapa kali.
4. Buka board di Miro. Bandingkan gambar dengan flow spec baris per baris.

## Prompt

Ganti dulu: `[LINK BOARD]`.

```
Flow spec sudah benar. Gambar sebagai swimlane di board Miro ini, di frame baru: satu lane per aktor, bentuk keputusan untuk setiap Keputusan, dan label jelas di setiap cabang. Format portrait: alur dari atas ke bawah, lebar frame maksimal 1500 unit, ukuran font di kotak minimal 24, supaya terbaca saat diekspor ke BRD. Jangan mengubah isi flow spec dan jangan menyentuh isi board yang lain.

[LINK BOARD]
```

## Cek

- Semua baris flow spec muncul sebagai kotak, tidak ada yang hilang dan tidak ada kotak tambahan.
- Setiap Keputusan punya panah berlabel untuk tiap cabang.
- Ada satu titik mulai dan minimal satu titik akhir.
- Teks di kotak terbaca tanpa zoom berlebihan dan label cabang tidak menumpuk dengan panah atau kotak. Label cabang yang berupa kotak teks tidak ikut bergerak bila panah dipindah.
- Kalau Claude menggambar flowchart biasa tanpa lane, itu cukup. Minta lane sebagai target lanjutan.

Kalau gambar berantakan atau menumpuk, minta Claude menggambar ulang di frame baru. Jangan memperbaiki satu kotak demi satu kotak lewat chat.

---

Sebelumnya: [Langkah 2: Susun flow spec di chat](02-draft-flow-spec.md)  
Berikutnya: [Langkah 4: Cari skenario hilang dan perbaiki Skill](04-find-gaps-improve-skill.md)
