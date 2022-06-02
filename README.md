# client-BBB-sales-data-analysis

it's a project done to analyze the sales data of BBB company, to definr some trends, KPIs, the main business metrics that may help the managers to make their decisions.

## Data Preparation:

The dataset of the project has 4 tables, one for the customers data, other for the division, another one for the regions, and the last is for the sales data, which we can consider to be our main table in the dataset.

- the date key had a problem as there was some columns with date 29/2/2009 which is wrong as 2009 isn’t a leap year, For fixing this problem, I changed the date to the nearest date to it which was 28/2/2009
- Then I loaded the dataset on power query to modify it by changing the type of some columns to their right data type
- Also I created a new derived table which contains the date key and sales amount to use it in calculating the “cumulative sales revenue”

## Data Processing:
for processing, i uploaded the data on power BI, where i used power query to make some transformations to the table to be ready to use in making the dashboard, then i used DAX to make new measures that would calculate some important things to show in the results obtained, like:
- Total number of orders (number of orders = DISTINCTCOUNT('Sales Table'[Order Number ]) )
- Net profit (net profit = SUM('Sales Table'[Sales Amount ] ) -SUM('Sales Table'[Sales Cost Amount ]) )
- Gross margin (gross margin = (SUM('Sales Table'[Sales Amount ] ) -SUM('Sales Table'[Sales Cost Amount ]))/ SUM('Sales Table'[Sales Amount ] ))
- Average deal size (average deal size = SUM('Sales Table'[Sales Amount ]) / DISTINCTCOUNTNOBLANK('Sales Table'[Order Number ]) )
- cumulative sales revenue calculated column (cumlativesales revenue = CALCULATE(sum(cumlative[Count]),FILTER(ALLEXCEPT(cumlative,cumlative[DateKey]), cumlative[DateKey] <=MAX(cumlative[DateKey]))) )


## the main insights obtained from the analysis are:
- The sales revenue for the last year is 15690000 million, the number of orders for that period is 1596 orders, the net profit is 6628600 million with gross margin 40%
- The top sold product is the “better large canned shrimp”
- The main customer is “acer superstore”
- The net profit for the company was obtained from the “G2” customer type
- Most of the customers are international customers

https://user-images.githubusercontent.com/79236835/171741647-22d59f17-8466-458f-9c0a-315aa3fbe07d.mp4


