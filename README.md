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
```
2. Insert the data in the newly created tables.
```sql
insert into passenger values 
(1, 'sejal','AC','F','Bengaluru','chennai',350,'sleeper'),
(2, 'Anmol','Non-AC','M','Mumbai','Hyderabad',700,'sitting'),
(3, 'pallavi','AC','F','panaji','Bengaluru',600,'sleeper'),
(4, 'Khusboo','AC','F','chennai','Mumbai',1500,'sleeper'),
(5, 'udit','Non-AC','M','Trivandrum','panaji',1000,'sleeper'),
(6, 'Ankur','AC','M','Nagpur','Hyderabad',500,'sitting'),
(7, 'Hemant','Non-AC','M','Panaji','Mumbai',700,'sleeper'),
(8, 'Manish','Non-AC','M','Hyderabad','Bengaluru',500,'sitting'),
(9, 'Piyush','AC','M','Pune','Nagpur',700,'Sitting');

Insert into price values 
(1,'Sleeper',350,770),
(2,'Sleeper',500,1100),
(3,'Sleeper',600,1320),
(4,'Sleeper',700,1540),
(5,'Sleeper',1000,2200),
(6,'Sleeper',1200,2640),
(7,'Sleeper',1500,2700),
(8,'sitting',500,620),
(9,'sitting',600,744),
(10,'sitting',700,868),
(11,'sitting',1000,1240),
(12,'sitting',1200,1488),
(13,'sitting',1500,1860);
```
## Data Analysis and creating reports.
1. How many female passengers traveled a minimum distance of 600KMs?
```sql
select count(*) as No_of_female_passanger from passenger where Gender='F' and distance>=600;
```
2. Write a query to display the passenger details whose travel distance is greater than 500 and who are traveling in a sleeper bus.
```sql
select * from passenger where distance >500 and bus_type='Sleeper';
```
![a2](https://github.com/Abdulmalik25/Travego_Travelers_Sql--Project/assets/153974173/e7356d55-a046-402e-8d40-0abdac38d902)

3. Select passenger names whose names start with the character'S'.
``` sql
select * from passenger where passenger_name like 's%';
```

4. Calculate the price charged for each passenger,displaying the Passenger name,BoardingCity,DestinationCity,Bustype,and Price in the output.
``` sql
select * from passenger p
right join price pr on p.distance=pr.distance and p.bus_type=pr.bus_type;
select 
	passenger_name,
	Boarding_city,
    destination_city,
    p.bus_type,
    price 
from passenger p
join price pr on p.bus_type=pr.bus_type and p.distance=pr.distance;
```
![a3](https://github.com/Abdulmalik25/Travego_Travelers_Sql--Project/assets/153974173/8d065501-ad67-4d85-9819-38d1e0d613df)

5. What are the passenger name (s) and the ticket price for those who traveled 1000KMs Sitting in a bus?
``` sql
select p.passenger_name,pr.price
from passenger p
join price pr on p.bus_type = pr.bus_type
where p.distance = 1000 and p.bus_type = 'sitting';
```
6. What will be the Sitting and Sleeper bus charge for Pallavi to travel from Bangalore to Panaji?
``` sql
select 'Sitting' as Bus_type ,price as Charge
from passenger p left join price pr on p.distance=pr.distance
where pr.bus_type='sitting' and pr.distance=(select p.distance from passenger p where boarding_city='panaji' and destination_city='Bengaluru')
union
select 'Sleeper' as Bus_type ,price as Charge
from passenger p left join price pr on p.distance=pr.distance
where pr.bus_type='sleeper' and pr.distance=(select p.distance from passenger p where boarding_city='panaji' and destination_city='Bengaluru');
```
![a3](https://github.com/Abdulmalik25/Travego_Travelers_Sql--Project/assets/153974173/2b35fbf3-91bc-438c-bef6-d24e24ab2c4a)
![a1](https://github.com/Abdulmalik25/Travego_Travelers_Sql--Project/assets/153974173/c2163a6c-1457-473b-a715-49b922744f01)
![3h](https://github.com/Abdulmalik25/Travego_Travelers_Sql--Project/assets/153974173/9a5b418c-e3dc-48c8-999b-14ffa98c719f)
![a4](https://github.com/Abdulmalik25/Travego_Travelers_Sql--Project/assets/153974173/fb3e29e7-dcff-4f61-93d6-08e229297bbe)


7. Alter the column category with the value "Non-AC" where the Bus_Type is sleeper.
``` sql
update passenger set category = 'Non-AC' where Bus_Type = 'sleeper';
select * from passenger;
```
8. .Delete an entry from the table where the passenger name is Piyus hand commit this change in the database.
``` sql
delete from passenger where passenger_name='piyush';
commit;
```
9. Truncate the table passenger and comment on the number of rows in the table(explainifrequired).
``` sql
truncate table passenger;
select * from passenger;
# Truncation of table will delete all the entries in the table leaving only the structure of it.
```
10. Delete the table passenger from the database
``` sql
drop table passenger;
```
