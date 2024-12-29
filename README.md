# SQL_Notes


# SQL Documentation

## Table of Contents

1. [Introduction](#introduction)  
2. [SQL Data Types](#sql-data-types)  
3. [SQL Commands](#sql-commands)  
   - [Data Definition Language (DDL)](#1-data-definition-language-ddl)  
   - [Data Manipulation Language (DML)](#2-data-manipulation-language-dml)  
   - [Data Query Language (DQL)](#3-data-query-language-dql)  
   - [Data Control Language (DCL)](#4-data-control-language-dcl)  
   - [Transaction Control Language (TCL)](#5-transaction-control-language-tcl)  
4. [Joins](#joins)  
5. [Aggregate Functions](#aggregate-functions)  
6. [Subqueries](#subqueries)  
7. [Set Operations](#set-operations)  
8. [Best Practices](#best-practices)  

---

## Introduction

SQL (Structured Query Language) is used to interact with relational databases. It performs operations such as creating, reading, updating, and deleting data (CRUD).

### Key Concepts:
- **Database**: A collection of interrelated data.
- **DBMS**: Software to manage databases.
- **RDBMS**: Uses tables (relations) to organize data.
- **SQL**: Language to interact with RDBMS.

---

## SQL Data Types

| **Type**      | **Description**                       |
|---------------|---------------------------------------|
| **CHAR(n)**   | Fixed-length string (0-255).          |
| **VARCHAR(n)**| Variable-length string (0-255).       |
| **INT**       | Integer (-2.1B to 2.1B).              |
| **FLOAT**     | Decimal (23-digit precision).         |
| **DATE**      | Stores date (YYYY-MM-DD).             |

- Use `UNSIGNED` for non-negative numeric values (e.g., `UNSIGNED INT`).

---

## SQL Commands

### 1. Data Definition Language (DDL)
- **CREATE**: Create database objects.
  ```sql
  CREATE TABLE employees (id INT, name VARCHAR(50));
  ```
- **ALTER**: Modify structure.
  ```sql
  ALTER TABLE employees ADD COLUMN salary DECIMAL(10, 2);
  ```
- **DROP**: Delete objects.
  ```sql
  DROP TABLE employees;
  ```

### 2. Data Manipulation Language (DML)
- **INSERT**: Add data.
  ```sql
  INSERT INTO employees (id, name) VALUES (1, 'John');
  ```
- **UPDATE**: Modify data.
  ```sql
  UPDATE employees SET name = 'Alice' WHERE id = 1;
  ```
- **DELETE**: Remove data.
  ```sql
  DELETE FROM employees WHERE id = 1;
  ```

### 3. Data Query Language (DQL)
- **SELECT**: Retrieve data.
  ```sql
  SELECT * FROM employees WHERE salary > 50000;
  ```

### 4. Data Control Language (DCL)
- **GRANT**: Assign permissions.
  ```sql
  GRANT SELECT ON employees TO user;
  ```
- **REVOKE**: Remove permissions.
  ```sql
  REVOKE SELECT ON employees FROM user;
  ```

### 5. Transaction Control Language (TCL)
- **COMMIT**: Save changes.
- **ROLLBACK**: Undo changes.
- **SAVEPOINT**: Partial rollback point.
  ```sql
  SAVEPOINT before_update;
  ```

---

## Joins

### Types of Joins:
1. **INNER JOIN**: Rows with matching values in both tables.
2. **LEFT JOIN**: All rows from the left table, matches from the right.
3. **RIGHT JOIN**: All rows from the right table, matches from the left.
4. **FULL JOIN**: All rows from both tables.

### Example:
```sql
SELECT e.name, d.department 
FROM employees e 
INNER JOIN departments d 
ON e.dept_id = d.id;
```

---

## Aggregate Functions

| **Function** | **Description**                     |
|--------------|-------------------------------------|
| **COUNT()**  | Count rows.                         |
| **SUM()**    | Total sum of values.                |
| **AVG()**    | Average value.                      |
| **MAX()**    | Maximum value.                      |
| **MIN()**    | Minimum value.                      |

### Example:
```sql
SELECT department, AVG(salary) 
FROM employees 
GROUP BY department;
```

---

## Subqueries

- Used for filtering, comparison, or calculations.
  ```sql
  SELECT name 
  FROM employees 
  WHERE salary > (SELECT AVG(salary) FROM employees);
  ```

---

## Set Operations

1. **UNION**: Combine results, remove duplicates.
2. **UNION ALL**: Combine results, keep duplicates.
3. **INTERSECT**: Rows common to all queries.
4. **EXCEPT**: Rows in the first query but not in the second.

### Example:
```sql
SELECT name FROM employees
UNION
SELECT name FROM contractors;
```

---

## Best Practices

1. Use **naming conventions** for clarity.
2. Optimize queries with **indexes**.
3. Avoid `SELECT *`; specify required columns.
4. Use **transactions** to ensure data integrity.

