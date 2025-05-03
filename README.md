## Sales-Trend-Analysis-Using-Aggregations

## Objective
Analyze monthly revenue and order volume for an online sales database using SQL aggregation functions.

## Dataset
I created a sample dataset with the required structure:
- Table: orders
- Fields: order_id, order_date, product_id, amount
- 20 sample records spanning January to June 2023

## SQL Queries

### 1. Monthly Revenue and Order Volume Analysis
This query extracts the year and month from order dates, calculates total revenue using SUM(), and determines order volume using COUNT(DISTINCT order_id):

```sql
SELECT 
    EXTRACT(YEAR FROM order_date) AS year,
    EXTRACT(MONTH FROM order_date) AS month,
    SUM(amount) AS total_revenue,
    COUNT(DISTINCT order_id) AS order_volume
FROM 
    orders
GROUP BY 
    EXTRACT(YEAR FROM order_date),
    EXTRACT(MONTH FROM order_date)
ORDER BY 
    year ASC,
    month ASC;
```

### 2. Top 3 Months by Revenue
This query identifies the months with the highest revenue:

```sql
SELECT 
    EXTRACT(YEAR FROM order_date) AS year,
    EXTRACT(MONTH FROM order_date) AS month,
    SUM(amount) AS total_revenue,
    COUNT(DISTINCT order_id) AS order_volume
FROM 
    orders
GROUP BY 
    EXTRACT(YEAR FROM order_date),
    EXTRACT(MONTH FROM order_date)
ORDER BY 
    total_revenue DESC
LIMIT 3;
```

### 3. Average Order Value by Month
This query calculates average order value for each month:

```sql
SELECT 
    EXTRACT(YEAR FROM order_date) AS year,
    EXTRACT(MONTH FROM order_date) AS month,
    SUM(amount) AS total_revenue,
    COUNT(DISTINCT order_id) AS order_volume,
    ROUND(SUM(amount) / COUNT(DISTINCT order_id), 2) AS avg_order_value
FROM 
    orders
GROUP BY 
    EXTRACT(YEAR FROM order_date),
    EXTRACT(MONTH FROM order_date)
ORDER BY 
    year ASC,
    month ASC;
```

## Results

### Monthly Revenue and Order Volume
| year | month | total_revenue | order_volume |
|------|-------|--------------|-------------|
| 2023 | 1     | 649.48       | 3           |
| 2023 | 2     | 999.48       | 3           |
| 2023 | 3     | 1749.96      | 4           |
| 2023 | 4     | 1149.48      | 3           |
| 2023 | 5     | 999.48       | 3           |
| 2023 | 6     | 1749.96      | 4           |

### Key Insights
1. March and June had the highest revenue ($1,749.96) and highest order volume (4 orders)
2. January had the lowest revenue ($649.48)
3. The overall trend shows increasing revenue in Q1, a slight dip in April-May, and a strong recovery in June

## How to Run
1. Create a database in your preferred SQL environment (PostgreSQL/MySQL/SQLite)
2. Run the create_table.sql script to set up the database schema and sample data
3. Execute the queries in analysis.sql to perform the sales trend analysis
