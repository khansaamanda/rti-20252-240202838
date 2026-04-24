# WS-02: Problem Statement

> **Bab 2 — Problem Formulation & System Context**

---

## Ringkasan Materi

### Problem Formation Model

Masalah riset melewati 5 tahap transformasi. Melompat langsung dari Reality ke Variable adalah kesalahan paling umum.

```
Reality → Observed Issue (Symptom) → Diagnosed Problem (Root Cause)
→ Researchable Problem (Scoped) → Measurable Variable (Operationalized)
```

### Topic ≠ Problem ≠ Research Problem

| Level | Contoh | Status |
|-------|--------|--------|
| **Topik** | Keamanan IoT | Terlalu luas, tidak bisa diuji |
| **Problem** | MQTT tidak terenkripsi | Spesifik tapi belum riset |
| **Research Problem** | Belum ada studi membandingkan overhead TLS 1.3 vs DTLS pada MQTT di IoT RAM < 64KB | Bisa dirancang eksperimennya |

### Symptom vs Root Cause

Apa yang diamati (gejala) ≠ mengapa terjadi (akar masalah). Gunakan **5 Whys** atau **Fishbone Diagram** untuk menggali.

Contoh: "User meninggalkan checkout" (symptom) → "Waktu loading > 8 detik karena API call sequential" (root cause).

### System Thinking

Setiap masalah riset TI harus terikat pada komponen sistem: **Input → Process → Output → Outcome → Constraints → Stakeholders**.

### Problem Quality Check

Masalah riset yang layak harus memenuhi 5 kriteria:
- **Clarity** — Satu orang membaca akan paham
- **Measurability** — Ada metrik kuantitatif
- **Relevance** — Penting untuk domain
- **Testability** — Bisa gagal (falsifiable)
- **Impact** — Ada kontribusi jika terjawab

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Menyelesaikan masalah (*solve*) | Memahami dan membuktikan (*understand & prove*) |
| Masalah | Bug, error, fitur belum ada | Gap dalam pengetahuan |
| Scope | Selesaikan semua yang perlu | Batasi agar bisa dibuktikan |
| Output | Working system | Evidence, paper, replicable findings |

### Istilah Penting

- **Problem Statement** — Formulasi tertulis: konteks sistem + gap + dampak + justifikasi
- **System Context** — Deskripsi lengkap: input, proses, output, outcome, constraints, stakeholders
- **Problem Drift** — Masalah "bermutasi" dari pendahuluan ke metodologi karena statement awal tidak presisi
- **Solution-First Thinking** — Memulai dari solusi tanpa masalah yang jelas — berbahaya dalam riset
- **Operational Definition** — Definisi variabel yang cukup jelas agar peneliti lain bisa mengukur hal yang sama

---

## Template A.2 — Problem Statement Builder

```
PROBLEM STATEMENT BUILDER

Domain & Konteks
  Domain   : ____________________
  Konteks  : ____________________

System Context
  Input       : ____________________
  Process     : ____________________
  Output      : ____________________
  Outcome     : ____________________
  Constraints : ____________________
  Stakeholders: ____________________

Fenomena → Problem
  Fenomena yang diamati             : ____________________
  Gejala (symptom) yang terukur     : ____________________
  Masalah yang didiagnosis          : ____________________
  Masalah riset (researchable)      : ____________________
  Variabel yang terukur             : ____________________

Problem Quality Check
  [ ] Clarity — Apakah satu orang membaca akan paham?
  [ ] Measurability — Apakah ada metrik kuantitatif?
  [ ] Relevance — Apakah penting untuk domain?
  [ ] Testability — Apakah bisa gagal?
  [ ] Impact — Apakah ada kontribusi jika terjawab?

Problem Statement (1 paragraf):
  ____________________
```

---

## Latihan 1 — Dari Topik ke Masalah Riset

Pilih satu topik di bidang TI yang diminati. Transformasikan melalui 5 tahap Problem Formation Model.

**Topik awal:** Pengaruh IoT terhadap Manajemen Aset Digital

