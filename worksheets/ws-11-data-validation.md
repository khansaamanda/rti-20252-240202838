# WS-11: Data Validation & Integrity

> **Bab 11 — Validasi Data & Integritas**

---

## Ringkasan Materi

### Data Trust Model

```
Raw Data → Data Cleaning → Consistency Check → Validation Process → Trusted Data
```

Data mentah belum bisa dipercaya. Harus melewati pipeline validasi sebelum siap untuk analisis statistik.

### Empat Pilar Data Quality

| Pilar | Deskripsi | Contoh Pelanggaran |
|-------|----------|-------------------|
| **Accuracy** | Nilai dalam range masuk akal | Akurasi = 1.5 (di luar [0,1]) |
| **Consistency** | Format seragam di semua run | Run 1: CSV, Run 2: JSON |
| **Completeness** | Tidak ada data hilang dari plan | 97 dari 100 run tercatat |
| **Validity** | Data sesuai desain eksperimen | Parameter baseline tercampur treatment |

### Proses Validasi Progresif

1. **Format validation** — Tipe file, header, kolom
2. **Range validation** — Nilai dalam batas logis
3. **Consistency validation** — Format seragam antar-run
4. **Logic validation** — Data cocok dengan desain eksperimen

Jika gagal di langkah awal → tidak perlu lanjut.

### Anomaly Detection — 3 Jenis

| Jenis | Deskripsi | Deteksi |
|-------|----------|---------|
| **Statistical outlier** | Nilai di luar distribusi normal | IQR: < Q1-1.5×IQR atau > Q3+1.5×IQR |
| **Contextual anomaly** | Normal absolut, abnormal dalam konteks | Run 1-10: ~91%, Run 11-20: ~88% |
| **Pattern anomaly** | Pola sistematis (bukan random) | Performa menurun berurutan |

**Prinsip:** Detect → Investigate → Document → Decide — **JANGAN langsung hapus.**

### Engineering vs Research Validation

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan | Data sesuai spesifikasi bisnis | Data layak untuk analisis statistik |
| Missing data | Impute / set default | Investigasi penyebab → dokumentasi |
| Outlier | Bug → fix | Mungkin temuan → investigasi |
| Dokumentasi | Minimal (log error) | Komprehensif (anomali + keputusan) |

### Jebakan Kognitif

1. "Logging otomatis ≠ data benar" → bisa ada bug di logger
2. "Outlier = hapus" → bisa jadi temuan penting
3. "Dataset kecil tidak perlu validasi" → justru lebih rentan
4. "Mean normal = data benar" → [94, 95, 93, **44**, 94] → mean 84% terlihat wajar

---

## Template A.11 — Data Validation Checklist

```
DATA VALIDATION CHECKLIST

Completeness:
  [ ] Semua skenario tercakup
  [ ] Jumlah run sesuai rencana
  [ ] Tidak ada file output hilang
  Missing: 3 dari 40 data points

Format Consistency:
  [x] Semua file format sama (CSV/JSON/...)
  [x] Header konsisten
  [x] Tipe data konsisten (numerik tetap numerik)

Range & Logic:
  [ ] Nilai dalam range masuk akal
  [x] Tidak ada waktu negatif
  [x] Metrik 0–100%, tidak di luar range
  Anomali ditemukan: Run 4 drop ke 78.3% akibat mesin kepanasan (thermal throttling).

Cross-Validation:
  [x] Run identik → hasil mendekati
  [x] Trend konsisten dengan ekspektasi teori

Keputusan:
  [ ] Data siap analisis
  [ ] Perlu cleaning
  [x] Perlu re-run (skenario: LSTM, DS-3 [run 7 & 9], Transformer, DS-4 [run 10], dan sampel Run 4)
```

---

## Latihan 1 — Completeness Check

Verifikasi apakah semua data yang direncanakan sudah terkumpul.

| Skenario | Run Direncanakan | Run Tercatat | Missing | Alasan |
|----------|-----------------|-------------|---------|--------|
| BERT, DS-1 | 10 | 10 | 0 | — |
| LSTM, DS-3 | 10 | 8 | 2 | OOM (Out of Memory) pada run 7 & 9 |
| ResNet, DS-2 | 10 | 10 | 0 | — |
| Transformer, DS-4 | 10 | 9 | 1 | Koneksi server terputus saat run terakhir |

**Total expected:** 40 | **Total actual:** 37 | **Missing:** 3

**Keputusan untuk data missing:**
> saya akan melakukan re-run (menjalankan ulang) pada run yang gagal (LSTM run 7 & 9, serta Transformer run 10) setelah memperbaiki kapasitas memori dan memastikan koneksi server stabil. Jangan diabaikan begitu saja agar hasil analisis akhir tidak bias.

---

## Latihan 2 — Anomaly Investigation

Periksa data Anda untuk anomali. Gunakan metode IQR atau z-score.

**Dataset sampel (atau data Anda sendiri):**

| Run | Accuracy (%) |
|-----|-------------|
| 1 | *91.2* |
| 2 | *90.8* |
| 3 | *91.5* |
| 4 | *78.3* |
| 5 | *91.0* |

**Deteksi outlier:**
- Q1 = 90.8 | Q3 = 91.2 | IQR = 0.4
- Batas bawah (Q1 - 1.5×IQR) = 90.8 - 0.6 = 90.2
- Batas atas (Q3 + 1.5×IQR) = 91.2 + 0.6 = 91.8
- Outlier terdeteksi: Run 4 (78.3%)

**Investigasi (untuk setiap outlier):**

| Outlier | Nilai | Kemungkinan Penyebab | Keputusan |
|---------|-------|---------------------|-----------|
| Run 4 | 78.3 | Thermal throttling (prosesor kepanasan dan menurunkan performa otomatis) karena berjalan nonstop tanpa jeda di 3 run sebelumnya. |

---

## Latihan 3 — Validation Report

Buat laporan validasi ringkas untuk dataset eksperimen Anda.

**1. Completeness:** 92.5% data terkumpul (37 dari 40 run).
**2. Format:** [x] Konsisten / [ ] Ada inkonsistensi
**3. Range check (anomali):** Terdeteksi 1 data aneh (outlier) pada Run 4 dengan nilai 78.3%.
**4. Logic check:** [x] Parameter sesuai plan / [ ] Ada ketidaksesuaian

**Kesimpulan:** [ ] Data siap analisis / [x] Perlu tindakan: Jalankan ulang (re-run) 3 data yang hilang karena kendala teknis dan 1 data outlier yang drop akibat mesin kepanasan sebelum lanjut ke tahap analisis statistik.

---

## Refleksi

> Apa perbedaan antara "data yang benar" dan "data yang dipercaya"? Mengapa proses validasi formal diperlukan meskipun data dikumpulkan secara otomatis?

> Data yang benar adalah data asli apa adanya yang terekam oleh sistem komputer. Data ini bisa saja mengandung eror, salah format, atau drop akibat gangguan teknis (seperti nilai 78.3% di atas).

Data yang dipercaya (Trusted Data) adalah data yang sudah melalui proses penyaringan dan validasi formal. Data ini dipastikan lengkap, masuk akal secara logika, dan siap digunakan untuk mengambil keputusan tanpa risiko menyesatkan.
> Karena sistem otomatis (logger) dibuat oleh manusia yang tidak luput dari bug atau gangguan lingkungan. Otomatis merekam bukan berarti otomatis datanya bersih dan masuk akal. Tanpa validasi formal, kita bisa saja terjebak mengira performa model kita buruk, padahal aslinya komputer kita cuma sedang kepanasan (thermal throttling) saat merekam data tersebut!
