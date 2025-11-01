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


# Business Problems and Solutions
-- 1. Retrieve all successful bookings
SELECT * 
FROM bookings 
WHERE Booking_Status = 'Successful';

-- 2. Find the average ride distance for each vehicle type
SELECT Vehicle_Type, 
       AVG(Ride_Distance) AS avg_distance 
FROM bookings 
GROUP BY Vehicle_Type;

-- 3. Get the total number of cancelled rides by customers
SELECT * 
FROM bookings 
WHERE Cancelled_Rides_by_Customer = '1';

-- 4. List the top 5 customers who booked the highest number of rides
SELECT Customer_ID, 
       COUNT(Booking_ID) AS total_rides 
FROM bookings 
GROUP BY Customer_ID 
ORDER BY total_rides DESC 
LIMIT 5;

-- 5. Get the number of rides cancelled by drivers due to personal and car-related issues
SELECT COUNT(*) AS cancelled_by_driver 
FROM bookings 
WHERE Reason_for_cancelling_by_Driver = 'Personal & Car related issues';

-- 6. Find the maximum and minimum driver ratings for Prime Sedan bookings
SELECT MAX(Driver_Ratings) AS max_ratings, 
       MIN(Driver_Ratings) AS min_ratings 
FROM bookings 
WHERE Vehicle_Type = 'Prime Sedan';

-- 7. Retrieve all rides where payment was made using UPI
SELECT * 
FROM bookings 
WHERE Payment_Method = 'UPI';

-- 8. Find the average customer rating per vehicle type
SELECT Vehicle_Type, 
       AVG(Customer_Rating) AS avg_CR 
FROM bookings 
GROUP BY Vehicle_Type;

-- 9. Calculate the total booking value of rides completed successfully
SELECT SUM(Booking_Value) AS total_successful_bookings 
FROM bookings 
WHERE Booking_Status = 'Successful';

-- 10. List all incomplete rides along with the reason
SELECT Booking_ID, 
       Incomplete_Rides_Reason 
FROM bookings 
WHERE Booking_Status = 'Incomplete';
# Findings
Booking Trends: The majority of rides are completed, but a significant portion is canceled due to driver unavailability and high wait times.
Revenue Growth: Revenue peaks during weekends and festive seasons, highlighting opportunities for targeted promotions.
Customer Satisfaction: Cities with better driver availability and lower wait times show higher average ratings.
Peak Hours: Demand is highest during morning (8–10 AM) and evening (5–8 PM) commute hours.
# Conclusions
The analysis reveals that operational efficiency can be improved by:

# Reducing Cancellations: Addressing driver unavailability and reducing wait times.
Dynamic Pricing: Implementing surge pricing during peak hours to balance supply and demand.
nDriver Incentives: Rewarding top-performing drivers to boost service quality.
Future Work
Integrate real-time data to optimize ride dispatching.
Analyze customer feedback for service improvement.
Compare OLA’s performance with competitors to identify market gaps.
