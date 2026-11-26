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
What is the count of male and female patients?

Sample table: Patients Table



For example:

Result
Gender      TotalPatients
----------  -------------
Female      5
Male        5

```
SELECT Gender, COUNT(*) AS TotalPatients
FROM Patients
GROUP BY Gender;
```

**Output:**

<img width="946" height="350" alt="image" src="https://github.com/user-attachments/assets/46f4aa70-3835-4af2-855a-8876f31e8e79" />


**Question 2**
---
How many prescriptions were written for each medication?

Sample tablePrescriptions Table



For example:

Result
Medication     TotalPrescriptions
-------------  ------------------
Ciprofloxacin  1
Doxorubicin    1
Ibuprofen      1
Levothyroxine  1
Lisinopril     1
MMR            1
Pending        1
Prenatal vita  1
Sertraline     1
Topiramate     1

```
SELECT Medication, COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY Medication;
```

**Output:**
<img width="786" height="640" alt="image" src="https://github.com/user-attachments/assets/ea3b01d3-8cae-4cf9-a057-213bf5e28a83" />


**Question 3**
---
How many medical records does each doctor have?

Sample table:MedicalRecords Table



For example:

Result
DoctorID    TotalRecords
----------  ------------
3           4
5           1
6           1
7           1
8           3

```
SELECT DoctorID, COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY DoctorID;
```

**Output:**
<img width="1140" height="545" alt="image" src="https://github.com/user-attachments/assets/dc7975a7-e381-4831-a1a3-e92278fa36a2" />


**Question 4**
---
Write a SQL query to find  how many employees work in California?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
 

For example:

Result
employees_in_california
-----------------------
2

```
SELECT COUNT(*) AS employees_in_california
FROM employee
WHERE city = 'California';
```

**Output:**

<img width="928" height="301" alt="image" src="https://github.com/user-attachments/assets/7f4fb5a4-4a9f-4f95-b96e-eeaa531de1a4" />


**Question 5**
---
Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

For example:

Result
TOTAL
----------
17541.18

```
SELECT SUM(purch_amt) AS TOTAL
FROM orders;
```

**Output:**

<img width="973" height="307" alt="image" src="https://github.com/user-attachments/assets/fba9ea7a-3de5-4294-8a14-eab8d55dfe4c" />


**Question 6**
---
Write a SQL query to find the total income of employees aged 40 or above.

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
For example:

Result
total_income
------------
1800000

```
SELECT SUM(income) AS total_income
FROM employee
WHERE age >= 40;
```

**Output:**

<img width="955" height="300" alt="image" src="https://github.com/user-attachments/assets/c728a5f6-2fc3-4ae2-8b91-3b45976350a9" />


**Question 7**
---
Write a SQL query to find the total number of unique cities in the customer table?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
For example:

Result
unique_cities
-------------
10

```
SELECT COUNT(DISTINCT city) AS unique_cities
FROM customer;
```

**Output:**

<img width="1282" height="302" alt="image" src="https://github.com/user-attachments/assets/13696050-0a60-4f81-8881-c6508af648f2" />


**Question 8**
---
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the average age for each group, and excludes groups where the average age is not less than 24.

Sample table: customer1



For example:

Result
age_group   AVG(age)
----------  ----------
20          23.0

```
SELECT (age/5)*5 AS age_group, AVG(age)
FROM customer1
GROUP BY (age/5)*5
HAVING AVG(age) < 24;
```

**Output:**

<img width="1075" height="300" alt="image" src="https://github.com/user-attachments/assets/ddcf8046-4b66-4271-b25e-f063fbcc9564" />


**Question 9**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the minimum work hours for each occupation, and excludes occupations where the minimum work hour is not greater than 8.

Sample table: employee1



For example:

Result
occupation  MIN(workhour)
----------  -------------
Business    10
Doctor      15
Engineer    12
Teacher     9

```
SELECT occupation, MIN(workhour)
FROM employee1
GROUP BY occupation
HAVING MIN(workhour) > 8;
```

**Output:**

<img width="962" height="421" alt="image" src="https://github.com/user-attachments/assets/40532eff-0201-45d5-b091-a73f22fe4b2d" />


**Question 10**
---
Write the SQL query that accomplishes the selection of number of products for each category from products table which includes only those products where the category ID is greater than 2.

Sample table: products



For example:

Result
category_id  COUNT
-----------  ----------
3            3

```
SELECT category_id, COUNT(*) AS COUNT
FROM products
WHERE category_id > 2
GROUP BY category_id;
```

**Output:**

<img width="782" height="315" alt="image" src="https://github.com/user-attachments/assets/69e8715c-9669-4cd2-baaf-6a357da5f195" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
