# Glosarium Sesi 4

| Istilah | Arti |
|---|---|
| Test case | Satu skenario uji: prakondisi, langkah bernomor, expected result, dan prioritas, dengan rujukan ke ID requirement |
| Skenario positif | Jalur normal dengan data yang valid |
| Skenario negatif | Jalur yang seharusnya ditolak atau gagal, mis. nama role yang sudah dipakai |
| Skenario batas | Nilai di tepi aturan, mis. panjang maksimal atau rentang tanggal |
| Prakondisi | Keadaan yang harus ada sebelum langkah pertama dijalankan |
| Expected result | Hasil yang seharusnya tampak di layar. Harus bisa diamati, bukan "berfungsi" |
| Actual result | Hasil yang benar-benar tampak saat test case dijalankan |
| Prioritas | Tinggi, Sedang, atau Rendah, ditentukan oleh dampak bila test case gagal |
| Coverage matrix | Tabel requirement terhadap test case, untuk melihat requirement yang belum teruji |
| Agentic testing | Menguji dengan Claude yang mengendalikan browser: membuka halaman, mengklik, mengetik, dan melaporkan apa yang terlihat |
| Claude in Chrome | Ekstensi Chrome yang membiarkan Claude bekerja di halaman web lewat side panel. Tersedia di paket berbayar |
| Side panel | Panel obrolan Claude di sisi jendela Chrome, dibuka dari ikon Claude di toolbar |
| Mode persetujuan | Seberapa sering Claude meminta izin: Manually approve (tiap aksi), Automatically approve, atau Skip all approvals |
| Izin situs | Izin per situs yang kamu berikan: Allow this action, Always allow actions on this site, atau Decline |
| Prompt injection | Teks tersembunyi atau terang di halaman yang mencoba menyuruh Claude melakukan hal di luar tugasmu |
| Evidence | Bukti hasil, biasanya tangkapan layar, dengan nama berkas yang bisa dilacak ke langkahnya |
| Execution record | Tabel hasil eksekusi per langkah: expected, actual, hasil, dan bukti |
| Hasil: Lulus, Gagal, Terblokir | Lulus bila actual sama dengan expected, Gagal bila berbeda, Terblokir bila langkah tidak bisa dijalankan atau tidak teramati |
| Defect | Satu ketidaksesuaian antara expected dan actual, dicatat lengkap dengan langkah reproduksi dan bukti |
| Tingkat defect | Tinggi (fungsi inti gagal), Sedang (ada jalan keluar), Rendah (tampilan atau kenyamanan) |
| Change note | Usulan perubahan BRD dari temuan uji. Hanya usulan sampai manusia menyetujuinya |
| QA Report | Laporan satu halaman hasil pengujian: ringkasan, cakupan, hasil per test case, defect, bukti, dan usulan change note |
