## Table of Contents

1. [Manipulation](#manipulation)
   - [Introduction to SQL](#introduction-to-sql)
   - [Relational Databases](#relational-databases)
   - [Statements](#statements)
   - [Create](#create)
   - [Insert](#insert)
   - [Select](#select)
   - [Alter](#alter)
   - [Update](#update)
   - [Delete](#delete)
   - [Constraints](#constraints)
   - [Review](#review)
2. [Queries](#queries)
   - [Introduction](#introduction)
   - [Select](#select-1)
   - [As](#as)
   - [Distinct](#distinct)
   - [Where](#where)
   - [Like I](#like-i)
   - [Like II](#like-ii)
   - [Is Null](#is-null)
   - [Between](#between)
   - [And](#and)
   - [Or](#or)
   - [Order By](#order-by)
   - [Limit](#limit)
   - [Case](#case)
   - [Review](#review-1)

---

# Manipulation

---

## Introduction to SQL

### What is SQL?

**SQL** stands for **Structured Query Language**.

- It is a **programming language** used to talk to databases.
- It is used by **Database Management Systems (DBMS)** to **manage** and **query** (ask questions about) data stored in a **relational database**.

---

### What is a Relational Database?

A **relational database** is a way of storing data using:

- **Tables** made of **columns** and **rows**
- **Relationships** between those tables

Think of it like organized spreadsheets that can be linked to each other.

---

### How Does SQL Work?

SQL uses **simple, declarative statements**. That means you tell the database **what** you want, not **how** to do it step by step.

This helps to:

- Keep data **accurate** and **secure**
- Maintain the **integrity** (correctness and consistency) of databases
- Work with databases of **any size**

---

### Why Learn SQL?

- SQL is used in **web frameworks** and **database applications** everywhere.
- Knowing SQL lets you **explore your data** and **make better decisions**.
- The ideas you learn in SQL apply to **almost every data storage system**.

---

### The Four Types of SQL Statements

SQL commands can be grouped into **four main classes** (sub-languages):

| Type                           | Short Name | What It Does                                                         | Example                                      |
| ------------------------------ | ---------- | -------------------------------------------------------------------- | -------------------------------------------- |
| **Data Query Language**        | DQL        | Asks questions and gets data from the database                       | `SELECT` — retrieves data                    |
| **Data Definition Language**   | DDL        | Creates and changes the **structure** of the database (tables, etc.) | `CREATE` — creates an object (e.g., a table) |
| **Data Manipulation Language** | DML        | Adds, updates, or deletes **data** inside the database               | (covered later)                              |
| **Data Control Language**      | DCL        | Controls who can access or change the data                           | (covered later)                              |

---

### A Quick Note About Different SQL Systems

- SQL has been an **ANSI standard** since 1986.
- Different DBMS (e.g., MySQL, PostgreSQL, SQL Server, **SQLite**) have their **own version** of SQL.
- Code written for one system might need **small changes** to run on another.
- The **core skills** you learn (like `SELECT`, `CREATE`) are **similar** across systems, so learning one helps you use others.

---

### What This Course Uses

This course uses **SQLite** — a popular, lightweight Relational Database Management System (RDBMS). You can also use the course **glossary** to look up all the SQL commands taught here.

---

## Relational Databases

You can get information from a relational database with just one line of code. For example:

```sql
SELECT * FROM celebs;
```

We’ll see what this code means later. For now, focus on **what relational databases are** and **how they are organized**.

---

### What is a Relational Database?

A **relational database** organizes information into **one or more tables**. In the example above, the database has one table.

---

### Key Parts of a Table

| Term       | Meaning                                                                                        | Example                                            |
| ---------- | ---------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| **Table**  | A collection of data organized into **rows** and **columns**. Sometimes called a **relation**. | The table might be named `celebs`.                 |
| **Column** | A set of data values of **one type**. Each column has a name and a data type.                  | `id`, `name`, `age` are columns.                   |
| **Row**    | **One record** in the table. Each row has a value for every column.                            | First row: id = 1, name = Justin Bieber, age = 29. |

---

### Data Types

Every value stored in a relational database has a **data type**. Some of the most common types are:

| Data Type   | Description                             | Example                  |
| ----------- | --------------------------------------- | ------------------------ |
| **INTEGER** | A positive or negative **whole number** | 1, -5, 100               |
| **TEXT**    | A **text string**                       | "Hello", "Justin Bieber" |
| **DATE**    | A date in the form **YYYY-MM-DD**       | 2024-01-15               |
| **REAL**    | A **decimal** number                    | 3.14, -0.5               |

---

## Statements

A **statement** is text that the database recognizes as a **valid command**. Statements **always end with a semicolon** `;`.

Example of a SQL statement that creates a table:

```sql
CREATE TABLE table_name (
   column_1 data_type,
   column_2 data_type,
   column_3 data_type
);
```

---

### Parts of a Statement

| Part           | What it is                                                                                                                          | In the example above                                           |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| **Clause**     | A keyword that does a specific job. By convention, clauses are written in **capital letters**. (Also called **commands**.)          | `CREATE TABLE`                                                 |
| **Table name** | The name of the table the command applies to.                                                                                       | `table_name`                                                   |
| **Parameter**  | Extra information given to the clause: often a list of **columns** and their **data types**. It is written inside parentheses `()`. | `(column_1 data_type, column_2 data_type, column_3 data_type)` |

---

### How to Write Statements

- The **number of lines** does not matter. A statement can be:
  - All on **one line**, or
  - Split across **multiple lines** to make it easier to read.
- As you practice, you will get used to the **structure** of common SQL statements.

---

## Create

**CREATE** statements let you **create a new table** in the database. Use them whenever you want to make a new table from scratch.

**Syntax:**

```sql
CREATE TABLE Table_Name (
    column_1 data_type,
    column_2 data_type,
    column_3 data_type
);
```

**Example:** creating a table named `celebs`:

```sql
CREATE TABLE celebs (
   id INTEGER,
   name TEXT,
   age INTEGER
);
```

---

### What Each Part Does

| Step | Part                                     | Meaning                                                             |
| ---- | ---------------------------------------- | ------------------------------------------------------------------- |
| 1    | **CREATE TABLE**                         | A clause that tells SQL you want to **create a new table**.         |
| 2    | **celebs**                               | The **name** of the table.                                          |
| 3    | **(id INTEGER, name TEXT, age INTEGER)** | The **columns** (attributes) in the table and their **data types**: |

---

### Columns in the `celebs` Table

| Column   | Data Type | What it stores                       |
| -------- | --------- | ------------------------------------ |
| **id**   | INTEGER   | Whole numbers (e.g., 1, 2, 3)        |
| **name** | TEXT      | Text strings (e.g., "Justin Bieber") |
| **age**  | INTEGER   | Whole numbers (e.g., 29)             |

---

## Insert

The **INSERT** statement **adds a new row** (or rows) into a table. Use it when you want to add new records.

**Syntax:**

```sql
INSERT INTO Table_Name (
    column_1,
    column_2,
    column_3
)
VALUES (
    value_1,
    value_2,
    value_3
);
```

**Example:** adding a row for Justin Bieber into the `celebs` table:

```sql
INSERT INTO celebs (id, name, age)
VALUES (1, 'Justin Bieber', 29);
```

---

### What Each Part Does

| Part                         | Meaning                                                                |
| ---------------------------- | ---------------------------------------------------------------------- |
| **INSERT INTO**              | A clause that **adds** the row(s) you specify.                         |
| **celebs**                   | The **table** you are adding the row to.                               |
| **(id, name, age)**          | The **columns** that will get the new data.                            |
| **VALUES**                   | A clause that introduces the **data** you are inserting.               |
| **(1, 'Justin Bieber', 29)** | The **values** for each column, in the same order as the column names. |

---

### How the Values Match the Columns

| Value               | Column | What goes where                  |
| ------------------- | ------ | -------------------------------- |
| **1**               | id     | Integer → `id` column            |
| **'Justin Bieber'** | name   | Text (in quotes) → `name` column |
| **29**              | age    | Integer → `age` column           |

The order of values must match the order of columns: first value goes to first column, second to second, and so on.

---

## Select

**SELECT** statements are used to **get (fetch) data** from a database.

**Syntax:**

```sql
SELECT column_name FROM Table_Name;
-- or
SELECT * FROM Table_Name;
```

**Example:** get all data from the `name` column in the `celebs` table:

```sql
SELECT name FROM celebs;
```

---

### What Each Part Does

| Step | Part            | Meaning                                                                                            |
| ---- | --------------- | -------------------------------------------------------------------------------------------------- |
| 1    | **SELECT**      | A clause that says this is a **query**. You use `SELECT` every time you ask the database for data. |
| 2    | **name**        | The **column** you want to get data from.                                                          |
| 3    | **FROM celebs** | The **table** you want to get data from. Here, data comes from `celebs`.                           |

---

### Getting All Columns with `*`

You can get data from **every column** in a table in one go:

```sql
SELECT * FROM celebs;
```

- **`*`** is a **wildcard**. It means "every column."
- You don’t have to list each column name — `*` selects all of them.
- In this example, the result includes every column in the `celebs` table.

---

### Result Set

**SELECT** statements always return a **new table** called the **result set**. That’s the table of rows and columns the database gives you back from your query.

---

## Alter

The **ALTER TABLE** statement **adds a new column** to an existing table. Use it when you want to add more columns to a table.

**Syntax:**

```sql
ALTER TABLE Table_Name
ADD COLUMN column_name data_type;
```

**Example:** adding a column named `twitter_handle` to the `celebs` table:

```sql
ALTER TABLE celebs
ADD COLUMN twitter_handle TEXT;
```

---

### What Each Part Does

| Step | Part                    | Meaning                                                                    |
| ---- | ----------------------- | -------------------------------------------------------------------------- |
| 1    | **ALTER TABLE**         | A clause that lets you **change** the table (e.g., add a column).          |
| 2    | **celebs**              | The **name** of the table you are changing.                                |
| 3    | **ADD COLUMN**          | A clause that **adds a new column** to the table.                          |
| 4    | **twitter_handle TEXT** | The **new column**: `twitter_handle` is its name, `TEXT` is its data type. |

---

### About NULL

- **NULL** is a special value in SQL. It means **missing** or **unknown** data.
- When you add a new column to a table that already has rows, those **existing rows** get **NULL** (∅) in the new column until you fill in values.
- So after adding `twitter_handle`, every existing row has NULL in that column until you update them.

---

## Update

The **UPDATE** statement **changes existing row(s)** in a table. Use it when you want to edit records that are already there.

**Syntax:**

```sql
UPDATE Table_Name
SET column_name = value
WHERE condition;
```

**Example:** set the `twitter_handle` to `@taylorswift13` for the row where `id` is 4:

```sql
UPDATE celebs
SET twitter_handle = '@taylorswift13'
WHERE id = 4;
```

---

### What Each Part Does

| Step | Part                                  | Meaning                                                                                       |
| ---- | ------------------------------------- | --------------------------------------------------------------------------------------------- |
| 1    | **UPDATE**                            | A clause that **edits** row(s) in the table.                                                  |
| 2    | **celebs**                            | The **name** of the table you are editing.                                                    |
| 3    | **SET**                               | A clause that says **which column** to change and **what value** to put in it.                |
| 4    | **twitter_handle = '@taylorswift13'** | The column to update (`twitter_handle`) and its **new value** (`@taylorswift13`).             |
| 5    | **WHERE id = 4**                      | Which **row(s)** to update. Here: only the row where `id` is 4 gets the new `twitter_handle`. |

---

**Important:** Always use **WHERE** to say which row(s) to update. If you leave out WHERE, the UPDATE will change **every row** in the table.

---

## Delete

The **DELETE FROM** statement **removes one or more rows** from a table. Use it when you want to delete existing records.

**Syntax:**

```sql
DELETE FROM Table_Name
WHERE condition;
```

**Example:** delete all rows in the `celebs` table where `twitter_handle` is missing (NULL):

```sql
DELETE FROM celebs
WHERE twitter_handle IS NULL;
```

---

### What Each Part Does

| Part                       | Meaning                                                                                       |
| -------------------------- | --------------------------------------------------------------------------------------------- |
| **DELETE FROM**            | A clause that **deletes** row(s) from a table.                                                |
| **celebs**                 | The **name** of the table you are deleting rows from.                                         |
| **WHERE**                  | A clause that says **which rows** to delete. Without it, you would delete every row.          |
| **twitter_handle IS NULL** | The **condition**: only delete rows where the `twitter_handle` column has no value (is NULL). |

---

### About IS NULL

- **IS NULL** is a condition that checks if a value is **missing** (NULL).
- It returns **true** when the value is NULL, and **false** when there is a value.
- Use it when you want to find or delete rows where a column is empty.

---

**Important:** Always use **WHERE** to say which row(s) to delete. If you leave out WHERE, the DELETE will remove **every row** in the table.

---

## Constraints

**Constraints** are **rules** you put on a column. They come **after** the data type and control how the column can be used. The database can **reject** data that breaks these rules.

**Syntax:**

```sql
CREATE TABLE Table_Name (
    column_1 data_type PRIMARY KEY,
    column_2 data_type UNIQUE,
    column_3 data_type NOT NULL,
    column_4 data_type DEFAULT 'value'
);
```

**Example:** creating a table with constraints on each column:

```sql
CREATE TABLE celebs (
   id INTEGER PRIMARY KEY,
   name TEXT UNIQUE,
   date_of_birth TEXT NOT NULL,
   date_of_death TEXT DEFAULT 'Not Applicable'
);
```

---

### Common Constraints

| Constraint      | What it does                                                                       | What happens if the rule is broken                                                            |
| --------------- | ---------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| **PRIMARY KEY** | The column **uniquely identifies** each row. No two rows can have the same value.  | Inserting a duplicate value causes an error; the row is **not** inserted.                     |
| **UNIQUE**      | Every row must have a **different** value in this column.                          | Like PRIMARY KEY, but a table can have **more than one** UNIQUE column.                       |
| **NOT NULL**    | The column **must** have a value. It cannot be left empty (NULL).                  | Inserting a row without a value for this column causes an error; the row is **not** inserted. |
| **DEFAULT**     | If you don’t provide a value when inserting a row, this **default value** is used. | You give the default in the definition (e.g. `DEFAULT 'Not Applicable'`).                     |

---

### Quick Reference

- **PRIMARY KEY** — One per table. Unique ID for each row.
- **UNIQUE** — All values in the column must be different. You can have many UNIQUE columns.
- **NOT NULL** — Column cannot be empty.
- **DEFAULT** — Value used when you don’t specify one on insert.

---

## Review

**Manipulation** is about changing and querying data in a relational database. Here’s a quick recap of what you learned:

| Topic                    | Key idea                                                                           |
| ------------------------ | ---------------------------------------------------------------------------------- |
| **Introduction to SQL**  | SQL is the language for talking to databases; it uses declarative statements.      |
| **Relational Databases** | Data lives in tables (rows and columns) with types like INTEGER, TEXT, DATE, REAL. |
| **Statements**           | Commands end with `;`; they have clauses, table names, and parameters.             |
| **Create**               | `CREATE TABLE` defines a new table and its columns.                                |
| **Insert**               | `INSERT INTO ... VALUES` adds new rows.                                            |
| **Select**               | `SELECT` gets data; use `*` for all columns.                                       |
| **Alter**                | `ALTER TABLE ... ADD COLUMN` adds a column to an existing table.                   |
| **Update**               | `UPDATE ... SET ... WHERE` changes existing rows (always use WHERE).               |
| **Delete**               | `DELETE FROM ... WHERE` removes rows (always use WHERE).                           |
| **Constraints**          | PRIMARY KEY, UNIQUE, NOT NULL, and DEFAULT enforce rules on columns.               |

---

# Queries

---

## Introduction

In this lesson you will learn different **SQL commands** to **query a single table** in a database.

---

### What is querying?

One of the main goals of SQL is to **get information** that is stored in a database. This is called **querying**. When you query, you:

- **Ask questions** of the database
- Get back a **result set** with rows and columns that answer your question

Queries are how you “talk” to the database and get the data you need.

---

### What we’ll use in this lesson

We will query a database that has **one table** named **movies**. The commands you learn will help you ask questions about that table and see the results.

---

**Fun fact:** IBM first developed SQL in the 1970s as **SEQUEL** (Structured English QUEry Language) to query databases.

---

## Select

You already know that **SELECT** starts every query that gets data from a database, and that **`*`** means “all columns.” Sometimes you only want **specific columns**. You can list those columns by name, separated by commas.

**Syntax:**

```sql
SELECT column1, column2
FROM table_name;
```

**Example:** getting only two columns from a table (e.g. `name` and `genre` from `movies`):

```sql
SELECT name, genre
FROM movies;
```

Here, **FROM** is on a new line to make the query easier to read. In SQL, **line breaks do not change the meaning** of the query — you could write the same query on one line and it would run the same way.

---

## As

**AS** is a keyword that lets you **rename** a column (or table) in your **result**. The new name is called an **alias**. You can choose any alias you want; in SQLite, put it inside **single quotes**.

**Syntax:**

```sql
SELECT column_name AS 'Alias_Name'
FROM table_name;
```

**Example:** showing the `name` column as "Titles" in the result:

```sql
SELECT name AS 'Titles'
FROM movies;
```

Here we gave the `name` column the alias **Titles**. In the result set, the column header will show "Titles" instead of "name".

---

### Things to remember

- **Best practice:** Put aliases in single quotes (e.g. `'Titles'`). It’s not always required in SQLite, but it’s clearer and avoids issues with spaces or special characters.
- **Other databases:** In SQLite we use single quotes for aliases. In other systems (e.g. PostgreSQL), rules can differ — sometimes no quotes or double quotes are used.
- **Only in the result:** Using AS does **not** change the real column name in the table. The alias only appears in the **result set** of your query.

---

## Distinct

When you look at a column, you often want to know which **different** values it has, without seeing the same value repeated. **DISTINCT** returns only **unique** values — it removes duplicates from the result.

**Syntax:**

```sql
SELECT DISTINCT column_name
FROM table_name;
```

**Example (without DISTINCT):** `SELECT tools FROM inventory;` might return:

| tools  |
| ------ |
| Hammer |
| Nails  |
| Nails  |
| Nails  |

**Example (with DISTINCT):** `SELECT DISTINCT tools FROM inventory;` returns:

| tools  |
| ------ |
| Hammer |
| Nails  |

Each value appears only once. DISTINCT works on the column(s) you list — it filters out duplicate rows in the result.

Filtering like this is very useful in SQL. For example, using **DISTINCT** on the **genre** column in the **movies** table makes it easy to see all the different genres instead of scrolling through every row.

---

## Where

The **WHERE** clause **narrows down** your results. It keeps only the rows that meet a **condition** you specify, so you get just the information you want.

**Syntax:**

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

**Example:** only movies with an IMDb rating greater than 8:

```sql
SELECT *
FROM movies
WHERE imdb_rating > 8;
```

---

### How it works

- **WHERE** filters the result set: only rows where the condition is **true** are returned.
- In the example, the condition is **imdb_rating > 8**. So only rows with a value **greater than 8** in the `imdb_rating` column are included.
- The **>** symbol is an **operator**. Operators build conditions that are either true or false for each row.

---

### Comparison operators

Use these with **WHERE** to compare values:

| Operator | Meaning                  |
| -------- | ------------------------ |
| **=**    | equal to                 |
| **!=**   | not equal to             |
| **>**    | greater than             |
| **<**    | less than                |
| **>=**   | greater than or equal to |
| **<=**   | less than or equal to    |

You’ll see more special operators in the next exercises.

---

## Like I

**LIKE** is an operator you use with **WHERE** when you want to match a **pattern** in a column instead of an exact value. It’s useful when values are similar but not identical (e.g. "Se7en" and "Seven").

**Syntax:**

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column_name LIKE 'pattern';
```

**Example:** find all movies whose name starts with "Se", has **one character** in the middle, then "en":

```sql
SELECT *
FROM movies
WHERE name LIKE 'Se_en';
```

This returns both **Seven** and **Se7en** because both match the pattern.

---

### How it works

- **LIKE** is used with **WHERE** to search for a **pattern** in a column.
- **name LIKE 'Se_en'** is the condition: it checks the `name` column against that pattern.
- **`_` (underscore)** is a **wildcard**. It stands for **exactly one** character (any letter, digit, or symbol). So `Se_en` matches "Seven" (one "v"), "Se7en" (one "7"), or any name that is Se + one character + en.

---

## Like II

The **`%` (percent sign)** is another **wildcard** you use with **LIKE**. It matches **zero or more** characters (any length). So you can match the start of a string, the end, or a part in the middle.

**Syntax:**

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column_name LIKE 'pattern_with_%';
```

**Example 1:** movies whose name **starts with** the letter "A":

```sql
SELECT *
FROM movies
WHERE name LIKE 'A%';
```

**Example 2:** movies whose name **contains** "man" anywhere (e.g. "Batman", "Man of Steel"):

```sql
SELECT *
FROM movies
WHERE name LIKE '%man%';
```

---

### How `%` works

| Pattern   | Matches                                    |
| --------- | ------------------------------------------ |
| **A%**    | Any value that **starts with** "A"         |
| **%a**    | Any value that **ends with** "a"           |
| **%man%** | Any value that **contains** "man" anywhere |

- **%** = zero or more characters. So `A%` can be "A", "Avengers", "Avatar", etc.
- **LIKE** is **not case sensitive** in SQLite. So "Batman" and "Man of Steel" both match `%man%`.

---

## Is Null

Real data often has **missing** values. In SQL, missing or unknown values are called **NULL**. You can’t test for NULL with **=** or **!=**; you must use **IS NULL** or **IS NOT NULL**.

**Syntax:**

```sql
-- Rows where the column is missing (NULL)
SELECT column1, column2, ...
FROM table_name
WHERE column_name IS NULL;

-- Rows where the column has a value (not NULL)
SELECT column1, column2, ...
FROM table_name
WHERE column_name IS NOT NULL;
```

**Example:** only movies that **have** an IMDb rating (no missing rating):

```sql
SELECT name
FROM movies
WHERE imdb_rating IS NOT NULL;
```

---

### Things to remember

- **NULL** = missing or unknown value. It is not the same as zero or an empty string.
- Do **not** use `= NULL` or `!= NULL`. They don’t work for NULL. Use **IS NULL** or **IS NOT NULL** instead.
- **IS NULL** — keeps rows where the column has no value.
- **IS NOT NULL** — keeps rows where the column has a value (filters out missing ones).

---

## Between

The **BETWEEN** operator is used in a **WHERE** clause to filter rows **within a range**. You give two values (numbers, text, or dates), and BETWEEN includes everything **from the first value up to and including the second**.

**Syntax:**

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```

**Example 1:** movies released from **1990 through 1999** (both years included):

```sql
SELECT *
FROM movies
WHERE year BETWEEN 1990 AND 1999;
```

**Example 2:** movies whose name is **alphabetically from "A" up to (but not past) "J"**:

```sql
SELECT *
FROM movies
WHERE name BETWEEN 'A' AND 'J';
```

So you get names that start with A, B, C, … up to names that are considered "up to J". Names starting with "J" or later (like "Jaws") are handled as in the note below.

---

### How BETWEEN works with text

When you use BETWEEN with **text**, SQL compares values **alphabetically** (like A, B, C …).

**Example:** `WHERE name BETWEEN 'A' AND 'J'`

| Movie name | Included? | Why                                                                                      |
| ---------- | --------- | ---------------------------------------------------------------------------------------- |
| Avatar     | Yes       | Starts with "A"                                                                          |
| Batman     | Yes       | Starts with "B"                                                                          |
| J          | Yes       | Exactly "J" — the second value is included                                               |
| Jaws       | No        | "Jaws" comes after "J" in alphabetical order (because "Jaws" has more letters after "J") |
| Superman   | No        | Starts with "S", which is after "J"                                                      |

**Takeaway:** BETWEEN goes **up to and including** the second value. So "J" is in the range, but "Jaws" is not. If you want all names starting with "J", use **LIKE 'J%'** instead.

---

## And

You can combine **more than one condition** in a **WHERE** clause using **AND**. That makes your result set more specific: a row is returned only when **every** condition is true.

**Syntax:**

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1
   AND condition2;
```

**Example:** only **90’s romance** movies (released 1990–1999 **and** genre is romance):

```sql
SELECT *
FROM movies
WHERE year BETWEEN 1990 AND 1999
   AND genre = 'romance';
```

- **1st condition:** `year BETWEEN 1990 AND 1999` — movie is from the 1990s.
- **2nd condition:** `genre = 'romance'` — movie is a romance.
- **AND** — both must be true. So we get only 90’s romance movies.

**Rule:** With **AND**, **both** conditions must be true for the row to be included. If one condition fails, the row is not returned.

![AND Venn diagram: only the overlapping area (both conditions true) is included.](AND.png)

---

## Or

Like **AND**, the **OR** operator combines multiple conditions in **WHERE**. The difference is:

- **AND** — a row is included only if **all** conditions are true.
- **OR** — a row is included if **any** condition is true.

**Syntax:**

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1
   OR condition2;
```

**Example:** movies that are **either** after 2014 **or** action (or both):

```sql
SELECT *
FROM movies
WHERE year > 2014
   OR genre = 'action';
```

- **1st condition:** `year > 2014` — movie is from 2015 or later.
- **2nd condition:** `genre = 'action'` — movie is an action film.
- **OR** — if **either** condition is true, the row is included. So you get new movies, action movies, and movies that are both.

**Rule:** With **OR**, a row is added to the result if **any** of the conditions are true.

![OR Venn diagram: the full area of both circles is included — a row is included if condition 1 OR condition 2 (or both) is true.](OR.png)

---

## Order By

**ORDER BY** sorts the rows in your result set by a column — alphabetically or numerically. That makes the data easier to read and analyze.

**Syntax:**
```sql
SELECT column1, column2, ... 
FROM table_name 
WHERE condition   -- optional
ORDER BY column_name ASC;   -- or DESC
```

**Example 1:** sort all movies by **name** (A to Z):

```sql
SELECT *
FROM movies
ORDER BY name;
```

- **ORDER BY** — clause that says “sort the result by this column.”
- **name** — the column used for sorting. Rows are ordered A–Z (ascending) by default.

**Example 2:** well-rated movies (rating > 8), sorted by **year** from **newest to oldest**:

```sql
SELECT *
FROM movies
WHERE imdb_rating > 8
ORDER BY year DESC;
```

- **DESC** — sort **descending** (high to low, or Z–A). So years go from highest to lowest.
- **ASC** — sort **ascending** (low to high, or A–Z). This is the **default** if you don’t write ASC or DESC.

---

### Things to remember

- **ORDER BY** always comes **after WHERE** (if you use WHERE).
- The column you **ORDER BY** does **not** have to be in the **SELECT** list. You can sort by a column you don’t display.

---

## Limit

Real tables often have huge numbers of rows. **LIMIT** lets you **cap** how many rows the query returns. That keeps the result smaller, easier to read, and often makes the query run faster.

**Syntax:**
```sql
SELECT column1, column2, ... 
FROM table_name 
WHERE condition   -- optional
ORDER BY column_name   -- optional
LIMIT number_of_rows;
```

**Example:** return only the **first 10** movies:

```sql
SELECT *
FROM movies
LIMIT 10;
```

- **LIMIT** — clause that sets the **maximum number of rows** in the result. Here, no more than 10 rows are returned.
- Useful when you only need a **sample** of rows (e.g. a few examples) instead of the full table.

---

### Things to remember

- **LIMIT** always goes at the **very end** of the query (after WHERE and ORDER BY if you use them).
- **LIMIT** is **not supported** in every SQL database. It works in SQLite (and MySQL, PostgreSQL); other systems may use different syntax (e.g. **TOP** in SQL Server).

---

## Case

**CASE** is SQL’s way of doing **if-then** logic. It lets you show **different values** in the result depending on conditions — usually inside a **SELECT**. For example: “if rating > 8 then show ‘Fantastic’, else if rating > 6 then show ‘Poorly Received’, else show ‘Avoid at All Costs’.”

**Syntax:**
```sql
SELECT column1,
 CASE
  WHEN condition1 THEN 'value1'
  WHEN condition2 THEN 'value2'
  ELSE 'default_value'
 END
FROM table_name;
```

**Example:** turn IMDb ratings into three simple labels:

```sql
SELECT name,
 CASE
  WHEN imdb_rating > 8 THEN 'Fantastic'
  WHEN imdb_rating > 6 THEN 'Poorly Received'
  ELSE 'Avoid at All Costs'
 END
FROM movies;
```

- **WHEN** — checks a condition (e.g. `imdb_rating > 8`).
- **THEN** — value to use if that condition is true.
- **ELSE** — value to use if **none** of the WHEN conditions are true.
- **END** — required; it closes the CASE.

**Example (with a short column name):** give the CASE result a clearer name like **Review** using **AS**:

```sql
SELECT name,
 CASE
  WHEN imdb_rating > 8 THEN 'Fantastic'
  WHEN imdb_rating > 6 THEN 'Poorly Received'
  ELSE 'Avoid at All Costs'
 END AS 'Review'
FROM movies;
```

Without **AS 'Review'**, the column name in the result can be long and hard to read. Using **AS** renames it to something short like **Review**.

_Happy learning!_
