# MoM Review BRD WebTM Role Management v1.1

- Tanggal meeting: diisi tanggal hari ini di Hands-on #3 Langkah 4
- Jenis: Review BRD
- Waktu: 10.00 sampai 11.00 WIB, Google Meet
- Notulen: Functional Analyst

Dokumen sample untuk training. Peserta, keputusan, dan tanggal tindak lanjut fiktif. Isi BRD diambil dari BRD WebTM Role Management v1.1.

## Peserta

Functional Analyst (FA), Product Owner (PO), Tech Lead, Backend Engineer, Frontend Engineer, QA Engineer.

## Tujuan meeting

1. Memastikan perubahan v1.1 (hasil meeting klarifikasi 20 Oktober 2026) sudah dipahami semua pihak.
2. Mengumpulkan sisa pertanyaan pada item TBC sebelum BRD naik ke v1.2.
3. Membuka diskusi perbaikan struktur dan isi BRD.

## Ringkasan

Tim Tech dan PO sepakat 10 perubahan di bagian 8.3 sudah mewakili hasil klarifikasi. Pembahasan terbanyak ada di tiga area: item TBC di RM-003 sampai RM-005, ketidakkonsistenan hak akses antara Rules 8.2 dan business requirement, dan jarak antara Definition of Success dengan Project Scope. Beberapa keputusan sudah diambil di meeting. Sisanya menjadi action item menuju v1.2.

## Pembahasan

### 1. Konfirmasi perubahan v1.1 (bagian 8.3)

- 1 user hanya memiliki 1 role. Additional Role, Main Role otomatis, serta block dan unblock sudah dihapus. Tech Lead mengonfirmasi model data lebih sederhana: satu kolom role per user.
- Force logout dihapus. User ter-logout setelah session habis, dan login berikutnya gagal bila Account Status atau Role Status Inactive (RM-006).
- Akses menu via URL untuk permission None ditolak. User belum login diarahkan ke Login, user sudah login ke Home (RM-005).
- View Only hanya menghilangkan button yang mengubah data. Export tetap bisa.
- Hasil: seluruh 10 perubahan diterima tanpa revisi.

### 2. Item TBC yang masih terbuka

| Req | Item TBC | Usulan di meeting | Status |
|---|---|---|---|
| RM-003 | Mapping change log dan entrypoint halaman | Entrypoint lewat Role Details. Mapping nama data: Role Name, Role Permission, Role Status | Perlu konfirmasi PO |
| RM-004 | Format Role ID | Prefix "ROL-" diikuti angka berurut | Disetujui sementara |
| RM-004 | Default Role Status | Active | Disetujui |
| RM-004 | Pesan validasi nama duplikat | Teks final dari PO | Terbuka |
| RM-004 | Field mandatory | Role Name dan Role Status | Disetujui |
| RM-005 | Default permission saat role baru | None untuk semua menu | Disetujui |
| RM-005 | Relasi akses menu induk dan submenu | Belum ada kesepakatan | Terbuka |
| 8.1 | Adjustment View Only untuk Master Menu | Menunggu keputusan fungsi Master Menu | Terbuka |

### 3. Konsistensi hak akses

QA menemukan tiga titik yang bisa dibaca berbeda:

- Business requirement RM-001 sampai RM-007 menyebut aktor "Super admin". Rules 8.2 butir 4 menyebut akses menu Role Management untuk super admin dan admin.
- Rules 8.2 butir 2 menyebut role diberikan oleh "admin", sedangkan butir 3 menyebut "super admin".
- Belum jelas level akses Admin di Role Management: tidak ada akses, View Only, atau All Access.

Hasil: PO menyatakan Admin mendapat View Only di Role Management. FA menyamakan istilah aktor di seluruh dokumen.

### 4. Definition of Success vs Project Scope

- Definition of Success meminta 100% existing user termigrasi dan user baru dapat ditambahkan lewat frontend.
- Out of Scope menyebut User Management dan login.
- Tech Lead: migrasi data user tetap diperlukan walau halaman User Management ada di dokumen lain.

Hasil: disepakati migrasi user dipisah menjadi kebutuhan tersendiri. FA menandai dua butir Definition of Success yang berada di luar scope dokumen ini, atau menambahkan migrasi di In Scope. Keputusan akhir menunggu PO.

### 5. Dampak Edit Role dan Role Status

