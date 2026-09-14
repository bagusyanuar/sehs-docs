---
name: trd-dra-scaffolder
description: "Framework and architectural standards for scaffolding Technical Requirements Documents (TRD) and Data Requirements Architecture (DRA) specifications. Enforces PostgreSQL best practices, strict relational constraints, universal audit trails, precise decimal types, RESTful API envelope standardization, and bidirectional traceability to PRD business rules."
---

# TRD & DRA Scaffolder Skill

Standardized framework for creating production-ready, enterprise-grade **Technical Requirements Documents (TRD)** and **Data Requirements Architecture (DRA)** for the **Smart Environment Health System (SEHS)**.

---

## 1. Core Principles of Technical Documentation

Technical specifications translate business requirements from the PRD into concrete, unambiguous engineering blueprints for Backend Engineers, DBAs, Frontend Engineers, and DevOps.

* **DRA (Data Requirements Architecture):** Focuses on the *Logical & Physical Data Model* (ERD, DDL PostgreSQL, constraints, indexing, and data retention).
  * **Scoping Rule:** **DIGLOBALKAN PER MILESTONE BESAR.** Database relasional memerlukan integritas Foreign Key dan satu diagram ERD utuh agar tidak tercerai-berai.
* **TRD (Technical Requirements Document):** Focuses on the *Software Architecture & API Contracts* (RESTful endpoints, DTO payloads, security mechanisms, caching, and infrastructure).
  * **Scoping Rule:** **DI-SPLIT PER KLASTER / DOMAIN API.** Setiap domain (Auth, Master Data, Operasional) memiliki dokumen TRD tersendiri agar dokumentasi payload JSON tidak menumpuk ribuan baris di satu file.
* **Bidirectional Traceability:** Every database column, constraint, and API endpoint MUST explicitly trace back to a business rule in the corresponding PRD using its ID (e.g., `-- Implements BR-MD04-03`).

---

## 2. Standards for DRA (Database Architecture & ERD)

All DRA documents MUST comply with the following PostgreSQL standards:

### 2.1 Universal Audit Trail (Wajib di Setiap Tabel)
Every entity table MUST include these five standard columns:
```sql
id          UUID PRIMARY KEY DEFAULT gen_random_uuid(),
created_at  TIMESTAMPTZ NOT NULL DEFAULT NOW(),
updated_at  TIMESTAMPTZ NOT NULL DEFAULT NOW(),
created_by  UUID NULL REFERENCES users(id) ON DELETE RESTRICT,
deleted_at  TIMESTAMPTZ NULL -- Soft delete untuk menjaga rekam jejak akreditasi
```

### 2.2 Relational Integrity & Deletion Policy
* **Foreign Keys:** MUST use `ON DELETE RESTRICT` (or `ON DELETE NO ACTION`). Hard cascade deletes (`ON DELETE CASCADE`) are **strictly prohibited** on historical operational data to prevent accidental erasure of hospital audit logs.
* **Soft Deletes:** Deletion of master data (e.g., room, user, waste category) sets `deleted_at = NOW()`. Queries MUST filter `WHERE deleted_at IS NULL`.

### 2.3 Strict Data Type Conventions
* **Identifiers:** `UUID` (never auto-increment integer in distributed healthcare systems).
* **Measurements & Weights:** `DECIMAL(10,2)` or `DECIMAL(8,3)` (e.g., waste weight in Kg, water pH). `FLOAT` or `DOUBLE PRECISION` is **strictly prohibited** due to floating-point inaccuracies.
* **Timestamps:** `TIMESTAMPTZ` (always timezone-aware, stored in UTC).
* **Categorical States:** PostgreSQL `ENUM` or lookup foreign key table.

### 2.4 Indexing Strategy
* All Foreign Key columns MUST be indexed: `CREATE INDEX idx_table_fk ON table(fk_id);`
* Searchable unique identifiers MUST have unique indexes: `CREATE UNIQUE INDEX uq_table_code ON table(code) WHERE deleted_at IS NULL;`

### 2.5 Mermaid ERD Standard
Must provide a visual `erDiagram` using standard Crow's Foot notation:
* `||--o{` (One-to-Many optional)
* `||--|{` (One-to-Many mandatory)
* `||--||` (One-to-One)

---

## 3. Standards for TRD (API Contracts & Security)

All TRD documents MUST comply with the following RESTful API standards:

### 3.1 Standard Response Envelope
All API responses MUST be wrapped in a consistent JSON structure:

**Success Response (200 / 201):**
```json
{
  "success": true,
  "data": { ... },
  "meta": {
    "timestamp": "2026-09-14T21:40:00Z",
    "request_id": "req_8f12a9b4"
  }
}
```

**Paginated Success Response (200):**
```json
{
  "success": true,
  "data": [ ... ],
  "pagination": {
    "page": 1,
    "limit": 20,
    "total_records": 150,
    "total_pages": 8
  },
  "meta": { ... }
}
```

