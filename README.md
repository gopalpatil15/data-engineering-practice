# Data Engineering Practice Notebooks

Hands-on daily ETL practice notebooks showing progression
from pandas fundamentals to production-style pipelines.
Each notebook builds on the previous one in complexity.

---

## Notebooks

### Day 1 — Netflix ETL Pipeline
[`01_netflix_etl_pandas_sql.ipynb`](01_netflix_etl_pandas_sql.ipynb)

**Dataset:** Netflix Shows (Kaggle) — 8,807 rows · 12 columns
**Stack:** Python · pandas · SQLAlchemy · SQLite · SQL

**What I built:**
- Loaded and explored real-world dataset
- Vectorized string cleaning with `.str.strip()`
- Deduplication on `show_id` key column
- Dictionary-based `fillna` for selective null handling
- Dead Letter Queue (DLQ) pattern — invalid records
  routed to separate table instead of silently dropped
- SQL business insights: content split, top directors,
  country hub analysis
- `groupby().transform()` to broadcast group stats

---

<<<<<<< HEAD
### Day 2 — Shein E-Commerce Multi-Source ETL Pipeline
=======
### Day 2 — Shein E-Commerce Multi-Source ETL
>>>>>>> bb119a2 (Day 4)
[`02_shein_ecommerce_etl_multifile_pipeline.ipynb`](02_shein_ecommerce_etl_multifile_pipeline.ipynb)

**Dataset:** Shein US Product Listings — 21 CSV files · 82,105 rows
**Stack:** Python · pandas · NumPy · SQLAlchemy · SQLite · Regex

**What I built:**
- Merged 21 heterogeneous CSV files using `pd.concat`
- Extracted numeric values from mixed-format strings
  using regex + `pd.to_numeric(errors='coerce')`
- Built `clean_sales()` transformer handling shorthand
  notation (`3.7k` → `3700`)
- Extracted `pack_size` and `sub_category` from raw text
- Engineered `original_price` using `np.where`
- Loaded 82,105 rows into SQLite via SQLAlchemy

---

### Day 3 — Superstore ETL + SQL Analytics
[`03_superstore_etl_sql_pipeline.ipynb`](03_superstore_etl_sql_pipeline.ipynb)

**Dataset:** Superstore Sales (Kaggle) — 9,994 rows · 21 columns
**Stack:** Python · pandas · NumPy · SQLAlchemy · SQLite · SQL

**What I built:**
- Fixed column names (spaces → snake_case)
- Parsed date strings → datetime, extracted year/month/quarter
- Calculated shipping duration (`ship_days`)
- numpy transforms: `np.where` sales tiers, 95th percentile
  outlier detection, discount levels, profit status
- apply/lambda: customer labels, shipping speed categories
- map: region → zone classification
- 5 groupby KPI aggregations with business insights
- 4 SQL queries including window function `RANK() OVER`
- Saved Parquet backup (568 KB)

**Key findings:**
- Technology = highest revenue ($836K, 1,847 orders)
- 933 "bad deals" = high discount + negative profit
- California = top state ($401K net revenue)
- Phones = #1 sub-category by sales ($330K)

---

## Progression

| Notebook | Dataset | Rows | Key Concepts |
|---|---|---|---|
| Day 1 — Netflix | 1 file | 8,807 | DLQ, groupby transform, SQL |
| Day 2 — Shein | 21 files | 82,105 | Multi-source, regex, np.where |
| Day 3 — Superstore | 1 file | 9,994 | numpy, apply/lambda, SQL window functions |

---

<<<<<<< HEAD
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
=======
## Skills Demonstrated
>>>>>>> bb119a2 (Day 4)
