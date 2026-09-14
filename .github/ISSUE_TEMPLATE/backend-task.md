---
name: "Backend Engineering Task"
about: "Template tugas implementasi Backend (Database, REST API, Security, Business Rules)"
title: "[BE] <Nama Modul>: <Tujuan Implementasi>"
labels: ["backend"]
assignees: []
---

### 🎯 1. Objective & Scope
<!-- Jelaskan secara singkat tujuan teknis yang ingin dicapai pada tugas backend ini -->

---

### 📚 2. Spesifikasi & Acuan Dokumen (Traceability)
* **Source PRD (Aturan Bisnis):** [`features/...`](https://github.com/bagusyanuar/sehs-docs/blob/main/features/...)
  * *Aturan Bisnis Terkait:* `BR-XXX-01`, `BR-XXX-02`
* **DRA (Skema Database):** [`technical/01-dra-database-erd-master-auth.md`](https://github.com/bagusyanuar/sehs-docs/blob/main/technical/01-dra-database-erd-master-auth.md)
  * *Tabel Terkait:* `table_name_1`, `table_name_2`
* **TRD (Kontrak API):** [`technical/...`](https://github.com/bagusyanuar/sehs-docs/blob/main/technical/...)
  * *Endpoint Terkait:* `POST /api/v1/...`, `GET /api/v1/...`

---

### 🗄️ 3. Kebutuhan Database & Migration
* [ ] Buat migration tabel dengan kolom audit universal:
  * `id UUID PRIMARY KEY DEFAULT gen_random_uuid()`
  * `created_at TIMESTAMPTZ NOT NULL DEFAULT NOW()`
  * `updated_at TIMESTAMPTZ NOT NULL DEFAULT NOW()`
  * `created_by UUID NULL REFERENCES users(id) ON DELETE RESTRICT`
  * `deleted_at TIMESTAMPTZ NULL` (Soft delete)
* [ ] Tipe data presisi: Gunakan `DECIMAL(10,2)` untuk berat/pengukuran (dilarang `FLOAT`).
* [ ] Indeks & Constraint:
  * `CREATE INDEX idx_... ON ...(...);`
  * `CREATE UNIQUE INDEX uq_... ON ...(...) WHERE deleted_at IS NULL;`

---

### 🔌 4. Kontrak REST API & Endpoint Specs
* **Route:** `METHOD /api/v1/...`
* **Header Wajib:** `Authorization: Bearer <token>`, `Content-Type: application/json`
* **Response Envelope Standar:**
```json
{
  "success": true,
  "data": { ... },
  "meta": { "timestamp": "...", "request_id": "..." }
}
```
* **Matriks Error Code:** Pastikan mengembalikan kode error spesifik sesuai tabel TRD (misal `409 CONFLICT`, `422 UNPROCESSABLE_ENTITY`).

---

### 🛡️ 5. Keamanan & Validasi Aturan Bisnis
* [ ] Hashing & Enkripsi: Argon2id untuk password/PIN, JWT RS256 untuk token.
* [ ] Rate Limiting / Proteksi Brute-Force via Redis jika relevan.
* [ ] Idempotency: Dukungan header `Idempotency-Key` untuk transaksi offline sync.

---

### ✅ 6. Definition of Done (DoD)
- [ ] Database migration dan seeder data dummy berjalan tanpa error.
- [ ] Semua endpoint REST API telah diimplementasikan sesuai payload TRD.
- [ ] Validasi aturan bisnis PRD (`BR-*`) teruji dan mengembalikan error code yang sesuai.
- [ ] Unit Test & Integration Test lulus 100% dengan coverage minimum 80%.
