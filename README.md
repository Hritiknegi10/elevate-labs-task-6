# elevate-labs-task-6

Task 6 — Sales Trend Analysis Using Aggregations

Objective

Analyze monthly revenue and order volume using SQL aggregation functions.

Tool Used

PostgreSQL

Dataset

The project uses an online_sales table with:

Column

Meaning

order_id

Order identifier

order_date

Date on which the order was placed

amount

Revenue for a product line

product_id

Product identifier

An order may contain multiple product lines, so order_id can appear more than once.
That is why order volume is calculated with COUNT(DISTINCT order_id).

Dataset note: The task brief names the table/columns but does not include a source file.
This repository therefore contains a clearly labeled, reproducible synthetic sample dataset.
The SQL logic remains the same if an official dataset is provided later.

Main SQL Query

SELECT
    EXTRACT(YEAR FROM order_date)::INT AS year,
    EXTRACT(MONTH FROM order_date)::INT AS month,
    ROUND(SUM(amount), 2) AS monthly_revenue,
    COUNT(DISTINCT order_id) AS order_volume
FROM online_sales
GROUP BY
    EXTRACT(YEAR FROM order_date),
    EXTRACT(MONTH FROM order_date)
ORDER BY
    year,
    month;

SQL Concepts Used

EXTRACT(YEAR FROM order_date)

EXTRACT(MONTH FROM order_date)

SUM(amount)

COUNT(DISTINCT order_id)

GROUP BY

ORDER BY

WHERE

LIMIT

Files

How to Run

Open pgAdmin.

Create/open a PostgreSQL database.

Open Query Tool.

Open task6_sales_trend_analysis.sql.

Click Execute.

The script creates the table, inserts the sample data, and contains all required queries.

Run the MAIN DELIVERABLE query to get the monthly result table.

Run the Top 3 months query for the ranking.

No CSV import is required because the SQL file already contains the seed data.

Conclusion

The analysis groups sales by year and month and calculates:

total monthly revenue with SUM(amount);

unique monthly orders with COUNT(DISTINCT order_id).

This makes it easy to compare sales performance over time and identify the highest-revenue months.
