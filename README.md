# TABLEAU ATLIK HARDWARE SALE'S ANALYSIS
 
 
 
 # Problem Statement
 
AtliQ Hardware supplies hardware to various clients, with its head office in Delhi, India and regional offices across the country. Bhavin Patel is the sales director in charge of the head office.

Bhavin noticed declining sales, but tracking sales data was difficult due to the many branches and regional managers who presented a rosy picture of the business. He turned to data analytics to gain insights into the sales data, which will help the company make informed decisions. This proactive step towards enhancing sales performance is expected to yield positive results for the company.

# Data Discovery
In this project, the process begins with the IT team entering data into the Sales Management System via the MySQL database. The data is then transformed into an automated dashboard by the data analyst team. The process is designed to be simple and efficient, ensuring that data is readily available for analysis and decision-making purposes.


I will also explain the direction of this project using Aim’s grid:

# Purpose:
To unlock previously unseen sales insights to assist sales team decision making & automate insights to reduce time spent on data collection.

# Stakeholders:
Sales and marketing team, IT team and data analytics team.

# End Result:
An automated dashboard that provides quick & up-to-date sales insights to support data-driven decision making.

# Success Criteria:
The sales dashboard provides sales order insights using the most recent data available. The sales team can utilize these insights to make informed decisions and potentially reduce costs by 10% of total expenses. Additionally, sales analysts no longer have to manually collect data, saving them 20% of their business time, which can be redirected towards value-added activities. Overall, the dashboard is an effective tool that promotes efficiency and productivity in sales-related activities.


# Data Analysis Using SQL

I used MySQL Workbench to analyze the data first before doing ETL (Extract-Transform-Load) via Tableau. I have several table, consisting of 1 fact table, transactions, and 4 dimension tables, customers, date, markets, and products.


1.	Show all customer records
SELECT * FROM customers;
2.	Show total number of customers
SELECT count(*) FROM customers;
3.	Show transactions for Chennai market (market code for chennai is Mark001
SELECT * FROM transactions where market_code='Mark001';
4.	Show distrinct product codes that were sold in chennai
SELECT distinct product_code FROM transactions where market_code='Mark001';
5.	Show transactions where currency is US dollars
SELECT * from transactions where currency="USD"
6.	Show transactions in 2020 join by date table
SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;
7.	Show total revenue in year 2020,
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";
8.	Show total revenue in year 2020, January Month,
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");
9.	Show total revenue in year 2020 in Chennai
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001";
Data Analysis Using Power BI
1.	Formula to create norm_amount column
= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)


