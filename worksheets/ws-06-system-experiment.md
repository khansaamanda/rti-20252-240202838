# WS-06: System-Experiment Mapping

> **Bab 6 — System Design sebagai Experimental Artifact**

---

## Ringkasan Materi

### Sistem = Instrumen Pengujian, Bukan Produk

Seorang engineer bertanya "apakah sistem bekerja?" — seorang peneliti bertanya "apa yang bisa dibuktikan sistem ini?" Sistem dalam riset adalah **artifact** — objek yang sengaja dibuat untuk menguji klaim spesifik.

### System as Experiment Model

```
RQ → Variable → System Component → Experimental Setup → Output
```

Setiap komponen sistem harus bisa ditelusuri ke variabel riset (top-down), dan setiap pengukuran harus menjawab RQ (bottom-up).

### Mapping Variabel ke Komponen

| Tipe Variabel | Peran di Sistem | Contoh |
|---------------|----------------|--------|
| **IV** (Independent) | Modul yang bisa di-toggle/swap | Algoritma A vs B |
| **DV** (Dependent) | Modul pengukuran | Logger, metrics collector |
| **CV** (Control) | Config yang dikunci | Dataset, parameter tetap |

Jika variabel tidak bisa di-map ke komponen apapun → arsitektur perlu didesain ulang.

### 4 Prinsip Desain Eksperimental

| Prinsip | Pertanyaan Kunci |
|---------|-----------------|
| **Traceability** | Komponen ini melayani variabel yang mana? |
| **Modularity** | Bisakah IV diubah tanpa memengaruhi yang lain? |
| **Controllability** | Apakah CV dieksternalisasi ke config file? |
| **Measurability** | Apakah sistem otomatis menghasilkan data yang dibutuhkan? |

### Variable Isolation melalui Arsitektur

- **Modular architecture** — Pisahkan berdasarkan variabel
- **Configuration-driven** — Ubah config (YAML/JSON), bukan code
- **Feature toggles** — On/off flag untuk ablation study

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan sistem | Memenuhi kebutuhan user | Menguji hipotesis, menghasilkan bukti |
| Arsitektur | Optimasi performa & skalabilitas | Optimasi isolasi variabel & reprodusibilitas |
| Konfigurasi | Sering hardcoded | Dieksternalisasi ke config file |
| Fitur tambahan | Menambah nilai user | Menambah noise jika tidak terkait RQ |

### Istilah Penting

- **Artifact** — Objek yang sengaja dibuat untuk memecahkan masalah atau menguji proposisi
- **Traceability** — Kemampuan menelusuri hubungan RQ → variabel → komponen → output
- **Variable Isolation** — Mengubah hanya satu variabel sambil menahan yang lain konstan
- **Ablation Study** — Menguji kontribusi tiap komponen dengan melepasnya satu per satu
- **Configuration-driven Execution** — Semua parameter di config file, bukan hardcoded

---

## Template A.6 — Mapping RQ ke Arsitektur Sistem

```
SYSTEM-EXPERIMENT MAPPING

Research Question: Bagaimana pengaruh penerapan teknologi Internet of Things (IoT) terhadap efisiensi manajemen aset digital secara real-time , serta bagaimana kemampuan sistem pemantauan ini dalam merespons ancaman siber?

Variable → Component Mapping:
| Variabel | Tipe | Komponen Sistem | Cara Manipulasi/Pengukuran |
|----------|------|-----------------|---------------------------|
| Penerapan Teknologi IoT | IV | Modul Sensor Jaringan dan Pelacak Otomatis (seperti RFID, Inframerah, atau GPS).| Diubah melalui file config untuk mengaktifkan sensor (real-time) atau menonaktifkannya (pengelolaan manual/tradisional). |
| Waktu Respons & Frekuensi Ancaman | DV   | Modul Pengukur Keamanan (Dashboard Metrics Logger). | Diukur secara otomatis oleh sistem untuk mencatat durasi deteksi masalah (detik) dan grafik jumlah ancaman siber yang berhasil dikurangi. |
| Keamanan Data & Jenis Aset | CV   | Repositori Data Sentral dan Standar Enkripsi/Firewall Pokok. | Dikunci (dibuat tetap sama) sepanjang pengujian, baik pada jenis berkas aset yang dipantau maupun parameter keamanan dasarnya. |

4 Prinsip Desain:
  [x] Traceability — Setiap komponen bisa ditelusuri ke variabel
  [x] Variable Isolation — IV bisa diubah tanpa mengubah CV
  [x] Measurement Integration — Pengukuran DV built-in
  [x] Reproducibility — Setup bisa direkonstruksi

Experimental Setup:
  Input data     : Data telemetri status aset fisik/digital dan injeksi sampel serangan siber (Malware/Ransomware)
  Parameter      : Jumlah perangkat terhubung (skala tren 2015-2025) dan interval pembaruan data real-time [cite: 338, 341]
  Output format  : Grafik simulasi peningkatan keamanan (tren waktu respons vs tingkat keandalan data) [cite: 363, 365]
```

---

## Latihan 1 — Variable-to-Component Mapping

Gunakan RQ dan variabel dari WS-05. Petakan ke komponen sistem.

**RQ:** Bagaimana pengaruh integrasi sensor IoT real-time dalam mendeteksi ancaman keamanan dan mengoptimalkan efisiensi manajemen aset digital?

