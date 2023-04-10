What are your risk areas? Identify and describe them.

There are many risk areas in the dataset. Many of our calculations for city and country have data that has missing values that we are not able to include in calculations. We run the risk of incomplete columns from revenue. There may be duplicate rows in the database. 


QA Process:

QA1 - Is the revenue column complete? 

Query 1 :Creates table with units_price and unit_sold and calculates if revenue is equal to this amount.
```SQL
SELECT unit_price, units_sold, 
Unit_price * Units_sold AS testrev, 
revenue
FROM analytics
WHERE revenue IS NOT null
```


Query 2: Create table that shows difference of revenue and the (unit_price * units_sold)
```SQL
SELECT unit_price, 
units_sold, 
testrev, 
revenue, 
testrev - revenue as difference
FROM (
    SELECT unit_price, units_sold, unit_price * units_sold as testrev, revenue
    FROM analytics
    WHERE revenue IS NOT NULL
) AS subquery
```

Query 3: Search for other columns that may calculate for the difference in the numbers of revenues and units sold
```SQL
Select 
unit_price, 
units_sold, 
Unit_price * Units_sold as testrev,  
revenue                           --Alter this code to add any lines from all_sessions that may account for change    
from analytics
JOIN all_sessions as als
ON als.visitid = analytics.visitid
where revenue is not null
```
Answer: Revenue is often off by $3 or $2 in most cases. There are also many cases where revenue is off by much more. There are no other columns in all_sessions that can explain this difference. 

Conclusion: Either revenue or the unit_price and units_sold cannot be relied upon for exact amounts. 

QA2 - Do the city’s in dataset have accurate countries? 


Query 1: Spot check Los Angeles

```SQL
select * from all_sessions
where city = 'Los Angeles'
AND country != 'United States'
```

Answer: Los Angeles has Australia listed as country in one row. There may be many other errors.




