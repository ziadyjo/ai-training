# Requirement Document: WebTM Role Management

Version 1.1 · [Tanggal]

BRD acuan untuk Sesi 3 dan 4, hasil Sesi 1 dan 2 (BRD v1.1 dengan link flow dan desain). Pakai bila BRD-mu tertinggal. BRD-mu sendiri tetap yang utama.

## 1. Document Identity

| Prepared By | Prepared For | Creation Date | Version |
|---|---|---|---|
| [Nama] - Functional Analyst | Tim Tech | [Tanggal] | 1.1 |

## 2. Document Change Control

| Version | Date | Summary of Change |
|---|---|---|
| 1.0 | [Tanggal] | First draft |
| 1.1 | [Tanggal] | Update hasil meeting klarifikasi 20 Oktober 2026. Detail perubahan di 8.3 Changes. |

## 3. Approval

| Name | Date | Sign |
|---|---|---|
|  |  |  |

## 4. Project Summary

**Background / Problem Statement**

- User Management dan Role Management antara WebTM dan CRM diajukan untuk dipisah, supaya data lebih rapi karena tidak cross platform.
- Dengan pemisahan ini WebTM tidak bergantung ke CRM, misalnya saat CRM down tidak berdampak ke WebTM.

**Objective**

- Memisahkan Role Management WebTM dari CRM.
- Menyediakan pengelolaan role di WebTM: daftar role, role members, change log, create, permission, status, dan edit role.

**Definition of Success**

- Seluruh existing user WebTM termigrasi dari CRM (100%), tidak ada user yang kehilangan akses.
- User baru dapat ditambahkan lewat frontend tanpa request ke IT.
- Perubahan role dan status user tercatat di change log.

## 5. Project Scope

**In Scope Functionality:** Halaman Daftar Role, Halaman Role Members, Halaman Change Log Role, Create New Role, Role Permission, Dampak perubahan Role Status terhadap user, Edit Role.

**Out of Scope Functionality:** User Management dan login.

## 6. Business Process Overview

**Current Business Process (As-Is):** User Management dan Role Management WebTM masih tergabung dengan CRM.

**Proposed Business Process:** Flow Create New Role (swimlane Super admin dan Sistem) ada di board Miro: [LINK BOARD MIRO]. Ringkasan alur:

1. Super admin membuka Access Control > Roles (akses Roles: All Access). RM-001, RM-005
2. Sistem menampilkan Daftar Role dengan button Create New Role. RM-001
3. Super admin klik Create New Role. RM-001
4. Super admin mengisi Role Name (free text, alphanumeric). RM-004
5. Super admin mengatur Role Permission (None, View Only, All Access). RM-004, RM-005
6. Super admin memilih Role Status (Active atau Inactive). RM-004
7. Super admin mengirim form (nama button dan konfirmasi: TBC).
8. Keputusan sistem: Role Name sama dengan role existing (Active atau Inactive)? RM-004
9. Ya: sistem menampilkan pesan validasi (teks: TBC), kembali ke form. RM-004
10. Tidak: sistem generate Role ID (format: TBC) dan menyimpan role baru. RM-004
11. Role baru tersimpan (tampilan setelah simpan: TBC). RM-004

Exception: View Only pada Roles menghilangkan button Create New Role (RM-005, 8.1). None pada Roles menyembunyikan entrypoint menu, dan akses via URL ditolak (RM-005).

## 7. Requirement

Design: [LINK CLAUDE DESIGN] · Prototype: [LINK PROTOTYPE]. Bila tertinggal: lihat gambar di folder `mockup-acuan/`.

