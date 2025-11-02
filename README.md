# 📊 Superstore Sales ETL Pipeline

A complete **Extract, Transform, Load (ETL)** data pipeline project that processes Kaggle's Superstore sales dataset, cleans the data, and loads it into an SQLite database for analysis.

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)](https://jupyter.org/)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

---

## 📋 Project Overview

This ETL pipeline demonstrates end-to-end data engineering skills including:
- **Extracting** data from Kaggle using KaggleHub API
- **Transforming** messy data by handling duplicates, missing values, and data type issues
- **Loading** cleaned data into a SQLite database
- **Validating** data quality improvements with SQL queries

**Key Achievement**: Improved data quality from 12,617 raw records to 11,737 clean records (93% retention rate) by removing duplicates and handling missing critical fields.

---

## 🎯 Skills Demonstrated

- **Python Programming**: pandas, logging, datetime
- **Data Cleaning**: Duplicate removal, missing value handling, data type conversion
- **ETL Design**: Modular pipeline with extract/transform/load phases
- **Database Operations**: SQLite integration, table creation, bulk loading
- **Data Quality Management**: Validation, error handling, logging
- **Documentation**: Clear code comments and project documentation

---

## 📊 Data Quality Improvements

| Metric | Before ETL | After ETL | Improvement |
|--------|-----------|-----------|-------------|
| **Total Records** | 12,617 | 11,737 | -880 bad records |
| **Duplicates** | Present | 0 | 100% removed |
| **Missing Dates** | Present | 0 | 100% handled |
| **Missing Critical Fields** | Present | 0 | 100% cleaned |
| **Data Quality** | 🟡 Poor | ✅ High | +93% |

---

## 🚀 Quick Start

### Prerequisites

```bash
pip install pandas kagglehub jupyter
```

### Running the Pipeline

1. **Clone or download this project**
2. **Open the Jupyter Notebook**
```bash
jupyter notebook salesetl_corrected-1.ipynb
```
3. **Run all cells** to execute the complete ETL pipeline
4. **Query the database** using the provided SQL examples

---

## 📁 Project Structure

```
superstore-etl-pipeline/
│
├── salesetl_corrected-1.ipynb    # Main ETL pipeline notebook
├── README.md                      # Project documentation (this file)
├── QUICKSTART.md                  # 5-minute setup guide
├── requirements.txt               # Python dependencies
├── LICENSE                        # MIT license
├── .gitignore                     # Git ignore patterns
│
└── docs/
    └── ETL_PROCESS.md             # Detailed ETL documentation
```

---

## 🔄 ETL Pipeline Workflow

### 1. Extract 📥
- Download Superstore sales dataset from Kaggle
- Load CSV file into pandas DataFrame
- Initial: **12,617 rows × 19 columns**

### 2. Transform 🔧
- Remove duplicate records
- Handle missing dates
- Convert date strings to datetime
- Fill missing categories with 'Unknown'
- Remove incomplete records
- Calculate `total_amount = Quantity × Sales`
- Add processing timestamp
- Final: **11,737 rows × 21 columns**

### 3. Load 💾
- Create SQLite database: `superstore_sales_clean.db`
- Bulk insert cleaned records
- Verify with SQL queries

---

## 📈 Technologies Used

| Technology | Purpose |
|-----------|---------|
| **Python 3.8+** | Core programming language |
| **Pandas** | Data manipulation |
| **KaggleHub** | Dataset download |
| **SQLite3** | Database storage |
| **Jupyter** | Interactive development |
| **Logging** | Pipeline monitoring |

---

## 🔗 Connect to BI Tools

### Power BI
1. Get Data → SQLite
2. Browse to `superstore_sales_clean.db`
3. Select `SUPERSTORE_SALES_CLEAN` table

### Tableau
1. Connect to Data → SQLite
2. Select database file
3. Start building dashboards

---

## 📝 Next Steps

**Beginner:**
- Add data validation rules
- Export to CSV format
- Create summary reports

**Intermediate:**
- Implement incremental loading
- Add email notifications
- Build data quality dashboard

**Advanced:**
- Deploy on AWS/Azure
- Integrate Apache Airflow
- Build data warehouse

---

## 📄 License

MIT License - see [LICENSE](LICENSE) file

---

## 👤 Author

**Your Name**
- GitHub: [@yourusername](https://github.com/yourusername)
- LinkedIn: [linkedin.com/in/yourprofile](https://linkedin.com/in/yourprofile)
- Email: your.email@example.com

---

## 🙏 Acknowledgments

- Dataset: [Kaggle Superstore Sales](https://www.kaggle.com/datasets/dataobsession/superstore-sales-the-data-quality-challenge)
- Built for data engineering portfolio development

---

⭐ **If you found this helpful, please star the repo!**

**Built with ❤️ for Data Engineering**
