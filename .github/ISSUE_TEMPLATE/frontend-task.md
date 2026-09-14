---
name: "Frontend Engineering Task"
about: "Template tugas implementasi Frontend (Mobile PWA, Web Admin Dashboard, UI Components, State & API Integration)"
title: "[FE] <Nama Modul>: <Tujuan Implementasi Antarmuka>"
labels: ["frontend"]
assignees: []
---

### 🎯 1. Objective & Target Platform
<!-- Jelaskan target platform: Mobile PWA (Petugas Lapangan) atau Web Admin Dashboard (Kantor/Sanitarian/Direksi) -->
* **Target Pengguna:** [Petugas Lapangan (CS/Porter) / Sanitarian / IPSRS / Direksi]
* **Platform:** [Mobile PWA (Touch-Optimized) / Desktop Web Browser]

---

### 📚 2. Spesifikasi & Acuan Dokumen (Traceability)
* **Source PRD (Alur Pengguna & Validasi):** [`features/...`](https://github.com/bagusyanuar/sehs-docs/blob/main/features/...)
  * *Aturan Bisnis:* `BR-XXX-01`, `BR-XXX-02`
* **TRD (Kontrak API & DTO):** [`technical/...`](https://github.com/bagusyanuar/sehs-docs/blob/main/technical/...)
  * *Endpoint yang Dikonsumsi:* `POST /api/v1/...`, `GET /api/v1/...`
* **Keamanan & Offline Spec (Jika Relevan):** [`technical/04-trd-security-qr-offline.md`](https://github.com/bagusyanuar/sehs-docs/blob/main/technical/04-trd-security-qr-offline.md)

---

### 📱 3. Kebutuhan UI/UX & Interaksi Komponen
* [ ] Desain responsif, modern, dan ergonomis (mudah disentuh dengan satu tangan untuk Mobile PWA).
* [ ] Validasi form secara *real-time* di sisi klien sesuai batasan PRD (misal: PIN tepat 6 angka).
* [ ] Tampilan penanganan *Loading State*, *Empty State*, dan *Error State* yang jelas.

---

### 🔌 4. Integrasi REST API & State Management
* [ ] Integrasikan interceptor HTTP (Axios / Fetch) dengan header otomatis `Authorization: Bearer <access_token>`.
* [ ] Implementasikan auto-refresh token saat menerima response `401 AUTH_TOKEN_EXPIRED`.
* [ ] Ekstraksi response envelope: Baca data dari `response.data.data` dan tangani error dari `response.data.error`.

---

### 📡 5. Kebutuhan Khusus Perangkat & Mode Offline (Jika Relevan)
* [ ] **Kamera Fisik (QR Scanner):** Gunakan `getUserMedia` (live camera stream only). Blokir penggunaan upload foto dari galeri.
* [ ] **Penyimpanan Lokal (IndexedDB):** Simpan data transaksi ke `outbox_queue` saat `navigator.onLine === false`.
* [ ] **Indikator Koneksi:** Tampilkan banner visual saat perangkat sedang offline vs online.

---

### ✅ 6. Definition of Done (DoD)
- [ ] Tampilan antarmuka telah diverifikasi pada resolusi mobile (360px - 420px) dan desktop (1280px+).
- [ ] Integrasi ke backend API berhasil dan data berhasil disimpan/ditampilkan.
- [ ] Pengujian skenario offline berhasil (transaksi tersimpan lokal dan otomatis tersinkron saat internet pulih).
- [ ] Bersih dari error console browser dan memory leak.
