
--1.Previe first row
SELECT * FROM superstore
LIMIT 10;

--2.Total Rows Count
SELECT COUNT(*) FROM superstore;

--3.Distinct catergories
SELECT DISTINCT Category
FROM superstore;

--4.Total sales by catergory
SELECT 
    Category,
    SUM(Sales) AS Total_Sales
FROM superstore
GROUP BY Category
ORDER BY Total_Sales DESC;

--5.Total sales in 2014(fixed date format)
SELECT 
    Category,
    SUM(Sales) AS Total_Sales_2014
FROM superstore
WHERE "Order Date" LIKE '%2014'
GROUP BY Category
ORDER BY Total_Sales_2014 DESC;

--6.Top 10 customers by spend
SELECT 
    "Customer Name",
    SUM(Sales) AS Total_Spent
FROM superstore
GROUP BY "Customer Name"
ORDER BY Total_Spent DESC
LIMIT 10;

--7.Top 10 products by sales
SELECT 
    "Product Name",
    SUM(Sales) AS Total_Sales
FROM superstore
GROUP BY "Product Name"
ORDER BY Total_Sales DESC
LIMIT 10;

--8.Profit by region
SELECT 
    Region,
    SUM(Profit) AS Total_Profit
FROM superstore
GROUP BY Region
ORDER BY Total_Profit DESC;

--9.Monthly sales trend(corrected)
SELECT
    substr("Order Date", 1, 2) AS Month_Number,
    substr("Order Date", 7, 4) AS Year,
    SUM(Sales) AS Total_Sales
FROM superstore
GROUP BY Year, Month_Number
ORDER BY Year, Month_Number;

--10.Top 5 profitable subcatergories
SELECT
    "Sub-Category",
    SUM(Profit) AS Total_Profit
FROM superstore
GROUP BY "Sub-Category"
ORDER BY Total_Profit DESC
LIMIT 5;







