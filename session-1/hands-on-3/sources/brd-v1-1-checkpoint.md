# BRD acuan v1.1: User & Role Management WebTM

> Acuan ini memuat seluruh modul User & Role Management. BRD yang kamu susun di Hands-on #1 sampai #3 hanya memuat kelompok fitur Role Management (RM-001 sampai RM-009). Bandingkan bagian itu saja; kelompok fitur lain (AC, UM, MM, VO) tidak perlu ada di BRD-mu.

Hasil acuan Hands-on #3. Dibuat dari Product Concept dan notulen meeting klarifikasi (`meeting-notes.pdf` di folder ini). Isinya ditulis dalam Markdown agar mudah dibaca; BRD-mu sendiri ada di Google Docs dengan format template. Hasilmu akan berbeda: nomor ID, rumusan, dan jumlah TBC bisa lain. File ini dipakai lagi di Sesi 2.

## 1. Document Identity

| | |
|---|---|
| Prepared By | [Nama penyusun] - [Jabatan] |
| Prepared For | Tim Tech |
| Creation Date | [Tanggal pembuatan] |
| Version | 1.1 |

## 2. Document Change Control

| Version | Date | Summary of Change |
|---|---|---|
| 1.0 | [Tanggal] | First draft |
| 1.1 | [Tanggal] | Hasil meeting klarifikasi dimasukkan |

## 3. Approval

Dibiarkan seperti template.

## 4. Project Summary

**Background/Problem Statement.** User Management dan Role Management WebTM dan CRM diajukan untuk dipisah. Alasannya, data menjadi lebih rapi karena tidak cross platform dan tidak ada ketergantungan ke CRM (jika CRM down, WebTM tidak terdampak). Jika dipisah, data user existing yang sudah punya akses ke WebTM perlu dimigrasi dari CRM ke WebTM.

**Objective**
- Memisahkan User Management dan Role Management WebTM dari CRM.
- Menyediakan fitur Role Management, User Management, dan Master Menu di WebTM.
- Memigrasikan data user existing dari CRM ke WebTM.

**Definition of Success**
- 100% existing user WebTM termigrasi dari CRM tanpa kehilangan akses.
- User baru bisa ditambahkan sendiri lewat frontend tanpa request ke IT.
- Perubahan role dan status user tercatat di change log untuk kebutuhan audit.
- Kebutuhan akses karyawan yang diperbantukan dipenuhi lewat role khusus.

## 5. Project Scope

**In Scope Functionality**
- Role Management: daftar role, Role Members, change log role, create role (termasuk Managed Roles), role permission, edit role.
- User Management: daftar user, change log user, add new user, edit user.
- Master Menu: daftar menu, tambah menu, edit menu, ubah urutan menu di sidebar.
- Pembatasan data dashboard berdasarkan Business Unit.
- Penyesuaian tampilan menu untuk akses View Only.
- Migrasi data user dari CRM, hanya untuk existing user yang sudah punya akses ke WebTM.
- Sinkronisasi status akun dan password dengan Taconnect.

**Out Of Scope Functionality**
- Perubahan line of approval: tetap ikut atasan di Taconnect, perubahan manual lewat request ke IT.
- Pengelolaan data master karyawan (NIK, nama, email, no. handphone, position, superordinate, password): seluruhnya bersumber dari Taconnect dan tidak diedit di WebTM.

## 6. Business Process Overview (Optional)

**Current Business Process (As-Is)**
- User login dengan NIK dan password Taconnect. Jika password Taconnect berubah, password WebTM ikut berubah.
- Akses WebTM karyawan resign menjadi inactive ketika akun Taconnect-nya inactive.
- Line of approval mengikuti atasan di Taconnect. Perubahan line of approval dilakukan manual lewat request ke IT.

**Proposed Business Process**
TBC. Draft memuat user flow Role Management dan User Management dalam bentuk gambar yang tidak terbaca di teks.

## 7. Requirement

Design & Prototype: Belum ada. User Interface: Belum ada pada semua baris.

