# Claude Design (Langkah 3 sampai 5)

Claude Design adalah jalur kedua Hands-on #2. Hasil akhirnya sama dengan jalur Stitch: 3 sampai 4 screen, dua layout dibandingkan, satu feedback, dan tautan di BRD. Bedanya, semua dikerjakan di aplikasi Claude. Tidak perlu API key, Claude Code, atau MCP.

Kapan memakainya:
- Kamu memilih jalur ini dari awal, misalnya karena sudah punya design system di akunmu.
- Koneksi Stitch tidak jadi dalam 10 menit, atau muncul galat 401, 403, `RATE_LIMITED`, atau dynamic client registration (lihat [README](README.md)).

Langkah 1 dan 2 (pasang `ui-brief`, jalankan `ui-brief`) sama untuk kedua jalur. Setelah brief selesai, ikuti langkah di bawah sebagai pengganti Langkah 3 sampai 5. Tampilan menu bisa berbeda per akun, jadi ikuti tombol yang tampil di layarmu.

| Langkah | Pengganti | Menit |
|---|---|---|
| C1 | Langkah 3: siapkan Claude Design | ±5 |
| C2 | Langkah 4: buat screen, bandingkan layout, beri feedback | ±30 |
| C3 | Langkah 5: simpan dan tautkan ke BRD | ±10 |

## C1. Siapkan Claude Design (±5 menit)

1. Di sidebar aplikasi Claude buka **Artifacts**, lalu pilih **Design** untuk membuat desain baru. Beri nama `WebTM Role Management`.
2. Referensi gaya (pilih salah satu):
   - Punya design system: buka **Settings > Design systems**, pastikan design system-mu ada, lalu pilih saat membuat desain.
   - Tidak punya: tulis gaya sebagai "ikuti gaya produk yang sudah ada" di prompt, seperti di brief. Hasilnya memakai gaya bawaan Claude Design.
3. Kembali ke chat Langkah 2 (tempat `ui-brief` berjalan) dan kirim Prompt A di [Langkah 4](04-generate-compare-screens.md) untuk mendapat prompt desain final. Salin blok prompt itu.

## C2. Buat screen, bandingkan layout, beri feedback (±30 menit)

Semua prompt di sini dikirim di kanvas atau chat Claude Design, kecuali Prompt D.

**Buat screen.** Tempel prompt desain dari Prompt A:

```
Buat 4 screen dari prompt desain di bawah, satu per satu: Halaman Daftar Role, Role Members, Change Log Role, dan Create New Role (satu halaman). Jangan menambah screen, menu navigasi, kolom, atau data contoh di luar daftar. Bagian bertanda placeholder tampilkan sebagai teks netral.

[TEMPEL PROMPT DESAIN]
```

Tunggu semua screen selesai, lalu hitung. Kalau kurang atau ada ganda, minta hanya yang kurang:

```
Sebutkan screen yang sudah ada di desain ini. Tandai yang ganda. Buat hanya screen dari daftar yang belum ada, dan jangan mengubah screen yang sudah ada.
```

**Cek terhadap brief.** Bandingkan tiap screen dengan tabel brief dari Langkah 2. Elemen yang tidak ada di brief (menu tambahan, kolom, data contoh) dihitung sebagai elemen dikarang, sama seperti di jalur Stitch.

**Dua layout.** Pilih screen Create New Role, lalu kirim:

```
Buat dua variasi layout untuk screen Create New Role. Variasi A: form satu kolom, Role Permission di bagian bawah. Variasi B: form dua kolom, Role Permission di panel kanan. Isi field dan aksi sama persis di keduanya. Jangan mengubah screen lain dan jangan menambah field atau fitur.
```

Nilai kedua variasi dengan tabel Kriteria di [Langkah 4](04-generate-compare-screens.md), tulis satu kalimat alasan per kriteria, lalu pilih satu.

**Periksa terhadap brief.** Ambil screenshot layout terpilih, unggah ke chat Claude (bukan kanvas), lalu kirim Prompt D dari Langkah 4.

**Satu feedback.** Di kanvas atau lewat komentar di screen terpilih:

```
Pada layout yang kupilih: [PERUBAHAN]. Ubah screen itu saja. Jangan mengubah screen lain.
```

Contoh: "hapus elemen yang tidak ada di brief" atau "tambahkan state error di bawah field Role Name dengan teks 'Role Name sudah dipakai'". Catat scorecard UI baris v1 (screen pertama) dan v2 (setelah feedback).

## C3. Simpan dan tautkan ke BRD (±10 menit)

1. Buka menu ekspor di desain dan lihat opsi di akunmu. Claude Design bisa mengekspor, misalnya, PDF atau HTML. Simpan semua screen dalam satu format. Kalau opsi tidak ada, ambil screenshot tiap screen.
2. Namai berkas dengan nama screen dan ID requirement, misalnya `create-new-role-RM-004.png`.
3. Di BRD bagian 7, isi kolom **User Interface** untuk Create New Role dengan link desain Claude Design (atau nama berkas bila link tidak bisa dibagikan), sebagai hyperlink. Tempel satu gambar screen utama dengan satu kalimat keterangan.
4. Simpan tabel brief dari Langkah 2 untuk Sesi 3.
5. Reviewer mengecek lewat Version history bahwa bagian BRD lain tidak berubah.

## Cek

- 3 sampai 4 screen, tiap screen cocok dengan satu baris brief.
- Ada alasan tertulis untuk layout terpilih, dan feedback hanya mengubah yang diminta.
- Link atau gambar ada di BRD, dan [scorecard](../scorecard.md) UI v1 dan v2 terisi.

Perbedaan dengan jalur Stitch: tidak ada Prompt B2 lewat tool (kamu menghitung screen sendiri) dan tidak ada langkah API key. Kriteria lulus di README sama untuk kedua jalur.
