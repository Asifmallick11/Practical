# Practical 1 : Install MongoDB and create a database with a collection. Perform basic CRUD operations(Create, Read, Update, Delete).

```javascript

// Step 1 : Create a Database and then run the following command into the mongodb shell

db["users"].insertMany([  { "user_id": 1, "user_name": "Rahul Sharma", "user_address": "Mumbai, Maharashtra" },
  { "user_id": 2, "user_name": "Priya Verma", "user_address": "Delhi, India" },
  { "user_id": 3, "user_name": "Amit Kumar", "user_address": "Bangalore, Karnataka" },
  { "user_id": 4, "user_name": "Neha Singh", "user_address": "Hyderabad, Telangana" },
  { "user_id": 5, "user_name": "Sahil Gupta", "user_address": "Pune, Maharashtra" },
  { "user_id": 6, "user_name": "Anjali Mishra", "user_address": "Chennai, Tamil Nadu" },
  { "user_id": 7, "user_name": "Rohit Agarwal", "user_address": "Kolkata, West Bengal" },
  { "user_id": 8, "user_name": "Sneha Patel", "user_address": "Ahmedabad, Gujarat" },
  { "user_id": 9, "user_name": "Vikram Joshi", "user_address": "Jaipur, Rajasthan" },
  { "user_id": 10, "user_name": "Kiran Reddy", "user_address": "Visakhapatnam, Andhra Pradesh" },
  { "user_id": 11, "user_name": "Manish Tiwari", "user_address": "Lucknow, Uttar Pradesh" },
  { "user_id": 12, "user_name": "Simran Kaur", "user_address": "Chandigarh" },
  { "user_id": 13, "user_name": "Aditya Mehta", "user_address": "Surat, Gujarat" },
  { "user_id": 14, "user_name": "Pooja Nair", "user_address": "Kochi, Kerala" },
  { "user_id": 15, "user_name": "Yashwant Rao", "user_address": "Indore, Madhya Pradesh" },
  { "user_id": 16, "user_name": "Aarav Malhotra", "user_address": "Nashik, Maharashtra" },
  { "user_id": 17, "user_name": "Divya Desai", "user_address": "Vadodara, Gujarat" },
  { "user_id": 18, "user_name": "Harshit Jain", "user_address": "Bhopal, Madhya Pradesh" },
  { "user_id": 19, "user_name": "Kavya Shetty", "user_address": "Mangalore, Karnataka" },
  { "user_id": 20, "user_name": "Nikhil Chauhan", "user_address": "Shimla, Himachal Pradesh" },
  { "user_id": 21, "user_name": "Farhan Khan", "user_address": "Aligarh, Uttar Pradesh" },
  { "user_id": 22, "user_name": "Zoya Siddiqui", "user_address": "Patna, Bihar" },
  { "user_id": 23, "user_name": "Arjun Sinha", "user_address": "Ranchi, Jharkhand" },
  { "user_id": 24, "user_name": "Tanvi Kapoor", "user_address": "Gurgaon, Haryana" },
  { "user_id": 25, "user_name": "Ritesh Das", "user_address": "Bhubaneswar, Odisha" },
  { "user_id": 26, "user_name": "Meera Krishnan", "user_address": "Madurai, Tamil Nadu" },
  { "user_id": 27, "user_name": "Shubham Roy", "user_address": "Guwahati, Assam" },
  { "user_id": 28, "user_name": "Lavanya Iyer", "user_address": "Coimbatore, Tamil Nadu" },
  { "user_id": 29, "user_name": "Jay Patel", "user_address": "Rajkot, Gujarat" },
  { "user_id": 30, "user_name": "Aisha Mir", "user_address": "Srinagar, Jammu & Kashmir" }])

// Step 2 : FindOne Operation 

db["users"].find()

// Step 3 : FindOne with user_id Operation

db["users"].findOne({user_id : 3})

// Step 4 : DeleteOne Operation

db["users"].deleteOne({user_id : 3})

// Step 5 : UpdateOne Operation

db["users"].updateOne({user_id : 2} , {$set : {user_address : "San Francisco , USA"}})

// Step 6 : Last Step 

db["users"].find().pretty()

```

## Conclusion : 
- In this way we have Installed MongoDB and created a database with a collection and  Performed basic CRUD operations(Create, Read, Update, Delete).

---

# Practical 2 : To write NoSQL queries to understand the concept of an Open Source Database Management System such as MongoDB, and perform CRUD, Indexing, Sharding, and Deployment operations.

