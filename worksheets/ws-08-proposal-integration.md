# WS-08: Proposal Integration (UTS)

> **Bab 8 — Proposal & Checkpoint**

---

## Ringkasan Materi

### Proposal = Satu Argumen Utuh

Proposal riset bukan kumpulan bab yang independen. Ia adalah **satu argumen** yang mengalir dari masalah ke rencana solusi. Jika satu koneksi putus, seluruh proposal kehilangan koherensi.

### Integration Map — 6 Koneksi Kritis

```
Problem (Bab 2) → Gap (Bab 3) → RQ & H (Bab 4) → Metrik (Bab 5) → Sistem (Bab 6) → Eksperimen (Bab 7)
```

| Koneksi | Pertanyaan Verifikasi |
|---------|----------------------|
| Problem → Gap | Apakah gap muncul dari analisis literatur terhadap masalah? |
| Gap → RQ | Apakah RQ langsung menjawab gap yang teridentifikasi? |
| RQ → Metrik | Apakah setiap variabel di RQ punya metrik terdefinisi? |
| Metrik → Sistem | Apakah setiap metrik bisa diukur oleh komponen sistem? |
| Sistem → Eksperimen | Apakah desain eksperimen menggunakan sistem sebagai instrumen? |

### Koherensi Vertikal + Horizontal

- **Vertikal** — Alur logis atas-ke-bawah (problem → experiment)
- **Horizontal** — Konsistensi terminologi (nama variabel di RQ = di hipotesis = di metrik = di desain)

### Jebakan Kognitif

| Jebakan | Deskripsi |
|---------|----------|
| "Selling" Introduction | Menulis promosi, bukan menyajikan data dan gap |
| Copy-paste Methodology | Menyalin deskripsi tekstbook tanpa menyesuaikan ke RQ |
| Optimistic Timeline | Meremehkan waktu implementasi; selalu tambah buffer 30-50% |
| No Possibility of Failure | Mengimplikasikan hasil pasti sukses — proposal jujur mengakui H₀ mungkin tidak ditolak |

### Struktur Proposal

1. **Pendahuluan** — Latar belakang + problem statement (Bab 1-2)
2. **Tinjauan Pustaka** — Literature review + gap + baseline (Bab 3)
3. **RQ / Kontribusi / Hipotesis** — (Bab 4)
4. **Metodologi** — Metrik + sistem + desain eksperimen (Bab 5-7)
5. **Timeline & Output**

### Istilah Penting

- **Integration Map** — Diagram 6 koneksi kritis antar komponen proposal
- **Vertical Coherence** — Alur logis atas-ke-bawah
- **Horizontal Coherence** — Konsistensi terminologi di semua bagian
- **Checkpoint** — Titik self-assessment sebelum transisi dari desain ke eksekusi

---

## Template A.8 — Integration Checklist

```
PROPOSAL INTEGRATION CHECKLIST

Koneksi Vertikal (Flow Atas-Bawah):
  [x] Problem → Gap: masalah terdokumentasi di literatur
  [x] Gap → RQ: pertanyaan menjawab gap spesifik
  [x] RQ → Hypothesis: hipotesis memprediksi jawaban
  [x] Hypothesis → Metric: metrik mengukur variabel dalam hipotesis
  [x] Metric → System: komponen sistem menghasilkan/mengukur metrik
  [x] System → Experiment: desain eksperimen menggunakan sistem

Koneksi Horizontal (Konsistensi):
  [x] Istilah sama di semua bagian
  [x] Variabel di RQ = variabel di hipotesis = metrik di desain
  [x] Scope tidak berubah dari masalah ke eksperimen

Rubrik Self-Assessment:
| Kriteria | 1 (Lemah) | 2 (Cukup) | 3 (Baik) | Skor |
|----------|-----------|-----------|----------|------|
| Koherensi |>2 koneksi vertikal terputus|1-2 koneksi lemah, argumen masih bisa diikuti|Semua 6 koneksi terhubung, red thread jelas|3|
| Specificity |Variabel/metrik masih abstrak, tidak ada angka|Sebagian metrik terdefinisi numerik|Semua metrik + threshold + unit pengukuran jelas|2|
| Feasibility |Timeline >6 bulan tanpa memperhitungkan sumber|Timeline 3-6 bulan dengan asumsi tertentu|Timeline 1-3 bulan realistis dengan rencana detail|3|
| Rigor     |Baseline tidak jelas atau straw man|1-2 baseline dengan justifikasi partial|2+ baseline SOTA + justifikasi pemilihan lengkap|2|
```

---

