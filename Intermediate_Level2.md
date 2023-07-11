# Set 4 : Intermediate Level

We'll continue with the **`Rides`** table / collection from the previous set.

# MONGODB


**Problem 36:**

- **Prerequisite**: Understand using the MAX and MIN functions in SQL / using sort and limit in MongoDB
- **Problem**: Write a query to find the ride with the highest and lowest **`fare`**.

```
// Finding the ride with the highest fare
db.Rides.find().sort({ fare: -1 }).limit(1);

// Finding the ride with the lowest fare
db.Rides.find().sort({ fare: 1 }).limit(1);

```
**Problem 37:**

- **Prerequisite**: Understand using the GROUP BY clause in SQL / using aggregate in MongoDB
- **Problem**: Write a query to find the average **`fare`** and **`distance`** for each **`driver_id`**.

```

```
**Problem 38:**

- **Prerequisite**: Understand using HAVING clause in SQL / using match in MongoDB's aggregate pipeline
- **Problem**: Write a query to find **`driver_id`** that have completed more than 5 rides.

```

```
**Problem 39:**

- **Prerequisite**: Understand the use of INNER JOIN in SQL / Lookup in MongoDB
- **Problem**: Assuming there is another collection/table called **`Drivers`** with **`driver_id`** and **`name`** fields, write a query to find the name of the driver with the highest **`fare`**.

```

```
**Problem 40:**

- **Prerequisite**: Understand the concept of subqueries in SQL / using multiple stages in MongoDB's aggregate pipeline
- **Problem**: Write a query to find the top 3 drivers who have earned the most from fares. Return the drivers' ids and total earnings.

```

```
**Problem 41:**

- **Prerequisite**: Understand date and time functions in SQL / MongoDB
- **Problem**: Assuming there's a **`ride_date`** field of date type in the **`Rides`** table / collection, write a query to find all rides that happened in the last 7 days.

```

```
**Problem 42:**

- **Prerequisite**: Understand the concept of NULL values and how to handle them in SQL / MongoDB
- **Problem**: Write a query to find all rides where the **`end_location`** is not set.

```

```
**Problem 43:**

- **Prerequisite**: Understand the use of complex mathematical operations in SQL / MongoDB
- **Problem**: Write a query to calculate the fare per mile for each ride and return the ride ids and their fare per mile, ordered by fare per mile in descending order.

```

```
**Problem 44:**

- **Prerequisite**: Understand the use of multiple JOINs in SQL / multiple Lookups in MongoDB
- **Problem**: Assuming there's another collection/table **`Passengers`** with **`passenger_id`** and **`name`** fields, write a query to return a list of all rides including the driver's name and passenger's name.

```

```
**Problem 45:**

- **Prerequisite**: Understand how to alter table schemas in SQL / adding and modifying fields in MongoDB documents
- **Problem**: Write a query to add a **`tip`** field to the **`Rides`** table / collection.

```

```

# SQL


**Problem 36:**

- **Prerequisite**: Understand using the MAX and MIN functions in SQL / using sort and limit in MongoDB
- **Problem**: Write a query to find the ride with the highest and lowest **`fare`**.

```
-- Finding the ride with the highest fare
SELECT * FROM Rides WHERE fare = (SELECT MAX(fare) FROM Rides);

-- Finding the ride with the lowest fare
SELECT * FROM Rides WHERE fare = (SELECT MIN(fare) FROM Rides);

```
**Problem 37:**

- **Prerequisite**: Understand using the GROUP BY clause in SQL / using aggregate in MongoDB
- **Problem**: Write a query to find the average **`fare`** and **`distance`** for each **`driver_id`**.

```
SELECT driver_id, AVG(fare) AS averageFare, AVG(distance) AS averageDistance
FROM Rides
GROUP BY driver_id;

```
**Problem 38:**

- **Prerequisite**: Understand using HAVING clause in SQL / using match in MongoDB's aggregate pipeline
- **Problem**: Write a query to find **`driver_id`** that have completed more than 5 rides.

```
SELECT driver_id, COUNT(*) AS rideCount
FROM Rides
GROUP BY driver_id
HAVING COUNT(*) > 5;

```
**Problem 39:**

- **Prerequisite**: Understand the use of INNER JOIN in SQL / Lookup in MongoDB
- **Problem**: Assuming there is another collection/table called **`Drivers`** with **`driver_id`** and **`name`** fields, write a query to find the name of the driver with the highest **`fare`**.

```
SELECT Drivers.name
FROM Rides
INNER JOIN Drivers ON Rides.driver_id = Drivers.driver_id
WHERE Rides.fare = (SELECT MAX(fare) FROM Rides);

```
**Problem 40:**

- **Prerequisite**: Understand the concept of subqueries in SQL / using multiple stages in MongoDB's aggregate pipeline
- **Problem**: Write a query to find the top 3 drivers who have earned the most from fares. Return the drivers' ids and total earnings.

```
SELECT driver_id, SUM(fare) AS totalEarnings
FROM Rides
GROUP BY driver_id
ORDER BY totalEarnings DESC
LIMIT 3;

```
**Problem 41:**

- **Prerequisite**: Understand date and time functions in SQL / MongoDB
- **Problem**: Assuming there's a **`ride_date`** field of date type in the **`Rides`** table / collection, write a query to find all rides that happened in the last 7 days.

```
SELECT * FROM Rides WHERE ride_date >= CURRENT_DATE - INTERVAL 7 DAY;

```
**Problem 42:**

- **Prerequisite**: Understand the concept of NULL values and how to handle them in SQL / MongoDB
- **Problem**: Write a query to find all rides where the **`end_location`** is not set.

```
SELECT * FROM Rides WHERE end_location IS NULL;

```
**Problem 43:**

- **Prerequisite**: Understand the use of complex mathematical operations in SQL / MongoDB
- **Problem**: Write a query to calculate the fare per mile for each ride and return the ride ids and their fare per mile, ordered by fare per mile in descending order.

```
SELECT id, fare / distance AS farePerMile
FROM Rides
ORDER BY farePerMile DESC;

```
**Problem 44:**

- **Prerequisite**: Understand the use of multiple JOINs in SQL / multiple Lookups in MongoDB
- **Problem**: Assuming there's another collection/table **`Passengers`** with **`passenger_id`** and **`name`** fields, write a query to return a list of all rides including the driver's name and passenger's name.

```
SELECT Rides.id, Rides.start_location, Rides.end_location, Rides.driver_id, Drivers.name AS driver_name, Passengers.name AS passenger_name
FROM Rides
JOIN Drivers ON Rides.driver_id = Drivers.driver_id
JOIN Passengers ON Rides.passenger_id = Passengers.passenger_id;

```
**Problem 45:**

- **Prerequisite**: Understand how to alter table schemas in SQL / adding and modifying fields in MongoDB documents
- **Problem**: Write a query to add a **`tip`** field to the **`Rides`** table / collection.

```
ALTER TABLE Rides ADD COLUMN tip DECIMAL(6, 2);

```
