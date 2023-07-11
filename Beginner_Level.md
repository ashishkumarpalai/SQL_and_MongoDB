# **MongoDB:**

In MongoDB, we're using a **`Customers`** collection. Each document in the collection represents one customer. Here is the schema of the **`Customers`** collection:


```
{
  "_id": ObjectId(), // a unique identifier created by MongoDB itself
  "name": String,
  "email": String,
  "address": String,
  "phone_number": String
}
```

**_id**: This field is a unique identifier for the document. MongoDB automatically generates and assigns an ObjectId to this field when we create a new document.

**name**: This field holds the name of the customer as a string.

**email**: This field holds the email address of the customer as a string.

**address**: This field holds the customer's address as a string.

**phone_number**: This field holds the customer's phone number as a string.


### create database

```
use database_name
```
### show all database

```
show dbs
```
### create collections

```
db.createCollection("Customers")
```

### show collections

```
show collections

```

### Insert a document into a collection:

```
db.collection_name.insertOne({ key: value })

```
### Find documents in a collection:

```
db.collection_name.find()

```

### Update a document in a collection:


```
db.collection_name.updateOne({ key: value }, { $set: { key: new_value } })

```

### Delete a document from a collection:

```
db.collection_name.deleteOne({ key: value })

```

**Problem 1:**

- **Prerequisite**: Understand creating tables in SQL / collections in MongoDB
- **Problem**: Create a **`Customers`** table / collection with the following fields: **`id`** (unique identifier), **`name`**, **`email`**, **`address`**, and **`phone_number`**.
```
db.createCollection("Customers")
```


**Problem 2:**

- **Prerequisite**: Understand inserting data into SQL tables / MongoDB collections
- **Problem**: Insert five rows / documents into the **`Customers`** table / collection with data of your choice.

```
db.Customers.insertMany([
    { id: 1, name: 'John Doe', email: 'john@example.com', address: '123 Main St', phone_number: '1234567890' },
    { id: 2, name: 'Jane Smith', email: 'jane@example.com', address: '456 Oak Ave', phone_number: '9876543210' },
    { id: 3, name: 'Alice Johnson', email: 'alice@example.com', address: '789 Elm Rd', phone_number: '4561237890' },
    { id: 4, name: 'Bob Williams', email: 'bob@example.com', address: '321 Pine Ln', phone_number: '7890123456' },
    { id: 5, name: 'Sarah Davis', email: 'sarah@example.com', address: '567 Maple Dr', phone_number: '5432109876' }
]);
```

**Problem 3:**

- **Prerequisite**: Understand basic data fetching in SQL / MongoDB
- **Problem**: Write a query to fetch all data from the **`Customers`** table / collection.

```
db.Customers.find()

```
**Problem 4:**

- **Prerequisite**: Understand how to select specific fields in SQL / MongoDB
- **Problem**: Write a query to select only the **`name`** and **`email`** fields for all customers.


```
db.Customers.find({}, { name: 1, email: 1 })

```
**Problem 5:**

- **Prerequisite**: Understand basic WHERE clause in SQL / MongoDB's find method
- **Problem**: Write a query to fetch the customer with the **`id`** of 3.

```
db.Customers.find({ id: 3 });
```

**Problem 6:**

- **Prerequisite**: Understand using string patterns in SQL (LIKE clause) / using regex in MongoDB
- **Problem**: Write a query to fetch all customers whose **`name`** starts with 'A'.

```
db.Customers.find({ name: /^A/ });
```
**Problem 7:**

- **Prerequisite**: Understand how to order data in SQL / MongoDB
- **Problem**: Write a query to fetch all customers, ordered by **`name`** in descending order.

```
db.Customers.find().sort({ name: -1 });
```
**Problem 8:**

- **Prerequisite**: Understand data updating in SQL / MongoDB
- **Problem**: Write a query to update the **`address`** of the customer with **`id`** 4.

```
db.Customers.updateOne({ id: 4 }, { $set: { address: 'New Address' } });
```
**Problem 9:**

- **Prerequisite**: Understand how to limit results in SQL / MongoDB
- **Problem**: Write a query to fetch the top 3 customers when ordered by **`id`** in ascending order.

```
db.Customers.find().sort({ id: 1 }).limit(3);
```
**Problem 10:**

- **Prerequisite**: Understand data deletion in SQL / MongoDB
- **Problem**: Write a query to delete the customer with **`id`** 2.

```
db.Customers.deleteOne({ id: 2 });
```

**Problem 11:**

- **Prerequisite**: Understand how to count rows / documents in SQL / MongoDB
- **Problem**: Write a query to count the number of customers.

```
db.Customers.countDocuments();
```
**Problem 12:**

- **Prerequisite**: Understand how to skip rows / documents in SQL / MongoDB
- **Problem**: Write a query to fetch all customers except the first two when ordered by **`id`** in ascending order.

