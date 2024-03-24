# Supply Chain Analytics

## Table of Content
* [Introduction](#introduction)
* [Entity Relationship Diagram](#entity-relationship-diagram)
* [Tools](#tools)
* [Methodology](#methodology)
* [Data Cleansing and Manipulation](#data-cleansing-and-manipulation)
* [DAX Measures and Calculated Columns](#dax-measures-and-calculated-columns)
* [Final Data Model](#final-data-model)
* [Insights](#insights)
* [Live Dashboard Link](https://app.powerbi.com/view?r=eyJrIjoiY2YyZjYzMWMtYzU5OC00NjdhLTk0NTgtYWFjZjgxN2I5ZTg5IiwidCI6ImRmODY3OWNkLWE4MGUtNDVkOC05OWFjLWM4M2VkN2ZmOTVhMCJ9)

## Introduction
The purpose of this dashboard is to provide a comprehensive view of the entire supply chain by merging data from various sources, including Revenue, Warehousing, and Product-related information.

## Entity Relationship Diagram
### The initial data model

![image](https://github.com/ritusantra/Power-BI-Projects/assets/75059347/2eb1dda0-43bb-411b-88a8-0086d770d188)


## Tools
* Microsoft Power BI

## Methodology
* Data cleaning and manipulation was performed on the data in the Power Query.
* Defined KPIs based on Revenue, Warehouse and Products using DAX.
* Created visuals to present the insights from data.

## Data Cleansing and Manipulation


## DAX Measures and Calculated Columns
### Calculated Columns in Sales Table
1. ```Days to Deliver``` = DATEDIFF(Sales[Ship Date],Sales[Delivery Date],DAY)
2. ```Days to Ship``` = DATEDIFF(Sales[OrderDate],Sales[Ship Date],DAY)
3. ```Order Year``` = YEAR(Sales[OrderDate])

### Calculated Table
1. **Slicer** ```Top N``` = {1,2,3,4,5}
2. **Pseudo Product** ```Product Name``` = UNION(DISTINCT(Products[Product Name]), DATATABLE("Product",STRING,{{"Others"}}))
3. **Date** ```Date``` = CALENDAR(DATE(2017,01,01),DATE(2020,12,31))

### Measures
1. ```Revenue``` = SUMX(Sales,Sales[Order Quantity]*Sales[Unit Price])
2. ```Cost``` = SUMX(Sales,Sales[Order Quantity]*Sales[Unit Cost])
3. ```Profit``` = [Revenue] - [Cost]
4. ```Profit %``` = [Profit]/[Revenue]*100
5. ```Warehouses``` = DISTINCTCOUNT(Warehouses[Warehouse Index])
6. ```Total Transactions``` = COUNTROWS(Sales)
7. ```Average Ship Time```= AVERAGE(Sales[Days to Ship])
8. ```Average Delivery Time``` = AVERAGE(Sales[Days to Deliver])
9. ```Products``` = DISTINCTCOUNT(Products[Index])
10. ```Average Order Quantity``` = AVERAGE(Sales[Order Quantity])
11. ```Average Price of Product``` = AVERAGE(Sales[Unit Price])
12. ```Average Cost of Product``` = AVERAGE(Sales[Unit Cost])

13. 
```Top N Products``` = 
Var TopNSelected = SELECTEDVALUE(Slicer[Top N])
Var TopProdTable = TOPN(TopNSelected,ALLSELECTED('Pseudo Product'),[Revenue])

Var TopProdSales = CALCULATE([Revenue],KEEPFILTERS(TopProdTable))

Var OthersSales = CALCULATE([Revenue],ALLSELECTED('Pseudo Product')) - CALCULATE([Revenue],TopProdTable)

Var CurrentProd = SELECTEDVALUE('Pseudo Product'[Product Name])

Return if (CurrentProd <> "Others", TopProdSales, OthersSales)

14. 
```Rank Products``` = 
IF([Top N Products] <> BLANK(),
RANKX(TOPN(SELECTEDVALUE(Slicer[Top N]), ALLSELECTED('Pseudo Product'[Product Name]),[Revenue]),[Revenue],,DESC,Dense))

15.
```Dynamic Title``` = 
Var TopProd = CALCULATE([Revenue],
TOPN(SELECTEDVALUE(Slicer[Top N]),
ALLSELECTED('Pseudo Product'[Product Name]),[Revenue]))

Var TopProdPrect = DIVIDE(TopProd,[Revenue])

Return "Top " & SELECTEDVALUE(Slicer[Top N]) & " Products Made " & FORMAT(TopProdPrect,"#.#%") & " of Revenue"

## Final Data Model
![image](https://github.com/ritusantra/Power-BI-Projects/assets/75059347/1a4b0b51-51b6-40e6-b2b2-af5db58f194c)

## Insights
* About 53% of total revenue generated is from Wholesale and about 14% is from Export.
* Profit % from Export is higher than the over all Profit %.
* Quebec is the highest revenue generating and the most profitable province.
* Sainte-Marguerite-du-Lac-Masson is the highest revenue generating city.
* There's an drop in the overall profit % in 2020. This could be due to the global pandemic. But there's increase in profit % from Distributor channel in 2020.
* Total transactions in Sainte-Marguerite-du-Lac-Masson is the highest for all of the past 3 years.
* The Average Ship Time and Average Delivery Time are above average for Sainte-Marguerite-du-Lac-Masson. This could be due to the large volume of transactions.
* Whenever the Average Ship Time and Average Delivery Time are above average it will be indicated by the Red Arrow to keep a track of timings.
* The total transactions gradually increased over the year, which represents that there's a steady growth in the revenue.
* Compared to 2018, in 2019, the transactions per warehouse increased steadily.
* The average cost and price of the products are effected due to the global pandemic in 2020.
