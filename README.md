# Smart Environment Health System (SEHS) — Documentation Hub

Selamat datang di repositori dokumentasi resmi sistem **Smart Environment Health System (SEHS)**. Sistem ini dirancang untuk mendigitalisasi, memantau, dan mengelola operasional kesehatan lingkungan dan sanitasi secara terintegrasi dan *real-time*, khususnya pada fasilitas pelayanan kesehatan (Rumah Sakit, Klinik, dan Laboratorium).

---

## 📌 Navigasi Dokumentasi

Dokumentasi ini disusun menggunakan pendekatan **Modular Product Documentation (Master PRD & Feature PRDs)** agar mudah dipahami oleh manajemen, product manager, UI/UX designer, software engineer, dan tim QA.

```text
sehs-docs/
├── README.md                                  # Halaman panduan utama (Anda berada di sini)
├── 00-MASTER-PRD.md                           # Dokumen Induk (Global Product Requirement Document)
├── PROGRESS.md                                # Status pengerjaan, checkpoint sesi & roadmap harian
└── features/                                  # Rincian spesifikasi detail per modul (Feature PRD)
    ├── 01-prd-auth-user.md                    # Fondasi Identitas: Autentikasi NIK+PIN / Web Login
    │
    ├── master-data/                           # FONDASI DATA INDUK FASILITAS (PER KLASTER)
    │   ├── 01-md-organisasi-shift.md          # Klaster 1: Unit Departemen & Jam Shift Kerja
    │   ├── 02-md-fasilitas-ruangan-qr.md      # Klaster 2: Gedung, Ruangan & Cetak Stiker QR
    │   ├── 03-md-standar-checklist.md         # Klaster 3: Pustaka Indikator & Template Audit
    │   ├── 04-md-limbah-tps-vendor.md         # Klaster 4: Kategori Limbah B3, Kuota TPS & Vendor
    │   ├── 05-md-baku-mutu-air-udara.md       # Klaster 5: Standar Baku Mutu Permenkes Air & Udara
    │   └── 06-md-kategori-temuan-sla.md       # Klaster 6: Kategori Insiden & Batas Waktu SLA
    │
    └── operational/                           # TRANSAKSI OPERASIONAL HARIAN
        ├── 01-prd-checklist-kebersihan-qr.md  # Modul 1: Checklist Ruangan & Validasi QR Code
        ├── 02-prd-monitoring-limbah.md        # Modul 2: Pelacakan Limbah B3, Domestik & TPS
        ├── 03-prd-sanitasi-kualitas-lingkungan.md # Modul 3: Pemantauan Kualitas Air & Udara
        ├── 04-prd-temuan-tindak-lanjut.md     # Modul 4: Pelaporan Insiden & Tiket Perbaikan
        └── 05-prd-dashboard-laporan.md        # Modul 5: Executive Dashboard & Laporan Kepatuhan
│
└── technical/                                 # SPESIFIKASI TEKNIS & ARSITEKTUR (DRA & TRD)
    ├── 01-dra-database-erd-master-auth.md     # Skema Database PostgreSQL 15+, Relasi FK & Mermaid ERD
    ├── 02-trd-auth-session-api.md             # Kontrak REST API Autentikasi NIK+PIN, Web Login & Sesi
    ├── 03-trd-master-data-api.md              # Kontrak REST API Master Data Fasilitas & Standar
    └── 04-trd-security-qr-offline.md          # Keamanan Token QR Anti-Kloning & Offline PWA Sync
```

---

## 🚀 Ringkasan Modul & Klaster PRD

### A. Fondasi Identitas & Akses
* 📄 [`features/01-prd-auth-user.md`](./features/01-prd-auth-user.md) — Dual-UX login (Mobile NIK+PIN untuk petugas lapangan & Web Email+Password untuk kantor/direksi), sesi shift 8 jam stabil.

