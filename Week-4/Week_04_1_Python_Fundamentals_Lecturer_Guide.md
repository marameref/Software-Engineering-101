# WEEK 4.1 — PYTHON PROGRAMMING FUNDAMENTALS

**Opsfuxion Technologies Limited**  
*Orchestrate Intelligence, Deliver with Precision.*

**Practical Software Engineering Foundation Programme | Lecturer's Complete Teaching Manual**  
**Level:** Beginner | **Contact time:** 3 × 120 minutes = 6 hours | **Independent practice:** 6–10 hours  
**Prerequisites:** Week 0 developer tools; Week 3 Git/GitHub helpful  
**Weekly products:** Interactive calculator and Student Profile Generator

> **Teaching convention:** Every **STUDENT TASK** is followed by an **INSTRUCTOR SOLUTION**. Hide solutions until the learner has attempted the task. Use a clean terminal and write every command live. This is Week 4 **Python Part 1**; functions, loops, modules, exceptions and OOP receive deeper treatment in later weeks.

---

# Lecturer setup and learning outcomes

## Before class

1. Verify Python 3: `python3 --version` on macOS/Linux or `py --version` on Windows (where installed). Do not assume the command is `python` on every machine.
2. Verify VS Code Python extension and a working integrated terminal.
3. Create `week-04-1-python/` with `exercises/`, `assignments/`, `projects/` and `README.md`.
4. Open the VS Code terminal in the project directory; run a `hello.py` file once.
5. Explain that Python is a programming language used in backend development, automation, data and many other domains; this week focuses on the fundamentals.
6. Prepare sample mistakes intentionally: unmatched quote, bad indentation, dividing by zero, using a string as a number.

## Measurable outcomes

The student can create/run `.py` files; explain variables and primitive types; use `print`, `input`, conversions, operators, string formatting, comparisons, Boolean logic and simple `if/elif/else`; build a calculator and profile generator; test boundary cases; use Git commits; and distinguish syntax/runtime/logic errors at a basic level.

## Instructional routine

- **Explain** a concept in ordinary language.
- **Demonstrate** the smallest working example.
- **Predict** output before execution.
- **Practise** by changing one thing.
- **Debug** a deliberately broken version.
- **Reflect** by having the student explain it back.

---

# SESSION 1 — PYTHON SETUP, VARIABLES, DATA TYPES & OUTPUT (120 MINUTES)

| Time | Activity | Lecturer cue |
|---|---|---|
| 0–15 | Environment and first script | Verify interpreter, run hello |
| 15–35 | Python syntax and comments | Indentation, case sensitivity, file execution |
| 35–60 | Variables and types | `str`, `int`, `float`, `bool`, `None` |
| 60–80 | `print`, formatting, strings | f-strings, escaping, basic methods |
| 80–105 | Guided practice | Student introduction script |
| 105–115 | Debugging exercise | Fix 3 errors |
| 115–120 | Exit ticket | Oral explanations |

## Lecture 1.1 — Your first Python program

Create `exercises/hello.py`:

```python
print('Hello, Uzoamaka!')
print('Welcome to Python programming.')
```

Run:

```bash
python3 exercises/hello.py
```

On Windows with Python launcher, `py exercises/hello.py` may be appropriate. Explain terminal current directory, file extension, source code vs output, and that a Python interpreter executes the code.

**Say:** “We write instructions in a text file. Python reads and executes them. When something is wrong, it gives an error message that helps us investigate.”

### Syntax and comments

```python
# This line is a comment.
print('Python is case-sensitive')
# Print('This fails')  # Python's function is named print, not Print.
```

Show that indentation is meaningful for code blocks, even though no complex blocks are required yet. Demonstrate that `print('hello')` is valid but `print('hello'` causes `SyntaxError`.

## Lecture 1.2 — Variables: labelled storage

```python
name = 'Uzoamaka'
age = 16
height = 1.65
is_student = True

print(name)
print(age)
print(height)
print(is_student)
```

