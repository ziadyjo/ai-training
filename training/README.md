# Claude AI Training: Hands-on Repository

Repository hands-on untuk **Claude AI Training** (Claude for Product Teams: Analysis, Design & Testing). Satu studi kasus dipakai di semua sesi: **WebTM: Role & User Management**.

## Cara memakai

1. Clone repository ini ke laptopmu sebelum Sesi 1.
2. Buka folder sesi yang sedang berjalan. Tiap folder punya `README.md` yang menjelaskan isinya.
3. Ikuti slide sesi tersebut. Langkah dan prompt ada di berkas langkah di folder hands-on yang sedang berjalan (misalnya `session-1/hands-on-1/03-complete-starter.md`). Kriteria lulus, troubleshooting, scorecard, dan glosarium ada di `README.md` hands-on dan di folder sesinya.

## Struktur

```
training/
├── session-1/                Skills, Projects, BRD dan gap analysis
│   ├── hands-on-1/           Build Requirement Review & BRD Skill
│   ├── hands-on-2/           Requirement Gap Analysis
│   └── hands-on-3/           Standardized BRD & Skill Refinement
├── session-2/                Connectors, process flow, dan UI mockup
│   ├── hands-on-1/           Requirement-to-Process Flow
│   └── hands-on-2/           Requirement-to-UI Design Exploration
├── session-3/                HTML prototype, backlog, dan progress brief
│   ├── hands-on-1/           Design-to-Code Development
│   ├── hands-on-2/           Project Planning & Backlog Development
│   └── hands-on-3/           Scheduled Project Progress Brief
└── session-4/                Test case dan agentic testing
    ├── hands-on-1/           Test Case Skill & Test Case Development
    └── hands-on-2/           Agentic Test Execution & Documentation
```

Tiap folder hands-on memuat langkah dan prompt siap salin, serta `sources/` dengan berkas yang dipakai di hands-on itu. Berkas pendukung seperti `scorecard.md` dan `glossary.md` ada di folder sesinya.

## Prinsip kerja selama training

1. Hasil AI berbeda tiap kali dijalankan. Iterasi itu normal.
2. Beri feedback spesifik dan referensi, lalu simpan pelajarannya ke Skill atau Instructions Project.
3. Satu Project untuk satu produk atau modul. Jangan campur konteks.
4. Draft dulu di chat, baru eksekusi lewat connector.
5. Kamu yang menyetujui sebelum dokumen inti (BRD, flow, backlog) diubah.
6. Pilih model sesuai pekerjaan.

## Persiapan sebelum Sesi 1

Instruktur membagikan daftar persiapan terpisah: akun Claude, akun Google, salinan template BRD, dan Claude Code terpasang (dipakai di Hands-on #2 Sesi 2 lewat terminal; di Sesi 3 bisa lewat tab Code di aplikasi Claude desktop). Browser yang dipakai di Sesi 4 adalah Google Chrome. Pastikan repository ini sudah ter-clone dan folder `session-1/` bisa kamu buka.
