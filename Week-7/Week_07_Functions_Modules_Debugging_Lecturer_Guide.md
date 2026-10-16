# WEEK 7 — FUNCTIONS, MODULAR PROGRAMMING, DEBUGGING & ERROR HANDLING

**Opsfuxion Technologies Limited**  
*Orchestrate Intelligence, Deliver with Precision.*

**Practical Software Engineering Foundation Programme | Lecturer's Complete Teaching Manual**  
**Level:** Beginner | **Contact time:** 3 × 120 minutes = 6 hours | **Independent practice:** 6–10 hours  
**Student:** Uzoamaka | **Format:** instructor-led, code-along, independent lab, review

> **INSTRUCTOR EDITION:** Student tasks and model solutions appear together for ease of teaching. Share only the tasks before the student attempts them. The examples use Python 3. Do not assume a concept has been mastered because a learner can copy working code.

**Teaching rhythm:** Explain in plain language → draw or predict → live-code → student modifies → test boundaries → discuss why → commit.

## Instructor preparation and learning outcomes

**Prerequisite:** Week 6 lists, dictionaries, loops and score analyser. **Scope:** functions, parameters, return values, scope, default arguments, modules/imports, DRY/refactoring, syntax/runtime/logic errors, VS Code debugging, `try/except`, input validation and introductory text file persistence. OOP comes in Week 8 and databases in Week 10.

**Outcomes:** Design small reusable functions; distinguish `return` from `print`; pass parameters; explain local scope; organise code across modules; trace bugs; use breakpoints; catch expected exceptions; read/write/append text files; build a modular Expense Tracker and refactor Week 6's Score Analyser.

**Preparation:** Create `Week-07/{exercises,assignments,projects}`. Keep a clean Python environment and working VS Code debugger. Make a deliberately broken file to practise debugging. Avoid showing instructor solutions before attempts.

---

# SESSION 1 — FUNCTIONS, PARAMETERS, RETURN VALUES & SCOPE (120 MIN)

| Minutes | Activity | Lecturer action |
|---|---|---|
| 0–15 | Review Week 6 | Score analyser walkthrough |
| 15–35 | Why functions? | Duplicate code problem |
| 35–60 | Define/call, parameters | Live examples |
| 60–80 | Return vs print, scope | Predict output |
| 80–105 | Guided calculator | Independent modifications |
| 105–115 | Debugging | Common mistakes |
| 115–120 | Exit ticket | Explain one function |

## Lecture 1.1 — Why functions?

**Say:** “A function names a small, reusable operation. We can test it independently and call it whenever needed.” Contrast repeated calculation with a single function.

```python
def calculate_total(price, quantity):
    return price * quantity

print(calculate_total(500, 3))
print(calculate_total(1200, 2))
```

**Vocabulary:** `def` defines; function name describes behaviour; **parameters** are placeholders in definition; **arguments** are values passed during call; `return` sends a value back to caller.

### Parameter vs argument

```python
def greet(name):        # name is parameter
    return f"Hello, {name}!"

message = greet("Ada")  # "Ada" is argument
print(message)
```

### Return vs print

```python
def printed_double(number):
    print(number * 2)

def returned_double(number):
    return number * 2

x = printed_double(5)   # prints 10; x is None
z = returned_double(5)  # z is 10
print(x, z)
```

**Ask:** Which version can be reused in another calculation? Returned value.

### Default arguments

```python
def welcome(name, course="Python"):
    return f"Welcome {name} to {course}"

print(welcome("Ada"))
print(welcome("Uzoamaka", "Software Engineering"))
```

### Local scope

```python
def calculate_discount(price):
    discount = price * 0.1
    return price - discount

print(calculate_discount(1000))
# print(discount)  # NameError: local variable outside function
```

**Instructor note:** Avoid mutable default arguments (`def f(items=[])`) for beginner examples; explain why this can lead to surprising shared state if asked.

## Guided lab 1 — Reusable calculator

**STUDENT TASK:** Write `add`, `subtract`, `multiply` and `divide` functions. Each returns a result. `divide` must avoid division by zero. Build a simple menu or direct function calls to demonstrate them.

### INSTRUCTOR SOLUTION

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

print(add(4, 3))       # 7
print(subtract(4, 3))  # 1
print(multiply(4, 3))  # 12
result = divide(4, 0)
print("Cannot divide by zero" if result is None else result)
```

**Teaching prompt:** Why return `None` instead of printing from inside the function? It separates computation from presentation; caller decides message.

## Debugging demonstration

```python
def square(number):
    result = number * number
    # forgot return

