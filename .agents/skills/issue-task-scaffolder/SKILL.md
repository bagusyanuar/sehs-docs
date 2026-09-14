---
name: issue-task-scaffolder
description: "Framework and guidelines for scaffolding production-ready GitHub Issues for Backend (BE) and Frontend (FE) teams directly from PRD, DRA, and TRD specifications. Enforces zero-ambiguity scope, bidirectional traceability, exact endpoint/table references, and ready-to-run GitHub CLI (gh) commands."
---

# Issue Task Scaffolder Skill

Standardized framework for converting **Smart Environment Health System (SEHS)** specifications (PRD, DRA, and TRD) into clear, actionable, and unambiguous **GitHub Issues** for Backend and Frontend developers.

---

## 1. Core Principles of Issue Scaffolding

1. **Role Separation (BE vs FE-WEB vs FE-MOBILE):**
   * **Backend (`[BE]`):** Focuses on Database Schema (DRA), Migrations, REST API Controllers, Hashing, Token Generation, Business Logic Validation (`BR-*`), and Integration Tests.
   * **Frontend Web (`[FE-WEB]`):** Focuses on Web Admin Dashboard (React/Vue/Next.js) for Sanitarian, IPSRS, and Direksi. Desktop-optimized, data grids, charts, forms, and accreditation reports.
   * **Frontend Mobile (`[FE-MOBILE]`):** Focuses on **Flutter (Dart)** Mobile App for Field Officers (Cleaning Service & Porter). Touch-optimized numeric keypad, native camera scanner (`mobile_scanner`), local offline database (SQLite/Hive/Isar), background sync with `Idempotency-Key`, and secure storage (`flutter_secure_storage`).
2. **Single Source of Truth (Lean Scoping):**
   * **Tiket DILARANG menduplikasi DDL SQL mentah atau seluruh payload JSON API.**
   * Tiket GitHub Issue berfokus murni pada **lingkup tugas (*Scope of Work*)** dan **kriteria selesai (*DoD*)**.
   * Detail teknikal mendalam tetap menjadi tanggung jawab dokumen DRA dan TRD yang ditautkan, serta ditangani oleh skill spesifik di repositori kode (BE/FE).
3. **Absolute Traceability:**
   * Every issue MUST link to the exact PRD, DRA, and TRD on GitHub.
   * Every issue MUST cite the exact Business Rule IDs (`BR-*`) it implements.
4. **Actionable Definition of Done (DoD):**
   * Clear checklist of verification criteria that a developer or QA can check off.

---

## 2. Standard Issue Structure

### 2.1 Backend Issue Format (`[BE]`)
* **Title:** `[BE] <Module Name>: <Specific Objective>`
* **Labels:** `backend`, `<domain-label>` (e.g. `auth`, `master-data`, `operational`)
* **Template:** `.github/ISSUE_TEMPLATE/backend-task.md`

### 2.2 Frontend Web Issue Format (`[FE-WEB]`)
* **Title:** `[FE-WEB] <Module Name>: <Specific Dashboard UI Objective>`
* **Labels:** `frontend-web`, `<domain-label>`
* **Template:** `.github/ISSUE_TEMPLATE/frontend-web-task.md`

### 2.3 Frontend Mobile Flutter Issue Format (`[FE-MOBILE]`)
* **Title:** `[FE-MOBILE] <Module Name>: <Specific Flutter Feature Objective>`
* **Labels:** `frontend-mobile`, `<domain-label>`
* **Template:** `.github/ISSUE_TEMPLATE/frontend-mobile-task.md`

---

## 3. GitHub CLI (`gh`) Command Generation

When generating issues, the agent MUST format them so they can be published directly via `gh`:

```bash
# Contoh untuk Backend
gh issue create \
  --title "[BE] Auth API: Implement Dual-UX Login, Argon2id & Session Management" \
  --label "backend,auth" \
  --body-file "/path/to/issue-body.md"

# Contoh untuk Frontend Mobile Flutter
gh issue create \
  --title "[FE-MOBILE] Auth: Build NIK+PIN Numeric Keypad & Secure Storage" \
  --label "frontend-mobile,auth" \
  --body-file "/path/to/issue-body.md"
```

---

## 4. Verification Gate

Before publishing an issue:
* [ ] Does the issue clearly specify whether it is for BE, FE, or Fullstack?
* [ ] Are all referenced PRD/DRA/TRD links valid and pointing to `main` branch?
* [ ] Are the business rules (`BR-*`) explicitly listed?
* [ ] Does the DoD include automated tests and edge case verifications?
