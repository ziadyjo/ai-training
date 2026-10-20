# Langkah 4: Hasilkan dan bandingkan screen

Durasi ±25 menit. Claude menyusun prompt desain di chat, lalu Claude Code mengirimnya ke Stitch lewat MCP. Hasil pertama jarang tepat, jadi kamu meminta dua layout untuk satu screen, memilih satu dengan kriteria (bukan selera), dan memberi feedback ke yang terpilih.

Alternatif: kalau memakai Claude Design, ikuti [claude-design.md](claude-design.md), yang memuat versi lengkap semua prompt di bawah untuk kanvas Claude Design.

## Yang dikerjakan

1. Di chat Langkah 2 (tempat `ui-brief` berjalan), kirim Prompt A supaya Claude menampilkan prompt desain final untuk 3 sampai 4 screen yang kamu pilih. Salin blok prompt hasil Prompt A, bukan prompt di brief Langkah 2.
2. Di Claude Code, kirim Prompt B dengan prompt desain tadi. Beri izin tool Stitch bila diminta. Tunggu semua screen selesai: label "Generating Screen..." di Stitch harus hilang dulu. Jangan mengirim ulang Prompt B selama masih berjalan, karena itu membuat screen ganda.
3. Kirim Prompt B2 di Claude Code untuk mengecek jumlah screen. Kalau kurang, minta hanya screen yang belum ada.
4. Buka project di Stitch (web) untuk melihat hasilnya. Stitch biasanya menambah elemen sendiri (menu navigasi lain, breadcrumb, data contoh, kolom tambahan) dan bisa membuat design system serta prototype otomatis. Elemen tambahan dihitung sebagai elemen dikarang, lalu dihapus lewat Prompt E. Cek tiap screen terhadap tabel brief dari Langkah 2. Catat field tambahan, state yang hilang, dan aksi di luar BRD. Untuk detail perilaku layar (Role Details, chip akses, modal konfirmasi), bandingkan dengan RM-006 sampai RM-008 di [Reference BRD Role Management](../reference-brd-role-management.md).
5. Pilih screen yang paling penting (untuk Create New Role biasanya form dengan Role Permission). Di Claude Code, kirim Prompt C untuk dua variasi layout.
6. Nilai kedua variasi dengan tabel Kriteria di bawah. Tulis satu kalimat alasan per kriteria, lalu pilih satu.
7. Ambil screenshot layout terpilih dan unggah ke chat Claude dengan Prompt D. Claude hanya melaporkan yang terlihat.
8. Kirim feedback ke Stitch lewat Claude Code dengan Prompt E, satu perubahan saja. Catat hasilnya di [scorecard](../scorecard.md): baris v1 dari screen pertama, baris v2 setelah feedback.

Tertinggal? Minta brief UI dan prompt desain acuan ke instruktur, lalu mulai dari Prompt B atau Prompt C.

## Prompt mana dikirim di mana

| Prompt | Kirim di |
|---|---|
| A: prompt desain final | Chat Claude (tempat `ui-brief` berjalan) |
| B: buat screen di Stitch | **Claude Code** (terminal) |
| B2: cek jumlah screen | **Claude Code** |
| C: dua variasi layout | **Claude Code** |
| D: periksa screenshot | Chat Claude, dengan screenshot |
| E: feedback satu perubahan | **Claude Code** |

Kalau Claude menjawab "tool Stitch tidak ada di sesi ini", kamu mengirim prompt B, C, atau E di chat Claude. Pindah ke jendela terminal tempat `claude` berjalan dan kirim ulang di sana.

## Kriteria memilih layout

| Kriteria | Pertanyaan pengecekan |
|---|---|
| Kecocokan flow | Urutan pengisian sama dengan langkah di flow spec? |
| Kelengkapan | Semua field di brief ada, dan tidak ada field tambahan? |
| Aksi utama | Tombol Simpan terlihat jelas dan tidak mudah salah klik? |
| State | Ada tempat untuk pesan error nama duplikat? |
| Keterbacaan | Daftar permission per menu mudah dipindai tanpa menggulir berlebihan? |

## Prompt A: prompt desain final (kirim di chat Claude)

```
Brief sudah benar. Tulis prompt desain untuk Google Stitch untuk screen yang kita pilih. Satu blok, siap tempel, tanpa penjelasan di dalamnya.
```

## Prompt B: buat screen (kirim di Claude Code)

Ganti dulu: `[TEMPEL PROMPT DESAIN]`.

```
Gunakan tool Stitch untuk membuat project baru bernama "Claude AI Training" dan membuat screen dari prompt desain di bawah. Buat satu per satu, lalu sebutkan nama dan ID tiap screen yang dibuat. Jangan menambah screen atau fitur di luar daftar.

[TEMPEL PROMPT DESAIN]
```

## Prompt B2: cek jumlah screen (kirim di Claude Code)

```
Panggil list_screens untuk project "Claude AI Training" dan sebutkan nama dan ID tiap screen. Tandai screen ganda. Kalau ada screen dari daftar prompt desain yang belum dibuat, buat hanya yang belum ada, satu per satu, dengan gaya yang sama. Jangan mengubah screen yang sudah ada.
```

## Prompt C: dua variasi layout (kirim di Claude Code)

```
Gunakan tool Stitch untuk membuat dua variasi layout untuk screen Create New Role. Variasi A: form satu kolom, Role Permission di bagian bawah. Variasi B: form dua kolom, Role Permission di panel kanan. Isi field dan aksi sama persis di keduanya. Jangan mengubah screen lain dan jangan menambah field atau fitur.
```

## Prompt D: periksa terhadap brief (kirim di chat Claude, dengan screenshot)

```
TASK
Periksa screenshot screen ini terhadap brief UI di percakapan ini. Sebutkan: elemen yang tidak ada di brief, state yang hilang, dan aksi yang tidak punya requirement.

RULES
- Hanya yang terlihat di screenshot. Jangan menebak.
- Jangan membuat desain baru.
```

## Prompt E: feedback satu perubahan (kirim di Claude Code)

Ganti dulu: `[PERUBAHAN]`.

```
Pada layout yang kupilih: [PERUBAHAN]. Gunakan tool Stitch untuk mengedit screen itu saja. Jangan mengubah screen lain.
```

Contoh perubahan: "tambahkan state error di bawah field Role Name dengan teks 'Role Name sudah dipakai'", atau "hapus menu navigasi, kolom, dan data contoh yang tidak ada di brief".

Opsional, bila instruktur membagikan referensi gaya produk (DESIGN.md): minta Claude Code membuat design system dari berkas itu lewat tool design system Stitch dan menerapkannya ke satu screen dulu. Tanpa referensi gaya, hasil Stitch memakai gayanya sendiri; itu tidak mengurangi nilai latihan.

## Jika memakai Claude Design

Langkah lengkap dan prompt untuk kanvas Claude Design ada di [claude-design.md](claude-design.md). Prompt D tetap dikirim di chat Claude dengan screenshot.

## Cek

- Jumlah screen sama dengan yang kamu pilih (minimal 2, target 4), dan elemen bisa dicocokkan ke baris di brief.
- Ada alasan tertulis untuk layout terpilih, daftar temuan dari Prompt D, dan layout setelah feedback yang berubah hanya di bagian yang kamu minta.
- Elemen tanpa baris di brief dihitung sebagai elemen dikarang di scorecard.

---

Sebelumnya: [Langkah 3: Hubungkan Stitch lewat MCP](03-connect-stitch-mcp.md)  
Berikutnya: [Langkah 5: Simpan hasil dan tautkan ke BRD](05-save-link-to-brd.md)
