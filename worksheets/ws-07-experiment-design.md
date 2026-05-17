# WS-07: Experimental Design & Validity

> **Bab 7 — Experimental Design & Validity**

---

## Ringkasan Materi

### Correlation ≠ Causality

Kausalitas membutuhkan 3 syarat:
1. **Covariance** — X dan Y bergerak bersama
2. **Temporal precedence** — X berubah sebelum Y
3. **Elimination of alternatives** — Tidak ada faktor lain yang menjelaskan Y

Controlled experiment adalah satu-satunya metode yang bisa membuktikan kausalitas.

### Empat Jenis Validitas

| Jenis | Pertanyaan | Ancaman Umum |
|-------|-----------|-------------|
| **Internal** | Apakah hubungan IV→DV nyata? | Confounding variable, selection bias |
| **External** | Apakah bisa digeneralisasi? | Dataset terlalu spesifik |
| **Construct** | Apakah mengukur konsep yang benar? | Metrik tidak sesuai |
| **Conclusion** | Apakah kesimpulan statistik valid? | Sample size kecil, uji salah |

Internal dan external validity sering berkonflik: semakin terkontrol (internal kuat) → semakin artificial (external lemah).

### Tiga Tipe Eksperimen dalam Riset TI

| Tipe | Deskripsi | Kapan Digunakan |
|------|----------|----------------|
| **Comparison Study** | Metode A vs B pada kondisi identik | Membandingkan pendekatan berbeda |
| **Ablation Study** | Full system → lepas komponen satu per satu | Mengukur kontribusi tiap komponen |
| **Parameter Study** | Variasikan satu parameter, amati dampak | Uji sensitifitas/robustness |

### Fairness dalam Perbandingan

Perbandingan yang adil = **kondisi identik** untuk semua metode: dataset sama, preprocessing sama, tuning effort sebanding, environment sama, metrik sama.

Contoh tidak adil: Transformer (30 fitur tambahan + Bayesian optimization) vs RF (default params) → hasilnya misleading.

### Threats to Validity = Diidentifikasi Sebelum Eksperimen

Ancaman validitas harus diidentifikasi **sebelum** eksperimen dan mitigasinya dirancang sebagai bagian dari desain — bukan ditulis sebagai boilerplate setelah selesai.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan testing | Memastikan sistem memenuhi requirement | Membuktikan hubungan kausal antar variabel |
| Baseline | Versi sebelumnya (last release) | Metode tervalidasi dari literatur |
| Kegagalan | Bug → fix → release | H₀ tidak ditolak → tetap kontribusi ilmiah |
| Sukses | 100% test pass | Evidence valid — mendukung atau menolak hipotesis |

### Istilah Penting

- **Causality** — Hubungan sebab-akibat (covariance + temporal + elimination)
- **Controlled Experiment** — Ubah satu variabel, kontrol sisanya, amati efek
- **Fairness** — Semua metode diuji pada kondisi yang benar-benar identik
- **Threats to Validity** — Faktor yang bisa melemahkan kesimpulan jika tidak dimitigasi
- **Conclusion Validity** — Validitas statistik: power, sample size, uji yang tepat

---

## Template A.7 — Desain Eksperimen Lengkap

```
EXPERIMENT DESIGN

Research Question : Bagaimana penerapan teknologi Internet of Things (IoT) memengaruhi efisiensi manajemen aset digital secara real-time? [cite: 7]
Hypothesis        : Penerapan IoT secara real-time memberikan dampak signifikan dalam meningkatkan efisiensi manajemen aset digital (menurunkan biaya operasional dan mempercepat respons), dengan syarat didukung sistem keamanan yang kuat[cite: 11, 13, 153].
Tipe Eksperimen   : [x] Comparison  [ ] Ablation  [ ] Parameter

Kondisi Eksperimen:
| Kondisi | Deskripsi | IV Value | CV Settings |
|---------|-----------|----------|-------------|
| Control | Manajemen aset menggunakan cara konvensional/lama[cite: 187]. | Tanpa teknologi IoT (Proses manual dan terpusat)[cite: 63, 168]. | Jenis aset digital yang sama (perangkat lunak, file, data)[cite: 41, 67]. |
| Treatment | Manajemen aset menggunakan teknologi modern[cite: 44, 64]. | Dengan perangkat IoT (Sensor, RFID, GPS, otomatisasi real-time)[cite: 8, 38, 55]. | Jenis aset digital yang sama (perangkat lunak, file, data)[cite: 41, 67]. |

Fairness Checklist:
  [x] Dataset identik untuk semua kondisi (Aset digital & data yang dipantau sama jenis dan jumlahnya)[cite: 41, 67].
  [x] Preprocessing setara (Standar pencatatan awal kondisi fisik atau log digital diposisikan sama)[cite: 116].
  [x] Tuning effort setara (Frekuensi penarikan/pembaruan data dari sistem dibuat sebanding)[cite: 66].
  [x] Environment identik (Diuji pada infrastruktur jaringan organisasi atau simulasi sistem yang sama)[cite: 67, 69].
  [x] Metrik evaluasi sama (Sama-sama mengukur waktu respons ancaman, biaya operasional, dan efisiensi pemeliharaan)[cite: 11, 153].

Threat Analysis:
| Threat Type | Ancaman Spesifik | Mitigasi |
|-------------|-----------------|----------|
| Internal | Kesulitan integrasi perangkat IoT dengan sistem manajemen lama yang sudah ada di organisasi[cite: 46]. | Melakukan standardisasi protokol komunikasi dan uji coba kompatibilitas alat sebelum eksperimen penuh[cite: 48]. |
| External | Hasil penelitian terlalu spesifik pada satu sektor (misal: hanya cocok untuk logistik atau smart grid)[cite: 39, 121]. | Menggunakan variasi data studi literatur dari berbagai kasus sektor organisasi yang berbeda[cite: 71, 72]. |
| Construct | Indikator "efisiensi" salah diartikan (misal: hanya mengukur kecepatan tanpa melihat kualitas data)[cite: 9, 187]. | Mengombinasikan metrik waktu respons, keakuratan data, dan transparansi informasi secara bersamaan[cite: 9, 186]. |
| Conclusion | Adanya serangan siber (malware/ransomware) acak saat simulasi yang merusak validitas data hasil akhir[cite: 97, 188]. | Menerapkan sistem keamanan kuat (firewall, enkripsi, pembatasan akses) sepanjang jalannya eksperimen[cite: 108, 153]. |

Statistical Plan:
  Uji statistik   : Analisis Tren Korelasi & Deskriptif Komparatif[cite: 71, 125].
  Justifikasi      : Penelitian ini menggunakan studi literatur dan simulasi grafik untuk membandingkan variabel dari waktu ke waktu (seperti penurunan waktu respons dan frekuensi ancaman setelah pemantauan real-time berjalan)[cite: 71, 153, 154].
  Alpha            : 0.05 (Standar tingkat kekeliruan eksperimen 5%)
  Effect size min  : Signifikan (Mampu menunjukkan penurunan biaya operasional dan efisiensi waktu respons secara nyata)[cite: 11, 154].
```

