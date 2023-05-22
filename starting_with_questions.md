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

### Question #3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?

To study the pattern in the types of products ordered, we used product category to investigate the search path of visitors and product name for the exact product that visitors purchased. 

```
-- The product with highest average number ordered by visitors is Google Kick Ball and is listed under category sports&fitness and fun.
-- The same situation happened both in cities and countries.

select als.city, als.productcategory, als.productname, round(avg(p.orderedquantity),2) as avgprooductordered
from all_sessions als
join products p on p.sku = als.productsku
where city != 'not available in demo dataset'
group by city, productcategory, productname
order by avgprooductordered desc
limit 5

select als.country, als.productcategory, als.productname, round(avg(p.orderedquantity),2) as avgprooductordered
from all_sessions als
join products p on p.sku = als.productsku
group by country, productcategory, productname
order by avgprooductordered desc
limit 10

```
```
-- The product with highest ordered amount is Nest® Cam Indoor Security Camera of the nest category in city mountain view but kicking ball is still the highest ordered amount in USA.

select als.city, als.productcategory, als.productname, sum(p.orderedquantity) as totalprooductordered
from all_sessions als
join products p on p.sku = als.productsku
where city not in ('not available in demo dataset', '(not set)')
group by city, productcategory, productname
order by totalprooductordered desc

select als.country, als.productcategory, sum(p.orderedquantity) as totalprooductordered
from all_sessions als
join products p on p.sku = als.productsku
group by country, productcategory
order by totalprooductordered desc

```

### Question #4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?




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







### Question #5: Can we summarize the impact of revenue generated from each city/country?

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








