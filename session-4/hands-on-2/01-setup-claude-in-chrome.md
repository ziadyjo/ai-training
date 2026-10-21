# Langkah 1: Siapkan Claude in Chrome, izin, dan prototype

Durasi ±15 menit. Claude in Chrome menjalankan Claude di dalam browsermu, jadi yang pertama kamu atur adalah siapa yang boleh melakukan apa. Kamu membatasi situs, memilih mode persetujuan yang paling ketat, dan baru setelah itu membuka prototype.

## Yang dikerjakan

1. Pakai Google Chrome. Disarankan satu profil terpisah tanpa login ke akun kerja, bank, atau layanan pribadi: Claude bekerja dengan status login browser yang dipakai.
2. Pasang ekstensi dari [Chrome Web Store](https://chromewebstore.google.com/detail/claude/fcoeoabgfenejglbffodgkkbkcdhcgfn): **Add to Chrome**, masuk dengan akun Claude yang sama dengan aplikasi, lalu pin ekstensinya.
3. Klik ikon Claude di toolbar untuk membuka side panel. Di drop-down pada kotak input pilih mode **Manually approve**, supaya Claude meminta izin untuk tiap aksi.
4. Buka prototype-mu di tab Chrome: tarik `index.html` ke jendela Chrome, atau **File**, **Open File**. Alamatnya diawali `file://`.
5. Kirim prompt cek koneksi di bawah ke side panel. Claude hanya boleh membaca dan menjawab.
6. Bila Claude menjawab tidak bisa mengakses halaman: buka `chrome://extensions`, pilih **Detail** pada ekstensi Claude, aktifkan **Allow access to file URLs**, lalu muat ulang tab. Bila tetap gagal: buka `index.html` di Browser pane tab Code, jalankan langkah sendiri, dan pakai jalur manual dengan `qa-run`.

Claude in Chrome juga bisa dinyalakan dari aplikasi Claude desktop (**Settings**, **Connectors**, Claude in Chrome). Itu jalur alternatif: langkah dan aturannya sama.

## Prompt (kirim ke side panel)

```
CONTEXT
Tab aktif adalah prototype WebTM untuk pengujian.

TASK
Sebutkan judul halaman, tombol, dan tabel yang terlihat di tab ini. Jangan melakukan apa pun selain membaca.

RULES
- Jangan klik, ketik, atau berpindah halaman.
- Jangan membuka tab atau situs lain.

OUTPUT FORMAT
Daftar bernomor: judul halaman, tombol, kolom tabel.
```

## Cek

- Ekstensi Claude terpasang dan side panel terbuka di tab prototype.
- Mode persetujuan tertulis **Manually approve**.
- Claude menyebut elemen yang benar-benar ada di prototype (mis. Create New Role dan kolom Role ID, Role Name).
- Tidak ada aksi yang dijalankan di halaman.

---

Berikutnya: [Langkah 2: Pasang qa-run dan pilih test case](02-setup-qa-run-pick-test-case.md)
