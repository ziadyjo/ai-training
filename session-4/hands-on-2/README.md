# Hands-on #2: Agentic Test Execution & Documentation

Kamu menyiapkan Claude in Chrome, menjalankan satu test case dari Hands-on #1 di prototype dengan Claude yang mengendalikan browser dan kamu yang mengawasi, lalu mencatat hasil, bukti, dan defect. Berkas yang dipakai ada di [`sources/`](sources/).

| | |
|---|---|
| Durasi | 90 menit |
| Model | Sonnet 5.5 untuk menyusun catatan hasil. Claude in Chrome memakai pilihan model di side panel-nya |
| Jalur | Utama: Claude in Chrome (side panel) dengan mode Manually approve. Alternatif: nyalakan dari aplikasi Claude desktop (Settings, Connectors). Cadangan: jalur manual, kamu menjalankan langkah sendiri dan `qa-run` menyusun catatannya |
| Hasil | Satu test case dieksekusi sampai laporan, **QA Report** (execution record, defect record dengan bukti, usulan change note), Cek mutu execution record (N dari 6), scorecard v1 dan v2 |

Agentic testing di browser masih berkembang. Targetnya realistis: setup, satu test case sampai laporan, lalu satu iterasi. Dua test case dan satu defect adalah target lanjutan.

## Urutan langkah

| Langkah | Isi | Berkas | Menit |
|---|---|---|---|
| 1 | Siapkan Claude in Chrome, izin, dan prototype | [01-setup-claude-in-chrome.md](01-setup-claude-in-chrome.md) | ±15 |
| 2 | Pasang qa-run dan pilih test case | [02-setup-qa-run-pick-test-case.md](02-setup-qa-run-pick-test-case.md) | ±10 |
| 3 | Jalankan test case pertama | [03-run-first-test-case.md](03-run-first-test-case.md) | ±25 |
| 4 | Bandingkan, bukti, dan defect | [04-compare-evidence-defects.md](04-compare-evidence-defects.md) | ±15 |
| 5 | Iterasi: test case kedua atau aturan lebih ketat | [05-iterate-second-run.md](05-iterate-second-run.md) | ±15 |
| 6 | Konsolidasi dan QA Report | [06-consolidate-qa-report.md](06-consolidate-qa-report.md) | ±10 |

## Cek mutu execution record

Enam pemeriksaan tetap. Dipakai di Langkah 4 (v1) dan Langkah 5 (v2). Skor: jumlah yang lolos, dari 6.

| No | Pemeriksaan |
|---|---|
| 1 | Setiap Lulus dan Gagal punya nama berkas atau label bukti yang bisa dilacak ke langkahnya |
| 2 | Expected dan actual dicatat per langkah, bukan hanya hasil akhir |
| 3 | Tidak ada hasil yang disimpulkan tanpa teramati. Yang tidak teramati ditulis Terblokir dengan alasan |
| 4 | Satu ketidaksesuaian punya satu defect yang lengkap (langkah reproduksi, expected, actual, tingkat, bukti) |
| 5 | Semua aksi di alamat prototype yang diizinkan dan memakai data uji |
| 6 | Jumlah per hasil dan jumlah defect di ringkasan cocok dengan tabel |

## Cara menyalin prompt

1. Klik tombol salin di pojok kanan blok kode. Satu blok adalah satu prompt.
2. Ganti teks dalam kurung siku, misalnya `[ALAMAT PROTOTYPE]`, sebelum mengirim.
3. Tiap prompt bertanda tempat kirimnya: side panel Claude in Chrome, atau chat Claude di Project WebTM.
4. Prompt memakai label huruf besar: CONTEXT, TASK, RULES, OUTPUT FORMAT. Pertahankan labelnya saat kamu mengganti teks di dalamnya.

## Tertinggal?

Minta berkas acuan ke instruktur. Hasilmu akan berbeda dari acuan: pakai acuan untuk melanjutkan, bukan untuk menyalin.

## Kriteria lulus

- [ ] Claude in Chrome terpasang dan menjawab di tab prototype, atau kamu memakai jalur manual dengan alasan yang jelas.
- [ ] Mode **Manually approve** dipakai dan kamu menyetujui aksi satu per satu.
- [ ] Satu test case dieksekusi sampai selesai atau Terblokir dengan alasan.
- [ ] Expected dan actual dibandingkan per langkah, dengan bukti untuk tiap klaim.
- [ ] Defect (bila ada) lengkap dan bisa direproduksi orang lain.
- [ ] [Scorecard](../scorecard.md) v1 dan v2 untuk execution record terisi.
- [ ] QA Report satu halaman memuat hasil, defect, bukti, dan cakupan.
- [ ] Temuan menjadi usulan change note. BRD tidak diubah langsung.

## Kalau bermasalah

| Masalah | Jalan keluar |
|---|---|
| Ikon Claude tidak ada di toolbar Chrome | Klik ikon puzzle di Chrome lalu pin ekstensi Claude. Bila ekstensi belum ada, pasang dari Chrome Web Store dan masuk dengan akun Claude yang sama |
| Side panel meminta masuk atau upgrade | Claude in Chrome butuh paket berbayar dan akun yang sama dengan aplikasi Claude. Masuk ulang di ekstensi |
| Claude menjawab tidak bisa mengakses halaman prototype | Buka `chrome://extensions`, pilih Detail pada ekstensi Claude, dan aktifkan **Allow access to file URLs**. Muat ulang tab. Bila tetap gagal: buka `index.html` di Browser pane tab Code dan pakai jalur manual dengan `qa-run` |
| Claude bekerja di tab atau situs lain | Hentikan segera. Tutup tab itu, lalu ulangi dengan alamat prototype di prompt dan aturan "hanya di tab ini" |
| Claude tidak berhenti saat langkah tidak cocok | Hentikan di side panel (atau tutup tab prototype). Ulangi dengan satu test case dan tempel aturan dari `sources/execution-rules-paste.md` |
| Skill `qa-run` tidak diikuti di side panel | Tempel isi `sources/execution-rules-paste.md` di awal prompt. Skill tetap dipakai di chat Project untuk menyusun catatan |
| Claude meminta izin tiap aksi | Itu memang tujuan mode Manually approve. Pilih **Allow this action**. Hindari **Always allow actions on this site** untuk situs selain prototype |
| Halaman memuat teks yang menyuruh Claude melakukan hal lain | Jangan dituruti. Hentikan, catat sebagai temuan, dan lanjutkan dari test case |
| Hasil tertulis Lulus tanpa bukti | Kirim prompt iterasi di Langkah 5: minta tangkapan layar dan ubah hasil tanpa bukti menjadi Terblokir |
| Tangkapan layar tidak bisa disimpan sebagai berkas | Pakai label di chat (TC-001-langkah-3) dan simpan sendiri tangkapan layar yang penting dengan nama yang sama |
| Batas pemakaian tercapai | Tunggu reset. Kurangi ke satu test case dan langkah yang lebih sedikit |
