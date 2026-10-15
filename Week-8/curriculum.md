
# 🏗️ WEEK 8 — OBJECT-ORIENTED PROGRAMMING (OOP)

<div align="center">

![Python](https://img.shields.io/badge/Python-OOP-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Level](https://img.shields.io/badge/Level-Beginner-16A085?style=for-the-badge)
![Duration](https://img.shields.io/badge/Duration-1_Week-7C3AED?style=for-the-badge)
![Project](https://img.shields.io/badge/Project-Student_Management-D4A43A?style=for-the-badge)

**Practical Software Engineering Foundation Programme**

**Training Provider:** Opsfuxion Technologies Limited

*Orchestrate Intelligence, Deliver with Precision.*

</div>

---

## 📋 Programme Information

| Item | Details |
|---|---|
| Module | Week 8 — Object-Oriented Programming |
| Duration | 1 Week |
| Sessions | 3 instructor-led sessions |
| Session Duration | 2 Hours |
| Total Contact Hours | 6 Hours |
| Level | Beginner |
| Prerequisites | Weeks 4–7 |
| Primary Language | Python 3 |
| Weekly Project | Student Management System — OOP Version |
| Learning Approach | Theory, guided coding, independent practice and project development |

---

# 📖 Week Overview

In previous weeks, the student learned how to write Python programs using variables, functions, loops, dictionaries and modules.

These programming techniques are useful for building small applications.

However, as software systems grow, managing related data and behaviour separately can become increasingly difficult.

Consider a school management application.

Each student has information such as:

- Name
- Age
- Student ID
- Subjects
- Examination scores

Each student may also perform or be associated with actions such as:

- Updating information
- Recording examination scores
- Calculating averages
- Determining grades
- Displaying academic reports

Object-Oriented Programming provides a way to organise related data and behaviour into objects.

This week introduces classes, objects, attributes, methods, constructors, encapsulation and basic inheritance.

The student will apply these concepts to build a simple Student Management System.

---

# 🎯 Learning Objectives

By the end of Week 8, the student should be able to:

- Explain Object-Oriented Programming.
- Differentiate between procedural and object-oriented approaches.
- Explain what a class is.
- Explain what an object is.
- Understand attributes and methods.
- Define Python classes.
- Create objects from classes.
- Understand the purpose of `self`.
- Use the `__init__()` constructor method.
- Create instance attributes.
- Define instance methods.
- Update object attributes.
- Explain encapsulation.
- Understand public and conventionally non-public attributes.
- Apply basic data validation within methods.
- Explain inheritance.
- Create a simple subclass.
- Use `super()` to initialise inherited attributes.
- Organise related data and behaviour into classes.
- Build a beginner-level OOP application.

---

# 🗓️ SESSION 1 — INTRODUCTION TO CLASSES, OBJECTS & ATTRIBUTES

**Duration:** 2 Hours

## Session Objectives

The student will:

1. Understand OOP.
2. Compare procedural and object-oriented programming.
3. Understand classes and objects.
4. Define Python classes.
5. Create instance attributes.
6. Write simple methods.

### Session Breakdown

| Activity | Duration |
|---|---:|
| Review of Week 7 | 10 minutes |
| Introduction to OOP | 20 minutes |
| Classes and Objects | 25 minutes |
| Constructors and Attributes | 25 minutes |
| Methods and `self` | 15 minutes |
| Guided Practical | 20 minutes |
| Knowledge Check | 5 minutes |
| **Total** | **120 minutes** |

---

## 1. Review of Week 7 — 10 Minutes

Review:

- Functions
- Parameters
- Return values
- Modular programming
- Debugging
- Input validation

### Discussion

Suppose we have 100 students.

Each student has a name, age, identification number and examination score.

How can we represent each student in a structured and reusable way?

---

## 2. What is Object-Oriented Programming? — 20 Minutes

Object-Oriented Programming is a programming approach that organises software around objects containing related data and behaviour.

### Procedural Approach

```python
student_name = "Uzoamaka"
student_age = 16
student_score = 85

def display_student(name, age, score):
    print(name, age, score)

display_student(
    student_name,
    student_age,
    student_score
)
```

### Object-Oriented Approach

```python
class Student:
    def __init__(self, name, age, score):
        self.name = name
        self.age = age
        self.score = score

    def display(self):
        print(self.name, self.age, self.score)

student = Student("Uzoamaka", 16, 85)

student.display()
```

### Discussion

What information and behaviour belong together?

---

## 3. Understanding Classes and Objects — 25 Minutes

### What is a Class?

A class is a blueprint used to create objects.

### What is an Object?

An object is an instance of a class.

### Everyday Analogy

A class can be compared to a building plan.

Objects are individual buildings created using that plan.

### Basic Class

```python
class Student:
    pass
```

### Creating Objects

```python
student1 = Student()
student2 = Student()

print(student1)
print(student2)
```

Explain that both objects belong to the same class but are separate instances.

---

## 4. Constructors and Attributes — 25 Minutes

### The `__init__()` Method

The `__init__()` method initialises an object's attributes when an instance is created.

```python
class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age
```

### Creating Student Objects

```python
student1 = Student("Uzoamaka", 16)
student2 = Student("Ada", 17)
```

### Accessing Attributes

```python
print(student1.name)
print(student1.age)

print(student2.name)
print(student2.age)
```

### Understanding `self`

`self` refers to the particular object on which an instance method is operating.

### Discussion

Why does each student object have its own name and age?

---

## 5. Methods and Object Behaviour — 15 Minutes

Methods are functions defined inside classes.

### Example

```python
class Student:
    def __init__(self, name, score):
        self.name = name
        self.score = score

    def display_result(self):
        print(f"Student: {self.name}")
        print(f"Score: {self.score}")
```

### Calling a Method

```python
student = Student("Uzoamaka", 85)

student.display_result()
```

---

## 6. Guided Practical — 20 Minutes

### Exercise 1: Student Profile Class

Create:

`student_profile.py`

### Requirements

1. Create a `Student` class.
2. Add name, age, school and course attributes.
3. Create a method that displays student information.
4. Create at least three student objects.
5. Display each student's information.

### Suggested Class Structure

```python
class Student:
    def __init__(self, name, age, school, course):
        self.name = name
        self.age = age
        self.school = school
        self.course = course

    def display_profile(self):
        print(f"Name: {self.name}")
        print(f"Age: {self.age}")
        print(f"School: {self.school}")
        print(f"Course: {self.course}")
```

The student should create objects and call their methods independently.

---

## 7. Knowledge Check — 5 Minutes

1. What is OOP?
2. What is a class?
3. What is an object?
4. What is an attribute?
5. What is a method?
6. What is `self`?

---

# 📝 SESSION 1 ASSIGNMENT

## Library Book Class

Create:

`library_book.py`

### Requirements

Create a `Book` class with:

- Title
- Author
- Publication year
- Availability status

### Methods

- `display_details()`
- `borrow_book()`
- `return_book()`

### Expected Behaviour

- A book can be borrowed when available.
- Borrowing an available book changes its status.
- A borrowed book cannot be borrowed again until returned.
- Returning a book makes it available.

### Deliverable

A working Python program containing at least three `Book` objects.

---

# 🗓️ SESSION 2 — ENCAPSULATION, INSTANCE METHODS & INHERITANCE

**Duration:** 2 Hours

## Session Breakdown

| Activity | Duration |
|---|---:|
| Assignment Review | 15 minutes |
| Instance Attributes and Methods | 20 minutes |
| Encapsulation | 25 minutes |
| Introduction to Inheritance | 25 minutes |
| Guided Practical | 25 minutes |
| Knowledge Check | 10 minutes |
| **Total** | **120 minutes** |

---

## 1. Assignment Review — 15 Minutes

Review:

- Class structure
- Constructors
- Attributes
- Methods
- Object state changes

---

## 2. Instance Attributes and Methods — 20 Minutes

Objects can maintain their own information.

### Example

```python
class Student:
    def __init__(self, name):
        self.name = name
        self.scores = []

    def add_score(self, score):
        if 0 <= score <= 100:
            self.scores.append(score)
        else:
            print("Invalid score.")

    def calculate_average(self):
        if not self.scores:
            return None

        return sum(self.scores) / len(self.scores)
```

### Creating Objects

```python
student1 = Student("Uzoamaka")
student2 = Student("Ada")

student1.add_score(80)
student1.add_score(90)

student2.add_score(70)

print(student1.calculate_average())
print(student2.calculate_average())
```

### Discussion

Why do the two objects have different scores?

---

## 3. Understanding Encapsulation — 25 Minutes

Encapsulation involves grouping related data and methods together and controlling how an object's internal state is accessed or changed.

### Example

```python
class BankAccount:
    def __init__(self, owner, balance=0):
        self.owner = owner
        self._balance = balance

    def deposit(self, amount):
        if amount > 0:
            self._balance += amount

    def get_balance(self):
        return self._balance
```

### Usage

```python
account = BankAccount("Ada", 1000)

account.deposit(500)

print(account.get_balance())
```

### Important Note

In Python, a single leading underscore indicates that an attribute is intended for internal use by convention.

It does not make the attribute strictly private.

### Discussion

Why should a bank account validate deposits rather than accept every value?

---

## 4. Introduction to Inheritance — 25 Minutes

Inheritance allows a class to reuse and extend behaviour defined in another class.

### Parent Class

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def introduce(self):
        print(f"My name is {self.name}.")
```

### Child Class

```python
class Student(Person):
    def __init__(self, name, age, course):
        super().__init__(name, age)
        self.course = course

    def display_course(self):
        print(f"Course: {self.course}")
```

### Creating an Object

```python
student = Student(
    "Uzoamaka",
    16,
    "Software Engineering"
)

student.introduce()
student.display_course()
```

### Discussion

- What does the child class inherit?
- What does `super()` do?
- When is inheritance useful?

---

## 5. Guided Practical — 25 Minutes

### Exercise 2: School Personnel System

Create:

`school_personnel.py`

### Requirements

1. Create a `Person` class.
2. Add name and age attributes.
3. Create a `Student` subclass.
4. Add student ID and course attributes.
5. Create a `Teacher` subclass.
6. Add subject and staff ID attributes.
7. Create objects from both subclasses.
8. Display their information.

### Learning Focus

- Inheritance
- Constructors
- `super()`
- Reusable methods
- Object-specific attributes

---

## 6. Knowledge Check — 10 Minutes

1. What is encapsulation?
2. What is an instance attribute?
3. What is inheritance?
4. What is a parent class?
5. What is a child class?
6. What does `super()` do?
7. What does a leading underscore mean in Python?

---

# 📝 SESSION 2 ASSIGNMENT

## Student Academic Record

Create:

`student_academic_record.py`

### Requirements

Create a `Student` class that:

1. Stores a student name.
2. Stores a student ID.
3. Maintains a list of examination scores.
4. Provides a method to add scores.
5. Rejects scores outside 0–100.
6. Calculates the average score.
7. Determines Pass or Fail.
8. Displays an academic report.

### Pass Rule

Average score of 50 or above.

### Expected Output

```text
================================
       STUDENT REPORT
================================

Name: Uzoamaka
Student ID: STU001

Scores: [75, 85, 90]
Average: 83.33
Status: PASS

================================
```

---

# 🗓️ SESSION 3 — OOP APPLICATION DESIGN & WEEKLY PROJECT

**Duration:** 2 Hours

## Session Breakdown

| Activity | Duration |
|---|---:|
| Assignment Review | 15 minutes |
| Designing Classes from Requirements | 20 minutes |
| Guided Practical | 20 minutes |
| Project Development | 50 minutes |
| Project Review | 15 minutes |
| **Total** | **120 minutes** |

---

## 1. Assignment Review — 15 Minutes

Review:

- Class design
- Attributes
- Methods
- Input validation
- Average calculation
- Report generation

---

## 2. Designing Classes from Requirements — 20 Minutes

Before writing code, identify the objects required by a program.

### Scenario

A school needs a program to manage student records.

### Questions

1. What objects exist in the system?
2. What information belongs to each student?
3. What actions should students support?
4. What actions should the management system support?

### Proposed Classes

**Student**

Attributes:

- Student ID
- Name
- Age
- Scores

Methods:

- Add score
- Calculate average
- Display information

**StudentManager**

Attributes:

- Collection of students

Methods:

- Add student
- View students
- Find student
- Display student reports

---

## 3. Guided Practical — 20 Minutes

### Exercise 3: Student Manager Class

Create:

`student_manager.py`

### Starter Structure

```python
class StudentManager:
    def __init__(self):
        self.students = []

    def add_student(self, student):
        self.students.append(student)

    def view_students(self):
        for student in self.students:
            print(student.name)
```

### Student Task

Extend the class with a method for finding students by ID.

---

# 🏆 WEEK 8 PROJECT — STUDENT MANAGEMENT SYSTEM (OOP VERSION)

## Project Description

Build a command-line Student Management System using Object-Oriented Programming.

This project introduces the core application that will later be expanded during the final capstone.

---

## Functional Requirements

The system should:

1. Display a menu.
2. Allow users to register students.
3. Store student information.
4. Display registered students.
5. Search for students by ID.
6. Record examination scores.
7. Calculate student averages.
8. Display academic reports.
9. Handle invalid scores.
10. Exit the program.

---

## Required Classes

### `Student`

Responsible for:

- Student information
- Examination scores
- Average calculations
- Academic results

### `StudentManager`

Responsible for:

- Managing multiple student objects
- Registering students
- Finding students
- Listing records

---

## Suggested Menu

```text
====================================
       STUDENT MANAGEMENT
====================================

1. Register Student
2. View Students
3. Find Student
4. Add Student Score
5. View Academic Report
6. Exit

Select an option:
```

---

## Technical Requirements

The project must demonstrate:

- Classes
- Objects
- Constructors
- Attributes
- Instance methods
- Encapsulation principles
- Lists
- Loops
- Conditional statements
- Functions
- Input validation

### Optional Extension

Create a `Person` parent class and let `Student` inherit shared attributes.

Inheritance should only be introduced where it makes the design clearer.

---

## Suggested Project Structure

```text
Week-08/
│
├── exercises/
│   ├── student_profile.py
│   └── school_personnel.py
│
├── assignments/
│   ├── library_book.py
│   └── student_academic_record.py
│
└── projects/
    └── student-management-oop/
        ├── main.py
        ├── student.py
        ├── student_manager.py
        └── README.md
```

---

# 🧪 Suggested Test Cases

| Test Case | Expected Result |
|---|---|
| Create a student object | Student is created |
| Register a student | Student appears in records |
| Search existing ID | Correct student is returned |
| Search unknown ID | Appropriate message |
| Add valid score | Score is recorded |
| Add score above 100 | Score is rejected |
| Add negative score | Score is rejected |
| Calculate average with scores | Correct average |
| Calculate average without scores | Friendly message |
| Display student report | Correct student information |

---

# 🧠 Week 8 Knowledge Check

1. What is Object-Oriented Programming?
2. What is a class?
3. What is an object?
4. What is an instance?
5. What is an attribute?
6. What is a method?
7. What is `self`?
8. What is `__init__()`?
9. What is an instance variable?
10. What is encapsulation?
11. Why should object data be validated?
12. What is inheritance?
13. What is a parent class?
14. What is a child class?
15. What does `super()` do?
16. How is OOP different from procedural programming?
17. Why are classes useful for representing student records?
18. Can two objects from the same class have different values?
19. What is the difference between a function and a method?
20. How can OOP improve software maintainability?

---

# 📊 Week 8 Assessment

| Assessment Area | Weight |
|---|---:|
| Understanding OOP concepts | 20% |
| Class and object implementation | 20% |
| Constructors and methods | 15% |
| Encapsulation and validation | 15% |
| Introductory inheritance | 10% |
| Code organisation | 10% |
| Weekly project completion | 10% |
| **Total** | **100%** |

---

# 📦 Week 8 Deliverables

- Student Profile Class
- Library Book Class
- School Personnel Exercise
- Student Academic Record
- Student Manager Class
- Student Management System — OOP Version
- Week 8 Knowledge Check
- Documented GitHub commits

---

# 🎓 Expected Learning Outcomes

By the end of Week 8, the student should be able to:

- Explain OOP principles.
- Create Python classes and objects.
- Use constructors and instance methods.
- Organise related data and behaviour.
- Apply basic encapsulation.
- Understand introductory inheritance.
- Design simple object-oriented applications.
- Build a beginner-level Student Management System.

---

## ⏭️ Next Module

**Week 9 — Data Structures & Algorithms**

The student will learn how to implement searching, sorting, stacks and queues, and understand introductory algorithm efficiency.

---

<div align="center">

**Opsfuxion Technologies Limited**

*Orchestrate Intelligence, Deliver with Precision.*

© 2026 Opsfuxion Technologies Limited.

</div>
