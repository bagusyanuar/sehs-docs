# Graph Report - sehs-docs  (2026-09-14)

## Corpus Check
- 25 files · ~25,347 words
- Verdict: corpus is large enough that graph structure adds value.
- Unclassified: 2 file(s) not represented in the graph (top: (none) 2)

## Summary
- 359 nodes · 404 edges · 24 communities (23 shown, 1 thin omitted)
- Extraction: 100% EXTRACTED · 0% INFERRED · 0% AMBIGUOUS
- Token cost: 0 input · 0 output

## Graph Freshness
- Built from commit: `8cb7410f`
- Run `git rev-parse HEAD` and compare to check if the graph is stale.
- Run `graphify update .` after code changes (no API cost).

## Community Hubs (Navigation)
- Smart Environment Health System (SEHS)
- Feature PRD: Autentikasi & Manajemen Pengguna (Auth & User)
- Smart Environment Health System (SEHS) — Documentation Hub
- 3. Spesifikasi Skema Database PostgreSQL (DDL)
- 3. Spesifikasi Endpoint REST API
- Technical Requirements Document (TRD): Keamanan QR Code, Anti-Kloning & Arsitektur Offline-First (Flutter & PWA)
- PROGRESS.md
- 3. Spesifikasi Endpoint per Klaster Bisnis
- workflows/graphify.md
- Business-Centric PRD Scaffolder Skill
- 2. Standards for DRA (Database Architecture & ERD)
- Feature PRD: Master Data Fasilitas, Ruangan & Cetak QR Code
- Feature PRD: Master Data Limbah, TPS & Vendor Transporter
- Feature PRD: Master Data Baku Mutu Sanitasi Air & Udara
- Feature PRD: Master Data Organisasi & Shift Kerja
- Feature PRD: Master Data Standar Checklist & Template Audit
- Feature PRD: Master Data Kategori Temuan & Standar SLA
- SEHS Documentation Project — Progress & Checkpoint Tracker
- 2. Standard 4-Step Cascade Update Workflow
- Langkah-Langkah Eksekusi Otomatis
- Issue Task Scaffolder Skill
- Langkah-Langkah Eksekusi Otomatis
- 🎫 Panduan Penerbitan & Pembaruan Tiket Tugas (GitHub Issues untuk BE, FE-WEB & FE-MOBILE)
- frontend-web-task.md

## God Nodes (most connected - your core abstractions)
1. `Smart Environment Health System (SEHS)` - 11 edges
2. `Feature PRD: Autentikasi & Manajemen Pengguna (Auth & User)` - 9 edges
3. `Feature PRD: Master Data Fasilitas, Ruangan & Cetak QR Code` - 9 edges
4. `Feature PRD: Master Data Limbah, TPS & Vendor Transporter` - 9 edges
5. `Feature PRD: Master Data Baku Mutu Sanitasi Air & Udara` - 9 edges
6. `Feature PRD: Master Data Organisasi & Shift Kerja` - 9 edges
7. `Feature PRD: Master Data Standar Checklist & Template Audit` - 9 edges
8. `Feature PRD: Master Data Kategori Temuan & Standar SLA` - 9 edges
9. `3. Spesifikasi Skema Database PostgreSQL (DDL)` - 9 edges
10. `Technical Requirements Document (TRD): Keamanan QR Code, Anti-Kloning & Arsitektur Offline-First (Flutter & PWA)` - 8 edges

## Surprising Connections (you probably didn't know these)
- None detected - all connections are within the same source files.

## Communities (24 total, 1 thin omitted)

### Community 0 - "Smart Environment Health System (SEHS)"
Cohesion: 0.08
Nodes (24): 10. Indeks Rincian Feature PRD, 1. Metadata Dokumen, 2.1 Konteks Masalah, 2.2 Visi & Solusi Produk, 2. Latar Belakang & Problem Statement, 3. Matriks Peran Pengguna (Role-Based Access Control / RBAC), 4.1 Modul 1: Checklist Kebersihan Berbasis QR Code, 4.2 Modul 2: Monitoring & Pengelolaan Limbah (Waste Tracking) (+16 more)

