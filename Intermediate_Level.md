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
# MONGODB
**Problem 26:**

- **Prerequisite**: Understand creating tables in SQL / collections in MongoDB
- **Problem**: Create a **`Rides`** table / collection with the fields defined above.

```
db.createCollection("Rides", {
  validator: {
    $jsonSchema: {
      bsonType: "object",
      required: ["driver_id", "passenger_id", "start_location", "end_location", "distance", "ride_time", "fare"],
      properties: {
        id: {
          bsonType: "objectId"
        },
        driver_id: {
          bsonType: "objectId"
        },
        passenger_id: {
          bsonType: "objectId"
        },
        start_location: {
          bsonType: "string"
        },
        end_location: {
          bsonType: "string"
        },
        distance: {
          bsonType: "number"
        },
        ride_time: {
          bsonType: "number"
        },
        fare: {
          bsonType: "number"
        }
      }
    }
  }
});


```
**Problem 27:**

- **Prerequisite**: Understand inserting data into SQL tables / MongoDB collections
- **Problem**: Insert five rows / documents into the **`Rides`** table / collection with data of your choice.


```
db.Rides.insertMany([
  {
    _id: ObjectId(),
    driver_id: ObjectId(),
    passenger_id: ObjectId(),
    start_location: "Location A",
    end_location: "Location B",
    distance: 10.5,
    ride_time: 25.3,
    fare: 15.75
  },
  {
    _id: ObjectId(),
    driver_id: ObjectId(),
    passenger_id: ObjectId(),
    start_location: "Location C",
    end_location: "Location D",
    distance: 8.2,
    ride_time: 20.1,
    fare: 12.50
  },
  {
    _id: ObjectId(),
    driver_id: ObjectId(),
    passenger_id: ObjectId(),
    start_location: "Location E",
    end_location: "Location F",
    distance: 5.7,
    ride_time: 15.8,
    fare: 9.85
  },
  {
    _id: ObjectId(),
    driver_id: ObjectId(),
    passenger_id: ObjectId(),
    start_location: "Location G",
    end_location: "Location H",
    distance: 12.9,
    ride_time: 30.2,
    fare: 18.50
  },
  {
    _id: ObjectId(),
    driver_id: ObjectId(),
    passenger_id: ObjectId(),
    start_location: "Location I",
    end_location: "Location J",
    distance: 7.1,
    ride_time: 18.5,
    fare: 11.25
  }
]);


```
**Problem 28:**

- **Prerequisite**: Understand how to order data in SQL / MongoDB
- **Problem**: Write a query to fetch all rides, ordered by **`fare`** in descending order.


```
db.Rides.find().sort({ fare: -1 });

```
**Problem 29:**

- **Prerequisite**: Understand using math operations in SQL / MongoDB
- **Problem**: Write a query to calculate the total **`distance`** and total **`fare`** for all rides.

```
db.Rides.aggregate([
  { $group: { _id: null, totalDistance: { $sum: "$distance" }, totalFare: { $sum: "$fare" } } }
]);

```
**Problem 30:**

- **Prerequisite**: Understand how to use the AVG function in SQL / MongoDB's aggregate functions
- **Problem**: Write a query to calculate the average **`ride_time`** of all rides.


```
db.Rides.aggregate([
  { $group: { _id: null, averageRideTime: { $avg: "$ride_time" } } }
]);


```
**Problem 31:**

- **Prerequisite**: Understand using string patterns in SQL (LIKE clause) / using regex in MongoDB
- **Problem**: Write a query to fetch all rides whose **`start_location`** or **`end_location`** contains 'Downtown'.


```

db.Rides.find({
  $or: [
    { start_location: /Downtown/ },
    { end_location: /Downtown/ }
  ]
});

```
**Problem 32:**

- **Prerequisite**: Understand how to use the COUNT function in SQL / MongoDB's aggregate functions
- **Problem**: Write a query to count the number of rides for a given **`driver_id`**.

```
db.Rides.countDocuments({ driver_id: ObjectId("64ad967af83ed21d6eb2518e") });

```
**Problem 33:**

- **Prerequisite**: Understand data updating in SQL / MongoDB
- **Problem**: Write a query to update the **`fare`** of the ride with **`id`** 64ad967af83ed21d6eb2518d.


