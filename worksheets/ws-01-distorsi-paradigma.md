# WS-01: Distorsi & Paradigma

> **Bab 1 — Research Mindset in IT**

---

## Ringkasan Materi

### Research Trust Model

Pengetahuan ilmiah tidak muncul langsung dari kenyataan. Ia melewati **6 tahap transformasi** yang masing-masing rawan distorsi:

```
Reality → Data → Processing → Analysis → Inference → Knowledge
```

Etika mencegah distorsi yang disengaja (fabrikasi, cherry-picking). Validitas mendeteksi distorsi yang tidak disengaja (confounding variable, sampling bias).

### Tiga Jenis Validitas

| Jenis | Pertanyaan | Contoh Ancaman |
|-------|-----------|----------------|
| **Internal Validity** | Apakah hubungan kausal benar ada? | Confounding variable |
| **External Validity** | Apakah bisa digeneralisasi? | Dataset terlalu homogen |
| **Construct Validity** | Apakah mengukur hal yang benar? | Metrik tidak sesuai klaim |

### Paradigma Riset

Mata kuliah ini menggunakan pendekatan **Positivist** (fenomena TI bisa diukur objektif melalui eksperimen terkontrol) diperkuat **Design Science Research** (artefak dibuat sebagai instrumen pengujian hipotesis, bukan tujuan akhir).

### Mode Berpikir Peneliti

**Curious** (mempertanyakan fenomena) → **Critical** (mengevaluasi klaim berdasarkan bukti) → **Systematic** (merancang investigasi terstruktur dan reproducible).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Membuat sistem yang bekerja | Menghasilkan pengetahuan yang valid |
| Pertanyaan khas | "Bagaimana membuatnya jalan?" | "Apakah klaim ini benar?" |
| Ukuran sukses | Sistem berfungsi, client puas | Hipotesis terjawab, temuan tervalidasi |
| Kegagalan | Harus dihindari | Harus dilaporkan (negative result = kontribusi) |

### Istilah Penting

- **Research Mindset** — Pola pikir yang menuntut bukti dan mempertanyakan asumsi
- **Research Ethics** — Prinsip perilaku: kejujuran, objektivitas, keterbukaan, akuntabilitas
- **HARKing** — Hypothesizing After Results are Known — merumuskan hipotesis setelah melihat data
- **Falsifiability** — Hipotesis harus bisa dibuktikan salah

---

## Template A.1 — Research Mindset Self-Assessment

```
Nama Peneliti    : Khansa Amanda Icha Sentana
Tanggal          : 15 April 2026

1. Ketika membaca klaim "metode X 95% akurat":
   - Pertanyaan pertama saya: Bagaimana komposisi dataset yang digunakan untuk pengujian dan apakah terdapat variabel pengganggu (confounding variables) yang tidak terkontrol?
   - Data yang dibutuhkan untuk verifikasi: Distribusi data (apakah seimbang antara aset yang rusak dan normal), confusion matrix, serta dokumentasi lingkungan eksperimen untuk memastikan Internal Validity.

2. Posisi paradigma:
   - Pendekatan: [ ] Positivis  [ ] Interpretivis  [X] Design Science  [ ] Mixed
   - Alasan: Riset ini bertujuan untuk memecahkan masalah praktis organisasi dalam mengelola aset digital yang kompleks dengan memanfaatkan artefak teknologi (IoT) sebagai solusi fungsional.

3. Identifikasi distorsi:
   - Asumsi tersembunyi: Diasumsikan bahwa setiap organisasi memiliki infrastruktur internet yang stabil dan mampu membiayai sistem keamanan tingkat tinggi untuk mendukung operasional IoT.
   - Sumber bias potensial: Selection Bias dalam pemilihan literatur yang hanya menonjolkan keberhasilan implementasi IoT dan mengabaikan laporan kegagalan sistem.
   - Langkah mitigasi: Melakukan pencarian literatur yang lebih luas mencakup studi kasus tantangan implementasi dan melakukan analisis kritis terhadap simulasi keamanan data.

4. Komitmen etika:
   - Data yang tidak akan dimanipulasi: Data anomali atau ancaman siber yang terdeteksi (seperti malware atau ransomware) meskipun data tersebut menunjukkan kelemahan pada sistem yang sedang diusulkan.
   - Batasan yang diakui sejak awal: Kerentanan pada interoperabilitas perangkat dan ketergantungan sistem pada standar keamanan yang belum konsisten secara global.
```

---

## Latihan 1 — Identifikasi Distorsi

Pilih satu paper riset di bidang TI yang mengklaim "metode X meningkatkan performa." Telusuri setiap tahap Research Trust Model.

**Paper yang dipilih:**
> Judul: Pengaruh Teknologi Internet of Things Terhadap Manajemen Aset Digital Secara Real-Time
> Penulis (Tahun): Al Khaidar & Muhammad Fikry (2025) 

