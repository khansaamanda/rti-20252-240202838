# WS-05: Variabel & Metrik

> **Bab 5 — Metric, Measurement & Data**

---

## Ringkasan Materi

### Measurement Alignment Model

Setiap pengukuran yang valid harus bisa ditelusuri melalui rantai ini tanpa lompatan logis:

```
Problem → Concept → Variable → Metric → Data → Result
```

### Operationalization = Keputusan Desain

Menerjemahkan konsep abstrak menjadi variabel terukur bukan proses mekanis. "Code quality" yang diukur via SonarQube code smells membawa asumsi implisit. Setiap operasionalisasi harus didokumentasikan dan dijustifikasi.

### Empat Tipe Data (NOIR)

| Tipe | Ciri | Contoh | Operasi Valid |
|------|------|--------|---------------|
| **Nominal** | Kategori, tanpa urutan | Jenis algoritma (RF, SVM, CNN) | Modus, chi-square |
| **Ordinal** | Urutan, interval tidak sama | Skala Likert (1-5) | Median, Spearman |
| **Interval** | Jarak bermakna, tanpa nol absolut | Suhu Celsius | Mean, Pearson, t-test |
| **Ratio** | Jarak bermakna + nol absolut | Waktu eksekusi (ms) | Semua operasi |

Tipe data menentukan uji statistik yang valid. Kebanyakan metrik performa TI = ratio; persepsi pengguna = ordinal.

### Kriteria Pemilihan Metrik

- **Representative** — Mewakili konsep yang diteliti
- **Sensitive** — Cukup peka menangkap perbedaan bermakna (hindari ceiling effect)
- **Feasible** — Bisa dikumpulkan dalam batasan waktu dan biaya

### Pre-registration

Metrik harus ditentukan **sebelum** eksperimen. Memilih metrik setelah melihat data = **p-hacking**. Metrik tambahan yang ditemukan kemudian dilaporkan sebagai *exploratory*, bukan *confirmatory*.

### Primary vs Secondary Metric

- **Primary Metric** — Langsung terikat ke hipotesis, menentukan kesimpulan
- **Secondary Metric** — Pendukung, dilaporkan di samping primary; statusnya suplementer

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Pemilihan metrik | Berdasarkan kebiasaan/tool yang ada | Berdasarkan construct validity |
| Anomali | Dihapus untuk laporan bersih | Diinvestigasi — bisa jadi temuan |
| Kapan dipilih | Setelah sistem jadi (monitoring) | Sebelum eksperimen (by design) |

### Istilah Penting

- **Operationalization** — Transformasi konsep abstrak menjadi variabel terukur
- **Construct Validity** — Sejauh mana pengukuran benar-benar mengukur konsep yang dimaksud
- **Measurement Scale** — Klasifikasi data (NOIR) yang menentukan analisis valid
- **Multi-metric Evaluation** — Menggunakan beberapa metrik untuk menangkap konsep kompleks

---

## Template A.5 — Definisi Variabel, Metrik & Justifikasi

```
VARIABLE & METRIC DEFINITION

Research Question: Bagaimana pengaruh penerapan teknologi Internet of Things (IoT) terhadap efisiensi dan keamanan manajemen aset digital secara real-time?

| Variabel | Tipe | Konsep | Metrik | Skala | Satuan | Cara Mengukur | Justifikasi |
|----------|------|--------|--------|-------|--------|---------------|-------------|
|Penerapan Teknologi IoT|IV|Jaringan perangkat fisik yang saling terhubung melalui internet tanpa intervensi manusia.|Status implementasi sistem IoT dan jumlah perangkat aktif.|Nominal / Rasio|Perangkat / Tahun|Menghitung jumlah instalasi perangkat IoT terhubung secara global (Statista/Transforma Insights).|Diperlukan untuk melihat tren pertumbuhan ekosistem IoT dari tahun ke tahun.|
|Efisiensi Manajemen Aset Digital|DV|Pengelolaan sumber daya digital secara otomatis, cepat, dan akurat.|Kecepatan waktu respons, biaya operasional, dan downtime.|Rasio|Jam / Persen / Rupiah|Mengukur penurunan waktu respons penanganan masalah dan tingkat penghematan biaya.|Menjadi indikator utama apakah IoT berhasil meningkatkan performa operasional aset.|
|Keamanan Data|CV|Perlindungan informasi aset digital dari ancaman siber.|Frekuensi serangan/ancaman (malware, ransomware) yang berhasil.|Rasio|Frekuensi Kejadian|Menghitung jumlah insiden atau anomali siber yang terdeteksi oleh sistem pemantauan real-time.|Diperlukan untuk mengevaluasi ketahanan sistem karena IoT juga membawa risiko celah keamanan baru.|

Alignment Check:
  RQ → Concept → Variable → Metric → Data → Result
  [x] Setiap langkah terdokumentasi : Hubungan antara pertumbuhan IoT, efisiensi waktu respons, dan penurunan ancaman siber dibahas menggunakan simulasi dan data Statista.
  [x] Tidak ada "lompatan logis" : IoT menghasilkan data langsung (real-time) $\rightarrow$ Data mempermudah pemantauan $\rightarrow$ Pemantauan mempercepat deteksi masalah $\rightarrow$ Efisiensi meningkat. 
  [x] Metrik mengukur apa yang dimaksud (construct validity) : Menggunakan metrik waktu respons untuk mengukur aspek real-time dan frekuensi ancaman untuk mengukur aspek keamanan.
```

---

## Latihan 1 — Operationalization Chain

Gunakan RQ dari WS-04. Definisikan variabel dan metriknya.

**RQ:** Bagaimana dampak pemantauan real-time berbasis IoT terhadap keamanan data aset digital?

