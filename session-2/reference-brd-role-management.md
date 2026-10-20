# Reference BRD Role Management WebTM (v1.2)

> **Catatan penggunaan.** Potongan Reference BRD untuk Sesi 2 sampai 4. BRD utama tetap hasil Sesi 1. Pakai berkas ini sebagai pembanding untuk mengecek detail layar, skenario, dan aturan, bukan sebagai sumber utama. Cakupan hanya **Role Management** dan aturan akses yang menyertainya. Referensi ke UM-001, UM-003, UM-004, dan MM-002 menunjuk ke fitur User Management dan Master Menu yang di luar cakupan latihan; anggap perilakunya sebagai asumsi dan jangan dikembangkan.
>
> Salinan untuk pelatihan: nama pihak internal, link, dan gambar dihapus. Bentuk dan isi dokumen sama dengan `session-1/hands-on-1/sources/02-reference-brd.pdf`, dipotong sesuai cakupan. ID di sini (AC-001, RM-003, dan seterusnya) berbeda dari ID di BRD hasil Sesi 1.

## Document Identity
| Field | Isi |
|---|---|
| Prepared By | [Nama analis], Functional Analyst |
| Creation Date | 8 September 2026 |
| Version | 1.2 |

## Project Summary
**Background / Problem Statement**

Saat ini belum tersedia konfigurasi pada sisi frontend WebTM untuk melakukan perubahan maupun pemberian role kepada user. Seluruh proses tersebut masih dilakukan melalui backend oleh tim IT.

Selain itu, jika mengacu pada konsep Role Management v2.0 di CRM yang saat ini masih dalam tahap development, pemilihan role untuk WebTM masih digabungkan dengan konfigurasi User Management di CRM. Oleh karena itu, diusulkan agar pengelolaan role WebTM dipisahkan dari CRM sehingga data dapat dikelola secara lebih terstruktur, serta WebTM tidak lagi bergantung pada CRM dalam proses pengelolaan role.

Konsekuensi dari pemisahan tersebut adalah perlunya melakukan migrasi data user dari CRM ke WebTM, khususnya untuk existing user yang telah memiliki akses ke WebTM, guna memastikan data role tetap konsisten setelah proses migrasi dan pemisahan selesai dilakukan.

**Objective**
- Melakukan development modul Role Management, User Management, dan Menu Management yang berdiri sendiri di WebTM.
- Integrasi dengan sistem Taconnect sebagai sumber data user (NIK, password, position, superordinate, status karyawan).

**Definition of Success**
- 100% existing user WebTM berhasil dimigrasikan dari CRM tanpa kehilangan akses.
- Proses penambahan user baru dapat dilakukan secara mandiri melalui manual input dari sisi frontend.
- Kebutuhan akses bagi karyawan yang diperbantukan dapat diakomodasi melalui pembuatan dan pemberian role khusus sesuai kebutuhan bisnis.
- Perubahan role/status user tercatat pada change log untuk kebutuhan audit.

## Project Scope
**In Scope Functionality**
- Role Management: halaman daftar role, create new role, role details, change log role, dan pengaturan role permission (None / View Only / All Access) per menu dan submenu.
- User Management: halaman daftar user, add new user, edit user, change log user.
- Master Menu: halaman daftar menu, create new menu, edit menu.
- Logic pembatasan data dashboard berdasarkan pemilihan business unit per user.
- Migrasi data user dari CRM ke WebTM untuk existing user yang sudah memiliki akses WebTM.
- Sinkronisasi status akun dengan Taconnect: akses WebTM inactive ketika akun Taconnect user berubah status menjadi inactive (case karyawan resign), serta sinkronisasi password Taconnect.

**Out Of Scope Functionality**
- Perubahan line of approval. Line of approval tetap mengikuti atasan di Taconnect; jika staff diperbantukan sebagai manager, staff tersebut tidak otomatis menjadi bagian dari line of approval. Workaround mengikuti kondisi sekarang: perubahan dilakukan secara manual melalui request ke IT.
- Pengelolaan data master karyawan (NIK, nama, email, no. handphone, position, superordinate, password) seluruhnya bersumber dari Taconnect dan tidak dikelola di WebTM.

## Requirement

### Autentikasi & Access Control

#### Section: Login & Autentikasi
**Business Requirement:** User (existing maupun karyawan baru) dapat login ke WebTM menggunakan kredensial Taconnect.