| Tahap | Apa yang Dilakukan | Potensi Distorsi |
|-------|-------------------|-----------------|
| Reality → Data | Mengumpulkan sumber ilmiah (jurnal, buku, laporan) terkait IoT dan aset digital melalui studi literatur. | Selection Bias: Peneliti mungkin hanya memilih literatur yang mendukung dampak positif IoT, mengabaikan laporan kegagalan implementasi. |
| Data → Processing | Melakukan sintesis dan integrasi informasi dari berbagai sumber untuk membangun pemahaman komprehensif. | Incomplete Synthesis: Ada risiko informasi teknis yang usang atau tidak relevan dengan konteks infrastruktur lokal di Indonesia ikut diproses. |
| Processing → Analysis | Menganalisis ancaman keamanan (malware, ransomware) dan tren pertumbuhan perangkat IoT. | Over-generalization: Data pertumbuhan global dari Statista (75,44 miliar perangkat) mungkin tidak mencerminkan adopsi aset digital di UMKM lokal. |
| Analysis → Inference | Menyimpulkan bahwa pemantauan real-time meningkatkan efisiensi dan keamanan data berdasarkan simulasi. | Confounding Variables: Peningkatan keamanan mungkin disebabkan oleh faktor lain (seperti kebijakan regulasi baru) bukan hanya fitur real-time IoT. |
| Inference → Knowledge | Menghasilkan rekomendasi strategis bagi organisasi untuk berinvestasi pada teknologi IoT. | Confirmation Bias: Pengetahuan yang dihasilkan cenderung mempromosikan IoT tanpa memberikan batasan biaya investasi yang realistis. |

**Distorsi paling besar di tahap:** Reality → Data (Studi Literatur). Karena penelitian ini sangat bergantung pada sumber sekunder, jika pemilihan literatur tidak objektif, seluruh rantai pengetahuan berikutnya akan bias.

**Dua distorsi spesifik yang teridentifikasi:**
1. Sampling Bias pada Literatur: Fokus pada artikel yang membahas efisiensi (sisi positif) dapat menutupi realitas tingginya biaya pemeliharaan sistem IoT di lapangan.
2. Distorsi pada Visualisasi Data: Gambar 3 (Simulasi Peningkatan Keamanan) bersifat konseptual/simulasi, namun dapat disalahpahami sebagai data empiris realitas operasional yang pasti terjadi.

---

## Latihan 2 — Analisis Kasus Etika

Skenario: Peneliti mengklaim IoT menurunkan biaya operasional, namun dalam literatur yang ditemukan, ada data yang menunjukkan biaya keamanan siber justru membengkak secara signifikan melampaui penghematan tersebut.

| Perspektif | Analisis |
|------------|---------|
| Kejujuran ilmiah | Peneliti harus melaporkan bahwa meskipun operasional rutin lebih murah, biaya risiko keamanan (malware/ransomware) adalah pengeluaran kritis yang harus diperhitungkan. |
| Transparansi | Mengakui tantangan integrasi dan privasi data sebagai hambatan nyata bagi organisasi, bukan hanya menonjolkan fitur otomatisasi. |
| Peer review | Membiarkan peninjau mengevaluasi apakah klaim "efisiensi signifikan" tetap valid jika variabel biaya keamanan dimasukkan dalam model analisis. |

**Keputusan akhir dan justifikasi:**
> Melaporkan kedua sisi (manfaat efisiensi vs beban biaya keamanan). Sesuai prinsip Falsifiability, riset yang jujur harus mencantumkan batasan dan risiko (negative results) agar pengetahuan yang dihasilkan valid dan dapat dipertanggungjawabkan.

---

## Latihan 3 — Posisi Paradigma

**Topik riset:** Pengaruh IoT terhadap Manajemen Aset Digital.

| Kriteria | Positivis | Interpretivis | Design Science |
|----------|-----------|---------------|----------------|
| Kesesuaian dengan topik (1–5) | 4 | 2 | 5 |
| Jenis data yang dikumpulkan | Data kuantitatif jumlah perangkat (miliar unit) dan metrik waktu respons. | Persepsi manajer IT mengenai kemudahan penggunaan IoT. | Pembuatan prototipe sistem pemantauan aset real-time sebagai instrumen uji. |
| Limitasi paradigma | Mengabaikan faktor budaya organisasi dalam mengadopsi teknologi baru. | Hasil sulit digeneralisasi karena sangat subjektif. | Fokus terlalu teknis sehingga melupakan dampak ekonomi jangka panjang. |

**Paradigma yang dipilih:** Design Science Research dikombinasikan dengan Positivisme.
**Alasan:** Peneliti bertujuan mengidentifikasi solusi praktis (Design Science) untuk mengatasi tantangan integrasi dan keamanan, sembari menggunakan data objektif (Positivisme) untuk mengukur efektivitas sistem tersebut secara real-time.

---

## Refleksi

> Sebelum membaca materi ini, apakah pernah mempertanyakan klaim "95% akurat"? Setelah memahami rantai distorsi, pertanyaan apa yang sekarang akan diajukan saat membaca paper?

**Jawaban:**
> Sebelumnya, saya cenderung menerima klaim efisiensi IoT secara mentah-mentah. Setelah memahami Research Trust Model, saya kini akan bertanya: "Bagaimana data simulasi di Gambar 3 divalidasi?" atau "Apakah literatur yang digunakan juga mencakup kasus kegagalan implementasi?" Saya menyadari bahwa pengetahuan dalam paper adalah hasil olahan yang rentan terhadap distorsi di setiap tahapnya.