**Explain:** A variable is a name bound to a value. `=` assigns; it does not mean mathematical equality. Values have types; Python determines them dynamically. Use descriptive snake_case names, not `a`, `b`, `x` in real examples.

```python
print(type(name))        # <class 'str'>
print(type(age))         # <class 'int'>
print(type(height))      # <class 'float'>
print(type(is_student))  # <class 'bool'>
```

Discuss `None` as absence of a value and `True`/`False` capitalization. Avoid teaching type annotations as a requirement this week.

### Predict and explain

```python
age = 16
age = age + 1
print(age)
```

**Answer:** `17`, because assignment updates the variable.

## Lecture 1.3 — Strings and output

```python
first_name = 'Uzoamaka'
course = 'Software Engineering'
print('Name:', first_name)
print(f'{first_name} is studying {course}.')
print('python'.upper())
print('  hello  '.strip())
print(len(first_name))
```

Explain string concatenation, f-strings, `len`, `upper`, `lower`, `strip`; avoid overloading with slicing until later. Show escaping quotes:

```python
print("It's my first Python class.")
print('She said, "Hello!"')
```

### STUDENT TASK 1A — Output prediction (8 minutes)

```python
name = 'Ada'
age = 17
print(f'{name} will be {age + 1} next year.')
print(type(age))
```

**INSTRUCTOR SOLUTION:** `Ada will be 18 next year.` and `<class 'int'>`. Ask why f-string expression `{age + 1}` works.

### STUDENT TASK 1B — Student introduction (17 minutes)

Create `exercises/student_intro.py` that prints name, age, school, favourite subject, and one goal. Use variables and an f-string.

**INSTRUCTOR SOLUTION:**

```python
name = 'Uzoamaka'
age = 16
school = 'Example College'
favourite_subject = 'Mathematics'
goal = 'Become a software engineer'

print('=== STUDENT INTRODUCTION ===')
print(f'Name: {name}')
print(f'Age: {age}')
print(f'School: {school}')
print(f'Favourite subject: {favourite_subject}')
print(f'Goal: {goal}')
```

**Extension:** print a two-line introduction with `\n` and change one variable to observe updated output.

## Debugging lab — Spot the mistakes (10 minutes)

```python
StudentName = 'Ada'
print(studentname)
print('I love Python)
age = '16'
print(age + 1)
```

**INSTRUCTOR SOLUTION:** `NameError` due to case mismatch; `SyntaxError` from missing closing quote; `TypeError` when adding `str` and `int`. Correct as:

```python
student_name = 'Ada'
print(student_name)
print('I love Python')
age = 16
print(age + 1)
```

### Session 1 homework — Personal Biography Generator

**Student-facing specification:** Use at least eight variables: first name, surname, age, school, favourite subject, hobby, location (fictional is fine), dream career. Print a neatly formatted biography with f-strings. Include two string operations and comments. Commit code with message `feat: add personal biography generator`.

**INSTRUCTOR SOLUTION:**

```python
first_name = 'Uzoamaka'
surname = 'Okafor'
age = 16
school = 'Example College'
subject = 'Mathematics'
hobby = 'Reading'
city = 'Abuja'
career = 'Software Engineer'

full_name = f'{first_name} {surname}'
print('=== MY BIOGRAPHY ===')
print(f'Full name: {full_name.title()}')
print(f'Age: {age}')
print(f'School: {school}')
print(f'Favourite subject: {subject}')
print(f'Hobby: {hobby.lower()}')
print(f'City: {city}')
print(f'Career goal: {career}')
```

**Marking (20 points):** eight variables 8, readable output 4, f-strings 3, string methods 2, comments 1, Git commit 2.

### Exit questions (answers)

1. What is a variable? **A name referring to a value.**
2. `str` vs `int`? **Text vs whole number.**
3. `=` means? **Assignment.**
4. What does `print()` do? **Writes output to console.**
5. Why f-strings? **Readable string interpolation.**

