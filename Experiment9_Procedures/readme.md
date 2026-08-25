# Experiment 9: PL/SQL – Procedures and Functions

## AIM
To understand and implement procedures and functions in PL/SQL for performing various operations such as calculations, decision-making, and looping.

---

## THEORY

PL/SQL (Procedural Language/SQL) extends the  SQL by adding procedural constructs like variables, conditions, loops, procedures, and functions. Procedures and functions are subprograms that help modularize the code and improve reusability.

### **Procedure**
A PL/SQL **procedure** is a subprogram that performs a specific action. It does not return a value directly but can return values using `OUT` parameters.

**Syntax:**
```sql
CREATE OR REPLACE PROCEDURE procedure_name (parameters)
IS
BEGIN
   -- statements
END;
```

To call the procedure

```sql
EXEC procedure_name(arguments);
```

### **Function**
A PL/SQL **function** is a subprogram that returns a single value using the RETURN keyword.

```sql
CREATE OR REPLACE FUNCTION function_name (parameters)
RETURN datatype
IS
BEGIN
   -- statements
   RETURN value;
END;
```

To call the function:

```sql
SELECT function_name(arguments) FROM DUAL;
```

Key Differences:

-A procedure does not return a value, whereas a function must return a value.
-Functions can be called from SQL queries, procedures cannot (in most cases).

## 1. Write a PL/SQL Procedure to Find the Square of a Number

### Steps:
- Create a procedure named `find_square`.
- Declare a parameter to accept a number.
- Inside the procedure, compute the square of the input number.
- Use `DBMS_OUTPUT.PUT_LINE` to display the result.
- Call the procedure with a number as input.


**Query**
```
CREATE OR REPLACE PROCEDURE find_square(n NUMBER)
IS
    square NUMBER;
BEGIN
    square := n * n;

    DBMS_OUTPUT.PUT_LINE('Square of ' || n || ' is ' || square);
END;
/
```
**Execute**
```
EXEC find_square(6);
```

**Expected Output:**  
Square of 6 is 36

<img width="941" height="372" alt="Screenshot 2026-08-25 103746" src="https://github.com/user-attachments/assets/3449c2c2-407e-4c28-b47f-e9061f34b1d9" />

---

## 2. Write a PL/SQL Function to Return the Factorial of a Number

### Steps:
- Create a function named `get_factorial`.
- Declare a parameter to accept a number.
- Use a loop to calculate the factorial.
- Return the result using the `RETURN` statement.
- Call the function using a `SELECT` statement or in an anonymous block.

  
**Query**
```
CREATE OR REPLACE FUNCTION get_factorial(n NUMBER)
RETURN NUMBER
IS
    fact NUMBER := 1;
    i NUMBER := 1;
BEGIN
    WHILE i <= n LOOP
        fact := fact * i;
        i := i + 1;
    END LOOP;

    RETURN fact;
END;
/
```

**Execute**
```
BEGIN
    DBMS_OUTPUT.PUT_LINE('Factorial of 5 is ' || get_factorial(5));
END;
/
```

**Expected Output:**  
Factorial of 5 is 120
<img width="927" height="345" alt="image" src="https://github.com/user-attachments/assets/a62e69ff-5ede-408b-9e51-28e110bbb062" />

---

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Steps:
- Create a procedure named `check_even_odd`.
- Accept an input parameter.
- Use the `MOD` function to check if the number is divisible by 2.
- Display whether it is Even or Odd using `DBMS_OUTPUT.PUT_LINE`.

**Query**
```
CREATE OR REPLACE PROCEDURE check_even_odd(n NUMBER)
IS
BEGIN
    IF MOD(n, 2) = 0 THEN
        DBMS_OUTPUT.PUT_LINE(n || ' is Even');
    ELSE
        DBMS_OUTPUT.PUT_LINE(n || ' is Odd');
    END IF;
END;
/
```

**Execute**
```
EXEC check_even_odd(12);
```

**Expected Output:**  
12 is Even
<img width="968" height="367" alt="image" src="https://github.com/user-attachments/assets/ef92111b-c931-435f-9b24-d70277e7075b" />

---

## 4. Write a PL/SQL Function to Return the Reverse of a Number

### Steps:
- Create a function named `reverse_number`.
- Accept an input number as parameter.
- Use a loop to reverse the digits of the number.
- Return the reversed number.
- Call the function and display the output.

**Query**
```
CREATE OR REPLACE FUNCTION reverse_number(n NUMBER)
RETURN NUMBER
IS
    num NUMBER := n;
    rev NUMBER := 0;
    digit NUMBER;
BEGIN
    WHILE num > 0 LOOP
        digit := MOD(num, 10);
        rev := rev * 10 + digit;
        num := TRUNC(num / 10);
    END LOOP;

    RETURN rev;
END;
/
```

**Execute**
```
BEGIN
    DBMS_OUTPUT.PUT_LINE(
        'Reversed number of 1234 is ' || reverse_number(1234)
    );
END;
/
````

**Expected Output:**  
Reversed number of 1234 is 4321

<img width="928" height="345" alt="Screenshot 2026-08-25 104850" src="https://github.com/user-attachments/assets/5fe56005-0e22-4e73-aeed-6fc070d4fada" />


---

## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number

### Steps:
- Create a procedure named `print_table`.
- Accept an input number.
- Use a loop from 1 to 10 to multiply the input number.
- Display the multiplication results using `DBMS_OUTPUT.PUT_LINE`.

**Query**
```

CREATE OR REPLACE PROCEDURE print_table(n NUMBER)
IS
    i NUMBER := 1;
BEGIN
    DBMS_OUTPUT.PUT_LINE('Multiplication table of ' || n || ':');

    WHILE i <= 10 LOOP
        DBMS_OUTPUT.PUT_LINE(
            n || ' x ' || i || ' = ' || (n * i)
        );

        i := i + 1;
    END LOOP;
END;
/
```
**Execute**
```
EXEC print_table(5);
```

**Expected Output:**  
Multiplication table of 5:  
5 x 1 = 5  
5 x 2 = 10  
5 x 3 = 15  
...  
5 x 10 = 50
<img width="970" height="368" alt="image" src="https://github.com/user-attachments/assets/9f810638-4634-4060-9bf0-73e536590e5c" />

## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.
