# Practical 1 : Install MongoDB and create a database with a collection. Perform basic CRUD operations(Create, Read, Update, Delete).

```javascript

#Step 1 : Create a Database and then run the following command into the mongodb shell

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

# Step 2 : FindOne Operation 

db["users"].find()

# Step 3 : FindOne with user_id Operation

db["users"].findOne({user_id : 3})

# Step 4 : DeleteOne Operation

db["users"].deleteOne({user_id : 3})

# Step 5 : UpdateOne Operation

db["users"].updateOne({user_id : 2} , {$set : {user_address : "San Francisco , USA"}})

$ Step 6 : Last Step 

db["users"].find().pretty()

```

## Conclusion : 
- In this way we have Installed MongoDB and created a database with a collection and  Performed basic CRUD operations(Create, Read, Update, Delete).

---