# Data Engineering Practice Notebooks

Hands-on daily ETL practice notebooks showing progression
from pandas fundamentals to production-style pipelines.
Built independently — each notebook adds new concepts.

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
- Dictionary-based `fillna` for null handling
- Dead Letter Queue (DLQ) pattern — invalid records
  routed to separate table instead of silently dropped
- SQL business insights: content split, top directors,
  country hub analysis
- `groupby().transform()` to broadcast group stats

---

### Day 2 — Shein E-Commerce Multi-Source ETL
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
- Fixed column names — spaces to snake_case
- Parsed date strings to datetime, extracted
  year, month, quarter, order_dayname
- Calculated shipping duration (ship_days)
- numpy: sales tiers, 95th percentile outlier
  detection, discount levels, profit status
- apply/lambda: customer labels, shipping speed
- map: region to zone classification
- 5 groupby KPI aggregations
- 4 SQL queries including RANK() window function
- Parquet backup saved (568 KB)

**Key findings:**
- Technology = highest revenue ($836K)
- 933 bad deals = heavy discount + negative profit
- Phones = #1 sub-category by sales ($330K)

---

### Day 4 — UPI Payment ETL (Independent Practice)
[`04_payment_etl_independent_practice.ipynb`](04_payment_etl_independent_practice.ipynb)

**Dataset:** India Payment Pulse — 10,000 UPI transactions
**Stack:** Python · pandas · NumPy · SQLAlchemy · SQLite · SQL

**What I built:**
- Loaded and validated 10,000 simulated UPI transactions
- Multi-step cleaning: null removal, negative filtering,
  deduplication, status standardisation (9,211 clean rows)
- Feature engineering: hour, day_name, month, quarter,
  is_weekend from timestamp
- numpy: amount_tier (HIGH/MEDIUM/LOW), 99th percentile
  outlier detection, flag_suspicious transactions
- 5 groupby KPIs: city revenue, UPI app success rate,
  category averages, peak transaction hours,
  status distribution
- Loaded to SQLite — transactions + suspicious_transactions
- 3 SQL queries: top merchants, avg by status,
  DENSE_RANK city leaderboard using CTE

**Key findings:**
- Peak hours: 14:00, 09:00, 23:00
- Transfer category highest avg amount (₹25,811)
- Ghaziabad #1 city by transaction count
- 1,348 suspicious transactions flagged

---

### Day 5 — Live API Ingestion — Currency Exchange ETL
[`05_api_ingestion_currency_etl.ipynb`](05_api_ingestion_currency_etl.ipynb)

**Data Source:** Open Exchange Rates API (live, real-time)
**Stack:** Python · requests · pandas · SQLAlchemy · SQLite · SQL

**What I built:**
- Called live REST API — parsed JSON response
- Filtered 10 currencies from 166 available
- Calculated rate_vs_inr for each currency
- Flagged strong currencies (>₹50 per unit)
- Loaded to SQLite with SQL analytics
- RANK() window function on live data

**Key findings:**
- GBP strongest vs INR (₹127.6 per pound)
- JPY weakest (₹0.59 per yen)
- 6 of 10 currencies stronger than ₹50

---

## Progression

| Notebook | Dataset | Rows | Key Concepts Added |
|---|---|---|---|
| Day 1 — Netflix | 1 file | 8,807 | DLQ, groupby transform, SQL |
| Day 2 — Shein | 21 files | 82,105 | Multi-source, regex, feature eng |
| Day 3 — Superstore | 1 file | 9,994 | numpy, apply/lambda, SQL windows |
| Day 4 — UPI Payments | 1 file | 10,000 | Independent practice, CTE, DENSE_RANK |

---

## Skills Demonstrated
---

## Skills Demonstrated

| **Stage**          | **Techniques / Tools**                                                                 |
|---------------------|----------------------------------------------------------------------------------------|
| **Data Ingestion**  | `pd.read_csv`, `pd.concat`, `kagglehub`                                                |
| **Transformation**  | Pandas cleaning, NumPy vectorized operations                                           |
| **Feature Eng.**    | Date extraction, custom categorisation                                                 |
| **Data Quality**    | DLQ pattern, null handling, deduplication                                              |
| **SQL Analytics**   | `GROUP BY`, `HAVING`, window functions, `RANK()`                                       |
| **Storage**         | SQLite via SQLAlchemy, Parquet output                                                  |

---

## How to Run

```bash
pip install pandas numpy sqlalchemy kagglehub pyarrow
jupyter notebook
```

Open any notebook and run cells top to bottom.
Datasets download automatically via `kagglehub`.

---

## Author

**Gopal Patil**
[GitHub](https://github.com/gopalpatil15)