```javascript

// Step 1: Start MongoDB Server
mongod --dbpath "C:\data\db" --port 27017

// Step 2: Start MongoDB Shell
mongosh --port 27017

// CRUD OPERATIONS
// Create/Select Database
use vysya

// Insert Document
db.vysya.insertOne({
  course: "ADT",
  details: { lab: "6 months", Trainer: "Natarajan" },
  category: "Programming language"
})

// Read (Display/Search)
db.vysya.find().pretty()

// Update
db.vysya.updateOne(
  { course: "ADT" },
  { $set: { course: "Advanced Database Technology" } }
)

// Delete
db.vysya.deleteMany({})

// INDEXING OPERATION
db.vysya.createIndex({ regNo: 1 })


// SHARDING OPERATION

// Step 1: Create Collection
db.createCollection("movie1")

// Step 2: Enable Sharding on Database
sh.enableSharding("vysya")

// Step 3: Shard Collection
sh.shardCollection("vysya.movie1", { title: 1 })

// Step 4: Check Shard Distribution
db.movie1.getShardDistribution()

// Step 5: Check Shard Status
sh.status()

// DEPLOYMENT OPERATION (REPLICA SET)
// Step 1: Initialize Replica Set
rs.initiate({
  _id: "rs0",
  members: [
    { _id: 0, host: "mongodb0:27017" },
    { _id: 1, host: "mongodb1:27017" },
    { _id: 2, host: "mongodb2:27017" }
  ]
})

// Step 2: Check Replica Set Status
rs.status()

```

## Conclusion : 
- Thus , In this way we have performed CRUD, Indexing, Sharding, and Deployment operations on a MongoDB Database .

---

# Practical 3 : To write NOSQL QUERIES to understand the concept of Open Source Database Management System such as CASSANDRA.

## PROCEDURE:
- Step 1: Start the CASSANDRA Server (Cassandra) using CMD.
- Step 2: Start the Client (CQLSH.py) using CMD.
- Step 3: Perform the Cassandra Table Operation, Curd Operation and CQL Types.

## Cassandra Table Operations:
- 1. Create Key Space in Cassandra. CREATE KEYSPACE <identifier> WITH <properties>
- 2. To Create Cassandra Table, Using Create Command.
- 3. To Change the structure of the table, Using Alter Command.
- 4. To delete the existing table in Cassandra, Using Truncate Command.
- 5. To Insert the values in CQL, use insert command
- 6. The SELECT command is used to read data from Cassandra table
- 7. The UPDATE command is used to update the existing data in a Cassandra.
- 8. The DELETE command is used to delete data from Cassandra table

- Step 4 : Close the command prompt
- Step 5 : Stop the Server

```shell

# Pull the latest cassandra image from docker hub
docker pull cassandra:latest

# Make sure that the image is pulled
docker images

# Run the cassandra images 
docker run --name cassandra-container -d -p 9042:9042 cassandra:latest

# Cassandra conatiner logs
docker logs -f cassandra-container

# Exec into the container to run cqlsh commands
docker exec -it cassandra-container cqlsh

# Create a keyspace names vysya with replication factor 3 and class as SimpleStratergy
CREATE KEYSPACE vysya WITH replication = {'class' : 'SimpleStrategy' , 'replication-factor' : 3} ;

# USE the vysya keyspace
USE vysya ;

# Create table 
CREATE TABLE VVT(Id int PRIMARY KEY , name text , city text , fees variant);

# ALter table
ALTER TABLE VVT ADD email text ;

# Select Statement
select * from vvt ;

# Drop Email
ALTER TABLE VVT DROP email ;

select * from vvt ;

# TRUNCATE 
TRUNCATE VVT ;

# Insert into vvt
INSERT INTO VVT(id , fees , name , city) VALUES(1 , 5000 , 'Natarajan S' , 'Namakkal') ;

select * from vvt ; 

# Update 

UPDATE VVT SET fees=500 , name='Natarajan S' WHERE id=1 ;

select * from vvt ; 

# Inserting more values

INSERT INTO VVT(id , fees , name , city) VALUES(2 , 5000 , 'Rahul' , 'Aathur') ;
INSERT INTO VVT(id , fees , name , city) VALUES(3 , 5000 , 'Partha' , 'Salem') ;

select * from vvt ;

# Deleting 
delete from vvt where id = 3 ;

select * from vvt ;

# Describing table 
describe table vvt ;

```

## Conclusion : 
- Thus , the Cassandra distribution database was successfully set up using Docker and all NOSQL operations (CREATE , ALTER , INSERT , UPDATE , DELETE , TRUNCATE , DROP) were performed using CQL .

---

# Practical 4 : To create an aggregate data model in MongoDB for an online store and query product reviews using the aggregation framework.

## Implemetation :

### Step 1: Start MongoDB and Open Compass
- Open MongoDB Compass.
- Connect to mongodb://localhost:27017.
- Create a new database named OnlineStoreDB.