```
db.Customers.find().sort({ id: 1 }).skip(2);
```

**Problem 13:**

- **Prerequisite**: Understand filtering with multiple conditions in SQL / MongoDB
- **Problem**: Write a query to fetch all customers whose **`id`** is greater than 2 and **`name`** starts with 'B'.


```
db.Customers.find({ id: { $gt: 2 }, name: /^B/ });
```
**Problem 14:**

- **Prerequisite**: Understand how to use OR conditions in SQL / MongoDB
- **Problem**: Write a query to fetch all customers whose **`id`** is less than 3 or **`name`** ends with 's'.


```
db.Customers.find({ $or: [{ id: { $lt: 3 } }, { name: /s$/ }] });

```
**Problem 15:**

- **Prerequisite**: Understand how to use NULL checks in SQL / MongoDB
- **Problem**: Write a query to fetch all customers where the **`phone_number`** field is not set or is null.

```
db.Customers.find({ $or: [{ phone_number: null }, { phone_number: '' }] });
```













### **SQL:**

In SQL, we're using a **`Customers`** table. Each row in the table represents one customer. Here is the schema of the **`Customers`** table:

```
CREATE TABLE Customers (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100),
    address VARCHAR(255),
    phone_number VARCHAR(50)
);

```

**id**: This field is a unique identifier for the row. We manually assign a unique INT to this field when we create a new row. It's marked as the PRIMARY KEY.

**name**: This field holds the name of the customer as a variable character string (VARCHAR) of length 100.

**email**: This field holds the email address of the customer as a variable character string (VARCHAR) of length 100.

**address**: This field holds the customer's address as a variable character string (VARCHAR) of length 255.

**phone_number**: This field holds the customer's phone number as a variable character string (VARCHAR) of length 50.

**Problem 1:**

- **Prerequisite**: Understand creating tables in SQL / collections in MongoDB
- **Problem**: Create a **`Customers`** table / collection with the following fields: **`id`** (unique identifier), **`name`**, **`email`**, **`address`**, and **`phone_number`**.

**Problem 2:**

- **Prerequisite**: Understand inserting data into SQL tables / MongoDB collections
- **Problem**: Insert five rows / documents into the **`Customers`** table / collection with data of your choice.

**Problem 3:**

- **Prerequisite**: Understand basic data fetching in SQL / MongoDB
- **Problem**: Write a query to fetch all data from the **`Customers`** table / collection.

**Problem 4:**

- **Prerequisite**: Understand how to select specific fields in SQL / MongoDB
- **Problem**: Write a query to select only the **`name`** and **`email`** fields for all customers.

**Problem 5:**

- **Prerequisite**: Understand basic WHERE clause in SQL / MongoDB's find method
- **Problem**: Write a query to fetch the customer with the **`id`** of 3.

**Problem 6:**

- **Prerequisite**: Understand using string patterns in SQL (LIKE clause) / using regex in MongoDB
- **Problem**: Write a query to fetch all customers whose **`name`** starts with 'A'.

**Problem 7:**

- **Prerequisite**: Understand how to order data in SQL / MongoDB
- **Problem**: Write a query to fetch all customers, ordered by **`name`** in descending order.

**Problem 8:**

- **Prerequisite**: Understand data updating in SQL / MongoDB
- **Problem**: Write a query to update the **`address`** of the customer with **`id`** 4.

**Problem 9:**

- **Prerequisite**: Understand how to limit results in SQL / MongoDB
- **Problem**: Write a query to fetch the top 3 customers when ordered by **`id`** in ascending order.

**Problem 10:**

- **Prerequisite**: Understand data deletion in SQL / MongoDB
- **Problem**: Write a query to delete the customer with **`id`** 2.

**Problem 11:**

- **Prerequisite**: Understand how to count rows / documents in SQL / MongoDB
- **Problem**: Write a query to count the number of customers.

**Problem 12:**

- **Prerequisite**: Understand how to skip rows / documents in SQL / MongoDB
- **Problem**: Write a query to fetch all customers except the first two when ordered by **`id`** in ascending order.

**Problem 13:**

- **Prerequisite**: Understand filtering with multiple conditions in SQL / MongoDB
- **Problem**: Write a query to fetch all customers whose **`id`** is greater than 2 and **`name`** starts with 'B'.

**Problem 14:**

- **Prerequisite**: Understand how to use OR conditions in SQL / MongoDB
- **Problem**: Write a query to fetch all customers whose **`id`** is less than 3 or **`name`** ends with 's'.

**Problem 15:**

- **Prerequisite**: Understand how to use NULL checks in SQL / MongoDB
- **Problem**: Write a query to fetch all customers where the **`phone_number`** field is not set or is null.