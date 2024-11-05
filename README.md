[LITA_SalesData_Project](lita-salesdata-project)
[Project Overview](Project-Overview)
[Data Description](Data-Description)

# LITA_SalesData_Project
This is the SalesDate Project, Where I worked on Excel, SQL and Power BI


# Sales Data Analysis Project
-----

### Project Overview

This project involves analyzing the sales performance of a retail store to uncover key insights, including 
1. Top-selling products,
2. Regional sales performance, and
3. Monthly trends.

   * The goal is to produce a data-driven report and dashboard that can inform strategic business decisions.


### Data Description

#### Excel Analysis: Perform initial exploration using pivot tables to summarize

1. Total sales by product, Region, Month.
2. Created pivot tables to summarize sales metrics.
   
##### Calculated metrics like 
1. Average sales per product
2. Total revenue by region.


#### SQL Analysis: I used SQL queries to extract insights on
1. Product sales performance
2. Top regions
3. Monthly revenue
4. Top 5 customers by total purchase amount


### PowerBI: To create a dashboard that visualizes the insights found in Excel and SQL. 
#### The dashboard included;
1. Sales overview
2. Top-performing products
3. Regional breakdowns.




### Tools Used

#### Excel: For data exploration, pivot tables, and summary calculations.

#### SQL Server: For querying and extracting deeper insights.

#### PowerBI for Visualisations

https://1drv.ms/x/c/217a870815163ae5/ERv54YuXS3tEv3FNoumoox4BPkvC-WUqbWXU0JpxMZvoYw?e=g3qSo2

```create database LitaProject_Mary
select * from [dbo].[LITA Capstone_MaryAlabi]create database LitaProject_Mary
select * from [dbo].[LITA Capstone_MaryAlabi]

------ Total Sales for each product Category--------

```select product, sum(quantity * unitprice) AS Total_Sales
From [dbo].[LITA Capstone_MaryAlabi] Group By product


-------Number of Sales transactions in each Region------

```Select region,
count (*) AS TransactionCount
From [dbo].[LITA Capstone_MaryAlabi] 
Group by region


-----------Highest Selling Product by Total Sales Value

```Select product,
SUM(Quantity * UnitPrice) As TotalSales
From [dbo].[LITA Capstone_MaryAlabi]
Group By Product
Order By 
TotalSales DESC
 OFFSET 0 ROWS FETCH NEXT 10 ROWS ONLY

-------Total Revenue By Product-----

```Select product,
Sum(Quantity * UnitPrice) AS TotalRevenue
From [dbo].[LITA Capstone_MaryAlabi]
Group By Product


--------Monthly sales totals for the current year--------

```SELECT
FORMAT(ORDERDATE, 'MM') AS Sales_Month,
Sum(Quantity * UnitPrice) AS Monthly_Sales_Total
FROM [dbo].[LITA Capstone_MaryAlabi]
WHERE
YEAR(OrderDate) = 2024
GROUP BY
FORMAT (OrderDate, 'MM')
ORDER BY
FORMAT(OrderDate, 'MM')


-------Top 5 customers by total purchase amount--------

```Select Top 5
Customer_Id,
SUM(Quantity * UnitPrice) 
AS Total_Purchase_Amount
FROM [dbo].[LITA Capstone_MaryAlabi]
Group By Customer_Id
Order By Total_Purchase_Amount DESC


--------Percentage of total sales contributed by each region--------

``` Select region,
SUM(Quantity * UnitPrice) 
AS Region_Sales_Total,
   (SUM(Quantity * UnitPrice)* 100.0) / (SELECT SUM(Quantity * UnitPrice) 
   FROM [dbo].[LITA Capstone_MaryAlabi])
   AS Sales_Percentage
   FROM [dbo].[LITA Capstone_MaryAlabi]
   GROUP BY
   Region
  
    
  -------Products with no sales in the last quarter-----

  ```SELECT Product 
  FROM [dbo].[LITA Capstone_MaryAlabi]
  GROUP BY Product
  HAVING
  SUM(CASE WHEN OrderDate >= '2024-01-01' AND OrderDate < '2024-04-01' 
  THEN 1 ELSE 0 END


  


   










 
 







 