### Autentikasi dan Access Control

| ID | Requirement | Sumber |
|---|---|---|
| AC-001 | Login. User login dengan NIK dan password Taconnect. Jika password Taconnect berubah, password WebTM ikut berubah. Saat login sistem memeriksa Account Status dan Role Status. Jika salah satunya Inactive, login gagal dan muncul modal info untuk menghubungi admin | Product Concept, Proposed Concept; MoM poin 7 |
| AC-002 | User baru. User baru yang belum dibuatkan akun di WebTM tidak bisa login dan melihat modal info yang sama | MoM poin 7 |
| AC-003 | Entrypoint Access Control. Di sidebar ada menu "Access Control" dengan tiga submenu: Master Menu, Roles, Users. Menu hanya muncul untuk role yang punya View Only atau All Access pada menu tersebut | MoM poin 13 |
| AC-004 | Akses menu lewat URL. User belum login diarahkan ke halaman Login. User sudah login dengan permission None atau menu Inactive diarahkan ke Home | MoM poin 18 |
| AC-005 | Pembatasan data dashboard. BU 1 mengambil division code 12 dan BU 2 mengambil division code 14. Field Business Unit di Add New User dan Edit User berisi BU 1, BU 2, atau BU 1 & BU 2. Admin hanya bisa memilih BU yang termasuk BU miliknya | Product Concept, Proposed Concept; MoM poin 11 |
| AC-006 | Sinkronisasi dengan Taconnect. Yang disinkronkan adalah status akun dan password, dicek setiap login. Position tidak dipakai | MoM poin 7, 8, 10 |
| AC-007 | Login saat Taconnect tidak bisa diakses: TBC | MoM poin 21 |

### Role Management

| ID | Requirement | Sumber |
|---|---|---|
| RM-001 | Tabel Daftar Role. Ada entrypoint "Create New Role". Kolom: Role ID, Role Name, Total User, Role Status (Active atau Inactive), button "Edit Role", Log. Tersedia search dan sort. Status ditampilkan sebagai toggle | Product Concept, Halaman Daftar Role; MoM poin 20 |
| RM-002 | Role Members. Angka Total User bisa diklik dan membuka halaman Role Members berisi nama dan email user dengan role itu | Product Concept, Halaman Daftar Role |
| RM-003 | Change Log Role. Setiap role punya Log perubahan oleh super admin. Format contoh: "[nama super admin] memperbarui data "role name" pada [tanggal] pukul [jam]". Default tampil 3 bulan terakhir, filter tanggal maksimal rentang 3 bulan. Detail mapping change log: TBC | Product Concept, Halaman Daftar Role; MoM poin 19 |
| RM-004 | Create New Role. Role ID di-generate sistem. Role Name berupa free text alphanumeric dan tidak boleh sama dengan role existing, Active maupun Inactive. Managed Roles berupa dropdown multiple select, optional. Role Status dipilih lewat radio button. Pesan validasi nama duplikat: TBC | Product Concept, Create New Role; MoM poin 15 |
| RM-005 | Managed Roles. Menentukan role apa saja yang boleh di-assign pemegang role ini ke user, dan user mana yang tampil di daftar user. Tersedia opsi "All Active Roles". Managed Roles kosong: tidak bisa menambah atau mengubah user. "All Active Roles" hanya untuk Super Admin dan Auditor | MoM poin 15 |
| RM-006 | Role Permission. Menampilkan semua menu dan submenu WebTM. Tiap menu punya dropdown None, View Only, atau All Access. None: menu tidak tampil dan akses lewat URL ditolak. View Only: tombol yang mengubah data dihilangkan, menu report tetap dan export tetap bisa (lihat 8.1). All Access: full akses | Product Concept, Create New Role; MoM poin 14 |
| RM-007 | Dampak perubahan Role Status. Jika role menjadi Inactive, user yang sedang login tidak di-force logout saat itu juga. User ter-logout setelah session habis, lalu gagal login (modal info hubungi admin) | MoM poin 9 |
| RM-008 | Edit Role. Data yang dapat diedit: Role Name, Role Permission, Managed Roles, Role Status | Product Concept, Edit Role |
| RM-009 | Hak akses fitur. Hanya super admin dan admin, bukan manager. Rinciannya di Appendix 8.2 | MoM poin 12 |

