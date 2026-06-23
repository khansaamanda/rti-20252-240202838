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
| GPU | Intel Iris Xe Graphics (CPU-only) |
| OS | Windows 11 Home 64-bit |
| Runtime | Python 3.10.11 |
| Framework | Jupyter Notebook / Anaconda Environment |
| Random Seed | 42 |

**Dependencies (minimal 5):**

| Library | Version | Alasan Dibutuhkan |
|---------|---------|-------------------|
| pandas | 2.0.3 | Digunakan untuk membaca, membersihkan, dan mengolah data simulasi dalam bentuk tabel.Membaca file CSV hasil kuesioner (Google Form), membersihkan data kosong, dan mengubah format jawaban ke angka (Skala Likert). |
| numpy | 1.24.3 | Menghitung statistik dasar seperti nilai rata-rata (mean) dan standar deviasi dari jawaban responden. |
| matplotlib | 3.7.2 | Membuat grafik batang (bar chart) untuk memvisualisasikan persentase jawaban kuesioner. |
| seaborn | 0.12.2 | Membantu menampilkan diagram distribusi jawaban responden agar lebih menarik dan mudah dibaca di dalam laporan. |
| scikit-learn | 1.11.1 | Digunakan untuk melakukan uji statistik sederhana (seperti menghitung nilai p-value untuk melihat seberapa valid hubungan data tersebut). |

---

## Latihan 2 — Repeatability Test Plan

Rancang tes repeatability sederhana: jalankan kode yang sama 3× di environment yang sama.

| Run | Seed | Metrik Utama | Hasil Sama? |
|-----|------|-------------|-------------|
| 1 | 42 | Nilai Rata-Rata Kepuasan & Nilai P-Value Uji Statistik | — |
| 2 | 42 | Nilai Rata-Rata Kepuasan & Nilai P-Value Uji Statistik | [x] Ya / [ ] Tidak |
| 3 | 42 | Nilai Rata-Rata Kepuasan & Nilai P-Value Uji Statistik | [x] Ya / [ ] Tidak |

**Jika hasil berbeda, kemungkinan penyebab:**
> 1. Random state tidak dikunci di semua pustaka: Pengaturan seed hanya dilakukan pada program Python bawaan, tetapi lupa dikunci pada pustaka seperti scikit-learn (jika ada proses pembagian data acak dari hasil kuesioner).
2. Variabel sisa di memori (Cache): Jupyter Notebook tidak dibersihkan atau di-restart sebelum menjalankan ulang, sehingga data perhitungan statistik dari proses (run) pertama masih tersimpan dan memengaruhi perhitungan berikutnya.
3. Perubahan pada file data sumber: Terdapat penambahan baris data baru ke dalam file respons_kuesioner_iot.csv (misalnya ada responden yang baru mengumpulkan form) tepat saat skrip sedang dijalankan ulang, sehingga memengaruhi nilai rata-rata akhir.


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
> Eksperimen ini menggunakan data primer riil dari hasil penyebaran kuesioner bernama respons_kuesioner_iot.csv.
1. Sumber Data: Hasil survei kepada 50 responden (staf IT dan manajer pengelola aset digital).
2. Format: File teks terpisah koma (.csv) dengan ukuran sekitar 25 KB.
3. Isi Data: Nilai skala Likert (1-5) mengenai persepsi kemudahan, kecepatan respon pelacakan aset, dan tingkat keamanan setelah menggunakan sistem berbasis IoT.

## 4. Execution
> Untuk memproses data kuesioner, melakukan uji statistik, dan menampilkan grafik distribusi jawaban, jalankan perintah berikut:
Bash
python analyze_survey.py

Bash

## 5. Configuration
> Semua pengaturan analisis disimpan dalam file config.json. Beberapa parameter kunci yang digunakan meliputi:
1. random_seed: 42 (untuk mengunci konsistensi saat pembagian data uji jika diperlukan)
2. alpha_level: 0.05 (batas signifikansi uji statistik)
3. target_variable: "efisiensi_manajemen_aset"

## 6. Expected Output
>File gambar grafik_distribusi_persepsi.png yang menampilkan diagram batang persentase persetujuan responden terhadap efisiensi IoT.
Output teks di terminal yang menunjukkan nilai validitas, reliabilitas kuesioner, serta hasil uji hipotesis (nilai p-value).
```

---

## Refleksi

> Apakah eksperimen Anda saat ini bisa direproduksi oleh orang lain tanpa bantuan Anda? Komponen apa yang masih hilang?

**Level saat ini:** [x] Repeatability / [ ] Reproducibility / [ ] Belum keduanya
**Komponen yang belum terdokumentasi:**
> 1. Dokumen isolasi lingkungan otomatis seperti **Docker** atau file pengaturan **Conda** (`environment.yml`) belum dibuat. Hal ini penting agar orang lain yang menggunakan sistem operasi berbeda tidak mengalami kendala versi pustaka saat membaca data kuesioner.
2. Kode pembersihan data (*data cleaning*) untuk menyaring jawaban kuesioner yang tidak lengkap/kosong masih menyatu di dalam skrip utama, belum dipisahkan menjadi modul tersendiri.