---

# SESSION 2 — INPUT, CONVERSIONS, OPERATORS & CONDITIONALS (120 MINUTES)

| Time | Activity | Lecturer cue |
|---|---|---|
| 0–15 | Homework review | Ask student to explain each variable |
| 15–35 | `input()` and conversions | Everything from `input` starts as text |
| 35–60 | Arithmetic and precedence | `+ - * / // % **`, parentheses |
| 60–80 | Comparison and Boolean operators | `== != > < >= <=`, `and/or/not` |
| 80–100 | `if/elif/else` | Grade/pass eligibility |
| 100–115 | Guided lab | Age eligibility checker |
| 115–120 | Exit ticket | Explain validation limitations |

## Lecture 2.1 — Interactive input

```python
name = input('What is your name? ').strip()
print(f'Welcome, {name}!')
```

**Say:** “`input()` returns a string, even if the user types digits.”

```python
age_text = input('How old are you? ')
print(type(age_text))
age = int(age_text)
print(f'Next year you will be {age + 1}.')
```

Show `int('16')` works, `int('sixteen')` raises `ValueError`. Explain that error handling with `try/except` is formally taught in Week 7; for now use controlled sample inputs and explain limitations. `float()` handles decimal numbers. Do not confuse `int(3.9)` (truncates toward zero) with rounding.

## Lecture 2.2 — Arithmetic operators

```python
x = 17
y = 5
print(x + y)   # 22
print(x - y)   # 12
print(x * y)   # 85
print(x / y)   # 3.4
print(x // y)  # 3
print(x % y)   # 2
print(x ** 2)  # 289
```

Explain `/` true division, `//` floor division, `%` remainder, `**` exponentiation. Mention negative floor division as a future nuance. Demonstrate precedence:

```python
print(2 + 3 * 4)    # 14
print((2 + 3) * 4)  # 20
```

### STUDENT TASK 2A — Predict calculations

1. `10 % 3` → **1**
2. `10 // 3` → **3**
3. `2 ** 4` → **16**
4. `6 + 2 * 3` → **12**
5. `(6 + 2) * 3` → **24**

Ask the student to explain *why*, not just give numbers.

## Lecture 2.3 — Comparisons and logic

```python
score = 50
print(score >= 50)             # True
print(score == 50)             # True
print(score != 50)             # False
print(score >= 0 and score <= 100)  # True
print(score < 0 or score > 100)     # False
print(not (score < 50))        # True
```

Explain Boolean expressions; `==` compares while `=` assigns. Show why Python uses `and` rather than JavaScript `&&`.

## Lecture 2.4 — Decisions with `if`, `elif`, `else`

```python
score = float(input('Enter score (0–100): '))

if score < 0 or score > 100:
    print('Invalid score')
elif score >= 70:
    print('Excellent')
elif score >= 50:
    print('Pass')
else:
    print('Fail')
```

**Teach:** Indentation defines a block; conditions are evaluated in order; only the first matching branch runs. Test -1, 0, 49, 50, 69, 70, 100, 101. Non-numeric input currently raises `ValueError` and is handled more robustly later.

## Guided lab — Age Eligibility Checker (15 minutes)

**STUDENT TASK:** Ask for name and age. Display `Eligible` if age is 16 or older, otherwise `Not yet eligible`. Reject negative ages and ages above 120 as invalid. Use an f-string.

**INSTRUCTOR SOLUTION:**

```python
name = input('Name: ').strip()
age = int(input('Age: '))

if not name:
    print('Name is required.')
elif age < 0 or age > 120:
    print('Invalid age.')
elif age >= 16:
    print(f'{name}: Eligible')
else:
    print(f'{name}: Not yet eligible')
```

**Ask:** What happens for `15`, `16`, `-2`, `121`? What if input is `sixteen`? Expected: last case raises `ValueError` until later error handling is introduced.

### Session 2 homework — Shopping Receipt Calculator