| Variabel | Tipe | Komponen Sistem | Cara Manipulasi / Pengukuran |
|----------|------|-----------------|---------------------------|
| Mode Pemantauan IoT | IV | Modul Konektivitas Jaringan (Sensor Otomatis vs Pencatatan Manual) | Mengubah baris pengaturan pada file konfigurasi, misalnya dari mode: "realtime" menjadi mode: "manual" |
| Efisiensi Pengelolaan Data | DV | Modul Pengukur Performa (Dashboard Metrics Logger) | Dihitung otomatis oleh sistem berdasarkan kecepatan waktu respons penanganan data (detik) dan tingkat keandalan data yang masuk. |
| Kapasitas Dasar Aset Digital | CV | Pusat Penyimpanan Data (Database Sentral) | Dikunci atau dibuat tetap sama sepanjang pengujian agar tidak memengaruhi hasil pengukuran (misalnya jumlah file atau jenis akun media sosial yang dipantau tidak diubah-ubah). |

**Apakah semua variabel bisa di-map?** [x] Ya / [ ] Tidak
> Jika tidak, komponen apa yang perlu ditambahkan? Semua variabel di atas sudah bisa dipetakan langsung ke dalam komponen sistem karena arsitektur penelitian ini memisahkan antara bagian sensor penangkap data, bagian simulasi gangguan keamanan, dan bagian pelacak metrik keberhasilan.

---

## Latihan 2 — 4 Prinsip Desain

Evaluasi desain sistem terhadap 4 prinsip.

| Prinsip | Status | Bukti / Penjelasan |
|---------|--------|-------------------|
| Traceability | Lengkap | Setiap modul sensor (seperti GPS/RFID) langsung melayani pemenuhan data variabel pelacakan lokasi dan status aset secara transparan. |
| Modularity | Terpenuhi | Modul injeksi ancaman (malware/ransomware) dipisahkan sepenuhnya dari inti data manajemen aset, sehingga jenis serangan bisa ditukar tanpa merusak database utama. |
| Controllability | Terpenuhi | Parameter eksternal seperti jumlah basis data terpasang atau ambang batas suhu/tekanan berbahaya diatur via config file, bukan di-hardcode di dalam fungsi sensor. |
| Measurability | Terpenuhi | Sistem memiliki modul logger bawaan untuk menangkap waktu respons penanganan data, keandalan informasi, dan grafik penurunan frekuensi ancaman secara berkala. |

**Prinsip mana yang paling sulit dipenuhi?** Modularity & Controllability dalam isolasi data siber.
**Strategi untuk mengatasinya:**
> Membuat lapisan virtual environment atau sandbox simulation untuk menguji serangan siber (malware/ransomware) agar perilaku serangan dapat dikontrol lewat berkas konfigurasi tanpa mengekspos atau merusak sistem fasilitas operasional riil.

---

## Latihan 3 — Ablation Study Planning

Jika sistem memiliki 3 komponen utama, rencanakan ablation study.

| Kondisi | Komponen A | Komponen B | Komponen C | Hasil yang Diharapkan |
|---------|-----------|-----------|-----------|----------------------|
| Full | ✅ Aktif | ✅ Aktif | ✅ Aktif | Baseline Penuh: Pengelolaan aset optimal, keputusan cepat, waktu respons siber sangat rendah, data aman. |
| – A | ❌ Nonaktif (Manual) | ✅ Aktif | ✅ Aktif | Efisiensi turun drastis; alarm dan proteksi aktif tetapi data kondisi aset terlambat diperbarui (tidak real-time). |
| – B | ✅ Aktif | ❌ Nonaktif (Tanpa notifikasi) | ✅ Aktif | Data terpantau dan aman, namun manajemen tidak mendapat peringatan instan saat terjadi anomali siber/fisik. |
| – C | ✅ Akrif | ✅ Aktif | ❌ Nonaktif (Tanpa enkripsi) | Pemantauan sangat cepat, tetapi sistem rentan mengalami kebocoran informasi akibat infeksi malware atau penguncian data. |

**Komponen mana yang diprediksi paling berkontribusi?** Komponen C (Security Control Module).
**Mengapa?**
> Karena berdasarkan temuan riset, tantangan terbesar dari ekosistem IoT adalah masalah keamanan data dan integritas informasi. Tanpa komponen keamanan yang kuat, sistem pemantauan real-time yang efisien sekalipun akan lumpuh total jika terkena serangan malware atau ransomware yang memanipulasi fungsi perangkat dan mencuri data sensitif.

---

## Refleksi

> Apa risiko jika sistem dibangun seperti produk (monolitik, fitur lengkap) lalu baru dilakukan eksperimen? Mengapa arsitektur modular penting untuk riset?

**Jawaban:**
> Jika sistem dibangun langsung seperti produk komersial yang monolitik (semua fitur digabung jadi satu tanpa pemisahan variabel), peneliti akan menghadapi kesulitan besar dalam mengisolasi variabel. Ketika terjadi peningkatan efisiensi atau penurunan waktu respons, peneliti tidak akan bisa membuktikan secara ilmiah komponen spesifik mana yang sebenarnya membawa dampak positif tersebut—apakah karena kinerja sensornya, sistem alarmnya, atau protokol keamanannya. Fitur-fitur tambahan yang tidak relevan dengan pertanyaan penelitian justru akan menciptakan noise yang mengaburkan validitas data.
> Arsitektur modular sangat penting dalam riset karena memungkinkan adanya prinsip Variable Isolation dan pelaksanaan Ablation Study. Kita bisa mematikan atau menukar satu modul tertentu (misalnya mematikan enkripsi atau mengubah sensor dari otomatis ke manual) dengan mudah lewat file konfigurasi untuk melihat efeknya secara murni terhadap keamanan dan efisiensi sistem, tanpa harus merombak seluruh kode program dari awal. Hal ini menjamin bahwa data yang dihasilkan benar-benar akurat, objektif, serta dapat direproduksi ulang oleh peneliti lain (reproducible).
