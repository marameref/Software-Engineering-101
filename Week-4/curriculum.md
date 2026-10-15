
# Week 4 — Python Programming Fundamentals

## Practical Software Engineering Foundation Programme

**Duration:** 1 Week  
**Sessions:** 3 Instructor-Led Sessions  
**Session Duration:** 2 Hours  
**Total Instructor-Led Time:** 6 Hours  
**Level:** Beginner  
**Prerequisites:** Weeks 0–3  
**Weekly Projects:** Student Profile Generator & Basic Calculator  
**Primary Language:** Python 3

---

## Week Overview

Week 4 introduces Python programming and marks the student's transition from creating webpages to writing programs that process information and perform calculations.

Building on the foundational development skills acquired in Weeks 0–3, the student will learn how to write and execute Python programs, store information using variables, work with different data types, accept user input, perform arithmetic operations, and display meaningful results.

The focus is on understanding how programs execute instructions, how information is represented in code, and how basic programming concepts can be combined to solve simple problems.

By the end of the week, the student should be able to independently write a beginner-level Python application that accepts input, performs calculations, and displays formatted results.

---

# Learning Objectives

By the end of Week 4, the student should be able to:

- Explain what programming is.
- Explain what Python is and why it is used.
- Understand the difference between a programming language and a markup language.
- Install and verify a Python development environment.
- Create and execute Python scripts.
- Understand basic Python syntax.
- Write comments.
- Use the `print()` function.
- Create and assign values to variables.
- Identify common Python data types.
- Use the `type()` function.
- Understand basic naming conventions.
- Accept user input using `input()`.
- Convert values between data types.
- Perform arithmetic calculations.
- Use assignment operators.
- Format program output using f-strings.
- Identify and correct simple programming errors.
- Develop small interactive command-line programs.

---

# Session 1 — Introduction to Python, Variables & Data Types

**Duration:** 2 Hours

## 1. Review of Previous Weeks — 10 Minutes

Review:

- VS Code
- Terminal navigation
- HTML and CSS
- Git and GitHub
- Creating and organising project files

### Discussion

Previously, we created webpages using HTML and CSS.

What if we wanted to build a program that could:

- Calculate a student's average score?
- Add two numbers?
- Ask someone for their name?
- Calculate the cost of purchased items?

How would the computer know what calculations to perform?

This introduces programming.

---

## 2. What is Programming? — 15 Minutes

Programming is the process of writing instructions that a computer can execute to perform specific tasks.

### Programming vs Markup

HTML describes the structure of webpage content.

Python is a programming language that can process information, perform calculations, make decisions, and automate tasks.

### What is Python?

Python is a general-purpose programming language widely used for:

- Software development
- Backend development
- Automation
- Data processing
- Scientific computing
- Scripting
- Artificial intelligence and machine learning

The student will focus on general programming fundamentals.

---

## 3. Python Development Environment — 20 Minutes

### Verify Python Installation

Open the terminal and run:

```bash
python3 --version
```

Depending on the operating system, Python may also be available through:

```bash
python --version
```

If Python is not installed, install a supported Python 3 version.

### Create a Project Folder

```text
Week-04/
└── python-fundamentals/
```

Open the folder in VS Code.

Create:

```text
hello.py
```

### First Python Program

```python
print("Hello, World!")
print("Welcome to Python programming!")
```

Run the program:

```bash
python3 hello.py
```

Or use the appropriate Python command configured on the computer.

### Discussion

Explain:

- Python script
- File extension `.py`
- Python interpreter
- Source code
- Program execution
- Terminal output

---

## 4. Understanding Python Syntax — 15 Minutes

Python programs follow rules known as syntax.

Example:

```python
print("Hello, Uzoamaka!")
```

Discuss:

- Function names
- Parentheses
- Quotation marks
- Strings
- Case sensitivity
- Syntax errors

### Python Comments

```python
# This is a comment

print("Hello!")
```

Comments help explain code and are not executed as Python instructions.

---

## 5. Introduction to Variables — 20 Minutes

Variables allow programs to associate names with values.

Example:

```python
student_name = "Uzoamaka"
student_age = 16
course = "Software Engineering"

print(student_name)
print(student_age)
print(course)
```

### Variable Naming Rules

Introduce:

- Meaningful variable names
- Lowercase naming
- Snake case
- Avoiding spaces
- Avoiding Python keywords
- Case sensitivity

Example:

```python
first_name = "Uzoamaka"
last_name = "Student"
```

---

## 6. Python Data Types — 20 Minutes

Introduce four basic data types.

### String — `str`

```python
name = "Uzoamaka"
```

### Integer — `int`

```python
age = 16
```

### Float — `float`

```python
height = 1.65
```

### Boolean — `bool`