**STUDENT TASK:** Ask for product name, unit price and quantity; calculate subtotal, 7.5% *hypothetical classroom tax* and total. Display currency to two decimal places. Require price and quantity to be non-negative, and quantity to be a whole number. Do **not** present 7.5% as a statement of applicable Nigerian tax law; it is a practice constant.

**INSTRUCTOR SOLUTION:**

```python
product = input('Product name: ').strip()
unit_price = float(input('Unit price: '))
quantity = int(input('Quantity: '))
tax_rate = 0.075  # Hypothetical exercise rate

if not product or unit_price < 0 or quantity < 0:
    print('Invalid product, price or quantity.')
else:
    subtotal = unit_price * quantity
    tax = subtotal * tax_rate
    total = subtotal + tax
    print('=== RECEIPT ===')
    print(f'Product: {product}')
    print(f'Quantity: {quantity}')
    print(f'Subtotal: NGN {subtotal:,.2f}')
    print(f'Exercise tax: NGN {tax:,.2f}')
    print(f'Total: NGN {total:,.2f}')
```

**Marking (20 points):** input/conversion 5, arithmetic 5, validation 4, formatting 4, readable code 2.

### Exit questions (answers)

1. Type returned by `input()`? **`str`.**
2. Why `int()`? **Convert appropriate text to integer.**
3. Difference between `/` and `//`? **True division vs floor division.**
4. What is `%`? **Remainder operator.**
5. What does `elif` do? **Checks an additional condition if earlier branches fail.**

---

# SESSION 3 — PRACTICAL PROGRAMS: CALCULATOR & STUDENT PROFILE GENERATOR (120 MINUTES)

| Time | Activity | Lecturer cue |
|---|---|---|
| 0–15 | Review homework | Walk through calculations and formatting |
| 15–30 | Planning programs | Input → processing → output; pseudocode |
| 30–55 | Calculator guided build | Operators, branching, divide-by-zero |
| 55–75 | Profile generator guided build | String formatting, score/status |
| 75–100 | Independent project improvement | Add requirements without help |
| 100–112 | Test/debug/review | Run boundary tests and explain errors |
| 112–120 | Git submission and reflection | Commit and README |

## Lecture 3.1 — Plan before coding

**Say:** “Before writing Python, identify what goes in, what the program does, and what comes out.”

**Calculator:** inputs: two numbers and operator; processing: arithmetic and division safety; output: result or clear error.  
**Profile generator:** inputs: name, age, course, score; processing: validation and pass/fail; output: formatted report.

### Calculator pseudocode

```text
START
READ first number
READ operator
READ second number
IF operator is +, add
ELSE IF -, subtract
ELSE IF *, multiply
ELSE IF / and second number is not zero, divide
ELSE display an error
DISPLAY result when valid
END
```

Explain that pseudocode describes logic without language-specific syntax.

## Guided project A — Four-operation calculator

### STUDENT TASK (15 minutes)

Create `projects/calculator.py`. Requirements: ask for two numbers and operator (`+`, `-`, `*`, `/`); print result; reject unknown operator; prevent division by zero; format output clearly. The user may enter decimal numbers.

### INSTRUCTOR SOLUTION (complete)

```python
print('=== BASIC CALCULATOR ===')
first = float(input('First number: '))
operator = input('Operation (+, -, *, /): ').strip()
second = float(input('Second number: '))

if operator == '+':
    result = first + second
elif operator == '-':
    result = first - second
elif operator == '*':
    result = first * second
elif operator == '/':
    if second == 0:
        result = None
        print('Error: cannot divide by zero.')
    else:
        result = first / second
else:
    result = None
    print('Error: unsupported operation.')

if result is not None:
    print(f'Result: {first:g} {operator} {second:g} = {result:g}')
```

**Line-by-line teaching:** `float` converts decimal input; `.strip()` removes whitespace; `elif` selects one operation; nested `if` protects division; `None` is a sentinel meaning no valid result; `is not None` distinguishes a valid zero result from an error. `:g` displays numbers without unnecessary trailing zeros.