- Perubahan permission pada role yang sedang dipakai: kapan berlaku untuk user yang sudah login? BRD belum mengatur.
- Durasi session belum tertulis, padahal RM-006 bergantung padanya.
- Role Inactive yang masih punya user: apakah user perlu dipindahkan role lebih dulu? BRD belum mengatur.

Hasil: permission berlaku saat login berikutnya. Durasi session dikonfirmasi Tech Lead dan dicantumkan di RM-006. Perlakuan user pada role Inactive dibahas di sesi berikutnya.

## Diskusi improvement BRD

| No | Usulan improvement | Alasan | Pengusul | Status |
|---|---|---|---|---|
| 1 | Tambah kolom Acceptance Criteria per requirement | QA butuh dasar test case yang terukur, bukan hanya deskripsi | QA | Diskusi |
| 2 | Isi kolom User Interface tiap requirement dengan link frame desain | Kolom saat ini kosong. Link Design dan Prototype hanya ada di kepala bagian Requirement | FA | Disetujui |
| 3 | Samakan rujukan desain | RM-006 menyebut "mengikuti Figma", sedangkan desain di BRD ada di Claude Design | FA | Disetujui |
| 4 | Tambah bagian Non-Functional Requirement (session, audit, performa) | Durasi session dan retensi change log belum ada tempatnya | Tech Lead | Diskusi |
| 5 | Perluas Change Log Role: simpan nilai sebelum dan sesudah | Format saat ini hanya mencatat nama data dan waktu, sulit dipakai audit | PO | Diskusi |
| 6 | Pisahkan Rules 8.2 per topik (akses, assignment, approval) | Satu bagian berisi lima aturan campuran, sulit ditelusuri ke requirement | FA | Diskusi |
| 7 | Tambah kolom Priority dan Dependency | Frontend dan Backend butuh urutan pengerjaan | Frontend | Diskusi |
| 8 | Lengkapi Document Approval (nama, tanggal, tanda tangan) | Tabel Approval masih kosong menjelang sign-off | PO | Disetujui |

## Keputusan

1. 10 perubahan di bagian 8.3 diterima.
2. Admin mendapat View Only di Role Management. Istilah aktor diseragamkan.
3. Default Role Status: Active. Default permission role baru: None.
4. Role ID memakai prefix "ROL-" (sementara, menunggu konfirmasi Backend).
5. Kolom User Interface diisi link desain, dan rujukan Figma diganti rujukan desain yang berlaku.
6. BRD naik ke v1.2 setelah semua action item High selesai.

## Action item

| No | Tindakan | PIC | Due | Prioritas | Status |
|---|---|---|---|---|---|
| 1 | Konfirmasi mapping change log dan entrypoint RM-003 | PO | 2026-10-26 | High | Belum mulai |
| 2 | Teks final pesan validasi nama role duplikat | PO | 2026-10-26 | Medium | Belum mulai |
| 3 | Putuskan relasi akses menu induk dan submenu (RM-005) | Tech Lead, PO | 2026-10-27 | High | Belum mulai |
| 4 | Putuskan fungsi Master Menu dan adjustment View Only | PO | 2026-10-27 | Medium | Belum mulai |
| 5 | Cantumkan durasi session di RM-006 | Tech Lead | 2026-10-27 | High | Belum mulai |
| 6 | Seragamkan istilah aktor dan perbaiki Rules 8.2 butir 2 dan 4 | FA | 2026-10-28 | High | Belum mulai |
| 7 | Selaraskan Definition of Success dengan Project Scope | FA, PO | 2026-10-28 | High | Belum mulai |
| 8 | Isi kolom User Interface dan ganti rujukan Figma | FA | 2026-10-28 | Medium | Belum mulai |
| 9 | Susun draft Acceptance Criteria untuk RM-003 sampai RM-007 | QA, FA | 2026-10-29 | Medium | Belum mulai |
| 10 | Terbitkan BRD v1.2 dan catat di Document Change Control | FA | 2026-10-30 | High | Belum mulai |

## Pertanyaan terbuka

- Apakah user pada role Inactive harus dipindahkan role sebelum status diubah, atau dibiarkan sampai session habis?
- Apakah Change Log Role perlu menyimpan nilai lama dan baru, dan berapa lama retensinya?
- Apakah Role Management perlu fitur hapus role, atau cukup Inactive?

## Rencana pertemuan berikutnya

Tanggal usulan: 2026-10-29. Agenda: verifikasi action item High, bahas diskusi improvement yang masih berstatus Diskusi, dan review draft BRD v1.2.
