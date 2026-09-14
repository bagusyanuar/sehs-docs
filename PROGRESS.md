# SEHS Documentation Project — Progress & Checkpoint Tracker

Dokumen ini berfungsi sebagai **State Checkpoint & Persistent Memory** untuk melacak status pengerjaan seluruh dokumentasi arsitektur **Smart Environment Health System (SEHS)**. Siapapun agent/manusia yang membuka sesi kerja baru wajib membaca file ini terlebih dahulu untuk mengetahui konteks pengerjaan terakhir dan daftar tugas berikutnya.

---

## 📌 Status Terkini (Current State Snapshot)

* **Tanggal Pembaruan Terakhir:** 14 September 2026
* **Milestone Aktif Saat Ini:** **Fase 1 (Fondasi Master Data, Autentikasi & Arsitektur Teknis) — SELESAI (100%)**
* **Milestone Berikutnya:** **Fase 2 (Modul Transaksi Operasional Harian Lapangan) — ANTRIAN BESOK**
* **Integritas Knowledge Graph (Graphify):** Tersinkronisasi

---

## ✅ Deliverables yang Sudah Selesai (Completed - 100%)

### 1. Tata Kelola & Aturan Arsitektur (`.agents/` & `.github/`)
- [x] [`.agents/rules/graphify.md`](./.agents/rules/graphify.md) — Aturan hemat & efisien pembaruan graf (hanya saat push/checkpoint).
- [x] [`.agents/skills/business-prd-scaffolder/SKILL.md`](./.agents/skills/business-prd-scaffolder/SKILL.md) — Format PRD murni bisnis ("WHAT & WHY", no engineering leaks, mandatory depends_on/consumed_by).
- [x] [`.agents/skills/trd-dra-scaffolder/SKILL.md`](./.agents/skills/trd-dra-scaffolder/SKILL.md) — Format DRA PostgreSQL 15+, envelope REST API, matriks scoping global vs split, dan Offline PWA.
- [x] [`.agents/skills/change-impact-synchronizer/SKILL.md`](./.agents/skills/change-impact-synchronizer/SKILL.md) — SOP 4-langkah Zero Documentation Drift saat terjadi revisi modul.
- [x] [`.agents/skills/issue-task-scaffolder/SKILL.md`](./.agents/skills/issue-task-scaffolder/SKILL.md) — Framework perakitan tiket tugas GitHub Issue untuk tim BE & FE.
- [x] [`.agents/workflows/save-progress.md`](./.agents/workflows/save-progress.md) — Workflow checkpoint otomatis akhir sesi (`/save-progress`).
- [x] [`.agents/workflows/publish-issue.md`](./.agents/workflows/publish-issue.md) — Workflow penerbitan tiket tugas GitHub Issue via `gh` CLI (`/publish-issue`).
- [x] [`.github/ISSUE_TEMPLATE/backend-task.md`](./.github/ISSUE_TEMPLATE/backend-task.md) — Template GitHub Issue untuk tugas Backend.
- [x] [`.github/ISSUE_TEMPLATE/frontend-web-task.md`](./.github/ISSUE_TEMPLATE/frontend-web-task.md) — Template GitHub Issue untuk Web Admin Dashboard (React/Vue/Next).
- [x] [`.github/ISSUE_TEMPLATE/frontend-mobile-task.md`](./.github/ISSUE_TEMPLATE/frontend-mobile-task.md) — Template GitHub Issue untuk Mobile App Flutter (Keypad NIK+PIN, SQLite/Hive, Camera Scanner).

### 2. Dokumen Induk & Fondasi Identitas
- [x] [`README.md`](./README.md) — Hub dokumentasi, navigasi modul, RBAC matriks, panduan Graphify, dan status pengerjaan.
- [x] [`00-MASTER-PRD.md`](./00-MASTER-PRD.md) — Master PRD sistem (5 pilar, arsitektur modul, NFR, roadmap).
- [x] [`features/01-prd-auth-user.md`](./features/01-prd-auth-user.md) — Dual-UX login (Mobile NIK+PIN untuk petugas lapangan & Web Email+Password untuk admin/sanitarian), sesi shift 8 jam terikat jadwal aktif, 11 aturan bisnis.

### 3. Master Data PRD (6 Klaster / 15 Fitur Bisnis Lengkap)
- [x] [`features/master-data/01-md-organisasi-shift.md`](./features/master-data/01-md-organisasi-shift.md) — Fitur 1 (Unit/Instalasi) & Fitur 2 (Shift Kerja & Toleransi Handover 30 Menit).
- [x] [`features/master-data/02-md-fasilitas-ruangan-qr.md`](./features/master-data/02-md-fasilitas-ruangan-qr.md) — Fitur 3 (Gedung/Lantai), Fitur 4 (Ruangan & Zonasi Risiko Infeksi), Fitur 5 (Generator & Cetak Stiker QR PDF).
- [x] [`features/master-data/03-md-standar-checklist.md`](./features/master-data/03-md-standar-checklist.md) — Fitur 6 (Pustaka Indikator Kebersihan) & Fitur 7 (Template Checklist Ruangan, Bobot Nilai, Passing Grade).
- [x] [`features/master-data/04-md-limbah-tps-vendor.md`](./features/master-data/04-md-limbah-tps-vendor.md) — Fitur 8 (Kategori Limbah B3/Domestik & Warna Wadah), Fitur 9 (Kapasitas TPS, Alarm 80%, Batas Simpan 48 Jam), Fitur 10 (Vendor Transporter & Izin KLHK).
- [x] [`features/master-data/05-md-baku-mutu-air-udara.md`](./features/master-data/05-md-baku-mutu-air-udara.md) — Fitur 11 (Baku Mutu Air), Fitur 12 (Baku Mutu Udara per Zona Risiko), Fitur 13 (Titik Uji Sampling Rutin).
- [x] [`features/master-data/06-md-kategori-temuan-sla.md`](./features/master-data/06-md-kategori-temuan-sla.md) — Fitur 14 (Kategori Masalah: Cleaning/IPSRS/B3) & Fitur 15 (Tingkat Urgensi & Hitung Mundur SLA).

