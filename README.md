# Section B - G13 - RetailX Project README.md

> **Newton School of Technology | Data Visualization & Analytics**
> A 2-week industry simulation capstone using Python, GitHub, and Tableau to convert raw data into actionable business intelligence.

---

### Quick Start

To set up the environment and reproduce the analysis locally:

1. **Environment Setup**:
   ```bash
   # Create and activate virtual environment
   python -m venv .venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate

   # Install dependencies
   pip install -r requirements.txt
   ```

2. **Run ETL Pipeline** (Optional):
   ```bash
   # Executes the automated cleaning and transformation script
   python scripts/etl_pipeline.py
   ```

3. **Launch Analysis**:
   ```bash
   # Open Jupyter to explore the step-by-step notebooks
   jupyter notebook
   ```

---

## Project Overview

| Field | Details |
|---|---|
| **Project Title** | RetailX: Retail Store Sales Analytics |
| **Sector** | Retail |
| **Team ID** | SectionB-G13-RetailX |
| **Section** | B |
| **Faculty Mentor** | Satyaki Das |
| **Institute** | Newton School of Technology |
| **Submission Date** | April 29, 2026 |

### Team Members

| Role | Name | GitHub Username |
|---|---|---|
| Project Lead | Avneet Singh | `avneets0419` |
| Data Lead | Shreshth Gupta | `shresth2708` |
| ETL Lead | Abhigya Sachdeva | `ABHIGYA0205` |
| Analysis Lead | Riya Yadav | `riya11108` |
| Visualization Lead | Avneet SIngh | `avneets0419` |
| Strategy Lead | Kushal Tyagi | `WhiteHacker000` |
| PPT and Quality Lead | Amogha Raj Sandur | `amogharajsandur` |

---

## Business Problem

The retail sector is a highly competitive industry characterized by thin profit margins, diverse product categories, and fluctuating customer demand. Small to mid-sized retail chains often struggle to optimize inventory levels, personalize marketing efforts, and respond effectively to market trends. Without data-driven insights, these businesses risk overstocking unpopular items, missing out on high-demand periods, and failing to build customer loyalty. This project addresses these challenges by providing actionable analytics that enable data-informed decision-making.

The primary decision-maker for this analysis is the Retail Operations Manager responsible for inventory planning, sales strategy, and customer engagement. By leveraging Python for data processing and Tableau for visualization, the project delivers a clear, interactive view of sales performance, product trends, and customer behavior.

The core business challenge is to transform raw transaction data into actionable insights that improve profitability and operational efficiency. The analysis focuses on identifying key sales drivers, understanding temporal purchasing patterns, and evaluating the impact of discounts. These insights help retailers optimize stock levels, enhance marketing strategies, and ultimately drive revenue growth in a competitive market.


**Core Business Question**

> How can we optimize revenue and customer retention by identifying high-performing product categories, seasonal sales trends, and the impact of promotional discounts on customer purchasing behavior?

**Decision Supported**

> This analysis enables the Operations Manager to allocate inventory budgets more effectively toward high-demand categories, design data-backed promotional campaigns that maximize ROI, and implement targeted retention strategies for "at-risk" high-value customer segments identified through RFM analysis.

---

## Dataset

| Attribute | Details |
|---|---|
| **Source Name** | Simulated Retail Operations Dataset |
| **Direct Access Link** | [Internal Repository Data Folder](data/raw/retail_store_sales.csv) |
| **Row Count** | 12,575 |
| **Column Count** | 11 |
| **Time Period Covered** | January 2022 to August 2024 |
| **Format** | CSV |

**Key Columns Used**

| column_1 | Description | Role in Analysis |
|---|---|---|
| **transaction_id** | Unique identifier for each transaction | Primary key for transaction-level analysis |
| **customer_id** | Unique identifier for each customer | Used for customer segmentation and retention analysis |
| **item** | Name of the product purchased | Enables product-level performance tracking |
| **category** | Product category (Dairy, Patisserie, etc.) | Used for performance segmentation and dashboard filtering |
| **price_per_unit** | Price of a single unit of item | Used for calculating total_spent when missing |
| **quantity** | Number of units purchased | Used for calculating total_spent when missing |
| **total_spent** | Total amount spent in transaction | Primary KPI for revenue and growth analysis |
| **discount_applied** | Boolean flag for promotional discount | Used for hypothesis testing on price sensitivity |
| **transaction_date** | Date of the purchase | Enables temporal trend and seasonality analysis |
| **month** | Month of the transaction | Extracted from transaction_date for trend analysis |
| **day** | Day of the week | Extracted from transaction_date for pattern analysis |
| **year** | Year of the transaction | Extracted from transaction_date for trend analysis |