## Latihan 1 — Kompilasi Proposal Mini

Kumpulkan hasil dari WS-02 sampai WS-07 menjadi satu ringkasan proposal.

| Komponen | Sumber | Isi (1-2 kalimat) |
|----------|--------|-------------------|
| Problem Statement | WS-02 | Pengelolaan aset digital organisasi yang semakin kompleks sering kali masih dilakukan secara konvensional atau manual, sehingga rentan terhadap inefisiensi operasional serta ancaman keamanan serius seperti infeksi malware dan serangan ransomware. |
| Gap | WS-03 | Meskipun pemantauan real-time berbasis IoT menawarkan efisiensi tinggi, masih banyak organisasi yang menghadapi kendala teknis dalam proses integrasi sistem, kekhawatiran privasi data, serta kesulitan mengoptimalkan aliran data IoT untuk pengambilan keputusan. |
| RQ | WS-04 | Apakah penerapan infrastruktur Internet of Things (IoT) untuk pemantauan real-time mampu meningkatkan efisiensi operasional manajemen aset digital sekaligus mempercepat waktu respons dalam memitigasi ancaman keamanan data? |
| Hipotesis | WS-04 | $H_1$: Penerapan sistem manajemen aset berbasis IoT secara signifikan menurunkan waktu respons terhadap ancaman siber dan mengurangi biaya operasional pemeliharaan dibandingkan dengan sistem pemantauan manual. |
| Variabel & Metrik | WS-05 | IV: Metode sistem pemantauan (IoT Real-Time vs Manual).
DV: Waktu respons keamanan (detik), Frekuensi insiden ancaman siber (jumlah kasus), dan Pengurangan biaya operasional pemeliharaan (persen/Rupiah). |
| Sistem | WS-06 | Arsitektur jaringan IoT terintegrasi yang menggabungkan perangkat sensor fisik, kamera pengawas, dan pelacak GPS, yang kemudian dihubungkan ke platform cloud pusat untuk memberikan notifikasi anomali secara instan. |
| Desain Eksperimen | WS-07 | Eksperimen dilakukan melalui pengujian simulasi tren data dari waktu ke waktu (analisis historis periode 2020–2024) untuk membandingkan performa kecepatan respons dan efisiensi biaya pasca-penerapan sistem IoT terhadap data manajemen manual sebelumnya. |

---

## Latihan 2 — Integration Checklist

Verifikasi 6 koneksi kritis. Isi dengan merujuk tabel di Latihan 1.

| Koneksi | Status | Bukti |
|---------|--------|-------|
| Problem → Gap |✅|Gap muncul langsung dari masalah: pengelolaan konvensional rentan terhadap serangan siber (malware/ransomware), namun organisasi mengalami kendala teknis dan kekhawatiran privasi saat ingin mengintegrasikan solusi IoT yang ada.|
| Gap → RQ |✅|RQ langsung menanyakan solusi dari gap tersebut, yaitu apakah penerapan infrastruktur IoT untuk pemantauan real-time bisa meningkatkan efisiensi operasional sekaligus mempercepat respons terhadap ancaman siber.|
| RQ → Hypothesis |✅|$H_1$ secara langsung memprediksi jawaban atas RQ dengan menyatakan bahwa sistem berbasis IoT akan menurunkan waktu respons terhadap ancaman siber dan mengurangi biaya operasional dibanding pemantauan manual.|
| Hypothesis → Metric |✅|Variabel dalam hipotesis diturunkan menjadi metrik terukur yang jelas, yaitu waktu respons keamanan dalam satuan detik, jumlah kasus insiden siber, serta persentase pengurangan biaya operasional.|
| Metric → System |✅|Sistem IoT yang dirancang (sensor, kamera, GPS, platform cloud) memiliki komponen yang menghasilkan log data aktivitas dan notifikasi anomali secara instan, yang menjadi instrumen utama untuk menghitung metrik waktu respons.|
| System → Experiment |⚠️|Desain eksperimen menggunakan data sekunder berupa simulasi tren historis (2020-2024) untuk mengevaluasi kinerja sistem IoT, bukan menguji sistem arsitektur IoT yang dibangun secara langsung (live-testing/deployment).|

**Koneksi mana yang paling lemah?** > System → Experiment
**Bagaimana cara memperkuatnya?**
> Untuk memperkuat koneksi ini, desain eksperimen harus digeser dari yang awalnya hanya berupa pengamatan simulasi data historis/studi literatur menjadi eksperimen fungsional langsung (live-testing atau stress-testing). Peneliti perlu menjelaskan skenario uji di mana sistem IoT yang dirancang sengaja diberikan trigger berupa "anomali/simulasi serangan", lalu komponen platform cloud akan mengukur secara real-time berapa detik waktu yang dibutuhkan oleh sistem dari deteksi awal hingga notifikasi diterima oleh administrator.

