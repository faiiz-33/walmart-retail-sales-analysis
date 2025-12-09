-- Create database
CREATE DATABASE walmart;
USE walmart;

-- Create tables
CREATE TABLE stores (
    Store INT PRIMARY KEY,
    Type CHAR(1),
    Size INT
);

CREATE TABLE features (
    Store INT,
    Date DATE,
    Temperature FLOAT,
    Fuel_Price FLOAT,
    MarkDown1 FLOAT,
    MarkDown2 FLOAT,
    MarkDown3 FLOAT,
    MarkDown4 FLOAT,
    MarkDown5 FLOAT,
    CPI FLOAT,
    Unemployment FLOAT,
    IsHoliday BOOLEAN
);

CREATE TABLE sales (
    Store INT,
    Dept INT,
    Date DATE,
    Weekly_Sales FLOAT,
    IsHoliday BOOLEAN
);

-- Import your CSV data into each table
-- ------------------------------------

-- Check table row counts
SELECT COUNT(*) FROM stores;
SELECT COUNT(*) FROM features;
SELECT COUNT(*) FROM sales;

-- Identify missing values in key columns
SELECT * FROM features
WHERE Temperature IS NULL
   OR CPI IS NULL
   OR Unemployment IS NULL;

-- Handle missing values (example: replace NULL Size with mean)
UPDATE stores
SET Size = (SELECT AVG(Size) FROM stores)
WHERE Size IS NULL;


-- EDA: distinct values
SELECT COUNT(DISTINCT Store) FROM sales;
SELECT COUNT(DISTINCT Dept) FROM sales;
SELECT COUNT(*) FROM sales;

-- Averages
SELECT AVG(Weekly_Sales) FROM sales;
SELECT AVG(Size) FROM stores;

-- Top 10 selling stores
SELECT Store, SUM(Weekly_Sales) AS total_sales, AVG(Weekly_Sales) AS avg_sales
FROM sales
GROUP BY Store
ORDER BY total_sales DESC
LIMIT 10;

-- Top 10 selling departments
SELECT Dept, SUM(Weekly_Sales) AS dept_sales
FROM sales
GROUP BY Dept
ORDER BY dept_sales DESC
LIMIT 10;

-- Sales over time
SELECT YEAR(Date) AS year, SUM(Weekly_Sales)
FROM sales
GROUP BY YEAR(Date)
ORDER BY year;

SELECT MONTH(Date) AS month, SUM(Weekly_Sales)
FROM sales
GROUP BY MONTH(Date)
ORDER BY month;

-- Week-over-week growth
SELECT
    Store,
    Date,
    Weekly_Sales,
    Weekly_Sales - LAG(Weekly_Sales) OVER (PARTITION BY Store ORDER BY Date) AS wow_growth
FROM sales;

-- Effect of store type on sales
SELECT s.Store, st.Type, st.Size, SUM(s.Weekly_Sales) AS total_sales
FROM sales s
JOIN stores st ON s.Store = st.Store
GROUP BY s.Store, st.Type, st.Size
ORDER BY total_sales DESC;

-- Effect of temperature on sales
SELECT f.Temperature, AVG(s.Weekly_Sales)
FROM sales s
JOIN features f USING (Store, Date)
GROUP BY f.Temperature
ORDER BY f.Temperature;

-- Effect of fuel price on sales
SELECT f.Fuel_Price, AVG(s.Weekly_Sales)
FROM sales s
JOIN features f USING (Store, Date)
GROUP BY f.Fuel_Price
ORDER BY f.Fuel_Price;

-- Holiday vs Non-Holiday sales
SELECT IsHoliday, AVG(Weekly_Sales)
FROM sales
GROUP BY IsHoliday;

-- Holiday sales percentage growth
WITH a AS (
    SELECT 
        AVG(CASE WHEN IsHoliday = 0 THEN Weekly_Sales END) AS non_holiday_avg,
        AVG(CASE WHEN IsHoliday = 1 THEN Weekly_Sales END) AS holiday_avg
    FROM sales
)
SELECT
    holiday_avg,
    non_holiday_avg,
    ((holiday_avg - non_holiday_avg) / non_holiday_avg) * 100 AS holiday_growth_percentage
FROM a;