### Community 1 - "Feature PRD: Autentikasi & Manajemen Pengguna (Auth & User)"
Cohesion: 0.11
Nodes (19): 1. Metadata Dokumen, 2.1 Masalah Nyata di Fasilitas Kesehatan, 2.2 Nilai Bisnis & Manfaat Sistem, 2. Latar Belakang & Masalah Bisnis, 3. Persona Pengguna & Konteks Operasional, 4.1 Alur Masuk Kerja Petugas Lapangan (Mobile PWA), 4.2 Alur Pergantian Shift Kerja (Shift Handover), 4. Alur Pengalaman Pengguna (User Journey) (+11 more)

### Community 2 - "Smart Environment Health System (SEHS) — Documentation Hub"
Cohesion: 0.11
Nodes (18): 1. Membuka Visualisasi Graf Interaktif, 1. Prinsip Utama: *Zero Documentation Drift*, 2. Alur 4 Langkah Menangani Request Enhancement dari Klien, 2. Berinteraksi & Query Graf dengan AI, 3. Contoh Prompt Cepat untuk Menjalankan Enhancement dengan AI, 3. Memperbarui Graf Setelah Menambah/Mengubah Dokumen, 4. File Output Graphify (`graphify-out/`), 4. Titik Simpan Sesi Kerja (*Session Checkpoint*) (+10 more)

### Community 3 - "3. Spesifikasi Skema Database PostgreSQL (DDL)"
Cohesion: 0.07
Nodes (28): 1. Metadata Dokumen, 2. Diagram Hubungan Entitas (Entity-Relationship Diagram / ERD), 3.1 Domain & Enum Global, 3.2 Klaster Fondasi Identitas (Auth & User), 3.3 Klaster 1: Organisasi & Shift Kerja, 3.4 Klaster 2: Fasilitas, Ruangan & QR Code, 3.5 Klaster 3: Standar Checklist & Template Audit, 3.6 Klaster 4: Limbah, TPS & Vendor Transporter (+20 more)

### Community 4 - "3. Spesifikasi Endpoint REST API"
Cohesion: 0.07
Nodes (28): 1. Metadata Dokumen, 2. Arsitektur Komponen & Diagram Alur Teknis, 3.1 `POST /api/v1/auth/login-field`, 3.2 `POST /api/v1/auth/login-web`, 3.3 `POST /api/v1/auth/refresh`, 3.4 `POST /api/v1/auth/logout`, 3.5 `PUT /api/v1/auth/change-pin`, 3.6 `POST /api/v1/admin/users/:id/reset-pin` (+20 more)

### Community 5 - "Technical Requirements Document (TRD): Keamanan QR Code, Anti-Kloning & Arsitektur Offline-First (Flutter & PWA)"
Cohesion: 0.08
Nodes (25): 1. Metadata Dokumen, 1. Store: `cached_templates`, 2. Latar Belakang & Masalah Arsitektur, 2. Store: `outbox_queue`, 3.1 Struktur Muatan Token QR Fisik Ruangan (*Static Door QR*), 3.2 Rumus Perhitungan HMAC-SHA256 Server, 3. Arsitektur Kriptografi & Format QR Code, 3. Store: `offline_photos` (+17 more)

### Community 6 - "PROGRESS.md"
Cohesion: 0.18
Nodes (10): Master Product Requirements Document (PRD), graphify, 🎯 1. Objective, 📚 2. Dokumen Acuan (Single Source of Truth), 🛠️ 3. Scope of Work (Tugas Teknis), ✅ 4. Definition of Done (DoD), 🎯 1. Objective & Target Persona, 📚 2. Dokumen Acuan (Single Source of Truth) (+2 more)

