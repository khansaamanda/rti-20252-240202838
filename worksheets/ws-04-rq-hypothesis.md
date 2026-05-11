# WS-04: Research Question & Hypothesis

> **Bab 4 — Research Question, Contribution & Hypothesis**

---

## Ringkasan Materi

### RQ Bukan Pertanyaan Biasa

Research Question yang baik secara implisit mengandung cetak biru eksperimen: subjek, baseline, metrik, domain, dataset.

| Kualitas | Contoh |
|----------|--------|
| **Buruk** | "Bagaimana pengaruh deep learning terhadap deteksi malware?" |
| **Baik** | "Apakah CNN menghasilkan F1-Score lebih tinggi dari RF pada CIC-MalMem-2022?" |

Perbedaan: RQ yang baik menyebutkan **metode spesifik**, **metrik terukur**, **baseline**, dan **dataset**.

### Tiga Jenis RQ

| Jenis | Pola | Kebutuhan |
|-------|------|-----------|
| **Comparison** | A vs B → mana lebih baik? | ≥ 2 metode, metrik sama |
| **Improvement** | A' vs A → modifikasi lebih baik? | Pre/post, bukti perbaikan |
| **Exploratory** | Faktor X₁...Xₙ → pengaruh terhadap Y? | Multi-variabel, korelasi/regresi |

### Contribution Statement

Tiga jenis kontribusi: **Improvement** (metode terbukti lebih baik), **Comparison** (perbandingan sistematis yang belum ada), **Novel Approach** (pendekatan baru). Kontribusi harus terhubung langsung dengan gap — kontribusi tanpa gap = klaim tanpa justifikasi.

### Hypothesis H₀ / H₁

- **H₀** (Null) = Tidak ada perbedaan signifikan — asumsi default, harus dibuktikan salah
- **H₁** (Alternative) = Ada perbedaan signifikan — diterima hanya jika H₀ ditolak
- Harus **falsifiable**, mengandung **metrik terukur**, dirumuskan **SEBELUM eksperimen**

### Rantai Operasionalisasi

```
RQ → Variable → Metric → Data → Analysis
```

Jika rantai ini tidak lengkap, RQ belum mature. Bi-directional: RQ yang tidak bisa jadi hipotesis testable harus direvisi mundur.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan pertanyaan | Apa yang harus dibangun? | Apa yang harus dibuktikan? |
| Bentuk jawaban | Sistem yang berfungsi | Bukti empiris terukur |
| Sukses diukur oleh | User satisfaction, uptime | Signifikansi statistik, effect size |
| Jika gagal | Debug dan perbaiki | Laporkan, analisis mengapa |

### Istilah Penting

- **Research Question (RQ)** — Pertanyaan spesifik: variabel terukur + metrik + konteks
- **Contribution Statement** — Apa yang diketahui setelah riset selesai yang sebelumnya belum ada
- **H₀ / H₁** — Null vs Alternative Hypothesis
- **Falsifiability** — Kondisi hipotesis ditolak harus bisa didefinisikan sebelum eksperimen
- **Operationalization** — Proses mewujudkan konsep abstrak menjadi variabel terukur

---

## Template A.4 — RQ-Contribution-Hypothesis

```
RQ-CONTRIBUTION-HYPOTHESIS

Gap Statement  : Banyak organisasi kesulitan mengelola aset digital (perangkat lunak, data) secara optimal. Meskipun IoT menawarkan pemantauan otomatis, terdapat tantangan besar pada integrasi sistem serta masalah keamanan data (malware/ransomware) yang bisa menghambat efisiensi.

Research Question:
  Tipe         : [ ] Comparison  [ ] Improvement  [x] Exploratory
  Formulasi    : Bagaimana pengaruh teknologi IoT terhadap efisiensi manajemen aset digital secara real-time dan apa saja tantangan keamanan yang dihadapi?
  Variabel IV  : Penerapan Teknologi IoT.
  Variabel DV  : Efisiensi Manajemen Aset Digital (kecepatan, akurasi keputusan).
  Metrik       : Waktu respons, biaya operasional, tingkat deteksi ancaman.
  Dataset      : Studi literatur dari berbagai artikel jurnal dan laporan industri (seperti data Statista & Transforma Insights).
  Baseline     : Manajemen aset digital secara tradisional/manual (konvensional).

Quality Check RQ:
  [x] Variabel spesifik
  [x] Metrik jelas
  [x] Baseline ada
  [x] Konteks disebutkan
  [ ] Memerlukan eksperimen (bukan hanya survei literatur)

Contribution Statement:
  Apa yang baru diketahui : IoT terbukti meningkatkan efisiensi lewat pemeliharaan prediktif, namun butuh sistem keamanan kuat karena pertumbuhan perangkat IoT yang pesat meningkatkan risiko serangan siber.
  Jenis kontribusi        : [ ] Improvement  [x] Comparison  [ ] Novel approach
  Gap yang diisi          : Memberikan solusi atas ketidaktahuan organisasi dalam memanfaatkan data IoT untuk manajemen aset yang aman.

Hypothesis Pair:
  H₀ : Penerapan IoT tidak memberikan pengaruh signifikan terhadap efisiensi manajemen aset digital dibandingkan metode konvensional.
  H₁ : Penerapan IoT secara signifikan meningkatkan efisiensi (kecepatan dan akurasi) manajemen aset digital secara real-time.
  Threshold              : Peningkatan efisiensi minimal 20% (asumsi umum dalam riset manajemen) atau penurunan waktu respons ancaman.
  Justifikasi threshold  : Data simulasi menunjukkan penurunan waktu respons yang stabil seiring penggunaan sistem pemantauan real-time.
```

