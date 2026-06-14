# 📘 SQL Basic Commands (MySQL Notes)

This document contains basic SQL commands I learned while starting my SQL journey.

## DAY 01

---

## 1. CREATE TABLE

Used to create a new table in a database.

📌 Syntax:

```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype
);
📌 Example:
CREATE TABLE students (
    id INT,
    name VARCHAR(50),
    age INT
);

```

🟡 2. INSERT INTO

Used to insert data into a table.

```sql
📌 Syntax:
INSERT INTO table_name (column1, column2, column3)
VALUES (value1, value2, value3);
📌 Example:
INSERT INTO students (id, name, age)
VALUES (1, 'Jiya', 20);
```

🔵 3. SELECT

Used to retrieve data from a table.

```sql
📌 Syntax to view the created table:
SELECT * FROM table_name;
📌 Example:

SELECT * FROM students;
```

⭐ Summary
CREATE → Create a new table
INSERT → Add data into table
SELECT → Retrieve data from table

# Day 2 - SQL Querying Fundamentals

## Topics Covered

Today, I learned some of the most commonly used SQL querying commands that help retrieve, filter, sort, and analyze data from database tables.

---

## 1. SELECT

The `SELECT` statement is used to retrieve data from a table.

### Syntax

```sql
SELECT column_name
FROM table_name;
```

### Example

```sql
SELECT * FROM employees;
```

---

## 2. WHERE

The `WHERE` clause is used to filter records based on a specified condition.

### Syntax

```sql
SELECT column_name
FROM table_name
WHERE condition;
```

### Example

```sql
SELECT *
FROM employees
WHERE salary > 50000;
```

---

## 3. ORDER BY

The `ORDER BY` clause is used to sort query results in ascending or descending order.

### Syntax

```sql
SELECT column_name
FROM table_name
ORDER BY column_name ASC|DESC;
```

### Example

```sql
SELECT *
FROM employees
ORDER BY salary DESC;
```

---

## 4. LIMIT

The `LIMIT` clause is used to restrict the number of rows returned.

### Syntax

```sql
SELECT column_name
FROM table_name
LIMIT number;
```

### Example

```sql
SELECT *
FROM employees
LIMIT 5;
```

---

## 5. DISTINCT

The `DISTINCT` keyword is used to return only unique values.

### Syntax

```sql
SELECT DISTINCT column_name
FROM table_name;
```

### Example

```sql
SELECT DISTINCT department
FROM employees;
```

---

## 6. BETWEEN

The `BETWEEN` operator is used to filter values within a specified range.

### Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```

### Example

```sql
SELECT *
FROM employees
WHERE salary BETWEEN 30000 AND 70000;
```

---

# Aggregate Functions

Aggregate functions perform calculations on multiple rows and return a single result.

## 1. COUNT()

Returns the number of rows.

### Example

```sql
SELECT COUNT(*)
FROM employees;
```

---

## 2. SUM()

Returns the total sum of a numeric column.

### Example

```sql
SELECT SUM(salary)
FROM employees;
```

---

## 3. AVG()

Returns the average value of a numeric column.

### Example

```sql
SELECT AVG(salary)
FROM employees;
```

---

## 4. MIN()

Returns the minimum value in a column.

### Example

```sql
SELECT MIN(salary)
FROM employees;
```

---

## 5. MAX()

Returns the maximum value in a column.

### Example

```sql
SELECT MAX(salary)
FROM employees;
```

---

## Key Takeaways

- Learned how to retrieve data using `SELECT`.
- Filtered records using `WHERE`.
- Sorted results with `ORDER BY`.
- Limited output using `LIMIT`.
- Retrieved unique values using `DISTINCT`.
- Filtered data ranges using `BETWEEN`.
- Performed data analysis using aggregate functions:
  - `COUNT()`
  - `SUM()`
  - `AVG()`
  - `MIN()`
  - `MAX()`

m

## Day 3: CASE, GROUP BY, HAVING, and Subqueries

---

# 1. CASE Statement

The `CASE` statement is used to add conditional logic in SQL. It works like an IF-ELSE statement in programming.

### Syntax

```sql
SELECT column_name,
       CASE
           WHEN condition1 THEN result1
           WHEN condition2 THEN result2
           ELSE result
       END AS alias_name
FROM table_name;
```

### Example

```sql
SELECT employee_name,
       salary,
       CASE
           WHEN salary >= 70000 THEN 'High Salary'
           WHEN salary >= 40000 THEN 'Medium Salary'
           ELSE 'Low Salary'
       END AS salary_category
FROM employees;
```

### Use Cases

- Categorizing data
- Creating custom labels
- Conditional calculations

---

# 2. GROUP BY Clause

The `GROUP BY` clause is used to group rows that have the same values into summary rows.

### Syntax

```sql
SELECT column_name,
       aggregate_function(column_name)
FROM table_name
GROUP BY column_name;
```

### Example

```sql
SELECT department,
       COUNT(*) AS total_employees
FROM employees
GROUP BY department;
```

### Output Example

| Department | Total Employees |
| ---------- | --------------- |
| HR         | 5               |
| IT         | 10              |
| Sales      | 7               |

### Common Aggregate Functions

```sql
COUNT()
SUM()
AVG()
MIN()
MAX()
```

---

# 3. HAVING Clause

The `HAVING` clause is used to filter grouped data after applying `GROUP BY`.

### Difference Between WHERE and HAVING

| WHERE                          | HAVING                        |
| ------------------------------ | ----------------------------- |
| Filters rows before grouping   | Filters groups after grouping |
| Cannot use aggregate functions | Can use aggregate functions   |

### Syntax

```sql
SELECT column_name,
       aggregate_function(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

### Example

```sql
SELECT department,
       COUNT(*) AS total_employees
FROM employees
GROUP BY department
HAVING COUNT(*) > 5;
```

### Result

Only departments having more than 5 employees will be displayed.

---

# 4. Subqueries

A subquery is a query inside another query.

### Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name OPERATOR
(
    SELECT column_name
    FROM another_table
);
```

### Example 1: Salary Above Average

```sql
SELECT employee_name, salary
FROM employees
WHERE salary >
(
    SELECT AVG(salary)
    FROM employees
);
```

### Example 2: Maximum Salary

```sql
SELECT employee_name, salary
FROM employees
WHERE salary =
(
    SELECT MAX(salary)
    FROM employees
);
```

### Types of Subqueries

#### 1. Single Row Subquery

Returns one value.

```sql
SELECT *
FROM employees
WHERE salary >
(
    SELECT AVG(salary)
    FROM employees
);
```

#### 2. Multiple Row Subquery

Returns multiple values.

```sql
SELECT *
FROM employees
WHERE department_id IN
(
    SELECT department_id
    FROM departments
);
```

#### 3. Correlated Subquery

Runs once for every row processed by the outer query.

```sql
SELECT employee_name, salary
FROM employees e
WHERE salary >
(
    SELECT AVG(salary)
    FROM employees
    WHERE department = e.department
);
```

---

# Key Takeaways

✅ Learned how to use CASE statements for conditional logic

✅ Understood how GROUP BY creates summary data

✅ Used HAVING to filter grouped records

✅ Learned how subqueries allow one query to use the result of another query

✅ Practiced combining aggregate functions with grouping and filtering

---
