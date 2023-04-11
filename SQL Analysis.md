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


  
  
