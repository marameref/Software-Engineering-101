
# 🗄️ WEEK 10 — DATABASES, SQL & PYTHON INTEGRATION

<div align="center">

![Database](https://img.shields.io/badge/Database-SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)
![Language](https://img.shields.io/badge/Language-SQL-2563EB?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-Database_Integration-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Level](https://img.shields.io/badge/Level-Beginner-16A085?style=for-the-badge)

**Practical Software Engineering Foundation Programme**

**Training Provider:** Opsfuxion Technologies Limited

*Orchestrate Intelligence, Deliver with Precision.*

</div>

---

## 📋 Programme Information

| Item | Details |
|---|---|
| Module | Week 10 — Databases, SQL & Python Integration |
| Duration | 1 Week |
| Sessions | 3 instructor-led sessions |
| Session Duration | 2 Hours |
| Total Contact Hours | 6 Hours |
| Level | Beginner |
| Prerequisites | Weeks 4–9 |
| Primary Technologies | Python 3, SQLite, SQL |
| Weekly Project | Student Records Database |
| Learning Approach | Database design, SQL practice, Python integration and project development |

---

# 📖 Week Overview

In previous weeks, the student developed Python applications that stored information in lists, dictionaries and objects.

However, these applications generally lose their data when the program terminates.

Real-world applications require a way to store information permanently.

For example:

- Schools maintain student records.
- Hospitals store patient information.
- Banks maintain transaction records.
- Online stores maintain product information.
- Learning platforms maintain course and enrolment records.

Databases provide structured ways to store, retrieve, update and manage information.

This week introduces relational databases, Structured Query Language (SQL), SQLite and Python database integration.

The student will develop a Student Records Database that can store and retrieve student information across application sessions.

---

# 🎯 Learning Objectives

By the end of Week 10, the student should be able to:

- Explain what a database is.
- Explain why databases are important.
- Understand relational databases.
- Identify tables, rows and columns.
- Explain primary keys.
- Understand basic relationships between tables.
- Explain what SQL is.
- Create SQLite databases.
- Create database tables.
- Insert records.
- Retrieve records using `SELECT`.
- Filter records using `WHERE`.
- Sort query results using `ORDER BY`.
- Update records.
- Delete records.
- Understand CRUD operations.
- Use Python's `sqlite3` module.
- Connect Python applications to SQLite databases.
- Execute parameterised SQL queries.
- Understand basic database constraints.
- Handle common database errors.
- Build a persistent student records application.

---

# 🗓️ SESSION 1 — DATABASE FUNDAMENTALS & INTRODUCTION TO SQL

**Duration:** 2 Hours

## Session Breakdown

| Activity | Duration |
|---|---:|
| Review of Week 9 | 10 minutes |
| Introduction to Databases | 20 minutes |
| Relational Database Concepts | 25 minutes |
| Introduction to SQL | 20 minutes |
| Creating Tables and Inserting Records | 25 minutes |
| Guided Practical | 15 minutes |
| Knowledge Check | 5 minutes |
| **Total** | **120 minutes** |

---

## 1. Review of Week 9 — 10 Minutes

Review:

- Student records
- Searching
- Sorting
- Lists and dictionaries
- OOP-based student management

### Discussion

What happens to our student records when the Python program closes?

How can we preserve the information for future use?

---

## 2. Introduction to Databases — 20 Minutes

A database is an organised collection of information that can be stored, accessed and managed.

### Why Use Databases?

Databases help applications:

- Store information persistently.
- Retrieve information.
- Update records.
- Delete records.
- Organise related information.
- Maintain data integrity.

### Database vs Python List

| Python List | Database |
|---|---|
| Usually stores application data in memory | Stores records persistently |
| Simple to use | Supports structured queries |
| Useful for temporary collections | Useful for long-term records |
| Data must be saved separately | Database manages storage |

---

## 3. Relational Database Concepts — 25 Minutes

A relational database organises information into tables.

### Example: Students Table

| student_id | name | age | course |
|---|---|---|---|
| 1 | Ada | 16 | Software Engineering |
| 2 | Chidi | 17 | Computer Science |
| 3 | Uzoamaka | 16 | Software Engineering |

### Key Concepts

**Table:** Stores related records.

**Row:** Represents one record.

**Column:** Represents a particular attribute.

**Primary Key:** Uniquely identifies each record.

**Foreign Key:** References a record in another table.

### Example Relationship

A school may have:

- Students table
- Courses table
- Enrolments table

An enrolment record can reference both a student and a course.

### Discussion

Why should student IDs be unique?

---

## 4. Introduction to SQL — 20 Minutes

SQL stands for **Structured Query Language**.

It is used to work with relational databases.

### Common SQL Commands

| Command | Purpose |
|---|---|
| `CREATE TABLE` | Create a table |
| `INSERT INTO` | Add records |
| `SELECT` | Retrieve records |
| `UPDATE` | Modify records |
| `DELETE` | Remove records |
| `WHERE` | Filter records |
| `ORDER BY` | Sort results |

### CRUD Operations

CRUD represents:

- Create
- Read
- Update
- Delete

These are fundamental operations in database-driven applications.

---

## 5. Creating Tables and Inserting Records — 25 Minutes

Use SQLite through a database editor, SQLite CLI or Python.

### Create a Students Table

```sql
CREATE TABLE students (
    student_id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    age INTEGER NOT NULL,
    course TEXT NOT NULL
);
```

### Insert Records

```sql
INSERT INTO students (name, age, course)
VALUES ('Ada', 16, 'Software Engineering');
```

```sql
INSERT INTO students (name, age, course)
VALUES ('Uzoamaka', 16, 'Software Engineering');
```

### Retrieve Records

```sql
SELECT * FROM students;
```

### Discussion

What does `NOT NULL` mean?

Why do we use a primary key?

---

## 6. Guided Practical — 15 Minutes

### Exercise 1: Create a School Database

Create:

`school.db`

### Requirements

1. Create a `students` table.
2. Add at least five student records.
3. Retrieve all records.
4. Display student names.
5. Identify each student's primary key.

---

## 7. Knowledge Check — 5 Minutes

1. What is a database?
2. What is a relational database?
3. What is a table?
4. What is a primary key?
5. What does SQL stand for?
6. What does CRUD mean?

---

# 📝 SESSION 1 ASSIGNMENT

## Student Database Setup

Create a SQLite database containing a `students` table.

### Requirements

The table must contain:

- Student ID
- Full name
- Age
- Course
- Email address

### Tasks

1. Create the table.
2. Insert at least eight records.
3. Retrieve all records.
4. Retrieve only names and courses.
5. Document the SQL commands used.

### Deliverables

- SQL script
- SQLite database file
- Screenshots or text output of successful queries

---

# 🗓️ SESSION 2 — SQL QUERIES & CRUD OPERATIONS

**Duration:** 2 Hours

## Session Breakdown

| Activity | Duration |
|---|---:|
| Assignment Review | 15 minutes |
| SELECT and WHERE | 25 minutes |
| ORDER BY and Filtering | 20 minutes |
| UPDATE and DELETE | 20 minutes |
| Database Constraints | 15 minutes |
| Guided Practical | 20 minutes |
| Knowledge Check | 5 minutes |
| **Total** | **120 minutes** |

---

## 1. Assignment Review — 15 Minutes

Review:

- Database creation
- Table structure
- Primary keys
- Inserted records
- SQL syntax

---

## 2. Retrieving and Filtering Data — 25 Minutes

### Retrieve All Records

```sql
SELECT * FROM students;
```

### Retrieve Selected Columns

```sql
SELECT name, course FROM students;
```

### Filter by Course

```sql
SELECT *
FROM students
WHERE course = 'Software Engineering';
```

### Filter by Age

```sql
SELECT *
FROM students
WHERE age >= 16;
```

### Combining Conditions

```sql
SELECT *
FROM students
WHERE age >= 16
AND course = 'Software Engineering';
```

---

## 3. Sorting Query Results — 20 Minutes

### Ascending Order

```sql
SELECT *
FROM students
ORDER BY name ASC;
```

### Descending Order

```sql
SELECT *
FROM students
ORDER BY age DESC;
```

### Discussion

How is SQL sorting different from sorting a Python list?

---

## 4. Updating and Deleting Records — 20 Minutes

### UPDATE

```sql
UPDATE students
SET course = 'Computer Science'
WHERE student_id = 1;
```

### DELETE

```sql
DELETE FROM students
WHERE student_id = 2;
```

### Important Safety Rule

Always check the `WHERE` clause before executing updates or deletions.

Without a `WHERE` clause, an `UPDATE` or `DELETE` statement may affect every row in the table.

---

## 5. Introduction to Database Constraints — 15 Minutes

Constraints help maintain data integrity.

### Examples

- `PRIMARY KEY`
- `NOT NULL`
- `UNIQUE`
- `CHECK`
- `FOREIGN KEY`

### Example

```sql
CREATE TABLE results (
    result_id INTEGER PRIMARY KEY,
    student_id INTEGER NOT NULL,
    score REAL NOT NULL CHECK(score BETWEEN 0 AND 100),
    FOREIGN KEY(student_id)
        REFERENCES students(student_id)
);
```

Explain that foreign key enforcement must be enabled for each SQLite connection when relying on foreign key constraints.

---

## 6. Guided Practical — 20 Minutes

### Exercise 2: Student Records CRUD

Using the existing database:

1. Retrieve all students.
2. Find a student by ID.
3. Find students studying Software Engineering.
4. Sort students by name.
5. Update a student's course.
6. Delete a test record.
7. Verify the changes.

---

## 7. Knowledge Check — 5 Minutes

1. What does `SELECT` do?
2. What does `WHERE` do?
3. What does `ORDER BY` do?
4. What does `UPDATE` do?
5. What does `DELETE` do?
6. Why are database constraints important?

---

# 📝 SESSION 2 ASSIGNMENT

## SQL CRUD Practice

Create:

`student_queries.sql`

### Requirements

Write SQL statements to:

1. Insert three new students.
2. Retrieve all students.
3. Retrieve students older than 16.
4. Sort students alphabetically.
5. Update one student's information.
6. Delete one test student.
7. Count all student records.

### Bonus

Create a `results` table linked to the `students` table.

---

# 🗓️ SESSION 3 — PYTHON DATABASE INTEGRATION & WEEKLY PROJECT

**Duration:** 2 Hours

## Session Breakdown

| Activity | Duration |
|---|---:|
| Assignment Review | 15 minutes |
| Python SQLite Integration | 25 minutes |
| Parameterised Queries | 20 minutes |
| Guided Practical | 20 minutes |
| Weekly Project Development | 30 minutes |
| Project Review | 10 minutes |
| **Total** | **120 minutes** |

---

## 1. Assignment Review — 15 Minutes

Review:

- SQL queries
- CRUD operations
- Constraints
- Query correctness

---

## 2. Connecting Python to SQLite — 25 Minutes

Python includes the `sqlite3` module.

### Example

```python
import sqlite3

connection = sqlite3.connect("school.db")

cursor = connection.cursor()

cursor.execute("""
CREATE TABLE IF NOT EXISTS students (
    student_id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    age INTEGER NOT NULL,
    course TEXT NOT NULL
)
""")

connection.commit()
connection.close()
```

### Discussion

Explain:

- Database connection
- Cursor
- SQL execution
- Committing changes
- Closing connections

---

## 3. Parameterised Queries — 20 Minutes

When accepting user input, use SQL parameters rather than building SQL statements through string concatenation.

### Example

```python
import sqlite3

name = input("Student name: ")
age = int(input("Student age: "))
course = input("Course: ")

with sqlite3.connect("school.db") as connection:
    connection.execute(
        """
        INSERT INTO students (name, age, course)
        VALUES (?, ?, ?)
        """,
        (name, age, course)
    )

print("Student saved successfully.")
```

### Why Use Parameters?

Parameterised queries help prevent SQL injection and handle values safely.

---

## 4. Guided Practical — 20 Minutes

### Exercise 3: Python Student Registration

Create:

`student_registration.py`

### Requirements

1. Connect to SQLite.
2. Create a student table if necessary.
3. Ask for student information.
4. Insert the record.
5. Retrieve all students.
6. Display the records.

---

# 🏆 WEEK 10 PROJECT — STUDENT RECORDS DATABASE

## Project Description

Develop a Python application that stores student records persistently using SQLite.

The project should extend the Student Management System developed in Week 8.

---

## Functional Requirements

The application must:

1. Create or connect to a SQLite database.
2. Register students.
3. View student records.
4. Search for a student by ID.
5. Update student information.
6. Delete a student record.
7. Store examination scores.
8. Retrieve examination results.
9. Validate user input.
10. Exit safely.

---

## Suggested Database Tables

### Students

| Column | Data Type |
|---|---|
| student_id | INTEGER PRIMARY KEY |
| name | TEXT |
| age | INTEGER |
| course | TEXT |

### Results

| Column | Data Type |
|---|---|
| result_id | INTEGER PRIMARY KEY |
| student_id | INTEGER |
| subject | TEXT |
| score | REAL |

---

## Suggested Project Structure

```text
Week-10/
│
├── exercises/
│   ├── school_database.sql
│   └── student_registration.py
│
├── assignments/
│   ├── student_queries.sql
│   └── student_database_setup.sql
│
└── projects/
    └── student-records-database/
        ├── main.py
        ├── database.py
        ├── students.py
        ├── results.py
        ├── schema.sql
        ├── .gitignore
        └── README.md
```

---

# 🧪 Suggested Test Cases

| Test | Expected Result |
|---|---|
| Register student | Record saved |
| Restart application | Existing records remain |
| Search valid ID | Correct student returned |
| Search unknown ID | Friendly message |
| Update student | Updated information saved |
| Delete student | Record removed |
| Enter invalid score | Score rejected |
| Enter invalid age | Input rejected |
| Query empty table | No crash |
| Insert unsafe-looking text | Treated as data, not SQL |

---

# 🧠 Week 10 Knowledge Check

1. What is a database?
2. What is a relational database?
3. What is SQL?
4. What is SQLite?
5. What is a table?
6. What is a row?
7. What is a column?
8. What is a primary key?
9. What is a foreign key?
10. What does CRUD mean?
11. What does `CREATE TABLE` do?
12. What does `INSERT INTO` do?
13. What does `SELECT` do?
14. What does `WHERE` do?
15. What does `ORDER BY` do?
16. What does `UPDATE` do?
17. What does `DELETE` do?
18. What is a database constraint?
19. What does `sqlite3.connect()` do?
20. Why should SQL queries use parameters?

---

# 📊 Week 10 Assessment

| Assessment Area | Weight |
|---|---:|
| Database fundamentals | 15% |
| SQL queries | 20% |
| CRUD operations | 20% |
| Python database integration | 20% |
| Data validation and integrity | 10% |
| Code organisation | 5% |
| Weekly project completion | 10% |
| **Total** | **100%** |

---

# 📦 Week 10 Deliverables

- School Database
- Student Database Setup
- SQL CRUD Practice
- Python Student Registration
- Student Records Database Project
- Week 10 Knowledge Check
- GitHub commits and project documentation

---

# 🎓 Expected Learning Outcomes

By the end of Week 10, the student should be able to:

- Explain relational database concepts.
- Create SQLite databases.
- Write basic SQL queries.
- Perform CRUD operations.
- Connect Python to SQLite.
- Use parameterised queries.
- Store and retrieve information persistently.
- Build a beginner-level database-driven application.

---

## ⏭️ Next Module

**Week 11 — Software Engineering Practices & Capstone Planning**

The student will learn about the Software Development Life Cycle, requirements engineering, system design, testing, documentation and project planning.

---

<div align="center">

**Opsfuxion Technologies Limited**

*Orchestrate Intelligence, Deliver with Precision.*

© 2026 Opsfuxion Technologies Limited.

</div>
