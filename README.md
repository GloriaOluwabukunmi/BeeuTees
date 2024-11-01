## LITA PROJECT 2 

### PROJECT ANALYSIS ON CUSTOMERS DATA OF A RETAIL STORE

[PROJECT OVERVIEW](#project-overview)

[DATA SOURCE](#data-source)

[DATA COLLECTED](data-collected)

[PROJECT OBJECTIVE](project-objective)

[KEY METRICS](key-mertics)

[FUNCTIONS USED IN EXCEL](functions-used-in-excel)

[TOOLS AND METHOD](#tools-and-method)

[DATA ANALYSIS](#data-analysis)

[DATA VISUALIZATION](#data-visualization)



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
SELECT [SubscriptionType]
COUNT([CustomerID]) AS total
FROM [SubscriptionType]
WHERE [SubscriptionType] IN [Canceled]
GROUP BY [SubscriptionType]
```

### DATA VISUALIZATION

😆
💻

|Heading 1|Heading 2|Heading 3| 
|---------|--------|----------|
|Table 1|Table 2|Table 3|


  
