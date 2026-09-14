# Technical Requirements Document (TRD): API Master Data Fasilitas & Standar

---

## 1. Metadata Dokumen

| Properti | Keterangan |
| :--- | :--- |
| **Kode Dokumen** | `TRD-SEHS-02` |
| **Nama Modul** | Spesifikasi API Master Data Fasilitas, Sanitasi & Standar (*Master Data REST API*) |
| **Protokol** | RESTful API over HTTPS (TLS 1.3) / JSON |
| **Source PRD (Acuan Bisnis)** | [`features/master-data/01-md-organisasi-shift.md`](../features/master-data/01-md-organisasi-shift.md) s/d [`06-md-kategori-temuan-sla.md`](../features/master-data/06-md-kategori-temuan-sla.md) |
| **Depends On (Prasyarat)** | • [`technical/01-dra-database-erd-master-auth.md`](./01-dra-database-erd-master-auth.md) (Skema Database PostgreSQL 15+)<br>• [`technical/02-trd-auth-session-api.md`](./02-trd-auth-session-api.md) (Otentikasi JWT Bearer Token) |
| **Consumed By (Dampak)** | Web Admin Dashboard (Halaman Pengaturan Master Data Sanitarian), Mobile PWA (Dropdown Lookup) |
| **Versi** | 1.0.0 |
| **Status** | Approved / Baseline |
| **Terakhir Diperbarui** | 2026-09-14 |
| **Target Pembaca** | Backend Engineer, Frontend Engineer, QA Tester |

---

## 2. Standar Global API Master Data

Seluruh endpoint Master Data mengikuti kaidah arsitektur berikut:
1. **Otorisasi Default:** Wajib menyertakan header `Authorization: Bearer <access_token>`. Hak akses modifikasi (`POST`, `PUT`, `DELETE`) dibatasi untuk peran `SANITARIAN` dan `MANAGEMENT`.
2. **Paginasi & Pencarian Standar:**
   * Query params: `?page=1&limit=20&search=...&is_active=true`
3. **Soft Delete Behavior:**
   * Permintaan `DELETE /api/v1/master/{resource}/:id` mengeksekusi *soft delete* (`deleted_at = NOW()`).
4. **Caching Strategy (Redis):**
   * Data master yang jarang berubah namun sering dibaca (seperti daftar ruangan, tipe limbah, dan shift) disimpan di Redis Cache dengan TTL 1 jam: `cache:master:{resource}`. Cache otomatis di-invalidate saat ada aksi `POST`/`PUT`/`DELETE`.

---

## 3. Spesifikasi Endpoint per Klaster Bisnis

### 3.1 Klaster 1: Organisasi & Shift Kerja

#### `GET /api/v1/master/units`
* **Deskripsi:** Mengambil daftar seluruh unit/instalasi faskes.
* **Response `200 OK`:**
```json
{
  "success": true,
  "data": [
    {
      "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
      "code": "IRNA",
      "name": "Instalasi Rawat Inap",
      "head_name": "dr. Hendra Pratama, Sp.PD",
      "phone_number": "081234567890",
      "is_active": true
    }
  ]
}
```

#### `GET /api/v1/master/shifts` & `PUT /api/v1/master/shifts/:id`
* **Deskripsi:** Konfigurasi jam shift kerja dan batas toleransi handover (BR-MD01-04, BR-MD01-05).
* **Request Payload `PUT`:**
```json
{
  "start_time": "07:00:00",
  "end_time": "14:00:00",
  "handover_tolerance_minutes": 30
}
```

---

### 3.2 Klaster 2: Lokasi, Ruangan & Cetak QR Code

#### `GET /api/v1/master/rooms`
* **Deskripsi:** Menampilkan daftar ruangan lengkap dengan filter gedung, lantai, dan tingkat risiko.
* **Query Params:** `?building_id=...&floor_id=...&risk_level=VERY_HIGH`
* **Response `200 OK`:**
```json
{
  "success": true,
  "data": [
    {
      "id": "c3d4e5f6-a7b8-9012-cdef-123456789012",
      "room_code": "OK-01",
      "name": "Kamar Operasi Bedah Mayor 1",
      "building": { "id": "b1...", "name": "Gedung Bedah Sentral" },
      "floor": { "id": "f2...", "name": "Lantai 2" },
      "unit": { "id": "u3...", "name": "Instalasi Bedah Sentral" },
      "risk_level": "VERY_HIGH",
      "qr_token": "QR_SEC_98a7b6c5d4e3f2a1...",
      "is_active": true
    }
  ],
  "pagination": { "page": 1, "limit": 20, "total_records": 120, "total_pages": 6 }
}
```

#### `POST /api/v1/master/rooms`
* **Deskripsi:** Mendaftarkan ruangan baru (otomatis membuat token QR unik).
* **Request Payload:**
```json
{
  "room_code": "VIP-201",
  "name": "Kamar Pasien VIP Teratai 201",
  "floor_id": "f2b3c4d5-e6a7-8901-bcde-f23456789012",
  "unit_id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
  "risk_level": "HIGH"
}
```

#### `GET /api/v1/master/rooms/export-qr-pdf`
* **Deskripsi:** Mengunduh lembar cetak stiker QR code siap tempel (BR-MD02-07).
* **Query Params:** `?floor_id=...` (untuk cetak massal 1 lantai) atau `?room_id=...` (satuan).
* **Response Headers:** `Content-Type: application/pdf`, `Content-Disposition: attachment; filename="Stiker_QR_Lantai_2.pdf"`

---

### 3.3 Klaster 3: Standar Checklist & Template Audit

