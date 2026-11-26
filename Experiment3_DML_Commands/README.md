# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```
UPDATE products
SET sell_price = sell_price * 1.10
WHERE category = 'Bakery';
```

**Output:**

<img width="1261" height="391" alt="image" src="https://github.com/user-attachments/assets/35798678-20a8-44e1-b5d1-8d52d8821846" />


**Question 2**
---
Write a SQL statement to Change the supplier name to 'A1 Suppliers' where the supplier ID is 8 in the suppliers table.

Table info

suppliers(supplier_id,supplier_name,contact_person,phone_number,email,address)

For example:

Test	Result
select changes();
changes()
----------
1

```
UPDATE suppliers
SET supplier_name = 'A1 Suppliers'
WHERE supplier_id = 8;
```

**Output:**

<img width="1268" height="301" alt="image" src="https://github.com/user-attachments/assets/9f2486cd-2aac-4d9d-9549-dafb03994d09" />


**Question 3**
---
Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
For example:

Test	Result
SELECT * FROM EMPLOYEES WHERE DEPARTMENT_ID=80 AND COMMISSION_PCT=.25;
EMPLOYEE_ID  FIRST_NAME  LAST_NAME   EMAIL       PHONE_NUMBER        HIRE_DATE   JOB_ID      SALARY      COMMISSION_PCT  MANAGER_ID  DEPARTMENT_ID
-----------  ----------  ----------  ----------  ------------------  ----------  ----------  ----------  --------------  ----------  -------------
151          John        Bernstein   DBERNSTE    011.44.1344.345268  8/7/87      SA_REP      9500        0.25            145         80
152          John        Hall        PHALL       011.44.1344.478968  8/8/87      SA_REP      9000        0.25            145         80
161          John        Sewall      SSEWALL     011.44.1345.529268  8/17/87     SA_REP      7000        0.25            146         80
162          John        Vishney     CVISHNEY    011.44.1346.129268  8/18/87     SA_REP      10500       0.25            147         80
168          John        Ozer        LOZER       011.44.1343.929268  8/24/87     SA_REP      11500       0.25            148         80
175          John        Hutton      AHUTTON     011.44.1644.429266  8/31/87     SA_REP      8800        0.25            149         80

```
UPDATE employees
SET first_name = 'John'
WHERE department_id = 80
AND commission_pct < 0.35;
```

**Output:**

<img width="1270" height="418" alt="image" src="https://github.com/user-attachments/assets/2521b5bf-70a1-4e94-aec0-e43cfc6ee594" />


**Question 4**
---
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```
UPDATE products
SET product_name = 'Premium Bread'
WHERE product_id = 5;
```

**Output:**

<img width="1272" height="307" alt="image" src="https://github.com/user-attachments/assets/847d2888-2349-4166-9322-cb2633a2fc65" />


**Question 5**
---
Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.

products table

---------------
product_id
product_name
category_id
availability

```
UPDATE products
SET product_name = 'Grapefruit'
WHERE product_id = 4;
```

**Output:**

<img width="1277" height="225" alt="image" src="https://github.com/user-attachments/assets/8892f104-dbb4-40e8-a3dd-6cfbe008eecf" />


**Question 6**
---
Write a SQL query to Delete customers whose 'GRADE' is greater than 2 and have a 'PAYMENT_AMT' less than the average 'PAYMENT_AMT' for all customers, or whose 'OUTSTANDING_AMT' is greater than 8000:

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select changes();
changes()
----------
12

```
DELETE FROM Customer
WHERE (GRADE > 2 AND PAYMENT_AMT < (SELECT AVG(PAYMENT_AMT) FROM Customer))
OR OUTSTANDING_AMT > 8000;
```

**Output:**

<img width="1287" height="580" alt="image" src="https://github.com/user-attachments/assets/7f9efde2-16a2-4420-acdd-57ee916729f7" />


**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is less than 2.

 
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select distinct(grade)from customer;
GRADE
----------
2
3
1
0
GRADE
----------
2
3

```
DELETE FROM customer
WHERE GRADE < 2;
```

**Output:**

<img width="581" height="416" alt="image" src="https://github.com/user-attachments/assets/c6a19f69-b0d0-41ea-930d-bbe519b9efc9" />


**Question 8**
---
Write a SQL query to Delete customers with 'CUST_COUNTRY' 'UK' and 'WORKING_AREA' 'London' whose 'GRADE' is less than 3

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select changes();
changes()
----------
4

```
DELETE FROM customer
WHERE CUST_COUNTRY = 'UK'
AND WORKING_AREA = 'London'
AND GRADE < 3;
```

**Output:**

<img width="1276" height="361" alt="image" src="https://github.com/user-attachments/assets/7d253b9b-2a59-4a29-aad8-f37858cd3b92" />


**Question 9**
---
Write a SQL query to Delete All Doctors with a NULL Last Name

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
For example:

Test	Result
SELECT * FROM doctors;
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
4           Febin                   Cardiology
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics

```
DELETE FROM Doctors
WHERE last_name IS NULL;
```

**Output:**

<img width="965" height="580" alt="image" src="https://github.com/user-attachments/assets/f23b0c41-5913-49fd-9c47-287fa314dcd4" />


**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'OPENING_AMT' is between 4000 and 6000.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
SELECT * FROM customer
WHERE OPENING_AMT BETWEEN 4000 AND 6000;
CUST_CODE   CUST_NAME   CUST_CITY   WORKING_AREA  CUST_COUNTRY  GRADE       OPENING_AMT  RECEIVE_AMT  PAYMENT_AMT  OUTSTANDING_AMT  PHONE_NO    AGENT_CODE
----------  ----------  ----------  ------------  ------------  ----------  -----------  -----------  -----------  ---------------  ----------  ----------
C00013      Holmes      London      London        UK            2           6000         5000         7000         4000             BBBBBBB     A003
C00020      Albert      New York    New York      USA           3           5000         7000         6000         6000             BBBBSBB     A008
C00025      Ravindran   Bangalore   Bangalore     India         2           5000         7000         4000         8000             AVAVAVA     A011
C00024      Cook        London      London        UK            2           4000         9000         7000         6000             FSDDSDF     A006
C00015      Stuart      London      London        UK            1           6000         8000         3000         11000            GFSGERS     A003
C00002      Bolt        New York    New York      USA           3           5000         7000         9000         3000             DDNRDRH     A008
C00004      Winston     Brisban     Brisban       Australia     1           5000         8000         7000         6000             AAAAAAA     A005
C00023      Karl        London      London        UK            0           4000         6000         7000         3000             AAAABAA     A006
C00010      Charles     Hampshair   Hampshair     UK            3           6000         4000         5000         5000             MMMMMMM     A009
C00012      Steven      San Jose    San Jose      USA           1           5000         7000         9000         3000             KRFYGJK     A012

```
DELETE FROM Customer
WHERE OPENING_AMT >= 4000
AND OPENING_AMT <= 6000;
```

**Output:**

<img width="1276" height="520" alt="image" src="https://github.com/user-attachments/assets/2e6d8ecf-6f8c-4f8b-95f8-da3edcb7eefb" />

**Question 11**
---
Write a query to fetch details of employees with the address as “DELHI(DEL)” from EmployeeInfo table.
 
EmpID

EmpFname

EmpLname

Department

Project

Address

DOB

Gender

1

Sanjay

Mehra

HR

P1

Hyderabad(HYD)

01/12/1976

M

2

Ananya

Mishra

Admin

P2

Delhi(DEL)

02/05/1968

F



For example:

Result
EmpID       EmpFname    EmpLname    Department  Project     Address     DOB         Gender
----------  ----------  ----------  ----------  ----------  ----------  ----------  ----------
2           Ananya      Mishra      Admin       P2          Delhi(DEL)  1968-05-02  F
5           Ankit       Kapoor      Admin       P2          Delhi(DEL)  1994-07-03  M
```
SELECT *
FROM EmployeeInfo
WHERE Address = 'Delhi(DEL)';
```

**Output:**
<img width="1285" height="262" alt="image" src="https://github.com/user-attachments/assets/5cf7729b-a78f-468b-a145-d3488fa20079" />

**Question 12**
---
Show the categoryName and description from the categories table sorted by categoryName.

name                     type
---------------       ---------------
CategoryID           INTEGER
CategoryName     VARCHAR(25)
Description          VARCHAR(255)

For example:

Result
CategoryName  Description
------------  -------------------------------------------
Beverages     Soft drinks, coffees, teas, beers, and ales
Fruits        Apple, Grapes, Kiwi

```
SELECT CategoryName, Description
FROM categories
ORDER BY CategoryName;
```

**Output:**
<img width="935" height="455" alt="image" src="https://github.com/user-attachments/assets/17f1c6bf-cfb3-4bc1-b9be-6aa015759c4d" />

**Question 13**
---
Write a SQL query to classify value2 in the Calculations table as 'Small', 'Medium', or 'Large' based on whether it is less than 10, between 10 and 50, or greater than 50, respectively.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0
 

For example:

Result
id          value2      size_category
----------  ----------  -------------
1           2.0         Small
2           5.0         Small
3           7.0         Small
4           9.0         Small
```
SELECT id, value2,
CASE
    WHEN value2 < 10 THEN 'Small'
    WHEN value2 BETWEEN 10 AND 50 THEN 'Medium'
    WHEN value2 > 50 THEN 'Large'