**Important limitation:** This version assumes numeric input. `float('abc')` raises `ValueError`; teach robust exception handling in Week 7, or offer it as an optional extension now.

### Calculator test table

| First | Operator | Second | Expected |
|---:|---|---:|---|
| 2 | + | 3 | 5 |
| 9 | - | 12 | -3 |
| 2.5 | * | 4 | 10 |
| 10 | / | 4 | 2.5 |
| 0 | + | 0 | 0 (valid) |
| 7 | / | 0 | Division-by-zero message |
| 2 | ^ | 3 | Unsupported-operation message |
| abc | + | 2 | `ValueError` (known limitation) |

## Guided project B — Student Profile Generator

### STUDENT TASK (15 minutes)

Create `projects/student_profile.py` that requests name, age, school, course and exam score; checks blank name/course, valid age (0–120), score (0–100); prints a formatted profile with PASS if score >= 50. Use f-strings and clear messages.

### INSTRUCTOR SOLUTION (complete)

```python
print('=== STUDENT PROFILE GENERATOR ===')
name = input('Full name: ').strip()
age = int(input('Age: '))
school = input('School: ').strip()
course = input('Course: ').strip()
score = float(input('Exam score (0–100): '))

if not name or not school or not course:
    print('Error: name, school and course are required.')
elif age < 0 or age > 120:
    print('Error: age must be between 0 and 120.')
elif score < 0 or score > 100:
    print('Error: score must be between 0 and 100.')
else:
    status = 'PASS' if score >= 50 else 'FAIL'
    print('\n' + '=' * 34)
    print('         STUDENT PROFILE')
    print('=' * 34)
    print(f'Name: {name.title()}')
    print(f'Age: {age}')
    print(f'School: {school}')
    print(f'Course: {course}')
    print(f'Score: {score:.2f}')
    print(f'Status: {status}')
    print('=' * 34)
```

**Explain:** `if ... else` conditional expression for status; `:.2f` formats to two decimals; `'=' * 34` repeats a string; `.title()` changes display capitalization (may not be appropriate for every real-world name, so keep raw name if preferred).

### STUDENT TASK 3A — Independent improvements (25 minutes)

1. Add favourite programming language to profile.
2. Add a `**` exponent operation to calculator.
3. For calculator, reject an empty operator.
4. Show a `DISTINCTION` label for score >= 80, `PASS` for 50–79.99 and `FAIL` below 50, but only after validating score.
5. Explain how the program behaves for score 79.99, 80, 100, 101.

### INSTRUCTOR SOLUTION — Minimal changes

```python
# Calculator, before unsupported-operation else:
elif operator == '**':
    result = first ** second

# Profile, replace status assignment:
if score >= 80:
    status = 'DISTINCTION'
elif score >= 50:
    status = 'PASS'
else:
    status = 'FAIL'
```

For favourite language, add `language = input('Favourite programming language: ').strip()` and print it in the valid-profile branch. Empty operator already enters unsupported-operation branch; improve its message to `Please choose an operation.` if requested.

### Final independent weekly assignment — Calculator + Profile package

**Deliverables:** both working `.py` programs, screenshots or copied terminal test results, `README.md`, at least three meaningful commits, and a one-paragraph explanation of input → processing → output for each.

**Student README template:**

```markdown
# Week 4.1 — Python Fundamentals

## What I learned
- Variables and data types
- User input and conversion
- Arithmetic and comparisons
- Conditional statements

## Projects
1. Calculator — four operations with divide-by-zero handling.
2. Student Profile Generator — collects and validates profile details.

## How to run
```bash
python3 projects/calculator.py
python3 projects/student_profile.py
```

## Tests performed
| Test | Expected | Actual | Pass/Fail |
|---|---|---|---|

## Limitations and next improvements
- Non-numeric input currently raises an error.
- Future weeks will introduce functions and exception handling.
```