### Step 2: Create Collections
- Inside OnlineStoreDB, create two collections:
- users
- products

### Step 3: Insert Documents

users Collection
```javascript
[
  {
    "_id": ObjectId("6740a1111111111111111111"),
    "name": "Ganesh Deshpande",
    "email": "ganesh@example.com",
    "joinDate": ISODate("2024-05-01")
  },
  {
    "_id": ObjectId("6740a2222222222222222222"),
    "name": "Suresh Wamble",
    "email": "suresh@example.com",
    "joinDate": ISODate("2024-06-01")
  }
]
```

products Collection
```javascript
{
  "name": "Wireless Headphones",
  "category": "Electronics",
  "price": 2999,
  "stock": 120,
  "reviews": [
    {
      "userId": ObjectId("6740a1111111111111111111"),
      "rating": 5,
      "comment": "Amazing sound quality!",
      "date": ISODate("2025-09-10")
    },
    {
      "userId": ObjectId("6740a2222222222222222222"),
      "rating": 4,
      "comment": "Comfortable but a bit pricey.",
      "date": ISODate("2025-09-12")
    }
  ]
}
```

### Step 4: Run Aggregation Queries in Compass
#### Query 1: Get all reviews of a product
- Go to Aggregations tab in MongoDB Compass → Choose collection products.
- Add the following pipeline stages:

```javascript 
[
  { "$match": { "name": "Wireless Headphones" } },
  { "$unwind": "$reviews" },
  { "$project": {
      "_id": 0,
      "product": "$name",
      "rating": "$reviews.rating",
      "comment": "$reviews.comment",
      "userId": "$reviews.userId",
      "date": "$reviews.date"
  }}
]
```

#### Query 2: Join with Users Collection
- Run this aggregation in products → Aggregations tab:

```javascript
[
  { "$match": { "name": "Wireless Headphones" } },
  { "$unwind": "$reviews" },
  { "$lookup": {
      "from": "users",
      "localField": "reviews.userId",
      "foreignField": "_id",
      "as": "userDetails"
  }},
  { "$unwind": "$userDetails" },
  { "$project": {
      "_id": 0,
      "product": "$name",
      "rating": "$reviews.rating",
      "comment": "$reviews.comment",
      "reviewer": "$userDetails.name",
      "email": "$userDetails.email",
      "date": "$reviews.date"
  }}
]
``` 

## Conclusion : 
- In this way we have created an aggregate data model in MongoDB for an online store and query product reviews using the aggregation framework.

---

# Practical 5 : To implement the Map-Reduce operation in MongoDB for aggregating and calculating the total sales value for each product category. 

## Procedure :

```javascript 
// Step 1: Create a Collection and Insert Sample Documents

db.sales.insertMany([
 { _id: 1, product: "Laptop", category: "Electronics", quantity: 2, price: 50000 },
 { _id: 2, product: "Shirt", category: "Clothing", quantity: 3, price: 1000 },
 { _id: 3, product: "Phone", category: "Electronics", quantity: 1, price: 20000 },
 { _id: 4, product: "Jeans", category: "Clothing", quantity: 2, price: 2000 },
 { _id: 5, product: "Fridge", category: "Appliances", quantity: 1, price: 30000 }
]);

// Step 2: Define the Map Function
var mapFunction = function() {
 var salesAmount = this.quantity * this.price;
 emit(this.category, salesAmount);
};

// Step 3: Define the Reduce Function
var reduceFunction = function(keyCategory, valuesSales) {
 return Array.sum(valuesSales);
};

// Step 4: Run MapReduce Command
db.sales.mapReduce(
 mapFunction,
 reduceFunction,
 {
 out: "category_sales_totals"
 }
);

// Step 5: View the Results
db.category_sales_totals.find().pretty();
Expected Output:
{ "_id" : "Electronics", "value" : 120000 }
{ "_id" : "Clothing", "value" : 7000 }
{ "_id" : "Appliances", "value" : 30000 }
```

## Conclusion : 
- In this way we have implemented the Map-Reduce operation in MongoDB for aggregating and calculating the total sales value for each product category.

---

# Practical 6 : To study MongoDB, create a database and a schema-less collection. 

## Procedure :

