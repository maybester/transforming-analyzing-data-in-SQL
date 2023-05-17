What issues will you address by cleaning the data?





Queries:
Below, provide the SQL queries you used to clean your data.

--convert unitcost in table analytics to maintain data accuracy

update analytics set unitprice = unitprice * .000001;

--remove duplicate values across columns visitid and visitstarttime in talbe analytics

select * from analytics where visitid=visitstarttime;
alter table analytics drop visitstarttime;
