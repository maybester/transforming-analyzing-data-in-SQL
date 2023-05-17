Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**

Assumptions: since the transaction revenue is not explained by the data, thus i assume the column totaltransactionrevenue --88 rows of data will be used for indicating the transaction revenue.

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


Answer: country with highest level of transaction revenue is America,  while the city with highest level is San Francisco




**Question 2: What is the average number of products ordered from visitors in each city and country?**

Assumptions: since there are duplicate values in productsku in table all_sessions, thus decided to map the unitsold through visitor ids in analytics table.

SQL Queries:

  	select 
    	sum(a.unit_sold)/count(a.visitid) as avgunitsold, 
    
   	sum(a.unit_sold) as totalunitsold, 
    
    count(a.visitid) as orderedvisitor, ase.city
    
    from analytics a 

    join all_sessions ase

    on ase.visitid = a.visitid

    where a.unit_sold is not null and city not like '%available%'
    group by ase.city

    order by avgunitsold desc;

    select 
    sum(a.unit_sold)/count(a.visitid) as avgunitsold,
    
    sum(a.unit_sold) as totalunitsold, 
    
    count(a.visitid) as orderedvisitor, ase.country
    
    from analytics a 

    join all_sessions ase

    on ase.visitid = a.visitid

    where a.unit_sold is not null and city not like '%available%'

    group by ase.country

Answer: chicago has the highest avg number of products ordered from visitors which is 5 products per visitor, while visitors from pittsburg avergely ordered 4 products per peroson, New York maintain 3 products per pserson.
 ![image](https://github.com/maybester/transforming-analyzing-data-in-SQL/assets/73912419/1f58b8b2-f0c9-47f1-bcd8-1750e71b98e4)
 ![image](https://github.com/maybester/transforming-analyzing-data-in-SQL/assets/73912419/70266098-5b22-4392-bf8e-ebf10fc19ea2)


**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:

  	with category_info as (
	select country as name,'country'as type, productcategory, avg(p.orderedquantity) as avgorderedproducts
	from all_sessions aes
	join products p on p.sku = aes.productsku
	group by country, productcategory
	union 
	select city as name,'city'as type, productcategory, avg(p.orderedquantity) as avgorderedproducts
	from all_sessions aes
	join products p on p.sku = aes.productsku
	group by city, productcategory
	)

	select name, type, productcategory,avgorderedproducts
	from category_info
	where type ='country'
	order by avgorderedproducts desc
	limit 5;


Answer:

<img width="603" alt="image" src="https://github.com/maybester/transforming-analyzing-data-in-SQL/assets/73912419/e0e6d18c-e5b3-470a-ac2c-efbc60e3f05b">
<img width="608" alt="image" src="https://github.com/maybester/transforming-analyzing-data-in-SQL/assets/73912419/17b4c5d8-e95c-4ccf-a76f-f30bc10f5737">


**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:



Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

issues: large amount of missing data found in revenue column, which results in unable mathch of ids and the missing values in the total revenue for country and city in total.

SQL Queries:

	select sum(ana.revenue) as total_revenue, aes.city from analytics ana

	join all_sessions aes

	on aes.fullvisitorid = ana.fullvisitorid

	where aes.city !='(not set)' 

	group by aes.city

	order by total_revenue desc

	limit 5
	
	
	select sum(ana.revenue) as total_revenue, aes.country from analytics ana

	join all_sessions aes

	on aes.fullvisitorid = ana.fullvisitorid

	where aes.country !='(not set)' 

	group by aes.country

	order by total_revenue desc

	limit 5



Answer:

<img width="238" alt="image" src="https://github.com/maybester/transforming-analyzing-data-in-SQL/assets/73912419/86399fa7-19ce-4247-af30-29785a4c9807">
<img width="242" alt="image" src="https://github.com/maybester/transforming-analyzing-data-in-SQL/assets/73912419/fd115c30-0049-43a9-be5e-345554f6d620">