END AS size_category
FROM Calculations;
```
**Output:**
<img width="655" height="422" alt="image" src="https://github.com/user-attachments/assets/4810a995-0fa3-4cc0-bb43-41452c3bdb28" />

**Question 14**
---
Write a SQL statement to show all the contact_name, address, city of all customers who are from 'Germany', 'Mexico' and 'Spain' countries.

customers table

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           CustomerID    INTEGER      0                       1
1           CustomerName  VARCHAR(50)  0                       0
2           ContactName   VARCHAR(50)  0                       0
3           Address       VARCHAR(50)  0                       0
4           City          VARCHAR(20)  0                       0
5           PostalCode    VARCHAR(10)  0                       0
6           Country       VARCHAR(15)  0                       0
For example:

Result
ContactName  Address        City
-----------  -------------  ----------
John         Mataderos 231  Sevilla
Andrew       Obere Str. 57  Berlin
```
SELECT ContactName, Address, City
FROM customers
WHERE Country IN ('Germany', 'Mexico', 'Spain');
```

**Output:**
<img width="816" height="678" alt="image" src="https://github.com/user-attachments/assets/f385bb40-2063-4a58-963c-ec1f02abe089" />

**Question 15**
---
Write a SQL query to find customers who are from the city 'London' who have a grade greater than 200. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
For example:

Result
customer_id  cust_name     city        grade       salesman_id
-----------  ------------  ----------  ----------  -----------
3008         Julian Green  London      300         5002
```
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer
WHERE city = 'London'
AND grade > 200;
```

**Output:**
<img width="1080" height="320" alt="image" src="https://github.com/user-attachments/assets/b2e8a7a3-b9ca-4d7e-a57f-1d81c5233bf5" />

**Question 16**
---
Write a SQL query to calculate the discounted price for products where the discount percentage is greater than 0, and order the results by discounted_price in ascending order. Return product_id, original_price, discount_percentage, and discounted_price.

Sample table: Products

product_id | original_price | discount_percentage 

------------+----------------+--------------------- 

101 | 50.00 | 0.10 

102 | 75.00 | 0.00 

103 | 100.00 | 0.20

 

For example:

Result
product_id  original_price  discount_percentage  discounted_price
----------  --------------  -------------------  ----------------
101         50.0            0.1                  45.0
102         75.0            0.15                 63.75
103         100.0           0.2                  80.0
```
SELECT product_id,
       original_price,
       discount_percentage,
       original_price * (1 - discount_percentage) AS discounted_price
