# Graph Report - sehs-docs  (2026-09-14)

## Corpus Check
- Corpus is ~2,750 words - fits in a single context window. You may not need a graph.

## Summary
- 22 nodes · 25 edges · 5 communities
- Extraction: 92% EXTRACTED · 8% INFERRED · 0% AMBIGUOUS · INFERRED: 2 edges (avg confidence: 0.95)
- Token cost: 2,750 input · 1,200 output

## Community Hubs (Navigation)
- Sanitasi Lingkungan & Pengelolaan Limbah
- Arsitektur Inti & Standar Mutu Faskes
- Dashboard Manajemen & Analitik Eksekutif
- Operasional Lapangan & Inspeksi QR Mobile
- Sistem Tiket Temuan & Penanganan Sarana

## God Nodes (most connected - your core abstractions)
1. `Smart Environment Health System (SEHS)` - 8 edges
2. `Modul Temuan & Alur Tindak Lanjut (Ticketing)` - 5 edges
3. `Modul Checklist Kebersihan QR` - 4 edges
4. `Modul Monitoring Limbah & TPS` - 4 edges
5. `Modul Sanitasi & Kualitas Lingkungan` - 4 edges
6. `Modul Dashboard Eksekutif & Laporan` - 4 edges
7. `Role Sanitarian / Auditor Lingkungan` - 3 edges
8. `Role Petugas Lapangan (Cleaning Service / Porter)` - 2 edges
9. `Mobile-First Web / PWA App` - 2 edges
10. `SEHS Documentation Hub` - 2 edges

## Surprising Connections (you probably didn't know these)
- `SEHS Documentation Hub` --references--> `Smart Environment Health System (SEHS)`  [EXTRACTED]
  README.md → 00-MASTER-PRD.md

## Hyperedges (group relationships)
- **RBAC Stakeholder Personas** — 00_master_prd_role_petugas_lapangan, 00_master_prd_role_sanitarian, 00_master_prd_role_ipsrs, 00_master_prd_role_manajemen [EXTRACTED 1.00]
- **Five Core Modules of SEHS** — 00_master_prd_modul_checklist_qr, 00_master_prd_modul_limbah, 00_master_prd_modul_sanitasi_kualitas, 00_master_prd_modul_temuan_tindak_lanjut, 00_master_prd_modul_dashboard_laporan [EXTRACTED 1.00]

## Communities (5 total, 0 thin omitted)

### Community 0 - "Sanitasi Lingkungan & Pengelolaan Limbah"
Cohesion: 0.33
Nodes (6): Monitoring Kualitas Air (pH, TDS, E.coli), Monitoring Kualitas Udara (PM2.5, Suhu, RH, ACH), Modul Monitoring Limbah & TPS, Modul Sanitasi & Kualitas Lingkungan, Role Sanitarian / Auditor Lingkungan, Tempat Penampungan Sementara (TPS) Limbah B3

### Community 1 - "Arsitektur Inti & Standar Mutu Faskes"
Cohesion: 0.40
Nodes (5): Audit Trail & Immutability Data, Pencegahan Infeksi Nosokomial (HAIs), Smart Environment Health System (SEHS), SEHS Documentation Hub, Modular PRD Hierarchy (Master & Feature PRDs)

### Community 2 - "Dashboard Manajemen & Analitik Eksekutif"
Cohesion: 0.50
Nodes (4): Desktop Web Admin & Dashboard, KPI Kepatuhan Audit (>= 95%), Modul Dashboard Eksekutif & Laporan, Role Manajemen & Direksi Faskes

### Community 3 - "Operasional Lapangan & Inspeksi QR Mobile"
Cohesion: 0.50
Nodes (4): Modul Checklist Kebersihan QR, Offline-Resilience & Client-Side Caching, Mobile-First Web / PWA App, Role Petugas Lapangan (Cleaning Service / Porter)

### Community 4 - "Sistem Tiket Temuan & Penanganan Sarana"
Cohesion: 0.67
Nodes (3): KPI MTTR Insiden High (< 4 jam), Modul Temuan & Alur Tindak Lanjut (Ticketing), Role Teknisi IPSRS / Pemeliharaan Sarana

## Knowledge Gaps
- **9 isolated node(s):** `Pencegahan Infeksi Nosokomial (HAIs)`, `Role Teknisi IPSRS / Pemeliharaan Sarana`, `Role Manajemen & Direksi Faskes`, `Tempat Penampungan Sementara (TPS) Limbah B3`, `Monitoring Kualitas Air (pH, TDS, E.coli)` (+4 more)
  These have ≤1 connection - possible missing edges or undocumented components. (Counts symbols only; 12 node(s) total have ≤1 connection when file, concept and rationale nodes are included.)

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `Smart Environment Health System (SEHS)` connect `Arsitektur Inti & Standar Mutu Faskes` to `Sanitasi Lingkungan & Pengelolaan Limbah`, `Dashboard Manajemen & Analitik Eksekutif`, `Operasional Lapangan & Inspeksi QR Mobile`, `Sistem Tiket Temuan & Penanganan Sarana`?**
  _High betweenness centrality (0.712) - this node is a cross-community bridge._
- **Why does `Modul Dashboard Eksekutif & Laporan` connect `Dashboard Manajemen & Analitik Eksekutif` to `Arsitektur Inti & Standar Mutu Faskes`?**
  _High betweenness centrality (0.271) - this node is a cross-community bridge._
- **Why does `Modul Checklist Kebersihan QR` connect `Operasional Lapangan & Inspeksi QR Mobile` to `Arsitektur Inti & Standar Mutu Faskes`, `Sistem Tiket Temuan & Penanganan Sarana`?**
  _High betweenness centrality (0.221) - this node is a cross-community bridge._
- **What connects `Pencegahan Infeksi Nosokomial (HAIs)`, `Role Teknisi IPSRS / Pemeliharaan Sarana`, `Role Manajemen & Direksi Faskes` to the rest of the system?**
  _9 weakly-connected nodes found - possible documentation gaps or missing edges._