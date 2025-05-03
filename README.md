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

### Results
## 1. Monthly Revenue and Order Volume


   ![Screenshot 2025-05-04 004425](https://github.com/user-attachments/assets/3fb73c52-a213-4635-aab6-1d2c569e7d9e)

## 2. Top 3 Months by Revenue

   ![Screenshot 2025-05-04 004538](https://github.com/user-attachments/assets/d5403e3a-39c9-4bfb-a0dd-bc339147eec2)

## 3. Average Order Value by Month


   ![Screenshot 2025-05-04 004608](https://github.com/user-attachments/assets/68305abf-8f40-4ac0-bed8-c0a6d3b72a1a)

## 4. Product Performance by Month


   ![Screenshot 2025-05-04 004651](https://github.com/user-attachments/assets/023a8b08-66ae-4ef1-8f6f-6ae2eec97f3e)


## Objective Achieved
Successfully implemented SQL queries that analyze monthly revenue and order volume using:

- EXTRACT() function to get month and year from dates
- GROUP BY for aggregating data by time periods
- SUM() for calculating total revenue
- COUNT(DISTINCT) for determining order volume
- Advanced sorting and filtering techniques


### Key Insights
1. March and June had the highest revenue ($1,749.96) and highest order volume (4 orders)
2. January had the lowest revenue ($649.48)
3. The overall trend shows increasing revenue in Q1, a slight dip in April-May, and a strong recovery in June

## How to Run
1. Create a database in your preferred SQL environment (PostgreSQL/MySQL/SQLite)
2. Run the create_table.sql script to set up the database schema and sample data
3. Execute the queries in analysis.sql to perform the sales trend analysis

## 📧 Contact

Feel free to reach out with any questions or suggestions for improvement!

- LinkedIn: [saurabhhupadhyay](https://linkedin.com/in/saurabhhupadhyay)
- Email: saurabhu.2004@gmail.com

This project demonstrates SQL-based sales trend analysis using aggregation functions. All queries are written and executed using SQL and stored in analysis.sql and create_table.sql.
