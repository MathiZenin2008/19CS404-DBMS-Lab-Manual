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
<img width="909" height="569" alt="image" src="https://github.com/user-attachments/assets/805b0c52-cee9-41ba-815b-ad741e5dcc6f" />

```sql
SELECT DoctorID, COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY DoctorID
ORDER BY DoctorID;

```

**Output:**

<img width="615" height="668" alt="image" src="https://github.com/user-attachments/assets/f11b060e-9cde-445e-9c44-b3f6e7925310" />

**Question 2**
---
<img width="967" height="476" alt="image" src="https://github.com/user-attachments/assets/9daa1deb-c3f8-4885-b121-a69fda2c9685" />

```sql
SELECT DoctorID, COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DoctorID
ORDER BY DoctorID;
```

**Output:**

<img width="874" height="574" alt="image" src="https://github.com/user-attachments/assets/72573bf0-edaf-46c0-8432-073c3c4ec1c2" />

**Question 3**
---
<img width="614" height="246" alt="image" src="https://github.com/user-attachments/assets/a3cc92c5-9c30-4276-a8a0-a042a3f10068" />

```sql
SELECT AVG(income) AS Average_Salary
FROM employee;
```

**Output:**

<img width="525" height="270" alt="image" src="https://github.com/user-attachments/assets/f8521ffc-5d61-48d4-a6ea-4b63ebaaf000" />

**Question 4**
---
<img width="845" height="251" alt="image" src="https://github.com/user-attachments/assets/f77bd5dd-6ac2-4092-abfe-93368a1c7f4e" />

```sql
SELECT COUNT(*) AS employees_in_california
FROM employee
WHERE city = 'California';
```

**Output:**

<img width="622" height="280" alt="image" src="https://github.com/user-attachments/assets/f53b0db9-c543-4d3a-84e8-407d764f6b29" />

**Question 5**
---
<img width="969" height="278" alt="image" src="https://github.com/user-attachments/assets/dd84d73b-5781-49ca-935e-41844d9ed9f4" />

```sql
SELECT COUNT(*) AS COUNT
FROM customer
WHERE city <> 'Noida';
```

**Output:**

<img width="357" height="262" alt="image" src="https://github.com/user-attachments/assets/b64e4839-d073-46d4-b6f5-7dc5081c127a" />

**Question 6**
---
<img width="746" height="232" alt="image" src="https://github.com/user-attachments/assets/457ff3e4-9376-4151-bc97-845200eb52c7" />

```sql
SELECT SUM(income) AS total_income
FROM employee
WHERE age >= 40;
```

**Output:**

<img width="403" height="271" alt="image" src="https://github.com/user-attachments/assets/985524a3-b9d2-4129-9376-20aff394ef07" />

**Question 7**
---
<img width="595" height="275" alt="image" src="https://github.com/user-attachments/assets/8944f881-0d88-4ba8-a97f-1aaae9fc209a" />

```sql
SELECT name AS fruit_name, inventory AS lowest_quantity
FROM fruits
ORDER BY inventory ASC
LIMIT 1;
```

**Output:**

<img width="604" height="289" alt="image" src="https://github.com/user-attachments/assets/ddd53d75-37c2-44c2-ae04-3007267faad2" />

**Question 8**
---
<img width="1213" height="271" alt="image" src="https://github.com/user-attachments/assets/9af8ee7b-79e7-4140-86fb-18e2275cc1a0" />

```sql
SELECT city, AVG(income) AS "AVG(income)"
FROM employee
GROUP BY city
HAVING AVG(income) > 500000
ORDER BY city;
```

**Output:**

<img width="992" height="394" alt="image" src="https://github.com/user-attachments/assets/70420c12-bda0-4502-9b90-2d6caf399964" />

**Question 9**
---
<img width="1241" height="236" alt="image" src="https://github.com/user-attachments/assets/0e465570-c680-4749-ab26-c2028c6ff807" />

```sql
SELECT jdate, SUM(workhour) AS "SUM(workhour)"
FROM employee1
GROUP BY jdate
HAVING SUM(workhour) > 40
ORDER BY jdate;
```

**Output:**

<img width="632" height="320" alt="image" src="https://github.com/user-attachments/assets/4a451e78-8c34-4f17-a522-9e53bb469196" />

**Question 10**
---
<img width="1221" height="327" alt="image" src="https://github.com/user-attachments/assets/fa531931-e23f-447c-97db-9ba85622cd21" />

```sql
SELECT (age / 5) * 5 AS age_group, MAX(salary) AS "MAX(salary)"
FROM customer1
GROUP BY age_group
HAVING MAX(salary) > 8000
ORDER BY age_group;
```

**Output:**

<img width="653" height="309" alt="image" src="https://github.com/user-attachments/assets/6762c2e2-c3ef-4c7e-87b2-5436b0cdb277" />

## Grade
<img width="1344" height="59" alt="image" src="https://github.com/user-attachments/assets/008eb49d-930b-4266-8d4b-5f2e69992134" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
