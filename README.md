
## Project Title: MISOSA Sales Data Analysis

 This repository contains a comprehensive analysis of the sales data for a retail store- MISOSA. The aim of this project is to uncover key insights from the sales data, enabling the retail Store MISOSA to make informed business decisions and enhance overall sale performance

 

### Project Overview
This project involves analyzing sales performance to uncover sales key insights such as top-selling products, regional performance, and monthly sales trends. The final deliverable is a Power BI dashboard that presents these insights.

#### Outline
1. [Background and Objective](#background-and-objective)
2. [Data Sources and tools used](#data-sources-and-tools-used)
3. [Exploratory Data Analysis](#exploratory-data-analysis)
4. [Key Insights and Interpretation](#key-insights-and-interpretation)
5. [Code and Queries preview](#code-and-queries-preview)
6. [Data Visuals](#data-visuals)
7. [PowerBI Dashboard](#powerbi-dashboard)
8. [Results](#results)
9. [Conclusion](#conclusion)

### Background and Objective
MISOSA is a growing retail business in Nigeria that would like to enhance their sales performance. MISOSA has a large volume of data on sales across different products, regions, and years and it believes that it is now at a stage where the data needs to be analyzed to help with making strategic decisions. This will be done using Excel, SQL, and Power BI to conduct an exploratory analysis of the sales data for MISOSA. It will focus primarily on identifying the best performing products, regional trends in sales, and variations by season. 
The objective of this project is to create an interactive Power BI dashboard that highlights MISOSA’s key sales insights. By uncovering trends in product popularity, regional performance, and monthly sales patterns, this analysis aims to support MISOSA’s strategic planning, optimize inventory management, and improve targeted marketing efforts.

### Data Sources and tools used
Data Source: Data was gotten from the incubator hub- Ladies in tech Africa (LITA) Capstone Project in the form of an excel sheet
Tools used include;
- Microsoft Excel: For Data cleaning, initial data exploration and analysis
- SQL server management studio: Used for complex data querying to find out details of the data
- PowerBI Desktop: For building an interactive dashboard to present the key insights

### Exploratory Data Analysis
- Data Description; The unique columns contained in the excel sheet
  1. OrderID - Unique identifier for transaction
  2. CustomerID - Unique identifier for customers
  3. Product - Product types
  4. Region - Geographical locations
  5. Quantity - units of product
  6. Unitprice - price of product

 - #### Methodology
   1. Initial data exploration in excel to understand the dataset
   2. Data summarization with Pivot tables to find key metrics and calculation
   4. Flat file was imported into SQL server environment for more detailed analysis
   5. Data was imported into PowerBI for visualization 
   6. measures, calculated fields, and designed visualizations were used to answer key business questions
      


   ### Key Insights and Interpretation
  - Sales Overview: This give a view of MISOSA sales and financial performance. Any shift in sales could highlight external reasons such as seasonal performance etc
  - Top selling products; Products was broken down by region and type to understand regional and customer preferences. This insight help to prioritize popular products and increase marketing for less popular ones with high potential for profit
  - Regional sales performance; This helps the company identify geographical markets with high sales potential and identify the percentage of revenue brough in by the different region. This will help in understanding customer behaviour and marketing decisons.
  -  Monthly sales trend
  -  Products with no sale in last quarter
  -  Top customers which will help in building customer loyalty by engagemet


### Code and Queries Preview
---
     SQL QUERIES
     
   (1)Total sales for each product category
Select [Product], Sum(Sales) AS [Total Sales] From LITA_Data
GROUP BY [Product] Order By [Total Sales] DESC

----(2) Number of Sales Transaction in each rgion
SELECT Region, Count(OrderID) AS [No. of sales trans.] from Lita_Data
GROUP BY Region Order by 2 desc

----(3) HIGHEST SELLING PRODUCT BY TOTAL SALES
SELECT TOP 1 [Product], Sales FROM Lita_Data
WHERE Sales = (SELECT MAX(Sales) FROM Lita_Data)
---Showing the total sales made from Shoe
SELECT TOP 1 Product, SUM(Sales) AS TotalSales FROM lita_Data
GROUP BY Product


----(4) Total Revenue per product
     Select [Product], Sum(  Quantity * UnitPrice) as Totalsales
	 From Lita_Data
	 Group By [Product]

----(5) Monthly sales total for 2024-
Select FORMAT(OrderDate, 'YYYY-MM') AS [MONTH], SUM(Sales) AS [Total Sales]
FROM lITA_Data WHERE Year(OrderDate) = 2024
Group by FORMAT(OrderDate, 'YYYY-MM')
ORDER BY 1

-----(6) Top 5 customers by total purchase amount
SELECT * FROM LITA_DATA
Select TOP 5 Customer_id, Sum (Sales) as [Total Purchase] FROM LITA_DATA
GROUP BY Customer_id Order by 2 DESC

----(7) Percentage of Total sale Contributed by Region
--- % = (sales/ Total sales ) * 100
SELECT  Region, SUM(Sales) AS Region_Sales,
(SUM (Sales) / (Select Sum(Sales) from Lita_Data )* 100) As [Pecentage%]
FROM Lita_Data GROUP BY Region

----(8) Identify products with no sale in the last quarter---
---Last quarter is July - Sept 2024

SELECT DISTINCT Product From LITA_Data
EXCEPT Select Distinct Product from LITA_Data
WHERE OrderDate >= '2024-07-01' AND OrderDate < '2024-10-01'

---

### Data Visuals
![project 1 pivot excel](https://github.com/user-attachments/assets/47a26229-f545-4e36-8305-eab3d72d02f7)
![project 1 excel](https://github.com/user-attachments/assets/adc4d5e6-70f7-4cd2-a927-c8b0eb197972)
![excel P1visual](https://github.com/user-attachments/assets/dafa3516-be94-410c-ad34-5a312306ff07)
![SQL P14](https://github.com/user-attachments/assets/3a5bd0bf-2f53-40f9-8dd3-f5822d76c343)
![SQL P13](https://github.com/user-attachments/assets/4fd6db85-1e48-4711-9307-70fe4f2724c4)
![sql p12](https://github.com/user-attachments/assets/0595818b-1471-46bc-baea-4a63f4ef3f6d)
![sql p11](https://github.com/user-attachments/assets/36531303-ced7-4662-b596-115e6285ee55)




### PowerBI Dashboard
![project 1 Dashboard](https://github.com/user-attachments/assets/f39d510f-6257-476d-81d4-0e85cc65ef54)


### Results

From the interactive dashboard created, we get a clear story that help MISOSA understand the business
- **Product Strategy:** With Shoes and Hat as best-sellers, MISOSA should consider expanding their inventory of these items and exploring why they are more popular than others. This may also suggest an opportunity for cross-selling with other products. 
- **Regional Focus:** The high revenue contribution from the South region suggests it’s a strong market for MISOSA. Focused marketing efforts, regional promotions, and localized product availability could drive further sales in this area.
- **Timing of Promotions:** The sales spike in March suggests that seasonal factors may impact customer buying behavior. MISOSA can use this insight to plan seasonal promotions or new product launches around these peak times to maximize sales.
- **Customer Engagement:** Engage top customers with personalized offers, fostering loyalty and repeat purchases.


### Conclusion
Through this interactive dashboard, MISOSA will gain a comprehensive understanding of its sales performance, guiding strategic decisions to support strategic decision-making, aiming to boost sales, improve customer satisfaction, and drive sustainable growth.


      


