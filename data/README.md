# Dataset

**Sumber:** Kaggle, *Buy Now, Pay Later (BNPL) Fintech ML Dataset*
**Tautan:** [https://www.kaggle.com/datasets/shree0910/buy-now-and-pay-later-fintech-ml-dataset](https://www.kaggle.com/datasets/shree0910/buy-now-and-pay-later-fintech-ml-dataset)

## Cara Menggunakan

1. Unduh dataset dari tautan di atas.
2. Letakkan file `Buy_Now_Pay_Later_BNPL_CreditRisk_Dataset.csv` di folder ini (`data/`).
3. Jalankan notebook `notebooks/BNPL_Analysis.ipynb`.

## Deskripsi Singkat

- 10.345 baris dan 17 kolom (32 kolom setelah feature engineering)
- Periode 2023–2024, 6 negara
- Target: `default_flag` (1 = gagal bayar, 0 = membayar tepat waktu)

File hasil ekspor (`bnpl_clean_featured.csv` dan `.parquet`) dibuat otomatis oleh notebook dan tidak disimpan di repository.
