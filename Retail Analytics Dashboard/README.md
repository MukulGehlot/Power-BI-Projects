
## Retail Analytics for an Online Retail Store 🛒📊

[Power BI Link](https://app.powerbi.com/view?r=eyJrIjoiZjkxZTk3MjUtYjRkNC00YTBlLWJiNzYtM2I2YzhhMWU4OWMyIiwidCI6ImRmODY3OWNkLWE4MGUtNDVkOC05OWFjLWM4M2VkN2ZmOTVhMCJ9)

### Overview
* Created a retail analytics dashboard to analyse the revenue trend and sales trends of an online retail store.
* The aim was to analyse the major contributing factors that led to revenue and sales growth, so the leadership team could strategically plan for next year.
* The dataset was in CSV format. After loading 5,00,000+ records of data; data cleaning and manipulation were performed on Power Query Editor.
* Based on the data, visualizations were created to represent the key insights in the form of clustered bar charts, clustered column charts, line charts, and maps.

### Business Scenario
An online retail store needs to review their data and provide insights that would be valuable to the CEO and CMO of the business. The business has been performing well and the management wants to analyse what the major contributing factors are to the revenue so they can strategically plan for next year.
The leadership is interested in viewing the metrics from both an operations and marketing perspective. They would also like to view different metrics based on the demographic information that is available in the data.

### Objective
To draft the relevant analytics and insights that would help evaluate the current business performance so they can strategically plan for next year.

### Data Cleaning

* Applied filter in **Quantity** column to filter out the values greater than or equal to 1.
* Applied filter in **UnitPrice** column to filter out only the values above 0.
* Removed null values of **CustomerID**.

### Calculated Column

Added calculated column **Revenue**<br>
Revenue = 'Online Retail'[Quantity]*'Online Retail'[UnitPrice] 

### Data Visualization

Based on the data, visualizations were created to represent the key insights in the form of clustered bar charts, clustered column charts, line charts, and maps.
