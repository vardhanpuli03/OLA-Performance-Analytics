# OLA-Performance-Analytics
Project Overview
This project focuses on analyzing OLA ride data to uncover operational inefficiencies, improve performance, and enhance customer satisfaction. By leveraging SQL for data exploration and Power BI for visualization, the analysis provides actionable insights to support data-driven business decisions.

# Objectives
Analyze booking trends, cancellation reasons, customer ratings, and revenue metrics.
Identify patterns affecting operational performance and customer satisfaction.
Provide visual insights through interactive Power BI dashboards.
Recommend strategies to reduce cancellations and improve service efficiency.
Dataset
The dataset includes OLA ride information such as booking status, trip details, customer ratings, and revenue data.

SQL Dataset : Link
POWER BI Dataset : Link
# Business Problems and Solutions
Retrieve all successful bookings:
select *
from bookings
where `Booking Status` = 'Successful';
Find the average ride distance for each vehicle type:
select `Vehicle Type`, avg(`Ride Distance`) 
as avg_distance
from bookings
group by `Vehicle Type`;
Get the total number of cancelled rides by customers:
select * from bookings
where `Cancelled Rides by Customer` = '1';
List the top 5 customers who booked the highest number of rides:
select `Customer ID`, count(`Booking ID`)
as total_rides
from bookings
group by `Customer ID` 
order by total_rides desc limit 5;
Get the number of rides cancelled by drivers due to personal and car-related issues:
select count(*) from bookings 
where `Reason for cancelling by Driver` = 'Personal & Car related issues';
Find the maximum and minimum driver ratings for Prime Sedan bookings:
select max(`Driver Ratings`) as max_ratings, min(`Driver Ratings`) as min_ratings
from bookings 
where `Vehicle Type` = 'Prime Sedan'; 
Retrieve all rides where payment was made using UPI:
select * from bookings
where`Payment Method` = 'UPI';
Find the average customer rating per vehicle type:
select avg(`Customer Rating`) as avg_CR
from bookings
group by `Vehicle Type`;
Calculate the total booking value of rides completed successfully:
select sum(`Booking Value`) as total_successful_bookings
from bookings
where `Booking Status` = 'Successful';
List all incomplete rides along with the reason:
select `Booking ID`, `Incomplete Rides Reason`
from bookings
where `Booking Status` = 'Incomplete';
Findings
Booking Trends: The majority of rides are completed, but a significant portion is canceled due to driver unavailability and high wait times.
Revenue Growth: Revenue peaks during weekends and festive seasons, highlighting opportunities for targeted promotions.
Customer Satisfaction: Cities with better driver availability and lower wait times show higher average ratings.
Peak Hours: Demand is highest during morning (8–10 AM) and evening (5–8 PM) commute hours.
Conclusions
The analysis reveals that operational efficiency can be improved by:

Reducing Cancellations: Addressing driver unavailability and reducing wait times.
Dynamic Pricing: Implementing surge pricing during peak hours to balance supply and demand.
nDriver Incentives: Rewarding top-performing drivers to boost service quality.
Future Work
Integrate real-time data to optimize ride dispatching.
Analyze customer feedback for service improvement.
Compare OLA’s performance with competitors to identify market gaps.
