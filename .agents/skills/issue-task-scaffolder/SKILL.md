---
name: issue-task-scaffolder
description: "Framework and guidelines for scaffolding production-ready GitHub Issues for Backend (BE) and Frontend (FE) teams directly from PRD, DRA, and TRD specifications. Enforces zero-ambiguity scope, bidirectional traceability, exact endpoint/table references, and ready-to-run GitHub CLI (gh) commands."
---

# Issue Task Scaffolder Skill

Standardized framework for converting **Smart Environment Health System (SEHS)** specifications (PRD, DRA, and TRD) into clear, actionable, and unambiguous **GitHub Issues** for Backend and Frontend developers.

---

## 1. Core Principles of Issue Scaffolding

1. **Role Separation (BE vs FE):**
   * **Backend (`[BE]`):** Focuses on Database Schema (DRA), Migrations, REST API Controllers, Hashing, Token Generation, Business Logic Validation (`BR-*`), and Integration Tests.
   * **Frontend (`[FE]`):** Focuses on UI/UX Screens, User Interactions, Form Validations, API Integration (DTO consumption), Token Storage, Offline-First PWA (IndexedDB), and WebRTC Hardware Scanning.
2. **Absolute Traceability:**
   * Every issue MUST link to the exact PRD, DRA, and TRD on GitHub.
   * Every issue MUST cite the exact Business Rule IDs (`BR-*`) it implements.
3. **Actionable Definition of Done (DoD):**
   * Clear checklist of verification criteria that a developer or QA can check off.

---

## 2. Standard Issue Structure

### 2.1 Backend Issue Format (`[BE]`)
* **Title:** `[BE] <Module Name>: <Specific Objective>`
* **Labels:** `backend`, `<domain-label>` (e.g. `auth`, `master-data`, `operational`)
* **Key Contents:**
  * Link to Source PRD with `BR-*` rules.
  * Link to DRA with PostgreSQL table names and universal audit columns.
  * Link to TRD with endpoint signatures, JSON envelopes, and HTTP status codes.
  * Security rules (Argon2id, RS256, Idempotency-Key, Rate Limiting).
  * Definition of Done.

### 2.2 Frontend Issue Format (`[FE]`)
* **Title:** `[FE] <Module Name>: <Specific UI/UX Objective>`
* **Labels:** `frontend`, `<domain-label>`
* **Key Contents:**
  * Target Platform (Mobile PWA for Field Officers vs Web Admin for Office/Sanitarian).
  * Link to Source PRD for field requirements and client-side validations.
  * Link to TRD for API endpoints and token lifecycle (Auto-refresh on 401).
  * Hardware & Offline requirements (Live WebRTC stream, IndexedDB outbox queue).
  * Definition of Done.

---

## 3. GitHub CLI (`gh`) Command Generation

When generating issues, the agent MUST format them so they can be published directly via `gh`:

```bash
gh issue create \
  --title "[BE] Auth API: Implement Dual-UX Login, Argon2id & Session Management" \
  --label "backend,auth" \
  --body-file "/path/to/issue-body.md"
```

---

## 4. Verification Gate

Before publishing an issue:
* [ ] Does the issue clearly specify whether it is for BE, FE, or Fullstack?
* [ ] Are all referenced PRD/DRA/TRD links valid and pointing to `main` branch?
* [ ] Are the business rules (`BR-*`) explicitly listed?
* [ ] Does the DoD include automated tests and edge case verifications?
