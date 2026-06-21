# WS-09: Implementation & Environment

> **Bab 9 — Implementasi Riset & Kontrol Lingkungan**

---

## Ringkasan Materi

### Implementasi Riset ≠ Coding Biasa

Tujuan implementasi riset bukan membuat software yang berfungsi, melainkan membangun **instrumen pengukuran yang konsisten**. Setiap modul harus di-mapping ke variabel (dari Bab 6), parameter harus config-driven, dan logging aktif dari hari pertama.

### Reproducible Implementation Model

```
Design → Implementation → Environment Setup → Execution Consistency → Reproducibility → Trustworthy Result
```

Setiap transisi memiliki syarat:
- Design → Implementation: kode sesuai mapping variabel-ke-komponen
- Implementation → Environment: versi, dependency, seed, path, OS eksplisit
- Environment → Consistency: seed terkunci, urutan deterministik
- Consistency → Reproducibility: dokumentasi lengkap
- Reproducibility → Trust: siapa pun ikuti dokumentasi → hasil sama/serupa

### Repeatability vs Reproducibility

| Level | Peneliti | Environment | Hasil |
|-------|---------|-------------|-------|
| **Repeatability** | Sama | Sama | Sama persis |
| **Reproducibility** | Berbeda | Berbeda (ikuti docs) | Sama/serupa |

Capai **repeatability** dulu, baru **reproducibility**.

### Engineering vs Research Perspective

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan | Sistem berfungsi untuk user | Instrumen pengukuran konsisten |
| Dependency | Update ke terbaru | Lock di versi spesifik |
| Testing | Unit, integration, E2E | Repeatability test (run ulang → sama?) |
| Dokumentasi | User guide, API docs | Environment spec, execution steps, expected output |
| Config | Default masuk akal | Setiap parameter eksplisit & adjustable |

### Jebakan Kognitif

1. Menunda environment setup → bug sulit dilacak
2. Tidak pakai version control → hasil tidak bisa direkonstruksi
3. Menolak Docker/container → "di laptop saya bisa" saat review
4. 3× hasil sama ≠ repeatable (bisa cache/state tersimpan)

### Istilah Penting

- **Environment Specification** — Deskripsi lengkap: hardware, OS, runtime, library + versi, config, seed
- **Dependency** — Komponen eksternal yang harus di-lock versinya
- **Config-driven** — Parameter dieksternalisasi ke file konfigurasi, bukan hardcode

---

## Template A.9 — Dokumentasi Setup Eksperimen

```
EXPERIMENT SETUP DOCUMENTATION

Hardware:
  CPU     : Intel Core i5-1135G7 @ 2.40GHz (4 Cores, 8 Threads)
  RAM     : 16 GB DDR4 3200MHz
  GPU     : Intel Iris Xe Graphics (CPU-only untuk analisis data teks)
  Storage : 512 GB NVMe PCIe SSD

Software:
  OS        : Windows 11 Home 64-bit
  Runtime   : Python 3.10.11
  Framework : Jupyter Notebook / Anaconda Environment

Dependencies:
| Library | Version | Sumber | Hash/Checksum |
|---------|---------|--------|---------------|
|pandas|2.0.3|PyPI|sha256:e6a92b|
|numpy|1.24.3|PyPI|sha256:b891cf|

Konfigurasi:
  Config file     : config.json
  Random seed     : 42
  Hyperparameters : data_interval: "realtime", baseline: "traditional_manual", threshold_seconds: 5

Reproducibility Check:
  [x] Dependency terdokumentasi (requirements.txt / lock file)
  [x] Seed ditetapkan di semua level (Python, NumPy, framework)
  [x] Config di version control
  [x] README instruksi reproduksi lengkap
```

---

## Latihan 1 — Environment Specification

Dokumentasikan environment untuk eksperimen Anda (boleh environment saat ini atau yang direncanakan).

| Komponen | Spesifikasi |
|----------|------------|
| CPU | Intel Core i5-1135G7 @ 2.40GHz (4 Cores, 8 Threads) |
| RAM | 16 GB DDR4 |
| GPU | Intel Iris Xe Graphics (CPU-only untuk analisis data) |
| OS | Windows 11 Home 64-bit |
| Runtime | Python 3.10.11 |
| Framework | Jupyter Notebook / Anaconda Environment |
| Random Seed | 42 |

**Dependencies (minimal 5):**

| Library | Version | Alasan Dibutuhkan |
|---------|---------|-------------------|
| pandas | 2.0.3 | Digunakan untuk membaca, membersihkan, dan mengolah data simulasi dalam bentuk tabel. |
| numpy | 1.24.3 | Menyediakan fungsi matematika dan mengunci kestabilan urutan angka acak (random seed). |
| matplotlib | 3.7.2 | Digunakan untuk membuat visualisasi utama seperti grafik tren atau diagram batang hasil riset. |
| seaborn | 0.12.2 | Membantu mempercantik tampilan grafik analisis agar lebih mudah dibaca dan dipahami. |
| scikit-learn | 1.3.0 | Digunakan untuk kebutuhan pemodelan statistik atau evaluasi metrik tren data sederhana. |

