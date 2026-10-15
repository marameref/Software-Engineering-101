
# Week 5 — Programming Logic, Computational Thinking & Algorithms

## Practical Software Engineering Foundation Programme

**Duration:** 1 Week  
**Sessions:** 3 Instructor-Led Sessions  
**Session Duration:** 2 Hours  
**Total Instructor-Led Time:** 6 Hours  
**Level:** Beginner  
**Prerequisite:** Week 4 — Python Programming Fundamentals  
**Weekly Projects:** Student Grade Calculator & Admissions Eligibility Checker  
**Primary Language:** Python 3

---

## Week Overview

Week 5 introduces computational thinking, algorithm design, and decision-making in Python.

Building on the programming fundamentals acquired in Week 4, the student will learn how to analyse problems, break them into smaller steps, describe solutions using pseudocode and flowcharts, and implement conditional logic using Python.

The student will also learn how programs make decisions based on conditions and how basic input validation can improve program reliability.

The emphasis is on developing problem-solving skills rather than simply memorising Python syntax.

By the end of the week, the student should be able to design and implement a small Python application that makes decisions based on user input.

---

# Learning Objectives

By the end of Week 5, the student should be able to:

- Explain computational thinking.
- Understand problem decomposition.
- Identify patterns in problems.
- Understand abstraction.
- Explain what an algorithm is.
- Write simple algorithms.
- Understand pseudocode.
- Create basic flowcharts.
- Use comparison operators.
- Understand Boolean expressions.
- Apply logical operators.
- Use `if`, `elif`, and `else`.
- Write nested conditional statements.
- Understand Python indentation.
- Validate simple user input.
- Use basic exception handling.
- Translate written requirements into program logic.
- Build Python applications that make decisions.

---

# Session 1 — Computational Thinking, Algorithms & Pseudocode

**Duration:** 2 Hours

## 1. Review of Week 4 — 15 Minutes

Review:

- Python syntax
- Variables
- Data types
- Operators
- User input
- Type conversion
- Calculator project

### Discussion

The calculator developed in Week 4 performs arithmetic operations.

What if we wanted the program to:

- Allow users to select an operation?
- Determine whether a student passed or failed?
- Check whether someone is eligible for admission?
- Display different messages based on user input?

How would the program decide what to do?

This introduces programming logic.

---

## 2. What is Computational Thinking? — 20 Minutes

Computational thinking is a structured approach to solving problems in ways that can be represented as logical steps.

Introduce four important concepts.

### Decomposition

Breaking a large problem into smaller parts.

Example:

Building a student registration system involves:

1. Collecting student details.
2. Checking the information.
3. Storing the information.
4. Displaying confirmation.

### Pattern Recognition

Identifying similarities between problems.

Example:

Calculating grades for different students follows the same basic process.

### Abstraction

Focusing on important information while ignoring unnecessary details.

Example:

A grade calculator may need a student's score but not their favourite food.

### Algorithm Design

Creating a sequence of steps to solve a problem.

---

## 3. What is an Algorithm? — 20 Minutes

An algorithm is a finite, well-defined sequence of steps used to solve a problem.

### Everyday Example

Algorithm for preparing tea:

```text
1. Get a cup.
2. Boil water.
3. Place tea in the cup.
4. Add hot water.
5. Add other ingredients if desired.
6. Stir.
7. Serve.
```

### Programming Example

Algorithm for calculating the average of two scores:

```text
1. Start.
2. Receive the first score.
3. Receive the second score.
4. Add the scores.
5. Divide the total by 2.
6. Display the average.
7. End.
```

### Discussion

What makes an algorithm useful?

Introduce:

- Clear steps
- Correct order
- Defined inputs
- Expected outputs
- Termination

---

## 4. Introduction to Pseudocode — 20 Minutes

Pseudocode describes program logic using readable, language-independent instructions.

### Example

```text
START

INPUT first_score
INPUT second_score

total = first_score + second_score

average = total / 2

DISPLAY average

END
```

