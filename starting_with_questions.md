Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:

select sum(totaltransactionrevenue) as transaction_revenue, country, city from all_sessions

where totaltransactionrevenue is not null and city not like '%available%' 

group by country, city

order by transaction_revenue desc

limit 1

select sum(totaltransactionrevenue) as transaction_revenue, city from all_sessions

where totaltransactionrevenue is not null and city not like '%available%'

group by city

order by transaction_revenue desc

limit 1


Answer: country with highest level is America, city with highest level is San Francisco




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:



Answer:





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:



Answer:





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:



Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







