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
* 🛡️ [`technical/04-trd-security-qr-offline.md`](./technical/04-trd-security-qr-offline.md) — [TRD] Kriptografi token QR (HMAC-SHA256), validasi geofencing anti-kloning, dan arsitektur Offline-First (Flutter SQLite/Hive & PWA Outbox Queue).

---

## 👥 Matriks Peran Pengguna (Roles)

1. **Petugas Lapangan (Cleaning Service / Waste Porter):** Antarmuka **Mobile App (Flutter)** untuk scan QR ruangan instan via kamera, isi form checklist, input timbangan limbah, dan simpan offline di area tanpa sinyal.
2. **Sanitarian / Auditor Lingkungan:** Antarmuka **Web Admin Dashboard** untuk verifikasi hasil audit, input uji lab kualitas air/udara, pengawasan kepatuhan, dan approval tiket temuan.
3. **Tim Pemeliharaan Sarana / IPSRS:** Antarmuka **Web Dashboard & Mobile** untuk menerima disposisi tiket perbaikan sarana ruangan dan memperbarui status progres pengerjaan.
4. **Manajemen / Direksi Faskes:** Antarmuka **Web Dashboard** untuk memantau ringkasan kepatuhan fasilitas, status TPS, serta mengunduh dokumen laporan berkala.

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

### 1. Prinsip Utama: *Zero Documentation Drift*
Dalam ekosistem dokumentasi multi-tier SEHS (**Master PRD $\rightarrow$ Feature PRD $\rightarrow$ DRA Database $\rightarrow$ TRD API Contracts**):
- **Tidak ada dokumen yang berdiri sendiri (*No isolated island*).**
- Setiap perubahan aturan bisnis di tingkat PRD **wajib diselaraskan secara kaskade (*cascade update*)** ke dokumen hilir yang mengonsumsinya serta spesifikasi teknis di folder `technical/`.
- Prosedur tata kelola lengkap diatur dalam skill: [`.agents/skills/change-impact-synchronizer/SKILL.md`](./.agents/skills/change-impact-synchronizer/SKILL.md).

---

### 2. Alur 4 Langkah Menangani Request Enhancement dari Klien

Jika klien faskes atau manajemen mengajukan perubahan aturan, alur kerja baru, atau penambahan fitur (*enhancement*):

```mermaid
flowchart TD
    ClientReq([Permintaan Enhancement Klien]) --> Step1[1. Perbarui PRD Modul Asal & Tambah Kode Aturan BR-*]
    Step1 --> Step2[2. Lacak Dokumen Terdampak via Consumed By & Graphify]
    Step2 --> Step3A[3A. Update PRD Hilir Terkait]
    Step2 --> Step3B[3B. Update Skema DB di DRA]
    Step2 --> Step3C[3C. Update Payload REST API di TRD]
    Step3A & Step3B & Step3C --> Step4[4. Jalankan /save-progress & Git Commit]
```

1. **Langkah 1: Perbarui Dokumen Asal (Hulu)**
   * Buka PRD modul terkait di `features/`.
   * Tambahkan klausul aturan bisnis baru dengan ID unik (misal: `BR-MD04-06`, `BR-OP01-12`).
   * Naikkan nomor versi dokumen (misal: `v1.0.0` $\rightarrow$ `v1.1.0`).
2. **Langkah 2: Lacak Dokumen yang Terdampak (*Impact Analysis*)**
   * Periksa baris metadata `Consumed By (Dampak)` di bagian atas PRD asal.
   * Gunakan AI & Graphify untuk menemukan dependensi tersembunyi:
     ```bash
     graphify query "Apa saja alur, tabel DB, dan API yang terdampak oleh perubahan pada [Nama Fitur]?"
     ```
3. **Langkah 3: Eksekusi *Cascade Update* ke Dokumen Terkait**
   * **Di PRD Hilir:** Sesuaikan alur pengguna dan validasi input.
   * **Di DRA (`technical/01-dra-*.md`):** Tambahkan kolom baru, tipe data, foreign key, atau enum di tabel database dengan komentar referensi aturan bisnis (`-- Implements BR-XX-YY`).
   * **Di TRD (`technical/02-trd-*.md` s/d `04-trd-*.md`):** Tambahkan field pada request/response DTO JSON dan kode error baru.
4. **Langkah 4: Simpan Progres & Sinkronkan Knowledge Graph**
   * Jalankan perintah `/save-progress` untuk memperbarui [`PROGRESS.md`](./PROGRESS.md), menyinkronkan graf Graphify, dan membuat commit git.

---

### 3. Contoh Prompt Cepat untuk Menjalankan Enhancement dengan AI

Anda tidak perlu melakukan penelusuran manual satu per satu. Anda cukup memberikan perintah terarah kepada asisten AI:

> *"Bro, ada request enhancement dari klien: [Sebutkan permintaan fitur/aturan baru]. Tolong lakukan cascade update mulai dari PRD modul asal, dokumen hilir terkait, skema DRA database, hingga kontrak endpoint TRD API."*

Asisten AI akan secara otomatis:
1. Memicu skill `change-impact-synchronizer`.
2. Melacak seluruh rantai dependensi dari hulu ke hilir.
3. Melakukan editing berkas secara presisi tanpa merusak aturan arsitektur lainnya.
4. Menampilkan laporan daftar berkas yang telah diselaraskan.

---

### 4. Titik Simpan Sesi Kerja (*Session Checkpoint*)
* **Jalankan Slash Command:** Setiap kali selesai bekerja atau sebelum menutup IDE, ketik `/save-progress` atau perintahkan *"save progress bro"*.
* **Status Progres Proyek:** Pantau status penyelesaian seluruh modul dan rencana kerja di [`PROGRESS.md`](./PROGRESS.md).



