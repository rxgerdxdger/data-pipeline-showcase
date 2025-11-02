# ETL Process Documentation

## Overview
Detailed explanation of the Extract, Transform, Load process.

---

## Phase 1: Extract

**Data Source**: Kaggle Superstore Sales Dataset  
**Method**: KaggleHub API  
**Output**: Pandas DataFrame with 12,617 raw records

```python
path = kagglehub.dataset_download('dataobsession/superstore-sales-the-data-quality-challenge')
df = pd.read_csv(os.path.join(path, csv_files[0]))
```

---

## Phase 2: Transform

### Data Quality Issues
1. Duplicate records
2. Missing dates
3. Missing categories
4. Missing critical fields (Quantity, Sales, Profit)
5. Incorrect data types

### Transformation Steps
```python
def transform_data(df):
    df_clean = df.drop_duplicates()
    df_clean = df_clean.dropna(subset=['Order Date'])
    df_clean['Order Date'] = pd.to_datetime(df_clean['Order Date'])
    df_clean['Category'] = df_clean['Category'].fillna('Unknown')
    df_clean = df_clean.dropna(subset=['Quantity', 'Sales', 'Profit'])
    df_clean['total_amount'] = df_clean['Quantity'] * df_clean['Sales']
    df_clean['processed_at'] = datetime.now()
    return df_clean
```

**Result**: 11,737 clean records (93% retention)

---

## Phase 3: Load

**Database**: SQLite  
**Table**: SUPERSTORE_SALES_CLEAN  
**Method**: Pandas `to_sql()`

```python
conn = sqlite3.connect('superstore_sales_clean.db')
df_clean.to_sql('SUPERSTORE_SALES_CLEAN', conn, if_exists='replace', index=False)
```

---

## Validation

```sql
SELECT COUNT(*) FROM SUPERSTORE_SALES_CLEAN;
SELECT Category, SUM(total_amount) FROM SUPERSTORE_SALES_CLEAN GROUP BY Category;
```

---

## Performance
- Extraction: ~2-5 seconds
- Transformation: ~1-2 seconds
- Loading: ~1 second
- **Total**: ~5-10 seconds
