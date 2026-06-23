# WS-10: Experiment Execution & Data Collection

> **Bab 10 — Eksekusi Eksperimen & Pengumpulan Data**

---

## Ringkasan Materi

### Experiment Execution Pipeline

```
Design → Execution Plan → Controlled Execution → Data Collection → Data Logging → Dataset for Analysis
```

### Multiple Run = Non-Negotiable

Single run **tidak pernah cukup** untuk klaim ilmiah. Minimum 5-10 run per skenario dengan seed berbeda. Multiple run menghasilkan:
- Mean, std, confidence interval
- Distribusi hasil → uji statistik
- Variabilitas → error bar di grafik

### Execution Plan

Setiap eksperimen harus memiliki plan sebelum eksekusi:
- Daftar skenario
- Jumlah run per skenario
- Random seed per run (pre-determined!)
- Urutan eksekusi (randomisasi/counterbalancing)
- Pre-execution checklist

### Data Logging Komprehensif

Setiap run menghasilkan log terstruktur:
1. **Identitas** — Run ID, timestamp, skenario
2. **Konfigurasi** — Semua parameter, seed, code version
3. **Hasil** — Semua metrik, output detail
4. **Metadata** — Waktu eksekusi, resource usage, warning/error

Format: CSV/JSON/database — **bukan stdout yang di-copy-paste**.

### Engineering vs Research Execution

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Run | Sekali (deploy) | Multiple (min 5-10, seed berbeda) |
| Logging | Error log, access log | Semua parameter, metrik, metadata |
| Anomali | Bug → fix → redeploy | Investigasi → dokumentasi → analisis |
| Urutan | Tidak penting | Bisa bias — perlu randomisasi |

### Anomali = Dokumentasi, Bukan Hapus

Run gagal/anomali tidak boleh dihapus tanpa dokumentasi. Bisa jadi:
- **Bug** → fix & re-run (dokumentasikan!)
- **Batas kemampuan metode** → DNF = temuan
- **Data yang bias** jika hanya simpan run "berhasil"

### Jebakan Kognitif

1. "Satu angka cukup" → tanpa distribusi, tidak bisa diuji
2. "Seed tidak penting" → bahkan algoritma deterministik bisa dipengaruhi library stokastik
3. "Run gagal langsung hapus" → kehilangan temuan potensial
4. "Semua run harus hari ini" → thermal throttling, fatigue

---

## Template A.10 — Execution Plan & Data Log

```
EXECUTION PLAN

| Run # | Skenario | Seed | Parameter | Status | Waktu | Output File |
|-------|----------|------|-----------|--------|-------|-------------|
| 1     |Bootstrapping Data Kuesioner|42|sample=30, alpha=0.05|Planned|10:00|log_run_1.json|
| 2     |Bootstrapping Data Kuesioner|123|sample=30, alpha=0.05|Planned|10:05|log_run_2.json|
| 3     |Bootstrapping Data Kuesioner|2026|sample=30, alpha=0.05|Planned|10:10|log_run_3.json|
| 4  |Bootstrapping Data Kuesioner|777|sample=30, alpha=0.05|Planned|10:15|log_run_4.json|

Jumlah runs per skenario : 5
Total runs               : 5

DATA LOG (per run):
  Run ID    : run-survey-001
  Timestamp : 2026-06-23T10:00:00
  Skenario  : Bootstrapping Data Kuesioner Mahasiswa (Run 1)
  Input     : respons_kuesioner_iot_mahasiswa.csv
  Output    : p_value=0.024, cronbach_alpha=0.82, r_square=0.45
  Anomali   : Tidak ada anomali, semua baris data terbaca penuh.
  Catatan   : Hasil pada run awal menunjukkan pengaruh yang signifikan dan reliabilitas tinggi.
```

---

## Latihan 1 — Execution Plan

Susun execution plan untuk eksperimen Anda. Tentukan skenario, jumlah run, dan seed sebelum eksekusi.