---

## Latihan 2 — Repeatability Test Plan

Rancang tes repeatability sederhana: jalankan kode yang sama 3× di environment yang sama.

| Run | Seed | Metrik Utama | Hasil Sama? |
|-----|------|-------------|-------------|
| 1 | 42 | Waktu Respons Deteksi (detik) | — |
| 2 | 42 | Waktu Respons Deteksi (detik) | [x] Ya / [ ] Tidak |
| 3 | 42 | Waktu Respons Deteksi (detik) | [x] Ya / [ ] Tidak |

**Jika hasil berbeda, kemungkinan penyebab:**
> 1. Random state tidak dikunci di semua pustaka: Pengaturan seed hanya dilakukan pada program Python bawaan, tetapi lupa dikunci pada pustaka numpy atau scikit-learn yang bertugas mengacak data simulasi.
2. Variabel sisa di memori (Cache): Jupyter Notebook tidak dibersihkan atau di-restart sebelum menjalankan ulang, sehingga data dari proses (run) pertama masih tersimpan dan memengaruhi perhitungan berikutnya.
3. Gangguan proses latar belakang (Background process): Komputer tiba-tiba menjalankan pembaruan sistem (OS update) otomatis atau pemindaian antivirus di tengah-tengah pengujian yang memengaruhi kecepatan pemrosesan simulasi.


**Checklist kontrol yang sudah diterapkan:**
- [x] Random seed di-set di semua level
- [x] Tidak ada background process yang mengganggu
- [x] Cache dibersihkan antar-run
- [x] Config file yang sama untuk semua run

---

## Latihan 3 — README Eksperimen

Tulis README minimum untuk eksperimen Anda (6 komponen wajib).

```
# Judul Eksperimen: Simulasi Pengaruh IoT Terhadap Waktu Respons Keamanan Aset Digital

## 1. Environment
> - CPU: Intel Core i5-1135G7 @ 2.40GHz (4 Cores, 8 Threads)
- RAM: 16 GB DDR4
- GPU: Intel Iris Xe Graphics (CPU-only)
- OS: Windows 11 Home 64-bit
- Runtime: Python 3.10.11
- Framework: Jupyter Notebook / Anaconda Environment
- Pustaka Utama: pandas (2.0.3), numpy (1.24.3), matplotlib (3.7.2), seaborn (0.12.2), scikit-learn (1.3.0)

## 2. Installation
> Silakan pasang seluruh pustaka yang diperlukan dengan menjalankan perintah berikut di terminal:
```bash
pip install pandas==2.0.3 numpy==1.24.3 matplotlib==3.7.2 seaborn==0.12.2 scikit-learn==1.3.0

## 3. Data
> Eksperimen ini menggunakan data sekunder berupa file log simulasi bernama iot_asset_logs.csv. Data tersebut mencakup catatan waktu respon deteksi ancaman sebelum dan setelah integrasi sensor pintar IoT dengan ukuran file sekitar 150 KB (format teks terpisah koma).

## 4. Execution
> Untuk menjalankan simulasi dan menghasilkan grafik analisis, eksekusi perintah berikut pada terminal: python run_simulation.py

## 5. Configuration
> Semua pengaturan eksperimen disimpan dalam file config.json. Beberapa parameter kunci yang digunakan meliputi:
1. random_seed: 42 (untuk mengunci konsistensi urutan data acak)
2. data_interval: "realtime"
3. baseline_system: "traditional_manual"

## 6. Expected Output
> File gambar grafik_respons_keamanan.png yang menampilkan grafik garis penurunan waktu respon penanganan ancaman (dalam satuan detik).
Pesan teks ringkasan di terminal yang menampilkan rata-rata tingkat efisiensi pemantauan aset dalam persen (%).
```

---

## Refleksi

> Apakah eksperimen Anda saat ini bisa direproduksi oleh orang lain tanpa bantuan Anda? Komponen apa yang masih hilang?

**Level saat ini:** [x] Repeatability / [ ] Reproducibility / [ ] Belum keduanya
**Komponen yang belum terdokumentasi:**
> 1. Dokumen isolasi lingkungan otomatis seperti **Docker** atau file snapshot lingkungan **Conda** (`environment.yml`) belum dibuat. Hal ini berisiko menimbulkan error jika dijalankan pada sistem operasi yang berbeda (seperti Linux atau macOS).
2. File parameter konfigurasi luar (`config.json`) belum sepenuhnya terpisah, karena sebagian kecil parameter masih ditulis manual langsung di dalam baris kode utama (*hardcoded*).