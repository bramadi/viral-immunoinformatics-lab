# Praktikum Imunoinformatika

Repositori ini berisi materi dan data praktikum imunoinformatika, mencakup
analisis sequence protein antigenik dari lima virus model: HIV-1, RSV,
Measles morbillivirus, Hepatitis B virus, dan Lyssavirus rabies.

## Tujuan Praktikum

Mahasiswa akan mempelajari alur kerja dasar imunoinformatika, mulai dari
pengambilan sequence protein dari NCBI, quality control, hingga prediksi
epitope (B-cell dan/atau T-cell) yang relevan secara klinis (misalnya untuk
target vaksin atau diagnostik).

## Struktur Repositori

```
imunoinformatika-praktikum/
├── README.md
├── LICENSE
├── .gitignore
├── data/
│   ├── raw_sequences/        # Sequence FASTA mentah
│   └── metadata/
│       └── sequence_metadata.csv   # Metadata & sumber tiap sequence
├── docs/                      # Panduan praktikum
├── scripts/                   # Script analisis (epitope prediction, dll.)
├── results/                   # Output analisis
└── figures/                   # Visualisasi hasil
```

## Data Sequence

Lima protein antigenik virus digunakan sebagai model dalam praktikum ini.
Detail lengkap (accession, panjang sequence, sumber) tersedia di
[`data/metadata/sequence_metadata.csv`](data/metadata/sequence_metadata.csv).

| File | Organisme | Protein | Accession |
|---|---|---|---|
| `hbv_small_envelope_HBsAg.fasta` | Hepatitis B virus | Small envelope protein (HBsAg) | YP_009173871.1 |
| `hiv1_capsid_p24.fasta` | Human immunodeficiency virus 1 | Capsid (p24) | NP_579880.1 |
| `measles_hemagglutinin_H.fasta` | Measles morbillivirus | Hemagglutinin | NP_056923.1 |
| `rabies_glycoprotein_G.fasta` | Lyssavirus rabies | Transmembrane glycoprotein G | NP_056796.1 |
| `rsv_fusion_glycoprotein_F.fasta` | Human respiratory syncytial virus | Fusion glycoprotein F | NP_056863.1 |

Seluruh sequence diunduh dari NCBI Protein database (RefSeq) pada 23 Juli 2026.

## Cara Reproduksi

1. Clone repositori ini
2. Sequence mentah tersedia langsung di `data/raw_sequences/` — tidak
   perlu didownload ulang
3. Ikuti panduan langkah demi langkah di
   [`docs/panduan_praktikum.md`](docs/panduan_praktikum.md)

## Lisensi

Lihat [`LICENSE`](LICENSE).
