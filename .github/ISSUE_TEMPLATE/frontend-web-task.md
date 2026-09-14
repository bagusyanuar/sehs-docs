---
name: "Frontend Web Task (Admin Dashboard)"
about: "Template tugas implementasi Web Dashboard (Scope-focused: React/Vue/Next.js untuk Admin & Sanitarian)"
title: "[FE-WEB] <Nama Modul>: <Tujuan Antarmuka Dashboard>"
labels: ["frontend-web"]
assignees: []
---

### 🎯 1. Objective & Target Persona
* **Target Modul:** [Master Data / Audit Verifikasi / Kualitas Lingkungan / Laporan Eksekutif]
* **Target Pengguna:** Sanitarian / Tim Pemeliharaan IPSRS / Manajemen Direksi
* **Platform:** Desktop Web Browser

---

### 📚 2. Dokumen Acuan (Single Source of Truth)
* **Aturan Bisnis & Form PRD:** [`features/...`](https://github.com/bagusyanuar/sehs-docs/blob/main/features/...)
  * *Aturan Bisnis Terkait:* `BR-XXX-01`, `BR-XXX-02`
* **Kontrak REST API TRD:** [`technical/...`](https://github.com/bagusyanuar/sehs-docs/blob/main/technical/...)
  * *Endpoints Acuan:* `GET /api/v1/...`, `POST /api/v1/...`

---

### 🛠️ 3. Scope of Work (Tugas Teknis)
- [ ] Bangun komponen UI (Data table/grid, filter pencarian, modal form, grafik analitik).
- [ ] Implementasikan validasi form di sisi klien sesuai batasan PRD.
- [ ] Integrasikan request ke Backend API sesuai kontrak endpoint & DTO di TRD.
- [ ] Tangani state aplikasi (loading indicator, empty state, toast notifikasi error code dari TRD).
- [ ] Tangani fitur ekspor data (PDF stiker QR / laporan Excel) jika disyaratkan.

---

### ✅ 4. Definition of Done (DoD)
- [ ] Antarmuka responsif dan teruji pada resolusi desktop/tablet.
- [ ] Integrasi data dengan backend berjalan sukses.
- [ ] Validasi error code dari backend ditampilkan secara ramah kepada pengguna.
- [ ] Bersih dari error konsol browser dan lulus uji linting.
