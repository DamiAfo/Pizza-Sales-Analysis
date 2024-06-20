# Pizza-Sales-Analysis

## Table of Contents

- [Project Overview](#project-overview)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Recommendation](#recommendation)

### Project Overview

This data analysis project aims to provide insights into the sales of a pizza company over the year 2015. We analysed all aspects of the sales data in order to identity patterns and trends, gain a deeper understanding of consumers preference and make data-driven recommendation.

### Data Source

Sales Data: The primary dataset used for this analysis is "pizza_sales_excel_file.xlsx" file, containing detailed information about each sale made by the company.

### Tools

- Excel - Data Cleaning
- Microsoft SQL - Data Analysis
- PowerBI - Creating report and data visualization.

### Data Cleaning/Preparation

In the initial data preparation phase, we performed the following tasks:
1. Data loading and inspection
2. Convert Data types
3. Correct typos
4. Data cleaning and formatting.

### Exploratory Data Analysis

EDA involved exploring the pizza sales data to answer these key questions :

- What is the overall daily and monthly trend?
- Which products are the top sellers?
- Which products are the bottom sellers?

### Data Analysis

```sql
SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
FROM pizza_sales
GROUP BY DATENAME(DW, order_date)
```

```sql
select DATENAME(MONTH, order_date) as Month_Name, COUNT(DISTINCT order_id) as Total_Orders
from pizza_sales
GROUP BY DATENAME(MONTH, order_date)
```

```sql
SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_category
```

```sql
SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_size
ORDER BY pizza_size
```



### Results/Findings

The analysis results are summarized as follows:
1. For the daily trend, orders are highest on Fridays and Thursdays. For the monthly trend, maximum orders were recorded in July and May. Classic pizza category contributed to maximum sales and total order. Large size pizza contributed to maximum sales.
2. The Thai Chicken Pizza contributes to maximum Revenue. The Classic Deluxe Pizza contributes to maximum Total Quantities and Total Orders.
3. The Bree Carre Pizza contributes the least to Revenue, Quantities and Total Orders.
4. To check for the best and worst sellers, please refer to the visualization after the images provided.

![Daily trend](https://github.com/DamiAfo/Pizza-Sales-Analysis/assets/80990125/b917359c-7184-42d8-85da-10f358cbec37)


![Monthly trend](https://github.com/DamiAfo/Pizza-Sales-Analysis/assets/80990125/854d8fd8-9386-4e52-8fdb-303f41ef5ad7)


![Sales By Pizza Category](https://github.com/DamiAfo/Pizza-Sales-Analysis/blob/main/%25Sales%20by%20Pizza%20Category.png)


![Sales By Pizza Size](https://github.com/DamiAfo/Pizza-Sales-Analysis/blob/main/%25Sales%20by%20Pizza%20Size.png)

You can interact with the visualization [here](https://app.powerbi.com/groups/me/reports/21733948-814c-4860-9288-c94430449572?experience=power-bi)



### Recommendation

Based on the analysis, we recommend the following action:

- The high demand for Large pizza gives room for introducing more variants and offering exciting promos that would, in turn, improve sales and increase revenue.
- The three peak days for sales (Friday, Thursday and Saturday) should have adequate staff available for a better customer experience.
- In general, promotions should be done to amplify sales.
- Customers that purchased the worst sellers should give reviews. This would help determine if the variants should be made available, improved on or removed totally from the menu.





