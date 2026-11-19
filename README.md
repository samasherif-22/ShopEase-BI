# ShopEase BI – Order-to-Delivery Revenue Leakage

## Project Overview

ShopEase BI is a Business Intelligence project focused on analyzing order-to-delivery processes and identifying potential revenue leakage.

---

## Dataset

- **Source:** `shopease_raw_orders.csv`
- **Raw Records:** 10,020
- **Columns:** 16

---

## ETL Progress

### 1. Extraction – Completed

- Extracted data from the CSV file using SSIS.
- Loaded the raw data into SQL Server.
- **Database:** `ShopEaseDB`
- **Table:** `dbo.Raw_Orders`

**Extraction Summary**

| Metric | Value |
|---|---:|
| Loaded Rows | 10,020 |
| Unique OrderIDs | 10,000 |
| Duplicate OrderIDs | 20 |

### 2. Transformation – Pending

The next phase will focus on addressing the documented Data Quality issues while preserving the original raw data.

---

## Project Structure

```text
ShopEase-BI/
├── Dataset/
│   └── shopease_raw_orders.csv
├── SSIS/
│   └── ShopEase_ETL/
├── SQL/
├── Documentation/
├── .gitignore
└── README.md
```

---

## Technologies

- SQL Server 2022
- SQL Server Management Studio (SSMS)
- SQL Server Integration Services (SSIS)
- Visual Studio
- Git & GitHub

---

## Team Workflow

The Extraction phase is completed. The Transformation phase will continue from the `dbo.Raw_Orders` table.

---

*Turning Raw Data into Business Insights.*
