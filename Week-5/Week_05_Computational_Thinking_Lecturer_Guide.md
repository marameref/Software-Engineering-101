# WEEK 5 — COMPUTATIONAL THINKING, ALGORITHMS & DECISION MAKING

**Opsfuxion Technologies Limited**  
*Orchestrate Intelligence, Deliver with Precision.*

**Practical Software Engineering Foundation Programme | Lecturer's Complete Teaching Manual**  
**Level:** Beginner | **Contact time:** 3 × 120 minutes = 6 hours | **Independent practice:** 6–10 hours  
**Student:** Uzoamaka | **Format:** instructor-led, code-along, independent lab, review

> **INSTRUCTOR EDITION:** Student tasks and model solutions appear together for ease of teaching. Share only the tasks before the student attempts them. The examples use Python 3. Do not assume a concept has been mastered because a learner can copy working code.

**Teaching rhythm:** Explain in plain language → draw or predict → live-code → student modifies → test boundaries → discuss why → commit.

## Instructor preparation and alignment

**Prerequisite:** Week 4.1 Python variables, strings, numeric conversion, operators, input/output and simple `if/elif/else`. **Do not** require loops, dictionaries or user-defined functions yet: those are taught more thoroughly in Weeks 6–7. A small amount of optional preview material is clearly marked.

**Week outcomes:** Break problems into inputs/processes/outputs; recognise patterns and abstraction; write precise algorithms; distinguish pseudocode from Python; interpret flowchart symbols; trace conditions; apply comparison, Boolean and nested logic; validate grades and eligibility; build a Grade Calculator and Eligibility Checker.

**Equipment:** VS Code, Python 3, paper/whiteboard for flowcharts, terminal, Git repository. Confirm `python3 --version` (macOS/Linux) or `py --version` (Windows). Make `Week-05/{exercises,assignments,projects}`.

**Lecturer caution:** Real school grading and admissions criteria vary. Use explicitly fictional policies, not claims about any institution.

---

# SESSION 1 — COMPUTATIONAL THINKING, ALGORITHMS & PSEUDOCODE (120 MIN)

| Minutes | Segment | Instructor action |
|---|---|---|
| 0–15 | Recap Week 4 | Ask for input, conversion, comparisons |
| 15–35 | Computational thinking | Decompose a school problem |
| 35–55 | Algorithms and IPO | Trace examples by hand |
| 55–80 | Pseudocode | Convert English to structured steps |
| 80–105 | Guided lab | Admission fee estimator |
| 105–115 | Debug/reason | Spot ambiguous instructions |
| 115–120 | Exit ticket | Explain back without notes |

## Lecture 1.1 — What is computational thinking?

**Say:** “A computer follows instructions, not intentions. Before we code, we decide exactly what problem we are solving.” Explain four practices:

1. **Decomposition:** split a large task into smaller tasks. Example: a grade report needs a score, validity check, classification and output.
2. **Pattern recognition:** repeated situations share a rule. For every score, a range determines the grade.
3. **Abstraction:** keep what matters; omit irrelevant details. A grade calculator needs a score, not a student's favourite colour.
4. **Algorithm design:** produce ordered, unambiguous, finite instructions.

**Ask:** “If a user enters `hello` as a score, at which stage should we reject it?” Expected: validation before arithmetic. Explain numeric conversion may fail; a robust treatment of exceptions follows in Week 7.

### Board exercise: input–process–output (IPO)

| Problem | Input | Process | Output |
|---|---|---|---|
| Circle area | Radius | π × r² | Area |
| Age eligibility | Age | Compare to threshold | Eligible/Not eligible |
| Grade report | Score | Validate then classify | Grade and status |

**Instructor prompt:** “Is printing a grade the same as computing a grade?” No: processing computes; output presents.

## Lecture 1.2 — What makes an algorithm good?

Explain **correctness** (works for intended inputs), **clarity** (unambiguous), **termination** (eventually finishes), and **testability** (expected outcomes can be checked). Do not confuse a recipe with Python syntax.

**Algorithm: check an age threshold**

1. Read age.
2. If age is negative, report invalid input.
3. Otherwise, if age is at least 18, report eligible.
4. Otherwise, report not eligible.
5. Stop.

**Trace table**

| Age | Negative? | ≥18? | Output |
|---:|---|---|---|
| -1 | Yes | Not evaluated | Invalid |
| 17 | No | No | Not eligible |
| 18 | No | Yes | Eligible |
| 25 | No | Yes | Eligible |

## Lecture 1.3 — Pseudocode

Pseudocode is human-readable, language-independent structured logic. There is no universal pseudocode syntax. Be consistent.

