### CAPSTONE-PROJECT-2
### Project Title: Customer Data
### Project Overview
This project involves analyzing customer data for a subscription service to identify
segments and trends. My goal is to understand customer behavior, track subscription types,
and identify key trends in cancellations and renewals. The final deliverable is a Power BI
dashboard that presents my analysis.
### Data Sources
The primary source of my data was a customerData containing 75000 customer's ID with information
### Data Tools used
1. Microsoft Excel for data cleaning, analysis and visualization
2. SQL for structured data querrying
3. PowerBI for data cleaning, analysis and visualization  
4. GitHub for showcasing progress of the progress
## Data Cleaning and Preparation
In the initial stage of my data cleaning, I performed the following actions;

- Data Loading and inspection

   My data was loaded into Microsoft Excel using the Excel workbook and inspected to access the data quality

- Data handling of missing variables

   The missing variables was calculated using excel functions
- Data cleaning and formatting

### Exploratory Data analysis using Microsoft Excel 
   Data summarization was done on customer data using pivot tables to find different subscription patterns
   
   ![subscription type by duration](https://github.com/user-attachments/assets/6c76fc49-07c0-4d70-8d42-ba8fd0bb3077)
   ![SUBSCRIPTION TYPE BY REGION BY REVENUE](https://github.com/user-attachments/assets/0058542f-ad0d-4eb6-a912-acebbfb4000e)
   ![SUBSCRIPTION TYPE BY CUSTOMERID BY CANCELLED](https://github.com/user-attachments/assets/7565866f-d81b-492a-95ce-903e3511cdcb)
![subscription type by customer ID](https://github.com/user-attachments/assets/e9bed5ad-d5ba-4d01-ade5-3be5781050c6)

From the data summarized above, I was able to deduce the average subscription duration to be 365 and also identify 'basic' as the most popular
subscription types 

### Exploratory Data analysis using SQL
my customer Dataset was loaded into your SQL Server environment to write
and validate your queries.
i was able to write queries to extract key insights based on the following questions.
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
### Exploratory Data analysis and visualization using PowerBI
my customer Dataset was loaded into your PowerBI environment and necessary data formatting and visaulization tools were deployed to produce some beautiful visuals

![BI 1](https://github.com/user-attachments/assets/4e280965-1c19-4eaa-9157-f830821643e3)

![BI 2](https://github.com/user-attachments/assets/795f80f9-714a-4282-9cac-fae58772e372)
