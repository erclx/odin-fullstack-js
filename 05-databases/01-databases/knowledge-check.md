### Knowledge Check Answers 🎯

-----

**Question: What is a database?**

**Answer:** A database is an organized collection of structured information (data), typically stored electronically in a computer system.

**Why:** It allows for the efficient storage, retrieval, modification, and management of data (like user accounts, products, or posts) for web applications.

**Remember:** It is the **digital filing cabinet** 🗄️ for your application.

-----

**Question: What are relational databases?**

**Answer:** Relational databases (RDBMS) organize data into **tables** with rows and columns. These tables can be linked (related) to each other using unique keys.

**Why:** This structure reduces data duplication and ensures data consistency. For example, a `Users` table can be related to a `Posts` table by a User ID, so you know exactly who wrote which post without typing the user's name every time.

-----

**Question: What is a Primary Key?**

**Answer:** A Primary Key is a specific column in a table that uniquely identifies each row (record).

**Why:** It ensures that every record is distinct and can be easily referenced by other tables. No two rows can ever have the same Primary Key.

**Example:** A standard `id` column (e.g., `user_id: 1`) is usually the primary key.

-----

**Question: What is SQL?**

**Answer:** SQL (Structured Query Language) is the standard programming language used to communicate with relational databases.

**Why:** It provides a set of readable commands (like "verbs") that allow you to create, read, update, and delete data within the database.

**Remember:** SQL is the **language** you speak to the **database**.

-----

**Question: How do you get all the records from a table in SQL?**

**Answer:** You use the `SELECT` statement combined with the asterisk (`*`) wildcard.

**Why:** The asterisk (`*`) tells the database to return **all columns** for every row in the specified table.

**Example:**

```sql
SELECT * FROM users;
```

-----

**Question: How do you insert a record in SQL?**

**Answer:** You use the `INSERT INTO` statement, specifying the table name, the columns you want to fill, and the `VALUES` for those columns.

**Why:** This command creates a new row in the table with the specific data you provide.

**Example:**

```sql
INSERT INTO users (name, age) VALUES ('Odin', 100);
```