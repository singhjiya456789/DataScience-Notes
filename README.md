# 📘 SQL Basic Commands (MySQL Notes)

> A personal log of my SQL practice and learning.
> This document contains basic SQL commands I learned while starting my SQL journey.

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

# Day 4: SQL JOINS + GROUP BY + HAVING + AGGREGATES

## 1. Introduction to JOINS

Joins are used to combine data from two or more tables based on a related column (primary key–foreign key relationship).

Example Relationship
Customers → customer_id
Orders → customer_id

# 2. INNER JOIN

Returns only matching records from both tables.

- Syntax

```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.common_column = table2.common_column;
```

Example

```sql
SELECT c.name, o.order_id, o.amount
FROM Customers c
INNER JOIN Orders o
ON c.customer_id = o.customer_id;
```

## 3. LEFT JOIN

Returns all records from left table + matching records from right table.

Example

```sql
SELECT c.name, o.order_id, o.amount
FROM Customers c
LEFT JOIN Orders o
ON c.customer_id = o.customer_id;
```

## 4. RIGHT JOIN

Returns all records from right table + matching from left table.

Example

```sql
SELECT c.name, o.order_id, o.amount
FROM Customers c
RIGHT JOIN Orders o
ON c.customer_id = o.customer_id;
```

# 5. FULL OUTER JOIN

Returns all records from both tables.

Example

```sql
SELECT c.name, o.order_id, o.amount
FROM Customers c
FULL OUTER JOIN Orders o
ON c.customer_id = o.customer_id;
```

# 6. CROSS JOIN

Returns all possible combinations of rows.

Example

```sql
SELECT c.name, o.order_id
FROM Customers c
CROSS JOIN Orders o;
```

# 7. GROUP BY with JOINS

Used to group data after combining tables.

Example: Count Orders per Customer

```sql
SELECT c.name, COUNT(o.order_id) AS total_orders
FROM Customers c
INNER JOIN Orders o
ON c.customer_id = o.customer_id
GROUP BY c.name;

Example: Total Spending per Customer
SELECT c.name, SUM(o.amount) AS total_spent
FROM Customers c
INNER JOIN Orders o
ON c.customer_id = o.customer_id
GROUP BY c.name;
```

# 8. HAVING Clause with JOINS

Used to filter grouped results.

Example: Customers with more than 1 order

```sql
SELECT c.name, COUNT(o.order_id) AS total_orders
FROM Customers c
INNER JOIN Orders o
ON c.customer_id = o.customer_id
GROUP BY c.name
HAVING COUNT(o.order_id) > 1;
```

# 9. AGGREGATE FUNCTIONS WITH JOINS

```sql
COUNT
COUNT(o.order_id)
SUM
SUM(o.amount)
AVG
AVG(o.amount)
MIN / MAX
MIN(o.amount)
MAX(o.amount)
```

## Key Takeaways

✅ Learned all major types of SQL JOINs
✅ Understood how tables are connected using keys
✅ Practiced GROUP BY with joins
✅ Used HAVING to filter grouped results
✅ Applied aggregate functions (COUNT, SUM, AVG) with real data

# 📘 SQL Learning Journey - Day 5

## 🚀 What I Learned Today

Today, I continued strengthening my understanding of SQL JOINs and explored two important SQL concepts:

### 🔗 JOIN Practice

- Practiced INNER JOIN queries
- Solved customer-order analysis problems
- Used JOINs with aggregate functions like COUNT() and SUM()
- Worked on GROUP BY and HAVING with JOINs

### 📝 CASE WHEN

CASE WHEN is SQL's way of writing **conditional logic** — similar to if/else in Python.

Example:

```sql
SELECT customer_name,
       CASE
           WHEN amount >= 1000 THEN 'High Value'
           WHEN amount >= 500 THEN 'Medium Value'
           ELSE 'Low Value'
       END AS category
FROM Orders;
```

### Subqueries

A subquery is a query **nested inside another query**. It can appear in the SELECT, FROM, or WHERE clause.
Learned how to write queries inside other queries to solve more complex problems.

Example:

```sql
SELECT customer_name
FROM Customers
WHERE customer_id IN (
    SELECT customer_id
    FROM Orders
    WHERE amount > 1000
);
```

### Subquery in WHERE Clause

Find employees who earn more than the average salary.

```sql
SELECT name, salary
FROM employees
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
);
```

