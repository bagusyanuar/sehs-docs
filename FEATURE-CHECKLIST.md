# Smart Environment Health System (SEHS) — Master Feature & Implementation Checklist

Dokumen ini memuat daftar periksa (*checklist*) komprehensif seluruh fitur, spesifikasi arsitektur dokumen (PRD, DRA, TRD), serta status implementasi teknis lintas platform (**Backend Go**, **Frontend Mobile Flutter**, dan **Frontend Web Admin**).

---

## 📊 Status Ringkas Keseluruhan (High-Level Summary)

| Milestone / Layer | Status Dokumen | Backend (BE) | Mobile App (FE) | Web Admin (FE) |
| :--- | :---: | :---: | :---: | :---: |
| **Fase 1: Master Data & Autentikasi** | 🟢 100% Selesai | 🟡 Sedang Berjalan (Setup & Auth) | ⚪ Belum Mulai | ⚪ Belum Mulai |
| **Fase 2: Operasional Harian Lapangan** | ⏳ Antrean (0%) | ⚪ Menunggu Dokumen | ⚪ Menunggu Dokumen | ⚪ Menunggu Dokumen |
| **Fase 3: Pelaporan, Dashboard & Ekspor** | ⚪ Backlog | ⚪ Menunggu Dokumen | ⚪ Menunggu Dokumen | ⚪ Menunggu Dokumen |

---

## 🏢 FASE 1: Fondasi Master Data & Autentikasi

### 1. Spesifikasi Dokumen Arsitektur
- [x] [`.agents/rules/graphify.md`](./.agents/rules/graphify.md) — Aturan hemat & efisien pembaruan graf (hanya saat push/checkpoint).
- [x] [`.agents/skills/business-prd-scaffolder/SKILL.md`](./.agents/skills/business-prd-scaffolder/SKILL.md) — Format PRD murni bisnis ("WHAT & WHY", no engineering leaks).
- [x] [`.agents/skills/trd-dra-scaffolder/SKILL.md`](./.agents/skills/trd-dra-scaffolder/SKILL.md) — Standar DRA PostgreSQL 15+, envelope REST API, matriks global vs split.
- [x] [`.agents/skills/change-impact-synchronizer/SKILL.md`](./.agents/skills/change-impact-synchronizer/SKILL.md) — SOP Zero Documentation Drift saat revisi modul.
- [x] [`.agents/skills/issue-task-scaffolder/SKILL.md`](./.agents/skills/issue-task-scaffolder/SKILL.md) — Framework perakitan tiket tugas GitHub Issue BE & FE.
- [x] [`00-MASTER-PRD.md`](./00-MASTER-PRD.md) — Master PRD sistem (5 pilar, arsitektur modul, NFR, roadmap).
- [x] [`features/01-prd-auth-user.md`](./features/01-prd-auth-user.md) — Dual-UX login (Mobile NIK+PIN untuk petugas lapangan & Web Email+Password untuk admin/sanitarian).
- [x] [`features/master-data/01-md-organisasi-shift.md`](./features/master-data/01-md-organisasi-shift.md) — Unit faskes, shift kerja Pagi/Siang/Malam, toleransi handover 30 menit.
- [x] [`features/master-data/02-md-fasilitas-ruangan-qr.md`](./features/master-data/02-md-fasilitas-ruangan-qr.md) — Gedung, lantai, ruangan, zonasi risiko infeksi, dan generator stiker QR PDF.
- [x] [`features/master-data/03-md-standar-checklist.md`](./features/master-data/03-md-standar-checklist.md) — Pustaka indikator kebersihan, template checklist ruangan, bobot nilai, passing grade.
- [x] [`features/master-data/04-md-limbah-tps-vendor.md`](./features/master-data/04-md-limbah-tps-vendor.md) — Kategori limbah B3/domestik, kapasitas TPS 80%, batas simpan 48 jam, vendor KLHK.
- [x] [`features/master-data/05-md-baku-mutu-air-udara.md`](./features/master-data/05-md-baku-mutu-air-udara.md) — Baku mutu Permenkes air & udara per zona risiko, titik uji sampling rutin.
- [x] [`features/master-data/06-md-kategori-temuan-sla.md`](./features/master-data/06-md-kategori-temuan-sla.md) — Kategori masalah (Cleaning/IPSRS/B3), tingkat urgensi, hitung mundur SLA.
- [x] [`technical/01-dra-database-erd-master-auth.md`](./technical/01-dra-database-erd-master-auth.md) — Skema PostgreSQL 15+ (11 enum, 17 tabel master data, audit trail 5 kolom, indexes).
- [x] [`technical/02-trd-auth-session-api.md`](./technical/02-trd-auth-session-api.md) — REST API Auth NIK+PIN mobile, Web login, Argon2id, JWT RS256, Refresh Token Rotation.
- [x] [`technical/03-trd-master-data-api.md`](./technical/03-trd-master-data-api.md) — REST API CRUD untuk 6 klaster Master Data.
- [x] [`technical/04-trd-security-qr-offline.md`](./technical/04-trd-security-qr-offline.md) — Kriptografi token QR (HMAC-SHA256), geofencing, arsitektur Offline-First PWA/Mobile Sync.

