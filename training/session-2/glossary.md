# Glosarium Sesi 2

| Istilah | Arti |
|---|---|
| Connector | Jalan Claude ke tool lain (mis. Miro, Google Docs) supaya Claude bisa membaca dan menulis di tool itu, bukan hanya membalas teks |
| MCP | Model Context Protocol. Cara standar sebuah tool menyediakan "pintu" untuk Claude. Connector di aplikasi Claude memasang pintu itu tanpa kode |
| Tool permission | Izin per tool connector: Allow, Needs approval, atau Block. Bawaannya Needs approval |
| Board | Kanvas di Miro. Claude hanya bisa membuka board yang bisa diakses akunmu |
| Flow spec | Tabel aktor, langkah, jenis (Mulai, Proses, Keputusan, Akhir), tujuan langkah berikutnya, dan ID requirement. Diperiksa di chat sebelum digambar |
| Swimlane | Diagram alir dengan satu lajur per aktor |
| Keputusan | Titik di flow yang bercabang. Tiap cabang punya label |
| Exception | Jalur saat sesuatu gagal: input salah, akses ditolak, data kosong, status tidak aktif |
| Rujukan ID | ID requirement di BRD yang mendasari satu langkah atau satu screen. Tanpa ID, langkah ditandai "tanpa rujukan" |
| Cek mutu | Daftar enam pemeriksaan tetap di hasil Skill, ditulis sebagai "N dari 6" |
| Brief UI | Daftar screen, tujuan, aksi, komponen, dan state yang disusun sebelum mockup dibuat |
| State | Kondisi tampilan sebuah screen: normal, kosong, loading, error, sukses |
| Stitch | Alat Google untuk membuat desain layar dari deskripsi teks |
| Design system | Kumpulan aturan warna, tipografi, dan komponen yang dipakai untuk menjaga desain konsisten |
| Layout variation | Dua atau lebih susunan berbeda untuk satu screen dengan isi yang sama, dibandingkan dengan kriteria |
| Custom connector | Connector yang kamu tambahkan sendiri dengan URL server MCP jarak jauh. Tidak diverifikasi Anthropic, jadi pakai hanya server tepercaya |
| DESIGN.md | Format terbuka dari Stitch untuk aturan desain (warna, tipografi, komponen) yang bisa diekspor dan diimpor antar project |
| API key | Kunci rahasia untuk masuk ke sebuah layanan. Simpan di variabel lingkungan, jangan ditempel di chat, BRD, atau repo |
| Claude Code | Alat Claude yang berjalan di terminal atau aplikasi desktop dan bisa memakai server MCP. Dipakai di sini untuk menghubungkan Stitch |
| Claude Design | Kanvas desain di aplikasi Claude. Alternatif untuk Stitch di Hands-on #2 |
