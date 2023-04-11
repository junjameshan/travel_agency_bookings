# SQL Queries for Analysis

## Booking trends overtime 

````sql
WITH cte AS (SELECT 
  EXTRACT(YEAR FROM Arrival_date) AS year,
  EXTRACT(MONTH FROM Arrival_date) AS month,
  Commissionable_value____ AS commission_sum
FROM 
  travel.travel_bookings_data 
)

SELECT 
  year,
  month,
  ROUND(SUM(commission_sum), 2) AS total_commission
FROM 
  cte 
GROUP BY 
  year, month 
HAVING 
  year IS NOT NULL 
ORDER BY 
  year ASC, 
  month ASC,
  total_commission DESC 
````

#### Walkthrough 

In order to analyze the booking trends overtime, I first needed to group by based on the month and year of the arrival date for the booking in order to aggregate the total sum of the commissionable value for each booking. 

#### Results 

| year | month | total_commission |
|------|-------|------------------|
| 2022 | 2     | 5532.5           |
| 2022 | 3     | 1997             |
| 2022 | 4     | 2281             |
| 2022 | 5     | 6395.8           |
| 2022 | 6     | 22085.6          |
| 2022 | 7     | 9534.1           |
| 2022 | 8     | 11710.3          |
| 2022 | 9     | 8695.1           |
| 2022 | 10    | 21863.9          |
| 2022 | 11    | 8298.4           |
| 2022 | 12    | 25148.7          |
| 2023 | 1     | 867              |
| 2023 | 2     | 5000             |
| 2023 | 4     | 3661.6           |
| 2023 | 5     | 2867.4           |
| 2023 | 6     | 9568.6           |


























  
  