### 2. Implementasi Teknis Fase 1
#### A. Backend (sehs-be)
- [ ] Migrasi Database DDL (11 enum, 17 tabel Master Data & Auth).
- [ ] Modul Auth: Login NIK+PIN Mobile (Argon2id).
- [ ] Modul Auth: Login Email+Password Web (Argon2id).
- [ ] Modul Auth: JWT Access Token & Refresh Token Rotation.
- [ ] Modul Auth: Middleware RBAC (FIELD_OFFICER, SANITARIAN, TECHNICIAN, MANAGEMENT).
- [ ] CRUD API: Unit Faskes & Shift Kerja (`/api/v1/units`, `/api/v1/shifts`).
- [ ] CRUD API: Fasilitas Gedung, Lantai & Ruangan (`/api/v1/rooms`).
- [ ] Service API: Generator Token HMAC & Stiker QR Ruangan PDF (`/api/v1/rooms/:id/qr-code`).
- [ ] CRUD API: Pustaka Indikator & Template Checklist (`/api/v1/checklist-templates`).
- [ ] CRUD API: Kategori Limbah, TPS B3 & Vendor Transporter (`/api/v1/waste-categories`, `/api/v1/tps-locations`, `/api/v1/waste-vendors`).
- [ ] CRUD API: Baku Mutu Air, Udara & Titik Sampling (`/api/v1/quality-standards`, `/api/v1/sampling-points`).
- [ ] CRUD API: Kategori Temuan & Pengaturan SLA (`/api/v1/finding-categories`).

#### B. Frontend Mobile (sehs-mobile - Flutter)
- [ ] Desain Layar Login NIK + Virtual Keypad PIN.
- [ ] Modul Penyimpanan Token Aman (Flutter Secure Storage).
- [ ] Modul State Management Sesi Pengguna & Shift Aktif.

#### C. Frontend Web Admin (sehs-web - React / Next.js)
- [ ] Desain Layar Login Web (Email & Password).
- [ ] Antarmuka CRUD Master Data (Formulir Unit, Shift, Gedung, Ruangan).
- [ ] Fitur Preview & Download PDF Stiker QR Ruangan Siap Cetak.
- [ ] Antarmuka Builder Template Checklist (Drag-and-drop / selector indikator & bobot).
- [ ] Antarmuka Manajemen TPS, Vendor KLHK, Standar Baku Mutu, dan Matriks SLA.

---

## 🚀 FASE 2: Modul Transaksi Operasional Harian Lapangan (IN QUEUE)

### 1. 📱 Modul 01: Checklist Kebersihan Ruangan Berbasis QR
*Dokumen Target: `features/operational/01-prd-checklist-kebersihan-qr.md`*

