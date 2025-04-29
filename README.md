
# 🏆 Nobel Laureates: Data-Driven Discoveries

## 🔍 Project Overview

This project showcases an end-to-end **Azure Data Engineering pipeline** designed to analyze the Nobel Prize Laureates dataset. It applies the **Medallion Architecture**, builds a **Star Schema**, and presents insights through an interactive **Power BI dashboard**.

---

## 📌 Problem Statement

The Nobel Prize dataset is rich but raw and unstructured. The main objectives were:
- Ingest the data securely and efficiently.
- Clean, transform, and normalize the data.
- Model it for business intelligence (BI) reporting.
- Visualize trends, patterns, and insights in Power BI.

---

## 🛠️ Tools & Technologies Used

| Component             | Technology                      |
|----------------------|----------------------------------|
| Ingestion            | Azure Data Factory (HTTP)       |
| Storage              | Azure Data Lake Storage Gen2    |
| Processing           | Azure Databricks (PySpark)      |
| Format               | Delta Lake                      |
| Modeling             | 3NF → Star Schema (Gold Layer)  |
| Visualization        | Power BI Desktop                |
| Hashing              | SHA2 for surrogate keys         |

---

## 🏗️ Architecture: Medallion Layers

```text
          ┌────────────┐
          │   Bronze   │  ← Raw Data from Nobel_Price.csv
          └────────────┘
                ↓
          ┌────────────┐
          │   Silver   │  ← Cleaned, transformed, typed
          └────────────┘
                ↓
          ┌────────────┐
          │    Gold    │  ← Star Schema for reporting
          └────────────┘
```

---

## 🧱 Data Modeling

### 🔹 Fact Table
- `fact_awards`: Links all dimensions, stores key metrics like `Age_at_award`.

### 🔹 Dimension Tables
- `dim_laureate`: Name, gender, birth/death dates, location keys.
- `dim_organization`: Organization name, city, country.
- `dim_location`: Unique location ID using SHA2(city, country, type).
- `dim_category`: Prize categories (e.g., Medicine, Peace).
- `dim_time`: Year, decade, formatted time fields.

---

## 💡 Key Logic Implemented

- Cleaned duplicates and nulls.
- Converted data types (`date`, `int`, etc.).
- Generated surrogate keys using:
  ```python
  sha2(concat_ws("", city, country, location_type), 256)
  ```
- Calculated columns:
  - `Age_at_award`
  - `Decade`

---

## 📊 Power BI Dashboard

### ✔ KPIs
- 🎯 **Total Laureates**: 959  
- 🧓 **Average Age at Award**: 62.58  
- 🏛️ **Top Organization**: Yale University  
- 🌍 **Top Country**: USA  

### ✔ Visuals
- Prizes by Category & Year
- Gender Distribution
- Birth Country Mapping (World Map)
- Awards per Organization & Country
- Time Series from 1900–2020

### 🔍 Sample Insight
> Most laureates are male and aged between 60–65. The USA leads in Nobel prizes, particularly in Physics and Medicine.

---

## 🧠 Learnings

- Implemented **Delta Lake Medallion Architecture** using Databricks.
- Applied **3NF normalization and Star Schema modeling**.
- Built a scalable **ETL pipeline** in PySpark.
- Created **KPI-driven dashboards** in Power BI.

---

## 🚀 Future Enhancements

- Schedule ADF pipelines for automation.
- Add CI/CD integration for production deployment.
- Add drill-through and bookmarks in Power BI.

---

## 📂 Project Structure

```
📁 Nobel-Project/
│
├── 📄 Nobel_Price.csv                # Raw dataset
├── 📒 Nobel_Price.ipynb              # ETL in PySpark (Databricks)
├── 📊 Project.pdf                    # Power BI visual insights
├── 📄 README.md                      # Project documentation
```

---

## 🙏 Acknowledgements

- Dataset: [nobelprize.org](https://www.nobelprize.org/)
- Tools: Azure Free Services, Power BI, Databricks Community Edition

---

## 📬 Contact

**Prathamesh Pahune**  
📧 prathmeshpahune24@gmail.com  
💼 [LinkedIn](https://linkedin.com/in/prathameshpahune) 

---