### Why Use Pseudocode?

- Helps plan solutions.
- Makes logic easier to understand.
- Reduces confusion before coding.
- Supports communication.
- Helps identify missing steps.

---

## 5. Introduction to Flowcharts — 20 Minutes

Flowcharts visually represent the steps of an algorithm.

### Common Symbols

| Symbol | Meaning |
|---|---|
| Oval | Start or End |
| Rectangle | Process |
| Parallelogram | Input or Output |
| Diamond | Decision |
| Arrow | Direction of flow |

### Example: Pass or Fail

```text
       START
         |
    Enter Score
         |
   Is Score >= 50?
      /       \
    YES        NO
     |          |
   PASS        FAIL
      \        /
         END
```

Explain that flowcharts can represent decisions before code is written.

---

## 6. Guided Practical — 20 Minutes

### Practical Exercise 1: Design an Algorithm

Scenario:

A student passes an examination if their score is at least 50.

The student should:

1. Identify the required input.
2. Identify the expected output.
3. Write pseudocode.
4. Draw a flowchart.
5. Explain the decision process.

### Expected Result

A written algorithm and flowchart for determining whether a student passed or failed.

---

## 7. Session Review — 5 Minutes

Questions:

1. What is computational thinking?
2. What is decomposition?
3. What is abstraction?
4. What is an algorithm?
5. What is pseudocode?
6. What is a flowchart?

---

# Session 1 Assignment

## Algorithm Design Challenge

Create pseudocode and flowcharts for:

### Problem 1 — Age Eligibility

A person is eligible for a programme if they are at least 18 years old.

### Problem 2 — Number Comparison

Determine which of two numbers is greater, or whether they are equal.

### Problem 3 — Student Result

Determine whether a student passed or failed based on a score of 50 or above.

### Deliverable

Three algorithms represented using pseudocode and flowcharts.

---

# Session 2 — Conditional Statements & Boolean Logic

**Duration:** 2 Hours

## 1. Assignment Review — 15 Minutes

Review the pseudocode and flowcharts.

Discuss:

- Correct problem interpretation
- Input identification
- Decision conditions
- Logical sequence
- Expected outputs

---

## 2. Comparison Operators — 20 Minutes

Comparison operators evaluate relationships between values.

| Operator | Meaning | Example |
|---|---|---|
| `==` | Equal to | `5 == 5` |
| `!=` | Not equal to | `5 != 3` |
| `>` | Greater than | `5 > 3` |
| `<` | Less than | `5 < 3` |
| `>=` | Greater than or equal to | `5 >= 5` |
| `<=` | Less than or equal to | `3 <= 5` |

### Example

```python
score = 75

print(score >= 50)
print(score < 50)
```

### Discussion

What is the difference between `=` and `==`?

---

## 3. Boolean Expressions — 15 Minutes

Boolean expressions evaluate to:

```python
True
False
```

### Example

```python
age = 18

is_eligible = age >= 18

print(is_eligible)
```

Explain how Boolean values are used in decision-making.

---

## 4. Conditional Statements — 25 Minutes

### `if`

```python
score = 75

if score >= 50:
    print("Pass")
```

### `if` and `else`

```python
score = 40

if score >= 50:
    print("Pass")
else:
    print("Fail")
```

### `if`, `elif`, and `else`

```python
score = 85

if score >= 70:
    print("Grade A")
elif score >= 60:
    print("Grade B")
elif score >= 50:
    print("Grade C")
else:
    print("Grade F")
```

### Important Concept

Python uses indentation to define code blocks.

---

## 5. Logical Operators — 20 Minutes

Introduce:

- `and`
- `or`
- `not`

### `and`

Both conditions must be true.

```python
age = 18
has_certificate = True

if age >= 16 and has_certificate:
    print("Eligible")
```

### `or`

At least one condition must be true.

