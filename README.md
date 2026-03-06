# Online-Retail-Sales-Analysis-SQL

## Project Overview
This project analyzes an online retail transaction dataset using SQL to uncover sales performance, customer behavior, and product trends. The analysis includes data cleaning, feature engineering, and exploratory data analysis to generate business insights.

## Dataset
The dataset contains online retail transactions including information about products, invoices, customers, and countries.

Key columns include:

- InvoiceNo
- StockCode
- Description
- Quantity
- InvoiceDate
- UnitPrice
- CustomerID
- Country

## Tools Used

- SQL
- MySQL
- Data Cleaning
- Exploratory Data Analysis

## Data Cleaning

Several data preparation steps were performed before analysis:

- Created a copy of the original dataset for safe transformations
- Checked for duplicate records using `ROW_NUMBER()`
- Converted `InvoiceDate` from text to datetime format
- Converted `UnitPrice` to decimal data type
- Checked for missing values across columns

## Feature Engineering

New analytical features were created to support business analysis:

- `revenue` = Quantity × UnitPrice
- `is_return` flag for returned items
- `invoice_month` for monthly sales analysis
- `is_churned` indicator for customer churn detection

## Exploratory Data Analysis

Key analysis performed:

### Sales Performance
- Total revenue generated from transactions
- Top performing products by revenue
- Monthly sales trends

### Product Analysis
- Top selling products
- Product return rates
- Products with highest returned units

### Customer Analysis
- One-time vs repeat customers
- Top customers by revenue
- Customer purchase behavior

### Geographic Analysis
- Revenue distribution by country

### Customer Churn Analysis
- Identified customers who have not purchased for 90 days
- Flagged churned customers based on last purchase date

## Example Query

```sql
SELECT StockCode, SUM(revenue) AS total_revenue
FROM retail_datasets
WHERE Quantity > 0
GROUP BY StockCode
ORDER BY total_revenue DESC
LIMIT 10;