```javascript 
// Commands
// Switch to (or create) a database
use universityDB 

// Create a collection (implicitly when inserting)
db.students.insertOne({ name: "Rahul", course: "B.Sc CS" })

// Insert Multiple Documents
// Aim
// To insert multiple documents with varying structures.
// Commands

db.students.insertMany([
 { name: "Rahul", course: "B.Sc CS", year: 3 },
 { name: "Priya", courses: ["Big Data", "AI"], placement: true },
 { name: "Ankit", marks: { math: 85, cs: 92 }, year: 2 },
 { rollNo: 104, name: "Sneha", internship: { company: "TCS", duration: "3 months" }},
 { name: "Amit", skills: ["Java", "Python"], cgpa: 8.9 }
])

// Basic Queries
// Aim
// To retrieve documents using find().
// Commands
// Display all documents

db.students.find().pretty()

// Find student by name

db.students.find({ name: "Rahul" })

// Project only name & course

db.students.find({}, { name: 1, course: 1, _id: 0 })

// Conditional Queries
// Aim
// To query nested fields and apply conditions.
// Commands
// Students with cs marks greater than 90

db.students.find({ "marks.cs": { $gt: 90 } })

// Students with placements

db.students.find({ placement: true })

// Students who have internship details

db.students.find({ internship: { $exists: true } })

// Array Queries
// Aim
// To query array fields.
// Commands
// Students having Python skill

db.students.find({ skills: "Python" })

//Sorting & Limiting Results
//Aim
//To apply sorting, limiting, and skipping.
//Commands

// Sort by CGPA descending

db.students.find().sort({ cgpa: -1 })

// Limit output to 2 documents

db.students.find().limit(2)

// Skip first 2 results

db.students.find().skip(2)

// Aggregation
// Aim
// To perform aggregation operations.
// Commands

// Average CGPA

db.students.aggregate([
 { $match: { cgpa: { $exists: true } } },
 { $group: { _id: null, avgCGPA: { $avg: "$cgpa" } } }
])

// Count students with placements

db.students.aggregate([
 { $match: { placement: true } },
 { $count: "PlacedStudents" }
])

// Update & Delete
// Aim
// To update and delete documents.
// Commands

// Update one student’s year

db.students.updateOne({ name: "Rahul" }, { $set: { year: 4 } })

// Update many: set placement = false

db.students.updateMany({}, { $set: { placement: false } })

// Delete one

db.students.deleteOne({ name: "Sneha" })

// Delete all

db.students.deleteMany({})
```

## Conclusion : 
- In this way we have created a schema-less collection in MongoDB. Inserted documents with varying structures and query them.

---

# Practical 7 : To demonstrate how to create a CouchDB database, insert JSON documents, and query data using Mango queries.

## Procedure :

```shell

docker pull couchdb

docker run -d --name my-couchdb -p 5984:5984 -e COUCHDB_USER=admin  -e COUCHDB_PASSWORD=admin123 couchdb

```

```javascript 

// Description:
// 1. CouchDB runs on: http://127.0.0.1:5984/_utils/
// 2. Documents are stored as JSON objects with key-value pairs.
// 3. Each document has:
// _id: Unique identifier
// _rev: Revision number for version control

// Steps:
// 1. Open CouchDB in your browser:
// URL: http://127.0.0.1:5984/_utils/
// 2. Create a new database named blogdb.
// 3. Insert the following documents representing blog posts.

// Sample Documents (Posts):
{
  "type": "post",
  "title": "Understanding NoSQL Databases",
  "author": "Dr. Anup Kadble",
  "date": "2025-10-06",
  "tags": ["database", "NoSQL", "CouchDB"],
  "content": "This post introduces NoSQL databases and explains document-oriented models."
}
{
  "type": "post",
  "title": "AI Applications in Agriculture",
  "author": "Ganesh Pande",
  "date": "2025-09-20",
  "tags": ["AI", "Agriculture", "IoT"],
  "content": "Exploring AI-driven solutions for smart farming and irrigation."
}
{
  "type": "post",
  "title": "Smart Irrigation",
  "author": "Mangesh Deshpande",
  "tags": ["IoT", "Agriculture"],
  "content": "IoT sensors improve water efficiency."
}

// Creating Index for Mango Queries:
// To optimize queries, create indexes on the author and tags fields.
// Step 1: Create Index on author

{
  "index": { "fields": ["author"] },
  "name": "author-index",
  "type": "json"
}

// Step 2: Create Index on tags
{
  "index": { "fields": ["tags"] },
  "name": "tags-index",
  "type": "json"
}

// Performing Mango Queries:

// 1. Query posts by author:
{
  "selector": {
    "author": "Dr. Anup Kadble"
  },
  "fields": ["title", "author", "tags", "content"]
}

// 2. Query posts containing a specific tag (e.g., “AI”):
{
  "selector": {
    "tags": { "$elemMatch": { "$eq": "AI" } }
  },
  "fields": ["title", "author", "tags"]
}

// 3. Query posts written after a certain date:
{
  "selector": {
    "date": { "$gt": "2025-09-30" }
  },
  "fields": ["title", "author", "date"]
}

// 4. Retrieve all posts sorted by date (descending):
{
  "selector": { "type": "post" },
  "fields": ["title", "author", "date"],
  "sort": [{ "date": "desc" }]
}

```

