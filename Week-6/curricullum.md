
# 🐍 WEEK 6 — PYTHON DATA STRUCTURES & LOOPS

<div align="center">

![Python](https://img.shields.io/badge/Python-Data_Structures-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Level](https://img.shields.io/badge/Level-Beginner-16A085?style=for-the-badge)
![Duration](https://img.shields.io/badge/Duration-1_Week-7C3AED?style=for-the-badge)
![Learning](https://img.shields.io/badge/Learning-Hands_On-F59E0B?style=for-the-badge)

**Practical Software Engineering Foundation Programme**

**Training Provider:** Opsfuxion Technologies Limited

*Orchestrate Intelligence, Deliver with Precision.*

</div>

---

## 📋 Programme Information

| Item | Details |
|---|---|
| Module | Week 6 — Python Data Structures & Loops |
| Duration | 1 Week |
| Sessions | 3 instructor-led sessions |
| Session Duration | 2 Hours |
| Total Contact Hours | 6 Hours |
| Level | Beginner |
| Prerequisites | Weeks 4 and 5 |
| Primary Language | Python 3 |
| Weekly Project | Student Score Analyser |
| Learning Approach | Theory, guided labs, independent exercises and project development |

---

# 📖 Week Overview

In previous weeks, the student learned how to create variables, accept user input, perform calculations and make decisions using conditional statements.

However, real-world software often needs to manage more than one piece of information.

For example:

- A school may have hundreds of students.
- A shop may sell several products.
- A hospital may manage multiple patient records.
- A banking application may process many transactions.

Creating a separate variable for every piece of information would be difficult to manage.

Python provides **data structures** that allow programmers to organise and manage collections of information.

This week introduces four built-in Python collection types:

1. Lists
2. Tuples
3. Dictionaries
4. Sets

The student will also learn how to repeat instructions using `for` and `while` loops.

By combining data structures and loops, the student will build a program that processes multiple student scores and generates a basic performance report.

---

# 🎯 Learning Objectives

By the end of Week 6, the student should be able to:

- Explain what a data structure is.
- Explain why programs use collections.
- Create and manipulate Python lists.
- Access list elements using indexes.
- Understand positive and negative indexing.
- Use list slicing.
- Add and remove list elements.
- Understand tuples and immutability.
- Create dictionaries using key-value pairs.
- Access, add, update and remove dictionary entries.
- Understand sets and unique values.
- Explain iteration.
- Write `for` loops.
- Write `while` loops.
- Use `range()`.
- Understand `break` and `continue`.
- Avoid common infinite-loop errors.
- Iterate over lists and dictionaries.
- Calculate totals and averages from collections.
- Combine loops and conditional statements.
- Build a simple data-processing application.

---

# 🗓️ SESSION 1 — LISTS, TUPLES & COLLECTION FUNDAMENTALS

**Duration:** 2 Hours

## Session Objectives

The student will learn how to organise related information using Python lists and tuples.

### Session Breakdown

| Activity | Duration |
|---|---:|
| Review of Week 5 | 10 minutes |
| Introduction to Data Structures | 15 minutes |
| Python Lists | 30 minutes |
| List Operations and Methods | 25 minutes |
| Tuples | 15 minutes |
| Guided Practical | 20 minutes |
| Knowledge Check | 5 minutes |
| **Total** | **120 minutes** |

---

## 1. Review of Week 5 — 10 Minutes

Review:

- Variables
- Conditional statements
- Comparison operators
- Boolean logic
- Input validation
- Algorithms and pseudocode

### Discussion

Suppose we want to store the examination scores of five students.

We could write:

```python
score1 = 75
score2 = 82
score3 = 64
score4 = 91
score5 = 58
```

But what happens when we have 500 students?

Is there a better way to organise this information?

---

## 2. Introduction to Data Structures — 15 Minutes

A **data structure** is a way of organising and storing data so that a program can access and process it.

### Common Python Collection Types

| Data Structure | Description | Example |
|---|---|---|
| List | Ordered, changeable collection | `[10, 20, 30]` |
| Tuple | Ordered, unchangeable collection | `(10, 20, 30)` |
| Dictionary | Collection of key-value pairs | `{"name": "Ada"}` |
| Set | Unordered collection of unique values | `{10, 20, 30}` |

### Discussion

Why is it useful to store related information together?

---

## 3. Python Lists — 30 Minutes

A list stores multiple values in a single variable.

### Creating a List

```python
scores = [75, 82, 64, 91, 58]

print(scores)
```

### Accessing List Elements

```python
subjects = ["Mathematics", "English", "Physics"]

print(subjects[0])
print(subjects[1])
print(subjects[2])
```

Explain that Python indexing starts at zero.

### Negative Indexing

```python
print(subjects[-1])
```

This accesses the last element.

### List Slicing

```python
numbers = [10, 20, 30, 40, 50]

print(numbers[0:3])
print(numbers[2:])
print(numbers[:3])
```

### Changing List Elements

```python
subjects[1] = "Computer Science"

print(subjects)
```

### List Length

```python
print(len(subjects))
```

---

## 4. List Operations and Methods — 25 Minutes

### Adding Elements

```python
subjects.append("Biology")
```

### Inserting Elements

```python
subjects.insert(1, "Chemistry")
```

### Removing Elements

```python
subjects.remove("Biology")
```

### Removing by Index

```python
subjects.pop(0)
```

### Sorting

```python
scores = [75, 45, 90, 60]

scores.sort()

print(scores)
```

### Useful Built-in Functions

```python
scores = [75, 82, 64, 91, 58]

print(len(scores))
print(sum(scores))
print(max(scores))
print(min(scores))
```

### Practical Questions

1. How do you add an item to a list?
2. How do you remove an item?
3. How do you find the largest value?
4. What happens if you access an invalid index?

---

## 5. Introduction to Tuples — 15 Minutes

A tuple stores multiple values in a fixed sequence.

```python
coordinates = (10, 20)

print(coordinates[0])
```

Unlike lists, tuples cannot be modified after creation.

### Example

```python
student_details = ("Uzoamaka", 16, "Software Engineering")
```

### Lists vs Tuples

| List | Tuple |
|---|---|
| Uses `[]` | Uses `()` |
| Changeable | Not changeable |
| Suitable for frequently updated collections | Suitable for fixed collections |

### Discussion

When might a tuple be more appropriate than a list?

---

## 6. Guided Practical — 20 Minutes

### Exercise 1: Student Subject Manager

Create:

`student_subjects.py`

### Requirements

1. Create a list of five subjects.
2. Display the complete list.
3. Display the first subject.
4. Display the last subject.
5. Add a new subject.
6. Remove one subject.
7. Sort the subjects alphabetically.
8. Display the number of subjects.

### Expected Output

```text
STUDENT SUBJECT MANAGER

Subjects:
['Mathematics', 'English', 'Physics', 'Biology', 'Chemistry']

Total Subjects: 5
First Subject: Mathematics
Last Subject: Chemistry
```

---

## 7. Knowledge Check — 5 Minutes

1. What is a data structure?
2. What is a list?
3. What is indexing?
4. What does `append()` do?
5. What is the difference between a list and a tuple?

---

# 📝 SESSION 1 ASSIGNMENT

## Student Score Collection

Create:

`student_scores.py`

### Requirements

1. Create a list containing at least eight student scores.
2. Display all scores.
3. Display the highest score.
4. Display the lowest score.
5. Calculate the total score.
6. Calculate the average score.
7. Sort the scores in ascending order.
8. Sort the scores in descending order.
9. Display the total number of scores.

### Expected Deliverable

A working Python program that demonstrates list operations and basic data analysis.

---

# 🗓️ SESSION 2 — DICTIONARIES, SETS & FOR LOOPS

**Duration:** 2 Hours

## Session Breakdown

| Activity | Duration |
|---|---:|
| Assignment Review | 15 minutes |
| Python Dictionaries | 30 minutes |
| Python Sets | 15 minutes |
| Introduction to Iteration | 10 minutes |
| `for` Loops and `range()` | 25 minutes |
| Guided Practical | 20 minutes |
| Knowledge Check | 5 minutes |
| **Total** | **120 minutes** |

---

## 1. Assignment Review — 15 Minutes

Review the Student Score Collection assignment.

Check:

- Correct list creation
- Appropriate use of built-in functions
- Accurate average calculation
- Sorting
- Readable output
- Code organisation

---

## 2. Python Dictionaries — 30 Minutes

A dictionary stores information using **key-value pairs**.

### Creating a Dictionary

```python
student = {
    "name": "Uzoamaka",
    "age": 16,
    "course": "Software Engineering",
    "score": 85
}
```

### Accessing Values

```python
print(student["name"])
print(student["score"])
```

### Using `get()`

```python
print(student.get("course"))
```

### Updating Values

```python
student["score"] = 90
```

### Adding Values

```python
student["school"] = "Example Secondary School"
```

### Removing Values

```python
student.pop("school")
```

### Dictionary Keys and Values

```python
print(student.keys())
print(student.values())
print(student.items())
```

### Discussion

Why is a dictionary useful for storing student records?

---

## 3. Python Sets — 15 Minutes

A set stores unique values.

```python
subjects = {"Mathematics", "English", "Physics"}
```

### Duplicate Values

```python
numbers = {1, 2, 2, 3, 3, 4}

print(numbers)
```

Duplicates are automatically removed.

### Adding and Removing Values

```python
numbers.add(5)
numbers.discard(2)
```

### Set Membership

```python
print(3 in numbers)
```

### Discussion

When would we want to avoid duplicate values?

---

## 4. Introduction to Iteration — 10 Minutes

Iteration means repeating a process.

For example, displaying five student names.

Without loops:

```python
print("Student 1")
print("Student 2")
print("Student 3")
print("Student 4")
print("Student 5")
```

With a loop:

```python
for number in range(1, 6):
    print(f"Student {number}")
```

---

## 5. Python `for` Loops — 25 Minutes

### Iterating Over a List

```python
students = ["Ada", "Chidi", "Uzoamaka"]

for student in students:
    print(student)
```

### Iterating Over Numbers

```python
for number in range(1, 11):
    print(number)
```

### Calculating a Total

```python
scores = [70, 80, 90]

total = 0

for score in scores:
    total += score

print("Total:", total)
```

### Iterating Over Dictionaries

```python
student = {
    "name": "Uzoamaka",
    "age": 16,
    "course": "Software Engineering"
}

for key, value in student.items():
    print(f"{key}: {value}")
```

### Combining Loops and Conditions

```python
scores = [45, 75, 30, 90, 60]

for score in scores:
    if score >= 50:
        print(f"{score}: Pass")
    else:
        print(f"{score}: Fail")
```

---

## 6. Guided Practical — 20 Minutes

### Exercise 2: Student Records

Create:

`student_records.py`

### Requirements

1. Create a list containing three student dictionaries.
2. Each dictionary must contain a name, age and score.
3. Use a loop to display each student's information.
4. Determine whether each student passed or failed.
5. Display the total number of students.

### Starter Example

```python
students = [
    {"name": "Ada", "age": 16, "score": 75},
    {"name": "Chidi", "age": 17, "score": 45},
    {"name": "Uzoamaka", "age": 16, "score": 90}
]

for student in students:
    print(student["name"], student["score"])
```

The student should extend this code independently.

---

## 7. Knowledge Check — 5 Minutes

1. What is a dictionary?
2. What is a key-value pair?
3. What is a set?
4. What is iteration?
5. What does `range()` do?
6. Why are loops useful?

---

# 📝 SESSION 2 ASSIGNMENT

## Student Performance Reporter

Create:

`performance_reporter.py`

### Requirements

1. Store at least five student records.
2. Use dictionaries to represent each student.
3. Store the dictionaries in a list.
4. Use a `for` loop to process the records.
5. Display each student's name and score.
6. Determine Pass or Fail.
7. Count the number of passing students.
8. Count the number of failing students.
9. Display a summary.

### Expected Output

```text
STUDENT PERFORMANCE REPORT

Ada: 75 - PASS
Chidi: 45 - FAIL
Uzoamaka: 90 - PASS

Total Students: 3
Passed: 2
Failed: 1
```

---

# 🗓️ SESSION 3 — WHILE LOOPS, LOOP CONTROL & WEEKLY PROJECT

**Duration:** 2 Hours

## Session Breakdown

| Activity | Duration |
|---|---:|
| Assignment Review | 15 minutes |
| `while` Loops | 20 minutes |
| Loop Control | 15 minutes |
| Nested Loops and Input Collection | 15 minutes |
| Guided Practical | 20 minutes |
| Weekly Project Development | 25 minutes |
| Project Review | 10 minutes |
| **Total** | **120 minutes** |

---

## 1. Assignment Review — 15 Minutes

Review the Student Performance Reporter.

Discuss:

- Lists of dictionaries
- Iteration
- Conditional logic
- Counting
- Correct output

---

## 2. Python `while` Loops — 20 Minutes

A `while` loop repeats instructions while a condition remains true.

### Example

```python
count = 1

while count <= 5:
    print(count)
    count += 1
```

### Important Concept

A `while` loop must eventually stop unless continuous execution is intentional.

### Infinite Loop Example

```python
count = 1

while count <= 5:
    print(count)
```

Explain why this loop does not terminate.

---

## 3. Loop Control — 15 Minutes

### `break`

Stops a loop.

```python
for number in range(1, 10):
    if number == 5:
        break

    print(number)
```

### `continue`

Skips the remaining instructions in the current iteration.

```python
for number in range(1, 6):
    if number == 3:
        continue

    print(number)
```

### Discussion

What is the difference between `break` and `continue`?

---

## 4. Nested Loops and Input Collection — 15 Minutes

### Nested Loops

```python
for row in range(1, 4):
    for column in range(1, 4):
        print(row, column)
```

### Collecting Multiple Scores

```python
scores = []

for number in range(3):
    score = float(input(f"Enter score {number + 1}: "))
    scores.append(score)

print(scores)
```

For now, assume valid numerical input. More advanced exception handling will be covered in Week 7.

---

## 5. Guided Practical — 20 Minutes

### Exercise 3: Number Guessing Game

Create:

`number_guessing.py`

### Requirements

1. Define a secret number.
2. Ask the user to guess.
3. Continue asking until the correct number is entered.
4. Display whether the guess is too high or too low.
5. Display a success message when correct.

### Starter Code

```python
secret_number = 7
guess = None

while guess != secret_number:
    guess = int(input("Guess the number: "))

    if guess < secret_number:
        print("Too low!")
    elif guess > secret_number:
        print("Too high!")
    else:
        print("Correct!")
```

### Extension

Count the number of attempts.

---

# 🏆 WEEK 6 PROJECT — STUDENT SCORE ANALYSER

## Project Description

Build a Python command-line application that stores and analyses student examination scores.

The application should use collections, loops, conditional statements and basic calculations.

## Functional Requirements

The program must:

1. Display a welcome message.
2. Ask how many student records will be entered.
3. Collect each student's name.
4. Collect each student's score.
5. Store the information using a list of dictionaries.
6. Display all student records.
7. Calculate the class average.
8. Identify the highest score.
9. Identify the lowest score.
10. Count passing students.
11. Count failing students.
12. Display a formatted performance summary.

### Grading Rule

A score of **50 or above** is a pass.

Scores must be between 0 and 100.

### Example Output

```text
==================================
       STUDENT SCORE ANALYSER
==================================

How many students? 3

Student 1 Name: Ada
Score: 75

Student 2 Name: Chidi
Score: 45

Student 3 Name: Uzoamaka
Score: 90

==================================
         CLASS REPORT
==================================

Ada          75    PASS
Chidi        45    FAIL
Uzoamaka     90    PASS

Total Students: 3
Class Average: 70.00
Highest Score: 90
Lowest Score: 45

Passed: 2
Failed: 1

==================================
```

### Technical Requirements

Use:

- Lists
- Dictionaries
- `for` loops
- At least one `while` loop
- Conditional statements
- Arithmetic operations
- Meaningful variable names

### Bonus Challenges

- Sort students by score.
- Display students scoring above the class average.
- Allow another class report to be generated.
- Handle empty records and invalid scores.

---

# 📂 Suggested Folder Structure

```text
Week-06/
│
├── exercises/
│   ├── student_subjects.py
│   ├── student_records.py
│   └── number_guessing.py
│
├── assignments/
│   ├── student_scores.py
│   └── performance_reporter.py
│
├── projects/
│   └── student_score_analyser.py
│
└── README.md
```

---

# 🧠 Week 6 Knowledge Check

1. What is a data structure?
2. What is a list?
3. What is a tuple?
4. What is a dictionary?
5. What is a set?
6. What is indexing?
7. What is list slicing?
8. What does `append()` do?
9. What does `pop()` do?
10. What does `len()` do?
11. What is iteration?
12. What is a `for` loop?
13. What is a `while` loop?
14. What does `range()` do?
15. What does `break` do?
16. What does `continue` do?
17. What is an infinite loop?
18. What is a nested loop?
19. How can a list contain dictionaries?
20. How can loops help analyse student records?

---

# 📊 Week 6 Assessment

| Assessment Area | Weight |
|---|---:|
| Understanding data structures | 20% |
| List and dictionary operations | 20% |
| Loop implementation | 20% |
| Combining loops and conditions | 15% |
| Code organisation and readability | 10% |
| Independent problem-solving | 5% |
| Weekly project completion | 10% |
| **Total** | **100%** |

---

# 📦 Week 6 Deliverables

- Student Subject Manager
- Student Score Collection
- Student Records Exercise
- Student Performance Reporter
- Number Guessing Game
- Student Score Analyser
- Week 6 Knowledge Check
- Git commits documenting progress

---

# 🎓 Expected Learning Outcomes

By the end of Week 6, the student should be able to:

- Organise information using Python collections.
- Manipulate lists and dictionaries.
- Explain the purpose of tuples and sets.
- Use loops to process collections.
- Combine loops with conditional statements.
- Calculate summary statistics from stored data.
- Build a small command-line data-processing application.

---

## ⏭️ Next Module

**Week 7 — Functions, Modular Programming & Debugging**

The student will learn how to organise code into reusable functions, handle errors, debug applications and build a modular expense tracker.

---

<div align="center">

**Opsfuxion Technologies Limited**

*Orchestrate Intelligence, Deliver with Precision.*

© 2026 Opsfuxion Technologies Limited.

</div>