```python
is_student = True
```

### Checking Data Types

```python
print(type(name))
print(type(age))
print(type(height))
print(type(is_student))
```

Explain that different types of information are represented differently in programs.

---

## 7. Guided Practical — 15 Minutes

### Practical Exercise 1: Student Information

Create:

```text
student_info.py
```

The program should store:

- Student name
- Age
- School
- Intended university course
- Favourite subject
- Whether the student enjoys programming

Display the information using `print()`.

### Example

```python
student_name = "Uzoamaka"
age = 16
course = "Software Engineering"

print("Student:", student_name)
print("Age:", age)
print("Course:", course)
```

---

## 8. Session Review — 5 Minutes

Questions:

1. What is Python?
2. What is a Python script?
3. What does `print()` do?
4. What is a variable?
5. What is a data type?
6. What is the difference between `int` and `str`?

---

# Session 1 Assignment

## My Student Information Program

Create a Python program named:

```text
about_me.py
```

The program must:

1. Store at least eight personal or educational details.
2. Use meaningful variable names.
3. Include at least three different data types.
4. Display all information clearly.
5. Include appropriate comments.

### Deliverable

A working Python script containing organised student information.

---

# Session 2 — Operators, User Input & Type Conversion

**Duration:** 2 Hours

## 1. Assignment Review — 15 Minutes

The student will demonstrate the Session 1 assignment.

Review:

- Variable naming
- Data types
- Python syntax
- Code readability
- Correct output
- Error messages encountered

---

## 2. Arithmetic Operators — 25 Minutes

Python supports mathematical operations.

| Operator | Meaning | Example |
|---|---|---|
| `+` | Addition | `5 + 3` |
| `-` | Subtraction | `5 - 3` |
| `*` | Multiplication | `5 * 3` |
| `/` | Division | `5 / 2` |
| `//` | Floor division | `5 // 2` |
| `%` | Modulus | `5 % 2` |
| `**` | Exponentiation | `5 ** 2` |

### Practical Example

```python
a = 10
b = 3

print(a + b)
print(a - b)
print(a * b)
print(a / b)
print(a // b)
print(a % b)
print(a ** b)
```

### Discussion

What is the difference between `/` and `//`?

What does the modulus operator return?

---

## 3. Assignment Operators — 15 Minutes

Introduce:

```python
score = 10

score += 5
score -= 2
score *= 2
```

Explain how assignment operators update values.

---

## 4. Accepting User Input — 20 Minutes

Programs can request information from users.

### Example

```python
name = input("What is your name? ")

print("Hello,", name)
```

### Important Concept

The `input()` function returns a string.

Example:

```python
age = input("Enter your age: ")

print(type(age))
```

Even if the user enters `16`, the value is initially a string.

---

## 5. Type Conversion — 20 Minutes

Introduce:

- `int()`
- `float()`
- `str()`

### Example

```python
age = int(input("Enter your age: "))

print(age + 1)
```

### Another Example

```python
price = float(input("Enter item price: "))
quantity = int(input("Enter quantity: "))

total = price * quantity

print(total)
```

Explain that invalid input may cause errors.

More advanced input validation will be introduced in Week 5.

---

## 6. String Formatting — 10 Minutes

Introduce f-strings.

```python
name = "Uzoamaka"
age = 16

print(f"My name is {name} and I am {age} years old.")
```

Explain how f-strings combine text and variable values.

---

## 7. Guided Practical — 10 Minutes

### Practical Exercise 2: Shopping Calculator

Create:

```text
shopping_calculator.py
```

Requirements:

1. Ask the user for a product name.
2. Ask for the product price.
3. Ask for the quantity purchased.
4. Calculate the total cost.
5. Display the purchase summary.

### Example Output

```text
Product: Notebook
Price: 2500
Quantity: 3

Total Cost: NGN 7500.00
```

---

## 8. Session Review — 5 Minutes

Questions:

1. What does `input()` do?
2. What data type does `input()` return?
3. Why is type conversion important?
4. What does `%` do?
5. What is an f-string?

---

# Session 2 Assignment

## Simple Bill Calculator

Create:

```text
bill_calculator.py
```

Requirements:

- Ask for the name of an item.
- Ask for its price.
- Ask for the quantity.
- Calculate the subtotal.
- Apply a fixed 5% discount.
- Calculate the final total.
- Display a formatted receipt.

### Example

```text
Item: School Bag
Price: NGN 15000
Quantity: 2

Subtotal: NGN 30000.00
Discount: NGN 1500.00
Total: NGN 28500.00
```

### Deliverable

A working bill calculator using variables, operators, input, type conversion and formatted output.

---

# Session 3 — Combining Python Fundamentals & Weekly Projects

**Duration:** 2 Hours

