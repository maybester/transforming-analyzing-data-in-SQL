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
#### Answer: United States is the country with the highest level of transaction revenue, Mountain View is the city with the highest level of transaction level.

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

Order quantity in table products is representing the total ordered amount of each sku (product type) while the units_sold is representing the ordered amount by each individual. thus we use units_sold for representing the number of products ordered instead orderedquantity. Meanwile, in product quantity of all_sessions table contains only 53 rows of data, thus we would like to use units_sold (95147 rows).

```
select * from all_sessions where productquantity is not null -- Return 53 rows of data.

select * from analytics where units_sold is not null -- Return 95147 rows of data
```


#### Answer:  San Bruno is the city with the highest average number of products from visitors, United States is the country with the highest average number of products from visitors.
```
-- Return top 5 cities with the highest average number of products ordered from visitors

select als.city, round(avg(a.units_sold),2) as avgproductordered
from all_sessions als
join analytics a on a.fullvisitorid = als.fullvisitorid
where units_sold is not null and city not in('(not set)','not available in demo dataset')
group by city
order by avgproductordered desc
limit 10


-- Return top 5 countries with the highest average number of products ordered from visitors

select als.city, round(avg(a.units_sold),2) as avgproductordered
from all_sessions als
join analytics a on a.fullvisitorid = als.fullvisitorid
where units_sold is not null and city not in('(not set)','not available in demo dataset')
group by city
order by avgproductordered desc
limit 10
```  

### Question #3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?

To study the pattern in the types of products ordered, we used product category to investigate the search path of visitors and product name for the exact product that visitors purchased. 

#### answer: The product with highest average number ordered by visitors among all the cities and countries is Google Kick Ball and is listed under category sports&fitness and fun.  
```
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
#### answer: The product with highest ordered amount is Nest® Cam Indoor Security Camera of the nest category in city mountain view but kicking ball is still the highest ordered amount in USA.
```
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

#### answer: Waze Baby on Board Window Decal is the top selling product in city mountain view and also is the most selling product among all the cities. Meanwile, Waze Baby on Board Window Decalis also the the top selling product in USA and is the most selling product among all the other counties listed.

```
-- top selling peoduct in each city

with added_row_number as (select als.city, als.productname,sum(a.units_sold) as totalproductordered, 
	row_number() over(partition by city order by sum(a.units_sold) desc)as row_number
from all_sessions als
join analytics a on a.fullvisitorid = als.fullvisitorid
where units_sold is not null and city not in('(not set)','not available in demo dataset')
group by city,productname
order by totalproductordered desc)

select * from added_row_number where row_number =1

-- top selling product in each country

with added_row_number_countryas as ( select als.country, als.productname,sum(a.units_sold) as totalproductordered,
	row_number() over(partition by country order by sum(a.units_sold) desc) as row_number
from all_sessions als
join analytics a on a.fullvisitorid = als.fullvisitorid
where units_sold is not null and city not in('(not set)','not available in demo dataset')
group by country,productname
order by totalproductordered desc)

select * from added_row_number_countryas where row_number = 1
```

### Question #5: Can we summarize the impact of revenue generated from each city/country?

#### answer: Mountain View has the biggest impact on generating the revenue among all the cities, and USA has the biggest impact on generating the revenue among all the countries.

'''
select city, sum(a.revenue) as total_revenue from all_sessions als
join analytics a on a.fullvisitorid = als.fullvisitorid
where a.revenue is not null and city not in ('not available in demo dataset', '(not set)')
group by city
order by total_revenue desc

select country, sum(a.revenue) as total_revenue from all_sessions als
join analytics a on a.fullvisitorid = als.fullvisitorid
where a.revenue is not null
group by country
order by total_revenue desc

'''