```python
has_passport = True
has_national_id = False

if has_passport or has_national_id:
    print("Identity document available")
```

### `not`

Reverses a Boolean value.

```python
is_registered = False

if not is_registered:
    print("Registration required")
```

---

## 6. Guided Practical — 20 Minutes

### Practical Exercise 2: Grade Checker

Create:

```text
grade_checker.py
```

Requirements:

1. Ask for the student's name.
2. Ask for the examination score.
3. Determine the grade.
4. Display the student's name.
5. Display the score.
6. Display the grade.

### Grading Rules

| Score | Grade |
|---|---|
| 70–100 | A |
| 60–69 | B |
| 50–59 | C |
| 40–49 | D |
| 0–39 | F |

The program should identify scores outside the valid range.

---

## 7. Session Review — 5 Minutes

Questions:

1. What is a Boolean expression?
2. What does `if` do?
3. What does `elif` do?
4. What does `else` do?
5. What is the difference between `and` and `or`?
6. Why is indentation important in Python?

---

# Session 2 Assignment

## Admissions Eligibility Checker

Create:

```text
admission_checker.py
```

### Scenario

A fictional training institution accepts applicants who:

- Are at least 16 years old.
- Have completed secondary school.
- Have an entrance examination score of at least 60.

### Requirements

The program should:

1. Ask for the applicant's name.
2. Ask for age.
3. Ask whether secondary school has been completed.
4. Ask for entrance examination score.
5. Determine eligibility.
6. Display an appropriate message.

### Example Output

```text
================================
     ADMISSIONS ELIGIBILITY
================================

Applicant: Uzoamaka
Age: 16
Secondary School Completed: Yes
Entrance Score: 75

Status: ELIGIBLE

================================
```

### Deliverable

A working Python application using comparison operators, logical operators and conditional statements.

---

# Session 3 — Input Validation, Nested Conditions & Weekly Projects

**Duration:** 2 Hours

## 1. Assignment Review — 15 Minutes

Review the Admissions Eligibility Checker.

Discuss:

- Conditions
- Logical operators
- Input handling
- Code readability
- Correct eligibility decisions

---

## 2. Understanding Input Validation — 20 Minutes

Input validation checks whether supplied information meets expected requirements.

### Examples

- Age should not be negative.
- Examination scores should be between 0 and 100.
- Numeric fields should contain valid numbers.
- Required information should not be empty.

### Example

```python
score = int(input("Enter score: "))

if score < 0 or score > 100:
    print("Invalid score")
else:
    print("Valid score")
```

---

## 3. Introduction to Exception Handling — 15 Minutes

A program may encounter errors when converting user input.

Example:

```python
try:
    age = int(input("Enter age: "))
    print(f"Age: {age}")
except ValueError:
    print("Please enter a valid whole number.")
```

Explain:

- `try`
- `except`
- `ValueError`

More advanced exception handling will be revisited in Week 7.

---

## 4. Nested Conditional Statements — 15 Minutes

Nested conditions allow decisions within decisions.

### Example

```python
age = 18
has_certificate = True

if age >= 16:
    if has_certificate:
        print("Eligible")
    else:
        print("Certificate required")
else:
    print("Age requirement not met")
```

Discuss when nested conditions are useful and when simpler logical expressions may be clearer.

---

# Week 5 Project 1

## Student Grade Calculator — Version 2

The student will improve the calculator concept by introducing decision-making and input validation.

### Requirements

The program should:

1. Display a welcome message.
2. Ask for the student's name.
3. Ask for an examination score.
4. Check whether the score is valid.
5. Determine the appropriate grade.
6. Display Pass or Fail.
7. Display a formatted result summary.
8. Handle non-numeric input gracefully.

### Grading Rules

| Score | Grade | Status |
|---|---|---|
| 70–100 | A | Pass |
| 60–69 | B | Pass |
| 50–59 | C | Pass |
| 40–49 | D | Fail |
| 0–39 | F | Fail |

### Example Output

