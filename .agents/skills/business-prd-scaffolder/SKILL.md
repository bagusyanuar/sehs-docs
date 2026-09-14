---
name: business-prd-scaffolder
description: "Framework and guidelines for scaffolding Business-Centric Product Requirements Documents (PRDs). Focuses strictly on business logic, user operations, workflows, and domain rules, while preventing low-level technical/engineering leakages (e.g. no JSON schemas, database keys, or API endpoint tables)."
---

# Business-Centric PRD Scaffolder Skill

Standardized framework for creating high-impact, business-centric Product Requirements Documents (PRDs) for the **Smart Environment Health System (SEHS)**.

## Core Philosophy: "WHAT & WHY", Not "HOW"

A **Product Requirements Document (PRD)** is written for business stakeholders, clients, product managers, designers, and domain experts (sanitarians/hospital directors). 
Technical implementation details belong in a **Technical Requirements Document (TRD)** or **Architecture Spec**.

### Strictly Prohibited in PRDs:
* ❌ Raw JSON payloads or API request/response samples.
* ❌ Low-level cryptographic algorithms (e.g., `RS256`, `Argon2id`, `bcrypt`).
* ❌ Database-specific technical schemas (e.g., `UUIDv4`, Foreign Keys, indexes).
* ❌ API endpoint tables (e.g., `POST /api/v1/...`).
* ❌ Code snippets or programming language specific libraries.

### Mandatory Focus in PRDs:
* ✅ **Latar Belakang & Nilai Bisnis (Business Value):** Mengapa fitur ini penting bagi operasional dan kepatuhan faskes?
* ✅ **Konteks & Lingkungan Kerja Pengguna (User Context):** Apakah pengguna bekerja di lapangan (pakai sarung tangan/APD), atau di meja kantor?
* ✅ **Alur Pengguna & Interaksi (User Journey & Experience):** Langkah demi langkah dari sudut pandang apa yang dilihat dan dilakukan pengguna.
* ✅ **Aturan Bisnis (Business Rules):** Kebijakan operasional (misal: batas toleransi waktu simpan, penanganan pergantian shift, validasi kepatuhan).
* ✅ **Skenario Khusus / Pengecualian (Edge Cases):** Apa yang terjadi saat jaringan mati, petugas lupa PIN, atau alat rusak?
* ✅ **Kriteria Penerimaan (Acceptance Criteria):** Berdasarkan hasil fungsional yang dapat diuji oleh pengguna/QA.

---

## Standard Template Structure for Feature PRDs

Every feature PRD inside `features/` MUST adhere to this structure:

```markdown
# Feature PRD: [Nama Fitur]

## 1. Metadata Dokumen
- **Kode Dokumen:** PRD-SEHS-XX
- **Nama Modul:** [Nama Modul]
- **Dokumen Induk:** 00-MASTER-PRD.md
- **Depends On (Prasyarat):** [Daftar PRD/Modul yang menjadi dependensi modul ini]
- **Consumed By (Dampak):** [Daftar PRD/Modul yang memanfaatkan/terdampak oleh modul ini]
- **Target Pengguna:** [Persona]

## 2. Latar Belakang & Masalah Bisnis
- Mengapa fitur ini dibutuhkan?
- Masalah nyata apa yang diselesaikan di lapangan?
- Manfaat bagi faskes, akreditasi, dan kepatuhan regulasi.

## 3. Persona & Konteks Penggunaan
- Siapa penggunanya?
- Di mana dan bagaimana mereka menggunakannya? (PWA Mobile di ruang rawat vs Web Desktop di kantor).

## 4. Alur Kerja Utama (Core User Journey)
- Visual diagram alur proses kerja (Mermaid flowchart / user journey).
- Narasi langkah demi langkah dari awal hingga selesai.

## 5. Kebutuhan Fungsional & Aturan Bisnis (Business Rules)
- Spesifikasi tiap sub-fitur dari kacamata pengguna.
- Kebijakan dan batasan operasional (Business constraints).

## 6. Skenario Pengecualian & Penanganan Masalah (Edge Cases)
- Penanganan saat kondisi abnormal (offline, salah input berulang, keadaan darurat).

## 7. Metrik Keberhasilan Bisnis (KPI)
- Dampak langsung terhadap operasional faskes.

## 8. Kriteria Penerimaan (Acceptance Criteria)
- Checklist pengujian fungsional yang dapat divalidasi.
```