### Community 7 - "3. Spesifikasi Endpoint per Klaster Bisnis"
Cohesion: 0.09
Nodes (22): 1. Metadata Dokumen, 2. Standar Global API Master Data, 3.1 Klaster 1: Organisasi & Shift Kerja, 3.2 Klaster 2: Lokasi, Ruangan & Cetak QR Code, 3.3 Klaster 3: Standar Checklist & Template Audit, 3.4 Klaster 4: Limbah, TPS & Vendor Transporter, 3.5 Klaster 5: Baku Mutu Sanitasi Air & Udara, 3.6 Klaster 6: Kategori Temuan & Standar SLA (+14 more)

### Community 9 - "Business-Centric PRD Scaffolder Skill"
Cohesion: 0.33
Nodes (5): Business-Centric PRD Scaffolder Skill, Core Philosophy: "WHAT & WHY", Not "HOW", Mandatory Focus in PRDs:, Standard Template Structure for Feature PRDs, Strictly Prohibited in PRDs:

### Community 10 - "2. Standards for DRA (Database Architecture & ERD)"
Cohesion: 0.12
Nodes (15): 1. Core Principles of Technical Documentation, 2.1 Universal Audit Trail (Wajib di Setiap Tabel), 2.2 Relational Integrity & Deletion Policy, 2.3 Strict Data Type Conventions, 2.4 Indexing Strategy, 2.5 Mermaid ERD Standard, 2. Standards for DRA (Database Architecture & ERD), 3.1 Standard Response Envelope (+7 more)

### Community 11 - "Feature PRD: Master Data Fasilitas, Ruangan & Cetak QR Code"
Cohesion: 0.14
Nodes (14): 1. Metadata Dokumen, 2.1 Masalah Nyata di Fasilitas Kesehatan, 2.2 Nilai Bisnis yang Dihasilkan, 2. Latar Belakang & Masalah Bisnis, 3. Persona Pengguna & Konteks Penggunaan, 4. Alur Kerja Pengelolaan (Core User Journey), 5.1 Fitur 1: Manajemen Gedung & Lantai, 5.2 Fitur 2: Manajemen Ruangan & Klasifikasi Risiko Infeksi (+6 more)

### Community 12 - "Feature PRD: Master Data Limbah, TPS & Vendor Transporter"
Cohesion: 0.14
Nodes (14): 1. Metadata Dokumen, 2.1 Masalah Nyata di Fasilitas Kesehatan, 2.2 Nilai Bisnis yang Dihasilkan, 2. Latar Belakang & Masalah Bisnis, 3. Persona Pengguna & Konteks Penggunaan, 4. Alur Kerja Pengelolaan (Core User Journey), 5.1 Fitur 1: Manajemen Kategori & Jenis Limbah, 5.2 Fitur 2: Manajemen Tempat Penampungan Sementara (TPS) (+6 more)

### Community 13 - "Feature PRD: Master Data Baku Mutu Sanitasi Air & Udara"
Cohesion: 0.14
Nodes (14): 1. Metadata Dokumen, 2.1 Masalah Nyata di Fasilitas Kesehatan, 2.2 Nilai Bisnis yang Dihasilkan, 2. Latar Belakang & Masalah Bisnis, 3. Persona Pengguna & Konteks Penggunaan, 4. Alur Kerja Pengelolaan (Core User Journey), 5.1 Fitur 1: Manajemen Baku Mutu Kualitas Air, 5.2 Fitur 2: Manajemen Baku Mutu Kualitas Udara Indoor (+6 more)

### Community 14 - "Feature PRD: Master Data Organisasi & Shift Kerja"
Cohesion: 0.15
Nodes (13): 1. Metadata Dokumen, 2.1 Masalah Nyata di Fasilitas Kesehatan, 2.2 Nilai Bisnis yang Dihasilkan, 2. Latar Belakang & Masalah Bisnis, 3. Persona Pengguna & Konteks Penggunaan, 4. Alur Kerja Pengelolaan (Core User Journey), 5.1 Fitur 1: Manajemen Master Unit / Instalasi, 5.2 Fitur 2: Manajemen Master Shift Kerja (+5 more)

