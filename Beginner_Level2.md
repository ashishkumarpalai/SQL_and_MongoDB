# Set 2 : Beginner Level

**Set 2: Beginner Level - Advanced**

We will be using a **`Restaurants`** table / collection for this set of problems. The schema represents a list of restaurants like one might find in a delivery app like Zomato. Each restaurant has an **`id`**, **`name`**, **`cuisine_type`** (e.g., Italian, Chinese), **`location`**, **`average_rating`**, and **`delivery_available`** (a boolean indicating if delivery is available).

**MongoDB Schema:**

```
{
  "_id": ObjectId(), 
  "name": String,
  "cuisine_type": String,
  "location": String,
  "average_rating": Number,
  "delivery_available": Boolean
}
```

**Problem 16:**

- **Prerequisite**: Understand creating tables in SQL / collections in MongoDB
- **Problem**: Create a **`Restaurants`** table / collection with the fields defined above.


```
db.createCollection("Restaurants")

```
**Problem 17:**

- **Prerequisite**: Understand inserting data into SQL tables / MongoDB collections
- **Problem**: Insert five rows / documents into the **`Restaurants`** table / collection with data of your choice.

```
db.Restaurants.insertMany([
    {
        id:1,
        name: "Pizza Hut",
        cuisine_type: "Italian",
        location: "New York",
        average_rating: 4.5,
        delivery_available: true
    },
    {
        id:2,
        name: "McDonalds",
        cuisine_type: "Fast Food",
        location: "Los Angeles",
        average_rating: 3.5,
        delivery_available: true
    },
    {
        id:3,
        name: "Chipotle",
        cuisine_type: "Mexican",
        location: "San Francisco",
        average_rating: 4.0,
        delivery_available: true
    },
    {
        id:4,
        name: "Subway",
        cuisine_type: "Sandwiches",
        location: "Chicago",
        average_rating: 3.0,
        delivery_available: true
    },
    {
        id:5,
        name: "Taco Bell",
        cuisine_type: "Mexican",
        location: "Miami",
        average_rating: 3.5,
        delivery_available: true
    }
]);


```
**Problem 18:**

- **Prerequisite**: Understand how to order data in SQL / MongoDB
- **Problem**: Write a query to fetch all restaurants, ordered by **`average_rating`** in descending order.


```
db.Restaurants.find().sort({ average_rating: -1 });
```
**Problem 19:**

- **Prerequisite**: Understand filtering with multiple conditions in SQL / MongoDB
- **Problem**: Write a query to fetch all restaurants that offer **`delivery_available`** and have an **`average_rating`** of more than 4.


```
db.Restaurants.find({
    delivery_available: true,
    average_rating: { $gt: 4 }
});
```
**Problem 20:**

- **Prerequisite**: Understand how to use NULL checks in SQL / MongoDB
- **Problem**: Write a query to fetch all restaurants where the **`cuisine_type`** field is not set or is null.

```
db.Restaurants.find({
    cuisine_type: { $exists: false }
});
```
**Problem 21:**

- **Prerequisite**: Understand how to count rows / documents in SQL / MongoDB
- **Problem**: Write a query to count the number of restaurants that have **`delivery_available`**.


```
db.Restaurants.count({
    delivery_available: true
});

```
**Problem 22:**

- **Prerequisite**: Understand using string patterns in SQL (LIKE clause) / using regex in MongoDB
- **Problem**: Write a query to fetch all restaurants whose **`location`** contains 'New York'.


```
db.Restaurants.find({
    location: { $regex: /New York/i }
});
```
**Problem 23:**

- **Prerequisite**: Understand how to use the AVG function in SQL / MongoDB's aggregate functions
- **Problem**: Write a query to calculate the average **`average_rating`** of all restaurants.


```

```
**Problem 24:**

- **Prerequisite**: Understand how to limit results in SQL / MongoDB
- **Problem**: Write a query to fetch the top 5 restaurants when ordered by **`average_rating`** in descending order.


```
db.Restaurants.find().sort({ average_rating: -1 }).limit(5);

```
**Problem 25:**

