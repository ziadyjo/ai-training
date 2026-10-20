# Glosarium

| Istilah | Arti |
|---|---|
| Project | Ruang kerja di claude.ai yang menyimpan dokumen referensi, instruksi, dan riwayat chat untuk satu produk atau modul |
| Skill | Folder berisi `SKILL.md` dan berkas pendukung yang menyimpan cara kerja berulang |
| Description | Field frontmatter yang menjelaskan apa yang dikerjakan Skill dan kapan dipakai |
| Gap | Bagian requirement yang hilang, ambigu, konflik, atau belum lengkap dibanding template BRD |
| Clarification question | Pertanyaan tertutup untuk stakeholder yang jawabannya bisa langsung ditulis ke BRD |
| TBC | To be confirmed. Penanda hal yang belum pasti, dipakai sebagai ganti menebak |
| Model | Versi Claude yang menjawab (Haiku, Sonnet, Opus, Fable). Dipilih per tier sesuai tugas |
| Effort | Seberapa teliti Claude bekerja. Lebih tinggi berarti lebih teliti, lebih lama, dan kuota lebih cepat habis |
| Tool | Bagian Claude yang bekerja di luar teks: code execution, file creation, web search, connectors |
| Context window | Batas isi yang bisa dibaca Claude sekaligus: instruksi, lampiran, dan riwayat chat |
| Checkpoint | Berkas acuan yang dibagikan instruktur bila kamu tertinggal, untuk melanjutkan dan bukan untuk disalin |
| Scorecard | Tabel di Hands-on #2 dan #3 untuk mencatat Skor mutu dan hasil review tiap versi BRD |
| Mode perbarui | Cara `brd-draft` memperbarui BRD yang sudah terisi: Claude menampilkan daftar perubahan (lama, baru, dasar) di chat, lalu hanya bagian di daftar itu yang ditulis ke dokumen |
| Versi BRD | Tiap versi (v1.0, v1.1, v1.2, ...) adalah salinan versi sebelumnya, bukan dibuat dari template kosong. Riwayatnya ada di berkas-berkasnya |
| Skor mutu | Nilai N dari 8 dari delapan pemeriksaan tetap di akhir laporan `brd-review`. Delapan pemeriksaan yang sama dipakai di tiap versi BRD supaya bisa dibandingkan |
| Reference BRD | BRD jadi yang dipakai sebagai contoh bentuk, tingkat detail, dan pola ID. Bukan sumber isi |
| Temuan berulang | Temuan review yang muncul lagi di versi atau BRD berikutnya, sehingga menunjukkan aturan Skill yang kurang |
| Siklus iterasi | Satu putaran: review, perbaiki Skill dari dua temuan, salin versi dan perbarui, review ulang. Bisa diulang sebanyak perlu |
