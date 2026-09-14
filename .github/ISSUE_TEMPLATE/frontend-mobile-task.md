---
name: "Frontend Mobile Task (Flutter App)"
about: "Template tugas implementasi Mobile App Flutter (Scope-focused: Petugas Lapangan, QR & Offline)"
title: "[FE-MOBILE] <Nama Modul>: <Tujuan Fitur Mobile Flutter>"
labels: ["frontend-mobile"]
assignees: []
---

### 🎯 1. Objective & Target Persona
* **Target Modul:** [Login NIK+PIN / Scanner QR Ruangan / Input Checklist / Timbangan Limbah / Lapor Insiden]
* **Target Pengguna:** Petugas Cleaning Service & Porter Limbah (Operasional Lapangan)
* **Tech Stack:** Flutter (Dart) — Android / iOS Mobile Application

---

### 📚 2. Dokumen Acuan (Single Source of Truth)
* **Alur Pengguna PRD:** [`features/...`](https://github.com/bagusyanuar/sehs-docs/blob/main/features/...)
  * *Aturan Bisnis Terkait:* `BR-XXX-01`, `BR-XXX-02`
* **Kontrak REST API TRD:** [`technical/...`](https://github.com/bagusyanuar/sehs-docs/blob/main/technical/...)
  * *Endpoints Acuan:* `POST /api/v1/...`
* **Arsitektur Keamanan & Offline TRD:** [`technical/04-trd-security-qr-offline.md`](https://github.com/bagusyanuar/sehs-docs/blob/main/technical/04-trd-security-qr-offline.md)

---

### 🛠️ 3. Scope of Work (Tugas Teknis)
- [ ] Bangun antarmuka mobile yang ergonomis & touch-friendly (misal: numeric keypad PIN 6 digit).
- [ ] Integrasikan scanner kamera hardware (misal `mobile_scanner`) dengan proteksi anti-galeri foto sesuai TRD-03.
- [ ] Integrasikan penyimpanan database lokal (SQLite/Hive/Isar) untuk template form & antrean `outbox_queue` saat offline.
- [ ] Simpan kredensial token JWT aman di Android Keystore / iOS Keychain via `flutter_secure_storage`.
- [ ] Pasang mekanisme deteksi jaringan & background sync saat online dengan menyertakan `Idempotency-Key`.

---

### ✅ 4. Definition of Done (DoD)
- [ ] Berjalan mulus di perangkat Android dan iOS.
- [ ] Skenario offline (mode pesawat) teruji: transaksi tersimpan lokal dan otomatis terkirim saat internet pulih.
- [ ] Scanner kamera responsif dan penolakan QR palsu / di luar geofence berfungsi dengan baik.
- [ ] Bebas memory leak pada controller kamera atau stream listener.
