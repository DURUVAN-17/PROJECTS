# Sales Analysis Dashboard

## Tool - Power BI Desktop

## Problem Statement

The Sales Analysis Dashboard is designed to provide comprehensive insights into sales performance, returns, and personnel effectiveness. By integrating data from the **Sales**, **Returns**, and **People** tables, this dashboard enables stakeholders to:

- **Monitor Sales Performance**: Track total sales, profits, and order counts across various dimensions.
- **Analyze Returns**: Understand return patterns to identify areas for improvement.
- **Evaluate Personnel Effectiveness**: Assess the performance of sales managers and their impact on sales outcomes.
- **Facilitate Decision-Making**: Utilize interactive filters and visualizations to make informed business decisions.

## Tables Used

- **Sales**: Contains details about orders, sales amounts, quantities, discounts, profits, and related metrics.
- **Returns**: Holds information about returned orders and reasons for returns.
- **People**: Includes data on employees, their roles, salaries, and branch affiliations.

## Reports and Visualizations

### **Report 1: Sales Overview**

#### **Filters:**
- Order Date
- City
- Region
- Category
- Sales Manager

#### **Card Values:**
- Total Profit
- Total Quantity
- Total Sales
- Total Order Count

#### **Visuals:**
1. **Pie Chart**: Total sales by manager.
2. **Bar Chart**: Total sales by manager.
3. **Waterfall Chart**: Sales breakdown by category.

---

### **Report 2: Customer and Product Insights**

#### **Filters:**
- Order Date
- Sales Manager
- Subcategory
- Ship Mode

#### **Card Values:**
- Total Sales
- Count of Cities
- Count of Products
- Count of Customers

#### **Visuals:**
1. **Matrix Chart**: Top 5 customers’ product names, sales, quantity, category, and city.
2. **Bar Chart**: Positive sales by manager.
3. **Bar Chart**: Negative sales by manager.
4. **Stacked Column Chart**: Top 5 states' profit and sales.

---

### **Report 3: Geographical and Temporal Analysis**

#### **Filters:**
- State
- City
- Region
- Category

#### **Visuals:**
1. **Line Chart**: Total profit per month.
2. **Line Chart**: Weekly sales trends.
3. **Ribbon Chart**: Sales by category.
4. **Scatter Chart**: Sales distribution by city.
5. **Tree Map**: Negative profit values by category.
6. **Map**: Quantity of sales by city.

---

### **Report 4: Sample Visuals**

#### **Visuals:**
1. **Matrix Chart**: Detailed data view.
2. **Table Chart**: Tabular representation of key metrics.
3. **Gauge Chart**: Performance against targets.
4. **Line and Stacked Column Chart**: Combined metrics visualization.
5. **Line and Clustered Column Chart**: Dual-axis data representation.

---

## Steps Followed

1. **Load Data**: Imported data from CSV files into Power BI Desktop.
2. **Data Cleaning**:
   - Opened Power Query Editor.
   - Enabled "Column Distribution," "Column Quality," and "Column Profile" under the Data Preview section.
   - Selected "Column profiling based on entire dataset" to analyze all rows.
   - Identified and addressed errors and empty values, specifically in the "Arrival Delay" column.
3. **Data Transformation**:
   - Excluded null values in "Arrival Delay" to ensure accurate average delay calculations.
   - Created calculated columns and measures using DAX for enhanced data analysis.