#### `GET /api/v1/master/checklist-templates/by-room/:room_id`
* **Deskripsi:** Endpoint kritis yang dipanggil aplikasi mobile petugas saat memindai QR code ruangan untuk memuat butir pertanyaan yang sesuai.
* **Response `200 OK`:**
```json
{
  "success": true,
  "data": {
    "template_id": "t1a2b3c4-d5e6-7890-abcd-ef1234567890",
    "template_name": "Template Kamar Rawat Inap (Risiko Tinggi)",
    "passing_grade_percentage": 85.00,
    "items": [
      {
        "indicator_id": "ind_1...",
        "name": "Kebersihan Lantai (Kering, Bersih, Anti-Licin)",
        "response_type": "PASS_FAIL",
        "weight_score": 1.00,
        "is_fatal": false,
        "item_order": 1
      },
      {
        "indicator_id": "ind_2...",
        "name": "Ketersediaan Sabun & Handrub Antiseptik",
        "response_type": "PASS_FAIL",
        "weight_score": 2.00,
        "is_fatal": true,
        "item_order": 2
      }
    ]
  }
}
```

---

### 3.4 Klaster 4: Limbah, TPS & Vendor Transporter

#### `GET /api/v1/master/waste-categories`
* **Deskripsi:** Mengambil daftar jenis limbah dan warna wadah (BR-MD04-01).
* **Response `200 OK`:**
```json
{
  "success": true,
  "data": [
    {
      "id": "w1...",
      "code": "INFECTIOUS",
      "name": "Limbah Medis Infeksius",
      "color_code": "YELLOW",
      "bag_type": "Kantong Plastik Kuning",
      "is_b3": true
    },
    {
      "id": "w2...",
      "code": "SHARPS",
      "name": "Limbah Benda Tajam",
      "color_code": "YELLOW",
      "bag_type": "Safety Box Anti-Tembus",
      "is_b3": true
    }
  ]
}
```

#### `GET /api/v1/master/tps-facilities/status-capacity`
* **Deskripsi:** Mengambil ringkasan kapasitas gudang TPS real-time.
* **Response `200 OK`:**
```json
{
  "success": true,
  "data": {
    "tps_id": "tps_main...",
    "name": "Gudang TPS B3 Utama",
    "max_capacity_kg": 5000.00,
    "current_weight_kg": 4120.50,
    "used_percentage": 82.41,
    "status": "WARNING_NEAR_CAPACITY",
    "warning_threshold_percentage": 80.00,
    "max_ambient_hours": 48
  }
}
```

#### `POST /api/v1/master/waste-transporters`
* **Deskripsi:** Pendaftaran vendor pengangkut berizin resmi KLHK (BR-MD04-05).
* **Request Payload:**
```json
{
  "company_name": "PT. Wastec International",
  "klhk_permit_number": "SK.120/MENLHK/PLB3/2024",
  "permit_expiry_date": "2027-08-30",
  "pic_name": "Pak Joko",
  "pic_phone": "081198765432",
  "armada_plate_numbers": "B 9123 KZA, B 9456 TYU"
}
```

---

### 3.5 Klaster 5: Baku Mutu Sanitasi Air & Udara

#### `GET /api/v1/master/quality-standards`
* **Deskripsi:** Mengambil standar baku mutu batas aman air dan udara untuk validasi data hasil uji.
* **Response `200 OK`:**
```json
{
  "success": true,
  "data": {
    "water_standards": [
      { "parameter": "pH", "unit": "pH", "min": 6.50, "max": 8.50, "is_critical": false },
      { "parameter": "Total Dissolved Solids (TDS)", "unit": "ppm", "min": null, "max": 300.00, "is_critical": false },
      { "parameter": "Bakteri E. coli", "unit": "CFU/100ml", "min": null, "max": 0.00, "is_critical": true }
    ],
    "air_standards": [
      { "zone": "VERY_HIGH", "parameter": "Suhu", "unit": "°C", "min": 19.00, "max": 24.00, "min_ach": 15.00 },
      { "zone": "HIGH", "parameter": "Partikulat PM2.5", "unit": "ug/m3", "min": null, "max": 25.00, "min_ach": null }
    ]
  }
}
```

---

### 3.6 Klaster 6: Kategori Temuan & Standar SLA

#### `GET /api/v1/master/sla-policies`
* **Deskripsi:** Konfigurasi batas waktu tanggap dan waktu selesai perbaikan per tingkat urgensi (BR-MD06-02).
* **Response `200 OK`:**
```json
{
  "success": true,
  "data": [
    {
      "urgency_level": "HIGH",
      "description": "Darurat / Mengancam Keselamatan Pasien",
      "max_response_time_minutes": 15,
      "max_resolution_time_minutes": 240
    },
    {
      "urgency_level": "MEDIUM",
      "description": "Kerusakan Sedang / Mengganggu Kenyamanan",
      "max_response_time_minutes": 60,
      "max_resolution_time_minutes": 1440
    },
    {
      "urgency_level": "LOW",
      "description": "Kerusakan Minor / Estetika",
      "max_response_time_minutes": 240,
      "max_resolution_time_minutes": 4320
    }
  ]
}
```

---

## 4. Standar Penanganan Validasi & Error

| HTTP Status | Error Code | Skenario |
| :---: | :--- | :--- |
| `409` | `ROOM_CODE_ALREADY_EXISTS` | Mencoba membuat ruangan dengan kode yang sudah terdaftar di fasilitas. |
| `422` | `TRANSPORTER_PERMIT_EXPIRED` | Mengaitkan vendor yang izin operasional KLHK-nya telah melewati batas tanggal kedaluwarsa. |
| `400` | `INVALID_THRESHOLD_PERCENTAGE` | Menginput batas peringatan TPS di luar rentang $1.00 - 100.00\%$. |
| `404` | `TEMPLATE_NOT_FOUND_FOR_ROOM` | Ruangan belum memiliki asosiasi template checklist aktif. |