**Lecturer note:** The nested code fence in this README template is meant as a separate fenced block in the actual README; use proper Markdown fencing when copying.

---

# Expanded practice bank (with solutions)

## Practice 1 — Convert minutes to hours and minutes

**STUDENT TASK:** Ask for non-negative integer minutes and display hours and remaining minutes. Example 135 → 2 hours, 15 minutes.

**INSTRUCTOR SOLUTION:**

```python
minutes = int(input('Total minutes: '))
if minutes < 0:
    print('Minutes cannot be negative.')
else:
    hours = minutes // 60
    remainder = minutes % 60
    print(f'{hours} hour(s), {remainder} minute(s)')
```

**Teaching point:** floor division and modulo solve different parts of the same problem.

## Practice 2 — Rectangle measurements

**STUDENT TASK:** Ask for width and height; print area and perimeter; reject negative dimensions.

**INSTRUCTOR SOLUTION:**

```python
width = float(input('Width: '))
height = float(input('Height: '))
if width < 0 or height < 0:
    print('Dimensions cannot be negative.')
else:
    print(f'Area: {width * height:.2f}')
    print(f'Perimeter: {2 * (width + height):.2f}')
```

## Practice 3 — Even or odd

**STUDENT TASK:** Ask for a whole number and determine parity.

**INSTRUCTOR SOLUTION:**

```python
number = int(input('Whole number: '))
if number % 2 == 0:
    print('Even')
else:
    print('Odd')
```

## Practice 4 — Compare two scores

**STUDENT TASK:** Ask for two scores, validate both 0–100, print which is higher or if tied.

**INSTRUCTOR SOLUTION:**

```python
first = float(input('First score: '))
second = float(input('Second score: '))
if not (0 <= first <= 100 and 0 <= second <= 100):
    print('Both scores must be between 0 and 100.')
elif first > second:
    print('First score is higher.')
elif second > first:
    print('Second score is higher.')
else:
    print('The scores are equal.')
```

## Practice 5 — Simple discount calculator

**STUDENT TASK:** Ask for purchase amount; apply 10% *fictional exercise discount* if amount >= 10000; print discount and final price.

**INSTRUCTOR SOLUTION:**

```python
amount = float(input('Purchase amount: '))
if amount < 0:
    print('Invalid amount.')
else:
    discount = amount * 0.10 if amount >= 10000 else 0
    print(f'Discount: NGN {discount:,.2f}')
    print(f'Final amount: NGN {amount - discount:,.2f}')
```

## Practice 6 — Debug and explain

**STUDENT TASK:** Find and fix the problems:

```python
age = input('Age: ')
if age >= 18
print('Adult')
else:
print('Minor')
```

**INSTRUCTOR SOLUTION:**

```python
age = int(input('Age: '))
if age >= 18:
    print('Adult')
else:
    print('Minor')
```

**Explain:** `input()` is text; comparisons require compatible types; colon after `if`; indentation after `if` and `else`. Input `'abc'` remains a known conversion limitation.

---

# Lecturer troubleshooting and misconceptions

| Student confusion | How to explain | Demonstration |
|---|---|---|
| `input()` gives a number | It always returns a string | `print(type(input('Age: ')))` |
| `=` is comparison | `=` assigns, `==` compares | `x = 5`; `x == 5` |
| `print` returns a result | `print` displays; return is later | `value = print('Hi')` is `None` |
| `16` and `'16'` are identical | Number vs text | `type(16)`, `type('16')` |
| Division by zero is fine | Arithmetic error | `5 / 0` |
| Indentation is decorative | It defines blocks | Misindent an `if` body |
| Zero result means error | Zero is a valid numeric result | Calculator `0 + 0` |
| `.title()` is mandatory | It's optional formatting | Compare original name |
| All user input is safe | Inputs can be blank/wrong type | `float('abc')` |
| Python and JS syntax match | Languages differ | `print` vs `console.log`; `and` vs `&&` |

