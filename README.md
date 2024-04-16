# Travego_Travelers_Sql-Project
Dive into the realm of passenger travel data management with SQL! Learn to effortlessly insert and retrieve information about bus travel between cities, whether it's sitting or sleeper. Uncover the power of MySQL functionality and commands for seamless database storage and data handling.

# Tech Stack used
<img src="https://github.com/Abdulmalik25/Travego_Travelers_Sql--Project/assets/153974173/fe50efa7-c836-4213-b20f-0b89ad397eb9" alt="images" width="450" height="350">

# Introduction
Let’s assume that you have to keep the record of the passengers and price to travel between two cities by bus, for types (Sitting and Sleeper). The focus of this project is to learn to write different types SQL statements to insert and retrieve data from a database. For database storage, we will use MySQL, information related to MySQL and several commands have already been discussed in weekly notebooks. You can refer to these to gather hints on functionality.

# Data Model
![Screenshot 2024-04-16 221810](https://github.com/Abdulmalik25/Travego_Travelers_Sql--Project/assets/153974173/2dfad99a-e4fe-4bf1-8500-3451069a5cd5)

# Getting Started
## Database creation and tables creation.
## Questions and Tasks
1. Create a schema named Travego and create the tables mentioned above with the mentioned column names.Also,declare the relevant datatypes for each feature/column in the dataset.
```sql
create schema Travego;

use travego;

create Table passenger (
    passenger_id int primary key,
    passenger_name varchar(20),
    category varchar(20),
    gender varchar(20),
    Boarding_city varchar(20),
    destination_city varchar(20),
    distance int,
    bus_type varchar(20)
);

create table price (
    id int primary key,
    bus_type varchar(20),
    distance int,
    price int
);





