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


##### 2022 Booking Trends 

![image](https://user-images.githubusercontent.com/123096758/231241874-736e931a-fe44-4cf5-9c54-5c79a5f73b85.png)

##### 2023 Booking Trends 

![image](https://user-images.githubusercontent.com/123096758/231241940-dcea184d-c75c-4aab-bcc5-aff89efedb60.png)


## Value of Completed vs. Canceled vs. Pending Bookings 

````sql
SELECT 
  Booking_status,
  COUNT(*) AS total_count,
  ROUND(SUM(Commissionable_value____), 2) AS total_commission_value
FROM 
  travel.travel_bookings_data 
WHERE 
  Booking_status IS NOT NULL
GROUP BY 
  Booking_status
````

#### Results 

| Booking_status | total_count | total_commission_value |
|----------------|-------------|------------------------|
| Booked         | 5           | 15497.6                |
| Canceled       | 3           | 7843.3                 |
| Completed      | 70          | 122166.1               |


## Top Clients 

````sql
SELECT 
  Guest_name, 
  ROUND(SUM(Commissionable_value____), 2) AS total_booking_value
FROM 
  travel.travel_bookings_data 
GROUP BY 
  Guest_name
ORDER BY 
  total_booking_value DESC 
  ````
  
#### Results 

| Guest_name        | total_booking_value |
|-------------------|---------------------|
| Patrick Miller    | 11261.7             |
| Abigail Morris    | 9363.4              |
| Lucia Chapman     | 8870                |
| Tess Davis        | 7508.7              |
| Belinda Murphy    | 6929.1              |
| Natalie Hopkins   | 6705                |
| Julian Nelson     | 6128.2              |
| Nelson Herst      | 5762.6              |
| John Cameron      | 5668.3              |
| Lana Carter       | 5600                |
| Maya Perkins      | 5000                |
| Michael Scott     | 3794.8              |
| Marcus West       | 3755.7              |
| Deanna Russell    | 3528                |
| James Warren      | 3155.7              |
| Lilianna Thompson | 2983.9              |
| John Miller       | 2776.8              |
| Julia Crawford    | 2760                |
| Darren Duvarson   | 2641                |
| Carina Nelson     | 2501.4              |
| Fenton Miller     | 2364                |
| Garry Murray      | 2322.1              |
| Evelyn Johnson    | 2290.1              |
| Frederick Edwards | 2288                |
| Kimberly Barrett  | 2158.5              |
| Amanda Lloyd      | 2124.4              |
| Kate Hamilton     | 2081.3              |
| Arnold Fowler     | 2062                |
| Lydia Harris      | 1990                |
| Elise Watson      | 1951                |
| Myra Richardson   | 1797                |
| Arianna Adams     | 1710.6              |
| Jacob Taylor      | 1215.6              |
| Chloe Carroll     | 1170.5              |
| Jacob Perry       | 1160                |
| Liz Bronstan      | 1090                |
| Tara Perkins      | 1083.5              |
| Lydia Wright      | 1077                |
| Chloe Hamilton    | 1050.3              |
| Alexia Murphy     | 990                 |
| Kimberly Turner   | 890.3               |
| Kelvin Henderson  | 719.9               |
| Nicole Hawkins    | 704.6               |
| Naomi Brooks      | 633                 |
| Julia Johnston    | 627                 |
| Kirsten Johnson   | 616                 |
| Steven Perry      | 194.2               |
| Natalie West      | 162                 |
| Tara West         | 154.8               |
| Carina Carter     | 135                 |


##  Top Suppliers

````sql
SELECT 
  Supplier, 
  ROUND(SUM(Commissionable_value____), 2) AS total_booking_value
FROM 
  travel.travel_bookings_data 
GROUP BY 
  Supplier
ORDER BY 
  total_booking_value DESC 
````

#### Results 

| Supplier                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | total_booking_value |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| Virgin Voyages                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | 8870                |
| Rosewood Las Ventanas                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | 7795                |
| Cap Rocat                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | 6128.2              |
| Lily Of The Valley                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | 6023.1              |
| Catherine Henry                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | 5668.3              |
| Viking Cruises                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | 5600                |
| Bela Vista Hotel & Spa                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | 5142.4              |
| Timbers Kauai - Ocean Club and Residences                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | 5000                |
| Can ferrereta                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | 4143.3              |
| Mezzatorre Hotel & Thermal Spa                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | 3968.6              |
| Six Senses Douro Valley                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | 3566                |
| Villa San Michele                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | 3102.5              |
| Arch RoamRight                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | 3055                |
| ROLZO                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | 3028.4              |
| Kimpton Fitzroy London                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | 2916.8              |
| Soho Grand Hotel                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2814                |
| Round Hill Hotel & Villas                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | 2792                |
| Athens Capital Hotel â€“ MGallery Collection                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | 2776.8              |
| The Bowery Hotel                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2760                |
| Sublime Comporta                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2710.6              |
| The Standard London                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | 2458.3              |
| Kimpton Hotel Palomar South Beach                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | 2428.5              |
| The Cape, A Thompson Hotel                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | 2364                |
| Hotel Borgo San Felice                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | 2322.1              |
| Acron Villas                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | 2288                |
| The Wilde Resort and Spa                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | 2212.5              |
| Wynn Las Vegas And Encore                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | 2145.5              |
| Le Cinq Codet                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | 2108                |
| Canaves Oia Epitome                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | 2084.9              |
| Ca Di Dio	|1992.9|
|Crosby Street Hotel	|1990|
|JW Marriott Scottsdale Camelback Inn Resort & Spa	|1990|
|The Balmoral, A Rocco Forte Hotel	|1951|
|Sound View Greenport	|1940.7|
|Bellevue Syrene	|1815|
|Spatia Comporta	|1794|
|Casa9	|1785|
|Ashford Castle	|1710.6|
|Inn on Fifth Naples	|1377|
|InterContinental Dublin	|1235.2|
|William Vale	|1160|
|Lupaia	|1086|
|Grand Hotel Tremezzo	|1083.5|
|The WIlliamsburg Hotel	|1077|
|11 Howard	|1050.3|
|The Dilly London	|1038.4|
|Arlo Midtown	|1008.1|
|Hotel Locarno	|990|
|Menorca Experimental	|890.3|
|The Plum Guide	|871.4|
|21c Museum Hotel Nashville	|867|
|Can Alomar	|776.6|
|LÂ´AND Vineyards Resort	|758.5|
|Covo Dei Saraceni	|719.9|
|The Lumiares Hotel & Spa	|704.6|
|Kimpton Vividora Hotel	|692.3|
|Le Regina Biarritz	|691.9|
|Freehand New York	|633|
|The Roxy Hotel New York	|627|
|Heritage Hotel Fermai Split MGallery	|617.4|
|Esplanade Hotel Zagreb	|309.6| 

## Top Supplier Types 

````sql
SELECT 
  Supplier_type, 
  ROUND(SUM(Commissionable_value____), 2) AS total_booking_value
FROM 
  travel.travel_bookings_data 
WHERE 
  Supplier_type IS NOT NULL
GROUP BY 
  Supplier_type
ORDER BY 
  total_booking_value DESC 
  ````
  
#### Results 

| Supplier_type  | total_booking_value |
|----------------|---------------------|
| Hotel          | 124379.2            |
| Cruise         | 14470               |
| Transportation | 3028.4              |
| Insurance      | 2758                |
| Villa          | 871.4               |

## Completed but unpaid bookings 

````sql
SELECT 
  Guest_name,
  Booking_status,
  Payment_status
FROM 
  travel.travel_bookings_data 
WHERE 
  Booking_status LIKE 'Completed'
  AND Payment_status NOT LIKE 'Paid'
````

#### Results 

| Guest_name    | Booking_status | Payment_status |
|---------------|----------------|----------------|
| Carina Nelson | Completed      | Not Paid       |


## Travel bookings upcoming in the next two weeks 

````sql
SELECT 
  Arrival_date
FROM 
  travel.travel_bookings_data 
WHERE 
  Arrival_date BETWEEN CURRENT_DATE()
  AND (CURRENT_DATE + 14)
````

#### Results 

| Arrival_date |
|--------------|
| 2023-04-16   |
| 2023-04-13   |














  
  