### User Management

| ID | Requirement | Sumber |
|---|---|---|
| UM-001 | Satu user satu role. Additional Role dan multiple role per user tidak dikerjakan. Karyawan yang diperbantukan dibuatkan role baru khusus oleh super admin, lalu di-assign ke user itu | Product Concept, Proposed Concept; MoM poin 5 |
| UM-002 | Tabel Daftar User. Entrypoint "Add New User". Kolom: NIK, Username, Name, Email, Role, Business Unit, Account Status, button "Edit User", Log. Tersedia search dan sort. Data yang tampil dibatasi Business Unit dan Managed Roles milik user yang login | Product Concept, Halaman Daftar User; MoM poin 15, 20 |
| UM-003 | Change Log User. Setiap user punya Log perubahan oleh super admin. Format contoh: "[nama super admin] memperbarui data "Role" pada [tanggal] pukul [jam]". Default tampil 3 bulan terakhir, filter tanggal maksimal rentang 3 bulan. Detail mapping: TBC | Product Concept, Halaman Daftar User; MoM poin 19 |
| UM-004 | Add New User (manual). NIK diambil dari Taconnect (cara memilih NIK: TBC). Username, Name, Email, No. Handphone, Superordinate di-generate sistem dan tidak bisa diedit. Role: dropdown role Active yang termasuk Managed Roles user yang login, satu pilihan, mandatory. Business Unit: BU 1, BU 2, atau BU 1 & BU 2. Account Status: Inactive berarti user tidak punya akses | Product Concept, Add New User; MoM poin 5, 11 |
| UM-005 | Edit User. Data yang dapat diedit: Role, Business Unit, Account Status | Product Concept, Edit User; MoM poin 6, 11 |
| UM-006 | Promosi atau pindah divisi. Super admin mengubah role user secara manual lewat Edit User | Product Concept, Use Case Scenario; MoM poin 6 |
| UM-007 | Karyawan resign. Account Status WebTM menjadi Inactive otomatis ketika akun Taconnect menjadi inactive | Product Concept, Use Case Scenario; MoM poin 8 |
| UM-008 | Nonaktifkan user manual. Di luar kasus resign, user dinonaktifkan lewat Edit User | Product Concept, Use Case Scenario; MoM poin 8 |
| UM-009 | Migrasi data user dari CRM. Hanya existing user yang sudah punya akses ke WebTM. Mapping role CRM ke role WebTM disiapkan FA dan di-review Product Owner sebelum migrasi. Jadwal migrasi dan target go-live: TBC | Product Concept, Overview; MoM poin 2, 3, 22 |
| UM-010 | Pembagian kerja kelola user. PIC tiap BU mengurus user dengan role Drafter dan Viewer. Role lain, serta pembuatan dan perubahan role, lewat request ke IT via helpdesk | MoM poin 16 |

### Master Menu

| ID | Requirement | Sumber |
|---|---|---|
| MM-001 | Fitur Master Menu: daftar menu, tambah menu, edit menu, dan ubah urutan menu di sidebar | MoM poin 17 |
| MM-002 | Menu Inactive tidak tampil di sidebar dan tidak bisa diakses lewat URL | MoM poin 17 |
| MM-003 | Menu baru otomatis muncul di semua role dengan permission default None | MoM poin 17 |

## 8. Appendix

### 8.1 Mapping Adjustment untuk Access Level "View Only"

Sel Menu yang kosong berarti masih menu induk yang sama dengan baris di atasnya. Sumber: Product Concept, tabel Mapping Adjustment; MoM poin 14.

