What issues will you address by cleaning the data?





Queries:
Below, provide the SQL queries you used to clean your data.


> convert unitcost in table analytics to maintain data accuracy in table analytics

update analytics set unitprice = unitprice * .000001;

> remove duplicate values across columns visitid and visitstarttime in talbe analytics

select * from analytics where visitid=visitstarttime;
alter table analytics drop visitstarttime;

> remove duplicate values across rows visitid in table analytics

alter table analytics 
add surrogate_key serial primary key;
alter table analytics
add primary key (surrogate_key);

delete from analytics
where surrogate_key not in (
	select min(surrogate_key)
	from analytics
	group by visitid, fullvisitorid, unitprice
);