---

## Latihan 1 — Desain Eksperimen

Susun desain eksperimen berdasarkan RQ, variabel, dan sistem dari WS-04 sampai WS-06.

**RQ:** Bagaimana pengaruh penerapan teknologi Internet of Things (IoT) terhadap efisiensi manajemen aset digital secara real-time?
**Tipe eksperimen:** [x] Comparison

| Kondisi | Deskripsi | IV Value | CV Settings |
|---------|-----------|----------|-------------|
| Control | Manajemen aset digital konvensional/tradisional | Tanpa IoT (Proses manual dan terpusat). | Jenis data/aset digital yang dikelola , metrik waktu pengamatan. |
| Treatment | Manajemen aset digital berbasis IoT. | Menggunakan IoT (Sensor, RFID, GPS, pemantauan otomatis). | Jenis data/aset digital yang dikelola , metrik waktu pengamatan. |

---

## Latihan 2 — Fairness Checklist

Evaluasi apakah desain eksperimen di Latihan 1 sudah fair.

| Kriteria | Status | Detail |
|----------|--------|--------|
| Dataset identik | ✅  | Menggunakan parameter cakupan data aset digital yang sama (perangkat lunak, file, perangkat keras). |
| Preprocessing setara | ✅ | Standar pencatatan awal kondisi aset diposisikan sama sebelum dipantau. |
| Tuning effort setara | ✅ | Komputasi pengawasan diatur pada frekuensi penarikan data yang sebanding. |
| Environment identik | ✅ | Diuji pada infrastruktur jaringan organisasi atau simulasi sistem yang sama. |
| Metrik evaluasi sama | ✅ | Keduanya mengukur kecepatan respons, akurasi keputusan, dan biaya operasional. |

**Ada yang tidak fair?** [ ] Ya / [x] Tidak

---

## Latihan 3 — Threat Analysis

Identifikasi ancaman validitas untuk desain eksperimen ini.

| Threat Type | Ancaman Spesifik | Mitigasi |
|-------------|-----------------|----------|
| Internal | Kesulitan integrasi IoT dengan sistem lama (legacy) yang dapat merusak data awal. | Melakukan standardisasi protokol komunikasi antar perangkat sebelum pengujian. |
| External | Kesimpulan riset terlalu bergantung pada data industri tertentu (misal: logistik/smart grid) sehingga sulit diterapkan di sektor lain. | Menggunakan variasi studi literatur dari berbagai sektor industri yang berbeda. |
| Construct | Indikator "efisiensi" hanya diukur dari kecepatan, mengabaikan beban kerja komputasi. | Mengombinasikan metrik waktu respons, biaya operasional, dan transparansi data. |
| Conclusion | Serangan siber (malware/ransomware) di tengah eksperimen yang memanipulasi data simulasi. | Menerapkan sistem keamanan kuat (firewall, enkripsi, pemantauan real-time) selama pengujian. |

**Ancaman mana yang paling sulit dimitigasi?** Keamanan Data (Internal & Conclusion Validity).
**Mengapa?**
> Karena semakin tinggi konektivitas perangkat IoT yang terhubung secara real-time, celah keamanan (interoperabilitas) dan risiko serangan siber seperti malware atau ransomware ikut meningkat secara acak, sehingga sulit diprediksi secara konstan tanpa enkripsi yang berlapis.

---

## Refleksi

> Sebuah paper melaporkan "metode kami mengalahkan semua baseline." Apa 3 pertanyaan pertama yang harus diajukan untuk mengevaluasi klaim ini?

**Jawaban:**
1. Apakah pengujian dilakukan pada kondisi lingkungan dan dataset yang benar-benar identik (Fair)? (Jangan sampai metode baru diuji di spek dewa, sedangkan baseline diuji di spek lawas).
2. Bagaimana paper tersebut menguji aspek keamanan data saat pengawasan real-time berjalan? (Apakah efisiensi mengorbankan keamanan data?).
3. Apakah metrik keberhasilan yang digunakan sudah divalidasi dengan benar? (Apakah penurunan waktu respons diiringi dengan akurasi data yang tetap tinggi?).