## Conclusion : 
- In this way we have demonstrated how to create a CouchDB database, insert JSON documents, and query data using Mango queries.

---

# Practical 8 : To design and implement a relational database schema for a Library Management System using PostgreSQL . To perform SQL queries related to book transactions such as issue, return, and fine management . To understand entity relationships, normalization, and integrity constraints in relational databases.

## Procedure :

```sql

-- Step 1: Create Database
CREATE DATABASE LibraryDB;
\c LibraryDB;
-- Step 2: Create Tables
CREATE TABLE Book (
  Book_ID INT PRIMARY KEY,
  Title VARCHAR(100),
  Author VARCHAR(100),
  Publisher VARCHAR(100),
  Year INT,
  ISBN VARCHAR(20),
  Category VARCHAR(50)
);

CREATE TABLE Member (
  Member_ID INT PRIMARY KEY,
  Name VARCHAR(100),
  Address VARCHAR(150),
  Phone VARCHAR(15),
  Email VARCHAR(100),
  Membership_Date DATE
);

CREATE TABLE Staff (
  Staff_ID INT PRIMARY KEY,
  Name VARCHAR(100),
  Designation VARCHAR(50),
  Contact VARCHAR(15)
);

CREATE TABLE Issue_Return (
  Transaction_ID INT PRIMARY KEY,
  Book_ID INT REFERENCES Book(Book_ID),
  Member_ID INT REFERENCES Member(Member_ID),
  Issue_Date DATE,
  Return_Date DATE,
  Status VARCHAR(20)
);

CREATE TABLE Fine (
  Fine_ID INT PRIMARY KEY,
  Transaction_ID INT REFERENCES Issue_Return(Transaction_ID),
  Amount DECIMAL(6,2),
  Paid_Status VARCHAR(10)
);

-- Step 3: Sample Data Insertion
INSERT INTO Book VALUES
(101, 'Database Systems', 'Elmasri', 'Pearson', 2022, '9780132147833', 'Education'),
(102, 'Operating Systems', 'Silberschatz', 'Wiley', 2021, '9780470128725', 'Technology'),
(103, 'Clean Code', 'Robert Martin', 'Prentice Hall', 2019, '9780132350884', 'Programming');

INSERT INTO Member VALUES
(1, 'John Doe', 'Pune', '9999999999', 'john@gmail.com', '2024-01-12'),
(2, 'Alice Smith', 'Mumbai', '8888888888', 'alice@gmail.com', '2024-02-15');

INSERT INTO Staff VALUES
(1, 'Ravi Sharma', 'Librarian', '7777777777');

INSERT INTO Issue_Return VALUES
(1, 101, 1, '2024-10-01', '2024-10-10', 'Returned'),
(2, 102, 2, '2024-10-05', NULL, 'Issued');

INSERT INTO Fine VALUES
(1, 1, 50.00, 'Paid');

-- Step 4: Execute Queries

-- List all books
SELECT * FROM Book;

-- Find all issued books
SELECT Book_ID, Member_ID, Issue_Date
FROM Issue_Return
WHERE Status = 'Issued';

-- Show overdue books
SELECT * FROM Issue_Return
WHERE Return_Date < CURRENT_DATE AND Status = 'Issued';

-- Count total books by category
SELECT Category, COUNT(*) AS TotalBooks
FROM Book
GROUP BY Category;

-- Calculate total fine collected
SELECT SUM(Amount) AS TotalFine
FROM Fine
WHERE Paid_Status = 'Paid';

```

## Conclusion : 
- In this way we have designed a relational database schema for a library management system and query book transaction

---

# Practical 9 : Design an Relational Database Schema for a Hospital Management System and Manage Patients , Doctors , Appointments and Treatments

## Procedure :

