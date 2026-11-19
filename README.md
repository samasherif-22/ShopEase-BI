# ShopEase BI – Order-to-Delivery Revenue Leakage

## Project Overview

ShopEase BI is a Business Intelligence project focused on analyzing the order-to-delivery process and identifying potential revenue leakage through data preparation, quality checks, and transformation.

The project uses an SSIS ETL pipeline to extract raw order data, clean and standardize it, and load the transformed data into SQL Server for further analysis.

---

## Dataset

- **Source:** `shopease_raw_orders.csv`
- **Raw Records:** 10,020
- **Columns:** 16
- **Format:** CSV

### Initial Data Overview

| Metric | Value |
|---|---:|
| Total Rows | 10,020 |
| Unique Order IDs | 10,000 |
| Duplicate Order IDs | 20 |

---

## ETL Progress

### 1. Extraction – Completed

- Extracted data from the source CSV file using SSIS.
- Loaded the original data into SQL Server.
- Preserved the raw data for reference and further processing.

**Destination:**
- Database: `ShopEaseDB`
- Table: `dbo.Raw_Orders`

### 2. Transformation – Completed

- Built an SSIS Data Flow pipeline to process the raw data.
- Applied data cleaning and standardization.
- Handled data quality issues and duplicate records.
- Performed data conversions and calculated required values.
- Loaded the transformed data into the staging table.

**Destination:**
- Database: `ShopEaseDB`
- Table: `dbo.stg_ShopEase_Orders`

The original raw data remains available in `dbo.Raw_Orders`.

---

## Project Structure

```text
ShopEase-BI/
│
├── Dataset/
│   └── shopease_raw_orders.csv
│
├── SSIS/
│   └── ShopEase_ETL/
│       └── ShopEase_ETL/
│           ├── ShopEase_ETL.sln
│           └── ShopEase_ETL/
│               ├── Package.dtsx
│               ├── ShopEase_Extraction.dtsx
│               ├── ShopEase_TransformAndLoad.dtsx
│               ├── Project.params
│               ├── ShopEase_CSV_Connection.conmgr
│               ├── localhost.ShopEaseDB.conmgr
│               └── ShopEase_ETL.dtproj
│
├── .gitignore
└── README.md
```

---

## Technologies Used

- SQL Server 2022
- SQL Server Management Studio (SSMS)
- SQL Server Integration Services (SSIS)
- Visual Studio
- Git & GitHub

---

## How to Get Started

### 1. Clone the Repository

Open Command Prompt or Git Bash and run:

```bash
git clone https://github.com/samasherif-22/ShopEase-BI.git
```

Or download the repository as a ZIP file from GitHub.

### 2. Install the Required Tools

Make sure you have:

- SQL Server (with a database instance available).
- SQL Server Management Studio (SSMS).
- Visual Studio with the **SQL Server Integration Services Projects** extension installed.

### 3. Open the SSIS Solution

1. Open the downloaded project folder.
2. Navigate to:

```text
SSIS/ShopEase_ETL/ShopEase_ETL/
```

3. Open `ShopEase_ETL.sln` using Visual Studio.
4. Wait for the SSIS project to load.

### 4. Configure Your Local Environment

The project uses connection managers and project parameters.

Before running the packages, update the values in `Project.params` according to your local setup:

| Parameter | Description | Example |
|---|---|---|
| `ServerName` | Your SQL Server instance name | `localhost` or `.\SQLEXPRESS` |
| `DatabaseName` | Target database name | `ShopEaseDB` |
| `CsvFilePath` | Full path to the source CSV file | Your local CSV path |

**Important:**
- Make sure the `ShopEaseDB` database exists on your SQL Server instance.
- Make sure the required raw and staging tables are available.
- Each team member must configure these parameters according to their own machine.
- The project uses Windows Authentication, so make sure your Windows account has the required SQL Server permissions.

### 5. Run the ETL Packages

Run the packages in the following order:

1. `ShopEase_Extraction.dtsx` – Loads the source CSV data into `dbo.Raw_Orders`.
2. `ShopEase_TransformAndLoad.dtsx` – Transforms the raw data and loads the results into `dbo.stg_ShopEase_Orders`.

You can execute the packages directly from Visual Studio.

### 6. Verify the Results

Open SSMS, connect to your SQL Server instance, and execute:

```sql
USE ShopEaseDB;

SELECT COUNT(*) AS RawRows
FROM dbo.Raw_Orders;

SELECT COUNT(*) AS TransformedRows
FROM dbo.stg_ShopEase_Orders;
```

---

## Team Workflow

The project is maintained using GitHub.

Team members should clone the repository, configure their local connection parameters, and continue working from the shared SSIS solution.

**Note:** Do not commit local machine-specific connection settings or temporary Visual Studio build files.

---

*Turning Raw Data into Business Insights.*
