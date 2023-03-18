# TABLEAU ATLIK HARDWARE SALE'S ANALYSIS
 
 
 
 # Problem Statement
 
AtliQ Hardware supplies hardware to various clients, with its head office in Delhi, India and regional offices across the country. Bhavin Patel is the sales director in charge of the head office.

Bhavin noticed declining sales, but tracking sales data was difficult due to the many branches and regional managers who presented a rosy picture of the business. He turned to data analytics to gain insights into the sales data, which will help the company make informed decisions. This proactive step towards enhancing sales performance is expected to yield positive results for the company.

# Data Discovery
In this project, the process begins with the IT team entering data into the Sales Management System via the MySQL database. The data is then transformed into an automated dashboard by the data analyst team. The process is designed to be simple and efficient, ensuring that data is readily available for analysis and decision-making purposes.



Data Analysis Using SQL
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


