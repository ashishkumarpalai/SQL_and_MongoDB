# Set 4 : Intermediate Level

We'll continue with the **`Rides`** table / collection from the previous set.

**Problem 36:**

- **Prerequisite**: Understand using the MAX and MIN functions in SQL / using sort and limit in MongoDB
- **Problem**: Write a query to find the ride with the highest and lowest **`fare`**.

**Problem 37:**

- **Prerequisite**: Understand using the GROUP BY clause in SQL / using aggregate in MongoDB
- **Problem**: Write a query to find the average **`fare`** and **`distance`** for each **`driver_id`**.

**Problem 38:**

- **Prerequisite**: Understand using HAVING clause in SQL / using match in MongoDB's aggregate pipeline
- **Problem**: Write a query to find **`driver_id`** that have completed more than 5 rides.

**Problem 39:**

- **Prerequisite**: Understand the use of INNER JOIN in SQL / Lookup in MongoDB
- **Problem**: Assuming there is another collection/table called **`Drivers`** with **`driver_id`** and **`name`** fields, write a query to find the name of the driver with the highest **`fare`**.

**Problem 40:**

- **Prerequisite**: Understand the concept of subqueries in SQL / using multiple stages in MongoDB's aggregate pipeline
- **Problem**: Write a query to find the top 3 drivers who have earned the most from fares. Return the drivers' ids and total earnings.

**Problem 41:**

- **Prerequisite**: Understand date and time functions in SQL / MongoDB
- **Problem**: Assuming there's a **`ride_date`** field of date type in the **`Rides`** table / collection, write a query to find all rides that happened in the last 7 days.

**Problem 42:**

- **Prerequisite**: Understand the concept of NULL values and how to handle them in SQL / MongoDB
- **Problem**: Write a query to find all rides where the **`end_location`** is not set.

**Problem 43:**

- **Prerequisite**: Understand the use of complex mathematical operations in SQL / MongoDB
- **Problem**: Write a query to calculate the fare per mile for each ride and return the ride ids and their fare per mile, ordered by fare per mile in descending order.

**Problem 44:**

- **Prerequisite**: Understand the use of multiple JOINs in SQL / multiple Lookups in MongoDB
- **Problem**: Assuming there's another collection/table **`Passengers`** with **`passenger_id`** and **`name`** fields, write a query to return a list of all rides including the driver's name and passenger's name.

**Problem 45:**

- **Prerequisite**: Understand how to alter table schemas in SQL / adding and modifying fields in MongoDB documents
- **Problem**: Write a query to add a **`tip`** field to the **`Rides`** table / collection.