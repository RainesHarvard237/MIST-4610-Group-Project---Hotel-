# MIST4610 Group 4 Project 1 
# Team Name 
21479 Group 4
## Team Members 
 1. Raines Harvard [@RainesHarvard237](https://www.github.com/RainesHarvard237)
 2. Grace Klatt [@gracecklatt](https://www.github.com/gracecklatt)
 3. Rocco Garcia [@roccog2024](https://www.github.com/roccog2024)
 4. Kory Cote [@Korycote](https://www.github.com/Korycote)

## Problem Description
The goal of this project is to model and build a relational database for the general operations of an organization. For our project we decided to create our data model for a fully functioning service hotel. The central entity in the model is Reservation which allows a tie to guest, rooms, employees, promotions, and financial data. The hotel operates a variety of departments and services, including a bar and restaurant, housekeeping, maintenance, and promotional campaigns. Our goal is to accurately model these relationships and generate sample data similar to that of a real hotel. Additionally, we will use the data model to create queries that can provide business insight into a hotel's daily operations, revenue performance, and service efficiency.
# Data Model
Explanation of data model:
Our model is based on the structure of a full-service hotel.

The **Reservation** entity is the central hub of the data model. Each reservation is linked to one guest and tracks when they will check in/out, and the status of their booking. A reservation can include multiple hotel rooms and a room can appear in multiple reservations over time. The **Reservation_Room** entity is an associative entity which resolves the many to many relationship that occurs between Reservation and Room. This allows the actual move in/out datetimes for each room assigned; allowing the hotel to keep track of which rooms are available and which are not.

The **Room** entity represents each individual room in the hotel, including the floor and status of the room. Each room belongs to a **Room_Type** which gives the room a categorization (ex: Standard, Double, King, Presidential Suite) and defines the occupancy limits, bed configuration, and nightly rate. **Room_Type** and **Room** have a one-to-many relationship allowing the hotel to manage pricing at each category level.

The **Guest** entity stores the personal information of each individual who makes a reservation at the hotel, including their name, contact information. A guest is able to have many reservations at a time, establishing a one-to-many relationship between Guest and Reservation.

The **Promotion** entity stores information about the promotion name, scope, percentage, and applicable date range. Promotions are tied to specific room types and are also linked to reservations so that the discount can be properly tracked throughout the booking process.

The **Invoice** entity captures the billing summary for each reservation, including the total amount, invoice date, and the payment status. Payments separate from the invoice, are tracked separately in the **Payment** entity, which records the amount paid, method, and datetime allowing the partial payments to be modeled over time.

The **Employee** entity stores all the information about the hotel staff. It includes their name, role, and hire date. The employee table includes a recursive relationship to model a supervisor hierarchy. Employees are assigned to specific departments through the associative entity, **Department_Assignment**. This entity tracks the start and end dates of each assignment so the department history can be preserved.

The **Department** entity represents operational divisions of the hotel (ex: front desk, housekeeping, food and beverages). Each department can have many employees and can be linked to restaurant and bar entities.

The **Restaurant** entity represents the hotel's dining establishments, each with a cuisine type, seating capacity, and meal service designation (room service or in house dining). Restaurants share **Menu_Items** with the bar and menu pricing and a category. The **Bar** entity represents the hotel's bar venue which is separate from the restaurants. The Bar entity has its own seating capacity, bar type, and operating hours.

The **Service_Order** entity is an associative entity to connect a reservation to the bar or restaurant. Each Service_Order is timestamped and contains many individual items captured in **Order_Line_Item**, which records the menu item, quantity, and line total.

The **HouseKeeping_Record** entity tracks each instance of a room being cleaned during or after reservations. Each record links a room, an employee, and a reservation. It also captures the cleaning type, date, status of the room, and any notes made by the housekeeper. Additionally, we created a **Maintenance_Request** entity to record any issues reported for a specific room and the employees' resolution. It tracks the issues description, priority, status, and both the reported and resolved dates.

Lastly, the **Review** entity allows quests to leave a review, star rating, any comments they want to share regarding reservation. Each review is tied to one reservation, which allows guests to share any feedback.

<img width="1478" height="983" alt="Screenshot 2026-03-30 185107" src="https://github.com/user-attachments/assets/753c5693-6fc9-4a55-b4d6-c28cca27274d" />

# Data Dictionary 
**Table: Reservation**

**Table: Reservation_Room**

**Table: Room**

**Table: Room_Type**

**Table: Guest**

**Table: Promotion**

**Table: Invoice** 

**Table: Payments**

**Table: Employee**

**Table: Department_Assignment**

**Table: Department**

**Table: Resturant**

**Table: Menu_Item**

**Table: Bar**
<img width="966" height="226" alt="image" src="https://github.com/user-attachments/assets/6e4f428f-99a4-4d56-98ec-fb3d279453d9" />

**Table: Service_Order**

**Table: Order_Line_Item**

**Table: HouseKeeping_Record**

**Table: Maintenance_Request**

**Table: Review** 

# Queries:
1. List the total food and beverage revenue generated by each department, calculated by summing all order line item totals for service orders linked to each department's restaurants.

2. Lists the name and emails of guests whose total spending across all reservations exceeds the average invoice amount, ordered by total spend in descending order

3. 






