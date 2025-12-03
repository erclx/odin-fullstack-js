# 🗄️ Databases

### Introduction
The bottom layer of any web application is the database. It handles remembering user data (like passwords). Databases can range from simple Excel-like structures to complex systems like Facebook's.

**SQL (Structured Query Language)** is used to query databases. It has a short syntax with only a handful of verbs, but requires visualizing what the data operations are doing.

---
### 📝 Lesson Overview
* What a database is.
* What relational databases are.
* In what way relational databases are different from XML.
* What SQL is and what it is used for.
* How to get all records from a table in SQL.
* How to insert a record in SQL.

---
### 🔗 Relational Databases
A **relational database** organizes data into tables which can be linked—or related—based on data common to each. This structure allows you to retrieve an entirely new table from data in one or more tables with a single query.



[Image of relational database model diagram]


* **Tables:** Data is stored in rows and columns.
* **Primary Key:** A unique identifier for a specific record (row) in a table.

---
### 🗣️ SQL (Structured Query Language)
SQL is the standard language for relational database management systems. It is used to communicate with a database.

**Common Commands:**

* **SELECT:** Retrieves data from a database.
    * *Example (Get all records):* `SELECT * FROM table_name;`
* **INSERT:** Adds new data into a database.
    * *Example:* `INSERT INTO table_name (column1, column2) VALUES (value1, value2);`
* **UPDATE:** Modifies data in a database.
* **DELETE:** Removes data from a database.

---
### 📚 Assignment
1.  **Introduction to SQL:** Check out how SQL organizes and manages data. (Only the first page is required).
2.  **Video Introduction:** Watch a short video on relational databases to understand the utility and terminology.
3.  **Khan Academy Tutorial:** Go through the SQL tutorial to practice creating and manipulating databases.

---
### 🤔 Knowledge Check
* **What is a database?** An organized collection of data, generally stored and accessed electronically from a computer system.
* **What are relational databases?** Databases that organize data into tables with predefined relationships between them.
* **What is a Primary Key?** A unique identifier for a record in a table.
* **What is SQL?** A standard language for storing, manipulating, and retrieving data in databases.
* **How do you get all the records from a table in SQL?** `SELECT * FROM table_name;`
* **How do you insert a record in SQL?** `INSERT INTO table_name (column1, column2) VALUES (value1, value2);`

---
### 🔗 Additional Resources
* **Article:** "What is a Relational Database?" from HowStuffWorks.
* **Wiki:** A brief Simple Wiki article describing relational databases.
* **Lecture:** David J. Malan’s SQL lecture from Harvard’s CS50x.
* **Comparison:** An article explaining the difference between SQL and NoSQL databases.