### Subquery in FROM Clause (Derived Table) Treat a subquery as a temporary table.

```sql
SELECT
    dept_summary.department_name,
    dept_summary.avg_salary
FROM (
    SELECT
        departments.department_name,
        AVG(employees.salary) AS avg_salary
    FROM employees
    INNER JOIN departments
        ON employees.department_id = departments.id
    GROUP BY departments.department_name
) AS dept_summary
WHERE dept_summary.avg_salary > 60000;
```

**What I learned:** Wrapping a query in FROM (...) creates a "derived table" — it's like a temporary view. This is a powerful pattern for multi-step analysis and will be useful when writing complex analytical queries.

### Subquery in SELECT Clause Add a calculated column based on a separate aggregation.

```sql
SELECT
    name,
    salary,
    (SELECT AVG(salary) FROM employees) AS company_avg
FROM employees;
```

**What I learned:** This is useful for side-by-side comparisons — seeing each employee's salary against the company average in the same row.

# 🎯 Skills Gained

Better understanding of table relationships using JOINs
Applying conditional logic with CASE WHEN
Retrieving data using nested queries (Subqueries)
Solving real-world SQL analysis problems

# 📘 SQL Learning Journey – Day 6: Common Table Expressions (CTEs)

# 🚀 What I Learned Today

Today, I learned about **Common Table Expressions (CTEs)**, a feature that helps write cleaner and more readable SQL queries.

CTEs allow complex queries to be broken into smaller logical steps, making them easier to understand, debug, and maintain.

---

# 📝 Common Table Expressions (CTEs)

A CTE is a temporary named result set created using the `WITH` keyword.

### Syntax

```sql
WITH cte_name AS (
    SELECT column_name
    FROM table_name
)
SELECT *
FROM cte_name;
```

---

# 🔄 Subquery vs CTE

### Using a Subquery

```sql
SELECT name, salary
FROM (
    SELECT name, salary
    FROM employees
    WHERE department = 'IT'
) AS it_employees
WHERE salary > 50000;
```

### Using a CTE

```sql
WITH it_employees AS (
    SELECT name, salary
    FROM employees
    WHERE department = 'IT'
)
SELECT name, salary
FROM it_employees
WHERE salary > 50000;
```

### Key Takeaway

- Both queries produce the same result.
- CTEs improve readability.
- CTEs are easier to maintain when queries become complex.

---

# 🔗 Multiple CTEs

Multiple CTEs can be chained together.

```sql
WITH dept_count AS (
    SELECT department,
           COUNT(*) AS total_emp
    FROM employees
    GROUP BY department
),
large_depts AS (
    SELECT department,
           total_emp
    FROM dept_count
    WHERE total_emp > 2
)
SELECT *
FROM large_depts;
```

### What I Learned

- One CTE can use another CTE.
- Complex logic can be divided into multiple steps.
- Queries become easier to understand.

---

# 🔁 Recursive CTEs

Recursive CTEs reference themselves and are useful for hierarchical data.

Examples:

- Employee-manager relationships
- Organization charts
- Category trees
- Folder structures

```sql
WITH RECURSIVE org_chart AS (
    SELECT id,
           name,
           manager_id,
           1 AS level
    FROM employees
    WHERE manager_id IS NULL

    UNION ALL

    SELECT e.id,
           e.name,
           e.manager_id,
           oc.level + 1
    FROM employees e
    JOIN org_chart oc
      ON e.manager_id = oc.id
)
SELECT *
FROM org_chart;
```

### How It Works

1. Finds the top-level employee.
2. Finds employees reporting to them.
3. Repeats the process.
4. Stops when no more rows are found.

---

# 💡 Important Concepts Learned

## Filtering Aggregated Results

```sql
WITH dept_summary AS (
    SELECT department,
           COUNT(*) AS total_emp
    FROM employees
    GROUP BY department
)
SELECT *
FROM dept_summary
WHERE total_emp > 2;
```

---

## COUNT Variations

```sql
COUNT(*)            -- Counts all rows
COUNT(emp_id)       -- Counts non-null emp_id values
COUNT(department)   -- Ignores NULL departments
```

### Key Learning

Use the appropriate COUNT function depending on what you want to measure.

---

## One Row Per What?

Whenever using `GROUP BY`, ask:

> "One row per WHAT?"

The answer determines the grouping column.

Example:

```sql
SELECT department,
       COUNT(*) AS total_emp
FROM employees
GROUP BY department;
```

One row per **department**.

---

## Joining Back to Original Table

```sql
WITH first_hired AS (
    SELECT department,
           MIN(emp_id) AS min_emp_id
    FROM employees
    GROUP BY department
)
SELECT e.emp_id,
       e.emp_name,
       e.department
FROM employees e
JOIN first_hired f
  ON e.emp_id = f.min_emp_id
 AND e.department = f.department;
```

### Why?

The CTE finds the required IDs, and the JOIN retrieves complete employee details.

---

## UNION ALL vs JOIN

| Feature               | JOIN           | UNION ALL           |
| --------------------- | -------------- | ------------------- |
| Combines              | Columns        | Rows                |
| Requires matching key | Yes            | No                  |
| Use Case              | Related tables | Similar result sets |

### Example

```sql
-- JOIN
SELECT *
FROM employees e
JOIN departments d
ON e.department = d.department;
```

```sql
-- UNION ALL
SELECT name
FROM employees

UNION ALL

SELECT name
FROM managers;
```

---

# 🎯 Skills Gained

- Creating and using CTEs
- Converting subqueries into CTEs
- Chaining multiple CTEs
- Understanding recursive CTEs
- Working with hierarchical data
- Using COUNT functions correctly
- Joining CTE results back to source tables
- Understanding UNION ALL vs JOIN
- Writing cleaner and more maintainable SQL

---

# 📘Day 7: Window Functions

## 🚀 What I Learned Today

Today, I learned about **Window Functions** in SQL. Window functions perform calculations across a set of rows related to the current row without grouping the results into a single row.

Unlike `GROUP BY`, window functions allow us to retain individual row details while performing aggregate calculations.

---

## 📝 Window Functions

A window function uses the `OVER()` clause to define the set of rows (window) on which the function operates.

### Basic Syntax

```sql
SELECT column_name,
       window_function() OVER (
           PARTITION BY column_name
           ORDER BY column_name
       )
FROM table_name;
```

📌 Concepts Covered

# 1. ROW_NUMBER()

Assigns a unique sequential number to each row.

```sql
SELECT emp_name,
       salary,
       ROW_NUMBER() OVER (ORDER BY salary DESC) AS row_num
FROM Employees;
```

# 2. RANK()

Assigns ranks to rows. Duplicate values receive the same rank, and gaps may occur.

```sql
SELECT emp_name,
       salary,
       RANK() OVER (ORDER BY salary DESC) AS emp_rank
FROM Employees;
```

# 3. DENSE_RANK()

Similar to RANK(), but without gaps in ranking.

```sql
SELECT emp_name,
       salary,
       DENSE_RANK() OVER (ORDER BY salary DESC) AS dense_rank
FROM Employees;
```

# 4. SUM() OVER()

Calculates running totals or totals without grouping rows.

```sql
SELECT emp_name,
       salary,
       SUM(salary) OVER () AS total_salary
FROM Employees;
```

# 5. AVG() OVER()

Calculates averages while keeping all rows visible.

```sql
SELECT emp_name,
       salary,
       AVG(salary) OVER (PARTITION BY department) AS dept_avg
FROM Employees;
```

# 6. MAX() OVER()

Finds the maximum value within a partition.

```sql
SELECT emp_name,
       department,
       MAX(salary) OVER (PARTITION BY department) AS max_salary
FROM Employees;
```

# 7. LAG()

Accesses the previous row's value.

```sql
SELECT emp_name,
       salary,
       LAG(salary) OVER (ORDER BY salary) AS previous_salary
FROM Employees;
```

# 8. LEAD()

Accesses the next row's value.

```sql
SELECT emp_name,
       salary,
       LEAD(salary) OVER (ORDER BY salary) AS next_salary
FROM Employees;
```

# 📚 Key Takeaways

- Window functions do not collapse rows like GROUP BY.
- PARTITION BY divides data into groups.
- ORDER BY defines row order within a window.
- Useful for ranking, running totals, comparisons, and analytics.
- Commonly used in Data Analyst and Data Science roles.

# 🛠 Skills Practiced

ROW_NUMBER()
RANK()
DENSE_RANK()
SUM() OVER()
AVG() OVER()
MAX() OVER()
LAG()
LEAD()
PARTITION BY
ORDER BY in Window Functions

---