**Konsistensi horizontal — apakah istilah dan scope konsisten?** [x] Ya / [ ] Tidak
> Jika tidak, di bagian mana terjadi inkonsistensi? Secara umum istilah utama (Internet of Things, Manajemen Aset Digital, Real-Time, Efisiensi, dan Waktu Respons) sudah konsisten digunakan dari bagian masalah hingga desain eksperimen. Scope penelitian juga terkunci erat pada aspek operasional keamanan dan efisiensi pemeliharaan aset digital organisasi tanpa melebar ke variabel luar seperti kepuasan pengguna (user satisfaction) atau analisis finansial profit perusahaan.

---

## Latihan 3 — Rubrik Self-Assessment

Evaluasi proposal mini menggunakan rubrik.

| Kriteria | Skor (1-3) | Justifikasi |
|----------|-----------|-------------|
| Koherensi | 3 | Semua 6 koneksi vertikal terhubung dengan kokoh. Masalah inefisiensi/serangan siber ditangani dengan solusi IoT real-time, yang diukur dengan metrik waktu respons melalui komponen sistem dalam sebuah simulasi eksperimen. |
| Specificity | 2 | Sebagian metrik sudah terdefinisi secara terukur (waktu respons dalam detik, biaya operasional). Namun, belum ada ambang batas keberhasilan (threshold value) numerik yang pasti pada hipotesis (misalnya: menurunkan waktu respons hingga < 5 detik). |
| Feasibility | 3 | Metode eksperimen menggunakan simulasi data tren historis (2020–2024) dan studi literatur komprehensif sangat realistis untuk dieksekusi dalam jangka waktu pendek (1–3 bulan) karena tidak memerlukan proses deployment perangkat fisik berskala besar. |
| Rigor | 2 | Proposal menggunakan baseline yang jelas berupa sistem pemantauan manual/konvensional, tetapi komparasi mendalam dengan metode State-of-the-Art (SOTA) dari arsitektur IoT sejenis lainnya masih perlu diperkuat di bagian tinjauan pustaka. |

**Skor total:** 10 / 12

**Apakah proposal siap untuk fase eksekusi?** [x] Ya / [ ] Belum
> Jika belum, apa yang perlu diperbaiki? Proposal sudah siap karena struktur logisnya (red thread) sudah sangat kuat. Namun, sebelum benar-benar memulai eksekusi, hal kecil yang perlu diperbaiki adalah menentukan angka target (threshold) keberhasilan kuantitatif pada bagian hipotesis/metrik serta memperjelas skenario teknis simulasinya agar jalannya pengujian lebih terarah.

---

## Refleksi

> Dari seluruh proses WS-01 sampai WS-08, bagian mana yang paling mudah dan paling sulit? Mengapa? Apa yang akan dilakukan berbeda jika mengulang dari awal?

**Bagian termudah:** Merumuskan Problem Statement dan Gap penelitian (WS-02 & WS-03). Alasan utamanya adalah karena literatur/artikel sumber sudah menyediakan data yang sangat jelas mengenai kerentanan manajemen aset konvensional terhadap serangan siber (seperti malware/ransomware) serta kendala nyata yang dihadapi organisasi dalam mengadopsi teknologi IoT.
**Bagian tersulit:** Menghubungkan Metric → System → Experiment (WS-05 hingga WS-07). Bagian ini cukup menantang karena artikel sumber cenderung menyajikan pemodelan sistem dan evaluasi secara konseptual-simulatif. Menyelaraskan komponen arsitektur IoT agar bisa menghasilkan metrik waktu respons yang konkret dalam sebuah skenario eksperimen memerlukan ketelitian tinggi agar argumen tidak terputus (cognitive trap).
**Yang akan dilakukan berbeda:**
> Jika mengulang dari awal, saya akan mendefinisikan target metrik numerik dan baseline SOTA sejak awal penyusunan metodologi. Selain itu, daripada hanya mengandalkan simulasi data historis, saya akan mencoba merancang skenario eksperimen berupa live stress-testing skala kecil (misalnya menggunakan prototype atau simulator jaringan lokal). Hal ini akan membuat koneksi antara arsitektur sistem dan pembuktian eksperimen menjadi jauh lebih kokoh, objektif, dan bernilai ilmiah tinggi.