### B. Fondasi Data Induk (Master Data Clusters)
* 🏢 [`features/master-data/01-md-organisasi-shift.md`](./features/master-data/01-md-organisasi-shift.md) — Pengelolaan unit faskes, shift kerja Pagi/Siang/Malam, dan aturan handover.
* 📍 [`features/master-data/02-md-fasilitas-ruangan-qr.md`](./features/master-data/02-md-fasilitas-ruangan-qr.md) — Hierarki gedung, inventaris ruangan, zonasi risiko infeksi, dan generator PDF stiker QR code siap cetak.
* 📋 [`features/master-data/03-md-standar-checklist.md`](./features/master-data/03-md-standar-checklist.md) — Pustaka indikator kebersihan, perakitan template form per tipe ruangan, bobot nilai, dan passing grade kelulusan.
* ☣️ [`features/master-data/04-md-limbah-tps-vendor.md`](./features/master-data/04-md-limbah-tps-vendor.md) — Kategori limbah B3 medis/domestik, kuota TPS, ambang waktu simpan maks 48 jam, dan legalitas vendor transporter KLHK.
* 💧 [`features/master-data/05-md-baku-mutu-air-udara.md`](./features/master-data/05-md-baku-mutu-air-udara.md) — Standar baku mutu Permenkes untuk air (pH, TDS, E.coli) dan udara ruangan (suhu, RH, ACH), serta titik uji sampling.
* ⚠️ [`features/master-data/06-md-kategori-temuan-sla.md`](./features/master-data/06-md-kategori-temuan-sla.md) — Klasifikasi masalah fasilitas, disposisi tim (Cleaning vs IPSRS), dan jam hitung mundur SLA penyelesaian tiket.

### C. Modul Transaksi Operasional & Analitik
* 📱 [`features/operational/01-prd-checklist-kebersihan-qr.md`](./features/operational/01-prd-checklist-kebersihan-qr.md) — Validasi fisik kehadiran via scan QR pintu, form inspeksi dinamis, dan kalkulasi kepatuhan.
* ⚖️ [`features/operational/02-prd-monitoring-limbah.md`](./features/operational/02-prd-monitoring-limbah.md) — Log timbangan limbah ruangan, kapasitas TPS real-time, dan manifes serah terima vendor.
* 🧪 [`features/operational/03-prd-sanitasi-kualitas-lingkungan.md`](./features/operational/03-prd-sanitasi-kualitas-lingkungan.md) — Form uji lab berkala & penerimaan data sensor fisik lingkungan.
* 🛠️ [`features/operational/04-prd-temuan-tindak-lanjut.md`](./features/operational/04-prd-temuan-tindak-lanjut.md) — Alur pelaporan kerusakan sarana, upload foto Before/After, pelacakan SLA, dan approval Sanitarian.
* 📊 [`features/operational/05-prd-dashboard-laporan.md`](./features/operational/05-prd-dashboard-laporan.md) — Visualisasi analitik eksekutif, rekap kepatuhan faskes, neraca limbah B3, dan ekspor laporan akreditasi.

### D. Spesifikasi Arsitektur Teknis (DRA & TRD)
* 🗄️ [`technical/01-dra-database-erd-master-auth.md`](./technical/01-dra-database-erd-master-auth.md) — [DRA] Skema relasional PostgreSQL 15+ (11 enum, 17 tabel, audit trail universal, soft delete, indexes, dan Mermaid ERD).
* 🔐 [`technical/02-trd-auth-session-api.md`](./technical/02-trd-auth-session-api.md) — [TRD] REST API Autentikasi NIK+PIN mobile, Web login, Argon2id, JWT RS256, Refresh Token Rotation, dan mitigasi brute-force.
* 🌐 [`technical/03-trd-master-data-api.md`](./technical/03-trd-master-data-api.md) — [TRD] REST API CRUD untuk 6 klaster Master Data (Unit, Shift, Ruangan, QR Generator, Checklist, Limbah, Standar Mutu, SLA).
* 🛡️ [`technical/04-trd-security-qr-offline.md`](./technical/04-trd-security-qr-offline.md) — [TRD] Kriptografi token QR (HMAC-SHA256), validasi geofencing anti-kloning, dan arsitektur Offline-First PWA (IndexedDB Outbox Queue + Service Worker Sync).

---

## 👥 Matriks Peran Pengguna (Roles)

1. **Petugas Lapangan (Cleaning Service / Waste Porter):** Antarmuka Mobile Web/PWA untuk scan QR ruangan, isi checklist, input timbangan limbah, dan lapor temuan cepat.
2. **Sanitarian / Auditor Lingkungan:** Antarmuka Web untuk verifikasi hasil audit, input uji lab kualitas air/udara, pengawasan kepatuhan, dan approval tiket temuan.
3. **Tim Pemeliharaan Sarana / IPSRS:** Antarmuka Web/Mobile untuk menerima disposisi tiket perbaikan sarana ruangan dan memperbarui status progres pengerjaan.
4. **Manajemen / Direksi Faskes:** Antarmuka Web Dashboard untuk memantau ringkasan kepatuhan fasilitas, status TPS, serta mengunduh dokumen laporan berkala.

