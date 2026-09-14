---
name: "Backend Engineering Task"
about: "Template tugas implementasi Backend (Scope-focused: Database, REST API, Security, Business Rules)"
title: "[BE] <Nama Modul>: <Tujuan Lingkup Tugas>"
labels: ["backend"]
assignees: []
---

### 🎯 1. Objective
<!-- Jelaskan secara padat tujuan fungsional tugas backend ini -->

---

### 📚 2. Dokumen Acuan (Single Source of Truth)
* **Aturan Bisnis PRD:** [`features/...`](https://github.com/bagusyanuar/sehs-docs/blob/main/features/...)
  * *Aturan Bisnis yang Wajib Lolos:* `BR-XXX-01`, `BR-XXX-02`
* **Skema Database DRA:** [`technical/...`](https://github.com/bagusyanuar/sehs-docs/blob/main/technical/...)
  * *Tabel Acuan:* `nama_tabel_1`, `nama_tabel_2`
* **Kontrak REST API TRD:** [`technical/...`](https://github.com/bagusyanuar/sehs-docs/blob/main/technical/...)
  * *Endpoints Acuan:* `POST /api/v1/...`, `GET /api/v1/...`

---

### 🛠️ 3. Scope of Work (Tugas Teknis)
- [ ] Buat migration tabel dan relasi foreign key sesuai rujukan DRA.
- [ ] Implementasikan service logika bisnis & validasi aturan PRD (`BR-*`).
- [ ] Implementasikan controller REST API, DTO, dan response envelope sesuai rujukan TRD.
- [ ] Terapkan mekanisme keamanan (hashing/token/rate limiting) yang ditentukan pada TRD.
- [ ] Buat seeder data awal / testing jika diperlukan.

---

### ✅ 4. Definition of Done (DoD)
- [ ] Database migration berjalan sukses tanpa konflik constraint.
- [ ] Seluruh aturan bisnis PRD `BR-*` teruji dan mengembalikan error code yang sesuai.
- [ ] Format request/response envelope konsisten sesuai TRD.
- [ ] Unit test dan integration test lulus.
