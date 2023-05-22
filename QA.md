## Part 4: Quality Assessment

>QA.md file
>
>* Identify and describe your risk areas
>* Develop and execute a QA process to address the risk areas identified, providing the SQL queries used to implement

### What are your risk areas? Identify and describe them.
| Risk area  | description |
| ------------- | ------------- |
| data source quality  | data source contained missing values and affect data consistency and copleteness.|
| data relationship  | lack of documentation to explain the relationship between columns across different tables.  |
| data definition  | data type such as time is not defined in the data source, the units for numeric measurement are also undefined. |


### Data quality dimensions

#### Completeness

* replace missing values in numeric columns with value 0
```
select replace(null,null,0) as revenue from analytics
select replace(null,null,0) as totaltransactionrevenue from all_sessions
```
* drop columns only containing missing values
```
alter table all_sessions
drop column itemquantity;

alter table all_sessions
drop column itemrevenue;

alter table all_sessions
drop column searchkeyword;

```

#### Validity

* convert unit in columns units_price
```


```
* convert data type of time 
```

```

#### Accuracy

#### Timeliness
* check the order date to be in reasonable range

#### Consistency
* check the currency column


#### Uniqueness
* check and drop unnecessary duplicate values


