# Panduan Praktikum Imunoinformatika
## Analisis Protein Antigenik Virus untuk Prediksi Epitope

---

## 1. Pendahuluan

Imunoinformatika adalah cabang bioinformatika yang mempelajari sistem imun
menggunakan pendekatan komputasi — misalnya untuk memprediksi bagian protein
(epitope) yang dapat dikenali oleh antibodi (B-cell epitope) atau oleh sel T
(T-cell epitope). Pendekatan ini banyak digunakan dalam pengembangan vaksin,
alat diagnostik, dan pemahaman mekanisme infeksi virus.

Pada praktikum ini, mahasiswa akan bekerja dengan lima protein antigenik dari
lima virus berbeda, mempelajari karakteristik masing-masing, dan melakukan
prediksi epitope menggunakan tools bioinformatika standar.

### Tujuan Pembelajaran

Setelah menyelesaikan praktikum ini, mahasiswa diharapkan mampu:

1. Menjelaskan konsep dasar epitope, antigen, dan imunogenisitas
2. Mengambil dan memvalidasi sequence protein dari database NCBI
3. Melakukan prediksi epitope B-cell dan/atau T-cell menggunakan tools daring
4. Menginterpretasikan hasil prediksi dalam konteks biologis masing-masing virus
5. Mendokumentasikan alur kerja analisis secara reproducible

---

## 2. Data Praktikum

Lima protein berikut digunakan sebagai model dalam praktikum ini. Detail
lengkap tersedia di [`data/metadata/sequence_metadata.csv`](../data/metadata/sequence_metadata.csv).

| No | Virus | Protein | Accession | Panjang (aa) | Relevansi Klinis |
|---|---|---|---|---|---|
| 1 | Hepatitis B virus | Small envelope protein (HBsAg) | YP_009173871.1 | 226 | Target vaksin utama; situs mutasi *escape* dapat mengganggu deteksi diagnostik |
| 2 | Human immunodeficiency virus 1 | Capsid (p24) | NP_579880.1 | 231 | Target diagnostik (deteksi antigen p24 pada infeksi akut) |
| 3 | Measles morbillivirus | Hemagglutinin (H) | NP_056923.1 | 617 | Target utama vaksin campak; berikatan dengan reseptor sel inang |
| 4 | Lyssavirus rabies | Transmembrane glycoprotein (G) | NP_056796.1 | 524 | Satu-satunya protein permukaan rabies; target vaksin dan antibodi netralisasi |
| 5 | Human respiratory syncytial virus | Fusion glycoprotein (F) | NP_056863.1 | 574 | Target vaksin RSV generasi terbaru (mis. prefusion F) |

> **Catatan:** Kelima sequence merupakan RefSeq reference sequence dari NCBI,
> bukan strain spesifik Indonesia. Untuk analisis mutasi spesifik populasi
> (seperti proyek HBsAg escape mutation), sequence ini berfungsi sebagai
> *reference*, sedangkan sequence query berasal dari isolat lokal.

---

## 3. Alur Kerja Praktikum

### Tahap 1. Persiapan dan Quality Control

1. Buka file FASTA di `data/raw_sequences/`
2. Periksa header sequence (baris yang diawali `>`). Pastikan organism dan
   accession sesuai dengan tabel di atas
3. Periksa apakah sequence mengandung karakter selain 20 asam amino standar
   (misalnya `X`, tanda ambiguitas)

### Tahap 2. Analisis Karakteristik Protein

Untuk setiap protein, catat:
- Panjang sequence (asam amino)
- Perkiraan berat molekul dan titik isoelektrik (dapat dihitung menggunakan
  [ExPASy ProtParam](https://web.expasy.org/protparam/))
- Domain fungsional (jika diketahui — misal domain transmembran pada
  glikoprotein G rabies)

### Tahap 3. Prediksi Epitope

Beberapa tools daring yang dapat digunakan (tanpa instalasi lokal):

| Tools | Jenis Prediksi | Link |
|---|---|---|
| IEDB Analysis Resource | B-cell & T-cell epitope | https://www.iedb.org |
| BepiPred | B-cell epitope (linear) | https://services.healthtech.dtu.dk/services/BepiPred-3.0/ |
| NetMHCpan | T-cell epitope (MHC class I) | https://services.healthtech.dtu.dk/services/NetMHCpan-4.1/ |
| NetMHCIIpan | T-cell epitope (MHC class II) | https://services.healthtech.dtu.dk/services/NetMHCIIpan-4.1/ |

**Langkah umum:**
1. Salin sequence dalam format FASTA dari `data/raw_sequences/`
2. Masukkan ke tool prediksi pilihan (paste langsung, sesuai instruksi masing-masing situs)
3. Jalankan prediksi dengan parameter default terlebih dahulu
4. Simpan hasil prediksi ke folder `results/` dengan format nama:
   `{virus}_{tool}_prediction.csv` atau `.txt`

### Tahap 4. Interpretasi dan Diskusi

Untuk setiap virus, diskusikan:
- Apakah epitope yang diprediksi berada di region yang secara biologis
  masuk akal (misalnya region permukaan/exposed, bukan region transmembran)?
- Bagaimana relevansi epitope tersebut dengan target vaksin atau diagnostik
  yang sudah ada di literatur?
- Apakah ada perbedaan pola antara protein struktural kecil (HBsAg, p24)
  dan glikoprotein besar (H, G, F)?

---

## 4. Worksheet Praktikum

Gunakan tabel berikut untuk mencatat hasil kerja per protein:

| Virus | Panjang (aa) | Jumlah Epitope B-cell Terprediksi | Epitope Tertinggi (posisi, skor) | Catatan Interpretasi |
|---|---|---|---|---|
| HBV (HBsAg) | | | | |
| HIV-1 (p24) | | | | |
| Measles (H) | | | | |
| Rabies (G) | | | | |
| RSV (F) | | | | |

---

## 5. Output yang Diharapkan

Setiap kelompok/mahasiswa diharapkan menghasilkan:

1. File hasil prediksi epitope untuk kelima protein (disimpan di `results/`)
2. Ringkasan/tabel perbandingan (dapat menggunakan worksheet di atas)
3. Singkat pembahasan (1–2 halaman) yang mengaitkan hasil prediksi dengan
   konteks biologis dan klinis masing-masing virus

---

## 6. Referensi Lanjutan

- Vita R, Blazeska N, Marrama D, et al. "The Immune Epitope Database (IEDB): 2024 update." *Nucleic Acids Research*, Volume 53, Issue D1, 6 January 2025, Pages D436–D443. https://doi.org/10.1093/nar/gkae1092
- Clifford J, Høie MH, Deleuran S, Peters B, Nielsen M, Marcatili P. "BepiPred-3.0: Improved B-cell epitope prediction using protein language models." *Protein Science*, 2022;31(12):e4497. https://doi.org/10.1002/pro.4497
- Situs NCBI Protein: https://www.ncbi.nlm.nih.gov/protein

---

*Dokumen ini merupakan bagian dari repositori [`viral-immunoinformatics-lab`](../README.md).*
