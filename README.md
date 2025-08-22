🧳 Tour & Travel Database

This project is a SQL-based database system designed for a Tour & Travel Website.
It implements database schema, triggers, stored procedures, views, and test queries to handle bookings, payments, reviews, and reporting for a travel management platform.

📌 Features

Database Schema with well-structured tables:

Countries, Users, Destinations, Tours

Tour Availability, Bookings, Payments, Reviews

Promotions

Data Integrity & Business Logic

Triggers to handle booking confirmations, cancellations, and seat availability updates

Stored Procedures for:

Creating bookings with validation

Confirming bookings with payment

Adding reviews after tour completion

Search & Reporting Views

V_AvailableTours: Searchable list of open tours with pricing and availability

V_TourRatings: Tour ratings and reviews summary

Queries & Reports

Search tours by price, keywords, availability

Track booking history of users

Generate sales and revenue reports

Promotion code usage analytics

Occupancy rate calculations

🛠️ Tech Stack

Database: MySQL (or any SQL RDBMS)

Concepts Used:

Normalization & Relationships

Triggers & Stored Procedures

Views for reporting

Sample seed data for testing

📂 Project Structure
📦 Tour-Travel-Database
 ┣ 📜 Tour & Travel Database.pdf   # Documentation with schema, SQL code & outputs
 ┣ 📜 README.md                    # Project description (this file)
 ┗ 📂 sql-scripts                  # (Optional) SQL scripts for schema, triggers, views

🚀 Example Queries

Find tours within a price range:

SELECT title, destination, price_per_person, start_date 
FROM V_AvailableTours 
WHERE price_per_person BETWEEN 1000 AND 2000;


Confirm booking after payment:

CALL ConfirmBookingAndPayment(102, 'txn_xyz789', 2376.00);


Get sales performance by destination:

SELECT d.name AS destination, COUNT(b.booking_id) AS total_bookings, 
       SUM(b.final_total_price) AS total_revenue
FROM Bookings b
JOIN TourAvailability ta ON b.availability_id = ta.availability_id
JOIN Tours t ON ta.tour_id = t.tour_id
JOIN Destinations d ON t.destination_id = d.destination_id
WHERE b.status IN ('Confirmed', 'Completed')
GROUP BY d.name
ORDER BY total_revenue DESC;

📊 Sample Outputs

Tour Search Results

title                destination   price_per_person   start_date
Parisian Wonders     Paris         1320.00            2025-10-20
Ancient Rome Explorer Rome         1800.00            2025-09-15


Promotion Usage Report

promo_code   times_used   revenue_generated
EARLYBIRD10  1            2376.00

📖 How to Use

Clone this repository:

git clone https://github.com/your-username/tour-travel-database.git
cd tour-travel-database


Import the SQL schema and seed data into your MySQL database.

Run queries from the documentation to test booking workflows, payments, and reports.

✨ Future Enhancements

API integration for booking system

Frontend UI for users and admins

More advanced analytics dashboards

👨‍💻 Author

Developed by Pankaj Yogesh Gangurde
Savitribai Phule Pune University, Department of Technology, Pune