```

db.Rides.updateOne(
  { _id: ObjectId("64ad967af83ed21d6eb2518d")},
  { $set: { fare: 12.5 } }
);

```
**Problem 34:**

- **Prerequisite**: Understand using GROUP BY in SQL / MongoDB's aggregate functions
- **Problem**: Write a query to calculate the total **`fare`** for each **`driver_id`**.


```
db.Rides.aggregate([
  { $group: { _id: "$driver_id", totalFare: { $sum: "$fare" } } }
]);

```
**Problem 35:**

- **Prerequisite**: Understand data deletion in SQL / MongoDB
- **Problem**: Write a query to delete the ride with **`id`** 64ad967af83ed21d6eb2518d.

```

db.Rides.deleteOne({ _id: ObjectId("64ad967af83ed21d6eb2518d") });

```



# SQL
**Problem 26:**

- **Prerequisite**: Understand creating tables in SQL / collections in MongoDB
- **Problem**: Create a **`Rides`** table / collection with the fields defined above.

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
**Problem 27:**

- **Prerequisite**: Understand inserting data into SQL tables / MongoDB collections
- **Problem**: Insert five rows / documents into the **`Rides`** table / collection with data of your choice.


```
INSERT INTO Rides (id, driver_id, passenger_id, start_location, end_location, distance, ride_time, fare)
VALUES
  (1, 1001, 2001, 'Start 1', 'End 1', 5.2, 15, 10.5),
  (2, 1002, 2002, 'Start 2', 'End 2', 3.7, 10, 8.2),
  (3, 1003, 2003, 'Start 3', 'End 3', 8.5, 20, 15.6),
  (4, 1001, 2004, 'Start 4', 'End 4', 6.1, 12, 9.8),
  (5, 1002, 2005, 'Start 5', 'End 5', 2.9, 8, 6.3);

```
**Problem 28:**

- **Prerequisite**: Understand how to order data in SQL / MongoDB
- **Problem**: Write a query to fetch all rides, ordered by **`fare`** in descending order.

```
SELECT * FROM Rides ORDER BY fare DESC;

```
**Problem 29:**

- **Prerequisite**: Understand using math operations in SQL / MongoDB
- **Problem**: Write a query to calculate the total **`distance`** and total **`fare`** for all rides.


```
SELECT SUM(distance) AS totalDistance, SUM(fare) AS totalFare FROM Rides;

```
**Problem 30:**

- **Prerequisite**: Understand how to use the AVG function in SQL / MongoDB's aggregate functions
- **Problem**: Write a query to calculate the average **`ride_time`** of all rides.


```
SELECT AVG(ride_time) AS averageRideTime FROM Rides;

```
**Problem 31:**

- **Prerequisite**: Understand using string patterns in SQL (LIKE clause) / using regex in MongoDB
- **Problem**: Write a query to fetch all rides whose **`start_location`** or **`end_location`** contains 'Downtown'.


```
SELECT * FROM Rides WHERE start_location LIKE '%Downtown%' OR end_location LIKE '%Downtown%';

```
**Problem 32:**

- **Prerequisite**: Understand how to use the COUNT function in SQL / MongoDB's aggregate functions
- **Problem**: Write a query to count the number of rides for a given **`driver_id`**.


```
SELECT COUNT(*) AS rideCount FROM Rides WHERE driver_id = 1001;

```
**Problem 33:**

- **Prerequisite**: Understand data updating in SQL / MongoDB
- **Problem**: Write a query to update the **`fare`** of the ride with **`id`** 4.


```
UPDATE Rides SET fare = 12.5 WHERE id = 4;

```
**Problem 34:**

- **Prerequisite**: Understand using GROUP BY in SQL / MongoDB's aggregate functions
- **Problem**: Write a query to calculate the total **`fare`** for each **`driver_id`**.


```
SELECT driver_id, SUM(fare) AS totalFare FROM Rides GROUP BY driver_id;

```
**Problem 35:**

- **Prerequisite**: Understand data deletion in SQL / MongoDB
- **Problem**: Write a query to delete the ride with **`id`** 2.

```
DELETE FROM Rides WHERE id = 2;

```