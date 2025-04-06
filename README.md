# 🚖 Chicago Taxi Ride Data Analysis – SQL

## 🚀 Overview  
This project explores Chicago taxi trip data using SQL to answer real-world business questions about company performance, ride behavior, and the impact of weather and location. Each exercise includes both SQL queries and screenshots of the output.

---

## 📊 Format  
For each exercise:
1. ✅ SQL code used to retrieve data  
2. 📸 Screenshot of the resulting output  

---

## 📂 Files Included  
- `sql/`: SQL queries used in the analysis  
- `visuals/`: Screenshots of query outputs  
- `README.md`: Project documentation  

---

## 🧠 Exercises

---

### 1️⃣ Ride Volume by Company (Nov 15–16, 2017)

#### 🔹 Objective  
Count the number of rides per company for a two-day period and sort by ride volume.

#### 🔹 SQL Code
```sql
SELECT
    cabs.company_name,
    COUNT(trips.trip_id) AS trips_amount
FROM 
    trips
    INNER JOIN cabs ON cabs.cab_id = trips.cab_id
WHERE 
    CAST(start_ts AS date) BETWEEN '2017-11-15' AND '2017-11-16' 
GROUP BY
    cabs.company_name    
ORDER BY 
    trips_amount DESC;

![Screenshot](visuals/exercise-x.png)

2️⃣ Rides by Companies with "Yellow" or "Blue" (Nov 1–7, 2017)

#### 🔹 Objective
Find ride volume for companies with "Yellow" or "Blue" in their name.

#### 🔹 SQL Code
SELECT
    cabs.company_name AS company_name,
    COUNT(trips.trip_id) AS trips_amount
FROM 
    trips
    INNER JOIN cabs ON cabs.cab_id = trips.cab_id
WHERE 
    CAST(start_ts AS date) BETWEEN '2017-11-01' AND '2017-11-07'
    AND cabs.company_name LIKE '%Yellow%'
GROUP BY
    company_name
UNION
SELECT
    cabs.company_name AS company_name,
    COUNT(trips.trip_id) AS trips_amount
FROM 
    trips
    INNER JOIN cabs ON cabs.cab_id = trips.cab_id
WHERE 
    CAST(start_ts AS date) BETWEEN '2017-11-01' AND '2017-11-07'
    AND cabs.company_name LIKE '%Blue%'
GROUP BY
    company_name;

![Screenshot](visuals/exercise-x.png)
