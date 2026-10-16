# WEEK 6 — PYTHON DATA STRUCTURES & LOOPS

**Opsfuxion Technologies Limited**  
*Orchestrate Intelligence, Deliver with Precision.*

**Practical Software Engineering Foundation Programme | Lecturer's Complete Teaching Manual**  
**Level:** Beginner | **Contact time:** 3 × 120 minutes = 6 hours | **Independent practice:** 6–10 hours  
**Student:** Uzoamaka | **Format:** instructor-led, code-along, independent lab, review

> **INSTRUCTOR EDITION:** Student tasks and model solutions appear together for ease of teaching. Share only the tasks before the student attempts them. The examples use Python 3. Do not assume a concept has been mastered because a learner can copy working code.

**Teaching rhythm:** Explain in plain language → draw or predict → live-code → student modifies → test boundaries → discuss why → commit.

## Instructor preparation and learning outcomes

**Prerequisite:** Week 5 conditions and validation; Week 4 Python basics. **Boundary:** this week introduces Python built-in collections and iteration; Week 9 will cover stacks, queues, searching, sorting and Big O in greater depth. Avoid confusing these two different levels.

**Outcomes:** Explain lists, tuples, dictionaries and sets; index, slice and update lists; choose an appropriate collection; write `for` and `while` loops; use `range`, `enumerate`, `break`, `continue` and nested loops; iterate through dictionaries; validate score ranges; calculate average, minimum, maximum and pass/fail counts; complete a Student Score Analyser.

**Before class:** Create `Week-06/{exercises,assignments,projects}`; prepare a five-student sample dataset; check VS Code and Python 3. Prepare to explain zero-based indexing with numbered cards.

**Teaching principle:** Start with literal values and printed outputs. Ask the learner to predict how the collection changes after each operation. Prefer readable code over clever one-liners.

---

# SESSION 1 — LISTS, TUPLES & BASIC COLLECTION OPERATIONS (120 MIN)

| Minutes | Segment | Lecturer cue |
|---|---|---|
| 0–10 | Week 5 review | Score and validation |
| 10–30 | Collections overview | Single variable vs many values |
| 30–60 | Lists | Indexing, slicing, mutation, methods |
| 60–75 | List aggregates | `len`, `sum`, `min`, `max` |
| 75–90 | Tuples | Ordered, immutable sequence |
| 90–110 | Guided practice | Subject score manager |
| 110–120 | Exit ticket | Predict and explain |

## Lecture 1.1 — Why collections?

**Say:** “Instead of creating `score1`, `score2`, `score3` and hundreds more variables, we can keep related values in one collection.”

```python
score1 = 80
score2 = 65
score3 = 90
scores = [80, 65, 90]
print(scores)
```

**Ask:** What is the first index? `0`, not `1`.

## Lecture 1.2 — Lists: ordered, changeable sequences

```python
subjects = ["Maths", "English", "Physics"]
print(subjects[0])       # Maths
print(subjects[-1])      # Physics
print(subjects[0:2])     # ['Maths', 'English']
print(len(subjects))     # 3
```

**Draw on board:**

```text
index      0         1          2
value    Maths    English     Physics
negative  -3        -2         -1
```

Explain `IndexError` for out-of-range positions; slicing usually returns a new list. Compare `subjects[1]` and `subjects[1:2]` (item vs list).

### Mutation and methods

```python
subjects = ["Maths", "English"]
subjects.append("Physics")          # add to end
subjects.insert(1, "Biology")       # insert at index 1
subjects[0] = "Mathematics"         # replace
subjects.remove("Biology")          # remove matching value
last = subjects.pop()               # remove and return last
print(subjects, last)
```

**Pause after each line** and have learner predict the list. Contrast `remove(value)` with `pop(index)` and mention that removing a missing value raises `ValueError`.

### Sorting and aggregating

```python
scores = [75, 90, 60, 85]
print(len(scores))       # 4
print(sum(scores))       # 310
print(min(scores))       # 60
print(max(scores))       # 90
print(sorted(scores))    # new sorted list
print(scores)            # original remains unchanged
scores.sort()            # modifies original
print(scores)
```

**Important:** `min`, `max` and mean calculations need care with empty lists; do not divide by zero.

## Lecture 1.3 — Tuples

A tuple is an ordered sequence that cannot be changed in place.

```python
coordinates = (9.07, 7.49)
print(coordinates[0])
print(len(coordinates))
# coordinates[0] = 10  # TypeError: tuple does not support assignment
```