```text
================================
       STUDENT RESULT
================================

Student: Uzoamaka
Score: 82
Grade: A
Status: PASS

================================
```

---

# Week 5 Project 2

## Admissions Eligibility Checker — Version 2

Improve the Session 2 assignment.

### Additional Requirements

- Reject negative ages.
- Reject examination scores outside 0–100.
- Handle invalid numeric input.
- Provide a clear reason when an applicant is not eligible.
- Display a formatted result summary.

### Example

```text
================================
     ADMISSIONS ELIGIBILITY
================================

Applicant: Example Student
Age: 15
Secondary School Completed: Yes
Entrance Score: 80

Status: NOT ELIGIBLE

Reason: Minimum age requirement not met.

================================
```

---

## 5. Independent Project Work — 45 Minutes

The student will independently develop or improve the projects.

The student may:

- Review pseudocode.
- Review flowcharts.
- Consult previous Python exercises.
- Research Python syntax.
- Test different inputs.
- Read error messages.
- Ask conceptual questions.

The instructor will provide guidance without writing the entire solution.

---

## 6. Project Review — 10 Minutes

Review:

- Correct conditional logic
- Appropriate comparison operators
- Correct logical operators
- Input validation
- Error handling
- Code readability
- Expected output
- Edge cases

### Suggested Test Cases

For the grade calculator:

```text
Score: 100 → Grade A
Score: 70  → Grade A
Score: 69  → Grade B
Score: 50  → Grade C
Score: 40  → Grade D
Score: 0   → Grade F
Score: -5  → Invalid
Score: 105 → Invalid
Score: abc → Invalid input
```

---

# Suggested Project Structure

```text
Week-05/
│
├── exercises/
│   ├── algorithms.md
│   ├── flowcharts/
│   └── conditions.py
│
├── assignments/
│   ├── grade_checker.py
│   └── admission_checker.py
│
└── projects/
    ├── student_grade_calculator.py
    └── admission_eligibility_checker.py
```

---

# Week 5 Knowledge Check

1. What is computational thinking?
2. What is problem decomposition?
3. What is pattern recognition?
4. What is abstraction?
5. What is an algorithm?
6. What is pseudocode?
7. What is a flowchart?
8. What is a Boolean expression?
9. What is the difference between `=` and `==`?
10. What does `if` do?
11. What does `elif` do?
12. What does `else` do?
13. What does `and` mean?
14. What does `or` mean?
15. What does `not` do?
16. What is a nested conditional statement?
17. Why is indentation important in Python?
18. What is input validation?
19. What is exception handling?
20. Why should programs test boundary values?

---

# Week 5 Assessment

| Assessment Area | Weight |
|---|---:|
| Computational thinking | 20% |
| Algorithm and pseudocode design | 15% |
| Conditional logic | 20% |
| Logical operators | 10% |
| Input validation | 15% |
| Independent problem-solving | 10% |
| Project completion | 10% |
| **Total** | **100%** |

---

# Week 5 Deliverables

By the end of Week 5, the student should have completed:

- Algorithm design exercises
- Pseudocode assignments
- Flowchart assignments
- Conditional statement exercises
- Grade Checker
- Admissions Eligibility Checker — Version 1
- Student Grade Calculator — Version 2
- Admissions Eligibility Checker — Version 2
- Week 5 knowledge check

---

# Expected Outcome

By the end of Week 5, the student should be able to:

- Break problems into smaller steps.
- Write basic algorithms.
- Represent solutions using pseudocode.
- Create simple flowcharts.
- Use comparison operators.
- Write conditional statements.
- Apply Boolean logic.
- Validate simple user input.
- Handle common input errors.
- Build Python programs that make decisions.
- Translate written requirements into executable logic.

---

## Next

**Week 6 — Python Data Structures & Loops**

Week 6 introduces lists, tuples, dictionaries, sets, iteration, `for` loops, `while` loops, and practical data-processing exercises.
