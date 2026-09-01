# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="1068" height="370" alt="image" src="https://github.com/user-attachments/assets/ddffe3a5-7eec-4935-9bd8-b7dfdb154e0d" />

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 1500;
```

**Output:**

<img width="1161" height="529" alt="image" src="https://github.com/user-attachments/assets/fccb709b-8fd7-4acc-a70e-f5e2e398a7cb" />

**Question 2**
---
<img width="1233" height="382" alt="image" src="https://github.com/user-attachments/assets/1e497635-92f2-4f5d-9113-e7c8ab286ef4" />

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY = 1500;
```

**Output:**

<img width="1221" height="297" alt="image" src="https://github.com/user-attachments/assets/319e4e0a-4dd4-4750-8e52-12bd8de7ec65" />

**Question 3**
---
<img width="1268" height="320" alt="image" src="https://github.com/user-attachments/assets/60d8b17f-7b89-4119-846c-7c719971b68d" />

```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE purch_amt > (
    SELECT AVG(purch_amt)
    FROM orders
    WHERE ord_date = '2012-10-10'
);
```

**Output:**

<img width="1127" height="393" alt="image" src="https://github.com/user-attachments/assets/dc772528-0a50-43dd-8136-31e188223be2" />

**Question 4**
---
<img width="1314" height="447" alt="image" src="https://github.com/user-attachments/assets/7920a2ad-8d7c-4fd0-976f-d43a6fbaa934" />

```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM orders o
JOIN salesman s
ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';

```

**Output:**

<img width="1133" height="391" alt="image" src="https://github.com/user-attachments/assets/fa6f01ee-5856-4075-ba14-41003c73168d" />

**Question 5**
---
<img width="1174" height="448" alt="image" src="https://github.com/user-attachments/assets/49e908f3-843d-4626-bd0f-a6a71d6551ed" />

```sql
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer
WHERE customer_id = (
    (SELECT salesman_id FROM salesman WHERE name = 'Mc Lyon') - 2001
);
```

**Output:**

<img width="1167" height="262" alt="image" src="https://github.com/user-attachments/assets/b8dc617a-5044-4702-89f0-899bec1c1e2f" />

**Question 6**
---
<img width="1270" height="456" alt="image" src="https://github.com/user-attachments/assets/2c7f2639-4d25-4451-a97a-fd0fdacf5497" />

```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.salesman_id
FROM orders o
JOIN salesman s
ON o.salesman_id = s.salesman_id
WHERE s.commission = (
    SELECT MAX(commission)
    FROM salesman
);
```

**Output:**

<img width="923" height="413" alt="image" src="https://github.com/user-attachments/assets/187e48e4-1e0d-4a25-b405-4ef05908b152" />

**Question 7**
---
<img width="1018" height="308" alt="image" src="https://github.com/user-attachments/assets/7f3d34a0-aca9-4e74-89ab-489bfaba18e0" />

```sql
SELECT id, name, age, city, income
FROM Employee
WHERE age < (
    SELECT AVG(age)
    FROM Employee
    WHERE income > 1000000
);
```

**Output:**

<img width="1325" height="381" alt="image" src="https://github.com/user-attachments/assets/b3a920ae-2729-4f82-bd86-57f323235776" />

**Question 8**
---
<img width="1149" height="488" alt="image" src="https://github.com/user-attachments/assets/68d4befa-2ffb-4ca8-8143-1a2c96565210" />

```sql
SELECT name, city
FROM customer
WHERE city IN (
    SELECT city
    FROM customer
    WHERE id IN (3,7)
);
```

**Output:**

<img width="540" height="435" alt="image" src="https://github.com/user-attachments/assets/40973405-ab12-4231-81e9-be4ffc8b7460" />

**Question 9**
---
<img width="1297" height="455" alt="image" src="https://github.com/user-attachments/assets/57340e2e-7eea-4694-a717-b754e5b893a1" />

```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM orders o
JOIN salesman s
ON o.salesman_id = s.salesman_id
WHERE s.name = 'Paul Adam';
```

**Output:**

<img width="1198" height="343" alt="image" src="https://github.com/user-attachments/assets/cbf6d069-2e71-4310-95f2-fc6b16431fee" />

**Question 10**
---
<img width="1237" height="552" alt="image" src="https://github.com/user-attachments/assets/5023b46a-0b89-43d6-bfe6-c6dee7f5266f" />

```sql
SELECT
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    o.customer_id,
    o.salesman_id
FROM
    ORDERS o
INNER JOIN
    SALESMAN s ON o.salesman_id = s.salesman_id
WHERE
    s.city='New York';
```

**Output:**

<img width="1240" height="444" alt="image" src="https://github.com/user-attachments/assets/7d4bbd10-e0a4-4c2f-9031-2a1cb80d8139" />

## Grade
<img width="1370" height="67" alt="image" src="https://github.com/user-attachments/assets/eb4f358a-1226-4fb7-b8dc-a0dc4b5ffe5e" />


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
