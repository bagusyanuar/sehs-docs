# Smart Environment Health System (SEHS) — Documentation Hub

Selamat datang di repositori dokumentasi resmi sistem **Smart Environment Health System (SEHS)**. Sistem ini dirancang untuk mendigitalisasi, memantau, dan mengelola operasional kesehatan lingkungan dan sanitasi secara terintegrasi dan *real-time*, khususnya pada fasilitas pelayanan kesehatan (Rumah Sakit, Klinik, dan Laboratorium).

---

## 📌 Navigasi Dokumentasi

Dokumentasi ini disusun menggunakan pendekatan **Modular Product Documentation (Master PRD & Feature PRDs)** agar mudah dipahami oleh manajemen, product manager, UI/UX designer, software engineer, dan tim QA.

```text
sehs-docs/
├── README.md                                  # Halaman panduan utama (Anda berada di sini)
├── 00-MASTER-PRD.md                           # Dokumen Induk (Global Product Requirement Document)
└── features/                                  # Rincian spesifikasi detail per modul (Feature PRD)
    ├── 01-prd-checklist-kebersihan-qr.md      # Modul 1: Checklist Ruangan & Validasi QR Code
    ├── 02-prd-monitoring-limbah.md            # Modul 2: Pelacakan Limbah B3, Domestik & Kapasitas TPS
    ├── 03-prd-sanitasi-kualitas-lingkungan.md # Modul 3: Pemantauan Kualitas Air & Udara Ruangan
    ├── 04-prd-temuan-tindak-lanjut.md         # Modul 4: Pelaporan Insiden & Alur Tiket Perbaikan
    └── 05-prd-dashboard-laporan.md           # Modul 5: Executive Dashboard & Laporan Kepatuhan
```

---

## 🚀 Ringkasan Modul Utama

| No | Modul | Dokumen Terkait | Deskripsi Singkat |
|:---:|:---|:---|:---|
| **00** | **Master PRD (Global)** | [`00-MASTER-PRD.md`](./00-MASTER-PRD.md) | Fondasi sistem: visi produk, profil pengguna (RBAC), arsitektur global, NFR, dan KPI kesuksesan. |
| **01** | **Checklist Kebersihan QR** | [`features/01-prd-checklist-kebersihan-qr.md`](./features/01-prd-checklist-kebersihan-qr.md) | Verifikasi fisik kehadiran petugas via scan QR di pintu/dinding ruangan, form inspeksi dinamis, dan pencatatan kepatuhan harian. |
| **02** | **Monitoring Limbah & TPS** | [`features/02-prd-monitoring-limbah.md`](./features/02-prd-monitoring-limbah.md) | Pencatatan volume & berat limbah (Infeksius, B3, Domestik, Daur Ulang), pemantauan kapasitas TPS, dan manifes serah terima transporter. |
| **03** | **Sanitasi & Kualitas Lingkungan** | [`features/03-prd-sanitasi-kualitas-lingkungan.md`](./features/03-prd-sanitasi-kualitas-lingkungan.md) | Pemantauan parameter fisik kualitas air (pH, TDS, Kekeruhan) dan udara ($PM_{2.5}$, Suhu, Kelembaban, ACH) serta notifikasi anomali. |
| **04** | **Temuan & Tindak Lanjut** | [`features/04-prd-temuan-tindak-lanjut.md`](./features/04-prd-temuan-tindak-lanjut.md) | Sistem pelaporan cepat kondisi tidak higienis atau kerusakan sarana di ruangan, terhubung langsung ke tim teknis/IPSRS hingga status *Closed*. |
| **05** | **Dashboard & Analitik Laporan** | [`features/05-prd-dashboard-laporan.md`](./features/05-prd-dashboard-laporan.md) | Visualisasi kinerja kesling, grafik kepatuhan audit harian, tren limbah, neraca B3, dan ekspor laporan siap audit akreditasi. |

---

## 👥 Matriks Peran Pengguna (Roles)