print(square(4))  # None
```

**Ask:** Why did the function not produce 16? It computed but did not return the result. Fix with `return result`.

### Homework 1 — Student Grade Functions

**STUDENT TASK:** Implement four reusable functions: `calculate_average(scores)`, `determine_grade(average)`, `check_pass_status(average)` and `display_student_report(name, scores)`. Use A≥70, B≥60, C≥50, F<50. Handle an empty score list without crashing. Test 0, 50, 70, 100 and empty list.

### INSTRUCTOR SOLUTION

```python
def calculate_average(scores):
    return sum(scores) / len(scores) if scores else None

def determine_grade(average):
    if average is None:
        return "N/A"
    if average >= 70:
        return "A"
    if average >= 60:
        return "B"
    if average >= 50:
        return "C"
    return "F"

def check_pass_status(average):
    if average is None:
        return "NO SCORES"
    return "PASS" if average >= 50 else "FAIL"

def display_student_report(name, scores):
    average = calculate_average(scores)
    print("Student:", name)
    print("Average:", f"{average:.2f}" if average is not None else "N/A")
    print("Grade:", determine_grade(average))
    print("Status:", check_pass_status(average))

display_student_report("Uzoamaka", [80, 90, 70])
display_student_report("Ada", [])
```

**Instructor note:** `display_student_report` intentionally prints; the calculation functions return values. This is a useful separation of responsibilities.

---

# SESSION 2 — MODULAR PROGRAMMING, REFACTORING & DEBUGGING (120 MIN)

| Minutes | Activity | Lecturer action |
|---|---|---|
| 0–15 | Assignment review | Check boundaries |
| 15–35 | DRY and refactoring | Spot repeated logic |
| 35–60 | Modules and imports | Multi-file demo |
| 60–85 | Error categories and tracebacks | Deliberately break code |
| 85–110 | VS Code debugger lab | Breakpoint, step, inspect |
| 110–120 | Exit ticket | Explain diagnosis |

## Lecture 2.1 — DRY and modularity

**DRY:** Don't Repeat Yourself. Avoid duplicating knowledge/logic unnecessarily. A **module** is a Python file that can expose reusable functions and variables. **Refactoring** improves internal structure while preserving observable behaviour.

**Say:** “Our Week 6 score analyser works, but it mixes input, calculation and display. Breaking it into small functions makes it easier to test.”

### Before refactoring

```python
print(sum([60, 70]) / len([60, 70]))
print(sum([80, 90]) / len([80, 90]))
```

### After refactoring

```python
def average(scores):
    return sum(scores) / len(scores) if scores else None

print(average([60, 70]))
print(average([80, 90]))
```

## Lecture 2.2 — Modules and imports

Create this directory:

```text
student_grade_calculator/
├── main.py
├── calculations.py
└── reports.py
```

**`calculations.py`**

```python
def calculate_average(scores):
    return sum(scores) / len(scores) if scores else None

def determine_grade(average):
    if average is None:
        return "N/A"
    if average >= 70:
        return "A"
    if average >= 60:
        return "B"
    if average >= 50:
        return "C"
    return "F"
```

**`reports.py`**

```python
from calculations import calculate_average, determine_grade

def show_report(name, scores):
    avg = calculate_average(scores)
    grade = determine_grade(avg)
    print(f"Student: {name}")
    print("Average:", f"{avg:.2f}" if avg is not None else "N/A")
    print("Grade:", grade)
```

**`main.py`**

```python
from reports import show_report

if __name__ == "__main__":
    show_report("Uzoamaka", [75, 85, 90])
```

Run from the project directory: `python3 main.py` (Windows: `py main.py`). Explain import lookup and why filenames must match. `if __name__ == '__main__'` makes the script entry point explicit.

## Lecture 2.3 — Errors and tracebacks

| Category | Example | How to diagnose |
|---|---|---|
| Syntax error | Missing `:` | Read parser message and line |
| Runtime error | `10 / 0` | Inspect traceback and values |
| Logic error | `total / 2` for 3 scores | Compare actual vs expected result |

**Say:** “A traceback is a trail of where execution failed. Read the exception type and the bottommost relevant application line first.”

### Deliberately broken function

```python
def average(scores):
    return sum(scores) / len(scores)