| Section | Business Requirement | Functional Requirement | User Interface |
|---|---|---|---|
| Halaman Daftar Role | Super admin dapat melihat seluruh role di WebTM beserta jumlah user dan statusnya. | **RM-001 Halaman Daftar Role**<br>- Menampilkan entrypoint button "Create New Role".<br>- Menampilkan table dengan kolom: Role ID, Role Name, Total User, Role Status (Active atau Inactive), dan button "Edit Role".<br>- Angka pada kolom Total User clickable dan mengarahkan ke Halaman Role Members (RM-002).<br>- Entrypoint menu: sidebar Access Control > Roles. | `mockup-acuan/list.png` |
| Halaman Role Members | Super admin dapat melihat user yang memiliki suatu role. | **RM-002 Halaman Role Members**<br>- Menampilkan daftar nama dan email user yang memiliki role tersebut. | `mockup-acuan/members.png` |
| Halaman Change Log Role | Super admin dapat melihat riwayat perubahan data pada setiap role. | **RM-003 Halaman Change Log Role**<br>- Log menyimpan informasi perubahan data yang dilakukan super admin terhadap role.<br>- Log tersedia di masing-masing role.<br>- Format log: "[Nama super admin] memperbarui data "[nama data]" pada [tanggal] pukul [jam] WIB."<br>- Detail mapping change log: TBC<br>- Entrypoint ke halaman: TBC | `mockup-acuan/log.png` |
| Create New Role | Super admin dapat membuat role baru. | **RM-004 Create New Role**<br>- Role ID: generate by system. Format: TBC<br>- Role Name: free text (alphanumeric). Validasi: nama role tidak boleh sama dengan role existing, baik Active maupun Inactive. Pesan validasi: TBC<br>- Role Permission: lihat RM-005.<br>- Role Status: radio button Active atau Inactive. Default: TBC<br>- Field mandatory: TBC | `mockup-acuan/create.png` |
| Role Permission | Super admin dapat mengatur level akses setiap role terhadap menu dan submenu WebTM. | **RM-005 Role Permission**<br>- Menampilkan listing seluruh menu dan submenu WebTM, ditambah menu "Access Control" dengan submenu Master Menu, Roles, dan Users. "User Management" dan "Role Management" adalah nama fitur di dokumen, bukan nama menu.<br>- Menu Access Control hanya tampil untuk role dengan akses View Only atau All Access pada menu tersebut.<br>- Setiap menu dan submenu memiliki dropdown dengan value None, View Only, dan All Access.<br>- None: entrypoint menu tidak ditampilkan di FE user. Akses menu via URL ditolak. User yang belum login diarahkan ke halaman Login. User yang sudah login diarahkan ke halaman Home.<br>- View Only: yang dihilangkan hanya button yang mengubah data (create, edit, delete, approve, upload, sync, dan sejenisnya). Export tetap bisa, termasuk pada menu report seperti TM Report. Detail per submenu di Appendix 8.1.<br>- All Access: user memiliki full akses terhadap menu.<br>- Default value: TBC<br>- Relasi akses menu induk dan submenu: TBC | `mockup-acuan/create.png` (bagian Role Permission) |
| Dampak Role Status | Perubahan status role membatasi akses user yang memiliki role tersebut. | **RM-006 Dampak Perubahan Role Status**<br>- User sedang login: jika role diubah menjadi Inactive, user tidak di-force logout saat itu. User ter-logout setelah session habis, dan login berikutnya gagal.<br>- Saat login, sistem mengecek Account Status dan Role Status. Jika salah satu Inactive, login gagal dan sistem menampilkan modal info untuk menghubungi admin. | `mockup-acuan/edit.png` (info saat Inactive dipilih) |
| Edit Role | Super admin dapat mengubah data role yang sudah ada. | **RM-007 Edit Role**<br>- Data yang dapat diedit: Role Name, Role Permission, Status Role (Active atau Inactive).<br>- Perubahan tercatat di Change Log Role (RM-003). | `mockup-acuan/edit.png` |

## 8. Appendix

### 8.1 Mapping Adjustment untuk Access Level "View Only"

