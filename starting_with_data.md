Question 1: Which months receive the most revenue ?

SQL Queries:

SELECT EXTRACT(MONTH FROM date) as month, SUM(revenue) as revenue
FROM Analytics
GROUP BY EXTRACT(MONTH FROM date)


Answer: From this query the result I got was that revenue was only received in May, June, July, and August; $357,152, $372,856 , 411,000 and $19564 respectively. 



Question 2: What is the average time on site for each of the products ordered?

SQL Queries:

SELECT sr.name, sr.total_ordered, AVG(als.timeonsite) AS average_timeonsite
FROM sales_report sr
JOIN all_sessions als 
ON sr.productsku = als.productsku
GROUP BY sr.name, sr.total_ordered
having sr.total_ordered != 0
order by average_timeonsite desc

Answer:



Question 3: How many times has someone visited the site more than once?

SQL Queries:

SELECT fullvisitorid, COUNT(DISTINCT visitid) AS num_visits
FROM analytics
GROUP BY fullvisitorid
HAVING COUNT(DISTINCT visitid) > 1
order by num_visits desc


Answer: 
More than once = 17233
More than twice = 5933
More than 3 times = 2763
More than 10 times = 137 
Top 10 visitors = between 27 and 71 visits





