# 💾 Databases and SQL

### Introduction
Data is the core of any good web app. While ORM tools (like Active Record or Prisma) handle database interactions behind the scenes, knowing SQL allows you to ask more complicated questions of your data and understand what's really happening.

SQL is about asking questions of your database. It has a small vocabulary of a dozen or so words that you'll consistently use.

---
### 📝 Lesson Overview
* What a Primary Key and Foreign Key are.
* What a Schema is.
* How to use statements like `SELECT`, `CREATE TABLE`, `UPDATE`, `DELETE`.
* How to use clauses like `WHERE`, `LIKE`, `DISTINCT`.
* How to use functions like `AVG`, `COUNT`, `SUM`.
* What Indexes are.
* The difference between `WHERE` and `HAVING`.

---
### ⚡ The World's Fastest Explanation of SQL
SQL is the language for relational databases.
* **Tables:** Spreadsheets storing data records (rows).
* **Primary Key:** A unique ID column that every table has.
* **Foreign Key:** A column that contains the ID of another table, linking them together (e.g., a `user_id` column in a `posts` table).

---
### 🛠️ Setting Stuff Up
* **Schema:** A special file storing the structure of your database (tables, columns, types).
* **`CREATE TABLE`**: Sets up a new table.
* **`CREATE INDEX`**: Makes searching faster by sorting a column ahead of time. Use this for columns you search often (like username).

---
### 🏗️ Mucking Around with Data (CRUD)
Every command has an **action** (statement), a **table**, and **conditions** (clauses).

* **Create (`INSERT INTO`):** Adds new rows.
    * `INSERT INTO users (name, email) VALUES ('foobar', 'foo@bar.com');`
* **Read (`SELECT`):** The most common action.
    * `SELECT * FROM users WHERE created_at < '2013-12-11';` (* means all columns).
    * `SELECT DISTINCT users.name FROM users;` (Returns only unique names).
* **Update (`UPDATE`):** Changes existing data. **Always use a `WHERE` clause!**
    * `UPDATE users SET name='barfoo' WHERE id=1;`
* **Destroy (`DELETE`):** Removes rows. **Always use a `WHERE` clause!**
    * `DELETE FROM users WHERE id = 1;`

---
### 🤝 Mashing Tables Together (JOINs)
To get data from multiple related tables (e.g., all posts by a user), use `JOIN`.

* **`INNER JOIN` (or just `JOIN`):** Keeps only rows that match in **both** tables. (95% of use cases).
* **`LEFT OUTER JOIN`:** Keeps all rows from the left table, adding matching data from the right (or NULL if no match).
* **`RIGHT OUTER JOIN`:** The opposite of LEFT.
* **`FULL OUTER JOIN`:** Keeps all rows from both tables, using NULLs for mismatches.

---
### 📊 Aggregate Functions
SQL can calculate data for you.
* **Functions:** `COUNT`, `SUM`, `MIN`, `MAX`, `AVG`.
    * `SELECT MAX(users.age) FROM users;`
* **`GROUP BY`:** Groups results by a specific column (e.g., count of posts *per user*).
    * `SELECT users.name, COUNT(posts.id) FROM users JOIN posts ON users.id = posts.user_id GROUP BY users.id, users.name;`
* **`HAVING`:** Acts like `WHERE`, but for aggregated data (since `WHERE` doesn't work on aggregates).
    * `... GROUP BY users.id HAVING COUNT(posts.id) >= 10;`

---
### 🚀 SQL is Faster Than Code!
Always try to filter and process data in SQL rather than pulling everything into your app and looping through it. Databases have query optimizers built for speed.
* **Example:** Use `SELECT DISTINCT name ...` instead of fetching all names and removing duplicates in JavaScript/Ruby.

---
### 📚 Assignment
* **SQL Teaching:** Go through this interactive tutorial.
* **SQL Bolt:** Go through this more in-depth interactive tutorial.

---
### 🤔 Knowledge Check
* What is the difference between a foreign key and a primary key?
* Where is the setup information for your database stored?
* Which SQL statement is associated with “Read”? (`SELECT`)
* Which JOIN statement keeps only matching rows? (`INNER JOIN`)
* In which situation would you use the `HAVING` clause? (Filtering aggregated data).