**When to choose:** Use a tuple for a fixed grouping (e.g., a latitude/longitude pair) and a list for a changing collection. A tuple can contain mutable items; immutability applies to its own element references.

## Guided lab 1 — Subject Score Manager

**STUDENT TASK:** Create a list of four subject scores, append a fifth, replace the second, display first and last, compute total/average/highest/lowest, and sort without losing original order. Check empty collection before calculating an average.

### INSTRUCTOR SOLUTION

```python
scores = [70, 85, 60, 90]
scores.append(75)
scores[1] = 88
print("First:", scores[0], "Last:", scores[-1])
print("Total:", sum(scores))
if scores:
    print("Average:", round(sum(scores) / len(scores), 2))
    print("Highest:", max(scores))
    print("Lowest:", min(scores))
else:
    print("No scores yet")
print("Sorted copy:", sorted(scores))
print("Original:", scores)
```

**Instructor questions:** Why does `sorted` preserve the original? What would `scores.sort()` do? Why check `if scores`?

### Homework 1 — Student Score Collection

**STUDENT TASK:** Start with an empty list. Ask for three numeric scores using three `input()` statements (loops are introduced in Session 2); validate each score 0–100 before appending; show count, total and average. Test 0 and 100.

### INSTRUCTOR SOLUTION

```python
scores = []
first = float(input("First score: "))
second = float(input("Second score: "))
third = float(input("Third score: "))
for score in (first, second, third):  # optional preview: loops taught next session
    if 0 <= score <= 100:
        scores.append(score)
    else:
        print("Rejected invalid score:", score)
print("Count:", len(scores))
if scores:
    print("Total:", sum(scores))
    print("Average:", sum(scores) / len(scores))
else:
    print("No valid scores")
```

**If avoiding preview loops**, replace the `for` block with three separate `if 0 <= first <= 100:` checks; use the loop version to motivate Session 2.

---

# SESSION 2 — DICTIONARIES, SETS & FOR LOOPS (120 MIN)

| Minutes | Segment | Lecturer cue |
|---|---|---|
| 0–15 | Homework review | Count and average |
| 15–40 | Dictionaries | Key–value model |
| 40–55 | Sets | Unique values |
| 55–85 | `for`, `range`, `enumerate` | Iterate collections |
| 85–110 | Guided lab | Student records |
| 110–120 | Quiz | Choose structures |

## Lecture 2.1 — Dictionaries

A dictionary maps keys to values. Keys must be hashable; values can be many types. Use meaningful keys.

```python
student = {
    "id": "STU001",
    "name": "Uzoamaka",
    "age": 16,
    "scores": [80, 90, 75],
}
print(student["name"])
print(student.get("course", "Not provided"))
student["age"] = 17
student["course"] = "Software Engineering"
print(student.keys())
print(student.values())
print(student.items())
```

**Explain:** `student['missing']` raises `KeyError`; `.get()` can provide a default. Keys are unique; assigning an existing key replaces its value. Dictionaries preserve insertion order in modern Python, but access by key, not numeric position.

### Iteration

```python
for key, value in student.items():
    print(key, "=", value)
```

**Ask:** Why is a dictionary better than a list for a student's named attributes?

## Lecture 2.2 — Sets

A set stores unique hashable elements; it has no meaningful positional indexing.

```python
subjects = ["Maths", "English", "Maths", "Physics"]
unique_subjects = set(subjects)
print(unique_subjects)  # order may vary
print("Maths" in unique_subjects)
unique_subjects.add("Biology")
unique_subjects.discard("English")
```

**Caution:** Sets are not sorted lists. Never write a test that assumes their display order.

## Lecture 2.3 — `for` loops and `range`

```python
for subject in ["Maths", "English", "Physics"]:
    print("Subject:", subject)

for number in range(1, 6):
    print(number)  # 1 through 5

scores = [70, 80, 90]
for index, score in enumerate(scores, start=1):
    print(f"Score {index}: {score}")
```

**Say:** “`range(1, 6)` stops before 6.” Explain iterable vs iteration, loop variable, and indentation. Predict number of iterations before running.

### Loop with conditions

```python
scores = [45, 55, 70, 30]
passes = 0
for score in scores:
    if score >= 50:
        passes += 1
print("Passes:", passes)
```

**Trace table:** score 45→passes 0; 55→1; 70→2; 30→2.

## Guided lab 2 — Student Records Reporter

**STUDENT TASK:** Store three students as dictionaries in a list. For each, display name, score and PASS/FAIL. Count passes and failures. Collect unique course names using a set.

### INSTRUCTOR SOLUTION

