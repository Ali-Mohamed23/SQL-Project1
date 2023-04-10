What issues will you address by cleaning the data?

- I will look for any duplicate rows and remove them
- I can make sure columns will make sense. 
- All revenue columns have been multiplied by 1 million, So I will alter the column by dividing all values by 1 million.





Queries:

Query: To alter product price column so that it is divided by 1 million.
```SQL
ALTER TABLE all_sessions 
ALTER COLUMN productprice 
TYPE double precision USING productprice/1000000
```
Query: To alter the revenue column to divide by 1 milllion. 
```SQL
ALTER TABLE analytics 
ALTER COLUMN revenue 
TYPE double precision USING revenue/1000000
```

Query: To find duplicate rows. 

```SQL
SELECT fullvisitorid, COUNT(*) as count 
FROM all_sessions
GROUP BY fullvisitorid
HAVING COUNT(*) > 1;

SELECT COUNT(*) FROM all_sessions WHERE fullvisitorid IS NULL
```

Answer: no null

Query: Check the usefulness of the totaltransaction column. 
```SQL
SELECT COUNT(*) FROM all_sessions WHERE totaltransaction IS NOT NULL
SELECT COUNT(*) FROM all_sessions WHERE totaltransaction IS NULL
```

Result: totaltransaction column has 81 values that are not null

It has 15053 values that are null 

Do not delete 


```SQL
SELECT COUNT(*) FROM all_sessions 
WHERE sessionqualitydim IS NOT NULL
```

Answer: 1228

Do not delete.

Query: Check if searchkeyword is useful.
```SQL
SELECT COUNT(*) FROM all_sessions WHERE searchkeyword IS NOT NULL
```
Answer: Drop column

```SQL
Alter Table all_sessions
DROP COLUMN itemquantity 
```

Query:
```SQL
select itemquantity from all_sessions
where itemquantity is not null
```
Answer: The answer is all null so this column can get deleted

Query: Delete itemquantity and itemrevenue
```SQL
ALTER TABLE all_sessions 
DROP COLUMN itemquantity

ALTER TABLE all_sessions 
DROP COLUMN itemrevenue
```

