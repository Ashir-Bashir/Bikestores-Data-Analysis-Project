# Bikestores-Data-Analysis-Project

## Table of contents
1. [Project Overview](Project-Overview)
2. [Data sources](Data-sources)
3. [Tools](Tools)
4. [Data Cleaning/Preperation](Data-Cleaning/Preperation)
5. [Exploratory Data Analysis](Exploratory-Data-Analysis)
6. [Results/Findings](Results/Findings)
7. [Recommendations](Recommendations)
8. [References](References)
   
### Project Overview 
Created a Sales Dashboard for a theoretical bicycle retail company, the project enhanced data-driven decisions. It involved strategic SQL data extraction, ensuring accuracy. The subsequent design phase utilised Excel and Tableau for a dynamic, visually appealing dashboard.

![image](https://github.com/Ashir-Bashir/Bikestores-Data-Analysis-Project/assets/152665079/857993e9-09e6-4548-a7a9-2ed8be67195c)



### Data sources
BikeStores data: The primary data set used for this project is 'BikeStores.xlsx' containing detailed information about each sale made by the company.
### Tools
PostgresQL-Extracting data and aggregated data from multiple tables
Excel- Creating comprehensive Dashboard
Tableau- Creating comprehensive Dashboard
### Data Cleaning/Preperation
In the intial data preperation stage, i performed the following tasks:

1. Data loading and Inspection

2. Handling missing values

3. Data cleaning and formating

### Exploratory Data Analysis (EDA)
EDA involved exploring the sales data to answer key questions, such as:

-Analyze sales trends by region, store, product category, and brand from 2016 to 2018, emphasizing noteworthy fluctuations or patterns?

-Share revenue data per region, store, product category, and brand for 2016-2018 to enhance understanding of revenue distribution?

-Identify top customers and sales representatives from 2016 to 2018, and provide insights into their contributions to sales performance?

### Data Analysis
Interesting code/features I used: 

```sql
SELECT
	ord.order_id,
	CONCAT(cus.first_name,' ',cus.last_name)AS customers,
	cus.city,
	cus.state,
	ord.order_date,
	SUM(ite.quantity) AS total_units,
	SUM(ite.quantity*ite.list_price) AS revenue,
	pro.product_name, 
	cat.category_name,
	sto.store_name,
	CONCAT(sta.first_name,' ',sta.last_name) AS sales_rep
FROM sales.orders ord
JOIN sales.customers cus
ON ord.customer_id = cus.customer_id
JOIN sales.order_items ite
ON ord.order_id = ite.order_id
JOIN production.products pro
ON ite.product_id = pro.product_id
JOIN production.categories cat
ON pro.category_id = cat.category_id
JOIN sales.stores sto
ON ord.store_id = sto.store_id
JOIN sales.staffs sta
ON ord.staff_id = sta.staff_id
GROUP BY ord.order_id,
	CONCAT(cus.first_name,' ',cus.last_name),
	cus.city,
	cus.state,
	ord.order_date,
	pro.product_name,
	cat.category_name,
	sto.store_name,
	CONCAT(sta.first_name,' ',sta.last_name);
```
### Results/Findings
The analysis and results are summarised as follows:
1. The company's bike sales have been increasing from 2016 to 2017 peaking in 2017 before dropping significantly in 2018.

2. The baldwin store and the product category mountain bikes with the brand Trek was the best performing in terms of sales and revenue.

3. Newman and Boyer was the top customer and sales representative that generated the most revenue from 2016 to 2018 period.

### Recommendations
Based on the analysis, I woudld recommend the following actions:

- Invest in marketing and promotions during peak sale seasons to maximise revenue.
- 

### Limitations

1.	Time Constraints:
The analysis is limited to the specified timeframe (2016-2018). Emerging trends or changes post-2018 may not be captured, potentially affecting the relevance of insights.

2.	Assumption of Homogeneous Stores:
	If there is significant variation among stores in terms of size, location, or customer base, grouping them together may oversimplify the analysis and mask important nuances.

3.	Limited Contextual Information:
The provided SQL code focuses on quantitative metrics. Including qualitative data or additional contextual information could provide a more comprehensive understanding of sales dynamics.

4.	External Factors:
Economic fluctuations, industry trends, or external events could impact sales trends. The analysis may benefit from considering external factors influencing the bicycle retail market.

### References
1. SQL for businesses by werty

2. (Stack Overflow) [https://stack.com]

3. Dataset Guru




