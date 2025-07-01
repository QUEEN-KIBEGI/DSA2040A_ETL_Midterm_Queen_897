# DSA2040A ETL Midterm Project - Queen_897

## Project Overview
This project implements an ETL pipeline for sales data as part of the DSA 2040 A US 2025 Mid Semester Exam. It processes `raw_data.csv` (100 rows) and `incremental_data.csv` (10 rows), applies transformations, and loads the results into SQLite databases.

## ETL Phases
1. **Extract (`etl_extract.ipynb`)**
   - Loads and inspects `raw_data.csv` and `incremental_data.csv`.
   - Converts quantity and unit_price to numeric.
   - Displays `.head()` and `.info()`.
   - Notes missing values, duplicates (order_id=4), and string order_date.
   - Saves raw data to `data/` folder.

2. **Transform (`etl_transform.ipynb`)**
   - Applies 4 transformations:
     - Fills missing customer_name and region with 'Unknown', quantity with median, unit_price with mean, order_date with 'Unknown'.
     - Removes duplicate row (order_id=4 in raw_data).
     - Adds total_price column (quantity * unit_price).
     - Converts order_date to datetime (invalid dates become NaT).
   - Includes bonus visualization: bar chart of total sales by product.
   - Saves results to `data/transformed/transformed_full.csv` and `transformed_incremental.csv`.

3. **Load (`etl_load.ipynb`)**
   - Loads transformed data into SQLite databases (`full_data.db`, `incremental_data.db`).
   - Verifies with SQL queries (`SELECT * FROM <table> LIMIT 5`).

## Tools Used
- Python
- Pandas
- SQLite (via `sqlite3`)
- Matplotlib (for visualization)
- Jupyter Notebooks

## How to Run
1. Clone the repository: `git clone <your-repo-url>`
2. Install required libraries: `pip install pandas sqlite3 matplotlib`
3. Run notebooks in order:
   - `etl_extract.ipynb`
   - `etl_transform.ipynb`
   - `etl_load.ipynb`
4. Check outputs in `data/transformed/` and `loaded/` folders.

## Screenshot
![image](https://github.com/user-attachments/assets/d1c8381d-2366-47c7-90f5-9b4381e8e8c4)