### Community 15 - "Feature PRD: Master Data Standar Checklist & Template Audit"
Cohesion: 0.15
Nodes (13): 1. Metadata Dokumen, 2.1 Masalah Nyata di Fasilitas Kesehatan, 2.2 Nilai Bisnis yang Dihasilkan, 2. Latar Belakang & Masalah Bisnis, 3. Persona Pengguna & Konteks Penggunaan, 4. Alur Kerja Pengelolaan (Core User Journey), 5.1 Fitur 1: Pustaka Indikator & Butir Kebersihan, 5.2 Fitur 2: Manajemen Template Formulir per Tipe Ruangan (+5 more)

### Community 16 - "Feature PRD: Master Data Kategori Temuan & Standar SLA"
Cohesion: 0.15
Nodes (13): 1. Metadata Dokumen, 2.1 Masalah Nyata di Fasilitas Kesehatan, 2.2 Nilai Bisnis yang Dihasilkan, 2. Latar Belakang & Masalah Bisnis, 3. Persona Pengguna & Konteks Penggunaan, 4. Alur Kerja Pengelolaan (Core User Journey), 5.1 Fitur 1: Manajemen Kategori & Sub-Kategori Temuan, 5.2 Fitur 2: Manajemen Tingkat Urgensi & Standar SLA (Service Level Agreement) (+5 more)

### Community 17 - "SEHS Documentation Project — Progress & Checkpoint Tracker"
Cohesion: 0.20
Nodes (10): 1. Tata Kelola & Aturan Arsitektur (`.agents/` & `.github/`), 2. Dokumen Induk & Fondasi Identitas, 3. Master Data PRD (6 Klaster / 15 Fitur Bisnis Lengkap), 4. Arsitektur Teknis & Kontrak API (`technical/`), 🎯 Antrean Pengerjaan Besok (Next Action Items: Fase 2), 🔑 Aturan Penting yang Wajib Dipertahankan (Invariants), 💡 Cara Memulai Kembali Sesi Besok (Resume Prompt), ✅ Deliverables yang Sudah Selesai (Completed - 100%) (+2 more)

### Community 18 - "2. Standard 4-Step Cascade Update Workflow"
Cohesion: 0.22
Nodes (9): 1. The Core Philosophy: "Zero Documentation Drift", 2. Standard 4-Step Cascade Update Workflow, 3. Aturan Pemetaan Kode Aturan Bisnis (Traceability ID), 4. Checklist Kesiapan Penyelarasan (Verification Gate), Change Impact Synchronizer & Traceability Skill, Langkah 1: Identifikasi & Update Dokumen Asal, Langkah 2: Lacak Dampak (Impact Traceability Analysis), Langkah 3: Eksekusi Cascade Update (Penyelarasan Hilir) (+1 more)

### Community 19 - "Langkah-Langkah Eksekusi Otomatis"
Cohesion: 0.22
Nodes (8): 1. Periksa Status Berkas & Perubahan Sesi Ini, 2. Perbarui Dokumen Pelacak (`PROGRESS.md`), 3. Sinkronkan Hub Navigasi (`README.md`), 4. Sinkronisasikan Knowledge Graph (Graphify), 5. Buat Titik Simpan Git (Commit), 6. Berikan Laporan Penutup ke Pengguna, Langkah-Langkah Eksekusi Otomatis, Workflow: /save-progress

### Community 20 - "Issue Task Scaffolder Skill"
Cohesion: 0.25
Nodes (8): 1. Core Principles of Issue Scaffolding, 2.1 Backend Issue Format (`[BE]`), 2.2 Frontend Web Issue Format (`[FE-WEB]`), 2.3 Frontend Mobile Flutter Issue Format (`[FE-MOBILE]`), 2. Standard Issue Structure, 3. GitHub CLI (`gh`) Command Generation, 4. Verification Gate, Issue Task Scaffolder Skill

