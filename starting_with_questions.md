Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries: 

select                                      
a.country,                          -- Select the countries
a.city,                             -- Select the city
Sum(al.revenue) AS City_Revenue     -- Get the sum of the revenue from the analytics table
from analytics al                   -- Identify table
join all_sessions a                 -- JOIN the all_sessions table 
on al.visitid=a.visitid             -- Identify how tables are related through visitID
where al.units_sold >= 1            -- Only show values where there was revenues
And a.transactions is not null      -- Make sure there is transaction that occured 
group by a.country, a.city          -- Sort these SUM of revenues by the country and city 
order by City_Revenue Desc          -- Show the highest revenues first 




Answer: All transaction revenues were in the United States (Sunnyvale $666, Seattle, San Fransisco, Chicago, Mountain view in descending order)  and Zurich Switzerland $16. *** These values were divided by 1 million in the revenue column from original dataset***




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries: 

SELECT  
country,
city,
Avg(total_ordered) AS average_quantity_ordered              -- Get the average of total orders from the sales_report table
FROM all_sessions AS a                                      
JOIN sales_report as sr                                     -- Join sales report table 
on a.productsku=sr.productsku                               -- Identify relationship between sales_report table and all_sessions
WHERE (
country IS NOT NULL                                         -- Only calculate for the orders that have country filled in
AND city IS NOT NULL                                        -- Only calculate for the orders that have city filled in
AND sr.productsku IS NOT NULL                               
AND sr.total_ordered IS NOT NULL
AND country != 'not available in demo dataset' and country!='(not set)'         -- Only calculate for the orders that have country filled in
AND city != 'not available in demo dataset' and city!='(not set)'               -- Only calculate for the orders that have city filled in
)
GROUP BY country, city                                                          -- Calculate average orders by country and city 
ORDER BY average_quantity_ordered desc, country, city                            -- Display them with average order quantity first




Answer: Riyadh has the largest average order quantity at 319, Hong Kong  and Czechia come next. Although average order quantity is high this may 
may not be many orders. 





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries: 

SELECT 
country, 
city, 
all_sessions.v2productcategory,                             -- show product categorys
SUM(sales_report.total_ordered) as total_ordered_sum        -- Get the sum of the total_ordered on a column
FROM all_sessions
JOIN sales_report                                           -- Join sales report table 
ON all_sessions.productsku = sales_report.productsku        -- Connect relation with sales report table 

WHERE (                                                     -- For the where remove null or not set values for city and country 
country IS NOT NULL
AND city IS NOT NULL
AND sales_report.productsku IS NOT NULL
AND sales_report.total_ordered IS NOT NULL
AND sales_report.total_ordered != 0
AND country != 'not available in demo dataset' and country!='(not set)'
AND city != 'not available in demo dataset' and city!='(not set)'
AND v2productcategory != '(not set)'                        -- Do not include any product categories that are not set
)

GROUP BY all_sessions.v2productcategory, country, city     -- Sum of orders is based on categories in each city or country 

order by country, total_ordered_sum desc, v2productcategory   -- Display in order by countries




Answer:: I moved around the order by to look for patterns, 1220 rows, - USA, Mountain view - Home/Nest/Nest-USA had 5876 orders and 2826 orders





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:



Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