---

## 🧠 Second Brain & Knowledge Graph (Graphify)

Repositori ini telah terintegrasi dengan **Graphify** sebagai *Second Brain* dan *Knowledge Graph* persisten. Graphify memetakan seluruh modul, peran pengguna, alur proses, dan konsep arsitektur ke dalam graf relasi (*Nodes & Edges*), sehingga AI assistant dan tim developer dapat menavigasi struktur sistem tanpa kehilangan konteks.

### 1. Membuka Visualisasi Graf Interaktif
Visualisasi graf interaktif tersedia di [`graphify-out/graph.html`](./graphify-out/graph.html). Anda dapat membukanya langsung di browser tanpa perlu menjalankan web server:

* **Di macOS (Terminal):**
  ```bash
  open graphify-out/graph.html
  ```
* **Fitur Visualizer:**
  * **Search & Inspect:** Cari entitas (misal: `Checklist`, `Limbah B3`, `IPSRS`) di kolom pencarian sebelah kanan untuk melihat tetangga relasinya (*connected neighbors*).
  * **Color Clusters:** Node dikelompokkan otomatis berdasarkan komunitas pengetahuan (*Sanitasi*, *Inspeksi Lapangan*, *Dashboard Eksekutif*, dll.).
  * **Interactive Physics:** Node dapat digeser, diperbesar (*zoom in/out*), dan difilter per komunitas.

### 2. Berinteraksi & Query Graf dengan AI
Anda dapat memanfaatkan graf pengetahuan ini langsung di terminal atau melalui prompt asisten AI:

* **Mencari Jawaban Terkait Relasi Arsitektur:**
  ```bash
  graphify query "Bagaimana alur checklist QR terhubung dengan sistem tiket temuan IPSRS?"
  ```
* **Melihat Jalur Hubungan Terpendek Antar-Konsep:**
  ```bash
  graphify path "00_master_prd_modul_checklist_qr" "00_master_prd_kpi_mttr"
  ```
* **Melihat Penjelasan Detail Suatu Node:**
  ```bash
  graphify explain "00_master_prd_tps_limbah"
  ```

### 3. Memperbarui Graf Setelah Menambah/Mengubah Dokumen
Setiap kali Anda membuat atau memperbarui file Feature PRD di folder `features/`, perbarui graf pengetahuan dengan perintah:

```bash
# Update inkremental (hanya memproses dokumen baru/berubah)
graphify update .

# Atau generate ulang secara penuh
graphify extract .
graphify export html
```

### 4. File Output Graphify (`graphify-out/`)
* **[`graphify-out/graph.html`](./graphify-out/graph.html):** Visual graf interaktif untuk browser.
* **[`graphify-out/GRAPH_REPORT.md`](./graphify-out/GRAPH_REPORT.md):** Laporan analisis jaringan, *God Nodes*, kohesi komunitas, dan pertanyaan arsitektur kunci.
* **[`graphify-out/graph.json`](./graphify-out/graph.json):** Data mentah graf untuk kebutuhan konsumsi AI dan GraphRAG.

---

## 📖 Panduan Kontribusi & Manajemen Perubahan (Change Management)
- **Filosofi Zero Documentation Drift:** Setiap kali ada perubahan aturan bisnis di suatu PRD, seluruh dokumen hilir yang tertera pada baris `Consumed By (Dampak)` dan dokumen teknis terkait di `technical/` **wajib diselaraskan secara kaskade (*cascade update*)**.
- **SOP Penyelarasan:** Prosedur lengkap pelacakan dan sinkronisasi perubahan diatur dalam skill: [`.agents/skills/change-impact-synchronizer/SKILL.md`](./.agents/skills/change-impact-synchronizer/SKILL.md).
- **Semua Perubahan Strategis Global:** Wajib diselaraskan di [`00-MASTER-PRD.md`](./00-MASTER-PRD.md).
- **Titik Simpan Akhir Sesi (`/save-progress`):** Setiap kali ingin mengakhiri sesi pengerjaan, jalankan slash command `/save-progress` atau perintahkan *"save progress"* agar sistem memperbarui [`PROGRESS.md`](./PROGRESS.md), menyinkronkan graf Graphify, dan membuat checkpoint commit git.
- **Penyelarasan Knowledge Graph:** Jalankan `graphify update .` ketika hendak melakukan `git push` ke GitHub agar visual graf tetap sinkron dengan versi dokumen terbaru.