For full column definitions, see [`docs/data_dictionary.md`](docs/data_dictionary.md).

---

## KPI Framework

| KPI | Definition | Formula / Computation |
|---|---|---|
| **Total Revenue** | Total revenue generated from all sales | Sum of all `total_spent` values across all transactions | Notebook 02, 05 |
| **Average Order Value (AOV)** | Average amount spent per transaction | `Total Revenue / Total Number of Transactions` | Notebook 02, 05 |
| **Transaction Count** | Total number of sales transactions | Count of unique `transaction_id` values | Notebook 02 |
| **Active Customers** | Number of unique customers who made purchases | Count of unique `customer_id` values with purchases | Notebook 02 |
| **Discount Effectiveness** | Percentage of transactions with discounts | `(Count of discounted transactions / Total transactions) * 100` | Notebook 04 |
| **Category Performance** | Revenue contribution by product category | Sum of `total_spent` grouped by `category` | Notebook 03 |
| **Seasonal Index** | Monthly deviation from average sales | Monthly revenue divided by average monthly revenue for the year | Notebook 03 |
| **Day-of-Week Performance** | Revenue by day of the week | Sum of `total_spent` grouped by `day` | Notebook 03 |
| **Repeat Purchase Rate** | Percentage of customers making multiple purchases | `(Number of repeat customers / Total active customers) * 100` | Notebook 04 |
| **Customer Value Segmentation** | Distribution of customers into RFM segments | RFM analysis scoring to identify high, medium, and low-value customers | Notebook 04 |

Document KPI logic clearly in `notebooks/04_statistical_analysis.ipynb` and `notebooks/05_final_load_prep.ipynb`.

---

## Tableau Dashboard