### 4. Arsitektur Teknis & Kontrak API (`technical/`)
- [x] [`technical/01-dra-database-erd-master-auth.md`](./technical/01-dra-database-erd-master-auth.md) — [DRA] Skema PostgreSQL 15+ (11 enum, 17 tabel, universal audit trail 5 kolom, soft delete, indexes, dan Mermaid ERD).
- [x] [`technical/02-trd-auth-session-api.md`](./technical/02-trd-auth-session-api.md) — [TRD] REST API Autentikasi NIK+PIN mobile, Web login, Argon2id, JWT RS256, Refresh Token Rotation, dan mitigasi brute-force.
- [x] [`technical/03-trd-master-data-api.md`](./technical/03-trd-master-data-api.md) — [TRD] REST API CRUD untuk 6 klaster Master Data.
- [x] [`technical/04-trd-security-qr-offline.md`](./technical/04-trd-security-qr-offline.md) — [TRD] Kriptografi token QR (HMAC-SHA256), validasi geofencing anti-kloning, dan arsitektur Offline-First PWA (IndexedDB Outbox Queue + Service Worker Sync).

---

## 🎯 Antrean Pengerjaan Besok (Next Action Items: Fase 2)

Besok kita akan menyusun **Modul Transaksi Operasional Harian Lapangan** (`features/operational/`) satu per satu:

1. ⏳ **`features/operational/01-prd-checklist-kebersihan-qr.md`**
   - *Cakupan Bisnis:* Alur scan QR pintu oleh Cleaning Service, validasi live camera, form checklist dinamis per ruangan, skor kelulusan, penanganan fatal items, submit offline saat tidak ada sinyal.
2. ⏳ **`features/operational/02-prd-monitoring-limbah.md`**
   - *Cakupan Bisnis:* Log timbangan limbah B3/domestik dari ruangan, serah terima ke TPS B3 oleh Porter, warning kuota TPS 80%, batas waktu simpan 48 jam, dan manifes penyerahan limbah ke vendor transporter KLHK.
3. ⏳ **`features/operational/03-prd-sanitasi-kualitas-lingkungan.md`**
   - *Cakupan Bisnis:* Input hasil uji lab berkala kualitas air (fisika, kimia, mikrobiologi E. coli) dan udara ruang operasi/ICU, deteksi otomatis parameter anomali di luar baku mutu Permenkes, dan notifikasi peringatan dini.
4. ⏳ **`features/operational/04-prd-temuan-tindak-lanjut.md`**
   - *Cakupan Bisnis:* Pelaporan kerusakan fasilitas saat inspeksi (kran bocor, stopkontak rusak), disposisi otomatis ke tim IPSRS atau Cleaning, upload foto Before & After, pelacakan countdown SLA, serta verifikasi approval Sanitarian.
5. ⏳ **`features/operational/05-prd-dashboard-laporan.md`**
   - *Cakupan Bisnis:* Executive dashboard untuk Direksi & Sanitarian, ringkasan kepatuhan ruangan, neraca limbah B3 faskes, matriks kepatuhan SLA IPSRS, dan ekspor laporan berkala akreditasi Kemenkes/KARS (PDF/Excel).

---

## 🔑 Aturan Penting yang Wajib Dipertahankan (Invariants)

1. **Format PRD Bisnis Murni:** Tidak boleh ada JSON schema, kode hash enkripsi, query database, atau tabel endpoint API di dalam folder `features/`. PRD hanya memuat alur kerja pengguna, aturan bisnis (`BR-*`), dan kriteria penerimaan.
2. **Metadata Ketergantungan Wajib:** Setiap dokumen PRD & TRD harus memiliki baris metadata `Depends On (Prasyarat)` dan `Consumed By (Dampak)`.
3. **Standar DRA Database:** PostgreSQL 15+, UUID v4, 5 kolom audit universal (`id`, `created_at`, `updated_at`, `created_by`, `deleted_at`), `ON DELETE RESTRICT`, `DECIMAL(10,2)` untuk berat/pengukuran.
4. **Scoping Pemisahan:** DRA diglobalkan per milestone, TRD di-split modular per klaster domain API.

---

## 💡 Cara Memulai Kembali Sesi Besok (Resume Prompt)

Saat Anda membuka sesi baru besok, cukup ketik pesan singkat berikut:

> *"Halo bro, tolong baca `PROGRESS.md` dan kita mulai eksekusi Modul Operasional 01: `01-prd-checklist-kebersihan-qr.md`."*