##### AC-001 Login
- User login menggunakan NIK dan Password Taconnect.
- Jika user melakukan perubahan password di akun Taconnect, password di WebTM otomatis mengikuti perubahan tersebut (seperti kondisi existing).
- Saat login, sistem melakukan pengecekan terhadap "Account Status" dan "Role Status" user tersebut. Jika **salah satunya** Inactive, maka login gagal dan muncul informasi untuk menghubungi admin.
- Saat login, sistem juga membaca Business Unit yang ter-assign pada user tersebut untuk menentukan data dashboard yang ditampilkan (BU 1, BU 2, atau BU 1 dan BU 2).
  - Business Unit mengambil source data dari "Division Code": BU1 memakai division code 12, BU2 memakai division code 14.

##### AC-002 New User (Karyawan Baru)
- Saat login, sistem melakukan pengecekan. Jika user baru tersebut belum pernah dibuatkan akun di WebTM (belum ter-assign role apa pun), user tidak berhasil login dan muncul informasi untuk menghubungi admin.

**User Interface (AC-001 dan AC-002):** modal informasi "Login to WebTM is temporarily restricted. Please contact your Admin for confirmation." dengan tombol OK.

#### Section: Use Case Scenario
**Business Requirement:** Sistem mengakomodasi skenario karyawan yang mungkin terjadi, yaitu: promosi, diperbantukan, resign, penonaktifan manual, dan handling case user akses menu via URL.

##### AC-003 Skenario
- **Promosi/mutasi:** super admin mengubah Role user secara manual melalui fitur edit user.
- **Diperbantukan:** super admin membuat role baru dan meng-assign-nya khusus untuk user yang diperbantukan.
- **Resign:** akses WebTM (Account Status) otomatis inactive ketika akun Taconnect berubah status menjadi inactive.
- **Penonaktifan di luar case resign:** dilakukan manual melalui entrypoint edit user.
- **Apabila user mencoba mengakses suatu menu melalui URL:**
  - User belum login: diarahkan ke halaman Login.
  - User sudah login: sistem memvalidasi dua kondisi, yaitu (i) Role Permission user terhadap menu tersebut (None / View Only / All Access) dan (ii) Menu Status pada Master Menu (Active / Inactive). Jika **salah satu** kondisi tidak terpenuhi (permission None, atau Menu Status Inactive), user diarahkan ke halaman Home.

**User Interface:** tidak ada UI.

#### Section: Entrypoint Admin
**Business Requirement:** Super admin dan admin dapat mengakses fitur role management, user management, dan master menu melalui entrypoint yang sudah tersedia.

##### AC-004 Entrypoint
- Super admin dapat mengakses fitur role management, user management, dan master menu dengan klik menu "Access Control" pada sidebar.
- Menu "Access Control" memiliki 3 submenu:
  - **Master Menu**: mengarahkan ke fitur Master Menu.
  - **Roles**: mengarahkan ke fitur Role Management.
  - **Users**: mengarahkan ke fitur User Management.
- Entrypoint "Access Control" hanya muncul untuk user yang memiliki role dengan permission View Only atau All Access pada menu Access Control.

**User Interface:** tampilan sidebar dengan menu "Access Control" dan tiga submenu.

### Role Management

#### Section: Halaman Daftar Role
**Business Requirement:** Super admin dan admin dapat melihat seluruh role yang tersedia di WebTM beserta status dan riwayat perubahannya.

##### RM-001 Halaman Daftar Role
- Entrypoint button "Create New Role".
- Tabel dengan kolom: Role ID, Role Name, Role Status (Active/Inactive), button "Edit Role", dan button "Log".

##### RM-002 Halaman Change Log Role
- Log menyimpan informasi perubahan data yang dilakukan super admin terhadap role tersebut; tersedia di masing-masing role.
- Secara default data yang tampil adalah 3 bulan terakhir. Super admin dapat mengubah filter tanggal dengan rentang maksimal 3 bulan.
- Mapping change log ada di dokumen terpisah (tidak disertakan).

**User Interface:** halaman Daftar Role dan halaman Change Log Role.

#### Section: Create New Role
**Business Requirement:** Super admin dapat membuat role baru dan melakukan pengaturan permission per menu dan submenu untuk role tersebut.