```sql

CREATE TABLE Patients (
 PatientID INT AUTO_INCREMENT PRIMARY KEY ,
 Name VARCHAR(100),
 DOB DATE,
 Gender VARCHAR(10),
 Contact VARCHAR(15),
 Address TEXT,
 BloodGroup VARCHAR(5),
 DateRegistered DATE
);

CREATE TABLE Departments (
 DeptID INT AUTO_INCREMENT PRIMARY KEY ,
 DeptName VARCHAR(50),
 Location VARCHAR(100)
);

CREATE TABLE Doctors (
 DoctorID INT AUTO_INCREMENT PRIMARY KEY ,
 Name VARCHAR(100),
 Specialization VARCHAR(50),
 Phone VARCHAR(15),
 Email VARCHAR(100),
 Department INT,
 FOREIGN KEY (Department) REFERENCES Departments(DeptID)
);

CREATE TABLE Appointments (
 AppointmentID INT AUTO_INCREMENT PRIMARY KEY ,
 PatientID INT,
 DoctorID INT,
 AppointmentDate DATE,
 Time TIME,
 Status VARCHAR(20),
 FOREIGN KEY (PatientID) REFERENCES Patients(PatientID),
 FOREIGN KEY (DoctorID) REFERENCES Doctors(DoctorID)
);

CREATE TABLE Treatments (
 TreatmentID INT AUTO_INCREMENT PRIMARY KEY ,
 AppointmentID INT,
 Diagnosis TEXT,
 Prescription TEXT,
 TreatmentDate DATE,
 Charges DECIMAL(10,2),
 FOREIGN KEY (AppointmentID) REFERENCES
Appointments(AppointmentID)
);

CREATE TABLE Billing (
 BillID INT  AUTO_INCREMENT PRIMARY KEY ,
 PatientID INT,
 TotalAmount DECIMAL(10,2),
 PaymentDate DATE,
 PaymentStatus VARCHAR(20),
 FOREIGN KEY (PatientID) REFERENCES Patients(PatientID)
);

```

```sql
INSERT INTO Departments (DeptID, DeptName, Location) VALUES
(1, 'Cardiology', 'Block A - 1st Floor'),
(2, 'Neurology', 'Block B - 2nd Floor'),
(3, 'Orthopedics', 'Block C - 3rd Floor'),
(4, 'Dermatology', 'Block D - Ground Floor');

-- ==============================
-- 2. PATIENTS (Fixed IDs)
-- ==============================
INSERT INTO Patients (PatientID, Name, DOB, Gender, Contact, Address, BloodGroup, DateRegistered) VALUES
(1, 'Rahul Sharma', '1990-02-14', 'Male', '9876543210', 'Delhi, India', 'A+', '2024-01-10'),
(2, 'Priya Singh',  '1985-07-22', 'Female', '9123456780', 'Mumbai, India', 'B+', '2024-02-18'),
(3, 'Amit Verma',   '1992-11-05', 'Male', '9988776655', 'Kolkata, India', 'O+', '2024-03-02'),
(4, 'Sara Khan',    '1996-04-19', 'Female', '9090909090', 'Hyderabad, India', 'AB+', '2024-04-11'),
(5, 'John Mathew',  '1988-09-12', 'Male', '9456123780', 'Chennai, India', 'A-', '2024-05-15');

-- ==============================
-- 3. DOCTORS (Fixed IDs + Valid Dept IDs)
-- ==============================
INSERT INTO Doctors (DoctorID, Name, Specialization, Phone, Email, Department) VALUES
(1, 'Dr. Arvind Patel', 'Cardiologist', '9000011111', 'arvind@hospital.com', 1),
(2, 'Dr. Neha Kapoor',  'Neurologist',  '9000022222', 'neha@hospital.com', 2),
(3, 'Dr. Rohit Menon',  'Orthopedic',   '9000033333', 'rohit@hospital.com', 3),
(4, 'Dr. Shalini Rao',  'Dermatologist','9000044444', 'shalini@hospital.com', 4),
(5, 'Dr. David Joseph', 'Neurologist',  '9000055555', 'david@hospital.com', 2);

-- ==============================
-- 4. APPOINTMENTS (Fixed IDs)
-- ==============================
INSERT INTO Appointments (AppointmentID, PatientID, DoctorID, AppointmentDate, Time, Status) VALUES
(1, 1, 1, '2024-05-10', '10:00:00', 'Completed'),
(2, 2, 2, '2024-06-15', '12:00:00', 'Completed'),
(3, 3, 3, '2025-11-20', '15:30:00', 'Upcoming'),
(4, 4, 3, '2025-11-18', '11:00:00', 'Upcoming'),
(5, 5, 5, '2024-07-22', '14:00:00', 'Completed'),
(6, 1, 5, '2024-09-10', '16:00:00', 'Completed');

-- ==============================
-- 5. TREATMENTS (Valid Appointment IDs: 5, 6)
-- ==============================
INSERT INTO Treatments (TreatmentID, AppointmentID, Diagnosis, Prescription, TreatmentDate, Charges) VALUES
(1, 5, 'Migraine Pain', 'Painkillers & Rest', '2024-07-22', 1200.00),
(2, 6, 'Nerve Weakness', 'Vitamin Supplements', '2024-09-10', 1500.00);

-- ==============================
-- 6. BILLING (Valid Patient IDs: 1–5)
-- ==============================
INSERT INTO Billing (BillID, PatientID, TotalAmount, PaymentDate, PaymentStatus) VALUES
(1, 1, 2000.00, '2024-05-10', 'Paid'),
(2, 2, 3500.00, '2024-06-15', 'Paid'),
(3, 3, 1500.00, '2024-07-20', 'Pending'),
(4, 4, 5000.00, '2024-09-22', 'Paid'),
(5, 5, 1800.00, '2024-10-05', 'Pending');

```