| No | Kode Fitur | Rincian Fitur Bisnis | Status Dokumen | Status BE | Status Mobile | Status Web |
| :---: | :--- | :--- | :---: | :---: | :---: | :---: |
| 1 | **FEAT-OP01-01** | Scanner Kamera QR Ruangan & Verifikasi Kehadiran Fisik | ⏳ In Queue | ⚪ Todo | ⚪ Todo | — |
| 2 | **FEAT-OP01-02** | Generator Form Checklist Dinamis per Tipe Ruangan | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |
| 3 | **FEAT-OP01-03** | Input Respon Checklist (Pass/Fail vs Skala 1-5 + Bukti Foto) | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |
| 4 | **FEAT-OP01-04** | Engine Kalkulasi Skor Kepatuhan & Passing Grade | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |
| 5 | **FEAT-OP01-05** | Mekanisme "Fatal Items" (Auto-Fail jika ada limbah B3/jarum tercecer) | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |
| 6 | **FEAT-OP01-06** | Mode Offline-First (Penyimpanan Lokal & Sync Otomatis saat Online) | ⏳ In Queue | ⚪ Todo | ⚪ Todo | — |
| 7 | **FEAT-OP01-07** | Dual-Mode Inspeksi: Rutinitas Cleaning Service vs Audit Sanitarian | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |
| 8 | **FEAT-OP01-08** | Integrasi Langsung ke Tiket Temuan jika Checklist Gagal / Rusak | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |

---

### 2. ⚖️ Modul 02: Monitoring & Pengelolaan Limbah (Waste Tracking)
*Dokumen Target: `features/operational/02-prd-monitoring-limbah.md`*

| No | Kode Fitur | Rincian Fitur Bisnis | Status Dokumen | Status BE | Status Mobile | Status Web |
| :---: | :--- | :--- | :---: | :---: | :---: | :---: |
| 1 | **FEAT-OP02-01** | Pencatatan Log Timbangan Limbah per Ruangan oleh Porter (Kg & Kantong) | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |
| 2 | **FEAT-OP02-02** | Serah Terima Limbah ke TPS B3 & Verifikasi Penerimaan Petugas TPS | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |
| 3 | **FEAT-OP02-03** | Monitoring Okupansi Kapasitas TPS Real-Time & Warning Ambang 80% | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |
| 4 | **FEAT-OP02-04** | Countdown & Alarm Masa Simpan Limbah B3 (Maksimal 48 Jam) | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |
| 5 | **FEAT-OP02-05** | Manifes Digital Penyerahan Limbah B3 ke Vendor Transporter KLHK | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |
| 6 | **FEAT-OP02-06** | Pencatatan Berita Acara & Tanda Tangan Digital Pengangkutan Limbah | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |

---

### 3. 🧪 Modul 03: Sanitasi & Kualitas Lingkungan Fisik
*Dokumen Target: `features/operational/03-prd-sanitasi-kualitas-lingkungan.md`*

| No | Kode Fitur | Rincian Fitur Bisnis | Status Dokumen | Status BE | Status Mobile | Status Web |
| :---: | :--- | :--- | :---: | :---: | :---: | :---: |
| 1 | **FEAT-OP03-01** | Input Hasil Uji Lab Kualitas Air Bersih & Minum (Fisika, Kimia, E. coli) | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |
| 2 | **FEAT-OP03-02** | Input Hasil Uji Kualitas Udara Ruangan (PM2.5, PM10, Suhu, Kelembaban, ACH) | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |
| 3 | **FEAT-OP03-03** | Ingestion & Integrasi Sensor IoT Lingkungan (Webhook / MQTT) | ⏳ In Queue | ⚪ Todo | — | ⚪ Todo |
| 4 | **FEAT-OP03-04** | Evaluasi Otomatis Kesesuaian Baku Mutu (Status: Hijau / Kuning / Merah) | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |
| 5 | **FEAT-OP03-05** | Notifikasi Peringatan Dini Parameter Tercemar / Melebihi Batas Aman | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |

---

### 4. 🛠️ Modul 04: Temuan Kerusakan / Insiden & Alur Tiket Tindak Lanjut (CAPA)
*Dokumen Target: `features/operational/04-prd-temuan-tindak-lanjut.md`*