| Tahap | Hasil |
|-------|-------|
| Reality | Organisasi di era digital memiliki banyak aset (data, akun, perangkat) yang semakin kompleks untuk dikelola |
| Observed Issue (Symptom) | Banyak organisasi sulit memanfaatkan aset secara optimal sehingga kinerja dan efisiensi operasional menurun. |
| Diagnosed Problem (Root Cause) | Pengelolaan aset masih dilakukan secara manual dan terpusat, sehingga informasi tidak diperbarui secara instan |
| Researchable Problem | Adanya hambatan dalam penerapan IoT untuk manajemen aset, terutama masalah integrasi sistem serta ancaman keamanan seperti malware dan ransomware |
| Measurable Variable | Kecepatan respons terhadap ancaman, frekuensi gangguan keamanan, dan tingkat efisiensi operasional |

**Apakah terjebak solution-first thinking?** [ ] Ya / [x] Tidak
> Jika ya, kembali ke tahap mana? Masalah yang diangkat berfokus pada hambatan keamanan dan efisiensi dalam sistem yang sudah ada, bukan sekadar ingin membuat alat baru.

---

## Latihan 2 — System Context Decomposition

Gambarkan konteks sistem dari masalah riset di Latihan 1.

| Komponen | Deskripsi |
|----------|----------|
| Input | Data dari perangkat fisik, sensor (suhu, tekanan), RFID, dan pelacakan GPS |
| Process | Pengumpulan, pengiriman, dan analisis data secara otomatis melalui jaringan internet |
| Output | Informasi kondisi aset secara real-time, laporan status, dan notifikasi peringatan dini |
| Outcome | Pengambilan keputusan yang lebih cepat, akurat, dan penurunan biaya operasional |
| Constraints | Masalah keamanan data, privasi, serta kesulitan integrasi dengan sistem lama |
| Stakeholders | Organisasi/perusahaan, admin sistem TI, dan pengguna perangkat IoT |

**Komponen mana yang paling relevan dengan masalah riset?**  Constraints (Keamanan Data) dan Process (Pemantauan Real-time).

---

## Latihan 3 — Problem Quality Check

Evaluasi problem statement yang sudah dibuat menggunakan 5 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Clarity | 5 | Masalah sangat jelas: IoT meningkatkan efisiensi tapi terhambat oleh celah keamanan |
| Measurability | 4 | Efisiensi diukur melalui waktu respons dan biaya operasional |
| Relevance | 5 | Sangat relevan karena jumlah perangkat IoT meningkat pesat (diprediksi 75,44 miliar pada 2025) |
| Testability | 4 | Dapat diuji melalui simulasi dampak pemantauan real-time terhadap penurunan ancaman |
| Impact | 5 | Berdampak besar pada perlindungan aset berharga dan keberlanjutan bisnis |

**Skor total:** 23 / 25

**Problem statement versi final (1 paragraf):**
> Meskipun teknologi IoT menawarkan efisiensi tinggi dalam manajemen aset digital melalui pemantauan secara real-time, namun penerapannya masih menghadapi tantangan serius berupa kerentanan terhadap serangan siber seperti malware dan ransomware. Hal ini menyebabkan risiko kebocoran data sensitif dan kerugian finansial akibat kerusakan perangkat atau penghentian operasional. Oleh karena itu, diperlukan strategi keamanan yang kuat dan sistem pemantauan yang mampu mendeteksi anomali secara instan untuk memastikan integrasi IoT yang aman dan optimal dalam organisasi.

---

## Refleksi

> Bandingkan "masalah" yang biasa ditemui saat coding (bug, error) dengan masalah riset. Apa perbedaan fundamental dalam cara mendefinisikan dan mendekati keduanya?

**Jawaban:**
> Masalah Coding (Bug): Biasanya bersifat teknis dan solusinya spesifik untuk memperbaiki fungsi agar berjalan kembali. Fokusnya adalah "Bagaimana agar ini tidak error?".
> Masalah Riset: Bersifat lebih luas dan mencari pemahaman tentang fenomena tertentu. Fokus riset dalam jurnal ini bukan sekadar memperbaiki satu sensor yang rusak, melainkan memahami bagaimana sistem keamanan secara keseluruhan dapat menangani ancaman siber yang kompleks di masa depan demi efisiensi organisasi.
