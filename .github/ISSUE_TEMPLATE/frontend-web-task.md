---
name: "Frontend Web Task (Admin Dashboard)"
about: "Template tugas implementasi Web Dashboard (React/Vue/Next.js untuk Sanitarian, Kantor, IPSRS & Direksi)"
title: "[FE-WEB] <Nama Modul>: <Tujuan Antarmuka Dashboard>"
labels: ["frontend-web"]
assignees: []
---

### 🎯 1. Objective & Target Persona
* **Target Modul:** [Master Data / Audit Verifikasi / Kualitas Lingkungan / Laporan Eksekutif]
* **Target Pengguna:** Sanitarian / Tim Pemeliharaan IPSRS / Manajemen Direksi
* **Platform:** Desktop Web Browser (Responsif Desktop & Tablet)

---

### 📚 2. Spesifikasi & Acuan Dokumen (Traceability)
* **Source PRD (Alur Bisnis & Validasi):** [`features/...`](https://github.com/bagusyanuar/sehs-docs/blob/main/features/...)
  * *Aturan Bisnis:* `BR-XXX-01`, `BR-XXX-02`
* **TRD (Kontrak REST API & DTO):** [`technical/...`](https://github.com/bagusyanuar/sehs-docs/blob/main/technical/...)
  * *Endpoint yang Dikonsumsi:* `GET /api/v1/...`, `POST /api/v1/...`

---

### 🖥️ 3. Kebutuhan Komponen Antarmuka (UI/UX)
* [ ] Data Table / Data Grid: Pagination server-side, search filter, dan multi-sorting.
* [ ] Modal & Form Dialog: Validasi input data master (misal: format kode ruangan, koordinat GPS gedung).
* [ ] Visualisasi & Charts (jika relevan): Grafik tren kepatuhan sanitasi, persentase keterisian TPS limbah B3.
* [ ] Ekspor Dokumen: Generator PDF stiker QR code siap cetak atau ekspor laporan berkala Excel/PDF.

---

### 🔌 4. Integrasi REST API & State Management
* [ ] Client HTTP Interceptor: Injeksi header otomatis `Authorization: Bearer <access_token>`.
* [ ] Auto-Refresh Token: Interceptor refresh token saat menerima `401 AUTH_TOKEN_EXPIRED`.
* [ ] Handling Error Response: Tampilkan notifikasi toast/alert spesifik berdasarkan `error.code` dari API TRD.

---

### ✅ 5. Definition of Done (DoD)
- [ ] Komponen halaman telah teruji pada resolusi desktop (1366x768 s/d 1920x1080).
- [ ] Alur CRUD data master atau verifikasi audit berjalan mulus terintegrasi dengan Backend API.
- [ ] Zero linting error dan tidak ada memory leak pada grafik/tabel data.
