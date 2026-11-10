# Dataset

**Source:** Kaggle, *Buy Now, Pay Later (BNPL) Fintech ML Dataset*
**Link:** [https://www.kaggle.com/datasets/shree0910/buy-now-and-pay-later-fintech-ml-dataset](https://www.kaggle.com/datasets/shree0910/buy-now-and-pay-later-fintech-ml-dataset)

## How to Use

1. Download the dataset from the link above.
2. Place the file `Buy_Now_Pay_Later_BNPL_CreditRisk_Dataset.csv` in this folder (`data/`).
3. Run the notebook `notebooks/BNPL_Analysis.ipynb`.

## Brief Description

- 10,345 rows and 17 columns (32 columns after feature engineering)
- Period: 2023–2024, 6 countries
- Target: `default_flag` (1 = defaulted, 0 = paid on time)

The exported files (`bnpl_clean_featured.csv` and `.parquet`) are created automatically by the notebook and are not stored in the repository.