## Debugging procedure for the lecturer

1. Read the last line of the traceback first.
2. Identify the file and line number.
3. State expected behaviour.
4. Reproduce with the smallest input.
5. Change one thing.
6. Rerun the failing case and one normal case.
7. Ask student to explain the fix.

## Safety and good habits

Use fictional student details in screenshots and public GitHub repositories. Do not commit passwords, access tokens or private personal information. Teach meaningful commit messages and `.gitignore`. Emphasise that input validation in this week is introductory; more robust handling comes in Week 7.

---

# Final knowledge assessment with answer key

1. What is Python? **General-purpose programming language.**
2. What is an interpreter? **Program that executes Python code.**
3. What is a `.py` file? **Python source file.**
4. What is a variable? **Name bound to a value.**
5. What is `str`? **Text type.**
6. What is `int`? **Integer type.**
7. What is `float`? **Floating-point numeric type.**
8. What is `bool`? **Boolean type.**
9. What is `None`? **Represents absence of a value.**
10. What does `print` do? **Outputs text/value.**
11. What does `input` return? **String.**
12. Why use `int`/`float`? **Convert appropriate input text to numbers.**
13. What is an f-string? **Formatted string with expressions.**
14. `=` vs `==`? **Assignment vs equality test.**
15. What is `%`? **Remainder.**
16. What is `//`? **Floor division.**
17. What is `**`? **Exponentiation.**
18. What is `if`? **Conditional execution.**
19. What is `elif`? **Additional conditional branch.**
20. What is `else`? **Fallback branch.**
21. What does `and` do? **True when both operands are truthy in a Boolean context.**
22. What does `or` do? **True when at least one operand is truthy in a Boolean context.**
23. What is `ValueError`? **An operation received an inappropriate value, e.g. `int('abc')`.**
24. What is `ZeroDivisionError`? **Attempt to divide by zero.**
25. Why test 49, 50, 100, 101? **Boundary and invalid-value coverage.**

## Final marking rubric (100 marks)

| Area | Marks | Evidence |
|---|---:|---|
| Variables and types | 15 | Correct values and naming |
| Input and conversions | 15 | Inputs converted appropriately |
| Operators and arithmetic | 20 | Correct calculator behaviour |
| Conditions and validation | 20 | Correct branches and boundary checks |
| Formatted output | 10 | Readable profile and calculator output |
| Testing and debugging | 10 | Test matrix and explained fixes |
| GitHub and documentation | 10 | Commits, README, reproducible commands |
| **Total** | **100** | |

### Recommended instructor feedback template

**Strengths:** Identify two observable skills.  
**Needs practice:** Name one or two concepts, with evidence.  
**Correction exercise:** Give one specific task to redo independently.  
**Readiness:** Ready for Week 5 algorithms/conditionals if the learner can explain input, conversion, arithmetic and `if/elif/else` without reading solutions.

## Submission checklist

- [ ] `exercises/hello.py`
- [ ] `exercises/student_intro.py`
- [ ] `assignments/biography.py`
- [ ] `assignments/shopping_receipt.py`
- [ ] `projects/calculator.py`
- [ ] `projects/student_profile.py`
- [ ] At least 5 practice problems attempted
- [ ] Boundary tests recorded
- [ ] README with run instructions
- [ ] Three or more meaningful Git commits
- [ ] Student explains calculator and profile logic independently

## Bridge to Week 5

Week 5 expands **computational thinking, algorithms, pseudocode, flowcharts and conditional problem-solving**. Reuse the calculator and profile generator to show how a problem is decomposed into input, decision, processing and output. Avoid jumping into loops and functions prematurely; those receive deeper coverage in Weeks 6 and 7.

---

**Opsfuxion Technologies Limited** · *Orchestrate Intelligence, Deliver with Precision.*  
**Instructor edition — Week 4.1** · © 2026 Opsfuxion Technologies Limited.
