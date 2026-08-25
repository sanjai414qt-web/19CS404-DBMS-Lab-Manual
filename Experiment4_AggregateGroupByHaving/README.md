# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
What is the most common diagnosis among patients?

```sql
SELECT Diagnosis,
       COUNT(*) AS DiagnosisCount
FROM MedicalRecords
GROUP BY Diagnosis
ORDER BY DiagnosisCount DESC
LIMIT 1;
```

**Output:**

<img width="955" height="308" alt="image" src="https://github.com/user-attachments/assets/bbb78739-2c2d-4ec5-a28d-c970ff6eade2" />


**Question 2**
---
What is the count of male and female patients?

```sql
SELECT Gender,
       COUNT(*) AS TotalPatients
FROM Patients
GROUP BY Gender;
```

**Output:**

<img width="710" height="337" alt="image" src="https://github.com/user-attachments/assets/bbdbc687-0e80-4732-b4bf-3661fbb63244" />


**Question 3**
---
How many prescriptions were written by each doctor?

```sql
SELECT DoctorID,
       COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY DoctorID;
```

**Output:**

<img width="1058" height="413" alt="image" src="https://github.com/user-attachments/assets/39dd3c4a-53de-4fbc-a31d-415d935eb4d6" />


**Question 4**
---
Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.

```sql
SELECT COUNT(*) AS COUNT
FROM customer
WHERE city <> 'Noida';
```

**Output:**
<img width="715" height="302" alt="image" src="https://github.com/user-attachments/assets/c968c575-7fcd-4a94-8fad-c2ea8a74ea65" />


**Question 5**
---
Write a SQL query to find the maximum purchase amount.

```sql
SELECT MAX(purch_amt) AS MAXIMUM
FROM orders;
```

**Output:**
<img width="608" height="330" alt="image" src="https://github.com/user-attachments/assets/ed2b1c80-21db-47b7-8dac-501b19da1ec1" />


**Question 6**
---
Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.

```sql
SELECT AVG(purch_amt) AS AVERAGE
FROM orders;
```

**Output:**

<img width="505" height="375" alt="image" src="https://github.com/user-attachments/assets/a9c35c78-6b29-4770-a107-2d0d81feffef" />


**Question 7**
---
Write a SQL query to find the shortest email address in the customer table?

```sql
SELECT name,
       email,
       LENGTH( email) AS min_email_length
FROM customer
WHERE LENGTH(email) = (
    SELECT MIN(LENGTH(email))
    FROM customer
)
LIMIT 1;
```

**Output:**

<img width="1147" height="357" alt="image" src="https://github.com/user-attachments/assets/22232af2-ba00-459f-9d53-3dd527c72362" />


**Question 8**
---
Write the SQL query that performs grouping by age groups and displays the maximum salary for each group, excluding groups where the maximum salary is not greater than 8000. 

Note: Calculate the age group as multiples of 5.

Eg., 20,22,23 comes in age group 20. 

25,27,29 comes in age group 25.

```sql
SELECT (age / 5) * 5 AS age_group,
       MAX(salary)
FROM customer1
GROUP BY (age / 5) * 5
HAVING MAX(salary) > 8000;
```

**Output:**

<img width="722" height="391" alt="image" src="https://github.com/user-attachments/assets/44d50948-c700-4b63-88a5-cdd93327578b" />


**Question 9**
---
Write the SQL query that accomplishes the grouping of data by addresses, calculates the sum of salaries for each address, and excludes addresses where the total salary sum is not greater than 2000.

```sql
SELECT address,
       SUM(salary)
FROM customer1
GROUP BY address
HAVING SUM(salary) > 2000;
```

**Output:**

<img width="746" height="307" alt="image" src="https://github.com/user-attachments/assets/f507f69a-dc91-48b9-8ae0-c38e0794a1b2" />






**Question 10**
---
Write the SQL query that accomplishes the selection of total cost of all products in each category from the "products" table and includes only those products where the total cost is greater than 50.

```sql
SELECT category_id,
       SUM(price) AS Total_Cost
FROM products
GROUP BY category_id
HAVING SUM(price) > 50;
```

**Output:**

<img width="607" height="326" alt="image" src="https://github.com/user-attachments/assets/71e5145b-a9f8-4fcc-9581-fd75229c15e7" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
