# Power-BI-Projects

# Car Sales Dashboard

## Problem Statement:

This dashboard helps to study the sales of cars over the period by the company. It helps the company know how much revenue generated as compared to previous years, which color of car is preferred by customer, which transmission system preferred by customer. They get to know their improvement area, & thus they can improve their car sales by identifying these area.

## DASHBOARD 1 : OVERVIEW
- Data from excel file is imported into Power BI 

- Calendar Table is created by below DAX:

 #### Calendar Table = CALENDAR(MIN(car_data[Date]), MAX(car_data[Date]))

Additional columns like Year, Week number, Month etc. are added using FORMAT function in Calendar table.
- Using Model View- One to many relation is formed between date column of Calendar Table and date column of Cars_data table.

## KPI'S Requirement

1. Sales Overview:

- Year-to-Date (YTD) Total Sales:
DAX:-- TOTALYTD(SUM(car_data[Price ($)]), 'Calendar Table'[Date] )

- Month-to-Date (MTD) Total Sales:
DAX:-- TOTALMTD(SUM(car_data[Price ($)]), 'Calendar Table'[Date])

- Year-over-Year (YOY) Growth in Total Sales:

To calculate YOY growth, first we need to calculate previous years total sales as below:

DAX:-- PYTD Total Sales = CALCULATE(SUM(car_data[Price ($)]), SAMEPERIODLASTYEAR('Calendar Table'[Date]))

Then, we get % sales growth as below: 

DAX:-- YoY Sales Growth = [Sales Difference]/[PYTD Total Sales]

- Difference between YTD Sales and Previous Year-to-Date (PTYD)  Sales
DAX:-- Sales Difference = [YTD Total Sales] - [PYTD Total Sales]

2. Average Price Analysis:

- YTD Average Price
DAX:-- YTD Avg Price = TOTALYTD([Avg Price], 'Calendar Table'[Date])

- MTD Average Price
DAX:-- MTD Avg Price = TOTALMTD([Avg Price], 'Calendar Table'[Date])

- YOY Growth in Average Price
DAX:-- YoY Avg Price Growth = [Avg Price Diff] / [PYTD Avg Price]

- Difference between YTD Average Price and PTYD Average Price
DAX:-- Avg Price Diff = [YTD Avg Price]-[PYTD Avg Price]

3. Cars Sold Metrics:

- YTD Cars Sold
DAX:-- YTD Cars Sold = TOTALYTD(COUNT(car_data[Car_id]), 'Calendar Table'[Date])

- MTD Cars Sold
DAX:-- MTD Cars Sold = TOTALMTD(COUNT(car_data[Car_id]), 'Calendar Table'[Date])

- YOY Growth in Cars Sold
DAX:-- YoY Car Sold Growth = [Cars Sold Diff]/[PYTD Cars Sold]

- Difference between YTD Cars Sold and PTYD Cars Sold
DAX:-- Cars Sold Diff = [YTD Cars Sold]-[PYTD Cars Sold]

## Chart's Requirement

1. YTD Sales Weekly Trend: 
Display a line chart illustrating the weekly trend of YTD sales. The X-axis should represent weeks, and the Y-axis should show the total sales amount.

- To show Max sales point on Area chart, use below DAX:

- Created Total Sales DAX:-- Total Sales = SUM(car_data[Price ($)]) 

- DAX:-- Max Point on Area Chart = IF(MAXX(ALLSELECTED('Calendar Table'[Week]), [Total Sales]) = [Total Sales], MAXX(ALLSELECTED('Calendar Table'[Week]), [Total Sales]), BLANK())

2. YTD Total Sales by Body Style: 
Visualize the distribution of YTD total sales across different car body styles using a Pie chart.

3. YTD Total Sales by Colour: 
Present the contribution of various car colors to the YTD total sales through a pie chart.

4. YTD Cars Sold by Dealer Region: 
Showcase the YTD sales data based on different dealer regions using a map chart to visualize the sales distribution geographically.

5. Company-Wise Sales Trend in Grid Form: 
Provide a tabular grid that displays the sales trend for each company. The grid should showcase the company name along with their YTD sales figures.

6. Details Grid Showing All Car Sales Information: 
Create a detailed grid that presents all relevant information for each car sale, including car model, body style, colour, sales amount, dealer region, date, etc.


Findings:

- Yearly Analysis:

1. This year 2023, total revenue generated by saling cars is 371.2 million dollars which is 23.59% more than the previous year 2022.
2. The average revenue made in the year 2023 by selling cars is 28 thousand dollars which is 0.79% less than previous year 2022.
3. In the year 2023, 13.3 Thousand cars were sold which is 24.57% more cars sold than previous year 2022.
4. In week 36 of 2023, the most income was earned, which was 14.9 million dollars.

- Monthly Findings: 

1. In this month, Total Sale is 54.28 million dollars.
2. In this month, Average revenue of cars saling is 28.26 thousand dollars.
3. In this month, total 1.92 Thousand cars sold.

- Overall Analysis:

1. Mostly customer likes car with pale white color
2. Austin is the region where most cars sold
