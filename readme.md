# Football Ticket Booking System Database

## Overview

The Football Ticket Booking System is a relational database project designed to manage football match ticket bookings efficiently. The system allows football fans to book tickets for matches, while ticket managers can oversee match availability and booking records.

This project demonstrates the use of SQL Data Definition Language (DDL) and Data Manipulation Language (DML) commands, including table creation, constraints, foreign key relationships, and sample data insertion.

---

## Database Schema

The database consists of three main tables:

### 1. Users

Stores information about registered users.

| Column       | Description                                |
| ------------ | ------------------------------------------ |
| user_id      | Unique identifier for each user            |
| full_name    | User's full name                           |
| email        | User's email address (must be unique)      |
| role         | User role (Football Fan or Ticket Manager) |
| phone_number | Contact number                             |

### 2. Matches

Stores information about football matches.

| Column              | Description                      |
| ------------------- | -------------------------------- |
| match_id            | Unique identifier for each match |
| fixture             | Match fixture name               |
| tournament_category | Competition category             |
| base_ticket_price   | Standard ticket price            |
| match_status        | Availability status              |

Possible match statuses:

* Available
* Selling Fast
* Sold Out
* Postponed

### 3. Bookings

Stores ticket booking information.

| Column         | Description               |
| -------------- | ------------------------- |
| booking_id     | Unique booking identifier |
| user_id        | References a user         |
| match_id       | References a match        |
| seat_number    | Assigned seat             |
| payment_status | Booking payment status    |
| total_cost     | Total booking amount      |

Possible payment statuses:

* Pending
* Confirmed
* Cancelled

---

## Entity Relationship

```text
Users
  |
  | (1:M)
  |
Bookings
  |
  | (M:1)
  |
Matches
```

* One user can make multiple bookings.
* One match can have multiple bookings.
* Each booking belongs to one user and one match.

---

## Constraints Implemented

### Users Table

* Primary Key on `user_id`
* Unique Constraint on `email`
* Check Constraint on `role`

### Matches Table

* Primary Key on `match_id`
* Check Constraint to prevent negative ticket prices
* Check Constraint on `match_status`

### Bookings Table

* Primary Key on `booking_id`
* Foreign Key to `Users(user_id)`
* Foreign Key to `Matches(match_id)`
* Check Constraint for non-negative `total_cost`
* Check Constraint on `payment_status`

---

## Sample Data Included

### Users

* Tanvir Rahman
* Asif Haque
* Sajjad Rahman
* Jannat Ara

### Matches

* Real Madrid vs Barcelona
* Man City vs Liverpool
* Bayern Munich vs PSG
* AC Milan vs Inter Milan
* Juventus vs Roma

### Bookings

Five sample booking records demonstrating:

* Confirmed bookings
* Pending bookings
* Missing seat assignment
* Default payment status usage

---

## SQL Features Demonstrated

* CREATE TABLE
* DROP TABLE
* PRIMARY KEY
* FOREIGN KEY
* UNIQUE Constraints
* CHECK Constraints
* DEFAULT Values
* INSERT Statements
* Relational Database Design

---

## Requirements

* PostgreSQL 12+ (recommended)
* Any SQL client such as:

  * pgAdmin
  * DBeaver
  * DataGrip
  * PostgreSQL Command Line (psql)

---

## How to Run

1. Create a PostgreSQL database.

```sql
CREATE DATABASE football_ticket_booking;
```

2. Connect to the database.

3. Execute the SQL script.

```sql
\i football_ticket_booking.sql
```

4. Verify data insertion.

```sql
SELECT * FROM Users;
SELECT * FROM Matches;
SELECT * FROM Bookings;
```

---

## Future Enhancements

* Match venue management
* Stadium seat allocation system
* Online payment integration
* Ticket cancellation functionality
* Booking history tracking
* User authentication and authorization
* Match scheduling module

---

## Author

Database Project – Football Ticket Booking System

---

## License

This project is intended for educational and academic purposes.
