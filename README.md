# LITA_CAPSTONE_PROJECT

### Project Title: Classy Hub Sales Analysis

### Project Overview
---
This Project aims to evaluate the sales performance of Classy Hub over the period. I would be analysing various parameters from the data with a view to identify trends, assess performance, and provide actionable insights to enhance revenue growth and optimize sales strategies.

### Data Sources
---
The primary Data used here is the SalesData provided by the Incubator Hub

### Tools Used
---
- Microsoft Excel for Data cleaning and analysis [download here](https://1drv.ms/x/c/3d767624932c4481/ERzDuN5kbpFDi2Wqln3uMh8BWO5GXEt1kxtKwOh4drFSsQ?e=pAxWru)
- Structured Query Languauge (SQL) for querying of Data [download here](https://1drv.ms/w/c/3d767624932c4481/Ef7LsocSyQNPtM0sxBkDodkBWGGN3mfFNM7SJ3Qck1IYZQ?e=UTUKSO)
- Micosoft PowerBI for visualization
- Github for portfolio building

### Data Cleaning and Preparations
----
After getting the data, I performed the following:
- Data loading and inspection
- Removal of duplicates
- Data cleaning and formatting

### Exploratory Data Analysis
---
This invoives exploring the data to answer pertinent questions such as:
- What is the total sales for each product category
- What is the number of sales transaction in each region
- What is the highest-selling product by total sales value
- What is the total revenue per product
- What is the monthly sales total for the current year
- Find the top 5 customers by total purchase amount
- What is the percentage of total sales contributed by each region
- Identify products without sales in the last quarter

### Data Analysis
---
Structured Query Language (SQL) was used to query data
```SQL
SELECT * FROM [LITA SalesData]
```
```SQL
SELECT Product, 
       SUM(Quantity) AS TotalSales
FROM  [LITA SalesData] 
GROUP BY Product;
```
```SQL
SELECT Region, 
       COUNT(*) AS OrderID
FROM [LITA SalesData]
GROUP BY Region;
```
```SQL
SELECT TOP 1 Product, 
       SUM(Quantity) AS TotalSales
FROM  [LITA SalesData]
GROUP BY Product
ORDER BY TotalSales DESC;
```
```SQL
SELECT Product, 
       SUM(Revenue) AS TotalRevenue
FROM [LITA SalesData]
GROUP BY Product;
```
```SQL
SELECT 
    DATENAME(MONTH, OrderDate) AS SalesMonth, 
    SUM([Quantity]) AS TotalSales
FROM 
    [LITA SalesData]
WHERE 
    YEAR(OrderDate) = YEAR(GETDATE()) 
GROUP BY 
    DATENAME(MONTH, OrderDate), MONTH(OrderDate)
ORDER BY 
    MONTH(OrderDate);
```
```SQL
SELECT TOP 5 [Customer_Id] , 
       SUM([Revenue]) AS TotalPurchaseAmount
FROM [LITA SalesData]
GROUP BY [Customer_Id]
ORDER BY TotalPurchaseAmount DESC;
```
```SQL
SELECT Region, 
       SUM([Quantity]) AS TotalSales, 
       ROUND((SUM([Quantity]) * 100 / (SELECT SUM([Quantity])
	   FROM [LITA SalesData])), 2) AS PercentageSales
FROM [LITA SalesData]
GROUP BY Region;
```
```SQL
SELECT Product
FROM [LITA SalesData]
WHERE Product NOT IN (
    SELECT DISTINCT Product
    FROM [LITA SalesData]
    WHERE OrderDate >= DATEADD(QUARTER, -1, GETDATE()))
GROUP BY Product;
```
### Data Visualization
---
![Highest Selling Product](https://github.com/user-attachments/assets/d387fcee-6076-4109-b514-4a2cbca77a87)
![Highest Selling Product2](https://github.com/user-attachments/assets/c80c59b3-e46f-4468-a6e6-69589af376d6)