4. **Report Design**:
   - Applied a consistent theme (#E3F6DC) to all card visuals.
   - Added slicers for interactive filtering based on relevant fields.
   - Incorporated various chart types to represent different data perspectives.
5. **Visual Enhancements**:
   - Inserted text boxes for branding elements like the company's name and tagline.
   - Added shapes and images (e.g., company logo) to enhance the report's visual appeal.
6. **Publishing**:
   - Published the finalized report to Power BI Service for accessibility and sharing.

---

## Data Formatting

- **Date Format**: All dates are formatted as `MM/DD/YYYY`.
- **Currency Format**: All currency values are displayed in US dollars with two decimal places.

---

## Insights

### **Report 1: Sales Overview**

- **Total Profit**: Displays overall profitability across selected filters.
- **Total Quantity**: Shows the volume of products sold.
- **Total Sales**: Highlights the total revenue generated.
- **Total Order Count**: Indicates the number of orders placed.

### **Report 2: Customer and Product Insights**

- **Top Customers**: Identifies the top 5 customers based on sales, including detailed product information.
- **Sales Performance**: Differentiates between positive and negative sales by manager.
- **State-wise Analysis**: Compares profit and sales across the top 5 states.

### **Report 3: Geographical and Temporal Analysis**

- **Profit Trends**: Monitors monthly profit fluctuations.
- **Sales Trends**: Tracks weekly sales performance.
- **Category Sales**: Analyzes sales distribution across different categories.
- **City-wise Sales**: Visualizes sales distribution and quantity by city.
- **Profitability**: Highlights categories with negative profit values.

### **Report 4: Sample Visuals**

- **Detailed Data Views**: Provides matrix and table charts for in-depth data analysis.
- **Performance Indicators**: Utilizes gauge charts to track performance against targets.
- **Combined Visuals**: Employs combination charts for multi-metric visualization.

---
# Power BI Report used sample DAX Queries

### Filters:
- Order Date
- City
- Region
- Category
- Sales Manager

### Card Values:
- Total Profit
- Total Quantity
- Total Sales
- Total Order Count

### Charts:
1. **Pie Chart**: Total sales by manager
   ```DAX
   Total Sales by Manager = SUM(Sales[Total_Sales])

### Charts:
2. **Matrix Chart**: Top 5 customers’ sales 
   ```DAX
   Top 5 Customers = TOPN(5, SUMMARIZE(Sales, Sales[Customer_Name], "Total Sales", SUM(Sales[Total_Sales])), [Total Sales], DESC)


### Charts:
3. **Bar Chart**: Positive sales by manager
   ```DAX
   Positive Sales by Manager = CALCULATE(SUM(Sales[Total_Sales]), Sales[Total_Sales] > 0)


### Charts:
4. **Bar Chart**: Negative sales by manager
   ```DAX
   Negative Sales by Manager = CALCULATE(SUM(Sales[Total_Sales]), Sales[Total_Sales] < 0)

### Charts:
5. **Stacked Column Chart**: Top 5 States by Profit and Sales
   ```DAX
   Top 5 States by Profit and Sales = TOPN(5, SUMMARIZE(Sales, Sales[State], "Total Profit", SUM(Sales[Profit]), "Total Sales", SUM(Sales[Total_Sales])), [Total Sales], DESC)

### Charts:
6. **Line Chart**: Total profit for each month
   ```DAX
   Monthly Profit = CALCULATE(SUM(Sales[Profit]), DATESMTD(Sales[Order_Date]))


### Charts:
7. **Line Chart**: Weekly sales
   ```DAX
   Weekly Sales = CALCULATE(SUM(Sales[Total_Sales]), DATESWEEK(Sales[Order_Date]))

### Map:
8. **Tree Map**: Negative profit values for all categories 
   ```DAX
   Negative Profit by Category = CALCULATE(SUM(Sales[Profit]), Sales[Profit] < 0)

### Reports screenshots

### Report 1 snapshot:

![Screenshot 2024-09-27 170913](https://github.com/user-attachments/assets/7b6ab243-73a9-4e7b-9862-1e2d9559044d)

### Report 2 snapshot:

![Screenshot 2024-09-27 170937](https://github.com/user-attachments/assets/4e751299-1e15-4e75-9d26-dc97cbd49aba)

### Report 3 snapshot:

![Screenshot 2024-09-27 170958](https://github.com/user-attachments/assets/2cd44e8c-2e05-4861-af99-88e0a1f3b5b2)

### Report 4 snapshot:

![Screenshot 2024-09-27 171014](https://github.com/user-attachments/assets/fe6b19b3-ab34-4fe6-9fb6-b482661e2e2d)