## 1. Assignment Review — 15 Minutes

Review the bill calculator.

Discuss:

- User input
- Type conversion
- Arithmetic operations
- Variable naming
- Output formatting
- Basic debugging

---

## 2. Understanding Program Execution — 15 Minutes

Explain how Python executes statements in sequence.

Example:

```python
name = input("Enter your name: ")
age = int(input("Enter your age: "))

next_age = age + 1

print(f"Hello {name}!")
print(f"Next year, you will be {next_age}.")
```

Discuss the order of execution.

### Introduction to Errors

- Syntax errors
- Runtime errors
- Logic errors

Example:

```python
number = int(input("Enter a number: "))
```

What happens if the user enters `"hello"`?

Introduce the importance of reading error messages.

---

## 3. Guided Practical — 20 Minutes

### Practical Exercise 3: Student Profile Generator

Create:

```text
student_profile.py
```

Requirements:

1. Ask for the student's name.
2. Ask for age.
3. Ask for school.
4. Ask for intended course.
5. Ask for favourite subject.
6. Display a formatted student profile.
7. Calculate the student's age next year.

### Example Output

```text
================================
       STUDENT PROFILE
================================

Name: Uzoamaka
Age: 16
School: Example Secondary School
Intended Course: Software Engineering
Favourite Subject: Mathematics

Age Next Year: 17
================================
```

---

# Week 4 Project

## Basic Python Calculator

**Project Type:** Python Command-Line Application

The student will develop a calculator that accepts numerical input and performs basic arithmetic operations.

### Project Requirements

The calculator should:

1. Display a welcome message.
2. Ask the user for the first number.
3. Ask for the second number.
4. Calculate addition.
5. Calculate subtraction.
6. Calculate multiplication.
7. Calculate division.
8. Display all results clearly.
9. Use meaningful variable names.
10. Use formatted output.

### Example Output

```text
================================
        BASIC CALCULATOR
================================

Enter first number: 20
Enter second number: 5

Addition: 25
Subtraction: 15
Multiplication: 100
Division: 4.0

================================
```

### Note

For Week 4, the calculator may display all four operations.

Allowing users to select an operation using conditional statements will be introduced in Week 5.

---

## 4. Independent Project Work — 40 Minutes

The student will independently develop the calculator.

The student may:

- Review lesson notes.
- Consult previous examples.
- Research unfamiliar syntax.
- Read error messages.
- Ask conceptual questions.

The instructor should encourage independent problem-solving.

---

## 5. Project Review — 10 Minutes

Review:

- Correct calculations
- Appropriate variables
- User input
- Type conversion
- Output formatting
- Code organisation
- Handling of division by zero as a known limitation

---

# Suggested Project Structure

```text
Week-04/
│
├── exercises/
│   ├── hello.py
│   ├── student_info.py
│   └── shopping_calculator.py
│
├── assignments/
│   ├── about_me.py
│   └── bill_calculator.py
│
└── projects/
    ├── student_profile.py
    └── basic_calculator.py
```

---

# Week 4 Knowledge Check

1. What is programming?
2. What is Python?
3. What is the difference between Python and HTML?
4. What is a Python script?
5. What does `print()` do?
6. What is a variable?
7. What is a data type?
8. Name four Python data types.
9. What does `type()` do?
10. What does `input()` do?
11. What data type does `input()` return?
12. What is type conversion?
13. What is the difference between `/` and `//`?
14. What does `%` do?
15. What is an f-string?
16. What is a syntax error?
17. What is a runtime error?
18. What is a logic error?
19. Why are meaningful variable names important?
20. Why should programmers test their code?

---

# Week 4 Assessment

| Assessment Area | Weight |
|---|---:|
| Understanding Python fundamentals | 20% |
| Variables and data types | 15% |
| Operators and calculations | 20% |
| User input and type conversion | 15% |
| Code organisation and readability | 10% |
| Independent problem-solving | 10% |
| Project completion | 10% |
| **Total** | **100%** |

---

# Week 4 Deliverables

By the end of Week 4, the student should have completed:

- First Python script
- Student information exercise
- Shopping calculator
- Bill calculator assignment
- Student Profile Generator
- Basic Python Calculator
- Week 4 knowledge check

---

# Expected Outcome

By the end of Week 4, the student should be able to:

- Write and execute Python scripts.
- Create variables.
- Work with basic data types.
- Accept user input.
- Convert values between data types.
- Perform arithmetic operations.
- Display formatted output.
- Identify simple programming errors.
- Build basic interactive command-line applications.

---

## Next

**Week 5 — Programming Logic, Computational Thinking & Algorithms**

Week 5 introduces problem-solving strategies, pseudocode, flowcharts, conditional statements, Boolean logic, and input validation.
