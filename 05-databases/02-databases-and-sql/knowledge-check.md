### Knowledge Check Answers 🎯

-----

**Question: What is the difference between a foreign key and a primary key?**

**Answer:** A **Primary Key** is a unique ID that identifies a specific row in its own table. A **Foreign Key** is a column that points to the Primary Key of *another* table to link them together.

**Why:** This linking mechanism allows relational databases to connect data (like linking a `post` to the `user` who wrote it) without duplicating information.

**Remember:** Primary Key = **My ID**. Foreign Key = **Your ID** (that I'm holding to find you).

-----

**Question: Where is the setup information for your database stored?**

**Answer:** It is stored in a special file called the **Schema**.

**Why:** The Schema acts as a blueprint, defining the structure of your database, including what tables exist and what columns (attributes) they contain.

-----

**Question: What are the important parts of a SQL command?**

**Answer:** The three main parts are the **Statement** (the action), the **Table** (the target), and the **Clauses** (the conditions).

**Example:**

```sql
DELETE FROM users WHERE id = 1;
-- Action: DELETE
-- Table: FROM users
-- Clause: WHERE id = 1
```

-----

**Question: Which SQL statement is associated with “Read” from the CRUD acronym?**

**Answer:** The **`SELECT`** statement.

**Why:** It allows you to "select" and view specific data from a table without modifying or deleting it.

-----

**Question: Which `JOIN` statement keeps only the rows from both tables where they match up?**

**Answer:** The **`INNER JOIN`** (or just `JOIN`).

**Why:** It acts like a filter that discards any rows that don't have a corresponding match in the other table.

**Remember:** `INNER JOIN` is the **exclusive club**; you only get in if you're on both lists.

-----

**Question: How do you use an aggregate function?**

**Answer:** You include the function (like `COUNT`, `SUM`, or `MAX`) inside the `SELECT` statement.

**Why:** These functions take a list of values from a column and "aggregate" (squash) them down into a single meaningful number.

**Example:**

```sql
SELECT MAX(age) FROM users; -- Returns just one number: the highest age.
```

-----

**Question: In which situation would you use the `HAVING` clause?**

**Answer:** You use `HAVING` when you need to filter results based on an **aggregate function** (like `COUNT`).

**Why:** The standard `WHERE` clause filters individual rows *before* they are grouped. `HAVING` filters the groups *after* the math has been done.

**Example:** "Show me users who have written more than 10 posts" (`HAVING COUNT(posts.id) > 10`).

**Remember:** `WHERE` is for rows; `HAVING` is for **groups**.

-----

**Question: Why can’t I just use code to process my database data?**

**Answer:** Because SQL is significantly **faster** and more efficient at filtering and sorting data than your application code.

**Why:** Databases have "query optimizers" designed specifically for this. If you use code, you have to pull *all* the raw data out of the database and into memory first, which is slow and resource-heavy.

**Remember:** Don't buy the whole grocery store just to make a sandwich; let SQL fetch just the ingredients you need.