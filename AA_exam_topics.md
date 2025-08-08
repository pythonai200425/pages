# 📘 Exam Topics: SQL, PostgreSQL, Python & Streamlit

## 1. 📄 SQLite Basics

* Creating tables with `CREATE TABLE`, including column constraints:

* `PRIMARY KEY`, `UNIQUE`, `NOT NULL`, `DEFAULT`, `CHECK`
* Inserting data using `INSERT INTO`
* Querying data using `SELECT`, `WHERE`, `ORDER BY`, `LIMIT`, `OFFSET`
* Using `UNION` to combine results without duplicates
* Updating and deleting rows using `UPDATE`, `DELETE`
* Aggregate functions like `AVG()`, `COUNT()`, `GROUP BY`, `HAVING`
* Filtering with conditions (`LIKE`, `>`, `<`, etc)
* Creating and using `TRIGGERS` for automated responses to changes

## 2. 🐍 Working with SQLite in Python

* Connecting to SQLite using `sqlite3.connect()`
* Executing SQL commands in Python using cursor
* Using `fetchall()` to get results
* Handling user input and validating it with `try-except`
* Example: inserting and displaying students with ID, name, grade, birth year

## 3. 🔗 SQL Relationships

* One-to-One (1:1): users + passwords

  * `UNIQUE`, `FOREIGN KEY`, `LEFT JOIN`, `INNER JOIN`
* One-to-Many (1\:N): employees + departments

  * Showing all employees with department name
  * Finding departments with or without employees
* Many-to-Many (M\:N): citizens + cable\_tv + subscriptions

  * Junction tables and composite primary keys
  * Counting subscriptions per company

## 4. 🐘 PostgreSQL  

* Basic operations with PostgreSQL  
* PGAdmin  

## 5. 🧐 Advanced SQL (SQLite & PostgreSQL)

* Creating and querying `VIEW`s for reusable queries
* Using `EXPLAIN QUERY PLAN` to analyze query performance *BONUS TOPIC*
* `AUTOINCREMENT` in SQLite and `SERIAL` in PostgreSQL
* `UNION` to combine two tables without duplicates
* `ON DELETE CASCADE` for handling deletions with foreign keys
* `RANDOM()` values and numeric formatting
* JSONB fields to replace M\:N structures in PostgreSQL
* `CROSS JOIN`, `FULL OUTER JOIN`, and other advanced JOIN types
* Defining `TRIGGERS` for insert/update/delete logic

## 6. ⚙️ Stored Procedures (PostgreSQL)

* Creating stored functions using `CREATE FUNCTION` and procedures with `CREATE PROCEDURE`
* Returning multiple `OUT` parameters
* Returning TABLE structure
* INTO usage
* Example procedures:

  * Greeting with timestamp
  * Multiply three numbers
  * Division with quotient and remainder
  * Math operations (sum, diff, sqrt, power)
  * Preparing and querying a books + authors database
  * Summary statistics: oldest, youngest, avg price, total books

## 7. PostgreSQL with Python

* Connecting using `psycopg2.connect()`
* Using `RealDictCursor` to get dictionary-like rows
* Creating tables, inserting data, and querying with Python
* Handling exceptions with `try-except-finally`
* Calling stored procedures from Python using `CALL procedure_name()` with `cursor.execute()`
* SQL Injection protection: using placeholders to prevent attacks

  * `?` for SQLite (parameterized queries)
  * `%s` for PostgreSQL with psycopg2

## 7. 🔁 UPSERT

* PostgreSQL `ON CONFLICT DO UPDATE`
* Inserting or updating records based on `PRIMARY KEY` or `UNIQUE` constraint
* Wrapping UPSERT logic in stored procedures
* Use of `EXCLUDED.column_name`

## 8. 🔐 Transactions

* What is a transaction?
* `BEGIN`, `COMMIT`, `ROLLBACK`
* Ensuring atomicity: all-or-nothing operations
* Python example: transferring money between accounts with commit/rollback