```text
START
READ score
IF score < 0 OR score > 100 THEN
    DISPLAY "Invalid score"
ELSE IF score >= 50 THEN
    DISPLAY "Pass"
ELSE
    DISPLAY "Fail"
END IF
STOP
```

**Walkthrough:** `READ` means input; `DISPLAY` means output; conditions must be checked in the right order. The boundary at 50 is inclusive.

**Common misconception:** “Pseudocode is executable.” Correct: it is a planning representation; Python executes only valid Python code.

## Guided practice 1 — Admission fee estimator (25 min)

**STUDENT TASK:** A fictional training centre charges ₦20,000. Applicants aged 16 or younger receive a ₦5,000 discount. Negative ages are invalid. Write IPO, algorithm and pseudocode; then implement in Python.

**Pause for attempt: 10 minutes.** Ask learner to test -1, 16, 17.

### INSTRUCTOR SOLUTION

IPO: age → validate and choose fee → message/fee.

```text
START
READ age
IF age < 0 THEN
    DISPLAY "Invalid age"
ELSE IF age <= 16 THEN
    DISPLAY 15000
ELSE
    DISPLAY 20000
END IF
STOP
```

```python
age = int(input("Enter age: "))
if age < 0:
    print("Invalid age")
elif age <= 16:
    print("Fee: ₦15,000")
else:
    print("Fee: ₦20,000")
```

**Explain:** `int()` expects numeric input. Non-numeric text causes `ValueError`; for now, state the input requirement and revisit graceful exception handling in Week 7.

### Instructor debugging demonstration

Broken pseudocode: “If age > 16 discount; otherwise full fee.” Ask student to find the reversed boundary and negative-age omission. Correct it before running code.

### Session 1 exit ticket

1. Explain decomposition with an example.
2. What is abstraction?
3. Why is an IPO table useful?
4. What is the difference between pseudocode and Python?
5. What happens at age exactly 16?

### Homework 1 — Electricity tariff planner

**STUDENT TASK:** A fictional tariff charges ₦50 per unit for the first 100 units, and ₦70 for each additional unit. Reject negative units. Prepare IPO, algorithm, pseudocode and a Python implementation. Test 0, 100, 101, -3.

**INSTRUCTOR SOLUTION:**

```python
units = int(input("Units used: "))
if units < 0:
    print("Invalid units")
elif units <= 100:
    print(f"Bill: ₦{units * 50:,}")
else:
    bill = 100 * 50 + (units - 100) * 70
    print(f"Bill: ₦{bill:,}")
```

Expected: 0→0, 100→5,000, 101→5,070, -3→invalid. **Ask why** charging all 101 units at ₦70 would be incorrect: only additional units receive the higher rate.

---

# SESSION 2 — FLOWCHARTS, CONDITIONALS & BOOLEAN LOGIC (120 MIN)

| Minutes | Segment | Instructor action |
|---|---|---|
| 0–15 | Homework review | Boundary tests and tariff rule |
| 15–40 | Flowcharts | Draw symbols and arrows |
| 40–65 | Comparisons and Boolean logic | Truth tables, precedence |
| 65–85 | `if/elif/else` and nesting | Trace branches |
| 85–110 | Guided lab | Scholarship checker |
| 110–120 | Quiz and recap | Student explains design |

## Lecture 2.1 — Flowcharts

Explain common symbols:

| Shape | Meaning | Example |
|---|---|---|
| Oval | Start or end | START |
| Parallelogram | Input/output | Read score |
| Rectangle | Processing | total = price × quantity |
| Diamond | Decision | score ≥ 50? |
| Arrow | Direction of flow | Next step |

**Board drawing (conceptual):**

```text
       (START)
          |
     / Read score /
          |
    < 0 <= score <= 100 ? >
      / No        \ Yes
 / Show invalid /   < score >= 50 ? >
       |           / Yes      \ No
     (END)    / Show Pass / / Show Fail /
                   \         /
                     (END)
```

**Instructor note:** Ask learner to redraw with proper shapes on paper; text diagrams are only a guide. Each decision needs labelled branches. Avoid flowcharts with branches that never rejoin or terminate.

## Lecture 2.2 — Comparison operators

`==` equal; `!=` not equal; `>` greater; `<` less; `>=` at least; `<=` at most. `=` is assignment, not comparison.

```python
score = 50
print(score == 50)  # True
print(score > 50)   # False
print(score >= 50)  # True
```

**Ask:** “Why is `score = 50` invalid inside an `if` comparison?” It assigns, whereas `==` compares.

## Lecture 2.3 — Boolean logic

`and`: both true. `or`: at least one true. `not`: reverse a Boolean.