| Variabel | Tipe | Konsep Abstrak | Metrik Konkret | Skala (NOIR) | Satuan |
|----------|------|---------------|----------------|-------------|--------|
| Keamanan Data | DV | Tingkat ketahanan sistem terhadap serangan siber yang merusak integritas informasi. | Jumlah atau frekuensi insiden serangan (malware/ransomware) yang berhasil menembus sistem. | Rasio | Kasus / Kejadian |
| Efisiensi Real-Time | DV | Kecepatan sistem dalam mendeteksi dan merespons ancaman atau masalah pada aset digital. | Waktu tunggu (durasi) dari kemunculan anomali hingga tindakan pencegahan diambil. | Rasio | Detik / Menit |
| Jenis Ancaman Siber | CV | Ragam variasi serangan siber yang berpotensi menyerang infrastruktur IoT selama pengujian. | Kategori serangan yang digunakan dalam simulasi (misalnya: Malware vs Ransomware). | Nominal | - |

**Apakah ada lompatan logis dalam rantai?** [ ] Ya / [X] Tidak
> Jika ya, di mana? (Tidak ada lompatan logis karena seluruh rantai operasionalisasi sudah mengalir secara runtut).

---

## Latihan 2 — Evaluasi Metrik

Evaluasi metrik DV yang dipilih di Latihan 1 menggunakan 3 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Representative | 5 | Waktu respons sangat mewakili (representatif) konsep real-time. Semakin cepat sistem memberikan peringatan instan saat ada anomali, artinya manajemen aset digital berjalan semakin efisien. |
| Sensitive | 4 | Metrik ini sangat sensitif terhadap perubahan kondisi jaringan atau kecanggihan perangkat IoT. Sedikit saja ada gangguan koneksi atau serangan malware, waktu respons sistem akan langsung berubah melambat. |
| Feasible | 5 | Metrik ini sangat mudah diukur (layak) karena perangkat lunak atau platform IoT zaman sekarang otomatis mencatat waktu (timestamp) setiap kali ada aktivitas atau ancaman yang masuk. |

**Apakah perlu secondary metric?** [x] Ya / [ ] Tidak
> Jika ya, apa dan mengapa? Kita perlu metrik sekunder bernama "Akurasi Deteksi" (atau Efektivitas Respons). Mengapa? Karena percuma jika sistem merespons sangat cepat (misal dalam 0,1 detik) , tetapi ternyata itu adalah false alarm (salah tebak/bukan ancaman asli) atau sistem gagal memblokir serangan tersebut secara tuntas.

**Contoh kasus ceiling effect untuk metrik ini:**
> Ceiling effect (efek langit-langit/mentok) terjadi ketika metrik sudah mencapai batas maksimalnya sehingga tidak bisa diukur lebih baik lagi. 
Contohnya: Ketika performa sistem keamanan IoT sudah sangat optimal hingga waktu responsnya menyentuh angka 0 detik (instan/seketika) berkat infrastruktur jaringan yang super cepat. Jika di masa depan sistem ini diperbarui lagi dengan teknologi yang lebih canggih, kita tidak bisa melihat peningkatannya pada metrik "Waktu Respons" karena angkanya sudah mentok di batas paling cepat (0 detik).

---

## Latihan 3 — Data Quality Check

Bayangkan data yang akan dikumpulkan dari eksperimen. Evaluasi 4 dimensi kualitas data.

| Dimensi | Pertanyaan | Jawaban | Strategi Mitigasi |
|---------|-----------|---------|------------------|
| Completeness | Apakah semua data point terkumpul? | Data tren jumlah perangkat terkumpul lengkap dari tahun 2015-2025, namun data metrik keamanan spesifik masih berupa simulasi. | Melakukan studi tambahan yang mencakup data empiris dari studi kasus nyata di organisasi. |
| Consistency | Apakah ada kontradiksi internal? | Tidak ada kontradiksi. Teks konsisten menyatakan IoT meningkatkan efisiensi, namun di sisi lain menambah risiko keamanan. | Memisahkan pembahasan hasil analisis menjadi dua sub-bab: manfaat operasional dan ancaman keamanan. |
| Validity | Apakah benar-benar mengukur yang dimaksud? | Ya, grafik simulasi secara valid mengukur penurunan risiko keamanan melalui indikator waktu respons yang mengecil. | Menyelaraskan indikator simulasi dengan teori manajemen keamanan fisik dan digital. |
| Representativeness | Apakah sampel mewakili populasi target? | Ya, karena data pertumbuhan menggunakan statistik global berskala besar dari Statista dan Transforma Insights. | Membatasi kesimpulan agar tetap relevan dalam ruang lingkup ekosistem IoT global. |

---

## Refleksi

> Mengapa memilih metrik setelah melihat data dianggap p-hacking? Apa bedanya dengan eksplorasi data yang sah?

**Jawaban:**
> 1. P-hacking (Tidak Sah): Dianggap curang/p-hacking karena peneliti dengan sengaja memilih atau mengubah metrik hanya agar hasilnya terlihat bagus, signifikan, atau sesuai dengan hipotesis awal setelah mereka melihat data lapangan. Ini seperti menembak dinding terlebih dahulu, baru kemudian menggambar pola target di sekitar lubang peluru.
> 2. Eksplorasi Data yang Sah: Eksplorasi data yang jujur dilakukan untuk memahami pola, melihat anomali, atau mencari tren baru tanpa memanipulasi metrik evaluasi yang telah ditetapkan sejak awal penelitian demi memaksakan kesimpulan tertentu. Metrik tetap konsisten, namun data dieksplorasi secara terbuka apa adanya.
