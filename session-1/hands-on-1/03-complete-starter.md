# Langkah 3: Lengkapi starter Skill

Durasi ±5 menit. Starter `brd-draft` sudah berisi langkah kerja, kriteria review, Aturan generate BRD, dan format output. Satu bagian masih kosong: **Description** di frontmatter. Description menentukan kapan Claude memanggil Skill, jadi bagian ini yang kamu tulis.

## Yang dikerjakan

1. Di chat yang sama dengan Langkah 2. Klik **+** lalu unggah berkas [`sources/brd-draft-starter/SKILL.md`](sources/brd-draft-starter/SKILL.md). Di baris `description:` berkas itu tertulis `[KOSONG ...]`.
2. Tempel prompt di bawah dan kirim.
3. Hitung karakter Description dan pastikan tidak lebih dari 450. Simpan paragrafnya, dipakai di Langkah 4.

## Prompt

```
TASK
Tulis isi description untuk starter Skill brd-draft yang terlampir. Cukup satu paragraf, maksimal 450 karakter.

Description harus menyebut:
- kapan Skill dipakai, termasuk variasi nama dokumen (draft requirement, product concept, catatan rapat, permintaan fitur) dan frasa yang mungkin diketik analis ("buat BRD", "susun requirement"),
- input yang dikenali,
- hasil yang dibuat,
- kapan Skill tidak dipakai, termasuk saat analis meminta review atau cek BRD yang sudah jadi (itu tugas brd-review).

OUTPUT FORMAT
Satu paragraf teks biasa dalam satu blok kode, lalu satu baris yang menyebut jumlah karakternya.

RULES
- Jangan mengubah bagian lain di starter.
- Tulis dari isi starter, bukan dari asumsi.
- Jangan membaca atau menilai Product Concept sekarang.
```

## Cek

Satu paragraf Description, maksimal 450 karakter, yang menyebut kapan Skill dipakai, input, hasil, dan kapan tidak dipakai. Kalau melebihi 450, kirim: `Perpendek jadi maksimal 450 karakter tanpa menghilangkan kapan Skill tidak dipakai.`

---

Sebelumnya: [Langkah 2: Analisis struktur dan konvensi BRD](02-analyze-structure.md)  
Berikutnya: [Langkah 4: Pasang Skill di Claude](04-setup-skill.md)
