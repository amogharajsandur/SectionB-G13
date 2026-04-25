###This data dictionary documents all fields, transformations, and assumptions applied during data cleaning to ensure transparency and reproducibility of analysis.


## Dataset Summary

| Item          | Details                           |
| ------------- | --------------------------------- |
| Dataset name  | Retail Store Sales Dataset        |
| Source        | Provided for DVA Capstone Project |
| Raw file name | retail_store_sales.csv            |
| Last updated  | April 2026                        |
| Granularity   | One row per transaction           |


## Column Definitions

| Column Name      | Data Type | Description                            | Example Value | Used In                 | Cleaning Notes                                       |
| ---------------- | --------- | -------------------------------------- | ------------- | ----------------------- | ---------------------------------------------------- |
| transaction_id   | string    | Unique identifier for each transaction | T12345        | EDA / KPI               | Checked for duplicates and removed duplicate rows    |
| customer_id      | string    | Unique identifier for each customer    | C102          | KPI / Segmentation      | Used for customer-level aggregation                  |
| item             | string    | Name of product purchased              | Milk          | EDA / KPI               | Missing values filled with "Unknown_Item"            |
| category         | string    | Product category                       | Dairy         | EDA / KPI / Tableau     | Standardized text formatting                         |
| price_per_unit   | float     | Price of a single unit of item         | 50.0          | EDA / Statistical       | Missing values computed using total_spent ÷ quantity |
| quantity         | int       | Number of units purchased              | 2             | EDA / KPI               | Missing values derived or defaulted to 1             |
| total_spent      | float     | Total amount spent in transaction      | 100.0         | KPI / EDA / Statistical | Calculated as price × quantity where missing         |
| discount_applied | boolean   | Whether discount was applied           | True          | Statistical             | Missing values filled with False                     |
| transaction_date | date      | Date of transaction                    | 2023-05-12    | EDA / KPI               | Converted to datetime format                         |
| month            | int       | Month of transaction                   | 5             | EDA / KPI               | Extracted from transaction_date                      |
| day              | string    | Day of the week                        | Monday        | EDA                     | Derived from transaction_date                        |
| year             | int       | Year of transaction                    | 2023          | EDA                     | Derived from transaction_date                        |


## Derived Columns

| Derived Column | Logic                           | Business Meaning                                   |
| -------------- | ------------------------------- | -------------------------------------------------- |
| total_spent    | price_per_unit × quantity       | Represents total revenue generated per transaction |
| month          | Extracted from transaction_date | Used to analyze seasonal trends                    |
| day            | Extracted from transaction_date | Helps identify weekday vs weekend patterns         |
| year           | Extracted from transaction_date | Enables yearly trend analysis                      |


## Data Quality Notes

Missing values were present in price, quantity, and total_spent, handled using logical relationships
Assumptions made:
If only price exists → quantity = 1
If only total exists → quantity = 1
Duplicate records were removed
Outliers detected using IQR method (not removed, only analyzed)
Some product names were missing → replaced with "Unknown_Item"
Discount field had nulls → treated as False
Data may contain skewness due to high-value transactions