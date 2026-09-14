---
name: "Frontend Mobile Task (Flutter App)"
about: "Template tugas implementasi Mobile App Flutter (Petugas Cleaning Service, Porter Limbah & Auditor Lapangan)"
title: "[FE-MOBILE] <Nama Modul>: <Tujuan Fitur Mobile Flutter>"
labels: ["frontend-mobile"]
assignees: []
---

### 🎯 1. Objective & Target Persona
* **Target Modul:** [Login NIK+PIN / Scanner QR Ruangan / Input Checklist / Timbangan Limbah / Lapor Insiden]
* **Target Pengguna:** Petugas Cleaning Service & Porter Limbah (Operasional Lapangan)
* **Tech Stack:** Flutter (Dart) — Android / iOS Mobile Application

---

### 📚 2. Spesifikasi & Acuan Dokumen (Traceability)
* **Source PRD (Alur Pengguna):** [`features/...`](https://github.com/bagusyanuar/sehs-docs/blob/main/features/...)
  * *Aturan Bisnis:* `BR-XXX-01`, `BR-XXX-02`
* **TRD API Kontrak:** [`technical/...`](https://github.com/bagusyanuar/sehs-docs/blob/main/technical/...)
  * *Endpoint yang Dikonsumsi:* `POST /api/v1/...`
* **TRD Keamanan QR & Sinkronisasi Offline:** [`technical/04-trd-security-qr-offline.md`](https://github.com/bagusyanuar/sehs-docs/blob/main/technical/04-trd-security-qr-offline.md)

---

### 📱 3. Kebutuhan UI/UX Mobile (Flutter)
* [ ] Desain antarmuka *touch-friendly* & ergonomis (mudah dioperasikan dengan satu tangan & sarung tangan).
* [ ] Custom Numeric Keypad: Input NIK & PIN 6 digit yang cepat dengan visual feedback instan.
* [ ] Status Bar Visual: Indikator jelas status koneksi (Online / Offline Mode) dan jumlah transaksi antrean outbox.

---

### 📷 4. Akses Hardware & Sensor Perangkat
* [ ] **Scanner Kamera QR (Live Stream Only):** Gunakan plugin kamera native (misal: `mobile_scanner`). Dilarang menyediakan opsi upload foto dari galeri HP untuk mencegah spoofing QR.
* [ ] **Geolokasi GPS:** Integrasikan plugin geolokasi (misal: `geolocator`) untuk menangkap koordinat saat scan QR. Tangani skenario bunker/basement (`is_gps_blindspot`).
* [ ] **Kamera Bukti Temuan:** Fitur ambil foto langsung kondisi ruangan / timbangan limbah.

---

### 💾 5. Arsitektur Offline-First & Penyimpanan Lokal
* [ ] **Penyimpanan Kredensial Aman:** Simpan JWT Access Token & Refresh Token di `flutter_secure_storage` (Android Keystore / iOS Keychain).
* [ ] **Database Lokal Offline (SQLite / Isar / Hive):**
  * Simpan template checklist aktif agar form bisa dirender tanpa internet.
  * Buat tabel `outbox_queue` untuk menampung transaksi checklist dan timbangan limbah saat offline.
* [ ] **Background Sync & Retry:**
  * Saat `connectivity_plus` mendeteksi internet pulih, kirim antrean outbox ke `POST /api/v1/sync/batch` dengan menyertakan `Idempotency-Key`.

---

### ✅ 6. Definition of Done (DoD)
- [ ] Berjalan mulus di perangkat Android (min. Android 8.0) dan iOS.
- [ ] Pengujian skenario offline di mode pesawat (*Airplane Mode*): transaksi tersimpan lokal dan otomatis tersinkron saat internet dinyalakan kembali.
- [ ] Token QR palsu / di luar geofence berhasil ditolak dengan dialog pesan yang informatif.
- [ ] Tidak ada memory leak pada camera scanner controller.