| No | Kode Fitur | Rincian Fitur Bisnis | Status Dokumen | Status BE | Status Mobile | Status Web |
| :---: | :--- | :--- | :---: | :---: | :---: | :---: |
| 1 | **FEAT-OP04-01** | Pelaporan Temuan Instan (Inline Checklist atau Laporan Ad-hoc Lapangan) | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |
| 2 | **FEAT-OP04-02** | Form Tiket Temuan: Kategori, Bukti Foto *Before*, Lokasi Ruangan & Urgensi | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |
| 3 | **FEAT-OP04-03** | Routing & Disposisi Otomatis ke Tim Terkait (Cleaning Service / IPSRS) | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |
| 4 | **FEAT-OP04-04** | Pelacakan Jam Hitung Mundur SLA Penyelesaian Tiket | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |
| 5 | **FEAT-OP04-05** | Penyelesaian Tiket oleh Teknisi: Catatan Kerja, Komponen & Foto *After* | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |
| 6 | **FEAT-OP04-06** | Verifikasi Akhir & Approval Closing Tiket oleh Sanitarian / Penanggung Jawab | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |

---

### 5. 📊 Modul 05: Jadwal Kegiatan & Dashboard Eksekutif
*Dokumen Target: `features/operational/05-prd-dashboard-laporan.md`*

| No | Kode Fitur | Rincian Fitur Bisnis | Status Dokumen | Status BE | Status Mobile | Status Web |
| :---: | :--- | :--- | :---: | :---: | :---: | :---: |
| 1 | **FEAT-OP05-01** | Kalender Terpadu Jadwal Sanitasi (Fogging, Kuras Tandon, Angkut B3) | ⏳ In Queue | ⚪ Todo | ⚪ Todo | ⚪ Todo |
| 2 | **FEAT-OP05-02** | Executive KPI Dashboard: % Kepatuhan Kebersihan, Okupansi TPS, SLA MTTR | ⏳ In Queue | ⚪ Todo | — | ⚪ Todo |
| 3 | **FEAT-OP05-03** | Peta Interaktif & Heatmap Kepatuhan Fasilitas per Gedung / Lantai | ⏳ In Queue | ⚪ Todo | — | ⚪ Todo |
| 4 | **FEAT-OP05-04** | Rekap Otomatis Neraca Limbah B3 Faskes (Masuk vs Keluar vs Sisa TPS) | ⏳ In Queue | ⚪ Todo | — | ⚪ Todo |
| 5 | **FEAT-OP05-05** | Generator & Ekspor Laporan Resmi Akreditasi Kemenkes / KARS & DLH (PDF & Excel) | ⏳ In Queue | ⚪ Todo | — | ⚪ Todo |

---

## 🗄️ Dokumen Arsitektur Teknis Transaksi (Menyusul Pasca-PRD Fase 2)
- [ ] `technical/05-dra-database-erd-transactional.md` — DDL skema transaksi (tabel checklist_sessions, checklist_answers, waste_logs, tps_transactions, lab_test_results, incident_tickets, ticket_actions).
- [ ] `technical/06-trd-operational-checklist-api.md` — REST API sesi checklist & validasi token QR.
- [ ] `technical/07-trd-waste-environmental-api.md` — REST API timbangan limbah & input lab uji sanitasi.
- [ ] `technical/08-trd-tickets-reporting-api.md` — REST API tiket temuan IPSRS, SLA tracking, dan agregasi analitik dashboard.

---

## 🧭 Panduan Eksekusi Berikutnya

Langkah paling tepat selanjutnya adalah memulai perancangan dokumen:
👉 **`features/operational/01-prd-checklist-kebersihan-qr.md`**

Setelah dokumen PRD Modul 01 disepakati:
1. Sinkronkan ke Knowledge Graph dengan `/save-progress`.
2. Generate tiket tugas BE & FE dengan workflow `/publish-issue`.
3. Lanjutkan implementasi kode di repo Backend (`sehs-be`) & Frontend (`sehs-mobile` / `sehs-web`).
