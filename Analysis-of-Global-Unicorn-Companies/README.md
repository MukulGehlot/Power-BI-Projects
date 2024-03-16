# Analysis of Global Unicorn Companies 🦄📊

A unicorn company is a private company with a valuation of more than $1 billion, and today there are over 1,000 unicorn companies around the world!

* This [dataset](https://www.mavenanalytics.io/blog/maven-unicorn-challenge) contains a csv table with 1,074 records, one for each company
* Each record contains details on the company's current valuation, total funding, country of origin, industry, select investors, and the years they were founded and became unicorns

Created a dashboard on Power BI to analyse the current landscape of unicorn companies around the globe. 

### Data Preprocessing

*	Data cleaning and data manipulation was done in order to handle missing data. The format of the data was changed for processing of the data.
*	Analysed the rows with missing City and dropped them.
*	Removed the duplicate entries of the Company.
*	Formatted the data type of Funding and Valuation.
*	Corrected the spelling mistake for Artificial Intelligence in Industry.
*	Investor column was split into four columns in order to have names of the investors in separate columns.
*	The year from Date Joined was extracted and new column Year Joined was added in order to calculate the Duration To Become Unicorn.

### Key Insights

*	There are 1054 Unicorn companies and it was analysed that most of the founded companies became a Unicorn in the year 2021. 
*	It takes about 7 years for a company to become Unicorn.
*	Bytedance, Shein, SpaceX are the top three companies by valuation.
*	Even though Bytedance is from Artificial Intelligence industry, FinTech industry is the top industry by valuation.
*	47.77% of the companies are from E-commerce & direct-to-consumer industry.
*	54.82% of the companies are from United States, majorly from San Francisco, New York City and Palo Alto. 30.52% of the companies are from San Francisco.

### Power BI Dashboard 

![image](https://i.imgur.com/tqR26mE.jpeg)
