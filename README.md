


ClassicModels Sales Dashboard -- Power BI Project 

Overview 

This project showcases a complete end‑to‑end transformation and visualization workflow using Power BI.

Designed and implemented a full Power BI analytics dashboard to evaluate ClassicModels’ global sales performance. Processed and cleaned raw Excel/CSV datasets using Power Query, standardized data types, removed nulls, and created business-ready metrics (sales value, cost of sales, MOM%, YTD). Built intuitive visuals such as time-series trends, product-line analysis, and regional comparisons. This project demonstrates strong skills in Power BI, DAX, data modeling, and end-to-end BI reporting.

Starting from a raw Excel dataset (carsalesdataset.xlsx), the data was cleaned, transformed, and modeled in Power Query and finally exported as a refined dataset named classicmodels_sales_report_for_power_bi for creating interactive dashboards. 

The dashboard visualizes key business metrics such as: - Total Sales Value - Year‑to‑Date (YTD) Sales - Month‑over‑Month (MoM%) Growth - Top Product Lines - Country‑wise Sales Performance - Office‑wise Sales Distribution - Profitability (Sales vs. Cost of Sales) 

Data Cleaning & Transformation (Power Query) 

The following steps were performed: 

Changed column data types 

Removed null or invalid rows 

Standardized date format 

Created new calculated fields: 

sales_value = priceEach * quantityOrdered 

cost_of_sales = buyPrice * quantityOrdered 

Saved cleaned table as: 

classicmodels_sales_report_for_power_bi 

 

Measures Used (DAX) 

1. Month-over-Month % Growth 

sales_value MoM% = 
IF( 
   ISFILTERED('classicmodels sales_report_for_power_bi'[orderDate]), 
   ERROR("Time intelligence quick measures can only be grouped or filtered by the Power BI-provided date hierarchy or primary date column."), 
   VAR __PREV_MONTH = 
       CALCULATE( 
           SUM('classicmodels sales_report_for_power_bi'[sales_value]), 
           DATEADD( 
               'classicmodels sales_report_for_power_bi'[orderDate].[Date], 
               -1, 
               MONTH 
           ) 
       ) 
   RETURN 
       DIVIDE( 
           SUM('classicmodels sales_report_for_power_bi'[sales_value]) - __PREV_MONTH, 
           __PREV_MONTH 
       ) 
) 
 

2. Year‑to‑Date (YTD) Sales 

sales_value YTD = 
IF( 
   ISFILTERED('classicmodels sales_report_for_power_bi'[orderDate]), 
   ERROR("Time intelligence quick measures can only be grouped or filtered by the Power BI-provided date hierarchy or primary date column."), 
   TOTALYTD( 
       SUM('classicmodels sales_report_for_power_bi'[sales_value]), 
       'classicmodels sales_report_for_power_bi'[orderDate].[Date] 
   ) 
) 
 

 

Visualizations Included 

These visuals were created in the Power BI report: 

Bar chart: Sales by product line 

Line chart: Monthly sales trend 

KPI cards: Total Sales, YTD Sales, MoM % 

Map visual: Country‑wise sales 

Stacked bar: Sales by office location 

Table visual: Detailed order summary 

 

How the Dashboard Helps 

This dashboard provides business insights such as: 

Which product lines generate the most revenue 

How sales are trending over months 

Country and office performance 

Month‑over‑month growth patterns 

High‑value customers and products 

 

 