| A | B | A and B | A or B |
|---|---|---|---|
| False | False | False | False |
| False | True | False | True |
| True | False | False | True |
| True | True | True | True |

```python
age = 17
has_permission = True
may_attend = age >= 18 or has_permission
print(may_attend)
```

**Teach precedence:** use parentheses for clarity: `(age >= 18) or has_permission`. Do not assume `and` and `or` mean the same thing.

## Lecture 2.4 — Branch order and nesting

```python
score = 83
if score < 0 or score > 100:
    print("Invalid")
elif score >= 70:
    print("A")
elif score >= 60:
    print("B")
elif score >= 50:
    print("C")
else:
    print("F")
```

**Say:** “Python executes the first true branch in an `if/elif/else` chain. The ordering is part of the algorithm.” A grade threshold of 70 checked before 80 would incorrectly catch 85 if written carelessly.

Nested example:

```python
age = 19
registered = True
if age >= 18:
    if registered:
        print("Admitted")
    else:
        print("Register first")
else:
    print("Age requirement not met")
```

**Discuss:** Nested `if` can clarify sequential checks; deeply nested logic can be hard to maintain.

## Guided practice 2 — Scholarship eligibility (25 min)

**STUDENT TASK:** Fictional rule: age 16–25 inclusive, score ≥80, and application submitted. Reject invalid ages/scores. Output Eligible or Not eligible. Draw a flowchart and write code. Test boundaries.

**INSTRUCTOR SOLUTION:**

```python
age = int(input("Age: "))
score = float(input("Test score (0-100): "))
submitted = input("Application submitted? yes/no: ").strip().lower() == "yes"
if age < 0 or score < 0 or score > 100:
    print("Invalid age or score")
elif 16 <= age <= 25 and score >= 80 and submitted:
    print("Eligible")
else:
    print("Not eligible")
```

**Test matrix:** (16,80,yes) eligible; (25,100,yes) eligible; (26,90,yes) not; (20,79,yes) not; (20,90,no) not; (20,101,yes) invalid.

**Teaching note:** Non-`yes` responses are treated as False in this introductory version; later, validate accepted yes/no choices explicitly.

### Homework 2 — Cinema ticket eligibility

**STUDENT TASK:** Fictional film requires age ≥18 **and** a valid ticket. Invalid negative age must be rejected. Produce a flowchart, code and at least five test cases.

**INSTRUCTOR SOLUTION:**

```python
age = int(input("Age: "))
ticket = input("Valid ticket? yes/no: ").strip().lower()
if age < 0 or ticket not in ("yes", "no"):
    print("Invalid input")
elif age >= 18 and ticket == "yes":
    print("Entry allowed")
else:
    print("Entry denied")
```

---

# SESSION 3 — ALGORITHM TRACING, VALIDATION & PROJECTS (120 MIN)

| Minutes | Segment | Instructor action |
|---|---|---|
| 0–15 | Review | Read flowcharts aloud |
| 15–35 | Dry runs and boundary testing | Build trace table |
| 35–55 | Validation patterns | Numeric ranges, menu choices |
| 55–95 | Project build | Grade calculator |
| 95–110 | Eligibility checker | Student codes with prompts |
| 110–120 | Review | Demo and exit questions |

## Lecture 3.1 — Dry runs and test cases

**Say:** “A dry run is manually executing an algorithm on paper. We test boundaries because bugs cluster at the edges.”

| Score | Valid? | Grade | Pass? |
|---:|---|---|---|
| -1 | No | — | — |
| 0 | Yes | F | No |
| 49.9 | Yes | F | No |
| 50 | Yes | C | Yes |
| 59.9 | Yes | C | Yes |
| 60 | Yes | B | Yes |
| 69.9 | Yes | B | Yes |
| 70 | Yes | A | Yes |
| 100 | Yes | A | Yes |
| 100.1 | No | — | — |

**Fictional grading policy:** A 70–100; B 60–69.999…; C 50–59.999…; F below 50. This is an exercise policy, not an official institutional scale.

## Lecture 3.2 — Input validation

Distinguish **range validation** (0–100) from **type validation** (a number rather than letters). Week 5 covers the former thoroughly; Week 7 introduces `try/except` for the latter. Demonstrate invalid data intentionally and describe the error without shame.

## Weekly project A — Grade Calculator

**STUDENT BRIEF:** Read student name and numeric score; reject empty name and scores outside 0–100; determine grade A/B/C/F and pass/fail; display a neat report. Write pseudocode and test cases first. Allow the student 15 minutes of independent design before help.

### INSTRUCTOR MODEL SOLUTION

