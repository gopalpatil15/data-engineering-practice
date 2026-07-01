# Data Engineering Learning Notebooks

Hands-on daily practice notebooks documenting my progression
from pandas fundamentals to production-style ETL pipelines.
Each notebook builds on the previous one in complexity and scale.

---

## Notebooks

### Day 1 — Netflix ETL Pipeline
[`01_netflix_etl_pandas_sql.ipynb`](01_netflix_etl_pandas_sql.ipynb)

**Dataset:** Netflix Shows (Kaggle) — 8,807 rows · 12 columns  
**Stack:** Python · pandas · SQLAlchemy · SQLite · SQL

**What I built:**
- Loaded and explored a real-world dataset
- Vectorized string cleaning with `.str.strip()`
- Deduplication on `show_id` key column
- Dictionary-based `fillna` for selective null handling
- Dead Letter Queue (DLQ) pattern — separated invalid records
  into a separate `netflix_shows_dlq` table instead of silently
  dropping or patching them
- Loaded clean data into SQLite via SQLAlchemy
- SQL business insights: content split, top directors,
  country hub analysis
- `groupby().transform()` to broadcast group-level stats
  back to individual rows (HAVING-equivalent filtering)

**Key concept learned:**  
DLQ pattern — routing invalid records to a separate table
for investigation rather than silently dropping them.
Same pattern used in Kafka, SQS, and enterprise ETL systems.

---

### Day 2 — Shein E-Commerce Multi-Source ETL Pipeline
[`02_shein_ecommerce_etl_multifile_pipeline.ipynb`](02_shein_ecommerce_etl_multifile_pipeline.ipynb)

**Dataset:** Shein US Product Listings (Kaggle) — 21 CSV files · 82,105 rows  
**Stack:** Python · pandas · NumPy · SQLAlchemy · SQLite · Regex

**What I built:**
- Ingested 21 heterogeneous CSV files with different schemas
  using `pd.concat` with automatic schema alignment
- Extracted numeric values from mixed-format strings
  (`rank-title`, `discount`) using regex + `pd.to_numeric(errors='coerce')`
- Built a custom `clean_sales()` transformer handling
  shorthand notation (`3.7k` → `3700`) using regex extraction
  and conditional multiplier logic
- Extracted `pack_size` feature from raw product title text
  using regex pattern matching
- Cleaned `sub_category` from raw ranking strings
  (`"in Hand Tools"` → `"Hand Tools"`)
- Engineered `original_price` from discounted price using
  `np.where` for conditional vectorized calculation
- Loaded 82,105 clean rows into SQLite via SQLAlchemy
- SQL aggregation: average discount by product sub-category

**Key concept learned:**  
Multi-source schema alignment — when upstream files have
inconsistent column structures, `pd.concat` with `ignore_index=True`
maps identical columns together and fills gaps with NaN,
which is then handled downstream in the transform layer.

---

## Progression

| Notebook | Dataset Size | New Concepts Added |
|---|---|---|
| Day 1 — Netflix | 8,807 rows · 1 file | pandas basics, DLQ, groupby transform, SQL |
| Day 2 — Shein | 82,105 rows · 21 files | multi-source ingestion, regex extraction, feature engineering, np.where |

---

## How to Run

```bash
pip install pandas numpy sqlalchemy kagglehub
jupyter notebook
```

Open any notebook and run cells top to bottom.
Datasets are downloaded automatically via `kagglehub`.

---

## Author

**Gopal Patil**  
[GitHub](https://github.com/gopalpatil15) ·
[LinkedIn](https://linkedin.com/in/gopalpatil)