print(average([]))  # ZeroDivisionError
```

**Fix:** `return sum(scores)/len(scores) if scores else None`.

### VS Code debugger walkthrough

1. Open `main.py`.
2. Click beside a line number to set a breakpoint.
3. Choose **Run and Debug** (Python File).
4. Inspect Variables pane.
5. Step Over to advance line by line.
6. Observe how `avg` changes.
7. Remove breakpoint and rerun.

**Student must explain:** what a breakpoint does, what value was observed, and which condition caused the behaviour.

## Guided lab 2 — Refactor the Week 6 analyser

**STUDENT TASK:** Extract `calculate_average`, `count_passes`, and `display_report` from the existing program. Preserve the same output for the sample data. Put calculations in `calculations.py`, report in `reports.py`, and calls in `main.py`.

### INSTRUCTOR SOLUTION

**`calculations.py`**

```python
def calculate_average(students):
    if not students:
        return None
    return sum(s["score"] for s in students) / len(students)

def count_passes(students):
    return sum(1 for s in students if s["score"] >= 50)
```

**`reports.py`**

```python
from calculations import calculate_average, count_passes

def display_report(students):
    for student in students:
        print(student["name"], student["score"])
    avg = calculate_average(students)
    print("Average:", f"{avg:.2f}" if avg is not None else "N/A")
    print("Passes:", count_passes(students))
```

**`main.py`**

```python
from reports import display_report

students = [
    {"name": "Ada", "score": 80},
    {"name": "Chidi", "score": 40},
]

if __name__ == "__main__":
    display_report(students)
```

**Instructor test:** empty list → `Average: N/A`, `Passes: 0`; original data → average 60, passes 1.

### Homework 2 — Modular Grade Calculator

**STUDENT TASK:** Deliver `main.py`, `calculations.py`, `reports.py`; use at least three named functions; document run command and two test cases in README.

**INSTRUCTOR SOLUTION:** The complete multi-file implementation above plus a README containing `python3 main.py`, sample output, and tests for normal/empty records is an acceptable reference. Ask student to implement a different dataset independently.

---

# SESSION 3 — EXCEPTIONS, FILE HANDLING & EXPENSE TRACKER (120 MIN)

| Minutes | Activity | Lecturer action |
|---|---|---|
| 0–15 | Assignment review | Run all modules |
| 15–35 | `try`/`except` | Handle expected errors |
| 35–55 | Validation patterns | Positive amount and menus |
| 55–75 | Files | `with open`, read/write/append |
| 75–105 | Expense tracker project | Build core features |
| 105–115 | Test and review | Empty/invalid cases |
| 115–120 | Exit ticket | Explain exception and persistence |

## Lecture 3.1 — Exception handling

An **exception** signals a problem encountered during execution. Catch expected exceptions at the point where the program can recover meaningfully.

```python
try:
    age = int(input("Age: "))
    print("Next year:", age + 1)
except ValueError:
    print("Please enter a whole number")
```

**Contrast:** Catching `ValueError` is more precise than a blanket `except:` that hides programming errors.

### Reusable input validation

```python
def read_positive_amount():
    while True:
        try:
            amount = float(input("Amount (₦): "))
            if amount > 0:
                return amount
            print("Amount must be greater than zero")
        except ValueError:
            print("Enter a numeric amount")
```

**Discuss:** A negative number is a valid float but an invalid expense. Type validation and business-rule validation are different.

## Lecture 3.2 — File handling

**Say:** “Lists disappear when the program exits. A text file can preserve simple information between runs. SQLite will provide more structured storage in Week 10.”

```python
with open("notes.txt", "w", encoding="utf-8") as file:
    file.write("First note\n")

with open("notes.txt", "a", encoding="utf-8") as file:
    file.write("Second note\n")

with open("notes.txt", "r", encoding="utf-8") as file:
    print(file.read())
```

`w` overwrites; `a` appends; `r` reads. `with` closes the file automatically. Use UTF-8 for Nigerian naira symbol and other Unicode characters. Reading a missing file raises `FileNotFoundError`.

### Safe file read

```python
try:
    with open("notes.txt", "r", encoding="utf-8") as file:
        print(file.read())
except FileNotFoundError:
    print("No notes file yet")
```

## Guided lab 3 — Expense Recorder

**STUDENT TASK:** Ask for a category and positive amount, append to a text file and display a confirmation. Then read back the file. Validate empty category and numeric amount.

### INSTRUCTOR SOLUTION

```python
category = input("Category: ").strip()
if not category:
    print("Category required")
else:
    try:
        amount = float(input("Amount: "))
        if amount <= 0:
            print("Amount must be positive")
        else:
            with open("expenses.txt", "a", encoding="utf-8") as file:
                file.write(f"{category}: {amount:.2f}\n")
            print("Expense recorded")
    except ValueError:
        print("Invalid amount")

try:
    with open("expenses.txt", "r", encoding="utf-8") as file:
        print(file.read())