```sql
-- 1. List all appointments with patient and doctor names
SELECT a.AppointmentID, p.Name AS Patient, d.Name AS Doctor, 
a.AppointmentDate, a.Status
FROM Appointments a
JOIN Patients p ON a.PatientID = p.PatientID
JOIN Doctors d ON a.DoctorID = d.DoctorID;

-- 2. Find all upcoming appointments for a specific doctor
SELECT p.Name AS Patient, a.AppointmentDate, a.Time
FROM Appointments a
JOIN Patients p ON a.PatientID = p.PatientID
WHERE a.DoctorID = 3 AND a.AppointmentDate >= CURRENT_DATE;

-- 3. Get total revenue collected by hospital
SELECT SUM(TotalAmount) AS TotalRevenue
FROM Billing
WHERE PaymentStatus = 'Paid';

-- 4. View all treatments given by a specific doctor
SELECT d.Name AS Doctor, p.Name AS Patient, t.Diagnosis, t.Prescription, 
t.TreatmentDate
FROM Treatments t
JOIN Appointments a ON t.AppointmentID = a.AppointmentID
JOIN Doctors d ON a.DoctorID = d.DoctorID
JOIN Patients p ON a.PatientID = p.PatientID
WHERE d.DoctorID = 5;

-- 5. Count total patients per department
SELECT dep.DeptName, COUNT(DISTINCT a.PatientID) AS TotalPatients
FROM Departments dep
JOIN Doctors doc ON dep.DeptID = doc.Department
JOIN Appointments a ON doc.DoctorID = a.DoctorID
GROUP BY dep.DeptName;
```

## Conclusion : 
- In this way we have Designed an Relational Database Schema for a Hospital Management System and Manage Patients , Doctors , Appointments and Treatments

---

# Practical 10 : To design and implement a relational database schema for a Hotel Management System that efficiently manages Guests, Rooms, Reservations, Services, and Payments using SQL. 

## Procedure :

```sql

-- a) Create Tables:

CREATE TABLE Guest (
 Guest_ID INT PRIMARY KEY,
 Name VARCHAR(100),
 Phone VARCHAR(15),
 Email VARCHAR(100),
 Address VARCHAR(255)
);
CREATE TABLE Room (
 Room_ID INT PRIMARY KEY,
 Room_Type VARCHAR(50),
 Status VARCHAR(20),
 Rate_Per_Night DECIMAL(10,2)
);
CREATE TABLE Reservation (
 Reservation_ID INT PRIMARY KEY,
 Guest_ID INT,
 Room_ID INT,
 CheckIn_Date DATE,
 CheckOut_Date DATE,
 No_of_Days INT,
 FOREIGN KEY (Guest_ID) REFERENCES Guest(Guest_ID),
 FOREIGN KEY (Room_ID) REFERENCES Room(Room_ID)
);
CREATE TABLE Service (
 Service_ID INT PRIMARY KEY,
 Service_Name VARCHAR(100),
 Service_Charge DECIMAL(10,2)
);
CREATE TABLE Reservation_Service (
 Reservation_ID INT,
 Service_ID INT,
 Quantity INT,
 PRIMARY KEY (Reservation_ID, Service_ID),
 FOREIGN KEY (Reservation_ID) REFERENCES Reservation(Reservation_ID),
 FOREIGN KEY (Service_ID) REFERENCES Service(Service_ID)
);
CREATE TABLE Payment (
 Payment_ID INT PRIMARY KEY,
 Reservation_ID INT,
 Payment_Date DATE,
 Amount DECIMAL(10,2),
 Payment_Method VARCHAR(50),
 FOREIGN KEY (Reservation_ID) REFERENCES Reservation(Reservation_ID)
);

-- b) Insert Sample Data:
INSERT INTO Guest VALUES (1, 'Rahul Patil', '9876543210', 'rahul@gmail.com', 'Pune');
INSERT INTO Room VALUES (101, 'Deluxe', 'Available', 3500.00);
INSERT INTO Service VALUES (1, 'Laundry', 300.00);
INSERT INTO Service VALUES (2, 'Breakfast', 250.00);
INSERT INTO Reservation VALUES (1001, 1, 101, '2025-11-10', '2025-11-12', 2);
INSERT INTO Reservation_Service VALUES (1001, 1, 1);
INSERT INTO Reservation_Service VALUES (1001, 2, 2);
INSERT INTO Payment VALUES (501, 1001, '2025-11-12', 4000.00, 'Credit Card');

-- c) Query Examples:
SELECT G.Name, R.Reservation_ID, R.CheckIn_Date, R.CheckOut_Date FROM Guest G JOIN 
Reservation R ON G.Guest_ID = R.Guest_ID;

SELECT R.Reservation_ID, SUM(S.Service_Charge * RS.Quantity) + (R.No_of_Days * 
Ro.Rate_Per_Night) AS Total_Bill FROM Reservation R JOIN Room Ro ON R.Room_ID = 
Ro.Room_ID JOIN Reservation_Service RS ON R.Reservation_ID = RS.Reservation_ID JOIN Service 
S ON RS.Service_ID = S.Service_ID GROUP BY R.Reservation_ID;

SELECT * FROM Room WHERE Status = 'Available';
```