FROM Products
WHERE discount_percentage > 0
ORDER BY discounted_price ASC;
```

**Output:**
<img width="1126" height="272" alt="image" src="https://github.com/user-attachments/assets/ec158a02-5251-41a1-98e9-e5a5fb493703" />

**Question 17**
---
Write a SQL query to calculate the discounted price for each product. Return product_id, original_price, discount_percentage, and discounted_price.

Sample table: Products

product_id | original_price | discount_percentage
------------+----------------+---------------------
101 | 50.00 | 0.10
102 | 75.00 | 0.15
103 | 100.00 | 0.20

For example:

Result
product_id  original_price  discount_percentage  discounted_price
----------  --------------  -------------------  ----------------
101         50.0            0.1                  45.0
102         75.0            0.15                 63.75
103         100.0           0.2                  80.0
```
SELECT product_id,
       original_price,
       discount_percentage,
       original_price * (1 - discount_percentage) AS discounted_price
FROM Products;
```
**Output:**
<img width="1123" height="392" alt="image" src="https://github.com/user-attachments/assets/ff6d0ca7-a697-4470-b386-92f9443e8c2e" />

**Question 18**
---
Write a SQL query to Select all patients who was admitted in hospital for more than 3 days.

Table: Patients

name                  type
--------------------  ----------
patient_id            INT
first_name            VARCHAR(50)
last_name             VARCHAR(50)
date_of_birth         DATE
admission_date        DATE
discharge_date        DATE
doctor_id             INT
For example:

Result
first_name  last_name   no_of_days
----------  ----------  ----------
Bob         Miller      16.0
```
SELECT first_name,
       last_name,
       julianday(discharge_date) - julianday(admission_date) + 1 AS no_of_days
