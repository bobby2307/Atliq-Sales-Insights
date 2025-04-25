# Atliq-Sales-Insights
This Power BI dashboard analyzes sales data across different markets, customers and products

## Technologies Used:
- **Power BI** – For data visualization and dashboard creation
- **MySQL** – As the backend data source
- **DAX & Power Query** – For data transformation and modeling

## Key Insights:
- Total Revenue: ₹984.81M
- Total Sales Quantity: 2M units
- Delhi NCR leads both in revenue and sales quantity
- Electricalsara Stores is the top customer (₹413.33M revenue)
- A large portion of revenue is from unspecified products ("Blank")



# Data Analysis Using SQL
Show all customer records

`SELECT * FROM customers;`

Show total number of customers

`SELECT count(*) FROM customers;`

Show transactions for Chennai market (market code for chennai is Mark001

`SELECT * FROM transactions where market_code='Mark001';`

Show distrinct product codes that were sold in chennai

`SELECT distinct product_code FROM transactions where market_code='Mark001';`

Show transactions where currency is US dollars

`SELECT * from transactions where currency="USD"`

Show transactions in 2020 join by date table

`SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;`

Show total revenue in year 2020,

`SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";`

Show total revenue in year 2020, January Month,

`SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");`

Show total revenue in year 2020 in Chennai

`SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001";`

## Dashboard Features:
- Revenue trends from 2017 to 2020
- Revenue & Sales Qty by market
- Top 5 customers and products by revenue

- `dashboard_screenshot.jpg`
-  ![Screenshot 2025-04-25 132559](https://github.com/user-attachments/assets/8abdec47-9608-4425-9e6b-751c8f348fee)


Data Analysis Using Power BI
Formula to create norm_amount column

`= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)`

