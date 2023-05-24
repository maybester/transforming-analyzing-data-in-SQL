## Part 1: Data Cleaning

> cleaning_data.md file
> * Fill out this file with a description of the issues that will be addressed by cleaning the data
> * Include the queries used to clean the data


Issue #1: The unit cost in the data needs to be divided by 1,000,000.

```
update analytics
set unit_price = unit_price/1000000;
```

Issue #2: Identify columns only contain null values and consider to drop.

```
select count(*) from all_sessions where itemquantity is not null
select count(*) from all_sessions where itemrevenue is not null
select count(*) from all_sessions where searchkeyword is not null

--all return 0 

alter table all_sessions
drop column itemquantity;

alter table all_sessions
drop column itemrevenue;

alter table all_sessions
drop column searchkeyword;
```

Issue #3: Explore dulicate values in analytics and all_sessions.

```
select visitid, count(visitid) 
from all_sessions 
group by visitid 
having count(visitid)>1;
--return 553 rows of duplicates in visitid

select fullvisitorid, count(fullvisitorid) 
from all_sessions 
group by fullvisitorid 
having count(fullvisitorid)>1;
--return 794 rows of duplicates in fullvisitorid

```
Since duplicate values exist in fullvisitorid and visitid, primary key cannot be defined in both analytics and all_sessions tables.
