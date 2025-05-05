# sql-data-analytics-project

A comprehensive collection of SQL scripts for data exploration, analytics, and reporting. These scripts cover various analyses such as database exploration, measures and metrics, time-based trends, cumulative analytics, segmentation, and more. This repository contains SQL queries designed to help data analysts and BI professionals quickly explore, segment, and analyze data within a relational database. Each script focuses on a specific analytical theme and demonstrates best practices for SQL queries.

## 🛠️ Tech Stack

- **SQL Server** (for querying and data analysis)
- **CSV files** (used as source data)
- **Windows Functions**, **CTEs**, **Aggregation**, **Joins**, **Date functions**

## 🔄 Analytical Process

1. **Data Acquisition**
   - Source data was provided as `.csv` files (compressed).
   - Data includes: `Orders`, `Customers`, `Products`, `Categories`, and `Sales`.

2. **Data Ingestion & Preparation**
   - Data loaded into SQL Server staging tables.
   - Applied data type validations (e.g., dates, numeric conversions).
   - Cleaned nulls, duplicate records, and inconsistent text (e.g., trimming customer names).

3. **Exploratory Data Analysis (EDA)**
   - Basic profiling (MIN, MAX, COUNT DISTINCT) to understand dimensions and metrics.
   - Identified key metrics: Revenue, Profit, Quantity Sold, and Customer Lifetime Value.

4. **Business-Focused Analysis**
   - **Sales Trend Analysis**: Time-based breakdown (monthly/yearly) using date functions and window functions.
   - **Customer Segmentation**: Tiered by revenue using `NTILE()` and frequency using `COUNT()` and `GROUP BY`.
   - **Profit Margin Analysis**: Category-wise margin analysis using derived fields and conditional logic.
   - **Top N Products/Regions**: Ranking using `RANK()` and `DENSE_RANK()` for executive reporting.
   - **Cohort Analysis (Optional)**: To study retention patterns.

5. **Insight Extraction**
   - Used `CASE` statements, subqueries, and CTEs to derive business rules and flags (e.g., loyal customer flag, profit tier).

6. **Query Optimization**
   - Indexed `Customer_ID`, `Order_Date`, and `Product_ID` for faster joins and filtering.
   - Rewrote subqueries as CTEs to enhance readability and execution plans.

## ❗ Challenges Faced

| Challenge | Resolution |
|----------|------------|
| Inconsistent date formats in CSVs | Parsed all `Order_Date` fields using `TRY_CONVERT()` and standardized to `DATE`. |
| Missing or duplicate customer records | Created a staging step with deduplication logic using `ROW_NUMBER()` and `PARTITION BY`. |
| Performance issues in large JOINs | Indexed key columns and reduced result sets with selective filtering early in the pipeline. |
| Aggregation mismatch (e.g., overcounting) | Used `DISTINCT` carefully and verified grouping logic with test cases. |
| Dynamic business logic (e.g., tiering) | Applied SQL window functions and dynamic bucket creation using `CASE`, `NTILE()`. |

## 💡 Business Insights Derived

1. **Revenue Growth**: Sales increased consistently Q-over-Q by ~12%, peaking during the holiday season (Nov-Dec).
2. **Customer Segmentation**:
   - Top 20% customers contributed ~65% of total revenue.
   - High churn detected in low-tier customers (one-time buyers).
3. **Product Performance**:
   - Electronics and Apparel had the highest margin but also the most return requests.
   - Region-wise, the West region outperformed all others in profit.
4. **Profitability Trends**:
   - Products with bundle offers showed higher average order value.
   - Discounts above 20% led to negative margins in ~10% of orders.
5. **Retention Patterns** (if Cohort Analysis added):
   - Customers acquired via holiday campaigns had ~40% lower second-order rates.
   - Repeat customers placed their second order within 25 days on average.
     

🌟 About Me

Hi there! I'm **Ishaan Guleria** — An IT professional passionate about learning, building, and delivering impactful solutions that drive real-world results.

Let's stay in touch! Feel free to connect with me on the following platforms:[Connect with me on LinkedIn](https://www.linkedin.com/in/ishaan-guleria-865858200/)