**Error Response (4xx / 5xx):**
```json
{
  "success": false,
  "error": {
    "code": "ROOM_ALREADY_EXISTS",
    "message": "Kode ruangan OK-01 sudah terdaftar di fasilitas ini.",
    "details": [
      { "field": "room_code", "issue": "Must be unique" }
    ]
  },
  "meta": { ... }
}
```

### 3.2 HTTP Status Codes
* `200 OK`: Sukses mengambil data (`GET`) atau pembaruan (`PUT`/`PATCH`).
* `201 Created`: Sukses membuat resource baru (`POST`).
* `400 Bad Request`: Format input / validasi payload salah.
* `401 Unauthorized`: Token otentikasi tidak ada atau kedaluwarsa.
* `403 Forbidden`: Pengguna tidak memiliki hak akses untuk resource ini.
* `404 Not Found`: Resource tidak ditemukan.
* `409 Conflict`: Bentrok data unik (misal NIK atau Kode Ruangan sudah terpakai).
* `422 Unprocessable Entity`: Validasi aturan bisnis gagal (misal kuota TPS penuh).

---

---

## 4. Standard Scoping Matrix (Kapan Global vs Kapan Split)

| Jenis Dokumen | Strategi Scoping | Justifikasi Arsitektur | Contoh File di `technical/` |
| :--- | :--- | :--- | :--- |
| **DRA (Data Requirements Architecture)** | **Global per Milestone Besar** | PostgreSQL membutuhkan konsistensi skema, integritas relasi *Foreign Key*, dan satu diagram ERD yang utuh. Pemisahan per fitur kecil akan memecah integritas relasional dan menyulitkan DBA. | • `01-dra-database-erd-master-auth.md`<br>• `05-dra-database-erd-operational.md` |
| **TRD (API Contracts)** | **Modular per Domain / Klaster** | Mencegah file spesifikasi membengkak menjadi ribuan baris. Frontend dan Backend engineer dapat fokus pada domain API yang sedang dikerjakan. | • `02-trd-auth-session-api.md`<br>• `03-trd-master-data-api.md`<br>• `06-trd-checklist-qr-api.md`<br>• `07-trd-waste-monitoring-api.md` |
| **TRD (Security & Infrastructure)** | **Dedicated Cross-Cutting Doc** | Topik spesifik seperti keamanan token QR anti-kloning, WebCrypto, dan arsitektur Offline-First PWA (IndexedDB + Outbox) membutuhkan dokumen arsitektur khusus yang diacu oleh banyak modul. | • `04-trd-security-qr-offline.md` |

---

## 5. Standard Document Templates

### 5.1 Template Dokumen DRA (`technical/XX-dra-*.md`)
```markdown
# Data Requirements Architecture (DRA): [Nama Modul/Sub-sistem]

## 1. Metadata Dokumen
- Kode Dokumen: DRA-SEHS-XX
- Target Database: PostgreSQL 15+
- Source PRD: [Link ke PRD Terkait]
- Depends On: [Prasyarat Dokumen]
- Consumed By: [Dampak Dokumen]
- Versi: 1.0.0

## 2. Diagram Hubungan Entitas (Entity-Relationship Diagram / ERD)
(Mermaid erDiagram dengan Crow's Foot Notation)

## 3. Spesifikasi Skema Tabel (Physical Data Model)
- Nama Tabel & Deskripsi
- Tabel Kolom (Nama, Tipe, Constraints, Deskripsi, Acuan Aturan Bisnis `BR-*`)
- Foreign Keys (`ON DELETE RESTRICT`) & Indexes
- DDL SQL Definition (Clean & Syntax-Ready, include universal audit columns)

## 4. Kebijakan Integritas & Retensi Data
- Soft Delete Handling (`deleted_at IS NULL`)
- Audit Log Triggers
- Data Purging / Archival Policy (Kepatuhan Akreditasi Faskes)
```

### 5.2 Template Dokumen TRD (`technical/XX-trd-*.md`)
```markdown
# Technical Requirements Document (TRD): [Nama Modul]

## 1. Metadata Dokumen
- Kode Dokumen: TRD-SEHS-XX
- Protokol: RESTful API over HTTPS (TLS 1.3) / JSON
- Source PRD: [Link ke PRD Terkait]
- Depends On: [DRA & Dokumen Terkait]
- Consumed By: [Klien & Servis Terkait]
- Versi: 1.0.0

## 2. Arsitektur Komponen & Alur Komunikasi
(Diagram Arsitektur / Sequence Diagram Teknis Mermaid)

## 3. Spesifikasi Endpoint REST API
- Detail per endpoint: Method, URL, Header, Request Body, Response 200/201 (Envelope Standard), Response Error (4xx/5xx)
- Acuan Aturan Bisnis (`BR-*`) di setiap endpoint

## 4. Spesifikasi Keamanan, Token & Sesi
- Detail JWT RS256, Enkripsi, Argon2id Hashing, Rate Limiting, Idempotency-Key

## 5. Strategi Caching, Offline & Kinerja
- Redis Cache Keys & TTL
- Offline-First PWA (Service Worker + IndexedDB Outbox Queue + Background Sync) jika relevan
- Background Jobs / Queue (BullMQ / RabbitMQ)
```
