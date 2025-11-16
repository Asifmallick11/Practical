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
- 1.Create Key Space in Cassandra. CREATE KEYSPACE <identifier> WITH <properties>
- 2.To Create Cassandra Table, Using Create Command.
- 3.To Change the structure of the table, Using Alter Command.
- 4.To delete the existing table in Cassandra, Using Truncate Command.
- 5.To Insert the values in CQL, use insert command
- 6.The SELECT command is used to read data from Cassandra table
- 7.The UPDATE command is used to update the existing data in a Cassandra.
- 8.The DELETE command is used to delete data from Cassandra table

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