##### RM-003 Halaman Create New Role
- Role ID: generated by sistem.
- Role Name: free text (alphanumeric); ada validasi nama role **tidak boleh sama** dengan role existing, baik active maupun inactive. Field ini **mandatory**.
- Managed Roles:
  - Dropdown multiple select, optional. Menampilkan seluruh role berstatus Active, ditambah satu pilihan khusus "All Active Roles".
  - Field ini menentukan role apa saja yang dapat di-assign oleh pemegang role ini saat menambah atau mengubah user (lihat UM-003 dan UM-004), serta membatasi data user yang dapat dilihatnya (UM-001).
  - Jika "All Active Roles" dipilih, cakupan Managed Roles mengikuti seluruh role Active. Role baru yang dibuat setelahnya otomatis termasuk tanpa perlu ditambahkan manual.
  - Managed Roles dapat mencakup role itu sendiri, sehingga role tersebut dapat meng-assign user lain ke role yang sama.
  - Role dengan Managed Roles kosong tidak dapat menambah maupun mengubah role user mana pun, meskipun memiliki permission All Access pada submenu Users.
  - Catatan: pilihan "All Active Roles" menurut SOP hanya diberikan kepada role Super Admin dan role Auditor (Auditor untuk kebutuhan view data).
  - Simulasi contoh case (dua tabel). Tabel 1, data user terdaftar: User A (Sales, BU 1), User B (Sales, BU 2), User C (Finance, BU 1), User D (Finance, BU 1 dan BU 2), User E (Staff Admin, BU 1), User F (Super Admin, BU 1 dan BU 2). Tabel 2, simulasi wewenang admin: Super Admin (Managed Roles: All Active Roles) melihat seluruh user dan dapat meng-assign seluruh role Active; Staff Admin 1 (Managed Roles: Sales, Finance; BU 1) melihat User A, C (User B beda BU, User D BU-nya bukan subset) dan dapat meng-assign Sales dan Finance; Staff Admin 2 (Managed Roles: Sales; BU 2) melihat User B dan dapat meng-assign Sales; Staff Admin 3 (Managed Roles: Sales, Staff Admin; BU 1 dan BU 2) melihat User A, B, E dan dapat meng-assign Sales dan Staff Admin.

##### RM-004 Role Permission
- Menampilkan daftar seluruh menu dan submenu **Active** di WebTM.
- Setiap menu dan submenu memiliki dropdown dengan nilai:
  - **None**: entrypoint menu tidak ditampilkan pada FE user, dan ada validasi block jika user mengakses menu via URL.
  - **View Only**: user hanya bisa melihat data; tidak bisa edit maupun delete (penyesuaian per menu ada di Appendix 8.1).
  - **All Access**: user memiliki akses penuh terhadap menu tersebut.
- Keterkaitan "Master Menu" dengan section "Menu Structure":
  - Menu berstatus Active yang baru ditambahkan melalui Master Menu **otomatis muncul** pada Menu Structure di seluruh role (baru maupun existing) dengan **default permission "None"**.
  - Urutan menu dan submenu pada Menu Structure (halaman Create/Edit Role) mengikuti urutan pada tabel Master Menu (MM-002).
  - Menu Structure hanya menampilkan menu berstatus Active.
  - Ketika menu yang sebelumnya Inactive diaktifkan kembali, menu muncul lagi di Menu Structure dan permission yang sudah ter-set (None, View Only, atau All Access) tetap berlaku, tanpa perlu di-set ulang oleh super admin.

##### RM-005 Role Status
- Set Active/Inactive melalui radio button "Role Status". Secara default terpilih "Active" ketika super admin membuat role baru.
- Dampak perubahan Role Status terhadap user: jika role yang dimiliki user diubah menjadi Inactive, user ter-logout setelah session berakhir, dan saat login kembali akan gagal karena role sudah tidak aktif.
  - Ketika user gagal login, muncul modal seperti pada AC-001.
- Role yang diubah menjadi Inactive tetap tersimpan pada konfigurasi Managed Roles role lain, tetapi tidak muncul sebagai pilihan pada dropdown User Role (UM-003/UM-004) karena dropdown tersebut hanya menampilkan role Active.

**User Interface (RM-003 sampai RM-005):** halaman Create New Role dengan field Role Name, Managed Roles, Role Status, dan daftar menu beserta dropdown permission.

#### Section: Role Details
**Business Requirement:** Super admin dan admin dapat melihat detail role dan mengubah data role. Super admin dapat melihat daftar member dari suatu role.

##### RM-006 Halaman Role Details
- Informasi yang ditampilkan:
  - Role ID.
  - Nama Role.
  - Section "Managed Roles": daftar role yang dapat dikelola role ini, atau label "All Active Roles" bila opsi itu dipilih. Jika kosong, tampil empty state.
  - Role Status.
  - Role Permission.
  - Role Members: total user yang memiliki role tersebut dan detail data user.
    - Section "Role Members" hanya ditampilkan untuk user yang memiliki permission All Access pada submenu Roles.
    - Terdapat searchbar untuk **search by account name, NIK, atau email**.
