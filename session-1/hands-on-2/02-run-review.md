# Langkah 2: Jalankan brd-review

Durasi ±8 menit.

## Yang dikerjakan

1. Buka `BRD WebTM v1.0` di Google Docs dan salin link-nya dari address bar. Dokumen tidak perlu disalin: review hanya membaca.
2. Buka chat baru di dalam Project, pilih **Opus 5.5**, lalu kirim prompt di bawah dengan link tadi.
3. Baca laporannya: tabel gap, jumlah temuan, Terpenuhi, Tidak diperiksa, dan Skor mutu. Kalau Skill bertanya mana berkas pembanding, jawab dengan nama berkas Product Concept.

## Prompt

Ganti `[LINK BRD]` dengan link `BRD WebTM v1.0`.

```
/brd-review [LINK BRD] fokus kelompok fitur Role Management

Pembanding: Product Concept saja. Reference BRD bukan pembanding isi.
```

Bisa juga kirim `/brd-review` saja, lalu tempel link saat diminta.

## Cek

Tabel gap berisi ID, jenis, bagian BRD, kutipan, dan satu pertanyaan per baris. Laporan ditutup dengan Skor mutu. Kolom Pembanding di baris pembuka menyebut Product Concept, bukan Reference BRD. Jumlah dan isi gap bisa berbeda tiap kali dijalankan, itu normal.

---

Sebelumnya: [Langkah 1: Pasang brd-review](01-setup-skill.md)  
Berikutnya: [Langkah 3: Periksa dan rapikan hasil](03-check-results.md)