---

## Latihan 1 — Dari Gap ke RQ

Gunakan gap yang ditemukan di WS-03. Transformasikan menjadi Research Question.

**Gap dari WS-03:** Banyak organisasi kesulitan memanfaatkan data dari perangkat IoT secara optimal untuk mengelola aset digital karena adanya tantangan besar pada integrasi sistem serta ancaman keamanan seperti malware dan ransomware.

**RQ versi pertama (tulis bebas):**
> Apakah penggunaan teknologi IoT benar-benar bisa membuat pengelolaan aset digital di perusahaan jadi lebih efisien dan aman dari serangan siber?

**Evaluasi RQ:**

| Komponen | Ada? | Isi |
|----------|------|-----|
| Metode spesifik | Ya | Menggunakan teknologi IoT (sensor dan pemantauan langsung). |
| Metrik terukur | Belum | Kata "cepat" dan "aman" masih terlalu umum, perlu indikator angka. |
| Baseline | Ya | Dibandingkan dengan cara lama yang masih manual/pakai tenaga manusia. |
| Dataset/konteks | Ya | Fokus pada aset digital di sebuah organisasi atau kantor. |

**Tipe RQ:** [x] Exploratory (Mencari tahu pengaruh dan tantangan baru).  

**RQ versi revisi (setelah evaluasi):**
> Bagaimana penggunaan sensor IoT dapat mempercepat waktu deteksi kerusakan aset dan menurunkan biaya operasional kantor dibandingkan dengan cara pengecekan manual?

---

## Latihan 2 — Hypothesis Pair

Rumuskan pasangan hipotesis dari RQ di Latihan 1.

| Komponen | Isi |
|----------|-----|
| H₀ | Penggunaan sensor IoT tidak memberikan pengaruh pada kecepatan deteksi kerusakan aset dan biaya operasional dibandingkan cara manual. |
| H₁ | Penggunaan sensor IoT secara nyata mempercepat deteksi kerusakan aset dan menurunkan biaya operasional kantor. |
| Metrik | Waktu deteksi (dalam jam/menit) dan jumlah biaya perbaikan (dalam Rupiah). |
| Threshold | Peningkatan efisiensi minimal 20%. |
| Justifikasi threshold | Angka 20% dianggap angka standar yang cukup besar untuk membuktikan bahwa perubahan teknologi itu bermanfaat, bukan cuma kebetulan. |

**Apakah hipotesis ini falsifiable?** [x] Ya / [ ] Tidak
> Bagaimana cara membuktikannya salah? Jika setelah data dikumpulkan, ternyata waktu deteksi tetap lama atau biaya operasional malah jadi lebih mahal (karena biaya perawatan alat IoT-nya sangat tinggi), maka pernyataan H₁ otomatis salah dan kita harus tetap memakai cara manual (H₀).

---

## Latihan 3 — Rantai Operasionalisasi

Lengkapi rantai dari RQ hingga metode analisis.

| Tahap | Isi |
|-------|-----|
| RQ | Bagaimana penggunaan sensor IoT mempercepat waktu deteksi kerusakan aset dan menurunkan biaya operasional kantor dibandingkan cara manual? |
| Variable (IV) | Metode Pengelolaan: (Penerapan teknologi IoT vs. Cara Konvensional/Manual). |
| Variable (DV) | Efisiensi Manajemen: (Waktu deteksi masalah dan Biaya operasional). |
| Metric | Waktu: Menit/Jam sejak kerusakan terjadi hingga terdeteksi. Biaya: Pengeluaran rutin untuk pengecekan dan perbaikan (Rupiah). |
| Data source | Laporan riwayat perbaikan aset, log sensor IoT, dan catatan pengeluaran operasional organisasi. |
| Analysis method | Analisis Komparatif: Membandingkan rata-rata waktu dan biaya antara periode manual dengan periode setelah pakai IoT. |

**Apakah rantai lengkap?** [x] Ya / [ ] Tidak
> Jika tidak, tahap mana yang perlu direvisi? Rantai sudah lengkap karena setiap tahap (dari variabel sampai cara analisis) sudah saling mendukung untuk menjawab pertanyaan penelitian (RQ).

---

## Refleksi

> Ambil satu judul skripsi/paper yang pernah dibaca. Coba ekstrak RQ-nya. Apakah RQ tersebut memenuhi semua komponen (metode, metrik, baseline, konteks)? Jika tidak, apa yang hilang?

**Judul:** Pengaruh Teknologi Internet of Things Terhadap Manajemen Aset Digital Secara Real-Time.
**RQ yang diekstrak:** pakah penerapan IoT memberikan dampak signifikan dalam meningkatkan efisiensi manajemen aset digital secara real-time?
**Komponen yang hilang:** Dalam artikel tersebut, yang hilang adalah Metrik Kuantitatif yang Spesifik dan Dataset Primer.
