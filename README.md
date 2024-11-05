# Capstone Project 1

# Project Title
Sales Performance Analysis for a Retail Store

## Project Overview
This Data Analysis Project aims to generate insight into the sales performance of a Retail Store. By exploring the sales data and analysing the various parameters, I seek to uncover key insights such as top-selling products, regional performance and monthly sales trend. This would help make data-driven decisions and enable me tell a unique story with the insights gotten from the data.

## Table of Content
* [*Project Title*](#project-title)
* [*Project Overview*](#project-overview)
* [*Data Sources*](#data-sources)
* [*Tools Used*](#tools-used)
* [*Data Cleaning and Preparation*](#data-cleaning-and-preparation)
* [*Data Analysis*](#data-analysis)
* [*Data Visualization*](#data-visualization)
* [*Recommendations*](#recommendations)
  
### Data Sources
The primary source of Data used in this Project is Sales Data file and this can be downloaded here.[Sales Data.csv](https://github.com/user-attachments/files/17631160/Sales.Data.csv)


### Tools Used
- Microsoft Excel for Data Cleaning [Download Here](https://www.microsoft.com)
- SQL Server for Querying and Analysis [Download Here](https://www.microsoft.com)
- Microsoft Power BI for  Analysis and Visualiation [Download Here](https://www.microsoft.com)
- Github for Portfolio building [Download Here](https://www.github.com)

### Data Cleaning and Preparation
**Steps Taken:**

1. **Import Data:**
   - The sales dataset was imported into Excel for initial exploration and cleaning.

2. **Remove Duplicates:**
   - Ensured the dataset was free of duplicate records by removing any duplicates based on `OrderID`.

3. **Handle Missing Values:**
   - Checked for and addressed any missing values within the dataset.

4. **Standardize Data:**
   - Ensured consistent formatting of text data, such as converting all text to uppercase where necessary.

5. **Create New Columns:**
   - **Total Sales (Revenue)**: Calculated as `Quantity * UnitPrice`.
   - **Order Month**: Extracted from `OrderDate` using the formula `=TEXT(OrderDate, "mmmm")`.

### Data Analysis

#### Data Analysis in Excel

**Pivot Tables:**

1. **Total Sales by Product:**
   - Created pivot tables to analyze total sales by `Product`.
     
     ![Screenshot 2024-11-04 131106](https://github.com/user-attachments/assets/e56cc69a-d59c-4f4a-b0c4-852c5a5397e1)


2. **Total Sales by Region:**
   - Created pivot tables to analyze total sales by `Region`.
     
     ![Screenshot 2024-11-04 131106](https://github.com/user-attachments/assets/a88e707e-c525-4eb2-8cc9-0e98526b9144)


3. **Total Sales by Month:**
   - Created pivot tables to analyze total sales by `Order Month`.
     
   ![Screenshot 2024-11-04 131129](https://github.com/user-attachments/assets/9707bec9-22d0-4b27-9630-e555264200ce)


4. **Average Sales per Product:**
   - Calculated the average sales per product using the formula `=AVERAGEIF(Product, "Product_Name", TotalSales)`.
     
     ![Screenshot 2024-11-04 132406](https://github.com/user-attachments/assets/197084d5-fd6e-4610-a7ba-4e4dde9b6f45)


5. **Total Revenue by Region:**
   - Calculated total revenue by region using the formula `=SUMIF(Region, "Region_Name", TotalSales)`.
     
     ![Screenshot 2024-11-04 132442](https://github.com/user-attachments/assets/84031a67-ceff-4cb4-a5b5-c362365364cf)


6. **Product Performance by Region:**
   - Created pivot tables to analyze product performance by region.
     
     ![Screenshot 2024-11-04 131459](https://github.com/user-attachments/assets/02096090-735a-40f7-846a-f4846d9ae9b3)


7. **Monthly Sales Trend:**
   - Created line charts or bar charts to visualize monthly sales trends.
     
     ![Screenshot 2024-11-04 133239](https://github.com/user-attachments/assets/91b011a1-637c-4c92-9110-3f8691bcc23c)

8. **Top 10 Customers by Revenue and with Highest Purchase Frequency:**
   - Created pivot tables to analyze Top 10 Customers by `Revenue` and Top 10 Customers with the `Highest Purchase Frequency`.
     
     ![Screenshot 2024-11-04 131559](https://github.com/user-attachments/assets/2ffc4609-be47-460f-8713-1ea16984ffcb)


#### SQL Analysis

**Queries Executed:**

   ![Screenshot 2024-11-05 102434](https://github.com/user-attachments/assets/19e629c6-0e28-4b5d-bf06-0a4b84268989)

1. **Total Sales for Each Product Category:**
   ```sql
   SELECT Product, SUM(Quantity * UnitPrice) AS TotalSales
   FROM SalesData
   GROUP BY Product;
   ```
   
   ![Screenshot 2024-11-05 103459](https://github.com/user-attachments/assets/63aa615d-b8c5-4e90-a6ca-c63accd06378)


2. **Number of Sales Transactions in Each Region:**
   ```sql
   SELECT Region, COUNT(OrderID) AS NumberOfTransactions
   FROM SalesData
   GROUP BY Region;
   ```
   
   ![Screenshot 2024-11-05 103537](https://github.com/user-attachments/assets/21cb21b8-7f8c-42da-ae9f-705415191c7b)


3. **Highest-Selling Product by Total Sales Value:**
   ```sql
   SELECT TOP 1 Product, SUM(Quantity * UnitPrice) AS TotalSales
   FROM SalesData
   GROUP BY Product
   ORDER BY TotalSales DESC;
   ```
   
   ![Screenshot 2024-11-05 103729](https://github.com/user-attachments/assets/b1faf626-48a2-4b27-8916-8a3f703cf054)


4. **Total Revenue Per Product:**
   ```sql
   SELECT Product, SUM(Quantity * UnitPrice) AS TotalRevenue
   FROM SalesData
   GROUP BY Product;
   ```
   
   ![Screenshot 2024-11-05 103826](https://github.com/user-attachments/assets/3ce8b965-5619-4764-95ed-4b218a770b62)


5. **Monthly Sales Totals for the Current Year:**
   ```sql
   SELECT MONTH(OrderDate) AS Month, SUM(Quantity * UnitPrice) AS TotalSales
   FROM SalesData
   WHERE YEAR(OrderDate) = YEAR(GETDATE())
   GROUP BY MONTH(OrderDate);
   ```
   
   ![Screenshot 2024-11-05 104909](https://github.com/user-attachments/assets/d1c58770-bc95-43fb-bd65-1392147c8612)


6. **Top 5 Customers by Total Purchase Amount:**
   ```sql
   SELECT TOP 5 CustomerID, SUM(Quantity * UnitPrice) AS TotalPurchaseAmount
   FROM SalesData
   GROUP BY CustomerID
   ORDER BY TotalPurchaseAmount DESC;
   ```
   
   ![Screenshot 2024-11-05 104942](https://github.com/user-attachments/assets/2cbbf024-ab77-41a6-b49e-d58bea0f38c9)


7. **Percentage of Total Sales Contributed by Each Region:**
   ```sql
   SELECT Region, 
   SUM(Quantity * UnitPrice) * 100.0 / (SELECT SUM(Quantity * UnitPrice) FROM SalesData) AS SalesPercentage
   FROM SalesData
   GROUP BY Region;
   ```
   
   ![Screenshot 2024-11-05 110417](https://github.com/user-attachments/assets/3e4472d7-2b28-4be8-978b-245e85074dcc)


8. **Identify Products with No Sales in the Last Quarter:**
   ```sql
   SELECT Product
   FROM SalesData
   WHERE OrderDate < DATEADD(MONTH, -3, GETDATE())
   AND Product NOT IN (
     SELECT Product
     FROM SalesData
     WHERE OrderDate >= DATEADD(MONTH, -3, GETDATE())
   )
   GROUP BY Product;
   ```
   
   ![Screenshot 2024-11-05 105946](https://github.com/user-attachments/assets/3c88ff1a-dbbe-4462-ba13-f8939958e83b)


### Data Visualization

#### Power BI Dasboard

**Steps Taken:**

1. **Load Data into Power BI:**
   - Imported the cleaned and prepared dataset into Power BI Desktop.

2. **Create Visuals:**
   - **Sales Overview:**
     - Created a card visual displaying total sales.
   - **Top-Performing Products:**
     - Created a bar chart showing total sales by product.
   - **Monthly Sales Trend:**
     - Created a line chart showing monthly sales trends

      ![Screenshot 2024-11-05 154306](https://github.com/user-attachments/assets/565f991b-c1f9-4155-b5e0-477b7b1c44eb)


      ![Screenshot 2024-11-05 154321](https://github.com/user-attachments/assets/77d041ea-7281-46f6-a118-1b9a2d07b61b)


      ![Screenshot 2024-11-05 154400](https://github.com/user-attachments/assets/5593fb39-0b75-48c6-a66a-c47bc1f2a5a3)


3. **Add Slicers:**
   - Added slicers for `Product`, `Region`, and `Order Month` to allow for interactive data exploration.

4. **Design and Layout:**
   - Arranged the visuals in a logical and visually appealing layout.
   - Used appropriate colors and themes to enhance readability.

5. **Publish Dashboard:**
   - Published the Power BI dashboard to the Power BI service for sharing and collaboration.

### Recommendations
**1. Optimize Inventory Management:**
   - **Insight:** Products like `Shirt` and `Shoes` are top-selling items.
   - **Recommendation:** Ensure these high-demand products are always in stock to meet customer demand and avoid stockouts. Implement an automated inventory management system to track stock levels in real-time.

**2. Tailor Marketing Strategies by Region:**
   - **Insight:** Certain regions like the `North` and `South` show higher sales volumes.
   - **Recommendation:** Allocate more marketing resources to these regions. Develop region-specific promotions and advertising campaigns to further boost sales.

**3. Enhance Customer Engagement:**
   - **Insight:** Top 5 customers contribute significantly to the total sales.
   - **Recommendation:** Implement loyalty programs and personalized marketing efforts to retain these high-value customers. Consider exclusive offers or early access to new products for loyal customers.

**4. Focus on Seasonal Trends:**
   - **Insight:** Monthly sales trends indicate seasonal peaks.
   - **Recommendation:** Plan marketing campaigns and stock levels around these peak periods. Offer seasonal promotions and discounts to maximize sales during high-demand months.

**5. Product Diversification:**
   - **Insight:** Products like `Hat` and `Socks` have lower sales compared to others.
   - **Recommendation:** Evaluate the demand and profitability of these products. Consider introducing new product variations or discontinuing underperforming items to optimize product mix.