except FileNotFoundError:
    print("No expenses yet")
```

**Explain limitation:** This introductory text format is good for reading, but awkward for reliable calculations if categories contain delimiters. The main weekly project below stores expenses in memory and may optionally persist via JSON. Do not claim it is a database.

# WEEKLY PROJECT — MODULAR EXPENSE TRACKER

## Student brief

Build a command-line Expense Tracker with a menu:

1. Add expense (category and positive amount)
2. View expenses
3. View total
4. View highest expense
5. Exit

**Must use:** `main.py`, `expenses.py`, `utils.py`; reusable functions; lists of dictionaries; `try/except ValueError`; clear error messages; empty-list handling. **Optional extension:** save/load expenses using a file, with explicit instructions on limitations.

**Instructor coaching:** Let learner outline function names and data shape first. Avoid writing the entire solution for them. Allocate more independent time outside the six contact hours if needed.

## INSTRUCTOR COMPLETE MULTI-FILE SOLUTION

### `utils.py`

```python
def read_positive_amount():
    while True:
        try:
            amount = float(input("Amount (₦): "))
        except ValueError:
            print("Please enter a number")
            continue
        if amount <= 0:
            print("Amount must be greater than zero")
            continue
        return amount
```

### `expenses.py`

```python
def add_expense(expenses, category, amount):
    expenses.append({"category": category, "amount": amount})

def total_expenses(expenses):
    return sum(item["amount"] for item in expenses)

def highest_expense(expenses):
    if not expenses:
        return None
    return max(expenses, key=lambda item: item["amount"])

def display_expenses(expenses):
    if not expenses:
        print("No expenses recorded")
        return
    for index, item in enumerate(expenses, start=1):
        print(f"{index}. {item['category']}: ₦{item['amount']:,.2f}")
```

**Instructor explanation:** `max(..., key=...)` selects the record with the greatest `amount`. It is a small preview of passing functions as values; alternatively use a `for` loop to find the maximum if the student is not ready for `lambda`.

### `main.py`

```python
from expenses import (
    add_expense, total_expenses, highest_expense, display_expenses
)
from utils import read_positive_amount


def main():
    expenses = []
    while True:
        print("\n=== EXPENSE TRACKER ===")
        print("1. Add expense")
        print("2. View expenses")
        print("3. View total")
        print("4. Highest expense")
        print("5. Exit")
        choice = input("Choose 1-5: ").strip()

        if choice == "1":
            category = input("Category: ").strip()
            if not category:
                print("Category is required")
                continue
            amount = read_positive_amount()
            add_expense(expenses, category, amount)
            print("Expense added")
        elif choice == "2":
            display_expenses(expenses)
        elif choice == "3":
            print(f"Total: ₦{total_expenses(expenses):,.2f}")
        elif choice == "4":
            item = highest_expense(expenses)
            if item is None:
                print("No expenses recorded")
            else:
                print(f"Highest: {item['category']} — ₦{item['amount']:,.2f}")
        elif choice == "5":
            print("Goodbye!")
            break
        else:
            print("Invalid menu choice")


if __name__ == "__main__":
    main()
```

**Run:** `python3 main.py` (or `py main.py` on Windows).

**Important scope statement:** This required version stores expenses **in memory only**; they are lost after exit. Session 3's file recorder demonstrates persistence separately. To add optional project persistence, use the JSON extension below.

### Optional persistence extension — JSON

**`storage.py`**

```python
import json

FILENAME = "expenses.json"

def load_expenses():
    try:
        with open(FILENAME, "r", encoding="utf-8") as file:
            data = json.load(file)
        if not isinstance(data, list):
            raise ValueError("Expected a list")
        return data
    except FileNotFoundError:
        return []
    except (json.JSONDecodeError, ValueError):
        print("Expense file is invalid; starting with an empty list")
        return []

def save_expenses(expenses):
    with open(FILENAME, "w", encoding="utf-8") as file:
        json.dump(expenses, file, indent=2)
```

**Integration:** In `main.py`, import `load_expenses` and `save_expenses`; initialise `expenses = load_expenses()` and call `save_expenses(expenses)` after each successful addition. For a real application, also validate each loaded record and handle filesystem errors; this extension is deliberately introductory.

## Test matrix

| Test | Expected |
|---|---|
| View empty list | Friendly message |
| Total with no records | ₦0.00 |
| Highest with no records | Friendly message |
| Add Food ₦500 and Transport ₦700 | Total ₦1,200 |
| Highest of those records | Transport ₦700 |
| Enter `abc` as amount | Prompt again, no crash |
| Enter `0` or `-50` | Rejected, prompt again |
| Empty category | Rejected |
| Menu option 9 | Invalid choice |
| Exit | Program terminates |
| Restart (core version) | Data reset; expected limitation |
| Restart (JSON extension) | Data loaded if valid |

## Extra independent practice with solutions

**P1 — Return or print?** Write a function returning the square of a number.

```python
def square(n):
    return n * n
