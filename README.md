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
[images/day1-1.png]
[images/day1-2.jpeg]
```

⭐ Summary
CREATE → Create a new table
INSERT → Add data into table
SELECT → Retrieve data from table
