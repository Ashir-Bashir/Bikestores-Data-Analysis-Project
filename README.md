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
This data analysis project was created to unveil the sales performance of a theoretical bicycle retail company from 2016 to 2018. Through a comprehensive analysis of diverse sales data facets, my aim is to pinpoint trends, derive data-driven insights, propose recommendations, and attain a profound comprehension of the company's overall performance. The strategic extraction of data using SQL was meticulously executed to guarantee precision. Following this, the design phase seamlessly integrated Excel and Tableau, resulting in a dynamic and visually captivating dashboard.

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
   
4. Visual Checking for Data Quality

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

1. Revenue Trends:
Revenue increased by $1,136,030.55 from 2016 to 2017 but decreased by $1,821,525.63 from 2017 to 2018. The lowest revenue was observed in 2018.

2. Monthly Revenue:
The highest revenue months were September 2016, June 2017, and April 2018. However, a significant drop in revenue occurred in June 2018.

3. Total Units and Customers:
Total units sold increased by 436 from 2016 to 2017 but dropped significantly by 1,783 from 2017 to 2018. The number of customers increased by 57 in 2017 but decreased by 414 in 2018.

4. Bike Sales by Store and Brand:
Baldwin Bikes store consistently led in bicycle sales, while Rowlette store consistently reported the lowest sales throughout the three-year period from 2016 to 2018. Additionally, Trek was the most popular brand, and Ritchey was the least popular across the three years.

5. Bike Category Insights:
Mountain bikes were the most popular, generating the highest revenue, while Children's bicycles were the least popular and generated the lowest revenue. The shift from Mountain bikes to Road bikes in 2018 suggests a potential change in customer preferences.

6. Revenue by State:
New York City generated the most revenue from 2016 to 2018, followed by California and Texas. Focusing efforts and tailoring services to customers in NYC could be beneficial.

7. Sales Representatives Performance:
Boyer and Daneil were the highest revenue-earning sales reps, while Vargras and Terell performed at a lower level. Investigating the reasons behind underperformance is recommended.

8. Top Customers:
The top revenue-generating customers varied each year, indicating changing preferences. Investigating why some customers are not returning is crucial, considering factors like product preferences, alternative transport options, and changing buying behaviors.

### Recommendations
Based on the analysis, I woudld recommend the following actions:
1. Revenue Downturn Analysis:
Investigate the reasons for the significant revenue decrease in 2018 to identify potential issues affecting sales.

2. Customer Retention Strategies:
Implement strategies to understand why certain customers are not returning, considering changes in preferences and the emergence of alternative transportation options like electric scooters.

3. Product Focus:
Shift focus towards adult categories of bicycles, as evidenced by the decline in popularity of children's bicycles. This aligns with the shift from Mountain bikes to Road bikes.

4. Sales Representative Performance:
Conduct a thorough analysis of underperforming sales reps (Vargras and Terell) to identify areas for improvement or additional support.

5. Adapt to Changing Trends:
Stay informed about changing customer preferences and market trends, adjusting product offerings and marketing strategies accordingly.

6. Tailored Services in Key States:
Tailor services and marketing efforts to customers in high-revenue-generating states, particularly New York City.

7. Regular Customer Insights:
Establish mechanisms to regularly gather insights into customer preferences, purchasing behaviors, and satisfaction to adapt the business strategy accordingly.

8. By addressing these findings and implementing the recommended strategies, the bicycle company can enhance its overall performance and adapt to the dynamic market landscape.

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




