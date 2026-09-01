# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id

```sql
select c.cust_name,
       c.city,
       c.grade,
       s.name as Salesman,
       s.city
from customer c
INNER JOIN salesman s
on c.salesman_id = s.salesman_id
where c.grade < 300
order by c.customer_id;
```

**Output:**

![Screenshot 2025-05-04 092729](https://github.com/user-attachments/assets/d346efd1-4053-46d9-b9a6-3ac325c2e11d)


**Question 2**
---
Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesmen with the name 'Mc Lyon'.

```sql
SELECT c.*
FROM customer AS c
LEFT JOIN salesman AS s
  ON c.salesman_id = s.salesman_id
WHERE s.name = 'Mc Lyon';
```

**Output:**

![Screenshot 2025-05-04 092943](https://github.com/user-attachments/assets/5816ad67-e4f7-4485-b226-76cc390fae39)


**Question 3**
---
Write a SQL statement to make a report with customer name, city, order number, order date, and order amount in ascending order according to the order date to determine whether any of the existing customers have placed an order or not.

```sql
SELECT 
    c.cust_name,
    c.city AS "city",
    o.ord_no AS "ord_no",
    o.ord_date AS "ord_date",
    o.purch_amt AS "Order Amount"
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
ORDER BY 
    o.ord_date;
```

**Output:**

![Screenshot 2025-05-04 093128](https://github.com/user-attachments/assets/89e72a03-b050-400f-8cdd-9adde8965472)


**Question 4**
---
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  

```sql
SELECT 
    c.cust_name AS "Customer Name ",
    c.city ,
    s.name AS "Salesman",
    s.city ,
    s.commission AS "commission"
FROM 
    customer c
INNER JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    c.city <> s.city
    AND s.commission > 0.12;

```

**Output:**

![Screenshot 2025-05-04 093244](https://github.com/user-attachments/assets/976700c4-070b-48ee-aecb-63a3ddeb787f)


**Question 5**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column.

```sql
SELECT 
    p.first_name AS patient_name,
    t.*
FROM 
    patients p
INNER JOIN 
    test_results t ON p.patient_id = t.patient_id;
```

**Output:**

![Screenshot 2025-05-04 093408](https://github.com/user-attachments/assets/91b8b0db-0ed6-4759-b2a2-0269d8be4a3d)


**Question 6**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for orders with a purchase amount greater than 1000.

```sql
SELECT 
    c.cust_name ,
    o.ord_no ,
    o.ord_date ,
    o.purch_amt 
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
WHERE 
    o.purch_amt > 1000;

```

**Output:**

![Screenshot 2025-05-04 093521](https://github.com/user-attachments/assets/1416cc66-f18d-4b2b-8852-423d010ef53e)


**Question 7**
---
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 



```sql
SELECT 
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name",
    c.grade,
    s.name AS "Salesman",
    s.commission
FROM 
    orders o
INNER JOIN 
    customer c ON o.customer_id = c.customer_id
INNER JOIN 
    salesman s ON o.salesman_id = s.salesman_id;
```

**Output:**

![Screenshot 2025-05-04 093644](https://github.com/user-attachments/assets/75e3626c-b3bb-48e1-a5d3-64b901d5f77b)


**Question 8**
---
Write the SQL query that achieves the selection of the date of birth from the "patients" table (aliased as "p") and all columns from the "appointments" table (aliased as "a"), with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'.

```sql
SELECT 
    p.date_of_birth AS "date_of_birth",
    a.*
FROM 
    patients p
INNER JOIN 
    appointments a ON p.patient_id = a.patient_id
WHERE 
    p.first_name = 'Alice';
```

**Output:**

![Screenshot 2025-05-04 093818](https://github.com/user-attachments/assets/a132faf4-2445-479b-a12d-b4a8d3370ca4)


**Question 9**
---
 From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  



```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city ,
    s.name AS "Salesman",
    s.commission
FROM 
    customer c
INNER JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    s.commission > 0.12;
```

**Output:**

![Screenshot 2025-05-04 093947](https://github.com/user-attachments/assets/b3bb52cb-a151-4ca4-907a-ece9444f734c)


**Question 10**
---
Write the SQL query that achieves the selection of admission dates from the "patients" table and surgery dates from the "surgeries" table, with an inner join on the "patient_id" column.

```sql
SELECT 
    p.admission_date ,
    s.surgery_date 
FROM 
    patients p
INNER JOIN 
    surgeries s ON p.patient_id = s.patient_id;

```

**Output:**

![Screenshot 2025-05-04 094039](https://github.com/user-attachments/assets/f67f7693-c8a8-4b29-886c-1a7a00f2fbad)



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.

