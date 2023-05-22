## Part 3: Starting with Data
>startingwithdata.md file
>
>* Provide the 3 - 5 new questions you decided could be answered with the data
>* Include the answer to each question and the accompanying queries used to obtain the answer

### Question #1: find the number of product orders in each month of 2017.

#### Answer: 
```
select extract(month from date) as month, extract(year from date) as year, count(*) 
from analytics 
where units_sold is not null 
group by extract(month from date),extract(year from date)
```
```
"month"	"year"	"count"
5	2017	29696
6	2017	27713
7	2017	36141
8	2017	1597
```
### Question #2: investigate the channel grouping type of each visitor that made an order on the wenbiste.

#### Answer:
```
select channelgrouping, count(*)*100.0/(select count(*)from analytics) as percentage 
from analytics 
where revenue is not null 
group by channelgrouping
```
```
"channelgrouping"	"percentage"
"Affiliates"	0.00041849545304690263
"Direct"	0.05312567278956514
"Display"	0.003464212361332694
"Organic Search"	0.07107447777579896
"Paid Search"	0.0124618646018411
"Referral"	0.21466491766566956
"Social"	0.0017902305491450834
```
### Question #3: find the visitor who made most number of orders on website.

#### Answer:
```
select visitid, count(*) 
from analytics 
where units_sold is not null 
group by visitid 
order by count(*) desc 
limit 10
```
```
"visitid"	"count"
"1501207944"	174
"1499951313"	172
"1500674987"	149
"1499458999"	139
"1498540914"	130
"1497970502"	111
"1493655700"	105
"1500915989"	102
"1494515095"	99
"1495182511"	98
```


