## LITA PROJECT 2 

### PROJECT ANALYSIS ON CUSTOMERS DATA OF A RETAIL STORE

[PROJECT OVERVIEW](#project-overview)

[DATA SOURCE](#data-source)

[DATA COLLECTED](data-collected)

[PROJECT OBJECTIVE](project-objective)

[KEY METRICS](key-mertics)

[FUNCTIONS USED IN EXCEL](functions-used-in-excel)

[TOOLS AND METHOD](#tools-and-method)

[DATA VISUALIZATION WITH PIVOT TABLE](data-visualization-with-pivot-table)

[SQL QUERIES FOR CUSTOMER DATA](#sql-queries-for-customer-data)

[DATA VISUALIZATION WITH PIVOT TABLE](#data-visualization-with-pivot-table)



### PROJECT OVERVIEW
This project is to analyze the Customers Data on a retail store, analyzing the subscription pattern for customers in each region

### DATA SOURCE
---
The primary sources of Data used here was provided by the company
### DATA COLLECTED
The Dataset includes the following key columns
- CustomerID
- CustomerName
- Region
- SubscriptionType
- SubscriptionStart
- SubscriptionEnd
- Canceled
- Revenue

### PROJECT OBJECTIVE
---
This project was designed to address the following analysis goals
- Analyze customer data in order to detect their subscription pattern 
- Calculate the average subscription duration and identify the most popular subscription type
- Retrieve total number of customer in each region
- Analyze customer who canceled their subscription within 6 months
- Average subscription duration for all customers
- Customers with subscription longer than 12 months 
- Total revenue by subscription type
- Top 3 region by subscription cancellation
- Total number of active and canceled subscription

### KEY METRICS
- Subscription Duration for each customer
- Subscription Type for each customer

### FUNCTIONS USED IN EXCEL
SUN, AVERAGE

### TOOLS AND METHOD
1. Microsoft Excel [Download Here](https://www.microsoft.com)
- for data cleaning and formatting
2. SQL (Structured Query Language)
- for querying and writing basic lines of codes
3. Powerbi
- for data visualization 
4. GitHub
- for Portfolio Building

  ### DATA ANALYSIS
  #### DATA VISUALIZATION WITH PIVOT TABLE
  
- Region by average subscription duration

![image](https://github.com/user-attachments/assets/feb2dda6-82b9-4a67-81e4-2bfa086e744c)


- Sum of Duration by Subscription Type

![image](https://github.com/user-attachments/assets/1551aa88-0f9a-48c9-acfa-f69ae461ad5b)



- Sum of Duration Count of Region by Canceled
		
![image](https://github.com/user-attachments/assets/580050fd-037d-40a4-bc06-a4ce11867a6f)




- Count of Region Average of Duration by Average of Revenue and Subscription Type
			
![image](https://github.com/user-attachments/assets/26688ef0-7432-49bb-ae76-81182641e931)


### SQL QUERIES FOR CUSTOMER DATA

- TOTAL NUMBER OF CUSTOMERS FROM EACH REGION
```SQL
SELECT Region, COUNT(*) AS total_customers
FROM CustomerData$
GROUP BY Region
```

- MOST POPULAR SUBSCRIPTION TYPE BY NUMBER OF CUSTOMERS
```SQL
SELECT SubscriptionType, COUNT(*) AS total_customers
FROM CustomerData$
GROUP BY SubscriptionType
ORDER BY total_customers Desc
```

- CUSTOMERS WHO CANCELLED THEIR SUBSCRIPTION WITHIN 6 MONTHS
```SQL
SELECT * FROM CustomerData$
WHERE Canceled IS NOT NULL
AND Canceled >= DATEADD (MONTH, -6, GETDATE());
```
- AVERAGE SUBSCRIPTION DURATION FOR ALL CUSTOMERS
```SQL
SELECT AVG(DATEDIFF(MONTH, SubscriptionStart,
coalesce(canceled, GETDATE()))) AS AVERAGE_DURATION
FROM [dbo].[CustomerData$]
```
- SUBSCRIPTION LONGER THAN 12 MONTHS
```SQL
SELECT * FROM  [dbo].[CustomerData$]
WHERE DATEDIFF(MONTH, SubscriptionStart,
COALESCE(Canceled, GETDATE())) >12;
```
- TOTAL REVENUE BY SUBSCRIPTION TYPE
```SQL
SELECT [SubscriptionType], 
SUM(Revenue) as revenue 
from [dbo].[CustomerData$]
GROUP BY [SubscriptionType]
```
- TOP 3 REGIONS BY SUBSCRIPTION CANCELLATION
```SQL
SELECT TOP 3 Region, COUNT(*) AS Canceled
FROM [dbo].[CustomerData$]
WHERE [Canceled] IS NOT NULL
GROUP BY [Region]
ORDER BY [Canceled] DESC
```
- TOTAL NUMBER OF ACTIVE AND CANCELLED SUBSCRIPTION TYPE
```SQL
SELECT 
SUM(CASE WHEN Canceled = 0 THEN 1 ELSE 0 END) AS ActiveSubscriptions,
SUM(CASE WHEN Canceled = 1 THEN 1 ELSE 0 END) AS CanceledSubscriptions
FROM [dbo].[CustomerData$]
GROUP BY CustomerID
```


### DATA VISUALIZATION WITH POWERBI DASHBOARD
![Screenshot 2024-11-04 195900](https://github.com/user-attachments/assets/41f20ec8-0348-45ea-8138-6d6675ca2f3d)

![Screenshot 2024-11-04 195933](https://github.com/user-attachments/assets/5d891e2c-9db2-4630-a8de-db2707bc33fb)

![Screenshot 2024-11-04 200053](https://github.com/user-attachments/assets/eba3cd90-e4ee-481e-93f1-b12c8f138a5a)

😆
💻