```

**P2 — Default argument:** Greet with optional title.

```python
def greet(name, title="Student"):
    return f"Hello, {title} {name}"
```

**P3 — Safe integer input:** Return `None` for invalid text.

```python
def parse_int(text):
    try:
        return int(text)
    except ValueError:
        return None
```

**P4 — File append:** Add a line without overwriting old lines.

```python
with open("log.txt", "a", encoding="utf-8") as file:
    file.write("New entry\n")
```

**P5 — Error classification:** `print(unknown)` is what kind of error? **Solution:** runtime `NameError`.

**P6 — Debugging:** Why does a function without `return` produce `None`? **Solution:** Python returns `None` implicitly.

**P7 — DRY:** Why extract score validation into a function? **Solution:** avoid repeated rules and make tests/changes consistent.

**P8 — Empty max:** Why must `max([])` be guarded? **Solution:** it raises `ValueError` because there is no item to select.

---

# Instructor assessment

| Criterion | Weight | Evidence |
|---|---:|---|
| Functions and parameters | 20% | Correct signatures/calls |
| Return values and scope | 15% | Reusable computations |
| Modules/refactoring | 20% | Separation of responsibilities |
| Debugging and tracebacks | 15% | Diagnosis and fix |
| Exceptions/validation | 15% | Safe numeric input |
| File handling | 5% | Read/write/append |
| Expense Tracker | 10% | Menu and required features |
| **Total** | **100%** | |

## Oral knowledge check (25 questions)

1. What is a function?
2. What does `def` do?
3. What is a parameter?
4. What is an argument?
5. What does `return` do?
6. How is `return` different from `print`?
7. What does a function return without `return`?
8. What is a default parameter?
9. What is local scope?
10. What is DRY?
11. What is refactoring?
12. What is a Python module?
13. What does `import` do?
14. Why use `if __name__ == '__main__'`?
15. What is a syntax error?
16. What is a runtime error?
17. What is a logic error?
18. What is a traceback?
19. What is a breakpoint?
20. What does `try` do?
21. What does `except ValueError` catch?
22. Why avoid bare `except:`?
23. What does `with open(...)` do?
24. Difference between `w` and `a` modes?
25. What happens to in-memory expenses when the program exits?

**Answer key:** These are directly answered in the lecture sections. Ask for explanations and examples, not memorised definitions. Questions 14 and 25 are especially useful to assess conceptual understanding.

## Common problems and fixes

| Symptom | Likely cause | Fix |
|---|---|---|
| `ModuleNotFoundError` | Wrong working directory or filename | Run from folder containing modules |
| `TypeError` on result | Function returned `None` | Check return paths |
| `ZeroDivisionError` | Empty list | Guard before dividing |
| `ValueError` on float | Non-numeric input | `try/except ValueError` |
| File unexpectedly erased | Used `w` not `a` | Explain overwrite vs append |
| Wrong expense total | Stored amount as string | Convert and validate float |
| Function works once only | Mutable shared state or bad scope | Inspect variable lifetime |
| Unexpected output | Logic error | Breakpoint and compare expected |

## Suggested deliverables

```text
Week-07/
├── exercises/
│   ├── reusable_calculator.py
│   ├── debugging_lab.py
│   └── expense_recorder.py
├── assignments/
│   ├── student_grade_functions.py
│   └── modular_grade_calculator/
│       ├── main.py
│       ├── calculations.py
│       └── reports.py
├── projects/
│   └── modular_expense_tracker/
│       ├── main.py
│       ├── expenses.py
│       ├── utils.py
│       ├── storage.py   # optional
│       └── README.md
└── README.md
```

## Instructor close-out checklist

- [ ] Learner explains parameter vs argument.
- [ ] Learner distinguishes `print` from `return`.
- [ ] Learner builds and imports multiple modules.
- [ ] Learner uses a breakpoint and interprets a traceback.
- [ ] Learner catches expected numeric conversion errors.
- [ ] Learner explains `r`, `w`, `a` file modes.
- [ ] Learner completes modular expense tracker and tests empty inputs.
- [ ] Learner refactors at least one Week 6 function and commits work.

**Transition to Week 8:** Next, organise related state and behaviour into classes and objects rather than managing every record only through separate functions.