- Data yang dapat di-edit: Role Name, Role Permission, Status Role (Active/Inactive).
- Perubahan tercatat pada Change Log Role (RM-002).

##### RM-007 Detail UX
- Ada 4 chip pada "Access Level":
  - **None**: role tidak memiliki akses terhadap suatu menu.
  - **Mixed**: role memiliki Access Level campuran; terjadi ketika beberapa submenu dengan parent menu yang sama memiliki akses berbeda.
  - **View Only**: role memiliki akses view terhadap suatu menu.
  - **All Access**: role memiliki akses penuh terhadap suatu menu.
- Jika user mengubah "Access Level" lewat parent menu, submenu di bawahnya mengikuti konfigurasi parent.
- Jika user mengubah "Access Level" lewat submenu, konfigurasi pada parent menu diabaikan. Catatan: pengalaman lengkapnya dapat dicek lewat prototype.

##### RM-008 Modal Konfirmasi
- Modal konfirmasi selalu muncul ketika user klik button "Submit" (berlaku di seluruh halaman yang memiliki button "Submit"). Isi modal: "Confirm Submission. Are you sure you want to submit these changes?" dengan tombol "Yes, Submit" dan "Cancel".

**User Interface (RM-006 sampai RM-008):** halaman Role Details (tampilan expand dan edit) dan modal konfirmasi.

## Appendix

### 8.1 Mapping Adjustment untuk Access Level "View Only" (menu contoh)
Delapan submenu dari daftar lengkap, cukup untuk latihan.

| Menu | Submenu | Adjustment View Only |
|---|---|---|
| TRADEMARKETING | DRAFT | Remove button "Create New Sales Brief"; remove button "Edit" dan "Delete" |
| TRADEMARKETING | SET PIC SALES | Remove button "Add Salesman"; remove button "Edit" |
| TRADEMARKETING | APPROVAL DRAFT SB | Remove button "Approve" dan "Reject"; remove button "Delete" pada section customer |
| SERVICES | DAILY ACUMULATION | Remove button "Sync" |
| INQUIRY FBP/TM | DMS SALES | Tidak ada perubahan |
| ACCESS CONTROL | MASTER MENU | Remove button "Add New Menu", "Change Menu Order", dan "Edit" |
| ACCESS CONTROL | ROLES | Remove button "Create New Role" dan "Edit" |
| ACCESS CONTROL | USERS | Remove button "Add New User" dan "Edit" |

### 8.2 Rules
1. Akses **All Access** pada fitur Role Management dan fitur Master Menu hanya diberikan kepada role Super Admin.
2. Akses **All Access** pada fitur User Management diberikan kepada role Super Admin dan PIC yang ditunjuk untuk mengelola user.
3. Proses pembuatan role baru maupun perubahan role dikelola oleh tim IT, sehingga apabila ada kebutuhan terkait hal tersebut, dapat mengajukan request kepada tim IT via helpdesk.
4. Proses pemberian akses kepada user baru maupun perubahan akses pada user yang sudah ada, **khusus** untuk user dengan role "Drafter" dan "Viewer", dikelola oleh PIC dari masing-masing Business Unit (BU).
5. Untuk kebutuhan penambahan user dengan role selain "Drafter" dan "Viewer", dapat mengajukan request kepada tim IT via helpdesk.
6. Untuk tim Audit akan diberikan akses View Only pada fitur Role dan User Management.
7. Role Mapping: tersedia di dokumen terpisah (tidak disertakan).

Catatan: aturan di atas sudah melalui diskusi dengan tim Audit.

### 8.3 Changes
Perubahan di bawah ini sudah melalui diskusi antara FA dengan tim Tech.

| No | Description | Note |
|---|---|---|
| 1 | Field status diubah menjadi bentuk toggle. Toggle ditampilkan di kolom "status" pada tabel master menu, tabel users, dan tabel roles | Dilakukan untuk mempermudah development dari sisi BE tanpa mengubah logic requirements |
| 2 | Di halaman user dan roles ditambahkan fitur search dan sort by (order) | |
| 3 | Label "Mixed" dihapus | Parent menu dengan kondisi ini tidak menampilkan label apa pun. Dilakukan supaya tidak perlu mapping status "Mixed"; tidak mempengaruhi fungsi atau logic lainnya |
