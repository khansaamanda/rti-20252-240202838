# WS-03: Literature Mapping & Gap

> **Bab 3 — Literature Review, Research Gap & Baseline**

---

## Ringkasan Materi

### Literature Review = Positioning, Bukan Ringkasan

Literature review bukan merangkum paper satu per satu. Pendekatan yang benar adalah **concept-centric** — organisasi berdasarkan tema, metode, atau variabel. Tujuan: menemukan **pola, kontradiksi, dan gap**.

### Empat Jenis Research Gap

| Jenis Gap | Deskripsi | Contoh |
|-----------|----------|--------|
| **Performance Gap** | Performa belum memadai | Akurasi deteksi hanya 78% pada kasus tertentu |
| **Method Gap** | Pendekatan belum diterapkan | Belum ada yang pakai transformer untuk task ini |
| **Data Gap** | Dataset terbatas/tidak representatif | Semua studi pakai dataset sintetis |
| **Context Gap** | Belum diuji pada konteks berbeda | Belum ada evaluasi di negara berkembang |

Gap terkuat = kombinasi 2+ jenis.

### Systematic Search Strategy

1. **Database**: IEEE Xplore, ACM DL, Scopus, Google Scholar
2. **Boolean query** yang terdokumentasi eksplisit
3. **Snowballing**: backward (telusuri referensi) + forward (cari yang mengutip)
4. Klaim "belum ada penelitian" harus didukung **bukti pencarian**

### Baseline Selection — 3 Kriteria

| Kriteria | Pertanyaan |
|----------|-----------|
| **Relevan** | Apakah menyelesaikan masalah yang sama? |
| **Representatif** | Apakah mewakili common practice? |
| **State-of-the-Art** | Apakah terbaru/terbaik? |

Membandingkan deep learning 2024 dengan decision tree sederhana tanpa justifikasi = **straw man comparison** (perbandingan tidak jujur).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan baca literatur | Mencari solusi yang sudah ada | Memahami apa yang belum terjawab |
| Cara membaca paper | Tutorial, how-to | Metode, limitasi, gap |
| Baseline | Framework terpopuler | State-of-the-art yang rigorous |
| Dokumentasi pencarian | Tidak diperlukan | Wajib (reproducible) |

### Istilah Penting

- **Concept-centric** — Organisasi literatur berdasarkan konsep/metode, bukan per penulis
- **Snowballing** — Backward (telusuri referensi) + Forward (cari yang mengutip paper kunci)
- **Research Position** — Pernyataan eksplisit posisi riset terhadap studi sebelumnya
- **Straw man comparison** — Memilih baseline lemah agar metode sendiri terlihat lebih baik

---

## Template A.3 — Literature Mapping & Gap Identification

```
LITERATURE MAPPING

Topik      : Pengaruh Internet of Things (IoT) terhadap Manajemen Aset Digital secara Real-Time.
Database   : Tidak disebutkan spesifik (menggunakan metode studi literatur).
Query      : Internet of Things, Manajemen Aset Digital, Keamanan Data.
Tahun      : Sumber rujukan berkisar antara 2017 hingga 2023.
Hasil awal : 10 paper → Screening → 10 paper final

Literature Matrix (concept-centric):

| Study | Tahun | Method | Data | Result | Limitation |
|-------|-------|--------|------|--------|------------|
|  Al Khaidar & M. Fikry     |    2025   |   Studi Literatur     |   Artikel jurnal & laporan penelitian   |    IoT meningkatkan efisiensi dan akurasi manajemen aset secara instan    |      Tantangan pada keamanan data dan integrasi sistem      |

Pola yang ditemukan:
  Metode dominan     : Studi literatur dan analisis deskriptif.
  Dataset umum       : Data sekunder dari survei (seperti APJII) dan proyeksi pertumbuhan perangkat (Statista/Transforma Insights).
  Limitasi berulang  : Kerentanan terhadap serangan siber (malware/ransomware) dan masalah privasi.

GAP IDENTIFICATION

Gap 1: [Jenis: Method Gap]
  Deskripsi    : Kurangnya pemahaman organisasi dalam mengolah dan memanfaatkan data yang dihasilkan oleh perangkat IoT untuk pengambilan keputusan strategis.
  Bukti        : Masih banyak organisasi yang belum sepenuhnya memahami cara memanfaatkan data dari perangkat IoT untuk meningkatkan efisiensi pengelolaan aset mereka.
  Signifikansi : Tanpa metode pengolahan data yang tepat, investasi pada teknologi IoT hanya akan menghasilkan tumpukan data mentah tanpa memberikan nilai tambah pada kinerja operasional perusahaan.

Gap 2: [Jenis: Context Gap]
  Deskripsi    : Adanya hambatan teknis yang signifikan dalam proses integrasi teknologi IoT dengan infrastruktur atau sistem manajemen aset yang sudah ada sebelumnya.
  Bukti        : Penerapan IoT dalam pengelolaan aset digital menghadapi tantangan besar seperti kesulitan integrasi dengan sistem yang sudah ada.
  Signifikansi : Kegagalan integrasi dapat menyebabkan silo data (data terpisah-pisah) dan menghambat pemantauan aset secara real-time yang menyeluruh di seluruh bagian organisasi.

Baseline Selection:
| Baseline | Relevansi | Representatif | Source |
|----------|-----------|---------------|--------|
|     Manajemen Aset Tradisional     |     Fokus pada pengelolaan aset digital seperti data dan perangkat keras yang dilakukan secara manual.      |       Mewakili standar operasional umum di mana proses masih terpusat dan belum menggunakan sistem otomatis.        |    Al Khaidar & Muhammad Fikry (2025)    |
```

---