FROM Patients
WHERE julianday(discharge_date) - julianday(admission_date) + 1 > 3;
```
**Output:**
<img width="658" height="322" alt="image" src="https://github.com/user-attachments/assets/239bcacc-59c9-4331-819b-4f37afb3cb97" />

**Question 19**
---
Write a SQL query to find all employees who were hired in the last 6 months from the emp table. 

Note: Assume current date as '01-09-2024'

emp table

cid         name        type        
----------  ----------  ---------- 
0           empno       INT         
1           ename       VARCHAR(100)
2           job         VARCHAR(50)
3           mgr         INT        
4           hiredate    DATE        
5           sal         DECIMAL(10,2)  
6           comm        DECIMAL(10,2)  
7           deptno      INT         
For example:

Result
empno       ename       job         mgr         hiredate    sal         comm        deptno
----------  ----------  ----------  ----------  ----------  ----------  ----------  ----------
7369        SMITH       CLERK       7902        2024-06-01  800                     20
7499        ALLEN       SALESMAN    7698        2024-06-01  1600        300         30
7521        WARD        SALESMAN    7698        2024-06-01  1250        500         30
7900        JAMES       CLERK       7698        2024-06-01  950                     30
7902        FORD        ANALYST     7566        2024-06-01  3000                    20
7934        MILLER      CLERK       7782        2024-06-01  1300                    10
```
SELECT *
FROM emp
WHERE hiredate >= date('2024-09-01', '-6 months')
AND hiredate <= '2024-09-01';
```
**Output:**
<img width="1307" height="351" alt="image" src="https://github.com/user-attachments/assets/dde08100-3623-4a19-a681-e9fad240a3e5" />

**Question 20**
---
Write a SQL query to Get the employee names where the first letter of each word is the same.

 
Table name: emp

name        type
----------  ----------
empno       INT
ename       VARCHAR(100)
job         VARCHAR(50)
mgr         INT
hiredate    DATE
sal         DECIMAL(10,2)
comm        DECIMAL(10,2)
deptno      INT
For example:

Result
ename
---------------
King Kong
Emily Ericson
Jerry Johnson
```
SELECT ename
FROM emp
WHERE LOWER(SUBSTR(ename, 1, 1)) = LOWER(SUBSTR(ename, INSTR(ename, ' ') + 1, 1));
```
**Output:**
<img width="487" height="375" alt="image" src="https://github.com/user-attachments/assets/6e52fe9d-9064-41d2-a0f0-935d64b78648" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
