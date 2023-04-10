# Final-Project-Transforming-and-Analyzing-Data-with-SQL

## Project/Goals
My goals for this project is to utilize the skills I have learned in week 1 so that I can extract, load, and transform the provided database. Furthermore, perform queries to answer questions. Lastly, perform quality assurance to validate these SQL queries. 

![alt text](pngtree-matrix-digital.jpeg)


## Process
Step 1: My first step was to download all the csv data files and create the ecommerce database in PostgreSQL.

Step 2: Create tables for all of the csv files with the correct data type.

Step 3: Load all of the data into PostgreSQL

Step 4: Get an understanding of the data and find out the meaning of each of the columns and tables. 

Step 5: Clean the data. In this step involved deleting duplicate rows, deleting unneccesary columns.

Step 6: Answering the questions in the starting_with_questions. This step included creating different queries and looking for the correct columns to use for the question being asked. 

Step 7: Review the data and look for useful information that can be extracted from it. This process included creating additional queries. 

Step 8: This step involved quality assurance to validate the SQL queries. In this step i looked at some of the columns I was using in my queries to validate them.

Step 9: Created an ERD for the database and loaded all of the files on to postgreSQL. This process involved using VScode in order to record all of my queries and files. Then using git commands to push the files on Github. 

## Results
- Transaction revenue was highest in the USA 
- Riyadh had the largest average order quantity (likely due to less overall orders)
- Did not identify pattern for product categories apart from many orders in Mountainview for Home/Nest/Nest-USA
- Indoor cameras are the top selling product in Mountain view, USA
- Mountain view was the city that has generated the most revenue at $10,439.
- USA was the country that generated most revenue 111,193 
- The site has been re-visited by people 17,233 times
- Revenue was only received in May, June, July, and August

## Challenges 
This project contained mainy challenges along the way which included:

- Loading the csv files, there was many issues with choosing the correct data types for each of the tables. I had to make adjustments after finally loading them since they still were not correct. For example for VisitID I was using numeric so that it could capture all of the digits, however VARCHAR would be the correct data type since this was not a numeric value but an identifier. 

- Understanding the data was very difficult. There were many of the same column names but finding out which was the unique identifier was a challenge. Also finding out what different revenue types meant, along with order_quantity. This was a very important step because the querys rely on choosing the correct columns. 

-  Writing the code was a challenge because the database contained a lot of information. 


## Future Goals

If I had more time I would spend a lot more time cleaning the data to ensure that it has the correct values. The dataset had a lot of missing information and this could effect the results of the queries. For future projects I will make sure I have a good understanding of the material before starting the project so there is less time reviewing processes. 
