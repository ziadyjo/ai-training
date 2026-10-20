# Glosarium Sesi 3

| Istilah | Arti |
|---|---|
| Claude Code | Agen Claude yang bekerja di folder proyek: membaca berkas, menjalankan perintah, dan mengubah berkas. Berjalan di tab **Code** aplikasi Claude desktop, di terminal, atau di ekstensi IDE |
| Tab Code | Bagian aplikasi Claude desktop (pilih Chat atau Code di bagian atas) untuk menjalankan Claude Code dengan antarmuka grafis, termasuk diff view dan Browser pane |
| Browser pane | Panel di tab Code yang membuka berkas HTML statis dari proyekmu |
| Konteks | Semua yang dibaca Claude dalam satu sesi: percakapan, isi berkas, dan hasil perintah. Makin penuh, makin turun mutunya |
| `CLAUDE.md` | Berkas teks di folder proyek yang dibaca Claude Code di awal tiap sesi. Berisi aturan dan konvensi proyek. Panduan, bukan penegak |
| `/init` | Perintah yang membuat `CLAUDE.md` awal dari isi folder |
| `/context` | Perintah untuk melihat isi konteks, termasuk apakah `CLAUDE.md` terbaca |
| `/clear` | Mengosongkan konteks di terminal. Di tab Code ekuivalennya sesi baru (Cmd+N atau Ctrl+N). Dipakai di antara tugas yang tidak berhubungan |
| `/rewind` | Mengembalikan sesi ke pesan sebelumnya. Ada di tab Code dan terminal (di terminal juga `Esc` dua kali) |
| Mode izin | Aturan kapan Claude Code meminta persetujuan sebelum bertindak: Manual, Accept edits, Plan, Auto, dan lainnya |
| Plan mode | Mode di mana Claude hanya membaca dan menyusun rencana. Berkas tidak diubah sampai kamu menyetujui rencananya |
| Prototype | Versi awal yang bisa diklik untuk didemokan dan diuji, bukan kode produksi |
| User story | Kebutuhan dalam satu kalimat: sebagai [peran], saya ingin [tujuan], supaya [manfaat] |
| Acceptance criteria | Butir yang bisa diperiksa ya atau tidak untuk menyatakan sebuah story selesai |
| Dependency | Story lain yang harus selesai lebih dulu |
| Backlog | Daftar story yang menunggu dikerjakan, dengan prioritas dan status |
| Database Notion | Tabel di Notion dengan properti (kolom) dan baris. Dipakai untuk backlog |
| Scheduled task | Tugas yang dijalankan Claude sesuai jadwal atau sesuai permintaan. Dibuat dan dikelola di menu **Scheduled** |
| Brief progres | Ringkasan tetap berformat tiga bagian: progres, prioritas, hambatan |
| Hambatan (blocker) | Hal yang menghentikan sebuah story. Dicatat dengan alasan dan sumbernya |
| Usulan perubahan | Perubahan BRD yang hanya diajukan Claude dan menunggu persetujuanmu, tidak ditulis langsung |