| Menu | Submenu | Adjustment View Only |
|---|---|---|
| TRADEMARKETING | DRAFT | Remove button "Create New Sales Brief". Remove button "Edit" dan "Delete" |
|  | INFORMASI PROMO | Remove button "Edit" dan "Duplicate" |
|  | UPLOAD SB MANUAL | Remove section "Upload" |
|  | SET PIC SALES | Remove button "Add Salesman". Remove button "Edit" |
|  | TM REPORT | Tidak ada perubahan |
| APPROVAL | DRAFT SB | Remove button "Approve" dan "Reject". Remove button "Delete" pada section customer |
|  | REALIZATION | Tidak ada perubahan |
| SERVICES | DAILY ACUMULATION | Remove button "Sync" |
|  | CLAIM STATUS | Tidak ada perubahan |
|  | ANNOUNCE | Tidak ada perubahan |
| INQUIRY FBP/TM | DMS SALES, TANGKAS SALES, NAV SALES, AUDIT GC DATA, REDEEM DIRECT | Tidak ada perubahan |
| SB MONITORING | SALES BRIEF, SB SELL OUT, SB SELL IN, TCM CLAIM & REDEEM, NAV REDEEM, SYNC SALES BRIEF | Tidak ada perubahan |
| PROMO NOTIF | WA REPORT, LOGGING HISTORY | Tidak ada perubahan |
| ACCESS CONTROL | ROLES | Remove button "Create New Role". Remove button "Edit" |
|  | USERS | Remove button "Add New User". Remove button "Edit" |
|  | MASTER MENU | TBC |

### 8.2 Rules

1. 1 user hanya memiliki 1 role.
2. Role diberikan manual oleh admin lewat Add User atau Edit User. Promosi atau mutasi dilakukan super admin dengan mengubah role lewat Edit User.
3. Untuk karyawan yang diperbantukan, super admin membuat role baru khusus lalu meng-assign role tersebut ke karyawan itu.
4. Akses menu Role Management dan User Management hanya untuk super admin dan admin. All Access Role Management dan Master Menu hanya Super Admin. All Access User Management untuk Super Admin dan PIC yang ditunjuk. Tim Audit mendapat View Only di Role Management dan User Management.
5. Line of approval tidak berubah dan tetap mengikuti atasan di Taconnect. Perubahan line of approval dilakukan manual dengan request ke IT.

### 8.3 Changes

Perubahan di bawah ini sudah melalui diskusi antara FA dengan tim Tech.

| No | Description | Note |
|---|---|---|
| 1 | Additional Role dan multiple role per user dihapus. 1 user hanya memiliki 1 role. Aturan line of approval ditulis ulang tanpa menyebut multiple role. Berdampak ke RM-002, RM-006, dan 8.2 Rules. | Poin notulen 4, 5 |
| 2 | Taconnect Position tidak lagi di-assign ke role. Main Role otomatis serta mekanisme block dan unblock dihapus. Berdampak ke Project Summary, RM-004, RM-006, RM-007, dan 8.2 Rules. | Poin notulen 6 |
| 3 | Definition of Success diisi. Berdampak ke Project Summary. | Poin notulen 2 |
| 4 | Nama menu di sidebar menjadi Access Control dengan submenu Master Menu, Roles, dan Users. Entrypoint Halaman Daftar Role: Access Control > Roles. Berdampak ke RM-001, RM-005, dan 8.1. | Poin notulen 13 |
| 5 | Akses menu via URL untuk permission None ditolak dan diarahkan ke halaman Login atau Home. Berdampak ke RM-005. | Poin notulen 14, 18 |
| 6 | View Only hanya menghilangkan button yang mengubah data. Export tetap bisa. Berdampak ke RM-005. | Poin notulen 14 |
| 7 | Aturan gabungan akses None dan All Access dihapus. Berdampak ke 8.2 Rules. | Poin notulen 14 |
| 8 | Force logout dihapus. User ter-logout setelah session habis. Berdampak ke RM-006. | Poin notulen 9 |
| 9 | Saat login sistem mengecek Account Status dan Role Status. Jika salah satu Inactive, login gagal dan sistem menampilkan modal info untuk menghubungi admin. Berdampak ke RM-006. | Poin notulen 7 |
| 10 | Akses menu Role Management dan User Management per peran ditambahkan. Berdampak ke 8.2 Rules. | Poin notulen 12 |
