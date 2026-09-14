---
name: publish-issue
description: Menerbitkan tiket tugas GitHub Issue untuk tim Backend (BE) dan/atau Frontend (FE) secara otomatis berdasarkan spesifikasi PRD, DRA, dan TRD.
---

# Workflow: /publish-issue

Gunakan workflow ini untuk mengonversi spesifikasi PRD, DRA, dan TRD menjadi tiket **GitHub Issues** siap eksekusi bagi developer Backend atau Frontend.

---

## Langkah-Langkah Eksekusi Otomatis

### 1. Identifikasi Modul & Peran Target
Tentukan modul yang ingin diterbitkan tiketnya dan target timnya:
* **Modul:** (Contoh: `Auth`, `Master Data Ruangan`, `Checklist QR`, `Monitoring Limbah`)
* **Target Tim:**
  * `BE`: Backend (Database & REST API)
  * `FE-WEB`: Frontend Web Admin Dashboard (React/Vue/Next)
  * `FE-MOBILE`: Frontend Mobile App (Flutter)
  * `ALL`: Terbitkan ketiga peran sekaligus

### 2. Kumpulkan Konteks Dokumen
Baca file spesifikasi yang relevan:
* **PRD:** Ambil aturan bisnis (`BR-*`) dan alur pengguna.
* **DRA:** Ambil nama tabel, relasi foreign key, dan skema migrasi PostgreSQL.
* **TRD:** Ambil rincian endpoint REST API, payload request/response JSON, dan penanganan keamanan/offline.

### 3. Susun Isi Tiket Sesuai Template
Gunakan template standar di `.github/ISSUE_TEMPLATE/`:
* [Backend Task Template](file:///Users/dystopia/projects/smart-environment-health-system/sehs-docs/.github/ISSUE_TEMPLATE/backend-task.md) untuk tiket `[BE]`.
* [Frontend Web Template](file:///Users/dystopia/projects/smart-environment-health-system/sehs-docs/.github/ISSUE_TEMPLATE/frontend-web-task.md) untuk tiket `[FE-WEB]`.
* [Frontend Mobile Flutter Template](file:///Users/dystopia/projects/smart-environment-health-system/sehs-docs/.github/ISSUE_TEMPLATE/frontend-mobile-task.md) untuk tiket `[FE-MOBILE]`.

Pastikan seluruh link mengarah ke URL GitHub repositori:
`https://github.com/bagusyanuar/sehs-docs/blob/main/...`

### 4. Terbitkan Tiket via GitHub CLI (`gh`)
Jalankan perintah `gh issue create`:
```bash
# Contoh Backend
gh issue create \
  --title "[BE] <Nama Modul>: <Tujuan>" \
  --label "backend,<domain>" \
  --body "..."

# Contoh Frontend Mobile Flutter
gh issue create \
  --title "[FE-MOBILE] <Nama Modul>: <Tujuan>" \
  --label "frontend-mobile,<domain>" \
  --body "..."
```

### 5. Laporkan Tautan Tiket ke Pengguna
Tampilkan URL tiket yang berhasil diterbitkan agar pengguna atau developer lain bisa langsung mengkliknya dan menggunakannya sebagai acuan kerja saat koding.