## Conclusion : 
- In this way we have designed and implemented a relational database schema for a Hotel Management System that efficiently manages Guests, Rooms, Reservations, Services, and Payments using SQL. 

---

# Practical 11 : To design and implement a relational database schema for a Pharmacy Management System that efficiently manages Medicines, Suppliers, Prescriptions, Customers, and Invoices using SQL.

## Procedure :

```sql

-- a) Create Tables:

CREATE TABLE Supplier (
 Supplier_ID INT PRIMARY KEY,
 Supplier_Name VARCHAR(100),
 Contact_No VARCHAR(15),
 Address VARCHAR(255)
);
CREATE TABLE Medicine (
 Medicine_ID INT PRIMARY KEY,
 Name VARCHAR(100),
 Category VARCHAR(50),
 Price DECIMAL(10,2),
 Stock INT,
 Supplier_ID INT,
 FOREIGN KEY (Supplier_ID) REFERENCES Supplier(Supplier_ID)
);
CREATE TABLE Customer (
 Customer_ID INT PRIMARY KEY,
 Name VARCHAR(100),
 Phone VARCHAR(15),
 Address VARCHAR(255)
);
CREATE TABLE Prescription (
 Prescription_ID INT PRIMARY KEY,
 Customer_ID INT,
 Doctor_Name VARCHAR(100),
 Date DATE,
 FOREIGN KEY (Customer_ID) REFERENCES Customer(Customer_ID)
);
CREATE TABLE Medicine_Prescription (
 Prescription_ID INT,
 Medicine_ID INT,
 Quantity INT,
 PRIMARY KEY (Prescription_ID, Medicine_ID),
 FOREIGN KEY (Prescription_ID) REFERENCES Prescription(Prescription_ID),
 FOREIGN KEY (Medicine_ID) REFERENCES Medicine(Medicine_ID)
);
CREATE TABLE Invoice (
 Invoice_ID INT PRIMARY KEY,
 Prescription_ID INT,
 Total_Amount DECIMAL(10,2),
 Date DATE,
 Payment_Method VARCHAR(50),
 FOREIGN KEY (Prescription_ID) REFERENCES Prescription(Prescription_ID)
);

-- b) Insert Sample Data:
INSERT INTO Supplier VALUES (1, 'Medilife Pharma', '9876543210', 'Pune');
INSERT INTO Medicine VALUES (101, 'Paracetamol', 'Tablet', 25.00, 200, 1);
INSERT INTO Medicine VALUES (102, 'Amoxicillin', 'Capsule', 50.00, 150, 1);
INSERT INTO Customer VALUES (1, 'Anita Sharma', '9898989898', 'Mumbai');
INSERT INTO Prescription VALUES (5001, 1, 'Dr. Mehta', '2025-11-10');
INSERT INTO Medicine_Prescription VALUES (5001, 101, 2);
INSERT INTO Medicine_Prescription VALUES (5001, 102, 1);
INSERT INTO Invoice VALUES (9001, 5001, 100.00, '2025-11-10', 'Cash');

-- c) Query Examples:
SELECT Name, Category, Price FROM Medicine WHERE Stock > 50;

SELECT C.Name, P.Prescription_ID, P.Doctor_Name FROM Customer C JOIN Prescription 
P ON C.Customer_ID = P.Customer_ID;

SELECT M.Name, MP.Quantity FROM Medicine M JOIN Medicine_Prescription MP ON 
M.Medicine_ID = MP.Medicine_ID WHERE MP.Prescription_ID = 5001;

SELECT I.Invoice_ID, I.Total_Amount, I.Payment_Method FROM Invoice I JOIN 
Prescription P ON I.Prescription_ID = P.Prescription_ID;
```

## Normalization Check:
- All tables are normalized up to 3rd Normal Form (3NF). There is no data redundancy, and all 
non-key attributes are fully dependent on the primary key

## Conclusion : 
- The relational schema successfully manages medicines, suppliers, prescriptions, customers, 
and invoices, ensuring accurate record-keeping and easy retrieval.

---