# Case Study: Travel Agency Bookings

![image](https://user-images.githubusercontent.com/123096758/231226803-a29cc2db-ff34-4fc6-9576-6c6b39482f7c.png)

## Introduction / Background 

A travel booking agency is looking into the total bookings that one of their advisor user has completed for the year of 2022 and 2023 so far. Working as a Data Analyst on the Marketing Analytics team, you want to be able to provide insights into the business performance of the advisor user for the Marketing Director.

A few examples of insights that the Marketing Director as well as the advisor user wants to see are: 

- Booking trends over time 
- Value of completed vs. canceled vs. pending bookings
- Top clients
- Top suppliers 
- Bookings with travel (arrival date) coming up in the next 2 weeks 
- Completed but unpaid bookings 

## Assumptions / Given Values 

Analyzing the dataset of the [Travel Bookings Data](https://github.com/junjameshan/travel_agency_bookings/blob/main/Travel%20Bookings%20Data.csv), we can determine the significance of each attribute within the dataset: 

- _Date_booked_: Date that the travel arrangement was booked 
- _Arrival_date_: Arrival date for the travel arrangement 
- _Departure_date_: Departure date for the travel arrangement 
- _Supplier_: The type of travel booking **(i.e. Hotel, Cruise, Villa, etc.)** 
- _Guest_name_: Name of the guest for the travel booking 
- _Room_nights_: Number of nights that the guest will be staying for in the travel arrangement 
- _Confirmation_: Confirmation number for the travel booking 
- _Booking_status_: Status of travel booking **(i.e. Booked, Canceled, Completed, etc.)** 
- _Commissionable_value_: Amount that is able to commissioned for the travel agency and user advisor 
- _Commission_: Total commission percentage
- _Total_commission_: Total commission in dollar figures 
- _Your_Commission_split_: Total user advisor commission percentage
- _Your_Commission_: Total user advisor commission in dollar figures 

## Analysis 

The analysis of the queries performed can be found in the link shown below: 

[SQL Queries Analysis](https://github.com/junjameshan/travel_agency_bookings/blob/main/SQL%20Analysis.md)

## Conclusions & Suggestions 

In addition to the data that is provided by the current dataset, further data points that will be beneficial in analyzing for future purposes are as follows:

1. **Demographic of clients**: Demographics of clients involve data such as age, location of residency,
occupation, ethnicity, and even marital status as well. These data points are
valuable in that it can be utilized to create a target market that the travel agency can
hyperfocus on for marketing and understanding the core of the company’s
customer base. It can also bring up questions around which demographic should
the company focus on targeting for future markets and what is the best GTM
strategy for how we will be able to reach these targeted markets?

2. **Location of destinations**: Another useful data point that can be included for future purposes is the location
of the destinations where the guests will be traveling to. This is beneficial in that it
can provide a great source of information in the hot cities and countries where
clients are interested in traveling to as well as creating additional commissions
for suggesting activities and amenities that are popular with the city. By having
this data at hand, the travel agency can create a suggested list of cities that are considered to
be “hot” with a curated list of hotels, activities and amenities that can be included
in a package for the city as well.

3. **Reviews of clients and agents**: The last additional data point that can be included within the travel agency platform
is the development of a review feature for its clients and travel agents. This
feature can create a credibility system where agents will be able to develop a
reputation among its source of previous experience of bookings travel
arrangements for its clients and also provide feedback regarding an agent’s
expertise in certain cities and countries to visit as well. On the client’s end, it can
provide credibility in their responsiveness to payments, bookings, and even
communication.