```python
print("=== STUDENT GRADE CALCULATOR ===")
name = input("Student name: ").strip()
score = float(input("Score (0-100): "))

if not name:
    print("Name is required")
elif score < 0 or score > 100:
    print("Score must be between 0 and 100")
else:
    if score >= 70:
        grade = "A"
    elif score >= 60:
        grade = "B"
    elif score >= 50:
        grade = "C"
    else:
        grade = "F"

    status = "PASS" if score >= 50 else "FAIL"
    print("\n--- ACADEMIC REPORT ---")
    print(f"Name: {name}")
    print(f"Score: {score:.1f}")
    print(f"Grade: {grade}")
    print(f"Status: {status}")
```

**Walk through every branch.** Ask: Why validate before classifying? Why does 70 need checking before 60? What happens for 100, 0, and 101?

## Weekly project B — Eligibility Checker

**STUDENT BRIEF:** Fictional technology bootcamp: applicants must be at least 16, have completed basic HTML and have parental consent if under 18. Accept `yes`/`no` inputs. Reject negative age and invalid yes/no responses. Print reason for rejection where possible.

### INSTRUCTOR MODEL SOLUTION

```python
print("=== BOOTCAMP ELIGIBILITY ===")
age = int(input("Age: "))
html = input("Completed HTML basics? yes/no: ").strip().lower()
consent = input("Parental consent? yes/no: ").strip().lower()

if age < 0 or html not in ("yes", "no") or consent not in ("yes", "no"):
    print("Invalid input")
elif age < 16:
    print("Not eligible: minimum age is 16")
elif html != "yes":
    print("Not eligible: HTML basics required")
elif age < 18 and consent != "yes":
    print("Not eligible: parental consent required")
else:
    print("Eligible to apply")
```

**Instructor prompts:** Is consent relevant at age 18? What if a 16-year-old has no consent? Which condition should be checked first? Note that input validation is a skill, not merely a technicality.

### Extra independent practice (with answers)

**P1.** Write pseudocode for checking whether a number is positive, negative or zero.

**Solution:** READ n → IF n > 0 display Positive → ELSE IF n < 0 display Negative → ELSE display Zero.

**P2.** Explain what `10 <= age <= 18` means. **Solution:** Age is at least 10 and at most 18, inclusive.

**P3.** Predict output:

```python
score = 70
if score >= 50:
    print("Pass")
elif score >= 70:
    print("Excellent")
```

**Solution:** `Pass`, because the first true branch wins. Correct by testing `>=70` first.

**P4.** Predict `not (True and False)`. **Solution:** `True`.

**P5.** Explain difference between `=` and `==`. **Solution:** assignment vs equality comparison.

**P6.** Why is `score > 100` invalid? **Solution:** It violates the defined score range; grading it would produce misleading results.

---

# Instructor assessment and grading

| Criterion | Weight | Evidence |
|---|---:|---|
| Decomposition/IPO | 15% | Problem breakdown |
| Algorithms and pseudocode | 20% | Clear ordered steps |
| Flowcharts | 15% | Correct symbols and branches |
| Conditional/Boolean logic | 20% | Correct boundaries and rules |
| Input validation and tests | 15% | Invalid/boundary cases |
| Project completeness | 10% | Both applications work |
| Communication and code readability | 5% | Explains choices |
| **Total** | **100%** | |

## Instructor observation checklist

- [ ] Learner explains the difference between an algorithm and code.
- [ ] Learner draws a decision flow with labelled Yes/No arrows.
- [ ] Learner predicts outputs before execution.
- [ ] Learner tests boundary values, not only happy paths.
- [ ] Learner completes both projects and explains conditions.
- [ ] Learner makes meaningful Git commits.

## Common mistakes and interventions

| Mistake | Why it happens | Teaching response |
|---|---|---|
| Uses `=` in comparison | Assignment confused with equality | Contrast `x = 5` and `x == 5` |
| Checks low threshold first | Misunderstands `elif` | Trace 85 through branches |
| Forgetting invalid range | Focus on happy path | Test -1 and 101 first |
| Wrong `and`/`or` | Natural-language ambiguity | Use two-column truth table |
| Poor indentation | Python block structure new | Draw branch nesting on board |
| Treats pseudocode as executable | Confuses design with code | Rewrite same logic in plain English |

## Suggested Git deliverables

```text
Week-05/
├── exercises/
│   ├── fee_estimator.py
│   └── scholarship_checker.py
├── assignments/
│   ├── electricity_tariff.py
│   └── cinema_eligibility.py
├── projects/
│   ├── grade_calculator.py
│   └── eligibility_checker.py
└── README.md
```

**Exit reflection:** “What was the hardest branch to reason about, and what test proved it worked?”

**Next week:** Use lists, dictionaries and loops to process many records instead of one input at a time.