| Run # | Skenario | Seed | Parameter Kunci | Status |
|-------|----------|------|----------------|--------|
| 1 | Bootstrapping Data Kuesioner | 42 | sample_size=30, alpha=0.05 | Completed |
| 2 | Bootstrapping Data Kuesioner | 123 | sample_size=30, alpha=0.05 | Completed |
| 3 | Bootstrapping Data Kuesioner  | 2026 | sample_size=30, alpha=0.05 | Completed |
| 4 | Bootstrapping Data Kuesioner | 777 | sample_size=30, alpha=0.05 | Completed |
| 5 | Bootstrapping Data Kuesioner | 999 | sample_size=30, alpha=0.05 | Completed |

**Total skenario:** 1 (Analisis Konsistensi Statistik Kuesioner)
**Run per skenario:** 5
**Total run keseluruhan:** 5

---

## Latihan 2 — Data Log Terstruktur

Desain format data log untuk eksperimen Anda. Tentukan field apa saja yang akan dicatat.

**Identitas:**
| Field | Contoh |
|-------|--------|
| Run ID | run-survey-001 |
| Timestamp | 2026-06-23T10:00:00 |
| Script Name | analyze_survey.py |

**Konfigurasi:**
| Field | Contoh |
|-------|--------|
| Seed | 42 |
| Code version | commit 5a2b13f |
| Sample Size | 30 |

**Hasil:**
| Metrik | Tipe Data | Range Valid |
|--------|----------|-------------|
| Cronbach's Alpha (Reliabilitas) | float | 0.0 – 1.0 |
| Nilai P-Value (Signifikansi) | float | 0.0 – 1.0 |
| Nilai R-Square (Besar Pengaruh) | float | 0.0 – 1.0 |

**Format output:** [ ] CSV / [x] JSON / [ ] Database / [ ] Lainnya: ____

---

## Latihan 3 — Anomaly Protocol

Rencanakan bagaimana menangani anomali. Untuk setiap jenis, tentukan langkah yang diambil.

| Jenis Anomali | Contoh | Tindakan |
|---------------|--------|----------|
| Run gagal (crash) | File CSV tidak terbaca karena pemisah kolom (delimiter) salah atau ada karakter aneh. | Dokumentasikan pesan error, bersihkan karakter yang rusak (data cleaning) pada file CSV, lalu jalankan ulang skrip. |
| Hasil ekstrem | Nilai reliabilitas (Cronbach's Alpha) sangat rendah, misalnya jatuh di bawah 0.5. | Identifikasi pertanyaan yang membingungkan responden melalui matriks korelasi, catat sebagai temuan keterbatasan kuesioner, dan jangan hapus data asli. |
| Waktu eksekusi anomali | Proses pengambilan sampel ulang (resampling) macet/freeze karena perulangan tanpa batas di Python. | Hentikan paksa proses (Ctrl+C), perbaiki batasan iterasi pada kode fungsi, lalu jalankan ulang (re-run). |
| Inkonsistensi dengan run lain | Nilai p-value berubah drastis antar seed (misal run 1 lolos uji, run 2 gagal). | Periksa apakah ada jawaban responden yang sangat menyimpang (outlier), hitung rata-rata hasil dari semua run, dan catat variasi ini sebagai efek dari ukuran sampel. |

**Prinsip:** Detect → Investigate → Document → Decide

---

## Refleksi

> Pernahkah Anda melaporkan hasil riset/tugas dari single run? Apa risikonya? Bagaimana multiple run mengubah kepercayaan terhadap hasil?

**Pengalaman sebelumnya:**
> Ya, dalam tugas sebelumnya saya sering hanya menjalankan kode satu kali saja (single run) dan langsung menyalin angkanya ke dalam laporan. Risikonya, angka tersebut bisa jadi hanya sebuah kebetulan karena urutan datanya sedang pas. Jika data tersebut diacak ulang atau dijalankan di komputer yang berbeda, hasilnya bisa berubah dan membuat kesimpulan riset menjadi rapuh atau tidak valid.
**Yang akan dilakukan berbeda:**
> Pada riset ini, saya menerapkan eksekusi berulang (multiple run) menggunakan teknik pengacakan teratur yang dikunci (seed). Dengan cara ini, hasil pengolahan data kuesioner tidak hanya bergantung pada tebakan satu angka mutlak, melainkan memiliki bukti konsistensi nilai rata-rata (mean) dan rentang yang stabil. Hal ini membuat analisis data saya menjadi jauh lebih jujur, ilmiah, dan dapat dipertanggungjawabkan saat sidang atau evaluasi.