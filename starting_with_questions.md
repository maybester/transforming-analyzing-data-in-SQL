## Part 2: Starting with Questions

>startingwithquestions.md file
>
> * Provide the answer to the 5 questions and the queries used to answer each question
    
### Question #1: Which cities and countries have the highest level of transaction revenues on the site?

Transaction revenue is not defined in the table, we assume transaction revenue is equal to the price amount that customers paied for the products. Thus, we choose product price (15134 rows) to represent the transaction revenue instead total transaction revenue (81 rows).

```
select * from all_sessions where totaltransactionrevenue is not null -- Return 81 rows of data

select * from all_sessions where productprice is not null -- Return with 15134 rows of data

```
Answer: United States is the country with the highest level of transaction revenue, Mountain View is the city with the highest level of transaction level.

```
-- Top 5 cities with highest transaction revenues

select city, sum(productprice) as transaction_revenues
from all_sessions
where city != 'not available in demo dataset'
group by city
order by sum(productprice) desc
limit 5

-- Top 5 countries with highest transaction revenues

select city, sum(productprice) as transaction_revenues
from all_sessions
where city != 'not available in demo dataset'
group by city
order by sum(productprice) desc
limit 5

```

### Question #2: What is the average number of products ordered from visitors in each city and country?**

Quantity is the amount or numerical value, while the unit is the measurement, thus we use product quantity for representing the number of products ordered instead units sold. However, in product quantity of all_sessions table contains only 53 rows of data, thus we would like to use ordered quantity from table products (1092 rows).

```
select * from all_sessions where productquantity is not null -- Return 53 rows of data.

select * from products where orderedquantity is not null -- Return 1092 rows of data
```

For each order of same product type, there is a unique sku number to represent the order.
```
select * from products order by name
```
Answer: Council Bluffs is the city with the highest average number of products from visitors, United States is the country with the highest average number of products from visitors.
```
-- Return top 5 cities with the highest average number of products ordered from visitors

select als.city, round(avg(p.orderedquantity),2) as avgprooductordered
from all_sessions als
join products p on p.sku = als.productsku
group by city
order by avgprooductordered desc
limit 5

-- Return top 5 countries with the highest average number of products ordered from visitors

select als.country, round(avg(p.orderedquantity),2) as avgprooductordered
from all_sessions als
join products p on p.sku = als.productsku
group by country
order by avgprooductordered desc
limit 5
```  

### Question #3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


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


### Question #4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:

	select 
	sum(a.unit_sold) as totalunitsold, 

	ase.city
	
	from analytics a 

	join all_sessions ase

	on ase.visitid = a.visitid

	where a.unit_sold is not null and city not like '%available%'
	group by ase.city

	order by totalunitsold desc;

	select 
	sum(a.unit_sold) as totalunitsold, 

	ase.country

	from analytics a 

	join all_sessions ase

	on ase.visitid = a.visitid

	where a.unit_sold is not null and country not like '%available%'
	group by ase.country

	order by totalunitsold desc;




Answer:

<img width="746" alt="image" src="https://github.com/maybester/transforming-analyzing-data-in-SQL/assets/73912419/b64009dd-2e71-4e72-b97a-0054d28c82a1">




### Question #5: Can we summarize the impact of revenue generated from each city/country?**

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








