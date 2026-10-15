
# 🧩 WEEK 7 — FUNCTIONS, MODULAR PROGRAMMING & DEBUGGING

<div align="center">

![Python](https://img.shields.io/badge/Python-Functions-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Module](https://img.shields.io/badge/Module-Modular_Programming-7C3AED?style=for-the-badge)
![Skill](https://img.shields.io/badge/Skill-Debugging-DC2626?style=for-the-badge)
![Project](https://img.shields.io/badge/Project-Expense_Tracker-16A085?style=for-the-badge)

**Practical Software Engineering Foundation Programme**

**Training Provider:** Opsfuxion Technologies Limited

*Orchestrate Intelligence, Deliver with Precision.*

</div>

---

## 📋 Programme Information

| Item | Details |
|---|---|
| Module | Week 7 — Functions, Modular Programming & Debugging |
| Duration | 1 Week |
| Sessions | 3 instructor-led sessions |
| Session Duration | 2 Hours |
| Total Contact Hours | 6 Hours |
| Level | Beginner |
| Prerequisites | Weeks 4–6 |
| Primary Language | Python 3 |
| Weekly Project | Modular Expense Tracker |
| Learning Approach | Guided coding, refactoring, debugging and independent development |

---

# 📖 Week Overview

In previous weeks, the student learned how to write Python programs using variables, conditions, loops and data structures.

As programs become larger, writing every instruction in one continuous block becomes difficult to maintain.

Consider a program that:

- Adds student records.
- Calculates scores.
- Displays reports.
- Searches for information.
- Updates existing records.

Without proper organisation, the code may become repetitive and difficult to debug.

This week introduces **functions**, which allow programmers to group instructions into reusable units.

The student will also learn modular programming, basic debugging techniques, exception handling and introductory file operations.

By the end of the week, the student will develop a modular expense tracker using functions, collections, loops and input validation.

---

# 🎯 Learning Objectives

By the end of Week 7, the student should be able to:

- Explain what a function is.
- Understand why functions improve code organisation.
- Define functions using `def`.
- Call functions.
- Use parameters and arguments.
- Understand return values.
- Differentiate between `print()` and `return`.
- Use default parameters.
- Understand local and global scope.
- Explain the DRY principle.
- Refactor repetitive code.
- Organise code into modules.
- Import functions from another Python file.
- Identify syntax, runtime and logic errors.
- Read Python traceback messages.
- Use debugging techniques.
- Handle exceptions using `try` and `except`.
- Validate user input.
- Understand introductory file handling.
- Build a modular command-line application.

---

# 🗓️ SESSION 1 — PYTHON FUNCTIONS & CODE REUSABILITY

**Duration:** 2 Hours

## Session Breakdown

| Activity | Duration |
|---|---:|
| Review of Week 6 | 10 minutes |
| Introduction to Functions | 20 minutes |
| Parameters and Arguments | 20 minutes |
| Return Values | 20 minutes |
| Scope and Default Parameters | 15 minutes |
| Guided Practical | 25 minutes |
| Knowledge Check | 10 minutes |
| **Total** | **120 minutes** |

---

## 1. Review of Week 6 — 10 Minutes

Review:

- Lists
- Dictionaries
- Loops
- Conditional statements
- Student Score Analyser

### Discussion

Suppose our program calculates the average score for several different classes.

Should we rewrite the same calculation every time?

How can we make the calculation reusable?

---

## 2. Introduction to Functions — 20 Minutes

A function is a reusable block of code designed to perform a specific task.

### Basic Function

```python
def greet():
    print("Welcome to Python programming!")
```

### Calling a Function

```python
greet()
```

### Function Structure

```python
def function_name():
    # Instructions
    pass
```

Explain:

- `def`
- Function names
- Parentheses
- Colon
- Indentation
- Function calls

### Why Use Functions?

- Reduce repetition
- Improve readability
- Organise programs
- Simplify testing
- Make maintenance easier

---

## 3. Parameters and Arguments — 20 Minutes

Functions can accept information.

### Example

```python
def greet_student(name):
    print(f"Hello, {name}!")

greet_student("Uzoamaka")
greet_student("Ada")
```

### Multiple Parameters

```python
def calculate_total(price, quantity):
    total = price * quantity
    print(total)

calculate_total(2500, 3)
```

### Discussion

What is the difference between a parameter and an argument?

---

## 4. Return Values — 20 Minutes

Functions can return results to the code that calls them.

### Example

```python
def add_numbers(a, b):
    return a + b

result = add_numbers(10, 5)

print(result)
```

### `print()` vs `return`

```python
def show_total(a, b):
    print(a + b)

def calculate_total(a, b):
    return a + b
```

Explain:

- `print()` displays information.
- `return` sends a value back to the caller.

### Practical Example

```python
def calculate_average(scores):
    return sum(scores) / len(scores)

scores = [70, 80, 90]

average = calculate_average(scores)

print(f"Average: {average:.2f}")
```

Discuss why this example requires a non-empty list.

---

## 5. Scope and Default Parameters — 15 Minutes

### Local Variables

```python
def greet():
    message = "Hello!"
    print(message)

greet()
```

Explain that `message` is local to the function.

### Global Variables

```python
school = "Example Secondary School"

def display_school():
    print(school)

display_school()
```

Explain the difference between reading a global value and modifying it.

Encourage passing information through parameters rather than relying unnecessarily on global variables.

### Default Parameters

```python
def greet(name="Student"):
    print(f"Hello, {name}!")

greet()
greet("Uzoamaka")
```

---

## 6. Guided Practical — 25 Minutes

### Exercise 1: Reusable Calculator

Create:

`function_calculator.py`

### Requirements

Write separate functions for:

1. Addition
2. Subtraction
3. Multiplication
4. Division

### Example

```python
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def multiply(a, b):
    return a * b

def divide(a, b):
    if b == 0:
        return None
    return a / b
```

### Student Task

Create a menu allowing the user to select an operation.

Use conditional statements to call the appropriate function.

---

## 7. Knowledge Check — 10 Minutes

1. What is a function?
2. Why do programmers use functions?
3. What does `def` mean?
4. What is a parameter?
5. What is an argument?
6. What does `return` do?
7. What is the difference between `print()` and `return`?
8. What is local scope?

---

# 📝 SESSION 1 ASSIGNMENT

## Student Grade Functions

Create:

`grade_functions.py`

### Requirements

Create the following functions:

- `calculate_average(scores)`
- `determine_grade(score)`
- `check_pass_status(score)`
- `display_student_report(name, scores)`

### Functional Requirements

The program should:

1. Accept a student's name.
2. Store at least three examination scores.
3. Calculate the average.
4. Determine the grade.
5. Determine Pass or Fail.
6. Display a formatted report.

### Expected Deliverable

A functional Python application organised into reusable functions.

---

# 🗓️ SESSION 2 — MODULAR PROGRAMMING & DEBUGGING

**Duration:** 2 Hours

## Session Breakdown

| Activity | Duration |
|---|---:|
| Assignment Review | 15 minutes |
| DRY Principle and Refactoring | 20 minutes |
| Python Modules and Imports | 25 minutes |
| Understanding Programming Errors | 20 minutes |
| Debugging Techniques | 25 minutes |
| Knowledge Check | 15 minutes |
| **Total** | **120 minutes** |

---

## 1. Assignment Review — 15 Minutes

Review:

- Function definitions
- Parameters
- Return values
- Function calls
- Program organisation
- Correct calculations

---

## 2. DRY Principle & Refactoring — 20 Minutes

DRY means:

**Don't Repeat Yourself.**

The principle encourages programmers to avoid unnecessary duplication.

### Repetitive Code

```python
print("Welcome, Ada!")
print("Welcome, Chidi!")
print("Welcome, Uzoamaka!")
```

### Refactored Code

```python
def welcome_student(name):
    print(f"Welcome, {name}!")

students = ["Ada", "Chidi", "Uzoamaka"]

for student in students:
    welcome_student(student)
```

### What is Refactoring?

Refactoring means improving the internal structure of code without intentionally changing its observable behaviour.

### Discussion

How can functions make a program easier to maintain?

---

## 3. Introduction to Modules — 25 Minutes

A module is a Python file containing reusable code.

### Example Structure

```text
calculator/
│
├── main.py
└── operations.py
```

### `operations.py`

```python
def add(a, b):
    return a + b

def multiply(a, b):
    return a * b
```

### `main.py`

```python
from operations import add, multiply

print(add(5, 3))
print(multiply(5, 3))
```

### Discussion

Why separate program functionality into different files?

Explain:

- Code organisation
- Reusability
- Separation of concerns
- Maintainability

---

## 4. Understanding Programming Errors — 20 Minutes

Introduce three common error categories.

### Syntax Errors

```python
print("Hello"
```

The statement is missing a closing parenthesis.

### Runtime Errors

```python
number = 10 / 0
```

This raises a `ZeroDivisionError`.

### Logic Errors

```python
price = 100
quantity = 3

total = price + quantity

print(total)
```

The code runs but produces an incorrect total.

### Discussion

Why can logic errors be more difficult to identify?

---

## 5. Debugging Techniques — 25 Minutes

Debugging is the process of locating and correcting defects in a program.

### Technique 1 — Read Error Messages

Examine the traceback and identify:

- Error type
- File name
- Line number
- Relevant code

### Technique 2 — Use Print Statements

```python
price = 2500
quantity = 3

print("Price:", price)
print("Quantity:", quantity)

total = price * quantity

print("Total:", total)
```

### Technique 3 — Test Small Sections

Run individual functions to confirm expected behaviour.

### Technique 4 — Use the VS Code Debugger

Introduce:

- Breakpoints
- Step Over
- Variable inspection
- Debug Console

### Guided Debugging Exercise

```python
def calculate_average(scores):
    total = sum(scores)
    average = total / len(scores)
    return average

scores = []

print(calculate_average(scores))
```

### Student Task

1. Run the code.
2. Identify the error.
3. Explain why it occurs.
4. Modify the function to handle an empty list.

---

## 6. Knowledge Check — 15 Minutes

1. What does DRY mean?
2. What is refactoring?
3. What is a module?
4. What does `import` do?
5. What is a syntax error?
6. What is a runtime error?
7. What is a logic error?
8. What is debugging?
9. What is a breakpoint?
10. Why should programmers test individual functions?

---

# 📝 SESSION 2 ASSIGNMENT

## Modular Student Grade Calculator

Refactor the previous Student Grade Calculator into separate modules.

### Suggested Structure

```text
student-grade-calculator/
│
├── main.py
├── calculations.py
└── reports.py
```

### Requirements

**`calculations.py`**

Contains functions for:

- Calculating averages
- Determining grades
- Checking pass status

**`reports.py`**

Contains functions for:

- Displaying student information
- Formatting reports

**`main.py`**

Responsible for:

- Accepting input
- Calling functions
- Displaying results

### Deliverable

A modular Python application with at least three source files.

---

# 🗓️ SESSION 3 — EXCEPTION HANDLING, FILE OPERATIONS & WEEKLY PROJECT

**Duration:** 2 Hours

## Session Breakdown

| Activity | Duration |
|---|---:|
| Assignment Review | 15 minutes |
| Exception Handling | 20 minutes |
| Input Validation | 15 minutes |
| Introduction to File Handling | 15 minutes |
| Guided Practical | 20 minutes |
| Weekly Project Development | 25 minutes |
| Project Review | 10 minutes |
| **Total** | **120 minutes** |

---

## 1. Assignment Review — 15 Minutes

Review the modular grade calculator.

Discuss:

- Separation of concerns
- Imports
- Function reuse
- Code organisation
- Debugging

---

## 2. Exception Handling — 20 Minutes

Python provides `try` and `except` for handling certain runtime errors.

### Example

```python
try:
    age = int(input("Enter your age: "))
    print(f"Age: {age}")
except ValueError:
    print("Please enter a valid number.")
```

### Handling Division by Zero

```python
try:
    a = float(input("First number: "))
    b = float(input("Second number: "))

    result = a / b

    print(result)

except ValueError:
    print("Invalid numeric input.")

except ZeroDivisionError:
    print("Cannot divide by zero.")
```

### Discussion

Why should programs handle expected errors?

---

## 3. Input Validation — 15 Minutes

Input validation ensures that information meets program requirements.

### Example

```python
def get_positive_amount():
    while True:
        try:
            amount = float(input("Enter amount: "))

            if amount > 0:
                return amount

            print("Amount must be greater than zero.")

        except ValueError:
            print("Please enter a valid number.")
```

Explain:

- Repeated prompting
- Positive-number validation
- Exception handling
- Returning valid input

---

## 4. Introduction to File Handling — 15 Minutes

Programs can write information to files and read it later.

### Writing to a File

```python
with open("notes.txt", "w", encoding="utf-8") as file:
    file.write("Welcome to Python file handling.")
```

### Reading from a File

```python
with open("notes.txt", "r", encoding="utf-8") as file:
    content = file.read()

print(content)
```

### Appending to a File

```python
with open("notes.txt", "a", encoding="utf-8") as file:
    file.write("\nNew information added.")
```

Explain:

- `"r"` — Read
- `"w"` — Write
- `"a"` — Append
- `with` — Automatic resource management

### Note

File handling is introduced briefly here.

Database persistence will be explored in Week 10.

---

## 5. Guided Practical — 20 Minutes

### Exercise 3: Expense Recorder

Create:

`expense_recorder.py`

### Requirements

1. Ask for an expense description.
2. Ask for an expense amount.
3. Validate the amount.
4. Store the expense in a dictionary.
5. Add the dictionary to a list.
6. Display the recorded expense.

### Example

```python
expenses = []

description = input("Expense description: ")
amount = float(input("Expense amount: "))

expense = {
    "description": description,
    "amount": amount
}

expenses.append(expense)

print(expenses)
```

### Student Extension

Convert the recording process into a reusable function.

---

# 🏆 WEEK 7 PROJECT — MODULAR EXPENSE TRACKER

## Project Overview

Develop a Python command-line application that allows users to record, view and analyse expenses.

The project should demonstrate functions, modular programming, lists, dictionaries, loops, validation and basic debugging.

---

## Functional Requirements

The application must:

1. Display a welcome message.
2. Display a menu of available operations.
3. Allow users to add an expense.
4. Allow users to view recorded expenses.
5. Calculate the total expenses.
6. Display the number of recorded expenses.
7. Identify the highest expense.
8. Validate expense amounts.
9. Handle invalid numeric input.
10. Allow users to exit the application.

### Example Menu

```text
====================================
          EXPENSE TRACKER
====================================

1. Add Expense
2. View Expenses
3. Calculate Total
4. Show Highest Expense
5. Exit

Select an option:
```

---

## Technical Requirements

Use:

- Functions
- Parameters
- Return values
- Lists
- Dictionaries
- `while` loops
- Conditional statements
- `try` and `except`
- Meaningful variable names
- Modular source files

---

## Suggested Functions

```python
def display_menu():
    pass

def add_expense(expenses):
    pass

def view_expenses(expenses):
    pass

def calculate_total(expenses):
    pass

def find_highest_expense(expenses):
    pass
```

The student should implement the functions independently.

---

## Suggested Project Structure

```text
Week-07/
│
├── exercises/
│   ├── function_calculator.py
│   ├── debugging_practice.py
│   └── expense_recorder.py
│
├── assignments/
│   ├── grade_functions.py
│   └── modular-grade-calculator/
│       ├── main.py
│       ├── calculations.py
│       └── reports.py
│
└── projects/
    └── expense-tracker/
        ├── main.py
        ├── expenses.py
        ├── utils.py
        └── README.md
```

---

## Suggested Module Responsibilities

### `main.py`

Handles:

- Main application loop
- User menu
- User selections
- Calling other functions

### `expenses.py`

Handles:

- Adding expenses
- Viewing expenses
- Calculating totals
- Finding highest expenses

### `utils.py`

Handles:

- Input validation
- Reusable helper functions

---

## Example Output

```text
====================================
          EXPENSE TRACKER
====================================

1. Add Expense
2. View Expenses
3. Calculate Total
4. Show Highest Expense
5. Exit

Select an option: 1

Expense Description: Transport
Amount: 2500

Expense added successfully!

------------------------------------

Select an option: 1

Expense Description: Lunch
Amount: 3500

Expense added successfully!

------------------------------------

Select an option: 3

Total Expenses: NGN 6000.00

------------------------------------

Select an option: 4

Highest Expense: Lunch
Amount: NGN 3500.00

------------------------------------

Select an option: 5

Goodbye!
```

---

# 🧪 Suggested Test Cases

| Test | Expected Result |
|---|---|
| Add a valid expense | Expense is recorded |
| Enter a negative amount | Input is rejected |
| Enter text instead of a number | Error message is displayed |
| View expenses when none exist | Friendly empty-list message |
| Calculate total with no expenses | Total is zero |
| Add multiple expenses | All expenses are displayed |
| Find highest expense | Largest recorded expense is identified |
| Enter an invalid menu option | Appropriate message is displayed |
| Select Exit | Application terminates |

---

# 🧠 Week 7 Knowledge Check

1. What is a function?
2. What does `def` do?
3. What is a parameter?
4. What is an argument?
5. What is a return value?
6. What is the difference between `print()` and `return`?
7. What is local scope?
8. What is global scope?
9. What is a default parameter?
10. What does DRY mean?
11. What is refactoring?
12. What is modular programming?
13. What is a Python module?
14. What does `import` do?
15. What is debugging?
16. What is a syntax error?
17. What is a runtime error?
18. What is a logic error?
19. What does `try` do?
20. What does `except` do?
21. What is input validation?
22. What is a traceback?
23. What is a breakpoint?
24. What is file handling?
25. Why is modular code easier to maintain?

---

# 📊 Week 7 Assessment

| Assessment Area | Weight |
|---|---:|
| Understanding functions | 20% |
| Parameters and return values | 15% |
| Modular programming | 20% |
| Debugging and error handling | 15% |
| Input validation | 10% |
| Code organisation | 10% |
| Weekly project completion | 10% |
| **Total** | **100%** |

---

# 📦 Week 7 Deliverables

- Reusable Calculator
- Student Grade Functions
- Modular Student Grade Calculator
- Debugging Exercises
- Expense Recorder
- Modular Expense Tracker
- Week 7 Knowledge Check
- GitHub commits and project documentation

---

# 🎓 Expected Learning Outcomes

By the end of Week 7, the student should be able to:

- Write reusable Python functions.
- Pass arguments and return values.
- Understand variable scope.
- Refactor repetitive code.
- Organise Python programs into modules.
- Import and reuse functionality.
- Read and interpret common error messages.
- Debug simple programs.
- Handle expected runtime errors.
- Validate user input.
- Perform basic file operations.
- Build a modular command-line application.

---

## ⏭️ Next Module

**Week 8 — Object-Oriented Programming (OOP)**

The student will explore:

- Classes and objects
- Attributes and methods
- Constructors
- Instance variables
- Encapsulation
- Introductory inheritance

The Week 8 project will involve creating a basic Student Management System using Python classes.

---

<div align="center">

### 🚀 Building Strong Programming Foundations

**Opsfuxion Technologies Limited**

*Orchestrate Intelligence, Deliver with Precision.*

© 2026 Opsfuxion Technologies Limited.

</div>
