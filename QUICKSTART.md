# Quick Start Guide

## Getting Started in 5 Minutes

### Step 1: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 2: Run the Notebook
```bash
jupyter notebook salesetl_corrected-1.ipynb
```

### Step 3: Execute All Cells
- Click "Kernel" → "Restart & Run All"
- Watch the ETL pipeline process the data
- Check the generated SQLite database: `superstore_sales_clean.db`

### Step 4: Query the Database
```python
import sqlite3
import pandas as pd

conn = sqlite3.connect('superstore_sales_clean.db')
df = pd.read_sql_query("SELECT * FROM SUPERSTORE_SALES_CLEAN LIMIT 10", conn)
print(df)
conn.close()
```

## What You'll See

1. **Extract**: Dataset downloaded from Kaggle (~12,617 records)
2. **Transform**: Data cleaned and validated (~11,737 clean records)
3. **Load**: Clean data saved to SQLite database
4. **Verify**: SQL queries confirm successful pipeline execution

## Troubleshooting

**Issue**: Kaggle download fails  
**Solution**: Ensure kagglehub is installed: `pip install kagglehub`

**Issue**: Jupyter not found  
**Solution**: Install Jupyter: `pip install jupyter`

**Issue**: Database file not created  
**Solution**: Check write permissions in the directory

## Next Steps

- Open the database with [DB Browser for SQLite](https://sqlitebrowser.org/)
- Connect Power BI or Tableau to the database
- Explore the data with SQL queries
- Customize the transformation logic

---

**Need help?** Check the full documentation in `docs/ETL_PROCESS.md`
