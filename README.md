### CAPSTONE-PROJECT-2
### Project Title: Customer Data
### Project Overview
This project involves analyzing customer data for a subscription service to identify
segments and trends. Your goal is to understand customer behavior, track subscription types,
and identify key trends in cancellations and renewals. The final deliverable is a Power BI
dashboard that presents your analysis.
### Data Sources
The primary source of my data was customer data
### Data Tools used
1. Microsoft Excel for data cleaning, analysis and visualization
2. SQL for structured data querrying
3. PowerBI for data cleaning, analysis and visualization  
4. GitHub for showcasing progress of the progress
## Data Cleaning and Preparation
In the initial stage of my data cleaning, I performed the following actions;
1. Data Loading and inspection
2. Data handling of missing variables
3. Data cleaning and formatting
## Exploratory Data analysis using Microsoft Excel 
   
## Exploratory Data analysis using SQL

Write queries to extract key insights based on the following questions.
```SQL
select * from [dbo].[CustumerData]
```
o retrieve the total number of customers from each region.
```SQL
SELECT Region,count(*) NumberofCustomer FROM [dbo].[CustumerData]
GROUP BY Region
```
o find the most popular subscription type by the number of customers.
```SQL
SELECT top 1 SubscriptionType, COUNT(CustomerID) CustomerCount
FROM [dbo].[CustumerData]
GROUP BY SubscriptionType
ORDER BY CustomerCount DESC
```
o find customers who canceled their subscription within 6 months.
```SQL
SELECT CustomerID, SubscriptionStart, SubscriptionEnd
FROM [dbo].[CustumerData]
WHERE DATEDIFF(month, SubscriptionStart, SubscriptionEnd) <= 6
  AND Canceled = 'TRUE'
```
o calculate the average subscription duration for all customers.
```SQL
SELECT AVG(DATEDIFF(day, SubscriptionStart, SubscriptionEnd)) AS AverageDuration
FROM [dbo].[CustumerData]
```
o find customers with subscriptions longer than 12 months.
```SQL
SELECT CustomerID, SubscriptionStart, SubscriptionEnd
FROM [dbo].[CustumerData]
WHERE DATEDIFF(month, SubscriptionStart, SubscriptionEnd) >12

```
o calculate total revenue by subscription type.
```SQL
SELECT SubscriptionType, SUM(Revenue) AS TotalRevenue
FROM [dbo].[CustumerData]
GROUP BY SubscriptionType
```
o find the top 3 regions by subscription cancellations.
```SQL
SELECT top 3 Region, COUNT(CustomerID) AS CanceledCount
FROM [dbo].[CustumerData]
WHERE Canceled = 'TRUE'
GROUP BY Region
ORDER BY CanceledCount DESC
```
o find the total number of active and canceled subscriptions.
```SQL
SELECT 
  COUNT(CASE WHEN Canceled = 'TRUE' THEN 1 END) AS CanceledCount,
  COUNT(CASE WHEN Canceled = 'FALSE' THEN 1 END) AS ActiveCount
FROM [dbo].[CustumerData]
```