### Community 21 - "Langkah-Langkah Eksekusi Otomatis"
Cohesion: 0.25
Nodes (7): 1. Identifikasi Modul & Peran Target, 2. Kumpulkan Konteks Dokumen, 3. Susun Isi Tiket Sesuai Template, 4. Terbitkan Tiket via GitHub CLI (`gh`), 5. Laporkan Tautan Tiket ke Pengguna, Langkah-Langkah Eksekusi Otomatis, Workflow: /publish-issue

### Community 22 - "🎫 Panduan Penerbitan & Pembaruan Tiket Tugas (GitHub Issues untuk BE, FE-WEB & FE-MOBILE)"
Cohesion: 0.17
Nodes (12): 1. Tiga Kategori Tiket Resmi, 2. Cara Menerbitkan Tiket via AI (Otomatis), 3. Cara Menerbitkan Tiket via GitHub CLI (`gh`) Secara Manual, 4. Cara Meng-update atau Menambah Lingkup pada Tiket yang Sudah Ada, 5. Cara Mengonsumsi Tiket Saat Mulai Coding, 6. Otomatisasi Lintas Repositori (Cross-Repo Auto-Close via PR), A. Melalui Perintah Asisten AI (Paling Praktis), B. Melalui Terminal GitHub CLI (`gh`) (+4 more)

### Community 23 - "frontend-web-task.md"
Cohesion: 0.40
Nodes (4): 🎯 1. Objective & Target Persona, 📚 2. Dokumen Acuan (Single Source of Truth), 🛠️ 3. Scope of Work (Tugas Teknis), ✅ 4. Definition of Done (DoD)

## Knowledge Gaps
- **248 isolated node(s):** `📌 Status Terkini (Current State Snapshot)`, `1. Tata Kelola & Aturan Arsitektur (`.agents/` & `.github/`)`, `2. Dokumen Induk & Fondasi Identitas`, `3. Master Data PRD (6 Klaster / 15 Fitur Bisnis Lengkap)`, `4. Arsitektur Teknis & Kontrak API (`technical/`)` (+243 more)
  These have ≤1 connection - possible missing edges or undocumented components. (Counts symbols only; 249 node(s) total have ≤1 connection when file, concept and rationale nodes are included.)
- **1 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `Smart Environment Health System (SEHS) — Documentation Hub` connect `Smart Environment Health System (SEHS) — Documentation Hub` to `PROGRESS.md`, `🎫 Panduan Penerbitan & Pembaruan Tiket Tugas (GitHub Issues untuk BE, FE-WEB & FE-MOBILE)`?**
  _High betweenness centrality (0.153) - this node is a cross-community bridge._
- **Why does `Technical Requirements Document (TRD): API Autentikasi & Manajemen Sesi` connect `3. Spesifikasi Endpoint REST API` to `PROGRESS.md`?**
  _High betweenness centrality (0.141) - this node is a cross-community bridge._
- **Why does `Data Requirements Architecture (DRA): Database Schema & ERD Master Data & Auth` connect `3. Spesifikasi Skema Database PostgreSQL (DDL)` to `PROGRESS.md`?**
  _High betweenness centrality (0.140) - this node is a cross-community bridge._
- **What connects `📌 Status Terkini (Current State Snapshot)`, `1. Tata Kelola & Aturan Arsitektur (`.agents/` & `.github/`)`, `2. Dokumen Induk & Fondasi Identitas` to the rest of the system?**
  _248 weakly-connected nodes found - possible documentation gaps or missing edges._
- **Should `Smart Environment Health System (SEHS)` be split into smaller, more focused modules?**
  _Cohesion score 0.08333333333333333 - nodes in this community are weakly interconnected._
- **Should `Feature PRD: Autentikasi & Manajemen Pengguna (Auth & User)` be split into smaller, more focused modules?**
  _Cohesion score 0.10526315789473684 - nodes in this community are weakly interconnected._
- **Should `Smart Environment Health System (SEHS) — Documentation Hub` be split into smaller, more focused modules?**
  _Cohesion score 0.1111111111111111 - nodes in this community are weakly interconnected._