# Langkah 2: Jalankan ui-brief

Durasi ±15 menit. Brief UI adalah daftar screen, tujuan, aksi, komponen, dan state. Kamu memeriksanya di chat, sebelum satu pun screen dibuat di Stitch.

## Yang dikerjakan

1. Di chat baru dalam Project WebTM, pilih **Sonnet 5.5**. Ketik `/ui-brief`, pilih Skill dari daftar, lalu tempel prompt di bawah dengan link BRD dan flow spec-mu.
2. Bila Skill bertanya soal design system atau panduan UI, jawab "tidak ada" kecuali kamu punya. Bila tidak bertanya, gaya ditulis "ikuti gaya produk yang sudah ada" dan masuk daftar pertanyaan. Keduanya normal.
3. Skill membaca BRD (lewat connector dengan kartu izin, atau sebagai lampiran bila link terbaca otomatis). Dia menampilkan tabel screen, **Cek mutu brief** (N dari 6), daftar pertanyaan, dan prompt desain.
4. Reviewer mengecek hasilnya dengan daftar di bagian Cek. Driver mencatat Cek mutu di [scorecard](../scorecard.md) baris v1.
5. Jangan menyetujui dulu. Pilih 3 sampai 4 screen inti, lalu lanjut ke Langkah 3.

## Prompt

Ganti dulu: `[LINK BRD]` dan `[TEMPEL FLOW SPEC]`.

```
/ui-brief [LINK BRD]

Flow: Create New Role. Flow spec ada di bawah. Platform: desktop (admin web). Pengguna: Super Admin. Screen inti: Halaman Daftar Role, Role Members, Change Log Role, dan Create New Role sebagai satu halaman seperti di BRD. Hal yang belum ditentukan ditulis sebagai placeholder netral, bukan kalimat bersyarat. Berhenti sebelum prompt desain dipakai.

[TEMPEL FLOW SPEC]
```

## Cek

- Setiap screen berasal dari langkah flow, atau ditandai "di luar flow" dengan ID requirement.
- Setiap screen punya tujuan dan minimal satu aksi.
- Screen penting menyebut state kosong, loading, atau error (mis. nama role duplikat).
- Tidak ada field atau aksi di luar BRD. Yang belum pasti ada di daftar pertanyaan.
- Create New Role tetap satu halaman. Kalau Claude memecahnya menjadi beberapa screen tanpa dasar di BRD, minta digabung.
- Prompt desain menyebut platform, gaya, dan "Jangan menambah fitur di luar daftar ini".
- Cek mutu bisa kurang dari 6, misalnya Role Members gagal di "Tujuan dan aksi" karena BRD hanya menyebut tampilan. Itu penilaian jujur, bukan kesalahanmu.

Elemen yang tidak punya ID requirement adalah elemen dikarang: hitung di scorecard.

---

Sebelumnya: [Langkah 1: Pasang ui-brief dan siapkan referensi](01-setup-skill.md)  
Berikutnya: [Langkah 3: Hubungkan Stitch lewat MCP](03-connect-stitch-mcp.md)
