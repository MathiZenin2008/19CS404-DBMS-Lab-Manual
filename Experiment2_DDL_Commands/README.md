# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
Insert the following customers into the Customers table:

CustomerID  Name         Address     City        ZipCode
----------  -----------  ----------  ----------  ----------
302         Laura Croft  456 Elm St  Seattle     98101
303         Bruce Wayne  789 Oak St  Gotham      10001

```sql
Insert INTO Customers(CustomerID,Name,Address,City ,ZipCode)
values(302,"Laura Croft","456 Elm St","Seattle",98101);
Insert INTO Customers(CustomerID,Name,Address,City ,ZipCode) 
values(303,"Bruce Wayne","789 Oak St","Gotham",10001);

**Output:**

<img width="1178" height="364" alt="Screenshot 2025-10-22 174959" src="https://github.com/user-attachments/assets/97c87376-06e4-41b2-b024-e4485b2a15f8" />



**Question 2**
Insert a record with EmployeeID 001, Name Sarah Parker, Position Manager, Department HR, and Salary 60000 into the Employee table.

```sql
insert into Employee(EmployeeID,Name,Position,Department,Salary)
values(1,"Sarah Parker","Manager","HR",60000); 
```

**Output:**
<img width="1184" height="279" alt="image" src="https://github.com/user-attachments/assets/105f07db-dddb-4780-9dcd-8ddbe0e3d829" />



**Question 3**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should set NULL on updates and deletes.
item_desc and rate should not accept NULL.


```sql
create table item(
item_id TEXT primary key,
item_desc TEXT not null,
rate   not null,
icom_id  TEXT(4),
foreign key(icom_id) references company (com_id) on update set null on delete set null
);
 
```

**Output:**

<img width="1209" height="364" alt="image" src="https://github.com/user-attachments/assets/504e8252-2588-4b14-89da-bbb4f6c5ec3c" />


**Question 4**
---
Write a SQL query to Add a new column named "discount" with the data type DECIMAL(5,2) to the "customer" table.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
 

```sql
alter table customer add discount DECIMAL(5,2);

```

**Output:**
<img width="1188" height="353" alt="image" src="https://github.com/user-attachments/assets/0bafbc83-0779-419f-8aa2-7ce3f484cfa6" />




**Question 5**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.

```sql
create table Invoices(
InvoiceID  INTEGER  primary key,
InvoiceDate DATE,
DueDate  DATE check(DueDate>InvoiceDate),
Amount REAL check(Amount>0)
);
```

**Output:**
<img width="1186" height="275" alt="image" src="https://github.com/user-attachments/assets/a7c63648-3068-4cf8-9e6a-6f8f99869329" />


**Question 6**
---
Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email

```sql
insert into Customers (CustomerID, Name, Address, Email )
select CustomerID, Name, Address, Email 
from Old_customers ;
```

**Output:**

<img width="1162" height="192" alt="image" src="https://github.com/user-attachments/assets/5ce0160b-73b4-4e28-95c7-9f76986e0b67" />


**Question 7**
---
Write a SQL query to Add a new ParentsNumber column  as number and Adhar_Number as Number in the Student_details table.

```sql
alter table Student_details add ParentsNumber  number;
alter table Student_details add  Adhar_Number number;
```

**Output:**
<img width="1181" height="373" alt="image" src="https://github.com/user-attachments/assets/26ebf6a6-d1c2-499b-8cab-5695a7cbe01f" />


**Question 8**
---
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
create table Shipments(
ShipmentID  INTEGER  primary key,
ShipmentDate  DATE,
SupplierID  INTEGER,
OrderID  INTEGER, 
foreign key(SupplierID) references  Suppliers(SupplierID),
foreign key(OrderID) references  Orders(OrderID)
);
```

**Output:**
<img width="1191" height="239" alt="image" src="https://github.com/user-attachments/assets/ea08b923-5923-4916-87c4-e0db2c4eb86c" />


**Question 9**
---
Create a table named Customers with the following columns:

CustomerID as INTEGER
Name as TEXT
Email as TEXT
JoinDate as DATETIME
```sql
create table customers(
CustomerID INTEGER,
Name  TEXT,
Email  TEXT,
JoinDate DATETIME
);
```

**Output:**
<img width="1189" height="387" alt="image" src="https://github.com/user-attachments/assets/03b50b06-4bed-42a4-8d01-79ae6147b91a" />


**Question 10**
---
Create a new table named products with the following specifications:
product_id as INTEGER and primary key.
product_name as TEXT and not NULL.
list_price as DECIMAL (10, 2) and not NULL.
discount as DECIMAL (10, 2) with a default value of 0 and not NULL.
A CHECK constraint at the table level to ensure:
list_price is greater than or equal to discount
discount is greater than or equal to 0
list_price is greater than or equal to 0

```sql
create table products(
product_id  INTEGER  primary key,
product_name  TEXT  not NULL,
list_price  DECIMAL (10, 2) not NULL,
discount  DECIMAL (10, 2) not null
default 0,
check(list_price>=discount
and discount>=0
and list_price>0
)
 
);
```

**Output:**

<img width="1188" height="288" alt="image" src="https://github.com/user-attachments/assets/dddeca5f-c219-4a31-a63e-ce0b312f8ae3" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
