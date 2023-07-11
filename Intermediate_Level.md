**Set 3: Intermediate Level**

We'll continue with a **`Rides`** table / collection for this set of problems. The schema represents a list of rides one might find in a ride-hailing app like Uber. Each ride has an **`id`**, **`driver_id`**, **`passenger_id`**, **`start_location`**, **`end_location`**, **`distance`** (in miles), **`ride_time`** (in minutes), and **`fare`** (in dollars).

**MongoDB Schema:**

```
{
  "_id": ObjectId(),
  "driver_id": ObjectId(),
  "passenger_id": ObjectId(),
  "start_location": String,
  "end_location": String,
  "distance": Number,
  "ride_time": Number,
  "fare": Number
}

```

**SQL Schema:**

```
CREATE TABLE Rides (
    id INT PRIMARY KEY,
    driver_id INT,
    passenger_id INT,
    start_location VARCHAR(255),
    end_location VARCHAR(255),
    distance DECIMAL(5,2),
    ride_time DECIMAL(5,2),
    fare DECIMAL(6,2)
);

```

**Problem 26:**

- **Prerequisite**: Understand creating tables in SQL / collections in MongoDB
- **Problem**: Create a **`Rides`** table / collection with the fields defined above.

**Problem 27:**

- **Prerequisite**: Understand inserting data into SQL tables / MongoDB collections
- **Problem**: Insert five rows / documents into the **`Rides`** table / collection with data of your choice.

**Problem 28:**

- **Prerequisite**: Understand how to order data in SQL / MongoDB
- **Problem**: Write a query to fetch all rides, ordered by **`fare`** in descending order.

**Problem 29:**

- **Prerequisite**: Understand using math operations in SQL / MongoDB
- **Problem**: Write a query to calculate the total **`distance`** and total **`fare`** for all rides.

**Problem 30:**

- **Prerequisite**: Understand how to use the AVG function in SQL / MongoDB's aggregate functions
- **Problem**: Write a query to calculate the average **`ride_time`** of all rides.

**Problem 31:**

- **Prerequisite**: Understand using string patterns in SQL (LIKE clause) / using regex in MongoDB
- **Problem**: Write a query to fetch all rides whose **`start_location`** or **`end_location`** contains 'Downtown'.

**Problem 32:**

- **Prerequisite**: Understand how to use the COUNT function in SQL / MongoDB's aggregate functions
- **Problem**: Write a query to count the number of rides for a given **`driver_id`**.

**Problem 33:**

- **Prerequisite**: Understand data updating in SQL / MongoDB
- **Problem**: Write a query to update the **`fare`** of the ride with **`id`** 4.

**Problem 34:**

- **Prerequisite**: Understand using GROUP BY in SQL / MongoDB's aggregate functions
- **Problem**: Write a query to calculate the total **`fare`** for each **`driver_id`**.

**Problem 35:**

- **Prerequisite**: Understand data deletion in SQL / MongoDB
- **Problem**: Write a query to delete the ride with **`id`** 2.