1. **Petugas Lapangan (Cleaning Service / Waste Porter):** Antarmuka Mobile Web/PWA untuk scan QR ruangan, isi checklist, input timbangan limbah, dan lapor temuan cepat.
2. **Sanitarian / Auditor Lingkungan:** Antarmuka Web untuk verifikasi hasil audit, input uji lab kualitas air/udara, pengawasan kepatuhan, dan approval tiket temuan.
3. **Tim Pemeliharaan Sarana / IPSRS:** Antarmuka Web/Mobile untuk menerima disposisi tiket perbaikan sarana ruangan dan memperbarui status progres pengerjaan.
4. **Manajemen / Direksi Faskes:** Antarmuka Web Dashboard untuk memantau ringkasan kepatuhan fasilitas, status TPS, serta mengunduh dokumen laporan berkala.

---

## 🧠 Second Brain & Knowledge Graph (Graphify)

Repositori ini telah terintegrasi dengan **Graphify** sebagai *Second Brain* dan *Knowledge Graph* persisten. Graphify memetakan seluruh modul, peran pengguna, alur proses, dan konsep arsitektur ke dalam graf relasi (*Nodes & Edges*), sehingga AI assistant dan tim developer dapat menavigasi struktur sistem tanpa kehilangan konteks.

### 1. Membuka Visualisasi Graf Interaktif
Visualisasi graf interaktif tersedia di [`graphify-out/graph.html`](./graphify-out/graph.html). Anda dapat membukanya langsung di browser tanpa perlu menjalankan web server:

* **Di macOS (Terminal):**
  ```bash
  open graphify-out/graph.html
  ```
* **Fitur Visualizer:**
  * **Search & Inspect:** Cari entitas (misal: `Checklist`, `Limbah B3`, `IPSRS`) di kolom pencarian sebelah kanan untuk melihat tetangga relasinya (*connected neighbors*).
  * **Color Clusters:** Node dikelompokkan otomatis berdasarkan komunitas pengetahuan (*Sanitasi*, *Inspeksi Lapangan*, *Dashboard Eksekutif*, dll.).
  * **Interactive Physics:** Node dapat digeser, diperbesar (*zoom in/out*), dan difilter per komunitas.

### 2. Berinteraksi & Query Graf dengan AI
Anda dapat memanfaatkan graf pengetahuan ini langsung di terminal atau melalui prompt asisten AI:

* **Mencari Jawaban Terkait Relasi Arsitektur:**
  ```bash
  graphify query "Bagaimana alur checklist QR terhubung dengan sistem tiket temuan IPSRS?"
  ```
* **Melihat Jalur Hubungan Terpendek Antar-Konsep:**
  ```bash
  graphify path "00_master_prd_modul_checklist_qr" "00_master_prd_kpi_mttr"
  ```
* **Melihat Penjelasan Detail Suatu Node:**
  ```bash
  graphify explain "00_master_prd_tps_limbah"
  ```

### 3. Memperbarui Graf Setelah Menambah/Mengubah Dokumen
Setiap kali Anda membuat atau memperbarui file Feature PRD di folder `features/`, perbarui graf pengetahuan dengan perintah:

```bash
# Update inkremental (hanya memproses dokumen baru/berubah)
graphify update .

# Atau generate ulang secara penuh
graphify extract .
graphify export html
```

### 4. File Output Graphify (`graphify-out/`)
* **[`graphify-out/graph.html`](./graphify-out/graph.html):** Visual graf interaktif untuk browser.
* **[`graphify-out/GRAPH_REPORT.md`](./graphify-out/GRAPH_REPORT.md):** Laporan analisis jaringan, *God Nodes*, kohesi komunitas, dan pertanyaan arsitektur kunci.
* **[`graphify-out/graph.json`](./graphify-out/graph.json):** Data mentah graf untuk kebutuhan konsumsi AI dan GraphRAG.

---

## 📖 Panduan Kontribusi Dokumentasi
- Semua perubahan strategis pada level sistem **harus** diselaraskan di [`00-MASTER-PRD.md`](./00-MASTER-PRD.md).
- Perubahan teknis spesifik (seperti penambahan kolom form, status tiket, atau validasi input) didokumentasikan langsung di masing-masing file pada folder `features/`.
- Setelah menambahkan dokumen baru, jalankan `graphify update .` untuk menyinkronkan graf pengetahuan.