## Latihan 1 — Concept-Centric Literature Table

Gunakan topik riset dari WS-02. Cari minimal 5 paper relevan menggunakan Google Scholar atau database lain.

**Topik riset:** Pengaruh Internet of Things (IoT) terhadap Manajemen Aset Digital secara Real-Time.
**Query pencarian:** Internet of Things, Digital Asset Management, Real-Time Monitoring, Data Security.
**Database:** Google Scholar, APJII, Statista, dan IEEE.

| # | Study | Tahun | Method | Dataset | Result | Limitasi |
|---|-------|-------|--------|---------|--------|----------|
| 1 | Al Khaidar & M. Fikry | 2025 | Studi Literatur | Artikel & Jurnal Ilmiah | IoT meningkatkan efisiensi dan akurasi manajemen aset | Tantangan integrasi sistem dan keamanan data |
| 2 | Prawiyogi & Anwar | 2023 | Literature Review | Sektor Energi | IoT mengoptimalkan pengawasan aset sektor energi | Belum mendetail pada aspek privasi data pengguna |
| 3 | Suryawijaya | 2023 | Studi Kasus | Blockchain | Memperkuat keamanan data melalui desentralisasi | Implementasi blockchain cenderung kompleks dan mahal |
| 4 | Yel & Nasution | 2022 | Analisis Deskriptif | Media Sosial | Identifikasi risiko kebocoran data pribadi | Fokus hanya pada aset di media sosial |
| 5 | Transforma Insights | 2019 | Proyeksi Pasar | Data Global | Pertumbuhan perangkat IoT mencapai 7,6 miliar | Tidak membahas metode pengamanan secara teknis |

**Pola yang terlihat — Metode dominan:** Penggunaan sensor (RFID, GPS) dan jaringan internet untuk pengumpulan data otomatis.
**Limitasi yang berulang:** Kerentanan terhadap serangan siber (malware, ransomware) dan sulitnya integrasi dengan sistem lama (legacy).

---

## Latihan 2 — Gap Identification

Berdasarkan tabel di Latihan 1, identifikasi gap.

| Jenis Gap | Ditemukan? | Gap Statement |
|-----------|-----------|---------------|
| Performance Gap | [ ] Ya / [x] Tidak | IoT sudah memberikan performa real-time yang cepat untuk deteksi aset. |
| Method Gap | [x] Ya / [ ] Tidak | Banyak organisasi belum paham cara memanfaatkan data mentah IoT menjadi keputusan strategis. |
| Data Gap | [ ] Ya / [x] Tidak | Data sangat melimpah, namun integritas data sering kali dipertanyakan. |
| Context Gap | [x] Ya / [ ] Tidak | Tantangan besar dalam integrasi IoT ke dalam sistem manajemen yang sudah ada sebelumnya. |

**Gap utama yang dipilih:** Method & Context Gap (Masalah integrasi dan pemanfaatan data).
**Mengapa gap ini penting (bukan sekadar "belum ada yang meneliti")?**
> Karena tanpa integrasi yang mulus dan pemahaman metode pengolahan data, teknologi IoT hanya akan menjadi perangkat pemantau tanpa memberikan dampak nyata pada efisiensi biaya operasional perusahaan.

---

## Latihan 3 — Baseline Selection

Pilih 2 baseline dari literatur yang sudah dibaca.

| # | Baseline | Mengapa Relevan | Mengapa Representatif | Apakah SOTA? | Sumber |
|---|----------|----------------|----------------------|-------------|--------|
| 1 | Manajemen Aset Konvensional | Fokus pada pencatatan manual dan terpusat | Masih digunakan oleh banyak organisasi tradisional | Tidak | Al Khaidar & Fikry (2025) |
| 2 | Sistem Keamanan IoT Standar | Menggunakan sensor dasar tanpa enkripsi kuat | Mewakili praktik umum perangkat IoT di pasar saat ini | Bukan (SOTA pakai Blockchain) | Suryawijaya (2023) |

**Apakah pemilihan baseline ini bisa dianggap straw man?** [ ] Ya / [x] Tidak
> Justifikasi: Baseline yang dipilih adalah metode nyata yang sedang digunakan di lapangan, sehingga perbandingan dengan solusi baru menjadi valid dan jujur.

---

## Refleksi

> Apa perbedaan antara "belum ada yang meneliti ini" (klaim tanpa bukti) dengan research gap yang valid? Bagaimana cara membuktikan bahwa sebuah gap benar-benar ada?

**Jawaban:**
> Perbedaan utama terletak pada landasan bukti dan dokumentasi pencarian. Klaim "belum ada yang meneliti" sering kali hanya asumsi subjektif karena kurangnya literatur yang dibaca atau ketidaktahuan peneliti. Sebaliknya, research gap yang valid adalah pernyataan masalah yang muncul setelah melakukan tinjauan literatur secara sistematis, di mana peneliti dapat menunjukkan secara spesifik di mana letak kelemahan, kontradiksi, atau keterbatasan (seperti masalah keamanan data atau kesulitan integrasi sistem) dari penelitian-penelitian sebelumnya.
> Cara membuktikan bahwa sebuah gap benar-benar ada adalah dengan menyusun Literature Matrix (Concept-Centric) yang memetakan metode, hasil, dan limitasi dari berbagai studi terkini. Peneliti harus mampu menunjukkan bukti pencarian yang kuat (seperti dokumentasi query pada database ilmiah) dan mengidentifikasi pola kegagalan atau keterbatasan yang berulang, seperti ancaman malware atau tantangan integrasi pada perangkat IoT, sehingga celah yang akan diteliti memiliki signifikansi nyata bagi perkembangan ilmu pengetahuan.