| Item | Details |
|---|---|
| **Dashboard URL** | [View Tableau Dashboard](https://public.tableau.com/app/profile/avneet.singh2247/viz/DVA_EndTerm_Capstone/Dashboard1) |
| **Executive View** | Summary of business performance, tracking Total Revenue, AOV, and Transaction counts with trend analysis. |
| **Operational View** | Detailed breakdown of Category-wise performance, Location-based sales distribution, and Customer segmentation insights. |
| **Main Filters** | Product Category (Dropdown), Year of Transaction (Dropdown), Store Location (Online vs. In-store). |

Store dashboard screenshots in [`tableau/screenshots/`](tableau/screenshots/) and document the public links in [`tableau/dashboard_links.md`](tableau/dashboard_links.md).

---

## Key Insights

1. **Mitigate Hyper-Concentrated Customer Risk**: The business relies on a remarkably small base of just 25 repeat customers for over 12,000 transactions. Losing even 2-3 top-tier clients (e.g., CUST_24 or CUST_08) could jeopardize nearly 10% of total revenue.
2. **Optimize Balanced Product Portfolio**: Sales are exceptionally well-distributed, with all 8 categories contributing 11-13% each. This low-risk portfolio allows the business to focus on increasing Average Order Value (AOV) rather than category expansion.
3. **Re-evaluate Margin-Eroding Discounts**: While 33.5% of transactions are discounted, statistical tests (p ≈ 0.47) confirm these discounts do not significantly increase the total amount spent per transaction. Promotions should be shifted toward cross-selling higher-margin items.
4. **Capitalize on Volume-Driven Growth**: The business operates on a high-volume, low-price model (Avg. Unit Price: ₹23.37). Profitability strategy should prioritize inventory turnover and supply chain efficiency over aggressive price hikes.
5. **Standardize Omnichannel Experience**: Revenue is split roughly 50/50 between Online and In-store channels. To protect this parity, the business must ensure real-time inventory synchronization to prevent "out-of-stock" friction on the digital platform.
6. **Protect Payment Method Diversity**: Usage is nearly identical across Cash (34%), Digital Wallets (33%), and Credit Cards (33%). Eliminating any single payment gateway would likely alienate a third of the customer base instantly.
7. **Synchronize Staffing with Weekly Peaks**: Sales consistently peak on Fridays and Sundays. Operational schedules should be adjusted to ensure maximum floor coverage and replenishment on these high-traffic days to maximize conversion.
8. **Institutionalize HNI Retention**: The Top 5 customers generate nearly 20% of total revenue. A formal "Platinum Loyalty" program is required to lock in these high-value individuals and defend the core revenue stream against competitors.
9. **Prepare for Q4 Seasonal Volatility**: Data shows significant sales spikes in November and December. Procurement and marketing budgets should be heavily weighted toward Q4 to capitalize on the 60-day window that drives the majority of annual growth.
10. **Enhance Category-Specific Financing**: High-ticket categories like 'Electric' show a natural affinity for Credit Card payments. Introducing zero-cost EMI or digital financing could further increase volume in this specific segment.

---

## Recommendations

| # | Insight | Recommendation | Expected Impact |
|---|---|---|---|
| 1 | **Customer Dependency (1 & 8)** | Launch an invitation-only "RetailX Platinum" loyalty program for the top 25 high-frequency customers, featuring exclusive pre-sales and personalized account management. | Secure the top 20% of total revenue against attrition and increase HNI retention by 15%. |
| 2 | **Discount Ineffectiveness (3)** | Replace flat discount rates with "Bundle & Save" promotions or "Spend Over ₹200" triggers to incentivize higher basket totals. | Increase Average Order Value (AOV) by 10-15% while reducing margin leakage from ineffective promos. |
| 3 | **Weekly Peaks (7)** | Reallocate 20% of weekly labor and inventory restocking budgets to "Peak Prep" on Thursdays and Saturdays. | Reduce "Out of Stock" occurrences during weekend rushes and improve peak conversion rates by 5-8%. |
| 4 | **Financing Opportunity (10)** | Partner with credit/wallet providers to offer 0% Interest EMI or "Buy Now Pay Later" specifically for high-ticket categories (Electric, Furniture, Computers). | Drive a 20% volume increase in high-ticket segments by reducing payment friction at checkout. |
| 5 | **Omnichannel Parity (5)** | Deploy a centralized real-time inventory management system to sync Online and In-store stock levels every 15 minutes. | Minimize online order cancellations and improve overall sales volume by 3-5% through optimized stock visibility. |

---

## Repository Structure

```text
SectionB-G13-RetailX/
├── README.md
├── requirements.txt
├── data/
│   ├── raw/
│   │   └── retail_store_sales.csv
│   └── processed/
│       ├── clean_retail_data.csv
│       └── final_ready_data.csv
├── notebooks/
│   ├── 01_extraction.ipynb
│   ├── 02_cleaning.ipynb
│   ├── 03_eda.ipynb
│   ├── 04_statistical_analysis.ipynb
│   └── 05_final_load_prep.ipynb
├── scripts/
│   ├── __init__.py
│   └── etl_pipeline.py
├── tableau/
│   ├── dashboard_links.md
│   └── screenshots/
│       ├── 1_dashboard_overview.jpeg
│       ├── 2_dashboard_overview.jpeg
│       └── 3_dashboard_overview.jpeg
├── reports/
│   ├── README.md
│   ├── project_report_template.md
│   └── presentation_outline.md
├── docs/
│   └── data_dictionary.md
├── DVA-oriented-Resume/
│   └── README.md
└── DVA-focused-Portfolio/
    └── README.md
```

---

## Analytical Pipeline

The project follows a structured 7-step workflow:

1. **Define** - Scoped the Retail sector, focusing on Sales and Revenue optimization for the Retail Operations Manager.
2. **Extract** - Sourced the `retail_store_sales.csv` dataset, documenting 12,575 transactions spanning 2022-2024.
3. **Clean and Transform** - Developed a Python-based ETL pipeline (`02_cleaning.ipynb`) to standardize column names, handle null values, and engineer time-based features.
4. **Analyze** - Conducted EDA to identify spending distributions and performed statistical testing (ANOVA/T-tests) in notebooks `03` and `04` to validate category performance.
5. **Visualize** - Designed an omnichannel Retail Dashboard on Tableau Public, featuring Executive KPIs and granular customer segmentation filters.
6. **Recommend** - Formulated 5 actionable strategies to mitigate customer dependency risks and optimize discount-driven revenue.
7. **Report** - Consolidated findings into a professional project report and executive presentation deck for final stakeholder delivery.

---

## Tech Stack

| Tool | Role | Purpose |
|---|---|---|
| **Python 3.x** | Core | Primary engine for ETL, cleaning, and KPI computation |
| **Jupyter Notebooks** | Analysis | Documentation of EDA and statistical hypothesis testing |
| **Tableau Public** | Visualization | Hosting the interactive Executive & Operational dashboards |
| **GitHub** | Collaboration | Version control and audit-trail for project contributions |
| **Pandas / NumPy** | Data Wrangling | High-performance manipulation of the 12,575-row dataset |
| **Seaborn / Matplotlib** | Plotting | Generating distribution, correlation, and trend charts |
| **Scipy / Statsmodels** | Statistics | Powering ANOVA and T-tests for business decision-making |

---

## Submission Checklist

**GitHub Repository**

- [x] Public repository created with the correct naming convention (`SectionName_TeamID_ProjectName`)
- [x] All notebooks committed in `.ipynb` format
- [x] `data/raw/` contains the original, unedited dataset
- [x] `data/processed/` contains the cleaned pipeline output
- [x] `tableau/screenshots/` contains dashboard screenshots
- [x] `tableau/dashboard_links.md` contains the Tableau Public URL
- [x] `docs/data_dictionary.md` is complete
- [x] `README.md` explains the project, dataset, and team
- [x] All members have visible commits and pull requests

**Tableau Dashboard**

- [x] Published on Tableau Public and accessible via public URL
- [x] At least one interactive filter included
- [x] Dashboard directly addresses the business problem

**Project Report**

- [x] Final report exported as PDF into `reports/`
- [x] Cover page, executive summary, sector context, problem statement
- [x] Data description, cleaning methodology, KPI framework
- [x] EDA with written insights, statistical analysis results
- [x] Dashboard screenshots and explanation
- [x] 8-12 key insights in decision language
- [x] 3-5 actionable recommendations with impact estimates
- [x] Contribution matrix matches GitHub history

**Presentation Deck**

- [x] Final presentation exported as PDF into `reports/`
- [x] Title slide through recommendations, impact, limitations, and next steps

**Individual Assets**

- [x] DVA-oriented resume updated to include this capstone
- [x] Portfolio link or project case study added

---

## Contribution Matrix

This table must match evidence in GitHub Insights, PR history, and committed files.

| Team Member | Dataset and Sourcing | ETL and Cleaning | EDA and Analysis | Statistical Analysis | Tableau Dashboard | Report Writing | PPT and Viva |
|---|---|---|---|---|---|---|---|
| Avneet Singh | **Owner** | Support | Support | Support | **Owner** | Support | Support |
| Shreshth Gupta | Support | Support | Support | **Owner** | Support | Support | Support |
| Abhigya Sachdeva | Support | **Owner** | **Owner** | Support | Support | Support | Support |
| Riya Yadav | Support | Support | Support | Support | **Owner** | Support | Support |
| Kushal Tyagi | Support | Support | Support | Support | Support | Support | **Owner** |
| Amogha Raj Sandur | Support | Support | Support | Support | Support | **Owner** | Support |

_Declaration: We confirm that the above contribution details are accurate and verifiable through GitHub Insights, PR history, and submitted artifacts._

**Team Lead Name:** Avneet Singh

**Date:** 29 April 2026

---

## Academic Integrity

All analysis, code, and recommendations in this repository must be the original work of the team listed above. Free-riding is tracked via GitHub Insights and pull request history. Any mismatch between the contribution matrix and actual commit history may result in individual grade adjustments.

---

*Newton School of Technology - Data Visualization & Analytics | Capstone 2*