```python
students = [
    {"name": "Ada", "course": "Python", "score": 85},
    {"name": "Chidi", "course": "Web", "score": 45},
    {"name": "Uzoamaka", "course": "Python", "score": 90},
]
passes = 0
courses = set()
for student in students:
    courses.add(student["course"])
    status = "PASS" if student["score"] >= 50 else "FAIL"
    if status == "PASS":
        passes += 1
    print(student["name"], student["score"], status)
print("Pass:", passes)
print("Fail:", len(students) - passes)
print("Courses:", sorted(courses))
```

**Check understanding:** What changes if Chidi's score becomes 50? Why use `sorted(courses)` for predictable output?

### Homework 2 — Student Performance Reporter

**STUDENT TASK:** Create four student dictionaries; print each student, grade status, class average and list of unique courses. At least one score must be exactly 50. Use loops rather than repeating print statements.

### INSTRUCTOR SOLUTION

```python
students = [
    {"name": "Ada", "course": "Python", "score": 80},
    {"name": "Emeka", "course": "Python", "score": 50},
    {"name": "Chidi", "course": "Web", "score": 40},
    {"name": "Zara", "course": "Data", "score": 90},
]
total = 0
for student in students:
    total += student["score"]
    print(student["name"], "PASS" if student["score"] >= 50 else "FAIL")
print("Class average:", total / len(students) if students else "N/A")
print("Unique courses:", sorted({s["course"] for s in students}))
```

---

# SESSION 3 — WHILE LOOPS, CONTROL FLOW & STUDENT SCORE ANALYSER (120 MIN)

| Minutes | Segment | Lecturer cue |
|---|---|---|
| 0–15 | Homework review | Read dictionaries aloud |
| 15–40 | `while` loops | Condition and termination |
| 40–55 | `break` / `continue` | Exit vs skip |
| 55–70 | Nested loops | Students × scores |
| 70–90 | Guided lab | Guessing game |
| 90–115 | Weekly project | Score analyser |
| 115–120 | Exit ticket | Edge cases |

## Lecture 3.1 — `while` loops

Use a `while` loop when repetition depends on a condition, not a predetermined number of items.

```python
count = 1
while count <= 3:
    print("Count:", count)
    count += 1
```

**Ask:** What if `count += 1` is removed? It could run forever. Stop a stuck terminal with Ctrl+C and explain how termination conditions matter.

## Lecture 3.2 — `break` and `continue`

```python
for number in range(1, 7):
    if number == 3:
        continue  # skip 3
    if number == 6:
        break     # end loop
    print(number)
```

Expected output: 1, 2, 4, 5. **Contrast:** `continue` skips the current iteration; `break` exits the loop.

## Lecture 3.3 — Nested loops

```python
students = ["Ada", "Chidi"]
subjects = ["Maths", "English"]
for student in students:
    for subject in subjects:
        print(student, "studies", subject)
```

Explain outer loop × inner loop: 2 students × 2 subjects = 4 lines. Ask learner to predict outputs in order.

## Guided lab 3 — Number Guessing Game

**STUDENT TASK:** Set secret number to 7. Keep asking until user guesses correctly; display Too high/Too low. Count attempts. For this week's version, assume valid integers.

### INSTRUCTOR SOLUTION

```python
secret = 7
attempts = 0
while True:
    guess = int(input("Guess 1-10: "))
    attempts += 1
    if guess == secret:
        print(f"Correct in {attempts} attempts!")
        break
    elif guess < secret:
        print("Too low")
    else:
        print("Too high")
```

**Optional:** Restrict guesses to 1–10 and use `continue` for invalid range without counting the attempt. Explain that handling letters gracefully belongs to Week 7 exceptions.

# WEEKLY PROJECT — STUDENT SCORE ANALYSER

## Student brief

Create a command-line program that repeatedly collects student names and scores, stopping when the user types `done` as the name. Validate scores from 0 to 100; store records in a list of dictionaries; print each record and PASS/FAIL; calculate total students, average score, highest/lowest score and pass/fail counts. Handle no records gracefully. For now, assume numeric input for scores; Week 7 will add `try/except`.

**Recommended plan:** (1) draw record structure, (2) input loop, (3) validation, (4) summary loop, (5) empty-data check, (6) test.

### INSTRUCTOR COMPLETE MODEL SOLUTION

