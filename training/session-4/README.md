# Sesi 4: Test Cases & Agentic Testing

Dua hands-on: membangun Skill `qa-test` lalu menyusun test case berprioritas dari BRD, dan menjalankan satu test case di prototype lewat Claude in Chrome sampai ada bukti, defect, dan catatan hasil. Memakai BRD dari Sesi 1 dan prototype dari Sesi 3.

Setiap folder hands-on berisi langkah-langkahnya dan folder `sources/` dengan berkas yang dipakai di hands-on itu.

| Folder | Isi |
|---|---|
| [`hands-on-1/`](hands-on-1/) | Test Case Skill & Test Case Development (60 menit). Langkah 1 sampai 5, prompt siap salin, `sources/` |
| [`hands-on-2/`](hands-on-2/) | Agentic Test Execution & Documentation (90 menit). Langkah 1 sampai 6, prompt siap salin, `sources/` |
| [`scorecard.md`](scorecard.md) | Tabel untuk membandingkan hasil antar versi di tiap hands-on |
| [`glossary.md`](glossary.md) | Istilah yang dipakai di Sesi 4 |

## Yang perlu siap

- BRD hasil Sesi 1 di Google Docs, dengan ID requirement. Bila tertinggal: [`BRD acuan`](../session-1/hands-on-3/sources/brd-v1-1-checkpoint.md).
- Referensi tambahan (opsional): [`Reference BRD Role Management`](../session-2/reference-brd-role-management.md) untuk cek silang expected result. BRD utamamu tetap hasil Sesi 1.
- Prototype `index.html` dari Sesi 3. Bila tertinggal: minta prototype acuan ke instruktur. Simpan di folder yang mudah kamu temukan.
- Browser **Google Chrome**. Claude in Chrome tersedia di semua paket berbayar, jadi akun Claude Pro cukup.
- Project **WebTM Role & User Management** dari Sesi 1 dengan connector Google Docs yang tersambung.
- Disarankan: satu profil Chrome terpisah tanpa login ke akun kerja, bank, atau layanan pribadi. Claude in Chrome ikut memakai status login browser yang dipakai.

Skill baru di sesi ini: `qa-test` (kamu bangun dari starter di Hands-on #1) dan `qa-run` (siap pakai di Hands-on #2).
