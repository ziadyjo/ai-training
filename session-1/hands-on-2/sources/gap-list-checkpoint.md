# Gap list acuan: User & Role Management WebTM

> Acuan ini memuat gap seluruh modul. Review-mu dibatasi ke kelompok fitur Role Management, jadi gap tentang User Management (mis. G06, G07, G09) boleh tidak muncul di hasilmu.

Hasil acuan Hands-on #2. Gap diturunkan dari Product Concept (`../../hands-on-1/sources/`), yang juga menjadi sumber BRD hasil Hands-on #1. Di hasilmu, kolom Kutipan sumber memuat kutipan BRD diikuti kutipan sumbernya. Hasilmu akan berbeda: jumlah, urutan, dan rumusan gap bisa lain. Yang diperiksa adalah apakah gapmu punya kutipan nyata dan satu pertanyaan tertutup.

## Gap

| ID | Jenis | Bagian BRD | Kutipan sumber | Clarification question | Ditujukan ke |
|---|---|---|---|---|---|
| G01 | Hilang | 4 Project Summary (Definition of Success) | (tidak ada kalimat tentang ukuran keberhasilan) | Apa ukuran keberhasilan pemisahan User & Role Management dari CRM? | Product Owner |
| G02 | Hilang | 5 Project Scope (Out Of Scope) | (tidak ada kalimat tentang fungsi yang tidak dikerjakan) | Fungsi apa yang sengaja tidak dikerjakan di rilis ini? | Product Owner |
| G03 | Belum lengkap | 5 Project Scope (migrasi data) | "khusus untuk existing user yang sudah memiliki akses ke WebTM" | Apakah migrasi hanya mencakup user dengan status aktif? | Product Owner |
| G04 | Ambigu | 6 Business Process Overview | "apakah sistem WebTM melakukan sinkronisasi secara real-time (setiap kali user menekan tombol login), atau melalui proses penarikan data secara berkala" | Sinkronisasi Taconnect Position berjalan real-time saat login atau batch? | IT Lead |
| G05 | Hilang | 7 Requirement (hak akses menu) | "Menu Role Management & User Management akan diberikan akses ke tim IT/FA atau ke manager?" | Siapa yang memegang akses ke menu Role Management dan User Management: tim IT dan FA, atau manager? | Product Owner |
| G06 | Belum lengkap | 7 Requirement (Additional Role) | "TBC, terkait jumlah max additional role per user" | Berapa jumlah maksimum Additional Role per user? | Product Owner |
| G07 | Konflik | 7 Requirement (Add New User) | "hanya bisa memilih satu" | Apakah satu user boleh punya lebih dari satu Additional Role, dan dropdown di Add New User mengikuti aturan itu? | Product Owner |
| G08 | Ambigu | 7 Requirement (Role Status) | "sistem harus segera melakukan force logout" | Berapa detik batas waktu force logout setelah role menjadi Inactive? | IT Lead |
| G09 | Belum lengkap | 7 Requirement (Block login) | "menampilkan error message untuk menghubungi super admin" | Apakah teks error saat user terkena block adalah "Hubungi super admin"? | Product Owner |
| G10 | Konflik | 7 Requirement (nama menu) | "menu “User Management” dan “Role Management”" (nama di mapping View Only: "ACCESS CONTROL", "ROLES", "USERS") | Apakah nama menu baru "User Management" dan "Role Management", atau "USERS" dan "ROLES" di bawah ACCESS CONTROL? | Product Owner |
| G11 | Ambigu | 7 Requirement (View Only) | "tidak bisa export, edit, delete" (mapping: "TM REPORT", "Tidak ada perubahan") | Apakah fitur export di submenu laporan, misalnya TM REPORT, disembunyikan pada akses View Only? | Product Owner |
| G12 | Belum lengkap | 8 Appendix (Rules) | "role 1 memiliki akses “None” pada fitur A, dan role 2 memiliki akses “All Access” pada fitur A" | Bagaimana aturan gabungan bila satu role View Only dan role lain None pada menu yang sama? | Product Owner |

## Ringkasan

| Jenis | Jumlah | Gap |
|---|---|---|
| Hilang | 3 | G01, G02, G05 |
| Ambigu | 3 | G04, G08, G11 |
| Konflik | 2 | G07, G10 |
| Belum lengkap | 4 | G03, G06, G09, G12 |
| Terpenuhi | 7 | Lihat di bawah |

## Terpenuhi

| ID | Bagian BRD | Kutipan sumber |
|---|---|---|
| T01 | 7 Requirement (Assign Taconnect Position) | "1 Taconnect Position tidak bisa di assign ke multiple role" |
| T02 | 7 Requirement (Create New Role) | "Role ID → generate by system" |
| T03 | 7 Requirement (Create New Role) | "ada validasi nama role tidak boleh sama dengan role existing (baik role active or inactive)" |
| T04 | 7 Requirement (Login User Baru) | "New user login menggunakan NIK & Password Taconnect" |
| T05 | 7 Requirement (Pembatasan data) | "memiliki “division code” 14 maka user tersebut hanya dapat melihat data yang berasal dari Business Unit 2" |
| T06 | 7 Requirement (Role Status) | "Main Role Inactive + Additional Role Active → user terkena block" |
| T07 | 6 Business Process Overview | "akses ke WebTM akan inactive ketika akun Taconnect nya berubah status menjadi inactive" |