| Menu | Submenu | Adjustment View Only |
|---|---|---|
| TRADEMARKETING | DRAFT | - Remove button "Create New Sales Brief"<br>- Remove button "Edit" dan "Delete" |
|  | INFORMASI PROMO | - Remove button "Edit" dan "Duplicate" |
|  | UPLOAD SB MANUAL | - Remove section "Upload" |
|  | SET PIC SALES | - Remove button "Add Salesman"<br>- Remove button "Edit" |
|  | TM REPORT | - Tidak ada perubahan |
| APPROVAL | DRAFT SB | - Remove button "Approve" dan "Reject"<br>- Remove button "Delete" pada section customer |
|  | REALIZATION | - Tidak ada perubahan |
| SERVICES | DAILY ACUMULATION | - Remove button "Sync" |
|  | CLAIM STATUS | - Tidak ada perubahan |
|  | ANNOUNCE | - Tidak ada perubahan |
| INQUIRY FBP/TM | DMS SALES | - Tidak ada perubahan |
|  | TANGKAS SALES | - Tidak ada perubahan |
|  | NAV SALES | - Tidak ada perubahan |
|  | AUDIT GC DATA | - Tidak ada perubahan |
|  | REDEEM DIRECT | - Tidak ada perubahan |
| SB MONITORING | SALES BRIEF | - Tidak ada perubahan |
|  | SB SELL OUT | - Tidak ada perubahan |
|  | SB SELL IN | - Tidak ada perubahan |
|  | TCM CLAIM & REDEEM | - Tidak ada perubahan |
|  | NAV REDEEM | - Tidak ada perubahan |
|  | SYNC SALES BRIEF | - Tidak ada perubahan |
| PROMO NOTIF | WA REPORT | - Tidak ada perubahan |
|  | LOGGING HISTORY | - Tidak ada perubahan |
| ACCESS CONTROL | ROLES | - Remove button "Create New Role"<br>- Remove button "Edit" |
|  | USERS | - Remove button "Add New User"<br>- Remove button "Edit" |

Fitur export di submenu laporan (mis. TM REPORT) tetap bisa dipakai pada akses View Only (MoM poin 14).

### 8.2 Rules

1. Akses All Access pada Role Management dan Master Menu hanya untuk Super Admin.
2. Akses All Access pada User Management untuk Super Admin dan PIC yang ditunjuk.
3. Tim Audit mendapat View Only pada Role Management dan User Management.
4. Pembuatan role baru dan perubahan role dikelola tim IT lewat request helpdesk.
5. PIC tiap BU mengelola user dengan role Drafter dan Viewer. User dengan role lain lewat request ke IT via helpdesk.
6. Opsi "All Active Roles" pada Managed Roles hanya untuk Super Admin dan Auditor.

### 8.3 Changes

| No | Description | Note |
|---|---|---|
| 1 | Additional Role, multiple role per user, Taconnect Position pada role, dan mekanisme block dan unblock dihapus. Satu user satu role | MoM poin 5, 6 |
| 2 | Managed Roles dan Master Menu ditambahkan | MoM poin 15, 17 |
| 3 | Division code BU 1 dikoreksi dari 13 menjadi 12 | MoM poin 11 |
| 4 | Status berbentuk toggle di tabel. Search dan sort ditambahkan di daftar user dan role. Label "Mixed" pada parent menu dihapus | MoM poin 20 |

## Catatan kerja (tidak masuk dokumen BRD)

### Daftar TBC

| No | Pertanyaan | Ditujukan ke |
|---|---|---|
| 1 | Bagaimana user login saat Taconnect tidak bisa diakses? (menunggu cek IT Lead) | IT Lead |
| 2 | Kapan target tanggal go-live dan jadwal migrasi? | IT Lead |
| 3 | Bagaimana cara memilih NIK di Add New User? | Product Owner |
| 4 | Pesan validasi nama role duplikat belum ditentukan | Product Owner |
| 5 | Detail mapping change log role dan user belum ada | Functional Analyst |
| 6 | Proposed Business Process: user flow di draft berupa gambar | Functional Analyst |
