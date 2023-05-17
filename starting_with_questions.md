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

    create view category_data as 
    select 
	ase.city, 
	regexp_substr(ase.productcategory, '[^/]+',1,2) as categorynatype,
	count(ase.productcategory) as ordered_num	
	from all_sessions ase
	where city !='(not set)' and productcategory != '(not set)'
	group by ase.city, ase.productcategory
	order by ase.city;
    
    
    
    
    create view category_data_country as 
    select 
	ase.country, 
	regexp_substr(ase.productcategory, '[^/]+',1,2) as categorynatype,
	count(ase.productcategory) as ordered_num	
	from all_sessions ase
	where country !='(not set)' and productcategory != '(not set)'
	group by ase.country, ase.productcategory
	order by ase.country;



Answer:





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:



Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