```python
print("=== STUDENT SCORE ANALYSER ===")
students = []

while True:
    name = input("Student name (or 'done'): ").strip()
    if name.lower() == "done":
        break
    if not name:
        print("Name cannot be empty")
        continue

    score = float(input("Score (0-100): "))
    if not 0 <= score <= 100:
        print("Invalid score. Student not added.")
        continue
    students.append({"name": name, "score": score})
    print("Student added.")

if not students:
    print("No student records available.")
else:
    total = 0
    pass_count = 0
    highest = students[0]
    lowest = students[0]

    print("\n--- CLASS REPORT ---")
    for student in students:
        score = student["score"]
        total += score
        if score >= 50:
            pass_count += 1
        if score > highest["score"]:
            highest = student
        if score < lowest["score"]:
            lowest = student
        status = "PASS" if score >= 50 else "FAIL"
        print(f"{student['name']}: {score:.1f} — {status}")

    print("Students:", len(students))
    print(f"Average: {total / len(students):.2f}")
    print("Passes:", pass_count)
    print("Failures:", len(students) - pass_count)
    print("Highest:", highest["name"], highest["score"])
    print("Lowest:", lowest["name"], lowest["score"])
```

**Model test:** Ada 80, Chidi 40, Uzoamaka 50 → average 56.67, passes 2, failures 1, highest Ada 80, lowest Chidi 40.

### Mandatory test cases

| Scenario | Expected |
|---|---|
| `done` immediately | No records, no division by zero |
| Score 0 | Accepted; FAIL |
| Score 50 | Accepted; PASS |
| Score 100 | Accepted; PASS |
| Score -1 or 101 | Rejected |
| Blank name | Rejected |
| Two equal highest scores | First encountered remains chosen; document tie policy |
| Non-numeric score | Known limitation until Week 7 |

## Extra practice and solutions

**P1 — Find even numbers:** Print even values in `[1,2,3,4,5,6]`.

```python
for n in [1, 2, 3, 4, 5, 6]:
    if n % 2 == 0:
        print(n)
```

**P2 — Dictionary update:** Add key `level` with value `beginner`.

```python
student = {"name": "Ada"}
student["level"] = "beginner"
```

**P3 — Distinct subjects:** Count unique values in `['Maths','Maths','English']`.

```python
subjects = ["Maths", "Maths", "English"]
print(len(set(subjects)))  # 2
```

**P4 — Average with empty data:** Fix `sum(scores)/len(scores)`.

```python
scores = []
average = sum(scores) / len(scores) if scores else None
print(average)
```

**P5 — List vs tuple:** When would you use each? **Solution:** list for changing sequence, tuple for fixed grouping.

**P6 — `break` vs `continue`:** **Solution:** terminate loop vs skip to next iteration.

**P7 — Off-by-one:** What does `range(3)` print? **Solution:** 0, 1, 2.

**P8 — Predict:** `scores=[10,20]; scores.append(30); print(scores[-1])`. **Solution:** 30.

---

# Instructor assessment

| Area | Weight | Evidence |
|---|---:|---|
| Choosing data structures | 20% | Lists/tuples/dicts/sets |
| List/dictionary operations | 20% | Correct manipulation |
| Loops and iteration | 20% | For/while/controls |
| Conditional logic | 15% | Pass/fail and validation |
| Data organisation | 10% | Clear records |
| Independent reasoning | 5% | Explains output |
| Weekly project | 10% | Working analyser |
| **Total** | **100%** | |

## Instructor checklist

- [ ] Learner distinguishes item index from dictionary key.
- [ ] Learner chooses list vs tuple vs set vs dictionary and justifies choice.
- [ ] Learner traces a loop by hand.
- [ ] Learner explains termination and `break`/`continue`.
- [ ] Learner handles empty student collection.
- [ ] Learner tests score boundaries.
- [ ] Learner pushes weekly work with meaningful Git commits.

## Troubleshooting reference

| Error | Likely cause | Demonstration |
|---|---|---|
| `IndexError` | Invalid list index | Compare index 2 vs 3 in 3-item list |
| `KeyError` | Missing dictionary key | Use `.get()` |
| `TypeError` on tuple | Attempted assignment | Compare list mutation |
| Infinite loop | Condition never changes | Add increment or `break` |
| `ZeroDivisionError` | Empty average | Guard with `if scores` |
| `ValueError` on input | Non-numeric text | Flag for Week 7 |

## Suggested deliverables

```text
Week-06/
├── exercises/
│   ├── subject_score_manager.py
│   ├── student_records.py
│   └── guessing_game.py
├── assignments/
│   ├── score_collection.py
│   └── performance_reporter.py
├── projects/
│   └── student_score_analyser.py
└── README.md
```

**Transition to Week 7:** The score analyser works, but its logic lives in one file. Next, extract reusable functions, organise modules, catch invalid numeric input and persist data.
