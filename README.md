# LITA_PROJECT-SALES-DATA-ANALYSIS-
This repository contains data analysis projects using Excel, SQL, and Power BI to extract insight from sales data.


### Project Sructure:
- Excel: Contains Excel files for data exploration and calculation.
- SQL: Contains SQL queries for data analysis.
- Power BI: Contains Power BI dashboard files(Data and Visualization).
- Data: Contains sales data(XLSX & CSV) files.

### Excel Files:
- Sales Exploration: Initial data exploration using pivot tables.
- Sales Metrics: Calculations for average sales per product and total revenue by region.

### SQL Queries:
- Sales_queries: Queries for total sales by product category, number of sales transactions by region, highest-selling product, total revenue per product, monthly sales totals, top 5 customers, and percentage of total sales by region.

### Power BI Dashboards:
- Sales Overview: Dashboard visualizing sales overview, top-performing products, and regional breakdowns.

### Data Files:
- Sales_data: Sales data used for analysis.

### Instuctions given;
1. Clone the repository.
2. Load the sales data into your SQL Server environment.
3. Run SQL queries to extract insights.
4. Open Excel files to view calculations and pivot tables.
5. Open Power BI dashboard files to visualize insights.

### SQL Queries Documentation:
CREATE DATABASE RUTH_01

```
SELECT * FROM [dbo].[Sales data1]
```

-----------Total Sales from each Product category-------
```
Select Product, SUM(Total_Sales) as Total_Sales from [dbo].[Sales data1]
Group by Product;
```

-------Number of Sales Transaction in each Region----------
```
Select Region,Count(Total_Sales) as No_of_Sales_by_Region
From [dbo].[Sales data1]
Group by Region
```

------Highest Selling Product by Total Sales Value--------
```
Select Product, Sum(Total_Sales) as Highest_Selling_Product from [dbo].[Sales data1]
Group by Product
Order by Product desc
```

------Total Revenue per Product-----
```
Select Product, Sum(Total_Sales) as Total_Sales from [dbo].[Sales data1]
Group by Product;
```

--------Monthly Sales Total for the Current Year---------
```
Select Month(OrderDate) as Month,
Sum(quantity*unitprice) as Monthly_Sales
From [dbo].[Sales data1]
Where Year(OrderDate)=Year(GetDate())
Group by Month(OrderDate);
```

------Top 5 Customers by Total Purchase Amount---------
```
Select Top 5 Customer_Id,
Sum(Total_Sales) as Total_Purchase_Amount
From [dbo].[Sales data1]
Group by Customer_Id
Order by
Total_Purchase_Amount desc;
```

------Percentage of Total Sales Contributed by each Region-----------
```
With Total_Sales as(
Select Sum(quantity*unitprice) as Total_Sales_Amount
From[dbo].[Sales data1]
)
Select Region, Sum(quantity*unitPrice) as Region_Sales,
(Sum(quantity*unitprice)*100)/ts. Total_Sales_Amount as Percentage_Contribution
From[dbo].[Sales data1]
Cross Join Total_Sales ts
Group by Region,
Total_Sales,Total_Sales_Amount;
```

-----------Product with no Sales in the last Quater---------
```
Select Distinct Product, Order_Id, Quantity
From[dbo].[Sales data1]
Where Product not in
(Select Distinct Product
From[dbo].[Sales data1]
Where OrderDate between '2024-07-01' and '2024-09-30'
)
```



### Visualizations
![Sales's Table](https://github.com/user-attachments/assets/572505e4-f76b-45ab-9f2d-98aa50ce060c)
![SalesData_Pivot Table2](https://github.com/user-attachments/assets/84ad09c8-a08f-4b37-8587-e086e5dd1a59)
![SalesData_Pivot Table1](https://github.com/user-attachments/assets/ce849e7e-79e2-449c-86c1-7b55b5318834)
![SalesData(Clean)](https://github.com/user-attachments/assets/6b00e172-d897-4359-9ff1-cf7570a85c86)
![SalesData_PowerBI(Clean)](https://github.com/user-attachments/assets/497c0e3f-2d4b-45c2-9fd9-1e33c2fa0446)
![SALES VISUALIZATION](https://github.com/user-attachments/assets/e756f990-fee9-4689-bff9-5dde30478b82)