- **Prerequisite**: Understand data deletion in SQL / MongoDB
- **Problem**: Write a query to delete the restaurant with **`id`** 3.

```
db.Restaurants.deleteOne({ _id: 3 });
```









































**SQL Schema:**

```
CREATE TABLE Restaurants (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    cuisine_type VARCHAR(100),
    location VARCHAR(255),
    average_rating DECIMAL(3,2),
    delivery_available BOOLEAN
);

```

### create database

```
CREATE DATABASE giapratice 

```
### used databse

```
use databasename
```


**Problem 16:**

- **Prerequisite**: Understand creating tables in SQL / collections in MongoDB
- **Problem**: Create a **`Restaurants`** table / collection with the fields defined above.

```
CREATE TABLE Restaurants (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    cuisine_type VARCHAR(100),
    location VARCHAR(255),
    average_rating DECIMAL(3,2),
    delivery_available BOOLEAN
);
```
**Problem 17:**

- **Prerequisite**: Understand inserting data into SQL tables / MongoDB collections
- **Problem**: Insert five rows / documents into the **`Restaurants`** table / collection with data of your choice.

```
INSERT INTO Restaurants (id,name, cuisine_type, location, average_rating, delivery_available)
VALUES
(1,'Pizza Hut', 'Italian', 'New York', 4.5, TRUE),
(2,'McDonalds', 'Fast Food', 'Los Angeles', 3.5, TRUE),
(3,'Chipotle', 'Mexican', 'San Francisco', 4.0, TRUE),
(4,'Subway', 'Sandwiches', 'Chicago', 3.0, TRUE),
(5,'Taco Bell', 'Mexican', 'Miami', 3.5, TRUE);

```
**Problem 18:**

- **Prerequisite**: Understand how to order data in SQL / MongoDB
- **Problem**: Write a query to fetch all restaurants, ordered by **`average_rating`** in descending order.

```
SELECT *
FROM Restaurants
ORDER BY average_rating DESC;

```
**Problem 19:**

- **Prerequisite**: Understand filtering with multiple conditions in SQL / MongoDB
- **Problem**: Write a query to fetch all restaurants that offer **`delivery_available`** and have an **`average_rating`** of more than 4.

```
SELECT *
FROM Restaurants
WHERE delivery_available = TRUE
AND average_rating > 4;

```
**Problem 20:**

- **Prerequisite**: Understand how to use NULL checks in SQL / MongoDB
- **Problem**: Write a query to fetch all restaurants where the **`cuisine_type`** field is not set or is null.


```
SELECT *
FROM Restaurants
WHERE cuisine_type IS NULL;
```
**Problem 21:**

- **Prerequisite**: Understand how to count rows / documents in SQL / MongoDB
- **Problem**: Write a query to count the number of restaurants that have **`delivery_available`**.


```
SELECT COUNT(*)
FROM Restaurants
WHERE delivery_available = TRUE;
```
**Problem 22:**

- **Prerequisite**: Understand using string patterns in SQL (LIKE clause) / using regex in MongoDB
- **Problem**: Write a query to fetch all restaurants whose **`location`** contains 'New York'.

```
SELECT *
FROM Restaurants
WHERE location LIKE '%New York%';
```
**Problem 23:**

- **Prerequisite**: Understand how to use the AVG function in SQL / MongoDB's aggregate functions
- **Problem**: Write a query to calculate the average **`average_rating`** of all restaurants.


```
SELECT AVG(average_rating)
FROM Restaurants;
```
**Problem 24:**

- **Prerequisite**: Understand how to limit results in SQL / MongoDB
- **Problem**: Write a query to fetch the top 5 restaurants when ordered by **`average_rating`** in descending order.


```
SELECT *
FROM Restaurants
ORDER BY average_rating DESC
LIMIT 5;
```
**Problem 25:**

- **Prerequisite**: Understand data deletion in SQL / MongoDB
- **Problem**: Write a query to delete the restaurant with **`id`** 3.

```
DELETE FROM Restaurants
WHERE id = 3;
```